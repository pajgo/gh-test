# Schema Common type: Sale object `sale`  [#/]


**Type**: object





**Constraints**:

```json
{
  "required": [
    "intent",
    "payer",
    "transactions",
    "redirect_urls"
  ]
}
```


Additional properties allowed: `true`


**Properties:**


 - **id**: `{string}` *isRequired: `false`* 
 - **intent**: `{string}` *isRequired: `false`* 
    ```json
    {
      "enum": [
        "sale",
        "authorize",
        "order"
      ]
    }
    ```
    
 - **payer**: `{reference}` *isRequired: `false`* 
    
    Reference: <a href="common.md#/definitions/payer">  (common#/definitions/payer)</a>
    
 - **transactions**: `{array}` *isRequired: `false`* Transactions list
    
    <a name="/properties/transactions"/>
    
    
    
    
    #### Items:
    
    
    <a name="/properties/transactions/items"/>
    
    
    
    
    
    **Constraints**:
    
    ```json
    {
      "required": [
        "amount"
      ]
    }
    ```
    
    
    Additional properties allowed: `true`
    
    
    **Properties:**
    
    
     - **reference_id**: `{string}` *isRequired: `false`* 
     - **amount**: `{object}` *isRequired: `false`* Amount
        
        <a name="/properties/transactions/items/properties/amount"/>
        
        
        
        
        
        Additional properties allowed: `true`
        
        
        **Properties:**
        
        
         - **currency**: `{string}` *isRequired: `false`* 
         - **total**: `{string}` *isRequired: `false`* 
        
     - **description**: `{string}` *isRequired: `false`* 
     - **note_to_payee**: `{string}` *isRequired: `false`* 
     - **custom**: `{string}` *isRequired: `false`* 
     - **invoice_number**: `{string}` *isRequired: `false`* 
     - **notify_url**: `{string}` *isRequired: `false`* 
     - **order_url**: `{string}` *isRequired: `false`* 
     - **item_list**: `{object}` *isRequired: `false`* Item list
        
        <a name="/properties/transactions/items/properties/item_list"/>
        
        
        
        
        
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
        
        
         - **items**: `{array}` *isRequired: `false`* Items
            
            <a name="/properties/transactions/items/properties/item_list/properties/items"/>
            
            
            
            
            ###### Items:
            
            
            Reference: <a href="common.md#/definitions/item">  (common#/definitions/item)</a>
            
        
    
 - **billing_agreement_tokens**: `{array}` *isRequired: `false`* Billing agreement tokens
    
    <a name="/properties/billing_agreement_tokens"/>
    
    
    
    
    #### Items:
    
 - **experience_profile_id**: `{string}` *isRequired: `false`* 
 - **redirect_urls**: `{object}` *isRequired: `false`* Redirect urls
    
    <a name="/properties/redirect_urls"/>
    
    
    
    
    
    Additional properties allowed: `true`
    
    
    **Properties:**
    
    
     - **return_url**: `{string}` *isRequired: `false`* 
     - **cancel_url**: `{string}` *isRequired: `false`* 
    
