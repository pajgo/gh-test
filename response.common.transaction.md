# Schema Transaction `response.common.transaction`  [#/]


**Type**: object





Additional properties allowed: `true`


**Properties:**


 - **agreement**: `{string}` *isRequired: `false`* 
 - **payer_email**: `{string}` *isRequired: `false`* 
    ```json
    {
      "format": "email"
    }
    ```
    
 - **status**: `{string}` *isRequired: `false`* 
 - **owner**: `{reference}` *isRequired: `false`* 
    
    Reference: <a href="common.md#/definitions/owner">  (common#/definitions/owner)</a>
    
 - **transaction_type**: `{string}` *isRequired: `false`* 
 - **transaction**: `{reference}` *isRequired: `false`* 
    
    Reference: <a href="response.transaction-info.md#">  (response.common.transaction-info#)</a>
    
 - **time_stamp**: `{number}` *isRequired: `false`* 
