# Schema sale.create `sale.create`  [#/]


**Type**: object





**Constraints**:

```json
{
  "required": [
    "owner",
    "amount"
  ]
}
```


Additional properties allowed: `true`


**Properties:**


 - **owner**: `{reference}` *isRequired: `false`* 
    
    Reference: <a href="common.md#/definitions/owner">  (common#/definitions/owner)</a>
    
 - **amount**: `{integer}` *isRequired: `false`* 
    ```json
    {
      "minimum": 1,
      "maximum": 10000
    }
    ```
    
