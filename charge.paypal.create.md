# Schema charge.paypal.create `charge.paypal.create`  [#/]


**Type**: object





**Constraints**:

```json
{
  "required": [
    "amount",
    "description",
    "returnUrl",
    "cancelUrl"
  ]
}
```


Additional properties allowed: `true`


**Properties:**


 - **amount**: `{integer}` *isRequired: `false`* 
    
    A positive integer representing how much to charge
    
    ```json
    {
      "minimum": 1,
      "maximum": 1000000
    }
    ```
    
 - **description**: `{string}` *isRequired: `false`* 
    
    An arbitrary string which you can attach to a charge object
    
    ```json
    {
      "minLength": 1,
      "maxLength": 65536
    }
    ```
    
 - **returnUrl**: `{string}` *isRequired: `false`* 
    ```json
    {
      "format": "uri"
    }
    ```
    
 - **cancelUrl**: `{string}` *isRequired: `false`* 
    ```json
    {
      "format": "uri"
    }
    ```
    
