# Schema Common definitions `common`  [#/]


**Type**: undefined





Additional properties allowed: `true`


**Definitions**:

#### common#/definitions/owner Payment owner


Identification of owner


Identification of owner

```json
{
  "minLength": 1
}
```

#### common#/definitions/chargeId Charge id


Identification of charge


Identification of charge

```json
{
  "format": "uuid"
}
```

#### common#/definitions/currency Currency name





<a name="/definitions/currency"/>





**Constraints**:

```json
{
  "required": [
    "currency",
    "value"
  ]
}
```


Additional properties allowed: `true`


**Properties:**


 - **currency**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 3,
      "maxLength": 3
    }
    ```
    
 - **value**: `{string}` *isRequired: `false`* 
    ```json
    {
      "pattern": "\\d{1,7}(\\.\\d{1,2})?$"
    }
    ```
    

#### common#/definitions/links Payment system provided links





<a name="/definitions/links"/>





Additional properties allowed: `true`


**Properties:**


 - **href**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    
 - **rel**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    
 - **method**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    

#### common#/definitions/term Term





<a name="/definitions/term"/>





**Constraints**:

```json
{
  "required": [
    "type",
    "max_billing_amount",
    "occurences",
    "amount_range",
    "buyer_editable"
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
    
 - **type**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    
 - **max_billing_amount**: `{reference}` *isRequired: `false`* 
    
    Reference: <a href="#/definitions/currency">  (common#/definitions/currency)</a>
    
 - **occurences**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    
 - **amount_range**: `{reference}` *isRequired: `false`* 
    
    Reference: <a href="#/definitions/currency">  (common#/definitions/currency)</a>
    
 - **buyer_editable**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    

#### common#/definitions/payment_definition Payment definition





<a name="/definitions/payment_definition"/>





**Constraints**:

```json
{
  "required": [
    "name",
    "type",
    "frequency_interval",
    "frequency",
    "cycles",
    "amount"
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
    
 - **type**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1,
      "enum": [
        "trial",
        "regular",
        "TRIAL",
        "REGULAR"
      ]
    }
    ```
    
 - **frequency_interval**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    
 - **frequency**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    
 - **cycles**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    
 - **amount**: `{reference}` *isRequired: `false`* 
    
    Reference: <a href="#/definitions/currency">  (common#/definitions/currency)</a>
    
 - **charge_models**: `{array}` *isRequired: `false`* Charge models
    
    <a name="/definitions/payment_definition/properties/charge_models"/>
    
    
    
    
    ###### Items:
    
    
    <a name="/definitions/payment_definition/properties/charge_models/items"/>
    
    
    
    
    
    **Constraints**:
    
    ```json
    {
      "required": [
        "type",
        "amount"
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
        
     - **type**: `{string}` *isRequired: `false`* 
        ```json
        {
          "minLength": 1
        }
        ```
        
     - **amount**: `{reference}` *isRequired: `false`* 
        
        Reference: <a href="#/definitions/currency">  (common#/definitions/currency)</a>
        
    

#### common#/definitions/merchant_preferences Merchant preferences





<a name="/definitions/merchant_preferences"/>





**Constraints**:

```json
{
  "required": [
    "cancel_url",
    "return_url"
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
    
 - **setup_fee**: `{reference}` *isRequired: `false`* 
    
    Reference: <a href="#/definitions/currency">  (common#/definitions/currency)</a>
    
 - **cancel_url**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    
 - **return_url**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    
 - **notify_url**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    
 - **max_fail_attempts**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    
 - **auto_bull_amount**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    
 - **initial_fail_amount_action**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    
 - **accepted_payment_type**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    
 - **char_set**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    

#### common#/definitions/agreement_details Agreement details





<a name="/definitions/agreement_details"/>





Additional properties allowed: `true`


**Properties:**


 - **outstanding_balance**: `{reference}` *isRequired: `false`* 
    
    Reference: <a href="#/definitions/currency">  (common#/definitions/currency)</a>
    
 - **cycles_remaining**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    
 - **cycles_completed**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    
 - **next_billing_date**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    
 - **last_payment_date**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    
 - **last_payment_amount**: `{reference}` *isRequired: `false`* 
    
    Reference: <a href="#/definitions/currency">  (common#/definitions/currency)</a>
    
 - **final_payment_date**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    
 - **failed_payment_count**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    

#### common#/definitions/payer Payer information





<a name="/definitions/payer"/>





**Constraints**:

```json
{
  "required": [
    "payment_method"
  ]
}
```


Additional properties allowed: `true`


**Properties:**


 - **payment_method**: `{string}` *isRequired: `false`* 
    ```json
    {
      "enum": [
        "credit_card",
        "bank",
        "paypal"
      ]
    }
    ```
    
 - **status**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    
 - **account_type**: `{string}` *isRequired: `false`* 
    ```json
    {
      "enum": [
        "business",
        "personal",
        "premier"
      ]
    }
    ```
    
 - **account_age**: `{string}` *isRequired: `false`* 
 - **funding_instruments**: `{array}` *isRequired: `false`* Funding instruments
    
    <a name="/definitions/payer/properties/funding_instruments"/>
    
    
    
    
    ###### Items:
    
    
    Reference: <a href="#/definitions/funding_instrument">  (common#/definitions/funding_instrument)</a>
    
 - **funding_option_id**: `{string}` *isRequired: `false`* 
 - **payer_info**: `{reference}` *isRequired: `false`* 
    
    Reference: <a href="#/definitions/payer_info">  (common#/definitions/payer_info)</a>
    

#### common#/definitions/funding_instrument Funding instruments





<a name="/definitions/funding_instrument"/>





Additional properties allowed: `true`


**Properties:**


 - **credit_card**: `{reference}` *isRequired: `false`* 
    
    Reference: <a href="#/definitions/credit_card">  (common#/definitions/credit_card)</a>
    
 - **credit_card_token**: `{reference}` *isRequired: `false`* 
    
    Reference: <a href="#/definitions/credit_card_token">  (common#/definitions/credit_card_token)</a>
    

#### common#/definitions/credit_card Credit card information





<a name="/definitions/credit_card"/>





**Constraints**:

```json
{
  "required": [
    "number",
    "type",
    "expire_month",
    "expire_year"
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
    
 - **payer_id**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    
 - **number**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    
 - **type**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    
 - **expire_month**: `{integer}` *isRequired: `false`* 
 - **expire_year**: `{integer}` *isRequired: `false`* 
 - **cvv2**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 3,
      "maxLength": 4
    }
    ```
    
 - **first_name**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    
 - **last_name**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    
 - **billing_address**: `{reference}` *isRequired: `false`* 
    
    Reference: <a href="#/definitions/address">  (common#/definitions/address)</a>
    
 - **external_customer_id**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    
 - **merchant_id**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    
 - **external_card_id**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    
 - **create_time**: `{string}` *isRequired: `false`* 
    ```json
    {
      "format": "date-time"
    }
    ```
    
 - **update_time**: `{string}` *isRequired: `false`* 
    ```json
    {
      "format": "date-time"
    }
    ```
    
 - **state**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    
 - **valid_until**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    

#### common#/definitions/credit_card_token Credit card token





<a name="/definitions/credit_card_token"/>





**Constraints**:

```json
{
  "required": [
    "credit_card_id"
  ]
}
```


Additional properties allowed: `true`


**Properties:**


 - **credit_card_id**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    
 - **payer_id**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    
 - **last4**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 4,
      "maxLength": 4
    }
    ```
    
 - **type**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    
 - **expire_year**: `{integer}` *isRequired: `false`* 
 - **expire_month**: `{integer}` *isRequired: `false`* 

#### common#/definitions/payer_info Payer information





<a name="/definitions/payer_info"/>





Additional properties allowed: `true`


**Properties:**


 - **email**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1,
      "maxLength": 127
    }
    ```
    
 - **salutation**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    
 - **first_name**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    
 - **middle_name**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    
 - **last_name**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    
 - **suffix**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    
 - **payer_id**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    
 - **phone**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    
 - **country_code**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    
 - **shipping_address**: `{reference}` *isRequired: `false`* 
    
    Reference: <a href="#/definitions/shipping_address">  (common#/definitions/shipping_address)</a>
    
 - **tax_id_type**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    
 - **tax_id**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    

#### common#/definitions/address Address





<a name="/definitions/address"/>





**Constraints**:

```json
{
  "required": [
    "line1",
    "city",
    "country_code"
  ]
}
```


Additional properties allowed: `true`


**Properties:**


 - **line1**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1,
      "maxLength": 100
    }
    ```
    
 - **line2**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1,
      "maxLength": 100
    }
    ```
    
 - **city**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1,
      "maxLength": 50
    }
    ```
    
 - **country_code**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1,
      "maxLength": 2
    }
    ```
    
 - **postal_code**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1,
      "maxLength": 20
    }
    ```
    
 - **state**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1,
      "maxLength": 100
    }
    ```
    
 - **phone**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1,
      "maxLength": 50
    }
    ```
    

#### common#/definitions/shipping_address Shipping address





*Could be allOf:*


 - 
    Reference: <a href="#/definitions/address">  (common#/definitions/address)</a>
    
 - ```json
    {
      "properties": {
        "recipient_name": {
          "type": "string",
          "minLength": 0
        },
        "type": {
          "type": "string",
          "minLength": 1
        }
      }
    }
    ```
    

#### common#/definitions/override_charge_model Override charge model





<a name="/definitions/override_charge_model"/>





**Constraints**:

```json
{
  "required": [
    "charge_id",
    "amount"
  ]
}
```


Additional properties allowed: `true`


**Properties:**


 - **charge_id**: `{string}` *isRequired: `false`* 
    ```json
    {
      "minLength": 1
    }
    ```
    
 - **amount**: `{reference}` *isRequired: `false`* 
    
    Reference: <a href="#/definitions/currency">  (common#/definitions/currency)</a>
    

#### common#/definitions/item Purchase item





<a name="/definitions/item"/>





**Constraints**:

```json
{
  "required": [
    "quantity",
    "name",
    "price",
    "currency"
  ]
}
```


Additional properties allowed: `true`


**Properties:**


 - **quantity**: `{string}` *isRequired: `false`* 
 - **name**: `{string}` *isRequired: `false`* 
 - **description**: `{string}` *isRequired: `false`* 
 - **price**: `{string}` *isRequired: `false`* 
 - **tax**: `{string}` *isRequired: `false`* 
 - **currency**: `{string}` *isRequired: `false`* 
 - **sku**: `{string}` *isRequired: `false`* 
 - **url**: `{string}` *isRequired: `false`* 
 - **category**: `{string}` *isRequired: `false`* 
    ```json
    {
      "enum": [
        "digital",
        "physical"
      ]
    }
    ```
    
 - **supplementary_data**: `{array}` *isRequired: `false`* Supplemetary data
    
    <a name="/definitions/item/properties/supplementary_data"/>
    
    
    
    
    ###### Items:
    
    
    Reference: <a href="#/definitions/kv">  (common#/definitions/kv)</a>
    
 - **postback_data**: `{array}` *isRequired: `false`* Postback data
    
    <a name="/definitions/item/properties/postback_data"/>
    
    
    
    
    ###### Items:
    
    
    Reference: <a href="#/definitions/kv">  (common#/definitions/kv)</a>
    

#### common#/definitions/kv KeyValue object





<a name="/definitions/kv"/>





**Constraints**:

```json
{
  "required": [
    "name",
    "value"
  ]
}
```


Additional properties allowed: `true`


**Properties:**


 - **name**: `{string}` *isRequired: `false`* 
 - **value**: `{string}` *isRequired: `false`* 

#### common#/definitions/planId Payment plan id





*Could be oneOf:*


 - ```json
    {
      "pattern": "^P-.+(\\|P-.+)?$"
    }
    ```
    
 - ```json
    {
      "const": "free"
    }
    ```
    

#### common#/definitions/paymentId Payment id


@TODO


@TODO

```json
{
  "minLength": 1,
  "pattern": "^PAYID-.+(\\|PAYID-.+)?"
}
```

#### common#/definitions/filter 


Search filter


<a name="/definitions/filter"/>


Search filter


Additional properties allowed: `true`


**Properties:**


 - **#multi**: `{object}` *isRequired: `false`* 
    
    <a name="/definitions/filter/properties/#multi"/>
    
    
    #multi query
    
    
    **Constraints**:
    
    ```json
    {
      "required": [
        "fields",
        "match"
      ]
    }
    ```
    
    
    Additional properties allowed: `true`
    
    
    **Properties:**
    
    
     - **fields**: `{array}` *isRequired: `false`* 
        
        <a name="/definitions/filter/properties/#multi/properties/fields"/>
        
        
        fields
        
        
        **Constraints**:
        
        ```json
        {
          "minItems": 1
        }
        ```
        
        ###### Items:
        
        ```json
        {
          "minLength": 1
        }
        ```
        
     - **match**: `{string}` *isRequired: `false`* 
        
        match
        
        ```json
        {
          "minLength": 1
        }
        ```
        
    


**Additional properties**:


*Could be oneOf:*


 - ```json
    {
      "minLength": 1
    }
    ```
    
 - 
    <a name="/definitions/filter/additionalProperties/oneOf/oneOf/1"/>
    
    
    
    
    
    **Constraints**:
    
    ```json
    {
      "minProperties": 1,
      "maxProperties": 2
    }
    ```
    
    
    Additional properties allowed: `true`
    
    
    **Pattern properties**:
    
    
     - ^(ne|eq|match)$: {string}
        ```json
        {
          "minLength": 1
        }
        ```
        
     - ^(gte|lte)$: {number}
     - ^(some)$: {array}
        
        <a name="/definitions/filter/additionalProperties/oneOf/oneOf/1/patternProperties/^(some)$"/>
        
        
        
        
        
        **Constraints**:
        
        ```json
        {
          "uniqueItems": true
        }
        ```
        
        ###### Items:
        
        ```json
        {
          "minLength": 1
        }
        ```
        
    
