# Schema plan.create `plan.create`  [#/]


**Type**: object





**Constraints**:

```json
{
  "required": [
    "alias",
    "hidden",
    "subscriptions",
    "plan"
  ]
}
```


Additional properties allowed: `true`


**Properties:**


 - **hidden**: `{boolean}` *isRequired: `false`* 
 - **alias**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    
 - **level**: `{reference}` *isRequired: `false`* 
    
    Reference: <a href="plan.md#/definitions/level">  (plan#/definitions/level)</a>
    
 - **subscriptions**: `{array}` *isRequired: `false`* Subscriptions
    
    <a name="/properties/subscriptions"/>
    
    
    
    
    #### Items:
    
    
    Reference: <a href="subscription.md#">  (subscription#)</a>
    
 - **plan**: `{reference}` *isRequired: `false`* 
    
    Reference: <a href="plan.md#">  (plan#)</a>
    
 - **meta**: `{reference}` *isRequired: `false`* 
    
    Reference: <a href="plan.md#/definitions/meta">  (plan#/definitions/meta)</a>
    
