# Schema  `response.common`  [#/]


**Type**: undefined





Additional properties allowed: `true`


**Definitions**:

#### response.common#/definitions/payment_definition Payment definition





<a name="/definitions/payment_definition"/>





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
    
 - **type**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1,
      "enum": [
        "trial",
        "regular",
        "TRIAL",
        "REGULAR"
      ]
    }
    ```
    
 - **frequency_interval**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    
 - **frequency**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    
 - **cycles**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    
 - **amount**: `{reference}` *isRequired: `false`* 
    
    Reference: <a href="common.md#/definitions/currency">  (common#/definitions/currency)</a>
    
 - **charge_models**: `{array}` *isRequired: `false`* Charge models
    
    <a name="/definitions/payment_definition/properties/charge_models"/>
    
    
    
    
    ###### Items:
    
    
    <a name="/definitions/payment_definition/properties/charge_models/items"/>
    
    
    
    
    
    **Constraints**:
    
    ```json
    {
      "required": [
        "type",
        "amount"
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
        
     - **type**: `{string}` *isRequired: `false`* 
        ```json
        {
          "minLength": 1
        }
        ```
        
     - **amount**: `{reference}` *isRequired: `false`* 
        
        Reference: <a href="common.md#/definitions/currency">  (common#/definitions/currency)</a>
        
    

#### response.common#/definitions/merchant_preferences Merchant preferences





<a name="/definitions/merchant_preferences"/>





Additional properties allowed: `true`


**Properties:**


 - **id**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    
 - **setup_fee**: `{reference}` *isRequired: `false`* 
    
    Reference: <a href="common.md#/definitions/currency">  (common#/definitions/currency)</a>
    
 - **cancel_url**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    
 - **return_url**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    
 - **notify_url**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    
 - **max_fail_attempts**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    
 - **auto_bill_amount**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    
 - **initial_fail_amount_action**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    
 - **accepted_payment_type**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    
 - **char_set**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    

#### response.common#/definitions/amount 





<a name="/definitions/amount"/>





Additional properties allowed: `true`


**Properties:**


 - **currency**: `{string}` *isRequired: `false`* 
 - **value**: `{number,string}` *isRequired: `false`* 

#### response.common#/definitions/transaction_item ResponsePurchase item





<a name="/definitions/transaction_item"/>





Additional properties allowed: `true`


**Properties:**


 - **quantity**: `{string,number}` *isRequired: `false`* 
 - **name**: `{string}` *isRequired: `false`* 
 - **description**: `{string}` *isRequired: `false`* 
 - **price**: `{string}` *isRequired: `false`* 
 - **tax**: `{string}` *isRequired: `false`* 
 - **currency**: `{string}` *isRequired: `false`* 
