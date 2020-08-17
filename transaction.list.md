# Schema transaction.list `transaction.list`  [#/]


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
    
 - **filter**: `{reference}` *isRequired: `false`* 
    
    Reference: <a href="common.md#/definitions/filter">  (common#/definitions/filter)</a>
    
 - **criteria**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
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
    
 - **owner**: `{reference}` *isRequired: `false`* 
    
    Reference: <a href="common.md#/definitions/owner">  (common#/definitions/owner)</a>
    
