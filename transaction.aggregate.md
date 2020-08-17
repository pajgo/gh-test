# Schema transaction.aggregate `transaction.aggregate`  [#/]


**Type**: object





**Constraints**:

```json
{
  "required": [
    "owners",
    "aggregate"
  ]
}
```


Additional properties allowed: `true`


**Properties:**


 - **owners**: `{array}` *isRequired: `false`* Transactions owners list
    
    <a name="/properties/owners"/>
    
    
    
    
    
    **Constraints**:
    
    ```json
    {
      "minItems": 1
    }
    ```
    
    #### Items:
    
    
    Reference: <a href="common.md#/definitions/owner">  (common#/definitions/owner)</a>
    
 - **filter**: `{reference}` *isRequired: `false`* 
    
    Reference: <a href="common.md#/definitions/filter">  (common#/definitions/filter)</a>
    
 - **aggregate**: `{object}` *isRequired: `false`* Aggregate param
    
    <a name="/properties/aggregate"/>
    
    
    
    
    
    **Constraints**:
    
    ```json
    {
      "minProperties": 1
    }
    ```
    
    
    Additional properties allowed: `true`
    
    
    **Additional properties**:
    
    ```json
    {
      "0": "s",
      "1": "t",
      "2": "r",
      "3": "i",
      "4": "n",
      "5": "g"
    }
    ```
    
    ```json
    {
      "0": "sum"
    }
    ```
    
