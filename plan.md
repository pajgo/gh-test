# Schema Common type: Payment plan object `plan`  [#/]


**Type**: object





**Constraints**:

```json
{
  "required": [
    "name",
    "description",
    "type",
    "payment_definitions"
  ]
}
```


Additional properties allowed: `true`


**Properties:**


 - **id**: `{string}` *isRequired: `false`* 
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
    ```json
    {
      "minLength": 1
    }
    ```
    
 - **type**: `{reference}` *isRequired: `false`* 
    
    Reference: <a href="#/definitions/type">  (#/definitions/type)</a>
    
 - **state**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    
 - **create_time**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    
 - **update_time**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    
 - **payment_definitions**: `{array}` *isRequired: `false`* Payment definitions
    
    <a name="/properties/payment_definitions"/>
    
    
    
    
    #### Items:
    
    
    Reference: <a href="common.md#/definitions/payment_definition">  (common#/definitions/payment_definition)</a>
    
 - **terms**: `{array}` *isRequired: `false`* Terms
    
    <a name="/properties/terms"/>
    
    
    
    
    #### Items:
    
    
    Reference: <a href="common.md#/definitions/term">  (common#/definitions/term)</a>
    
 - **merchant_preferences**: `{reference}` *isRequired: `false`* 
    
    Reference: <a href="common.md#/definitions/merchant_preferences">  (common#/definitions/merchant_preferences)</a>
    
 - **links**: `{array}` *isRequired: `false`* Payment provider links
    
    <a name="/properties/links"/>
    
    
    
    
    #### Items:
    
    
    Reference: <a href="common.md#/definitions/links">  (common#/definitions/links)</a>
    


**Definitions**:

#### plan#/definitions/meta Metadata





<a name="/definitions/meta"/>





Additional properties allowed: `true`


**Additional properties**:

```json
{
  "0": "#",
  "1": "/",
  "2": "d",
  "3": "e",
  "4": "f",
  "5": "i",
  "6": "n",
  "7": "i",
  "8": "t",
  "9": "i",
  "10": "o",
  "11": "n",
  "12": "s",
  "13": "/",
  "14": "f",
  "15": "e",
  "16": "a",
  "17": "t",
  "18": "u",
  "19": "r",
  "20": "e"
}
```

```json
{
  "local": true,
  "hash": "#/definitions/feature",
  "originalRef": "#/definitions/feature"
}
```

#### plan#/definitions/level 




#### plan#/definitions/feature Feature





<a name="/definitions/feature"/>





Additional properties allowed: `true`


**Properties:**


 - **description**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    
 - **type**: `{string}` *isRequired: `false`* 
    ```json
    {
      "enum": [
        "boolean",
        "number"
      ]
    }
    ```
    
 - **value**: `{number}` *isRequired: `false`* 
    
    0/1 for boolean and any other number to compare with for number type
    

#### plan#/definitions/type 




```json
{
  "minLength": 1,
  "enum": [
    "fixed",
    "infinite",
    "FIXED",
    "INFINITE"
  ]
}
```
