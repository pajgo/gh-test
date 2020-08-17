# Schema transaction.get response `response.transaction.get`  [#/]


**Type**: object





Additional properties allowed: `true`


**Properties:**


 - **amount**: `{number}` *isRequired: `false`* 
 - **owner**: `{reference}` *isRequired: `false`* 
    
    Reference: <a href="common.md#/definitions/owner">  (common#/definitions/owner)</a>
    
 - **type**: `{number}` *isRequired: `false`* 
    
    #TODO
    
 - **agreementId**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    
 - **payer**: `{string}` *isRequired: `false`* 
    
    #TODO
    
    ```json
    {
      "minLength": 1,
      "maxLength": 127
    }
    ```
    
 - **date**: `{number}` *isRequired: `false`* 
 - **description**: `{string}` *isRequired: `false`* 
    ```json
    {
      "maxLength": 512
    }
    ```
    
 - **status**: `{string}` *isRequired: `false`* 
    
    #TODO
    
