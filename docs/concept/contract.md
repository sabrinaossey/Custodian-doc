#Contract Manager
The Contract Manager (UCM) provides end-point REST apis to create and manage contracts.

A Contract is a binding agreement between parties based on agreed-upon terms and conditions for data sharing and processing.
A contract is readable by both people and machines. It is also cryptographically signed and verified against some security proofs.

## Contract Description

* Contract Body


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

* Digital Signatures
