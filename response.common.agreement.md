# Schema Response: Agreement object `response.common.agreement`  [#/]


**Type**: object


Agreement response object structure


Additional properties allowed: `true`


**Properties:**


 - **t**: `{integer}` *isRequired: `false`* 
    
    #TODO FINDOUT Something internal
    
 - **httpStatusCode**: `{integer}` *isRequired: `false`* 
 - **id**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    
 - **state**: `{string}` *isRequired: `false`* 
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
    
 - **start_date**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    
 - **agreement_details**: `{reference}` *isRequired: `false`* 
    
    Reference: <a href="common.md#/definitions/agreement_details">  (common#/definitions/agreement_details)</a>
    
 - **payer**: `{reference}` *isRequired: `false`* 
    
    Reference: <a href="common.md#/definitions/payer">  (common#/definitions/payer)</a>
    
 - **shipping_address**: `{reference}` *isRequired: `false`* 
    
    Reference: <a href="common.md#/definitions/address">  (common#/definitions/address)</a>
    
 - **override_merchant_preferences**: `{reference}` *isRequired: `false`* 
    
    Reference: <a href="common.md#/definitions/merchant_preferences">  (common#/definitions/merchant_preferences)</a>
    
 - **override_charge_models**: `{array}` *isRequired: `false`* Override chage models
    
    <a name="/properties/override_charge_models"/>
    
    
    
    
    #### Items:
    
    
    Reference: <a href="common.md#/definitions/override_charge_model">  (common#/definitions/override_charge_model)</a>
    
 - **plan**: `{reference}` *isRequired: `false`* 
    
    Reference: <a href="response.plan.md#">  (response.common.plan#)</a>
    
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
    
 - **links**: `{array}` *isRequired: `false`* Payment service links
    
    <a name="/properties/links"/>
    
    
    
    
    #### Items:
    
    
    Reference: <a href="common.md#/definitions/links">  (common#/definitions/links)</a>
    
