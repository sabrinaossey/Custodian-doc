## Tag

The list of tag **(name, value)** pairs that can be used to index the contract for faster retrieval

| Entry| Description|
| --- | --- |
| `name` | Name of a tag |
| `value`| The value of the named tag. It can be a constant or a reference to a variable declared in var[], and can be null if the variable is not set|


## Contract

A list of human-readable descriptions of the contract

| Entry| Description|
| --- | --- |
| `lang` | A 2-letter code of the language used for the contract|
| `title` | A short title|
| `description` |A human-readable descriptions of the contract|


## Var

The list of values that can be dereferenced in other part of the contract body, or template parameter whose values are defined in subsequent versions of the contract

| Entry| Description|
| --- | --- |
| `id` | The local identifier used to dereference the variable|
| `value` | The value of the variable. Once set, it cannot be modified or removed from the contract |
| `regexp`| Restricts the set of values the variable can take if it is still undefined, ignored otherwise |


## Subject

The list of subjects who may perform the operations described in the contract

| Entry| Description|
| --- | --- |
| `id` | The local identifier used to dereference the subject |
| `attribute` | A list of expressions on the subject attributes that must satisfied in order for the subject to be considered in that group.|


## Verb

The list of allowed operations

| Entry| Description|
| --- | --- |
| `id` | The local identifier used to dereference the verb|
| `function` | The actual command represented by the verb (e.g., method identifier, query pattern,...) |
| `attribute` | A list of additional attributes describing the verb| |


## Object

The list of resources that subjects are permitted to operate on

| Entry| Description|
| --- | --- |
| `id` |The local identifier used to dereference the object.|
| `owner`| The Local identifier of the object owner. |
| `attribute` |A list of expressions on the object attributes that must satisfied in order for the object to be considered in that group.|
