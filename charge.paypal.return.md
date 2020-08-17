# Schema charge.paypal.return `charge.paypal.return`  [#/]


**Type**: object





**Constraints**:

```json
{
  "required": [
    "PayerID",
    "paymentId"
  ]
}
```


Additional properties allowed: `true`


**Properties:**


 - **PayerID**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1,
      "maxLength": 1024
    }
    ```
    
 - **paymentId**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1,
      "maxLength": 1024
    }
    ```
    
 - **token**: `{string}` *isRequired: `false`* 
    
    Paypal token
    
    ```json
    {
      "minLength": 1,
      "maxLength": 1024
    }
    ```
    
