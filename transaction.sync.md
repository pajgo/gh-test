# Schema transaction.sync `transaction.sync`  [#/]


**Type**: object





**Constraints**:

```json
{
  "required": [
    "id"
  ]
}
```


Additional properties allowed: `true`


**Properties:**


 - **owner**: `{reference}` *isRequired: `false`* 
    
    Reference: <a href="common.md#/definitions/owner">  (common#/definitions/owner)</a>
    
 - **id**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    
 - **start**: `{string}` *isRequired: `false`* 
    ```json
    {
      "format": "date"
    }
    ```
    
 - **end**: `{string}` *isRequired: `false`* 
    ```json
    {
      "format": "date"
    }
    ```
    
