# Schema Paypal charge return `response.charge.paypal.return`  [#/]


**Type**: object





Additional properties allowed: `true`


**Properties:**


 - **data**: `{object}` *isRequired: `false`* Charge information
    
    <a name="/properties/data"/>
    
    
    
    
    
    Additional properties allowed: `true`
    
    
    **Properties:**
    
    
     - **id**: `{string}` *isRequired: `false`* 
        
        #TODO
        
        ```json
        {
          "format": "uuid"
        }
        ```
        
     - **type**: `{string}` *isRequired: `false`* 
        
        #TODO
        
        ```json
        {
          "const": "charge"
        }
        ```
        
     - **attributes**: `{object}` *isRequired: `false`* 
        
        <a name="/properties/data/properties/attributes"/>
        
        
        
        
        
        Additional properties allowed: `true`
        
        
        **Properties:**
        
        
         - **amount**: `{string}` *isRequired: `false`* 
         - **description**: `{string}` *isRequired: `false`* 
         - **status**: `{number}` *isRequired: `false`* 
         - **createAt**: `{string}` *isRequired: `false`* 
            ```json
            {
              "format": "date-time"
            }
            ```
            
         - **owner**: `{reference}` *isRequired: `false`* 
            
            Reference: <a href="common.md#/definitions/owner">  (common#/definitions/owner)</a>
            
         - **failReason**: `{string}` *isRequired: `false`* 
        
    
 - **meta**: `{object}` *isRequired: `false`* Paypal metadata
    
    <a name="/properties/meta"/>
    
    
    
    
    
    Additional properties allowed: `true`
    
    
    **Properties:**
    
    
     - **paypal**: `{object}` *isRequired: `false`* 
        
        <a name="/properties/meta/properties/paypal"/>
        
        
        
        
        
        Additional properties allowed: `true`
        
        
        **Properties:**
        
        
         - **payer**: `{reference}` *isRequired: `false`* 
            
            Reference: <a href="common.md#/definitions/payer">  (common#/definitions/payer)</a>
            
        
    
