# Schema charge.stripe.create `charge.stripe.create`  [#/]


**Type**: object





**Constraints**:

```json
{
  "required": [
    "amount",
    "description"
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
    
 - **statementDescriptor**: `{string}` *isRequired: `false`* 
    
    An arbitrary string to be displayed on your customer’s credit card statement
    
    ```json
    {
      "minLength": 1,
      "maxLength": 22
    }
    ```
    
 - **saveCard**: `{boolean}` *isRequired: `false`* 
    
    Save card for a future charges
    
    ```json
    {
      "default": false
    }
    ```
    
 - **email**: `{string}` *isRequired: `false`* 
    ```json
    {
      "format": "email"
    }
    ```
    
 - **token**: `{string}` *isRequired: `false`* 
    
    Token from stripe Checkout API. Stored card will be used if token is empty
    
    ```json
    {
      "minLength": 1,
      "maxLength": 65536
    }
    ```
    
 - **metadata**: `{object}` *isRequired: `false`* Metadata
    
    <a name="/properties/metadata"/>
    
    
    Set of key-value pairs that you can attach to a charge object
    
    
    **Constraints**:
    
    ```json
    {
      "default": {}
    }
    ```
    
    
    Additional properties allowed: `true`
    
