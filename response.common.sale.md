# Schema Common type: Sale response object `response.common.sale`  [#/]


**Type**: object





Additional properties allowed: `true`


**Properties:**


 - **httpStatusCode**: `{number}` *isRequired: `false`* 
    
    payment system response code
    
 - **id**: `{string}` *isRequired: `false`* 
    
    Some id
    
 - **intent**: `{string}` *isRequired: `false`* 
    
    payment intent
    
    ```json
    {
      "enum": [
        "sale",
        "authorize",
        "order"
      ]
    }
    ```
    
 - **state**: `{string}` *isRequired: `false`* 
    
    #TODO
    
 - **payer**: `{reference}` *isRequired: `false`* 
    
    Reference: <a href="common.md#/definitions/payer">  (common#/definitions/payer)</a>
    
 - **cart**: `{string}` *isRequired: `false`* 
    
    #TODO more definite type
    
 - **create_time**: `{string}` *isRequired: `false`* 
    ```json
    {
      "format": "date-time"
    }
    ```
    
 - **update_time**: `{string}` *isRequired: `false`* 
    ```json
    {
      "format": "date-time"
    }
    ```
    
 - **transactions**: `{array}` *isRequired: `false`* Transactions list
    
    <a name="/properties/transactions"/>
    
    
    
    
    #### Items:
    
    
    Reference: <a href="#/definitions/transaction">  (#/definitions/transaction)</a>
    
 - **failed_transactions**: `{array}` *isRequired: `false`* Transactions list
    
    <a name="/properties/failed_transactions"/>
    
    
    
    
    #### Items:
    
    
    Reference: <a href="#/definitions/transaction">  (#/definitions/transaction)</a>
    
 - **billing_agreement_tokens**: `{array}` *isRequired: `false`* Billing agreement tokens
    
    <a name="/properties/billing_agreement_tokens"/>
    
    
    
    
    #### Items:
    
 - **experience_profile_id**: `{string}` *isRequired: `false`* 
 - **links**: `{array}` *isRequired: `false`* Payment provider links
    
    <a name="/properties/links"/>
    
    
    
    
    #### Items:
    
    
    Reference: <a href="common.md#/definitions/links">  (common#/definitions/links)</a>
    


**Definitions**:

#### response.common.sale#/definitions/transaction Transaction





<a name="/definitions/transaction"/>





Additional properties allowed: `true`


**Properties:**


 - **reference_id**: `{string}` *isRequired: `false`* 
 - **amount**: `{object}` *isRequired: `false`* 
    
    <a name="/definitions/transaction/properties/amount"/>
    
    
    
    
    
    Additional properties allowed: `true`
    
    
    **Properties:**
    
    
     - **currency**: `{string}` *isRequired: `false`* 
     - **total**: `{number,string}` *isRequired: `false`* 
    
 - **description**: `{string}` *isRequired: `false`* 
 - **note_to_payee**: `{string}` *isRequired: `false`* 
 - **custom**: `{string}` *isRequired: `false`* 
 - **invoice_number**: `{string}` *isRequired: `false`* 
 - **notify_url**: `{string}` *isRequired: `false`* 
 - **order_url**: `{string}` *isRequired: `false`* 
 - **item_list**: `{object}` *isRequired: `false`* Item list
    
    <a name="/definitions/transaction/properties/item_list"/>
    
    
    
    
    
    **Constraints**:
    
    ```json
    {
      "required": [
        "items"
      ]
    }
    ```
    
    
    Additional properties allowed: `true`
    
    
    **Properties:**
    
    
     - **additionalProperties**: `{undefined}` *isRequired: `false`* 
     - **items**: `{array}` *isRequired: `false`* Items
        
        <a name="/definitions/transaction/properties/item_list/properties/items"/>
        
        
        
        
        ###### Items:
        
        
        Reference: <a href="response.common.md#/definitions/transaction_item">  (response.common#/definitions/transaction_item)</a>
        
    
 - **related_resources**: `{array}` *isRequired: `false`* 
    
    <a name="/definitions/transaction/properties/related_resources"/>
    
    
    #TODO
    
    ###### Items:
    
