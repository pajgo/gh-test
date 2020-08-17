# Schema sale.createDynamic `sale.createDynamic`  [#/]


**Type**: object





**Constraints**:

```json
{
  "required": [
    "owner",
    "amount",
    "cart",
    "type"
  ]
}
```


Additional properties allowed: `true`


**Properties:**


 - **owner**: `{reference}` *isRequired: `false`* 
    
    Reference: <a href="common.md#/definitions/owner">  (common#/definitions/owner)</a>
    
 - **amount**: `{number}` *isRequired: `false`* 
    ```json
    {
      "minimum": 0,
      "maximum": 999999
    }
    ```
    
 - **type**: `{integer}` *isRequired: `false`* 
    ```json
    {
      "const": 2
    }
    ```
    
 - **cart**: `{object}` *isRequired: `false`* Cart
    
    <a name="/properties/cart"/>
    
    
    
    
    
    **Constraints**:
    
    ```json
    {
      "required": [
        "id",
        "shipping_type",
        "shipping_price",
        "printing_price",
        "service_price",
        "user_price"
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
        
     - **shipping_type**: `{string}` *isRequired: `false`* 
        ```json
        {
          "minLength": 1
        }
        ```
        
     - **shipping_price**: `{number}` *isRequired: `false`* 
        ```json
        {
          "minimum": 0,
          "maximum": 999999
        }
        ```
        
     - **printing_price**: `{number}` *isRequired: `false`* 
        ```json
        {
          "minimum": 0,
          "maximum": 999999
        }
        ```
        
     - **service_price**: `{number}` *isRequired: `false`* 
        ```json
        {
          "minimum": 0,
          "maximum": 999999
        }
        ```
        
     - **user_price**: `{number}` *isRequired: `false`* 
        ```json
        {
          "minimum": 0,
          "maximum": 999999
        }
        ```
        
    
