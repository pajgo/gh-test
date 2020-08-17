# Schema balance.decrement `balance.decrement`  [#/]


**Type**: object





**Constraints**:

```json
{
  "required": [
    "ownerId",
    "amount",
    "idempotency",
    "goal"
  ]
}
```


Additional properties allowed: `true`


**Properties:**


 - **ownerId**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1,
      "maxLength": 65536
    }
    ```
    
 - **amount**: `{integer}` *isRequired: `false`* 
    
    A positive integer representing how much to charge
    
    ```json
    {
      "minimum": 1,
      "maximum": 1000000
    }
    ```
    
 - **idempotency**: `{string}` *isRequired: `false`* 
    
    An idempotency key
    
    ```json
    {
      "minLength": 1,
      "maxLength": 65536
    }
    ```
    
 - **goal**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1,
      "maxLength": 65536
    }
    ```
    
