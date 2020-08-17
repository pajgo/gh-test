# Schema plan.update `plan.update`  [#/]


**Type**: object





**Constraints**:

```json
{
  "required": [
    "id"
  ],
  "minProperties": 2
}
```


Additional properties allowed: `true`


**Properties:**


 - **id**: `{reference}` *isRequired: `false`* 
    
    Reference: <a href="common.md#/definitions/planId">  (common#/definitions/planId)</a>
    
 - **alias**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1,
      "not": {
        "const": "free"
      }
    }
    ```
    
 - **description**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    
 - **hidden**: `{boolean}` *isRequired: `false`* 
 - **subscriptions**: `{object}` *isRequired: `false`* Subscriptions
    
    <a name="/properties/subscriptions"/>
    
    
    
    
    
    **Constraints**:
    
    ```json
    {
      "minProperties": 1
    }
    ```
    
    
    Additional properties allowed: `true`
    
    
    **Properties:**
    
    
     - **monthly**: `{reference}` *isRequired: `false`* 
        
        Reference: <a href="#/definitions/subscription">  (plan.update#/definitions/subscription)</a>
        
     - **yearly**: `{reference}` *isRequired: `false`* 
        
        Reference: <a href="#/definitions/subscription">  (plan.update#/definitions/subscription)</a>
        
    
 - **meta**: `{reference}` *isRequired: `false`* 
    
    Reference: <a href="plan.md#/definitions/meta">  (plan#/definitions/meta)</a>
    
 - **level**: `{reference}` *isRequired: `false`* 
    
    Reference: <a href="plan.md#/definitions/level">  (plan#/definitions/level)</a>
    


**Definitions**:

#### plan.update#/definitions/subscription Subscription





<a name="/definitions/subscription"/>





**Constraints**:

```json
{
  "minProperties": 1
}
```


Additional properties allowed: `true`


**Properties:**


 - **models**: `{integer}` *isRequired: `false`* 
    ```json
    {
      "minimum": 0
    }
    ```
    
 - **modelPrice**: `{number}` *isRequired: `false`* 
    ```json
    {
      "minimum": 0.01
    }
    ```
    
