# Schema agreement.create `agreement.create`  [#/]


**Type**: object





**Constraints**:

```json
{
  "required": [
    "owner",
    "agreement"
  ]
}
```


Additional properties allowed: `true`


**Properties:**


 - **owner**: `{reference}` *isRequired: `false`* 
    
    Reference: <a href="common.md#/definitions/owner">  (common#/definitions/owner)</a>
    
 - **agreement**: `{undefined}` *isRequired: `false`* 
    
    *Could be allOf:*
    
    
     - 
        Reference: <a href="agreement.md#">  (agreement#)</a>
        
     - 
        <a name="/properties/agreement/allOf/1"/>
        
        
        
        
        
        Additional properties allowed: `true`
        
        
        **Properties:**
        
        
         - **plan**: `{object}` *isRequired: `false`* Plan
            
            <a name="/properties/agreement/allOf/1/properties/plan"/>
            
            
            
            
            
            **Constraints**:
            
            ```json
            {
              "required": [
                "id"
              ]
            }
            ```
            
            
            Additional properties allowed: `true`
            
            
            **Properties:**
            
            
             - **id**: `{string}` *isRequired: `false`* 
                ```json
                {
                  "pattern": "^P-[A-Z0-9]+$"
                }
                ```
                
            
        
    
 - **trialDiscount**: `{integer}` *isRequired: `false`* 
    ```json
    {
      "minimum": 0,
      "maximum": 100,
      "default": 0
    }
    ```
    
 - **trialCycle**: `{integer}` *isRequired: `false`* 
    ```json
    {
      "minimum": 1,
      "default": 12
    }
    ```
    
