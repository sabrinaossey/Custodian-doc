## Tag

| Entry| Description|
| --- | --- |
| `tag` |The list of tag **(name, value)** pairs that can be used to index the contract for faster retrieval|
| `tag[].name` | Name of a tag |
| `tag[].value`| The value of the named tag. It can be a constant or a reference to a variable declared in var[], and can be null if the variable is not set|


## Contract
| Entry| Description|
| --- | --- |
| `contract` | A list of human-readable descriptions of the contract|
| `contract[].lang` | A 2-letter code of the language used for the contract|
| `contract[].title` | A short title|
| `contract[].description` |A human-readable descriptions of the contract|


## Var
| Entry| Description|
| --- | --- |
| `var` | The list of values that can be dereferenced in other part of the contract body, or template parameter whose values are defined in subsequent versions of the contract |
| `var[].id` | The local identifier used to dereference the variable|
| `var[].value` | The value of the variable. Once set, it cannot be modified or removed from the contract |
| `var[].(regexp|type)` | Restricts the set of values the variable can take if it is still undefined, ignored otherwise |


## Subject
| Entry| Description|
| --- | --- |
| `subject` | The list of subjects who may perform the operations described in the contract|
| `subject[].id` | The local identifier used to dereference the subject |
| `subject[].attribute` | A list of expressions on the subject attributes that must satisfied in order for the subject to be considered in that group.|


## Verb
| Entry| Description|
| --- | --- |
| `verb` | The list of allowed operations |
| `verb[].id` | The local identifier used to dereference the verb|
| `verb[].function` | The actual command represented by the verb (e.g., method identifier, query pattern,...) |
| `verb[].attribute` | A list of additional attributes describing the verb| |


## Object
| Entry| Description|
| --- | --- |
| `object` | The list of resources that subjects are permitted to operate on |
| `object[].id` |The local identifier used to dereference the object.|
| `object[].owner`| The Local identifier of the object owner. |
| `object[].attribute` |A list of expressions on the object attributes that must satisfied in order for the object to be considered in that group.|
