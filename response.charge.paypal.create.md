# Schema Create paypal charge `response.charge.paypal.create`  [#/]


**Type**: object





Additional properties allowed: `true`


**Properties:**


 - **data**: `{object}` *isRequired: `false`* Charge
    
    <a name="/properties/data"/>
    
    
    
    
    
    Additional properties allowed: `true`
    
    
    **Properties:**
    
    
     - **amount**: `{number}` *isRequired: `false`* 
     - **description**: `{string}` *isRequired: `false`* 
     - **status**: `{number}` *isRequired: `false`* 
     - **createAt**: `{string}` *isRequired: `false`* 
        ```json
        {
          "format": "date"
        }
        ```
        
     - **owner**: `{reference}` *isRequired: `false`* 
        
        Reference: <a href="common.md#/definitions/owner">  (common#/definitions/owner)</a>
        
     - **failReason**: `{string}` *isRequired: `false`* 
    
 - **meta**: `{object}` *isRequired: `false`* Metadata
    
    <a name="/properties/meta"/>
    
    
    
    
    
    Additional properties allowed: `true`
    
    
    **Properties:**
    
    
     - **paypal**: `{object}` *isRequired: `false`* Paypal charge metadata
        
        <a name="/properties/meta/properties/paypal"/>
        
        
        
        
        
        Additional properties allowed: `true`
        
        
        **Properties:**
        
        
         - **approvalUrl**: `{reference}` *isRequired: `false`* 
            
            Reference: <a href="common.md#/definitions/links">  (common#/definitions/links)</a>
            
         - **paymentId**: `{reference}` *isRequired: `false`* 
            
            Reference: <a href="common.md#/definitions/paymentId">  (common#/definitions/paymentId)</a>
            
        
    
