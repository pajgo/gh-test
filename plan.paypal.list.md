# Schema plan.paypal-list `plan.paypal.list`  [#/]


**Type**: object





Additional properties allowed: `true`


**Properties:**


 - **hidden**: `{boolean}` *isRequired: `false`* 
 - **query**: `{object}` *isRequired: `false`* Paypal plan list uery params
    
    <a name="/properties/query"/>
    
    
    
    
    
    **Constraints**:
    
    ```json
    {
      "page": {
        "type": "string",
        "minLength": 1
      },
      "status": {
        "type": "string",
        "minLength": 1,
        "enum": [
          "created",
          "active",
          "inactive"
        ]
      },
      "page_size": {
        "type": "string",
        "minLength": 1
      },
      "total_required": {
        "type": "string",
        "minLength": 1
      }
    }
    ```
    
    
    Additional properties allowed: `true`
    
