# Schema agreement.list response `response.agreement.list`  [#/]


**Type**: object





**Constraints**:

```json
{
  "required": [
    "items",
    "cursor",
    "page",
    "pages"
  ]
}
```


Additional properties allowed: `true`


**Properties:**


 - **items**: `{array}` *isRequired: `false`* Agreements
    
    <a name="/properties/items"/>
    
    
    
    
    #### Items:
    
    
    Reference: <a href="response.agreement.get.md#">  (response.agreement.get#)</a>
    
 - **cursor**: `{number}` *isRequired: `false`* 
 - **page**: `{number}` *isRequired: `false`* 
 - **pages**: `{number}` *isRequired: `false`* 
