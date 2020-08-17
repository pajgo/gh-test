# Schema charge.list `charge.list`  [#/]


**Type**: object





**Constraints**:

```json
{
  "required": [
    "limit",
    "offset"
  ]
}
```


Additional properties allowed: `true`


**Properties:**


 - **owner**: `{reference}` *isRequired: `false`* 
    
    Reference: <a href="common.md#/definitions/owner">  (common#/definitions/owner)</a>
    
 - **limit**: `{integer}` *isRequired: `false`* 
    ```json
    {
      "minimum": 1,
      "maximum": 100,
      "default": 20
    }
    ```
    
 - **offset**: `{integer}` *isRequired: `false`* 
    ```json
    {
      "minimum": 0,
      "default": 0
    }
    ```
    
