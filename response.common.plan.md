# Schema Common type: Payment plan response object `response.common.plan`  [#/]


**Type**: object





Additional properties allowed: `true`


**Properties:**


 - **id**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    
 - **name**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    
 - **description**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    
 - **hidden**: `{boolean}` *isRequired: `false`* 
 - **type**: `{reference}` *isRequired: `false`* 
    
    Reference: <a href="plan.md#/definitions/type">  (plan#/definitions/type)</a>
    
 - **state**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    
 - **create_time**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    
 - **update_time**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    
 - **payment_definitions**: `{array}` *isRequired: `false`* Payment definitions
    
    <a name="/properties/payment_definitions"/>
    
    
    
    
    #### Items:
    
    
    Reference: <a href="response.common.md#/definitions/payment_definition">  (response.common#/definitions/payment_definition)</a>
    
 - **terms**: `{array}` *isRequired: `false`* Terms
    
    <a name="/properties/terms"/>
    
    
    
    
    #### Items:
    
    
    Reference: <a href="common.md#/definitions/term">  (common#/definitions/term)</a>
    
 - **merchant_preferences**: `{reference}` *isRequired: `false`* 
    
    Reference: <a href="response.common.md#/definitions/merchant_preferences">  (response.common#/definitions/merchant_preferences)</a>
    
 - **links**: `{array}` *isRequired: `false`* Payment provider links
    
    <a name="/properties/links"/>
    
    
    
    
    #### Items:
    
    
    Reference: <a href="common.md#/definitions/links">  (common#/definitions/links)</a>
    
 - **httpStatusCode**: `{integer}` *isRequired: `false`* 
