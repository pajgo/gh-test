# Schema Plan information `response.plan.get`  [#/]


**Type**: object





Additional properties allowed: `true`


**Properties:**


 - **id**: `{reference}` *isRequired: `false`* 
    
    Reference: <a href="common.md#/definitions/planId">  (common#/definitions/planId)</a>
    
 - **state**: `{string}` *isRequired: `false`* 
    
    #TODO
    
 - **alias**: `{string}` *isRequired: `false`* 
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
    
 - **description**: `{string}` *isRequired: `false`* 
 - **hidden**: `{boolean}` *isRequired: `false`* 
 - **level**: `{reference}` *isRequired: `false`* 
    
    Reference: <a href="plan.md#/definitions/level">  (plan#/definitions/level)</a>
    
 - **subs**: `{array}` *isRequired: `false`* 
    
    <a name="/properties/subs"/>
    
    
    
    
    #### Items:
    
    
    Reference: <a href="response.subscription.md#">  (response.common.subscription#)</a>
    
 - **plan**: `{reference}` *isRequired: `false`* 
    
    Reference: <a href="response.plan.md#">  (response.common.plan#)</a>
    
 - **meta**: `{reference}` *isRequired: `false`* 
    
    Reference: <a href="plan.md#/definitions/meta">  (plan#/definitions/meta)</a>
    
 - **type**: `{reference}` *isRequired: `false`* 
    
    Reference: <a href="plan.md#/definitions/type">  (plan#/definitions/type)</a>
    
 - **month**: `{reference}` *isRequired: `false`* 
    
    Reference: <a href="data-types.md#/definitions/nullable-string">  (data-types#/definitions/nullable-string)</a>
    
 - **year**: `{reference}` *isRequired: `false`* 
    
    Reference: <a href="data-types.md#/definitions/nullable-string">  (data-types#/definitions/nullable-string)</a>
    
