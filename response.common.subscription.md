# Schema Common type: Subscription response object `response.common.subscription`  [#/]


**Type**: object





**Constraints**:

```json
{
  "required": [
    "name",
    "models",
    "definition",
    "price"
  ]
}
```


Additional properties allowed: `true`


**Properties:**


 - **models**: `{number}` *isRequired: `false`* 
 - **price**: `{number}` *isRequired: `false`* 
 - **name**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    
 - **definition**: `{reference}` *isRequired: `false`* 
    
    Reference: <a href="common.md#/definitions/payment_definition">  (common#/definitions/payment_definition)</a>
    
