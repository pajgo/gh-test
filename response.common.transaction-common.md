# Schema Transaction common info `response.common.transaction-common`  [#/]


**Type**: object





Additional properties allowed: `true`


**Properties:**


 - **id**: `{string}` *isRequired: `false`* 
 - **type**: `{number}` *isRequired: `false`* 
 - **owner**: `{reference}` *isRequired: `false`* 
    
    Reference: <a href="common.md#/definitions/owner">  (common#/definitions/owner)</a>
    
 - **agreementId**: `{string}` *isRequired: `false`* 
 - **payer**: `{string}` *isRequired: `false`* 
    ```json
    {
      "format": "email"
    }
    ```
    
 - **date**: `{number}` *isRequired: `false`* 
 - **amount**: `{string}` *isRequired: `false`* 
 - **description**: `{string}` *isRequired: `false`* 
 - **status**: `{string}` *isRequired: `false`* 
