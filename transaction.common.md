# Schema transaction.common `transaction.common`  [#/]


**Type**: object





Additional properties allowed: `true`


**Properties:**


 - **offset**: `{integer}` *isRequired: `false`* 
    ```json
    {
      "minimum": 0
    }
    ```
    
 - **limit**: `{integer}` *isRequired: `false`* 
    ```json
    {
      "minimum": 1,
      "maximum": 100
    }
    ```
    
 - **order**: `{string}` *isRequired: `false`* 
    ```json
    {
      "enum": [
        "ASC",
        "DESC"
      ]
    }
    ```
    
 - **criteria**: `{string}` *isRequired: `false`* 
 - **owner**: `{reference}` *isRequired: `false`* 
    
    Reference: <a href="common.md#/definitions/owner">  (common#/definitions/owner)</a>
    
 - **type**: `{string}` *isRequired: `false`* 
    ```json
    {
      "enum": [
        "sale",
        "subscription"
      ]
    }
    ```
    
 - **filter**: `{reference}` *isRequired: `false`* 
    
    Reference: <a href="common.md#/definitions/filter">  (common#/definitions/filter)</a>
    
