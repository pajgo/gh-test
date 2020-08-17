# Schema plan.state `plan.state`  [#/]


**Type**: object





**Constraints**:

```json
{
  "required": [
    "id",
    "state"
  ]
}
```


Additional properties allowed: `true`


**Properties:**


 - **id**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    
 - **state**: `{string}` *isRequired: `false`* 
    ```json
    {
      "enum": [
        "created",
        "active",
        "inactive",
        "deleted"
      ]
    }
    ```
    
