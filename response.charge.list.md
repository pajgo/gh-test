# Schema List of charges `response.charge.list`  [#/]


**Type**: object





Additional properties allowed: `true`


**Properties:**


 - **data**: `{array}` *isRequired: `false`* Charges
    
    <a name="/properties/data"/>
    
    
    
    
    #### Items:
    
    
    <a name="/properties/data/items"/>
    
    
    
    
    
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
    
 - **meta**: `{object}` *isRequired: `false`* Pagination
    
    <a name="/properties/meta"/>
    
    
    
    
    
    Additional properties allowed: `true`
    
    
    **Properties:**
    
    
     - **offset**: `{number}` *isRequired: `false`* 
     - **limit**: `{number}` *isRequired: `false`* 
     - **cursor**: `{number}` *isRequired: `false`* 
     - **page**: `{number}` *isRequired: `false`* 
     - **pages**: `{number}` *isRequired: `false`* 
    
