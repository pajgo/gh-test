# Schema Charge `response.charge.get`  [#/]


**Type**: object





Additional properties allowed: `true`


**Properties:**


 - **data**: `{object}` *isRequired: `false`* Charge information
    
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
    
