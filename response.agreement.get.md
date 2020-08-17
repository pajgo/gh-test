# Schema agreement.get response `response.agreement.get`  [#/]


**Type**: object





Additional properties allowed: `true`


**Properties:**


 - **id**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 4
    }
    ```
    
 - **owner**: `{reference}` *isRequired: `false`* 
    
    Reference: <a href="common.md#/definitions/owner">  (common#/definitions/owner)</a>
    
 - **state**: `{string}` *isRequired: `false`* 
    
    #TODO
    
 - **token**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 10
    }
    ```
    
 - **plan**: `{reference}` *isRequired: `false`* 
    
    Reference: <a href="common.md#/definitions/planId">  (common#/definitions/planId)</a>
    
 - **agreement**: `{reference}` *isRequired: `false`* 
    
    Reference: <a href="response.agreement.md#">  (response.common.agreement#)</a>
    
