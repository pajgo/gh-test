# Schema Transaction info `response.common.transaction-info`  [#/]


**Type**: object





Additional properties allowed: `true`


**Properties:**


 - **transaction_id**: `{string}` *isRequired: `false`* 
 - **status**: `{string}` *isRequired: `false`* 
 - **transaction_type**: `{string}` *isRequired: `false`* 
 - **payer_email**: `{string}` *isRequired: `false`* 
    ```json
    {
      "format": "email"
    }
    ```
    
 - **payer_name**: `{string}` *isRequired: `false`* 
 - **time_stamp**: `{string}` *isRequired: `false`* 
    ```json
    {
      "format": "date-time"
    }
    ```
    
 - **time_zone**: `{string}` *isRequired: `false`* 
 - **amount**: `{reference}` *isRequired: `false`* Amount
    
    Reference: <a href="response.common.md#/definitions/amount">Amount  (response.common#/definitions/amount)</a>
    
 - **fee_amount**: `{reference}` *isRequired: `false`* Fee amount
    
    Reference: <a href="response.common.md#/definitions/amount">Fee amount  (response.common#/definitions/amount)</a>
    
 - **net_amount**: `{reference}` *isRequired: `false`* Net amount
    
    Reference: <a href="response.common.md#/definitions/amount">Net amount  (response.common#/definitions/amount)</a>
    
