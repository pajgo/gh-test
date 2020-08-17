# Schema agreement.bill `agreement.state`  [#/]


**Type**: object





**Constraints**:

```json
{
  "required": [
    "owner",
    "state"
  ]
}
```


Additional properties allowed: `true`


**Properties:**


 - **owner**: `{reference}` *isRequired: `false`* 
    
    Reference: <a href="common.md#/definitions/owner">  (common#/definitions/owner)</a>
    
 - **state**: `{string}` *isRequired: `false`* 
    ```json
    {
      "enum": [
        "suspend",
        "reactivate",
        "cancel"
      ]
    }
    ```
    
 - **note**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    
