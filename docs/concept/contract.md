#Contract Manager
The Contract Manager (UCM) provides REST end-points to create and manage contracts.

A Contract is a binding agreement between parties based on agreed-upon terms and conditions for data sharing and processing.
A contract is readable by both people and machines. It is also cryptographically signed and verified against some security proofs.

## Contract Description

A contract consist of a contract body that describes the terms of the contract and a list of digital signatures of the parties involved in.

**Elements of Contract Body**

| Entry| Required| Description| Schema|
| --- | --- | --- |--- |
| `id` | yes | A globally unique contract identifier | -|
| `tag` | no |The list of tag **(name, value)** pairs that can be used to index the contract for faster retrieval| [Tag](./schema.md#Tag)|
| `contract` | yes | A list of human-readable descriptions of the contract| [Contract](./schema.md#Contract)|
| `var` | no | The list of values that can be dereferenced in other part of the contract body, or template parameter whose values are defined in subsequent versions of the contract | [Var](./schema.md#Var)|
| `subject` | yes |The list of subjects who may perform the operations described in the contract| [Subject](./schema.md#Subject)|
| `verb` | yes | The list of allowed operations | [Verb](./schema.md#Verb)|
| `object` | yes | The list of resources that subjects are permitted to operate on | [Object](./schema.md#Object)|
| `scope` | yes | The list of permitted **subject, verb, object** triplets. | -|
| `validity` | yes |The conditions used to verify the validity of the contract.| -|


<details><summary>Example of Contrat Body in Json format</summary>
<p>

```json
{
  "id": "did:custodian:12345678abcdefgh",
  "tag": [
      {
          "name": "provider",
          "value": "#provider"
      },
      {
          "name": "consumer",
          "value": "#consumer"
      },
  ],
  "contract": [
      {
         "lang": "en",
         "title": "End User Agreement",
        "description": "...",
      }
  ],
  "var": [
      {
          "id": "did:custodian:12345678abcdefgh#provider",
          "type":  "oid",
          "regexp": "did:custodian:[0-9a-zA-Z_-]"
      },
      {
          "id": "did:custodian:12345678abcdefgh#consumer",
          "value": "did:custodian:1234abcd5678efgh"
      }
  ],
  "subject":  [
      {
          "id": "did:custodian:12345678abcdefgh#subj-1",
          "attribute": {
            "oid":  "#provider",
            "sign": [ "#id" ]
          }
      },
      {
          "id": "did:custodian:12345678abcdefgh#subj-2",
          "attribute": {
              "oid":  "#consumer",
              "sign": [ "#id" ]
          }
      }
  ],
  "verb": [
      {
          "id": "did:custodian:12345678abcdefgh#read",
          "function": "custodian.epfl.ch/select?query=*",
          "attribute": {
              "max_calls_per_day": 3
          }
      },
      {
          "id": "did:custodian:12345678abcdefgh#add",
          "function": "custodian.epfl.ch/add",
          "attribute": {}
      }
  ],
  "object": [
      {
          "id": "did:custodian:12345678abcdefgh#obj-1",
          "owner": "#subj-1",
          "attribute": {
              "sensitivity": {
                  "op": "lt",
                  "level": 7
              }
        }
      }
  ],
  "scope":  [
      {
          "subject": [ "#subj-1", "#subj-2" ], "verb": [ "#read" ], "object": [ "#obj-1" ]
      },
      {
          "subject": [ "#subj-2" ], "verb": [ "#add" ], "object": [ "#obj-1" ]
      }
  ],
  "validity": {
      "notBefore" : "2022-01-01T00:00:00Z",
      "notAfter"  : "2022-12-01T23:59:59Z",
      "duration"   : "1Y",
      "sign" : [ "#provider", "#consumer" ]
   }
}
```

</p>
</details>

**Digital Signatures**


Contract signatures are unforgeable and non-repudiable proofs that a user has agreed to a contract.
The JSON signature consists of a header and a seal.

**Elements of Signature**

| Entry| Required| Description|
| --- | --- | --- |
| `id` | yes | A globally unique signature identifier |
| `header.body` | yes |Verifiable reference to the contract body: its identity, base64 digest (hash) and method used to compute the digest|
| `header.body.id` | yes | The contract's identity |
| `header.body.digestMethod` | yes | The methods used to compute the contract's digest|
| `header.body.digest` | yes | The current contract's digest.|
| `header.prev` | no |The verifiable reference to a previous signature if any, otherwise it must not appear in the signature.|
| `header.prev.id` | yes | The previous signature's identity.|
| `header.prev.digestMethod` | yes | The methods used to compute the previous signature:21's digest.|
| `header.prev.digest` | yes | The previous contract's digest. |
| `seal[].signee` | yes |The identity and public key of the user signing the document|
| `seal[].timestamp` | yes | The signature timestamp, and a nonce |
| `seal[].source` | yes | The hash or unique representation of inputs and method used to create the contract body and signature, so that it can be used to deduplicate signatures |
| `seal[].signature` | yes | The base64 digest of the header part (everything between { and } included) encrypted with the secret key of the header.signee using the seal.signatureMethod |
| `seal[].signatureMethod` | yes | Signature method, subsums the header digest method|





<details><summary>Example Of Json Signature </summary>
<p>


```
{

  "id": "did:custodian:12345678zyxwvut",


  "header": {

      "body": {

          "id": "did:custodian:12345678abcdefgh",

          "digestMethod": "SHA256base64",

          "digest": "H/y/vkDEqVOeisYHEJynZJ7FnzGmJgNqbYOZEIBN1l4="

      },

      "prev": {

          "id": "did:custodian:87654321zyxwvu",

          "digestMethod": "SHA256base64",

          "digest": "Yqca1ey8ltbDI7eApqRrzVa0IcKSoRPLL6poGSJln/Y="

      },

  },


  "seal": [ {

      "signee": "did:custodian:12345678abcdefgh?kid=00123456habc123",

      "timestamp": "2022-05-01T19:07:31Z",

      "source": "bd4299f40251028465a541e52e1c24f3de5703c048ecce0f12ffeb95a06845a3",

      "signatureMethod": "ECDSA",

      "signature": "SumXX3esbBrXIsfafJCYQXAruPGX4DgSoGlD/ozKtO5AY98ErTQX/NGpOGaKNwCkResqtG9IeuyvdDh7eJMcWw=="

  } ]

}
```

</p>
</details>
