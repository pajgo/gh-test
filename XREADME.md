<a name="top"></a>
# Сервис трям8.3.1



- [Agreement](#Agreement)
	- [Bill agreement](#Bill-agreement)
	- [Changes agreement state](#Changes-agreement-state)
	- [Creates agreement for approval](#Creates-agreement-for-approval)
	- [Executes agreement for approval](#Executes-agreement-for-approval)
	- [Get Agreement information](#Get-Agreement-information)
	- [List Agreements](#List-Agreements)
	- [Returns agreement for user](#Returns-agreement-for-user)
	
- [Plan](#Plan)
	- [Retrieves Plan by its Id.](#Retrieves-Plan-by-its-Id.)
	
- [SchemaDefinitions](#SchemaDefinitions)
	- [[response.common] Agreement object](#[response.common]-Agreement-object)
	- [agreement.get response](#agreement.get-response)
	- [Common definitions](#Common-definitions)
	- [Common type: Agreement object](#Common-type:-Agreement-object)
	- [Common type: Payment plan object](#Common-type:-Payment-plan-object)
	- [Common type: Payment plan response object](#Common-type:-Payment-plan-response-object)
	- [Common type: Subscription response object](#Common-type:-Subscription-response-object)
	- [data-types](#data-types)
	

# <a name='Agreement'></a> Agreement
## <a name='Bill-agreement'></a> Bill agreement
<p>Bills requested agreement</p>

Исходный файл [src/actions/agreement/bill.js](src/actions/agreement/bill.js).
```
AMQP,INTERNAL agreement.bill
```


### Request schema

`{object}` 

Additional properties allowed: `true`


Properties:


 - **agreement**: 
    `{string}`
 - **nextCycle**: 
    `{integer}`
 - **username**: 
    `{string}`


### Response schema:

`{string}`
String as status of the operation




**[⬆ Back to Top](#top)**
## <a name='Changes-agreement-state'></a> Changes agreement state
<p>Change currently used agreement for {owner} to {state}</p>

Исходный файл [src/actions/agreement/state.js](src/actions/agreement/state.js).
```
AMQP &lt;prefix&gt;.agreement.state
```


### Request schema

`{object}` 
Constraints: `required`: `owner,state`

Additional properties allowed: `true`


Properties:


 - **owner**: 
    <a href="#common--/definitions/owner">(common#/definitions/owner)</a>
 - **state**: 
    `{string}`Constraints: `enum`: `suspend,reactivate,cancel`
 - **note**: 
    `{string}`Constraints: `minLength`: `1`


### Response schema:

`{string}`Constraints: `enum`: `suspend,reactivate,cancel`




**[⬆ Back to Top](#top)**
## <a name='Creates-agreement-for-approval'></a> Creates agreement for approval
<p>Creates agreement for approval through paypal and sends link back</p>

Исходный файл [src/actions/agreement/create.js](src/actions/agreement/create.js).
```
AMQP &lt;prefix&gt;.agreement.create
```


### Request schema

`{object}` 
Constraints: `required`: `owner,agreement`

Additional properties allowed: `true`


Properties:


 - **owner**: 
    <a href="#common--/definitions/owner">(common#/definitions/owner)</a>
 - **agreement**: 
    
    *Could be allOf:*
    
    
     - <a href="#agreement--">(agreement#)</a>
     - `{object}` <a name="--/properties/agreement/allOf/1"/>
        
        Additional properties allowed: `true`
        
        
        Properties:
        
        
         - **plan**: 
            `{object}` <a name="--/properties/agreement/allOf/1/properties/plan"/>
            Constraints: `required`: `id`
            
            Additional properties allowed: `true`
            
            
            Properties:
            
            
             - **id**: 
                `{string}`Constraints: `pattern`: `^P-[A-Z0-9]+$`
            
        
    
 - **trialDiscount**: 
    `{integer}`Constraints: `minimum`: `0`, `maximum`: `100`, `default`: `0`
 - **trialCycle**: 
    `{integer}`Constraints: `minimum`: `1`, `default`: `12`


### Response schema:

`{object}` 

Created agreement


Additional properties allowed: `true`


Properties:


 - **token**: 
    `{string}`Constraints: `minLength`: `1`
 - **url**: 
    `{string}`Constraints: `minLength`: `1`
 - **agreement**: 
    <a href="#response.common.agreement--">(response.common.agreement#)</a>





**[⬆ Back to Top](#top)**
## <a name='Executes-agreement-for-approval'></a> Executes agreement for approval
<p>Creates agreement for approval through paypal and sends link back</p>

Исходный файл [src/actions/agreement/execute.js](src/actions/agreement/execute.js).
```
AMQP &lt;prefix&gt;.agreement.execute
```


### Request schema

`{object}` 
Constraints: `required`: `token`

Additional properties allowed: `true`


Properties:


 - **token**: 
    `{string}`Constraints: `minLength`: `1`


### Response schema:

<a href="#response.common.agreement--">agreement.execute response`response.agreement.execute` (response.common.agreement#)</a>




**[⬆ Back to Top](#top)**
## <a name='Get-Agreement-information'></a> Get Agreement information
<p>Returns agreement information</p>

Исходный файл [src/actions/agreement/get.js](src/actions/agreement/get.js).
```
AMQP &lt;prefix&gt;.agreement.get
```


### Request schema

`{object}` 
Constraints: `required`: `id`

Additional properties allowed: `true`


Properties:


 - **id**: 
    `{string}`Constraints: `minLength`: `1`
 - **owner**: 
    <a href="#common--/definitions/owner">(common#/definitions/owner)</a>


### Response schema:

`{object}` 

Additional properties allowed: `true`


Properties:


 - **id**: 
    `{string}`Constraints: `minLength`: `4`
 - **owner**: 
    <a href="#common--/definitions/owner">(common#/definitions/owner)</a>
 - **state**: 
    `{string}`
    #TODO
 - **token**: 
    `{string}`Constraints: `minLength`: `10`
 - **plan**: 
    <a href="#common--/definitions/planId">(common#/definitions/planId)</a>
 - **agreement**: 
    <a href="#response.common.agreement--">(response.common.agreement#)</a>





**[⬆ Back to Top](#top)**
## <a name='List-Agreements'></a> List Agreements
<p>Returns list of the agreements information</p>

Исходный файл [src/actions/agreement/list.js](src/actions/agreement/list.js).
```
AMQP &lt;prefix&gt;.agreement.list
```


### Request schema

`{object}` 

Additional properties allowed: `true`


Properties:


 - **offset**: 
    `{integer}`Constraints: `minimum`: `0`
 - **limit**: 
    `{integer}`Constraints: `minimum`: `1`, `maximum`: `100`
 - **filter**: 
    <a href="#common--/definitions/filter">(common#/definitions/filter)</a>
 - **criteria**: 
    `{string}`Constraints: `minLength`: `1`
 - **order**: 
    `{string}`Constraints: `enum`: `ASC,DESC`
 - **owner**: 
    <a href="#common--/definitions/owner">(common#/definitions/owner)</a>


### Response schema:

`{object}` 
Constraints: `required`: `items,cursor,page,pages`

Additional properties allowed: `true`


Properties:


 - **items**: 
    `{array}` <a name="--/properties/items"/>
    
    Each item should be:
    
    <a href="#response.agreement.get--">(response.agreement.get#)</a>
 - **cursor**: 
    `{number}`
 - **page**: 
    `{number}`
 - **pages**: 
    `{number}`





**[⬆ Back to Top](#top)**
## <a name='Returns-agreement-for-user'></a> Returns agreement for user
<p>Agreement information for user</p>

Исходный файл [src/actions/agreement/forUser.js](src/actions/agreement/forUser.js).
```
AMQP &lt;prefix&gt;.agreement.forUser
```


### Request schema

`{object}` 
Constraints: `required`: `user`

Additional properties allowed: `true`


Properties:


 - **user**: 
    `{string}`Constraints: `minLength`: `1`


### Response schema:

<a href="#response.agreement.get--">agreement.forUser response`response.agreement.forUser` (response.agreement.get#)</a>




**[⬆ Back to Top](#top)**
# <a name='Plan'></a> Plan
## <a name='Retrieves-Plan-by-its-Id.'></a> Retrieves Plan by its Id.
<p>Retrieves plan or parent plan by its id.</p>

Исходный файл [src/actions/plan/get.js](src/actions/plan/get.js).
```
AMQP &lt;prefix&gt;.plan.get
```


### Request schema


*Could be anyOf:*


 - `{string}`Constraints: `minLength`: `1`, `maxLength`: `100`
 - `{object}` 
    Constraints: `required`: `id`
    
    Plan object
    
    
    Additional properties allowed: `true`
    
    
    Properties:
    
    
     - **id**: 
        `{string}`Constraints: `minLength`: `1`, `maxLength`: `100`
     - **fetchParent**: 
        `{boolean}`
    


### Response schema:

`{object}` 

Additional properties allowed: `true`


Properties:


 - **id**: 
    <a href="#common--/definitions/planId">(common#/definitions/planId)</a>
 - **state**: 
    `{string}`
    #TODO
 - **alias**: 
    `{string}`Constraints: `minLength`: `1`
 - **name**: 
    `{string}`Constraints: `minLength`: `1`
 - **description**: 
    `{string}`
 - **hidden**: 
    `{boolean}`
 - **level**: 
    <a href="#plan--/definitions/level">(plan#/definitions/level)</a>
 - **subs**: 
    `{array}` <a name="--/properties/subs"/>
    
    Each item should be:
    
    <a href="#response.common.subscription--">(response.common.subscription#)</a>
 - **plan**: 
    <a href="#response.common.plan--">(response.common.plan#)</a>
 - **meta**: 
    <a href="#plan--/definitions/meta">(plan#/definitions/meta)</a>
 - **type**: 
    <a href="#plan--/definitions/type">(plan#/definitions/type)</a>
 - **month**: 
    <a href="#data-types--/definitions/nullable-string">(data-types#/definitions/nullable-string)</a>
 - **year**: 
    <a href="#data-types--/definitions/nullable-string">(data-types#/definitions/nullable-string)</a>





**[⬆ Back to Top](#top)**
# <a name='SchemaDefinitions'></a> SchemaDefinitions
## <a name='[response.common]-Agreement-object'></a> [response.common] Agreement object
Agreement response object structure

Исходный файл [response/agreement.json](response/agreement.json).
```
SCHEMA response.common.agreement
```



### Schema

`{object}` 

Agreement response object structure


Additional properties allowed: `true`


Properties:


 - **t**: 
    `{integer}`
    #TODO FINDOUT Something internal
 - **httpStatusCode**: 
    `{integer}`
 - **id**: 
    `{string}`Constraints: `minLength`: `1`
 - **state**: 
    `{string}`Constraints: `minLength`: `1`
 - **name**: 
    `{string}`Constraints: `minLength`: `1`
 - **description**: 
    `{string}`Constraints: `minLength`: `1`
 - **start_date**: 
    `{string}`Constraints: `minLength`: `1`
 - **agreement_details**: 
    <a href="#common--/definitions/agreement_details">(common#/definitions/agreement_details)</a>
 - **payer**: 
    <a href="#common--/definitions/payer">(common#/definitions/payer)</a>
 - **shipping_address**: 
    <a href="#common--/definitions/address">(common#/definitions/address)</a>
 - **override_merchant_preferences**: 
    <a href="#common--/definitions/merchant_preferences">(common#/definitions/merchant_preferences)</a>
 - **override_charge_models**: 
    `{array}` <a name="--/properties/override_charge_models"/>
    
    Each item should be:
    
    <a href="#common--/definitions/override_charge_model">(common#/definitions/override_charge_model)</a>
 - **plan**: 
    <a href="#response.common.plan--">(response.common.plan#)</a>
 - **create_time**: 
    `{string}`Constraints: `minLength`: `1`
 - **update_time**: 
    `{string}`Constraints: `minLength`: `1`
 - **links**: 
    `{array}` <a name="--/properties/links"/>
    
    Each item should be:
    
    <a href="#common--/definitions/links">(common#/definitions/links)</a>


**[⬆ Back to Top](#top)**
## <a name='agreement.get-response'></a> agreement.get response
Исходный файл [response/agreement/get.json](response/agreement/get.json).
```
SCHEMA response.agreement.get
```



### Schema

`{object}` 

Additional properties allowed: `true`


Properties:


 - **id**: 
    `{string}`Constraints: `minLength`: `4`
 - **owner**: 
    <a href="#common--/definitions/owner">(common#/definitions/owner)</a>
 - **state**: 
    `{string}`
    #TODO
 - **token**: 
    `{string}`Constraints: `minLength`: `10`
 - **plan**: 
    <a href="#common--/definitions/planId">(common#/definitions/planId)</a>
 - **agreement**: 
    <a href="#response.common.agreement--">(response.common.agreement#)</a>


**[⬆ Back to Top](#top)**
## <a name='Common-definitions'></a> Common definitions
Исходный файл [common.json](common.json).
```
SCHEMA common
```



### Schema



**Definitions**:


 - **common#/definitions/owner**
    `{string}`Constraints: `minLength`: `1`
    Identification of owner
 - **common#/definitions/chargeId**
    `{string}`Constraints: `format`: `uuid`
    Identification of charge
 - **common#/definitions/currency**
    `{object}` <a name="common--/definitions/currency"/>
    Constraints: `required`: `currency,value`
    
    Additional properties allowed: `true`
    
    
    Properties:
    
    
     - **currency**: 
        `{string}`Constraints: `minLength`: `3`, `maxLength`: `3`
     - **value**: 
        `{string}`Constraints: `pattern`: `\d{1,7}(\.\d{1,2})?$`
    
 - **common#/definitions/links**
    `{object}` <a name="common--/definitions/links"/>
    
    Additional properties allowed: `true`
    
    
    Properties:
    
    
     - **href**: 
        `{string}`Constraints: `minLength`: `1`
     - **rel**: 
        `{string}`Constraints: `minLength`: `1`
     - **method**: 
        `{string}`Constraints: `minLength`: `1`
    
 - **common#/definitions/term**
    `{object}` <a name="common--/definitions/term"/>
    Constraints: `required`: `type,max_billing_amount,occurences,amount_range,buyer_editable`
    
    Additional properties allowed: `true`
    
    
    Properties:
    
    
     - **id**: 
        `{string}`Constraints: `minLength`: `1`
     - **type**: 
        `{string}`Constraints: `minLength`: `1`
     - **max_billing_amount**: 
        <a href="#--/definitions/currency">(common#/definitions/currency)</a>
     - **occurences**: 
        `{string}`Constraints: `minLength`: `1`
     - **amount_range**: 
        <a href="#--/definitions/currency">(common#/definitions/currency)</a>
     - **buyer_editable**: 
        `{string}`Constraints: `minLength`: `1`
    
 - **common#/definitions/payment_definition**
    `{object}` <a name="common--/definitions/payment_definition"/>
    Constraints: `required`: `name,type,frequency_interval,frequency,cycles,amount`
    
    Additional properties allowed: `true`
    
    
    Properties:
    
    
     - **id**: 
        `{string}`Constraints: `minLength`: `1`
     - **name**: 
        `{string}`Constraints: `minLength`: `1`
     - **type**: 
        `{string}`Constraints: `minLength`: `1`, `enum`: `trial,regular,TRIAL,REGULAR`
     - **frequency_interval**: 
        `{string}`Constraints: `minLength`: `1`
     - **frequency**: 
        `{string}`Constraints: `minLength`: `1`
     - **cycles**: 
        `{string}`Constraints: `minLength`: `1`
     - **amount**: 
        <a href="#--/definitions/currency">(common#/definitions/currency)</a>
     - **charge_models**: 
        `{array}` <a name="common--/definitions/payment_definition/properties/charge_models"/>
        
        Each item should be:
        
        `{object}` <a name="common--/definitions/payment_definition/properties/charge_models/items"/>
        Constraints: `required`: `type,amount`
        
        Additional properties allowed: `true`
        
        
        Properties:
        
        
         - **id**: 
            `{string}`Constraints: `minLength`: `1`
         - **type**: 
            `{string}`Constraints: `minLength`: `1`
         - **amount**: 
            <a href="#--/definitions/currency">(common#/definitions/currency)</a>
        
    
 - **common#/definitions/merchant_preferences**
    `{object}` <a name="common--/definitions/merchant_preferences"/>
    Constraints: `required`: `cancel_url,return_url`
    
    Additional properties allowed: `true`
    
    
    Properties:
    
    
     - **id**: 
        `{string}`Constraints: `minLength`: `1`
     - **setup_fee**: 
        <a href="#--/definitions/currency">(common#/definitions/currency)</a>
     - **cancel_url**: 
        `{string}`Constraints: `minLength`: `1`
     - **return_url**: 
        `{string}`Constraints: `minLength`: `1`
     - **notify_url**: 
        `{string}`Constraints: `minLength`: `1`
     - **max_fail_attempts**: 
        `{string}`Constraints: `minLength`: `1`
     - **auto_bull_amount**: 
        `{string}`Constraints: `minLength`: `1`
     - **initial_fail_amount_action**: 
        `{string}`Constraints: `minLength`: `1`
     - **accepted_payment_type**: 
        `{string}`Constraints: `minLength`: `1`
     - **char_set**: 
        `{string}`Constraints: `minLength`: `1`
    
 - **common#/definitions/agreement_details**
    `{object}` <a name="common--/definitions/agreement_details"/>
    
    Additional properties allowed: `true`
    
    
    Properties:
    
    
     - **outstanding_balance**: 
        <a href="#--/definitions/currency">(common#/definitions/currency)</a>
     - **cycles_remaining**: 
        `{string}`Constraints: `minLength`: `1`
     - **cycles_completed**: 
        `{string}`Constraints: `minLength`: `1`
     - **next_billing_date**: 
        `{string}`Constraints: `minLength`: `1`
     - **last_payment_date**: 
        `{string}`Constraints: `minLength`: `1`
     - **last_payment_amount**: 
        <a href="#--/definitions/currency">(common#/definitions/currency)</a>
     - **final_payment_date**: 
        `{string}`Constraints: `minLength`: `1`
     - **failed_payment_count**: 
        `{string}`Constraints: `minLength`: `1`
    
 - **common#/definitions/payer**
    `{object}` <a name="common--/definitions/payer"/>
    Constraints: `required`: `payment_method`
    
    Additional properties allowed: `true`
    
    
    Properties:
    
    
     - **payment_method**: 
        `{string}`Constraints: `enum`: `credit_card,bank,paypal`
     - **status**: 
        `{string}`Constraints: `minLength`: `1`
     - **account_type**: 
        `{string}`Constraints: `enum`: `business,personal,premier`
     - **account_age**: 
        `{string}`
     - **funding_instruments**: 
        `{array}` <a name="common--/definitions/payer/properties/funding_instruments"/>
        
        Each item should be:
        
        <a href="#--/definitions/funding_instrument">(common#/definitions/funding_instrument)</a>
     - **funding_option_id**: 
        `{string}`
     - **payer_info**: 
        <a href="#--/definitions/payer_info">(common#/definitions/payer_info)</a>
    
 - **common#/definitions/funding_instrument**
    `{object}` <a name="common--/definitions/funding_instrument"/>
    
    Additional properties allowed: `true`
    
    
    Properties:
    
    
     - **credit_card**: 
        <a href="#--/definitions/credit_card">(common#/definitions/credit_card)</a>
     - **credit_card_token**: 
        <a href="#--/definitions/credit_card_token">(common#/definitions/credit_card_token)</a>
    
 - **common#/definitions/credit_card**
    `{object}` <a name="common--/definitions/credit_card"/>
    Constraints: `required`: `number,type,expire_month,expire_year`
    
    Additional properties allowed: `true`
    
    
    Properties:
    
    
     - **id**: 
        `{string}`Constraints: `minLength`: `1`
     - **payer_id**: 
        `{string}`Constraints: `minLength`: `1`
     - **number**: 
        `{string}`Constraints: `minLength`: `1`
     - **type**: 
        `{string}`Constraints: `minLength`: `1`
     - **expire_month**: 
        `{integer}`
     - **expire_year**: 
        `{integer}`
     - **cvv2**: 
        `{string}`Constraints: `minLength`: `3`, `maxLength`: `4`
     - **first_name**: 
        `{string}`Constraints: `minLength`: `1`
     - **last_name**: 
        `{string}`Constraints: `minLength`: `1`
     - **billing_address**: 
        <a href="#--/definitions/address">(common#/definitions/address)</a>
     - **external_customer_id**: 
        `{string}`Constraints: `minLength`: `1`
     - **merchant_id**: 
        `{string}`Constraints: `minLength`: `1`
     - **external_card_id**: 
        `{string}`Constraints: `minLength`: `1`
     - **create_time**: 
        `{string}`Constraints: `format`: `date-time`
     - **update_time**: 
        `{string}`Constraints: `format`: `date-time`
     - **state**: 
        `{string}`Constraints: `minLength`: `1`
     - **valid_until**: 
        `{string}`Constraints: `minLength`: `1`
    
 - **common#/definitions/credit_card_token**
    `{object}` <a name="common--/definitions/credit_card_token"/>
    Constraints: `required`: `credit_card_id`
    
    Additional properties allowed: `true`
    
    
    Properties:
    
    
     - **credit_card_id**: 
        `{string}`Constraints: `minLength`: `1`
     - **payer_id**: 
        `{string}`Constraints: `minLength`: `1`
     - **last4**: 
        `{string}`Constraints: `minLength`: `4`, `maxLength`: `4`
     - **type**: 
        `{string}`Constraints: `minLength`: `1`
     - **expire_year**: 
        `{integer}`
     - **expire_month**: 
        `{integer}`
    
 - **common#/definitions/payer_info**
    `{object}` <a name="common--/definitions/payer_info"/>
    
    Additional properties allowed: `true`
    
    
    Properties:
    
    
     - **email**: 
        `{string}`Constraints: `minLength`: `1`, `maxLength`: `127`
     - **salutation**: 
        `{string}`Constraints: `minLength`: `1`
     - **first_name**: 
        `{string}`Constraints: `minLength`: `1`
     - **middle_name**: 
        `{string}`Constraints: `minLength`: `1`
     - **last_name**: 
        `{string}`Constraints: `minLength`: `1`
     - **suffix**: 
        `{string}`Constraints: `minLength`: `1`
     - **payer_id**: 
        `{string}`Constraints: `minLength`: `1`
     - **phone**: 
        `{string}`Constraints: `minLength`: `1`
     - **country_code**: 
        `{string}`Constraints: `minLength`: `1`
     - **shipping_address**: 
        <a href="#--/definitions/shipping_address">(common#/definitions/shipping_address)</a>
     - **tax_id_type**: 
        `{string}`Constraints: `minLength`: `1`
     - **tax_id**: 
        `{string}`Constraints: `minLength`: `1`
    
 - **common#/definitions/address**
    `{object}` <a name="common--/definitions/address"/>
    Constraints: `required`: `line1,city,country_code`
    
    Additional properties allowed: `true`
    
    
    Properties:
    
    
     - **line1**: 
        `{string}`Constraints: `minLength`: `1`, `maxLength`: `100`
     - **line2**: 
        `{string}`Constraints: `minLength`: `1`, `maxLength`: `100`
     - **city**: 
        `{string}`Constraints: `minLength`: `1`, `maxLength`: `50`
     - **country_code**: 
        `{string}`Constraints: `minLength`: `1`, `maxLength`: `2`
     - **postal_code**: 
        `{string}`Constraints: `minLength`: `1`, `maxLength`: `20`
     - **state**: 
        `{string}`Constraints: `minLength`: `1`, `maxLength`: `100`
     - **phone**: 
        `{string}`Constraints: `minLength`: `1`, `maxLength`: `50`
    
 - **common#/definitions/shipping_address**
    
    *Could be allOf:*
    
    
     - <a href="#--/definitions/address">(common#/definitions/address)</a>
     - Constraints: `properties`: `[object Object]`
    
 - **common#/definitions/override_charge_model**
    `{object}` <a name="common--/definitions/override_charge_model"/>
    Constraints: `required`: `charge_id,amount`
    
    Additional properties allowed: `true`
    
    
    Properties:
    
    
     - **charge_id**: 
        `{string}`Constraints: `minLength`: `1`
     - **amount**: 
        <a href="#--/definitions/currency">(common#/definitions/currency)</a>
    
 - **common#/definitions/item**
    `{object}` <a name="common--/definitions/item"/>
    Constraints: `required`: `quantity,name,price,currency`
    
    Additional properties allowed: `true`
    
    
    Properties:
    
    
     - **quantity**: 
        `{string}`
     - **name**: 
        `{string}`
     - **description**: 
        `{string}`
     - **price**: 
        `{string}`
     - **tax**: 
        `{string}`
     - **currency**: 
        `{string}`
     - **sku**: 
        `{string}`
     - **url**: 
        `{string}`
     - **category**: 
        `{string}`Constraints: `enum`: `digital,physical`
     - **supplementary_data**: 
        `{array}` <a name="common--/definitions/item/properties/supplementary_data"/>
        
        Each item should be:
        
        <a href="#--/definitions/kv">(common#/definitions/kv)</a>
     - **postback_data**: 
        `{array}` <a name="common--/definitions/item/properties/postback_data"/>
        
        Each item should be:
        
        <a href="#--/definitions/kv">(common#/definitions/kv)</a>
    
 - **common#/definitions/kv**
    `{object}` <a name="common--/definitions/kv"/>
    Constraints: `required`: `name,value`
    
    Additional properties allowed: `true`
    
    
    Properties:
    
    
     - **name**: 
        `{string}`
     - **value**: 
        `{string}`
    
 - **common#/definitions/planId**
    
    *Could be oneOf:*
    
    
     - Constraints: `pattern`: `^P-.+(\|P-.+)?$`
     - Constraints: `const`: `free`
    
 - **common#/definitions/paymentId**
    `{string}`Constraints: `minLength`: `1`, `pattern`: `^PAYID-.+(\|PAYID-.+)?`
    @TODO
 - **common#/definitions/filter**
    `{object}` <a name="common--/definitions/filter"/>
    
    Search filter
    
    
    Additional properties allowed: `true`
    
    
    Properties:
    
    
     - **#multi**: 
        `{object}` <a name="common--/definitions/filter/properties/--multi"/>
        Constraints: `required`: `fields,match`
        
        #multi query
        
        
        Additional properties allowed: `true`
        
        
        Properties:
        
        
         - **fields**: 
            `{array}` <a name="common--/definitions/filter/properties/--multi/properties/fields"/>
            Constraints: `minItems`: `1`
            
            fields
            
            
            Each item should be:
            
            `{string}`Constraints: `minLength`: `1`
         - **match**: 
            `{string}`Constraints: `minLength`: `1`
            match
        
    
    
    Additional properties:
    
    
    *Could be oneOf:*
    
    
     - `{string}`Constraints: `minLength`: `1`
     - `{object}` <a name="common--/definitions/filter/additionalProperties/oneOf/oneOf/1"/>
        Constraints: `minProperties`: `1`, `maxProperties`: `2`
        
        Additional properties allowed: `true`
        
        
        **Pattern properties**:
        
        
         - ^(ne|eq|match)$: {string}
            `{string}`Constraints: `minLength`: `1`
         - ^(gte|lte)$: {number}
            `{number}`
         - ^(some)$: {array}
            `{array}` <a name="common--/definitions/filter/additionalProperties/oneOf/oneOf/1/patternProperties/^(some)$"/>
            Constraints: `uniqueItems`: `true`
            
            Each item should be:
            
            `{string}`Constraints: `minLength`: `1`
        
    


**[⬆ Back to Top](#top)**
## <a name='Common-type:-Agreement-object'></a> Common type: Agreement object
Agreement object structure

Исходный файл [agreement.json](agreement.json).
```
SCHEMA agreement
```



### Schema

`{object}` 
Constraints: `required`: `name,description,payer,plan`

Agreement object structure


Additional properties allowed: `true`


Properties:


 - **id**: 
    `{string}`Constraints: `minLength`: `1`
 - **state**: 
    `{string}`Constraints: `minLength`: `1`
 - **name**: 
    `{string}`Constraints: `minLength`: `1`
 - **description**: 
    `{string}`Constraints: `minLength`: `1`
 - **start_date**: 
    `{string}`Constraints: `minLength`: `1`
 - **agreement_details**: 
    <a href="#common--/definitions/agreement_details">(common#/definitions/agreement_details)</a>
 - **payer**: 
    <a href="#common--/definitions/payer">(common#/definitions/payer)</a>
 - **shipping_address**: 
    <a href="#common--/definitions/address">(common#/definitions/address)</a>
 - **override_merchant_preferences**: 
    <a href="#common--/definitions/merchant_preferences">(common#/definitions/merchant_preferences)</a>
 - **override_charge_models**: 
    `{array}` <a name="--/properties/override_charge_models"/>
    
    Each item should be:
    
    <a href="#common--/definitions/override_charge_model">(common#/definitions/override_charge_model)</a>
 - **plan**: 
    
    *Could be oneOf:*
    
    
     - <a href="#plan.create--">(plan.create#)</a>
     - `{object}` <a name="--/properties/plan/oneOf/1"/>
        Constraints: `required`: `id`
        
        Additional properties allowed: `true`
        
        
        Properties:
        
        
         - **id**: 
            `{string}`Constraints: `minLength`: `1`
        
    
 - **create_time**: 
    `{string}`Constraints: `minLength`: `1`
 - **update_time**: 
    `{string}`Constraints: `minLength`: `1`
 - **links**: 
    `{array}` <a name="--/properties/links"/>
    
    Each item should be:
    
    <a href="#common--/definitions/links">(common#/definitions/links)</a>


**[⬆ Back to Top](#top)**
## <a name='Common-type:-Payment-plan-object'></a> Common type: Payment plan object
Исходный файл [plan.json](plan.json).
```
SCHEMA plan
```



### Schema

`{object}` 
Constraints: `required`: `name,description,type,payment_definitions`

Additional properties allowed: `true`


Properties:


 - **id**: 
    `{string}`Constraints: `minLength`: `1`
 - **name**: 
    `{string}`Constraints: `minLength`: `1`
 - **description**: 
    `{string}`Constraints: `minLength`: `1`
 - **type**: 
    <a href="#--/definitions/type">(#/definitions/type)</a>
 - **state**: 
    `{string}`Constraints: `minLength`: `1`
 - **create_time**: 
    `{string}`Constraints: `minLength`: `1`
 - **update_time**: 
    `{string}`Constraints: `minLength`: `1`
 - **payment_definitions**: 
    `{array}` <a name="--/properties/payment_definitions"/>
    
    Each item should be:
    
    <a href="#common--/definitions/payment_definition">(common#/definitions/payment_definition)</a>
 - **terms**: 
    `{array}` <a name="--/properties/terms"/>
    
    Each item should be:
    
    <a href="#common--/definitions/term">(common#/definitions/term)</a>
 - **merchant_preferences**: 
    <a href="#common--/definitions/merchant_preferences">(common#/definitions/merchant_preferences)</a>
 - **links**: 
    `{array}` <a name="--/properties/links"/>
    
    Each item should be:
    
    <a href="#common--/definitions/links">(common#/definitions/links)</a>


**Definitions**:


 - **plan#/definitions/meta**
    `{object}` <a name="plan--/definitions/meta"/>
    
    Additional properties allowed: `true`
    
    
    Additional properties:
    
    Constraints: `0`: `#`, `1`: `/`, `2`: `d`, `3`: `e`, `4`: `f`, `5`: `i`, `6`: `n`, `7`: `i`, `8`: `t`, `9`: `i`, `10`: `o`, `11`: `n`, `12`: `s`, `13`: `/`, `14`: `f`, `15`: `e`, `16`: `a`, `17`: `t`, `18`: `u`, `19`: `r`, `20`: `e`
    Constraints: `local`: `true`, `hash`: `#/definitions/feature`, `originalRef`: `#/definitions/feature`
 - **plan#/definitions/level**
    `{integer}`
 - **plan#/definitions/feature**
    `{object}` <a name="plan--/definitions/feature"/>
    
    Additional properties allowed: `true`
    
    
    Properties:
    
    
     - **description**: 
        `{string}`Constraints: `minLength`: `1`
     - **type**: 
        `{string}`Constraints: `enum`: `boolean,number`
     - **value**: 
        `{number}`
        0/1 for boolean and any other number to compare with for number type
    
 - **plan#/definitions/type**
    `{string}`Constraints: `minLength`: `1`, `enum`: `fixed,infinite,FIXED,INFINITE`


**[⬆ Back to Top](#top)**
## <a name='Common-type:-Payment-plan-response-object'></a> Common type: Payment plan response object
Исходный файл [response/plan.json](response/plan.json).
```
SCHEMA response.common.plan
```



### Schema

`{object}` 

Additional properties allowed: `true`


Properties:


 - **id**: 
    `{string}`Constraints: `minLength`: `1`
 - **name**: 
    `{string}`Constraints: `minLength`: `1`
 - **description**: 
    `{string}`Constraints: `minLength`: `1`
 - **hidden**: 
    `{boolean}`
 - **type**: 
    <a href="#plan--/definitions/type">(plan#/definitions/type)</a>
 - **state**: 
    `{string}`Constraints: `minLength`: `1`
 - **create_time**: 
    `{string}`Constraints: `minLength`: `1`
 - **update_time**: 
    `{string}`Constraints: `minLength`: `1`
 - **payment_definitions**: 
    `{array}` <a name="--/properties/payment_definitions"/>
    
    Each item should be:
    
    <a href="#response.common--/definitions/payment_definition">(response.common#/definitions/payment_definition)</a>
 - **terms**: 
    `{array}` <a name="--/properties/terms"/>
    
    Each item should be:
    
    <a href="#common--/definitions/term">(common#/definitions/term)</a>
 - **merchant_preferences**: 
    <a href="#response.common--/definitions/merchant_preferences">(response.common#/definitions/merchant_preferences)</a>
 - **links**: 
    `{array}` <a name="--/properties/links"/>
    
    Each item should be:
    
    <a href="#common--/definitions/links">(common#/definitions/links)</a>
 - **httpStatusCode**: 
    `{integer}`


**[⬆ Back to Top](#top)**
## <a name='Common-type:-Subscription-response-object'></a> Common type: Subscription response object
Исходный файл [response/subscription.json](response/subscription.json).
```
SCHEMA response.common.subscription
```



### Schema

`{object}` 
Constraints: `required`: `name,models,definition,price`

Additional properties allowed: `true`


Properties:


 - **models**: 
    `{number}`
 - **price**: 
    `{number}`
 - **name**: 
    `{string}`Constraints: `minLength`: `1`
 - **definition**: 
    <a href="#common--/definitions/payment_definition">(common#/definitions/payment_definition)</a>


**[⬆ Back to Top](#top)**
## <a name='data-types'></a> data-types
Исходный файл [data-types.json](data-types.json).
```
SCHEMA data-types
```



### Schema



**Definitions**:


 - **data-types#/definitions/nullable-string**
    `{string,null}`


**[⬆ Back to Top](#top)**
