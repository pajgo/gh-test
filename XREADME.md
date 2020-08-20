<a name="top"></a>
# Service ms-payments v8.3.1



- [Agreement](#Agreement)
	- [Bill agreement](#Bill-agreement)
	- [Change agreement state](#Change-agreement-state)
	- [Create agreement](#Create-agreement)
	- [Executes agreement for approval](#Executes-agreement-for-approval)
	- [Get Agreement](#Get-Agreement)
	- [Get agreement for user](#Get-agreement-for-user)
	- [List Agreements](#List-Agreements)
	- [Sync agreements](#Sync-agreements)
	
- [Balance](#Balance)
	- [Decrement balance](#Decrement-balance)
	- [Get balance](#Get-balance)
	
- [Charge](#Charge)
	- [Get charge](#Get-charge)
	- [List charges](#List-charges)
	
- [Charge.Paypal](#Charge.Paypal)
	- [Paypal - Capture paypal funds](#Paypal---Capture-paypal-funds)
	- [Paypal - Create Paypal charge](#Paypal---Create-Paypal-charge)
	- [Paypal - Return Paypal funds](#Paypal---Return-Paypal-funds)
	- [Paypal - Void paypal charge](#Paypal---Void-paypal-charge)
	
- [Charge.Stripe](#Charge.Stripe)
	- [Stripe - Create charge](#Stripe---Create-charge)
	- [Stripe - Webhook handler](#Stripe---Webhook-handler)
	
- [Plan](#Plan)
	- [Change plan state](#Change-plan-state)
	- [Create plan](#Create-plan)
	- [Delete plan](#Delete-plan)
	- [Get Plan](#Get-Plan)
	- [List plans](#List-plans)
	- [Update plan](#Update-plan)
	
- [Sale](#Sale)
	- [Create sale](#Create-sale)
	- [Execute sale](#Execute-sale)
	- [Get sale](#Get-sale)
	- [List sales](#List-sales)
	- [Sync sale](#Sync-sale)
	
- [SchemaDefinitions](#SchemaDefinitions)
	- [[common] Agreement object](#[common]-Agreement-object)
	- [[common] Definitions](#[common]-Definitions)
	- [[common] Extra `DataTypes`](#[common]-Extra-`DataTypes`)
	- [[common] Sale object](#[common]-Sale-object)
	- [[common] Subscription object](#[common]-Subscription-object)
	- [[common]: Payment plan object](#[common]:-Payment-plan-object)
	- [[response.common] Agreement object](#[response.common]-Agreement-object)
	- [[response.common] Payment plan object](#[response.common]-Payment-plan-object)
	- [[response.common] Sale object](#[response.common]-Sale-object)
	- [[response.common] Subscription object](#[response.common]-Subscription-object)
	- [[response.common] Transaction common information object](#[response.common]-Transaction-common-information-object)
	- [[response.common] Transaction information object](#[response.common]-Transaction-information-object)
	- [[response.common] Transaction object](#[response.common]-Transaction-object)
	
- [Transaction](#Transaction)
	- [Aggregate transaction](#Aggregate-transaction)
	- [Common transaction data](#Common-transaction-data)
	- [Get transaction](#Get-transaction)
	- [List transactions](#List-transactions)
	- [Sync transactions](#Sync-transactions)
	- [Sync Updated transactions](#Sync-Updated-transactions)
	

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


 - **agreement**
    `{string}`
 - **nextCycle**
    `{integer}`
 - **username**
    `{string}`


### Response schema:

`{string}`
String as status of the operation




**[⬆ Back to Top](#top)**
## <a name='Change-agreement-state'></a> Change agreement state
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


 - **owner**
    <a href="#common--/definitions/owner">(common#/definitions/owner)</a>
 - **state**
    `{string}`Constraints: `enum`: `suspend,reactivate,cancel`
 - **note**
    `{string}`Constraints: `minLength`: `1`


### Response schema:

`{string}`Constraints: `enum`: `suspend,reactivate,cancel`




**[⬆ Back to Top](#top)**
## <a name='Create-agreement'></a> Create agreement
<p>Creates new agreement</p>

Исходный файл [src/actions/agreement/create.js](src/actions/agreement/create.js).
```
AMQP &lt;prefix&gt;.agreement.create
```


### Request schema

`{object}` 
Constraints: `required`: `owner,agreement`

Additional properties allowed: `true`


Properties:


 - **owner**
    <a href="#common--/definitions/owner">(common#/definitions/owner)</a>
 - **agreement**
    
    *Could be allOf:*
    
    
     - <a href="#agreement--">(agreement#)</a>
     - `{object}` <a name="agreement.create--/properties/agreement/allOf/1"/>
        
        Additional properties allowed: `true`
        
        
        Properties:
        
        
         - **plan**
            `{object}` <a name="agreement.create--/properties/agreement/allOf/1/properties/plan"/>
            Constraints: `required`: `id`
            
            Additional properties allowed: `true`
            
            
            Properties:
            
            
             - **id**
                `{string}`Constraints: `pattern`: `^P-[A-Z0-9]+$`
            
        
    
 - **trialDiscount**
    `{integer}`Constraints: `minimum`: `0`, `maximum`: `100`, `default`: `0`
 - **trialCycle**
    `{integer}`Constraints: `minimum`: `1`, `default`: `12`


### Response schema:

`{object}` 

Created agreement


Additional properties allowed: `true`


Properties:


 - **token**
    `{string}`Constraints: `minLength`: `1`
 - **url**
    `{string}`Constraints: `minLength`: `1`
 - **agreement**
    <a href="#response.common.agreement--">(response.common.agreement#)</a>





**[⬆ Back to Top](#top)**
## <a name='Executes-agreement-for-approval'></a> Executes agreement for approval
<p>Performs agreement approval through paypal and sends link back</p>

Исходный файл [src/actions/agreement/execute.js](src/actions/agreement/execute.js).
```
AMQP &lt;prefix&gt;.agreement.execute
```


### Request schema

`{object}` 
Constraints: `required`: `token`

Additional properties allowed: `true`


Properties:


 - **token**
    `{string}`Constraints: `minLength`: `1`


### Response schema:

<a href="#response.common.agreement--">agreement.execute response`response.agreement.execute` (response.common.agreement#)</a>




**[⬆ Back to Top](#top)**
## <a name='Get-Agreement'></a> Get Agreement
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


 - **id**
    `{string}`Constraints: `minLength`: `1`
 - **owner**
    <a href="#common--/definitions/owner">(common#/definitions/owner)</a>


### Response schema:

`{object}` 

Additional properties allowed: `true`


Properties:


 - **id**
    `{string}`Constraints: `minLength`: `4`
 - **owner**
    <a href="#common--/definitions/owner">(common#/definitions/owner)</a>
 - **state**
    `{string}`
    #TODO
 - **token**
    `{string}`Constraints: `minLength`: `10`
 - **plan**
    <a href="#common--/definitions/planId">(common#/definitions/planId)</a>
 - **agreement**
    <a href="#response.common.agreement--">(response.common.agreement#)</a>





**[⬆ Back to Top](#top)**
## <a name='Get-agreement-for-user'></a> Get agreement for user
<p>Retrieves agreement information for user</p>

Исходный файл [src/actions/agreement/forUser.js](src/actions/agreement/forUser.js).
```
AMQP &lt;prefix&gt;.agreement.forUser
```


### Request schema

`{object}` 
Constraints: `required`: `user`

Additional properties allowed: `true`


Properties:


 - **user**
    `{string}`Constraints: `minLength`: `1`


### Response schema:

<a href="#response.agreement.get--">agreement.forUser response`response.agreement.forUser` (response.agreement.get#)</a>




**[⬆ Back to Top](#top)**
## <a name='List-Agreements'></a> List Agreements
<p>Returns list of the agreements</p>

Исходный файл [src/actions/agreement/list.js](src/actions/agreement/list.js).
```
AMQP &lt;prefix&gt;.agreement.list
```


### Request schema

`{object}` 

Additional properties allowed: `true`


Properties:


 - **offset**
    `{integer}`Constraints: `minimum`: `0`
 - **limit**
    `{integer}`Constraints: `minimum`: `1`, `maximum`: `100`
 - **filter**
    <a href="#common--/definitions/filter">(common#/definitions/filter)</a>
 - **criteria**
    `{string}`Constraints: `minLength`: `1`
 - **order**
    `{string}`Constraints: `enum`: `ASC,DESC`
 - **owner**
    <a href="#common--/definitions/owner">(common#/definitions/owner)</a>


### Response schema:

`{object}` 
Constraints: `required`: `items,cursor,page,pages`

Additional properties allowed: `true`


Properties:


 - **items**
    `{array}` <a name="response.agreement.list--/properties/items"/>
    
    Each item should be:
    
    
     - <a href="#response.agreement.get--">(response.agreement.get#)</a>
    
 - **cursor**
    `{number}`
 - **page**
    `{number}`
 - **pages**
    `{number}`





**[⬆ Back to Top](#top)**
## <a name='Sync-agreements'></a> Sync agreements
<p>Performs agreements synchronization <strong>TODO</strong>: Find out response schema</p>

Исходный файл [src/actions/agreement/sync.js](src/actions/agreement/sync.js).
```
AMQP &lt;prefix&gt;.agreement.sync
```


### Request schema

`{object}` 

Additional properties allowed: `true`


Properties:


 - **start**
    `{integer}`
 - **cursor**
    `{integer}`





**[⬆ Back to Top](#top)**
# <a name='Balance'></a> Balance
## <a name='Decrement-balance'></a> Decrement balance
Исходный файл [src/actions/balance/decrement.js](src/actions/balance/decrement.js).
```
AMQP &lt;prefix&gt;.balance.decrement
```


### Request schema

`{object}` 
Constraints: `required`: `ownerId,amount,idempotency,goal`

Additional properties allowed: `true`


Properties:


 - **ownerId**
    `{string}`Constraints: `minLength`: `1`, `maxLength`: `65536`
 - **amount**
    `{integer}`Constraints: `minimum`: `1`, `maximum`: `1000000`
    A positive integer representing how much to charge
 - **idempotency**
    `{string}`Constraints: `minLength`: `1`, `maxLength`: `65536`
    An idempotency key
 - **goal**
    `{string}`Constraints: `minLength`: `1`, `maxLength`: `65536`


### Response schema:

`{number}`




**[⬆ Back to Top](#top)**
## <a name='Get-balance'></a> Get balance
Исходный файл [src/actions/balance/get.js](src/actions/balance/get.js).
```
GET &lt;prefix&gt;.balance.get
```


### Request schema

`{object}` 
Constraints: `required`: `ownerId,amount,idempotency,goal`

Additional properties allowed: `true`


Properties:


 - **ownerId**
    `{string}`Constraints: `minLength`: `1`, `maxLength`: `65536`
 - **amount**
    `{integer}`Constraints: `minimum`: `1`, `maximum`: `1000000`
    A positive integer representing how much to charge
 - **idempotency**
    `{string}`Constraints: `minLength`: `1`, `maxLength`: `65536`
    An idempotency key
 - **goal**
    `{string}`Constraints: `minLength`: `1`, `maxLength`: `65536`


### Response schema:

`{number}`




**[⬆ Back to Top](#top)**
# <a name='Charge'></a> Charge
## <a name='Get-charge'></a> Get charge
<p>Get the charge information</p>

Исходный файл [src/actions/charge/get.js](src/actions/charge/get.js).
```
HTTP-GET &lt;prefix&gt;.charge.get
```


### Request schema

`{object}` 
Constraints: `required`: `id`

Additional properties allowed: `true`


Properties:


 - **id**
    <a href="#common--/definitions/chargeId">(common#/definitions/chargeId)</a>


### Response schema:

`{object}` 

Additional properties allowed: `true`


Properties:


 - **data**
    `{object}` <a name="response.charge.get--/properties/data"/>
    
    Additional properties allowed: `true`
    
    
    Properties:
    
    
     - **amount**
        `{number}`
     - **description**
        `{string}`
     - **status**
        `{number}`
     - **createAt**
        `{string}`Constraints: `format`: `date`
     - **owner**
        <a href="#common--/definitions/owner">(common#/definitions/owner)</a>
     - **failReason**
        `{string}`
    





**[⬆ Back to Top](#top)**
## <a name='List-charges'></a> List charges
<p>Get the list of charges</p>

Исходный файл [src/actions/charge/list.js](src/actions/charge/list.js).
```
HTTP-GET &lt;prefix&gt;.charge.list
```


### Request schema

`{object}` 
Constraints: `required`: `limit,offset`

Additional properties allowed: `true`


Properties:


 - **owner**
    <a href="#common--/definitions/owner">(common#/definitions/owner)</a>
 - **limit**
    `{integer}`Constraints: `minimum`: `1`, `maximum`: `100`, `default`: `20`
 - **offset**
    `{integer}`Constraints: `minimum`: `0`, `default`: `0`


### Response schema:

`{object}` 

Additional properties allowed: `true`


Properties:


 - **data**
    `{array}` <a name="response.charge.list--/properties/data"/>
    
    Each item should be:
    
    
     - `{object}` <a name="response.charge.list--/properties/data/items"/>
     - 
        Additional properties allowed: `true`
        
     - 
        Properties:
        
         - **amount**
            `{number}`
         - **description**
            `{string}`
         - **status**
            `{number}`
         - **createAt**
            `{string}`Constraints: `format`: `date`
         - **owner**
            <a href="#common--/definitions/owner">(common#/definitions/owner)</a>
         - **failReason**
            `{string}`
        
    
 - **meta**
    `{object}` <a name="response.charge.list--/properties/meta"/>
    
    Additional properties allowed: `true`
    
    
    Properties:
    
    
     - **offset**
        `{number}`
     - **limit**
        `{number}`
     - **cursor**
        `{number}`
     - **page**
        `{number}`
     - **pages**
        `{number}`
    





**[⬆ Back to Top](#top)**
# <a name='Charge.Paypal'></a> Charge.Paypal
## <a name='Paypal---Capture-paypal-funds'></a> Paypal - Capture paypal funds
<p>Captures requested <code>charge</code></p>

Исходный файл [src/actions/charge/paypal/capture.js](src/actions/charge/paypal/capture.js).
```
AMQP &lt;prefix&gt;.charge.paypal.capture
```


### Request schema

`{object}` 
Constraints: `required`: `paymentId`

Additional properties allowed: `true`


Properties:


 - **paymentId**
    `{string}`Constraints: `minLength`: `1`, `maxLength`: `1024`


### Response schema:

`{object}` 

Additional properties allowed: `true`


Properties:


 - **data**
    `{object}` <a name="response.charge.paypal.capture--/properties/data"/>
    
    Additional properties allowed: `true`
    
    
    Properties:
    
    
     - **amount**
        `{number}`
     - **description**
        `{string}`
     - **status**
        `{number}`
     - **createAt**
        `{string}`Constraints: `format`: `date`
     - **owner**
        <a href="#common--/definitions/owner">(common#/definitions/owner)</a>
     - **failReason**
        `{string}`
    





**[⬆ Back to Top](#top)**
## <a name='Paypal---Create-Paypal-charge'></a> Paypal - Create Paypal charge
Исходный файл [src/actions/charge/paypal/create.js](src/actions/charge/paypal/create.js).
```
HTTP-POST &lt;prefix&gt;.charge.paypal.create
```


### Request schema

`{object}` 
Constraints: `required`: `amount,description,returnUrl,cancelUrl`

Additional properties allowed: `true`


Properties:


 - **amount**
    `{integer}`Constraints: `minimum`: `1`, `maximum`: `1000000`
    A positive integer representing how much to charge
 - **description**
    `{string}`Constraints: `minLength`: `1`, `maxLength`: `65536`
    An arbitrary string which you can attach to a charge object
 - **returnUrl**
    `{string}`Constraints: `format`: `uri`
 - **cancelUrl**
    `{string}`Constraints: `format`: `uri`


### Response schema:

`{object}` 

Additional properties allowed: `true`


Properties:


 - **data**
    `{object}` <a name="response.charge.paypal.create--/properties/data"/>
    
    Additional properties allowed: `true`
    
    
    Properties:
    
    
     - **amount**
        `{number}`
     - **description**
        `{string}`
     - **status**
        `{number}`
     - **createAt**
        `{string}`Constraints: `format`: `date`
     - **owner**
        <a href="#common--/definitions/owner">(common#/definitions/owner)</a>
     - **failReason**
        `{string}`
    
 - **meta**
    `{object}` <a name="response.charge.paypal.create--/properties/meta"/>
    
    Additional properties allowed: `true`
    
    
    Properties:
    
    
     - **paypal**
        `{object}` <a name="response.charge.paypal.create--/properties/meta/properties/paypal"/>
        
        Additional properties allowed: `true`
        
        
        Properties:
        
        
         - **approvalUrl**
            <a href="#common--/definitions/links">(common#/definitions/links)</a>
         - **paymentId**
            <a href="#common--/definitions/paymentId">(common#/definitions/paymentId)</a>
        
    





**[⬆ Back to Top](#top)**
## <a name='Paypal---Return-Paypal-funds'></a> Paypal - Return Paypal funds
<p>Returns funds</p>

Исходный файл [src/actions/charge/paypal/return.js](src/actions/charge/paypal/return.js).
```
HTTP-GET &lt;prefix&gt;.charge.paypal.return
```


### Request schema

`{object}` 
Constraints: `required`: `PayerID,paymentId`

Additional properties allowed: `true`


Properties:


 - **PayerID**
    `{string}`Constraints: `minLength`: `1`, `maxLength`: `1024`
 - **paymentId**
    `{string}`Constraints: `minLength`: `1`, `maxLength`: `1024`
 - **token**
    `{string}`Constraints: `minLength`: `1`, `maxLength`: `1024`
    Paypal token


### Response schema:

`{object}` 

Additional properties allowed: `true`


Properties:


 - **data**
    `{object}` <a name="response.charge.paypal.return--/properties/data"/>
    
    Additional properties allowed: `true`
    
    
    Properties:
    
    
     - **id**
        `{string}`Constraints: `format`: `uuid`
        #TODO
     - **type**
        `{string}`Constraints: `const`: `charge`
        #TODO
     - **attributes**
        `{object}` <a name="response.charge.paypal.return--/properties/data/properties/attributes"/>
        
        Additional properties allowed: `true`
        
        
        Properties:
        
        
         - **amount**
            `{string}`
         - **description**
            `{string}`
         - **status**
            `{number}`
         - **createAt**
            `{string}`Constraints: `format`: `date-time`
         - **owner**
            <a href="#common--/definitions/owner">(common#/definitions/owner)</a>
         - **failReason**
            `{string}`
        
    
 - **meta**
    `{object}` <a name="response.charge.paypal.return--/properties/meta"/>
    
    Additional properties allowed: `true`
    
    
    Properties:
    
    
     - **paypal**
        `{object}` <a name="response.charge.paypal.return--/properties/meta/properties/paypal"/>
        
        Additional properties allowed: `true`
        
        
        Properties:
        
        
         - **payer**
            <a href="#common--/definitions/payer">(common#/definitions/payer)</a>
        
    





**[⬆ Back to Top](#top)**
## <a name='Paypal---Void-paypal-charge'></a> Paypal - Void paypal charge
<p>Invalidate <code>charge</code></p>

Исходный файл [src/actions/charge/paypal/void.js](src/actions/charge/paypal/void.js).
```
AMQP &lt;prefix&gt;.charge.paypal.void
```


### Request schema

`{object}` 
Constraints: `required`: `paymentId`

Additional properties allowed: `true`


Properties:


 - **paymentId**
    `{string}`Constraints: `minLength`: `1`, `maxLength`: `1024`


### Response schema:

`{object}` 

Additional properties allowed: `true`


Properties:


 - **data**
    `{object}` <a name="response.charge.paypal.void--/properties/data"/>
    
    Additional properties allowed: `true`
    
    
    Properties:
    
    
     - **amount**
        `{number}`
     - **description**
        `{string}`
     - **status**
        `{number}`
     - **createAt**
        `{string}`Constraints: `format`: `date`
     - **owner**
        <a href="#common--/definitions/owner">(common#/definitions/owner)</a>
     - **failReason**
        `{string}`
    





**[⬆ Back to Top](#top)**
# <a name='Charge.Stripe'></a> Charge.Stripe
## <a name='Stripe---Create-charge'></a> Stripe - Create charge
<p>Creates new Stripe charge</p>

Исходный файл [src/actions/charge/stripe/create.js](src/actions/charge/stripe/create.js).
```
HTTP-POST &lt;prefix&gt;.charge.stripe.create
```


### Request schema


 - 
    *If:*
    
    `{undefined}` 
    
    Constraints: `required`: `saveCard`
    
    
    
    Additional properties allowed: `true`
    
    
    
    
    
    Properties:
    
    
    
    
    
     - **saveCard**
    
        Constraints: `const`: `true`
    
    
    
 - 
    *Then:*
    
    Constraints: `required`: `email,token`
    


### Response schema:

`{object}` 

Additional properties allowed: `true`


Properties:


 - **data**
    `{object}` <a name="response.charge.stripe.create--/properties/data"/>
    
    Additional properties allowed: `true`
    
    
    Properties:
    
    
     - **amount**
        `{number}`
     - **description**
        `{string}`
     - **status**
        `{number}`
     - **createAt**
        `{string}`Constraints: `format`: `date`
     - **owner**
        <a href="#common--/definitions/owner">(common#/definitions/owner)</a>
     - **failReason**
        `{string}`
    





**[⬆ Back to Top](#top)**
## <a name='Stripe---Webhook-handler'></a> Stripe - Webhook handler
<p>Handles requests from Stripe</p>

Исходный файл [src/actions/charge/stripe/webhook.js](src/actions/charge/stripe/webhook.js).
```
HTTP-POST &lt;prefix&gt;.charge.stripe.webhook
```


### Request schema

`{object}` 

Additional properties allowed: `true`


### Response schema:

`{object}` 

Additional properties allowed: `true`


Properties:


 - **received**
    `{boolean}`Constraints: `const`: `true`





**[⬆ Back to Top](#top)**
# <a name='Plan'></a> Plan
## <a name='Change-plan-state'></a> Change plan state
<p>Changes plan state</p>

Исходный файл [src/actions/plan/state.js](src/actions/plan/state.js).
```
AMQP, INTERNAL &lt;prefix&gt;.plan.state
```


### Request schema

`{object}` 
Constraints: `required`: `id,state`

Additional properties allowed: `true`


Properties:


 - **id**
    `{string}`Constraints: `minLength`: `1`
 - **state**
    `{string}`Constraints: `enum`: `created,active,inactive,deleted`


### Response schema:

`{array}` 

Each item should be:


 - `{string}`





**[⬆ Back to Top](#top)**
## <a name='Create-plan'></a> Create plan
<p>Creates new plan</p>

Исходный файл [src/actions/plan/create.js](src/actions/plan/create.js).
```
AMQP &lt;prefix&gt;.plan.create
```


### Request schema

`{object}` 
Constraints: `required`: `alias,hidden,subscriptions,plan`

Additional properties allowed: `true`


Properties:


 - **hidden**
    `{boolean}`
 - **alias**
    `{string}`Constraints: `minLength`: `1`
 - **level**
    <a href="#plan--/definitions/level">(plan#/definitions/level)</a>
 - **subscriptions**
    `{array}` <a name="plan.create--/properties/subscriptions"/>
    
    Each item should be:
    
    
     - <a href="#subscription--">(subscription#)</a>
    
 - **plan**
    <a href="#plan--">(plan#)</a>
 - **meta**
    <a href="#plan--/definitions/meta">(plan#/definitions/meta)</a>


### Response schema:

<a href="#response.plan.get--">Created plan`response.plan.create` (response.plan.get#)</a>




**[⬆ Back to Top](#top)**
## <a name='Delete-plan'></a> Delete plan
<p>Deletes plan</p>

Исходный файл [src/actions/plan/delete.js](src/actions/plan/delete.js).
```
AMQP &lt;prefix&gt;.plan.delete
```


### Request schema

`{object}` 
Constraints: `required`: `alias,hidden,subscriptions,plan`

Additional properties allowed: `true`


Properties:


 - **hidden**
    `{boolean}`
 - **alias**
    `{string}`Constraints: `minLength`: `1`
 - **level**
    <a href="#plan--/definitions/level">(plan#/definitions/level)</a>
 - **subscriptions**
    `{array}` <a name="plan.create--/properties/subscriptions"/>
    
    Each item should be:
    
    
     - <a href="#subscription--">(subscription#)</a>
    
 - **plan**
    <a href="#plan--">(plan#)</a>
 - **meta**
    <a href="#plan--/definitions/meta">(plan#/definitions/meta)</a>


### Response schema:

<a href="#response.plan.get--">Created plan`response.plan.create` (response.plan.get#)</a>




**[⬆ Back to Top](#top)**
## <a name='Get-Plan'></a> Get Plan
<p>Retrieves plan or parent plan by its id.</p>

Исходный файл [src/actions/plan/get.js](src/actions/plan/get.js).
```
AMQP, INTERNAL &lt;prefix&gt;.plan.get
```


### Request schema


*Could be anyOf:*


 - `{string}`Constraints: `minLength`: `1`, `maxLength`: `100`
 - `{object}` 
    Constraints: `required`: `id`
    
    Plan object
    
    
    Additional properties allowed: `true`
    
    
    Properties:
    
    
     - **id**
        `{string}`Constraints: `minLength`: `1`, `maxLength`: `100`
     - **fetchParent**
        `{boolean}`
    


### Response schema:

`{object}` 

Additional properties allowed: `true`


Properties:


 - **id**
    <a href="#common--/definitions/planId">(common#/definitions/planId)</a>
 - **state**
    `{string}`
    #TODO
 - **alias**
    `{string}`Constraints: `minLength`: `1`
 - **name**
    `{string}`Constraints: `minLength`: `1`
 - **description**
    `{string}`
 - **hidden**
    `{boolean}`
 - **level**
    <a href="#plan--/definitions/level">(plan#/definitions/level)</a>
 - **subs**
    `{array}` <a name="response.plan.get--/properties/subs"/>
    
    Each item should be:
    
    
     - <a href="#response.common.subscription--">(response.common.subscription#)</a>
    
 - **plan**
    <a href="#response.common.plan--">(response.common.plan#)</a>
 - **meta**
    <a href="#plan--/definitions/meta">(plan#/definitions/meta)</a>
 - **type**
    <a href="#plan--/definitions/type">(plan#/definitions/type)</a>
 - **month**
    <a href="#data-types--/definitions/nullable-string">(data-types#/definitions/nullable-string)</a>
 - **year**
    <a href="#data-types--/definitions/nullable-string">(data-types#/definitions/nullable-string)</a>





**[⬆ Back to Top](#top)**
## <a name='List-plans'></a> List plans
<p>Returns list of the plans</p>

Исходный файл [src/actions/plan/list.js](src/actions/plan/list.js).
```
AMQP &lt;prefix&gt;.plan.list
```


### Request schema

`{object}` 

Additional properties allowed: `true`


Properties:


 - **offset**
    `{integer}`Constraints: `minimum`: `0`
 - **limit**
    `{integer}`Constraints: `minimum`: `1`, `maximum`: `100`
 - **filter**
    <a href="#common--/definitions/filter">(common#/definitions/filter)</a>
 - **criteria**
    `{string}`Constraints: `minLength`: `1`
 - **order**
    `{string}`Constraints: `enum`: `ASC,DESC`
 - **owner**
    <a href="#common--/definitions/owner">(common#/definitions/owner)</a>


### Response schema:

`{object}` 
Constraints: `required`: `items,cursor,page,pages`

Additional properties allowed: `true`


Properties:


 - **items**
    `{array}` <a name="response.plan.list--/properties/items"/>
    
    Each item should be:
    
    
     - <a href="#response.plan.get--">(response.plan.get#)</a>
    
 - **cursor**
    `{number}`
 - **page**
    `{number}`
 - **pages**
    `{number}`





**[⬆ Back to Top](#top)**
## <a name='Update-plan'></a> Update plan
<p>Update paypal plan with a special case for a free plan <strong>WARNING</strong>: this method is prone to race conditions, and, therefore, requires a lock to be used before updating data</p>

Исходный файл [src/actions/plan/update.js](src/actions/plan/update.js).
```
AMQP &lt;prefix&gt;.plan.state
```


### Request schema

`{object}` 
Constraints: `required`: `id`, `minProperties`: `2`

Additional properties allowed: `true`


Properties:


 - **id**
    <a href="#common--/definitions/planId">(common#/definitions/planId)</a>
 - **alias**
    `{string}`Constraints: `minLength`: `1`, `not`: `[object Object]`
 - **description**
    `{string}`Constraints: `minLength`: `1`
 - **hidden**
    `{boolean}`
 - **subscriptions**
    `{object}` <a name="plan.update--/properties/subscriptions"/>
    Constraints: `minProperties`: `1`
    
    Additional properties allowed: `true`
    
    
    Properties:
    
    
     - **monthly**
        <a href="#plan.update--/definitions/subscription">(plan.update#/definitions/subscription)</a>
     - **yearly**
        <a href="#plan.update--/definitions/subscription">(plan.update#/definitions/subscription)</a>
    
 - **meta**
    <a href="#plan--/definitions/meta">(plan#/definitions/meta)</a>
 - **level**
    <a href="#plan--/definitions/level">(plan#/definitions/level)</a>


**Definitions**:


 - **plan.update#/definitions/subscription**
    `{object}` <a name="plan.update--/definitions/subscription"/>
    Constraints: `minProperties`: `1`
    
    Additional properties allowed: `true`
    
    
    Properties:
    
    
     - **models**
        `{integer}`Constraints: `minimum`: `0`
     - **modelPrice**
        `{number}`Constraints: `minimum`: `0.01`
    


### Response schema:

<a href="#response.plan.get--">Update plan response`response.plan.update` (response.plan.get#)</a>




**[⬆ Back to Top](#top)**
# <a name='Sale'></a> Sale
## <a name='Create-sale'></a> Create sale
<p>Creates new sale</p>

Исходный файл [src/actions/sale/create.js](src/actions/sale/create.js).
```
AMQP &lt;prefix&gt;.sale.create
```


### Request schema

`{object}` 
Constraints: `required`: `owner,amount`

Additional properties allowed: `true`


Properties:


 - **owner**
    <a href="#common--/definitions/owner">(common#/definitions/owner)</a>
 - **amount**
    `{integer}`Constraints: `minimum`: `1`, `maximum`: `10000`


### Response schema:

`{object}` 

Additional properties allowed: `true`


Properties:


 - **token**
    `{string}`
 - **url**
    `{string}`
 - **sale**
    <a href="#response.common.saleresponse.common.sale">(response.common.sale)</a>





**[⬆ Back to Top](#top)**
## <a name='Execute-sale'></a> Execute sale
<p>Executes sale</p>

Исходный файл [src/actions/sale/execute.js](src/actions/sale/execute.js).
```
AMQP &lt;prefix&gt;.sale.execute
```


### Request schema

`{object}` 
Constraints: `required`: `owner,amount`

Additional properties allowed: `true`


Properties:


 - **owner**
    <a href="#common--/definitions/owner">(common#/definitions/owner)</a>
 - **amount**
    `{integer}`Constraints: `minimum`: `1`, `maximum`: `10000`


### Response schema:

`{object}` 

Additional properties allowed: `true`


Properties:


 - **token**
    `{string}`
 - **url**
    `{string}`
 - **sale**
    <a href="#response.common.saleresponse.common.sale">(response.common.sale)</a>





**[⬆ Back to Top](#top)**
## <a name='Get-sale'></a> Get sale
<p>Returns sale information</p>

Исходный файл [src/actions/sale/get.js](src/actions/sale/get.js).
```
AMQP &lt;prefix&gt;.sale.get
```


### Request schema

`{object}` 
Constraints: `required`: `id`

Additional properties allowed: `true`


Properties:


 - **id**
    `{string}`Constraints: `minLength`: `1`
 - **owner**
    <a href="#common--/definitions/owner">(common#/definitions/owner)</a>


### Response schema:

<a href="#sale--">Sale information`response.sale.get` (sale#)</a>




**[⬆ Back to Top](#top)**
## <a name='List-sales'></a> List sales
<p>Returns list of the sales</p>

Исходный файл [src/actions/sale/list.js](src/actions/sale/list.js).
```
AMQP &lt;prefix&gt;.sale.list
```


### Request schema

`{object}` 

Additional properties allowed: `true`


Properties:


 - **offset**
    `{integer}`Constraints: `minimum`: `0`
 - **limit**
    `{integer}`Constraints: `minimum`: `1`, `maximum`: `100`
 - **filter**
    <a href="#common--/definitions/filter">(common#/definitions/filter)</a>
 - **criteria**
    `{string}`Constraints: `minLength`: `1`
 - **order**
    `{string}`Constraints: `enum`: `ASC,DESC`
 - **owner**
    <a href="#common--/definitions/owner">(common#/definitions/owner)</a>


### Response schema:

`{object}` 
Constraints: `required`: `items,cursor,page,pages`

Additional properties allowed: `true`


Properties:


 - **items**
    `{array}` <a name="response.sale.list--/properties/items"/>
    
    List of the existing Sales
    
    
    Each item should be:
    
    
     - <a href="#salesale">(sale)</a>
    
 - **cursor**
    `{number}`
 - **page**
    `{number}`
 - **pages**
    `{number}`





**[⬆ Back to Top](#top)**
## <a name='Sync-sale'></a> Sync sale
<p>Performs synchronizations of sales <strong>TODO</strong>: Find response schema</p>

Исходный файл [src/actions/sale/sync.js](src/actions/sale/sync.js).
```
AMQP &lt;prefix&gt;.sale.sync
```


### Request schema

`{object}` 

Additional properties allowed: `true`


Properties:


 - **next_id**
    `{string}`





**[⬆ Back to Top](#top)**
# <a name='SchemaDefinitions'></a> SchemaDefinitions
## <a name='[common]-Agreement-object'></a> [common] Agreement object
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


 - **id**
    `{string}`Constraints: `minLength`: `1`
 - **state**
    `{string}`Constraints: `minLength`: `1`
 - **name**
    `{string}`Constraints: `minLength`: `1`
 - **description**
    `{string}`Constraints: `minLength`: `1`
 - **start_date**
    `{string}`Constraints: `minLength`: `1`
 - **agreement_details**
    <a href="#common--/definitions/agreement_details">(common#/definitions/agreement_details)</a>
 - **payer**
    <a href="#common--/definitions/payer">(common#/definitions/payer)</a>
 - **shipping_address**
    <a href="#common--/definitions/address">(common#/definitions/address)</a>
 - **override_merchant_preferences**
    <a href="#common--/definitions/merchant_preferences">(common#/definitions/merchant_preferences)</a>
 - **override_charge_models**
    `{array}` <a name="agreement--/properties/override_charge_models"/>
    
    Each item should be:
    
    
     - <a href="#common--/definitions/override_charge_model">(common#/definitions/override_charge_model)</a>
    
 - **plan**
    
    *Could be oneOf:*
    
    
     - <a href="#plan.create--">(plan.create#)</a>
     - `{object}` <a name="agreement--/properties/plan/oneOf/1"/>
        Constraints: `required`: `id`
        
        Additional properties allowed: `true`
        
        
        Properties:
        
        
         - **id**
            `{string}`Constraints: `minLength`: `1`
        
    
 - **create_time**
    `{string}`Constraints: `minLength`: `1`
 - **update_time**
    `{string}`Constraints: `minLength`: `1`
 - **links**
    `{array}` <a name="agreement--/properties/links"/>
    
    Each item should be:
    
    
     - <a href="#common--/definitions/links">(common#/definitions/links)</a>
    


**[⬆ Back to Top](#top)**
## <a name='[common]-Definitions'></a> [common] Definitions
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
    
    
     - **currency**
        `{string}`Constraints: `minLength`: `3`, `maxLength`: `3`
     - **value**
        `{string}`Constraints: `pattern`: `\d{1,7}(\.\d{1,2})?$`
    
 - **common#/definitions/links**
    `{object}` <a name="common--/definitions/links"/>
    
    Additional properties allowed: `true`
    
    
    Properties:
    
    
     - **href**
        `{string}`Constraints: `minLength`: `1`
     - **rel**
        `{string}`Constraints: `minLength`: `1`
     - **method**
        `{string}`Constraints: `minLength`: `1`
    
 - **common#/definitions/term**
    `{object}` <a name="common--/definitions/term"/>
    Constraints: `required`: `type,max_billing_amount,occurences,amount_range,buyer_editable`
    
    Additional properties allowed: `true`
    
    
    Properties:
    
    
     - **id**
        `{string}`Constraints: `minLength`: `1`
     - **type**
        `{string}`Constraints: `minLength`: `1`
     - **max_billing_amount**
        <a href="#common--/definitions/currency">(common#/definitions/currency)</a>
     - **occurences**
        `{string}`Constraints: `minLength`: `1`
     - **amount_range**
        <a href="#common--/definitions/currency">(common#/definitions/currency)</a>
     - **buyer_editable**
        `{string}`Constraints: `minLength`: `1`
    
 - **common#/definitions/payment_definition**
    `{object}` <a name="common--/definitions/payment_definition"/>
    Constraints: `required`: `name,type,frequency_interval,frequency,cycles,amount`
    
    Additional properties allowed: `true`
    
    
    Properties:
    
    
     - **id**
        `{string}`Constraints: `minLength`: `1`
     - **name**
        `{string}`Constraints: `minLength`: `1`
     - **type**
        `{string}`Constraints: `minLength`: `1`, `enum`: `trial,regular,TRIAL,REGULAR`
     - **frequency_interval**
        `{string}`Constraints: `minLength`: `1`
     - **frequency**
        `{string}`Constraints: `minLength`: `1`
     - **cycles**
        `{string}`Constraints: `minLength`: `1`
     - **amount**
        <a href="#common--/definitions/currency">(common#/definitions/currency)</a>
     - **charge_models**
        `{array}` <a name="common--/definitions/payment_definition/properties/charge_models"/>
        
        Each item should be:
        
        
         - `{object}` <a name="common--/definitions/payment_definition/properties/charge_models/items"/>
         - Constraints: `required`: `type,amount`
         - 
            Additional properties allowed: `true`
            
         - 
            Properties:
            
             - **id**
                `{string}`Constraints: `minLength`: `1`
             - **type**
                `{string}`Constraints: `minLength`: `1`
             - **amount**
                <a href="#common--/definitions/currency">(common#/definitions/currency)</a>
            
        
    
 - **common#/definitions/merchant_preferences**
    `{object}` <a name="common--/definitions/merchant_preferences"/>
    Constraints: `required`: `cancel_url,return_url`
    
    Additional properties allowed: `true`
    
    
    Properties:
    
    
     - **id**
        `{string}`Constraints: `minLength`: `1`
     - **setup_fee**
        <a href="#common--/definitions/currency">(common#/definitions/currency)</a>
     - **cancel_url**
        `{string}`Constraints: `minLength`: `1`
     - **return_url**
        `{string}`Constraints: `minLength`: `1`
     - **notify_url**
        `{string}`Constraints: `minLength`: `1`
     - **max_fail_attempts**
        `{string}`Constraints: `minLength`: `1`
     - **auto_bull_amount**
        `{string}`Constraints: `minLength`: `1`
     - **initial_fail_amount_action**
        `{string}`Constraints: `minLength`: `1`
     - **accepted_payment_type**
        `{string}`Constraints: `minLength`: `1`
     - **char_set**
        `{string}`Constraints: `minLength`: `1`
    
 - **common#/definitions/agreement_details**
    `{object}` <a name="common--/definitions/agreement_details"/>
    
    Additional properties allowed: `true`
    
    
    Properties:
    
    
     - **outstanding_balance**
        <a href="#common--/definitions/currency">(common#/definitions/currency)</a>
     - **cycles_remaining**
        `{string}`Constraints: `minLength`: `1`
     - **cycles_completed**
        `{string}`Constraints: `minLength`: `1`
     - **next_billing_date**
        `{string}`Constraints: `minLength`: `1`
     - **last_payment_date**
        `{string}`Constraints: `minLength`: `1`
     - **last_payment_amount**
        <a href="#common--/definitions/currency">(common#/definitions/currency)</a>
     - **final_payment_date**
        `{string}`Constraints: `minLength`: `1`
     - **failed_payment_count**
        `{string}`Constraints: `minLength`: `1`
    
 - **common#/definitions/payer**
    `{object}` <a name="common--/definitions/payer"/>
    Constraints: `required`: `payment_method`
    
    Additional properties allowed: `true`
    
    
    Properties:
    
    
     - **payment_method**
        `{string}`Constraints: `enum`: `credit_card,bank,paypal`
     - **status**
        `{string}`Constraints: `minLength`: `1`
     - **account_type**
        `{string}`Constraints: `enum`: `business,personal,premier`
     - **account_age**
        `{string}`
     - **funding_instruments**
        `{array}` <a name="common--/definitions/payer/properties/funding_instruments"/>
        
        Each item should be:
        
        
         - <a href="#common--/definitions/funding_instrument">(common#/definitions/funding_instrument)</a>
        
     - **funding_option_id**
        `{string}`
     - **payer_info**
        <a href="#common--/definitions/payer_info">(common#/definitions/payer_info)</a>
    
 - **common#/definitions/funding_instrument**
    `{object}` <a name="common--/definitions/funding_instrument"/>
    
    Additional properties allowed: `true`
    
    
    Properties:
    
    
     - **credit_card**
        <a href="#common--/definitions/credit_card">(common#/definitions/credit_card)</a>
     - **credit_card_token**
        <a href="#common--/definitions/credit_card_token">(common#/definitions/credit_card_token)</a>
    
 - **common#/definitions/credit_card**
    `{object}` <a name="common--/definitions/credit_card"/>
    Constraints: `required`: `number,type,expire_month,expire_year`
    
    Additional properties allowed: `true`
    
    
    Properties:
    
    
     - **id**
        `{string}`Constraints: `minLength`: `1`
     - **payer_id**
        `{string}`Constraints: `minLength`: `1`
     - **number**
        `{string}`Constraints: `minLength`: `1`
     - **type**
        `{string}`Constraints: `minLength`: `1`
     - **expire_month**
        `{integer}`
     - **expire_year**
        `{integer}`
     - **cvv2**
        `{string}`Constraints: `minLength`: `3`, `maxLength`: `4`
     - **first_name**
        `{string}`Constraints: `minLength`: `1`
     - **last_name**
        `{string}`Constraints: `minLength`: `1`
     - **billing_address**
        <a href="#common--/definitions/address">(common#/definitions/address)</a>
     - **external_customer_id**
        `{string}`Constraints: `minLength`: `1`
     - **merchant_id**
        `{string}`Constraints: `minLength`: `1`
     - **external_card_id**
        `{string}`Constraints: `minLength`: `1`
     - **create_time**
        `{string}`Constraints: `format`: `date-time`
     - **update_time**
        `{string}`Constraints: `format`: `date-time`
     - **state**
        `{string}`Constraints: `minLength`: `1`
     - **valid_until**
        `{string}`Constraints: `minLength`: `1`
    
 - **common#/definitions/credit_card_token**
    `{object}` <a name="common--/definitions/credit_card_token"/>
    Constraints: `required`: `credit_card_id`
    
    Additional properties allowed: `true`
    
    
    Properties:
    
    
     - **credit_card_id**
        `{string}`Constraints: `minLength`: `1`
     - **payer_id**
        `{string}`Constraints: `minLength`: `1`
     - **last4**
        `{string}`Constraints: `minLength`: `4`, `maxLength`: `4`
     - **type**
        `{string}`Constraints: `minLength`: `1`
     - **expire_year**
        `{integer}`
     - **expire_month**
        `{integer}`
    
 - **common#/definitions/payer_info**
    `{object}` <a name="common--/definitions/payer_info"/>
    
    Additional properties allowed: `true`
    
    
    Properties:
    
    
     - **email**
        `{string}`Constraints: `minLength`: `1`, `maxLength`: `127`
     - **salutation**
        `{string}`Constraints: `minLength`: `1`
     - **first_name**
        `{string}`Constraints: `minLength`: `1`
     - **middle_name**
        `{string}`Constraints: `minLength`: `1`
     - **last_name**
        `{string}`Constraints: `minLength`: `1`
     - **suffix**
        `{string}`Constraints: `minLength`: `1`
     - **payer_id**
        `{string}`Constraints: `minLength`: `1`
     - **phone**
        `{string}`Constraints: `minLength`: `1`
     - **country_code**
        `{string}`Constraints: `minLength`: `1`
     - **shipping_address**
        <a href="#common--/definitions/shipping_address">(common#/definitions/shipping_address)</a>
     - **tax_id_type**
        `{string}`Constraints: `minLength`: `1`
     - **tax_id**
        `{string}`Constraints: `minLength`: `1`
    
 - **common#/definitions/address**
    `{object}` <a name="common--/definitions/address"/>
    Constraints: `required`: `line1,city,country_code`
    
    Additional properties allowed: `true`
    
    
    Properties:
    
    
     - **line1**
        `{string}`Constraints: `minLength`: `1`, `maxLength`: `100`
     - **line2**
        `{string}`Constraints: `minLength`: `1`, `maxLength`: `100`
     - **city**
        `{string}`Constraints: `minLength`: `1`, `maxLength`: `50`
     - **country_code**
        `{string}`Constraints: `minLength`: `1`, `maxLength`: `2`
     - **postal_code**
        `{string}`Constraints: `minLength`: `1`, `maxLength`: `20`
     - **state**
        `{string}`Constraints: `minLength`: `1`, `maxLength`: `100`
     - **phone**
        `{string}`Constraints: `minLength`: `1`, `maxLength`: `50`
    
 - **common#/definitions/shipping_address**
    
    *Could be allOf:*
    
    
     - <a href="#common--/definitions/address">(common#/definitions/address)</a>
     - `{undefined}` <a name="common--/definitions/shipping_address/allOf/1"/>
        
        Additional properties allowed: `true`
        
        
        Properties:
        
        
         - **recipient_name**
            `{string}`Constraints: `minLength`: `0`
         - **type**
            `{string}`Constraints: `minLength`: `1`
        
    
 - **common#/definitions/override_charge_model**
    `{object}` <a name="common--/definitions/override_charge_model"/>
    Constraints: `required`: `charge_id,amount`
    
    Additional properties allowed: `true`
    
    
    Properties:
    
    
     - **charge_id**
        `{string}`Constraints: `minLength`: `1`
     - **amount**
        <a href="#common--/definitions/currency">(common#/definitions/currency)</a>
    
 - **common#/definitions/item**
    `{object}` <a name="common--/definitions/item"/>
    Constraints: `required`: `quantity,name,price,currency`
    
    Additional properties allowed: `true`
    
    
    Properties:
    
    
     - **quantity**
        `{string}`
     - **name**
        `{string}`
     - **description**
        `{string}`
     - **price**
        `{string}`
     - **tax**
        `{string}`
     - **currency**
        `{string}`
     - **sku**
        `{string}`
     - **url**
        `{string}`
     - **category**
        `{string}`Constraints: `enum`: `digital,physical`
     - **supplementary_data**
        `{array}` <a name="common--/definitions/item/properties/supplementary_data"/>
        
        Each item should be:
        
        
         - <a href="#common--/definitions/kv">(common#/definitions/kv)</a>
        
     - **postback_data**
        `{array}` <a name="common--/definitions/item/properties/postback_data"/>
        
        Each item should be:
        
        
         - <a href="#common--/definitions/kv">(common#/definitions/kv)</a>
        
    
 - **common#/definitions/kv**
    `{object}` <a name="common--/definitions/kv"/>
    Constraints: `required`: `name,value`
    
    Additional properties allowed: `true`
    
    
    Properties:
    
    
     - **name**
        `{string}`
     - **value**
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
    
    
     - **#multi**
        `{object}` <a name="common--/definitions/filter/properties/--multi"/>
        Constraints: `required`: `fields,match`
        
        #multi query
        
        
        Additional properties allowed: `true`
        
        
        Properties:
        
        
         - **fields**
            `{array}` <a name="common--/definitions/filter/properties/--multi/properties/fields"/>
            Constraints: `minItems`: `1`
            
            fields
            
            
            Each item should be:
            
            
             - `{string}`Constraints: `minLength`: `1`
            
         - **match**
            `{string}`Constraints: `minLength`: `1`
            match
        
    
    
    Additional properties:
    
    
     - **oneOf**
        
        *Could be oneOf:*
        
        
         - `{string}`Constraints: `minLength`: `1`
         - `{object}` <a name="common--/definitions/filter/additionalProperties/oneOf/oneOf/1"/>
            Constraints: `minProperties`: `1`, `maxProperties`: `2`
            
            Additional properties allowed: `true`
            
            
            **Pattern properties**:
            
            
             - **^(ne|eq|match)$**
                `{string}`Constraints: `minLength`: `1`
             - **^(gte|lte)$**
                `{number}`
             - **^(some)$**
                `{array}` <a name="common--/definitions/filter/additionalProperties/oneOf/oneOf/1/patternProperties/^(some)$"/>
                Constraints: `uniqueItems`: `true`
                
                Each item should be:
                
                
                 - `{string}`Constraints: `minLength`: `1`
                
            
        
    


**[⬆ Back to Top](#top)**
## <a name='[common]-Extra-`DataTypes`'></a> [common] Extra `DataTypes`
Исходный файл [data-types.json](data-types.json).
```
SCHEMA data-types
```



### Schema



**Definitions**:


 - **data-types#/definitions/nullable-string**
    `{string,null}`


**[⬆ Back to Top](#top)**
## <a name='[common]-Sale-object'></a> [common] Sale object
Исходный файл [sale.json](sale.json).
```
SCHEMA sale
```



### Schema

`{object}` 
Constraints: `required`: `intent,payer,transactions,redirect_urls`

Additional properties allowed: `true`


Properties:


 - **id**
    `{string}`
 - **intent**
    `{string}`Constraints: `enum`: `sale,authorize,order`
 - **payer**
    <a href="#common--/definitions/payer">(common#/definitions/payer)</a>
 - **transactions**
    `{array}` <a name="sale--/properties/transactions"/>
    
    Transactions list
    
    
    Each item should be:
    
    
     - `{object}` <a name="sale--/properties/transactions/items"/>
     - Constraints: `required`: `amount`
     - 
        Additional properties allowed: `true`
        
     - 
        Properties:
        
         - **reference_id**
            `{string}`
         - **amount**
            `{object}` <a name="sale--/properties/transactions/items/properties/amount"/>
            
            Additional properties allowed: `true`
            
            
            Properties:
            
            
             - **currency**
                `{string}`
             - **total**
                `{string}`
            
         - **description**
            `{string}`
         - **note_to_payee**
            `{string}`
         - **custom**
            `{string}`
         - **invoice_number**
            `{string}`
         - **notify_url**
            `{string}`
         - **order_url**
            `{string}`
         - **item_list**
            `{object}` <a name="sale--/properties/transactions/items/properties/item_list"/>
            Constraints: `required`: `items`
            
            Additional properties allowed: `true`
            
            
            Properties:
            
            
             - **items**
                `{array}` <a name="sale--/properties/transactions/items/properties/item_list/properties/items"/>
                
                Each item should be:
                
                
                 - <a href="#common--/definitions/item">(common#/definitions/item)</a>
                
            
        
    
 - **billing_agreement_tokens**
    `{array}` <a name="sale--/properties/billing_agreement_tokens"/>
    
    Each item should be:
    
    
     - `{string}`
    
 - **experience_profile_id**
    `{string}`
 - **redirect_urls**
    `{object}` <a name="sale--/properties/redirect_urls"/>
    
    Additional properties allowed: `true`
    
    
    Properties:
    
    
     - **return_url**
        `{string}`
     - **cancel_url**
        `{string}`
    


**[⬆ Back to Top](#top)**
## <a name='[common]-Subscription-object'></a> [common] Subscription object
Исходный файл [subscription.json](subscription.json).
```
SCHEMA subscription
```



### Schema

`{object}` 
Constraints: `required`: `name,models`

Additional properties allowed: `true`


Properties:


 - **models**
    `{number}`
 - **price**
    `{number}`
 - **name**
    `{string}`Constraints: `minLength`: `1`


**[⬆ Back to Top](#top)**
## <a name='[common]:-Payment-plan-object'></a> [common]: Payment plan object
Исходный файл [plan.json](plan.json).
```
SCHEMA plan
```



### Schema

`{object}` 
Constraints: `required`: `name,description,type,payment_definitions`

Additional properties allowed: `true`


Properties:


 - **id**
    `{string}`Constraints: `minLength`: `1`
 - **name**
    `{string}`Constraints: `minLength`: `1`
 - **description**
    `{string}`Constraints: `minLength`: `1`
 - **type**
    <a href="#plan--/definitions/type">(#/definitions/type)</a>
 - **state**
    `{string}`Constraints: `minLength`: `1`
 - **create_time**
    `{string}`Constraints: `minLength`: `1`
 - **update_time**
    `{string}`Constraints: `minLength`: `1`
 - **payment_definitions**
    `{array}` <a name="plan--/properties/payment_definitions"/>
    
    Each item should be:
    
    
     - <a href="#common--/definitions/payment_definition">(common#/definitions/payment_definition)</a>
    
 - **terms**
    `{array}` <a name="plan--/properties/terms"/>
    
    Each item should be:
    
    
     - <a href="#common--/definitions/term">(common#/definitions/term)</a>
    
 - **merchant_preferences**
    <a href="#common--/definitions/merchant_preferences">(common#/definitions/merchant_preferences)</a>
 - **links**
    `{array}` <a name="plan--/properties/links"/>
    
    Each item should be:
    
    
     - <a href="#common--/definitions/links">(common#/definitions/links)</a>
    


**Definitions**:


 - **plan#/definitions/meta**
    `{object}` <a name="plan--/definitions/meta"/>
    
    Variable metadata object
    
    
    Additional properties allowed: `true`
    
    
    Additional properties should be:
    
    
    
     - <a href="#plan--/definitions/feature">(#/definitions/feature)</a>
    
    
    
 - **plan#/definitions/level**
    `{integer}`
 - **plan#/definitions/feature**
    `{object}` <a name="plan--/definitions/feature"/>
    
    Additional properties allowed: `true`
    
    
    Properties:
    
    
     - **description**
        `{string}`Constraints: `minLength`: `1`
     - **type**
        `{string}`Constraints: `enum`: `boolean,number`
     - **value**
        `{number}`
        0/1 for boolean and any other number to compare with for number type
    
 - **plan#/definitions/type**
    `{string}`Constraints: `minLength`: `1`, `enum`: `fixed,infinite,FIXED,INFINITE`


**[⬆ Back to Top](#top)**
## <a name='[response.common]-Agreement-object'></a> [response.common] Agreement object
Исходный файл [response/agreement.json](response/agreement.json).
```
SCHEMA response.common.agreement
```



### Schema

`{object}` 

Additional properties allowed: `true`


Properties:


 - **t**
    `{integer}`
    #TODO FINDOUT Something internal
 - **httpStatusCode**
    `{integer}`
 - **id**
    `{string}`Constraints: `minLength`: `1`
 - **state**
    `{string}`Constraints: `minLength`: `1`
 - **name**
    `{string}`Constraints: `minLength`: `1`
 - **description**
    `{string}`Constraints: `minLength`: `1`
 - **start_date**
    `{string}`Constraints: `minLength`: `1`
 - **agreement_details**
    <a href="#common--/definitions/agreement_details">(common#/definitions/agreement_details)</a>
 - **payer**
    <a href="#common--/definitions/payer">(common#/definitions/payer)</a>
 - **shipping_address**
    <a href="#common--/definitions/address">(common#/definitions/address)</a>
 - **override_merchant_preferences**
    <a href="#common--/definitions/merchant_preferences">(common#/definitions/merchant_preferences)</a>
 - **override_charge_models**
    `{array}` <a name="response.common.agreement--/properties/override_charge_models"/>
    
    Each item should be:
    
    
     - <a href="#common--/definitions/override_charge_model">(common#/definitions/override_charge_model)</a>
    
 - **plan**
    <a href="#response.common.plan--">(response.common.plan#)</a>
 - **create_time**
    `{string}`Constraints: `minLength`: `1`
 - **update_time**
    `{string}`Constraints: `minLength`: `1`
 - **links**
    `{array}` <a name="response.common.agreement--/properties/links"/>
    
    Each item should be:
    
    
     - <a href="#common--/definitions/links">(common#/definitions/links)</a>
    


**[⬆ Back to Top](#top)**
## <a name='[response.common]-Payment-plan-object'></a> [response.common] Payment plan object
Исходный файл [response/plan.json](response/plan.json).
```
SCHEMA response.common.plan
```



### Schema

`{object}` 

Additional properties allowed: `true`


Properties:


 - **id**
    `{string}`Constraints: `minLength`: `1`
 - **name**
    `{string}`Constraints: `minLength`: `1`
 - **description**
    `{string}`Constraints: `minLength`: `1`
 - **hidden**
    `{boolean}`
 - **type**
    <a href="#plan--/definitions/type">(plan#/definitions/type)</a>
 - **state**
    `{string}`Constraints: `minLength`: `1`
 - **create_time**
    `{string}`Constraints: `minLength`: `1`
 - **update_time**
    `{string}`Constraints: `minLength`: `1`
 - **payment_definitions**
    `{array}` <a name="response.common.plan--/properties/payment_definitions"/>
    
    Each item should be:
    
    
     - <a href="#response.common--/definitions/payment_definition">(response.common#/definitions/payment_definition)</a>
    
 - **terms**
    `{array}` <a name="response.common.plan--/properties/terms"/>
    
    Each item should be:
    
    
     - <a href="#common--/definitions/term">(common#/definitions/term)</a>
    
 - **merchant_preferences**
    <a href="#response.common--/definitions/merchant_preferences">(response.common#/definitions/merchant_preferences)</a>
 - **links**
    `{array}` <a name="response.common.plan--/properties/links"/>
    
    Each item should be:
    
    
     - <a href="#common--/definitions/links">(common#/definitions/links)</a>
    
 - **httpStatusCode**
    `{integer}`


**[⬆ Back to Top](#top)**
## <a name='[response.common]-Sale-object'></a> [response.common] Sale object
Исходный файл [response/sale.json](response/sale.json).
```
SCHEMA response.common.sale
```



### Schema

`{object}` 

Additional properties allowed: `true`


Properties:


 - **httpStatusCode**
    `{number}`
    payment system response code
 - **id**
    `{string}`
    Some id
 - **intent**
    `{string}`Constraints: `enum`: `sale,authorize,order`
    payment intent
 - **state**
    `{string}`
    #TODO
 - **payer**
    <a href="#common--/definitions/payer">(common#/definitions/payer)</a>
 - **cart**
    `{string}`
    #TODO more definite type
 - **create_time**
    `{string}`Constraints: `format`: `date-time`
 - **update_time**
    `{string}`Constraints: `format`: `date-time`
 - **transactions**
    `{array}` <a name="response.common.sale--/properties/transactions"/>
    
    Each item should be:
    
    
     - <a href="#response.common.sale--/definitions/transaction">(#/definitions/transaction)</a>
    
 - **failed_transactions**
    `{array}` <a name="response.common.sale--/properties/failed_transactions"/>
    
    Each item should be:
    
    
     - <a href="#response.common.sale--/definitions/transaction">(#/definitions/transaction)</a>
    
 - **billing_agreement_tokens**
    `{array}` <a name="response.common.sale--/properties/billing_agreement_tokens"/>
    
    Each item should be:
    
    
     - `{string}`
    
 - **experience_profile_id**
    `{string}`
 - **links**
    `{array}` <a name="response.common.sale--/properties/links"/>
    
    Each item should be:
    
    
     - <a href="#common--/definitions/links">(common#/definitions/links)</a>
    


**Definitions**:


 - **response.common.sale#/definitions/transaction**
    `{object}` <a name="response.common.sale--/definitions/transaction"/>
    
    Additional properties allowed: `true`
    
    
    Properties:
    
    
     - **reference_id**
        `{string}`
     - **amount**
        `{object}` <a name="response.common.sale--/definitions/transaction/properties/amount"/>
        
        Additional properties allowed: `true`
        
        
        Properties:
        
        
         - **currency**
            `{string}`
         - **total**
            `{number,string}`
        
     - **description**
        `{string}`
     - **note_to_payee**
        `{string}`
     - **custom**
        `{string}`
     - **invoice_number**
        `{string}`
     - **notify_url**
        `{string}`
     - **order_url**
        `{string}`
     - **item_list**
        `{object}` <a name="response.common.sale--/definitions/transaction/properties/item_list"/>
        Constraints: `required`: `items`
        
        Additional properties allowed: `true`
        
        
        Properties:
        
        
         - **additionalProperties**
            
         - **items**
            `{array}` <a name="response.common.sale--/definitions/transaction/properties/item_list/properties/items"/>
            
            Each item should be:
            
            
             - <a href="#response.common--/definitions/transaction_item">(response.common#/definitions/transaction_item)</a>
            
        
     - **related_resources**
        `{array}` <a name="response.common.sale--/definitions/transaction/properties/related_resources"/>
        
        Each item should be:
        
        
         - `{any}`
        
    


**[⬆ Back to Top](#top)**
## <a name='[response.common]-Subscription-object'></a> [response.common] Subscription object
Исходный файл [response/subscription.json](response/subscription.json).
```
SCHEMA response.common.subscription
```



### Schema

`{object}` 
Constraints: `required`: `name,models,definition,price`

Additional properties allowed: `true`


Properties:


 - **models**
    `{number}`
 - **price**
    `{number}`
 - **name**
    `{string}`Constraints: `minLength`: `1`
 - **definition**
    <a href="#common--/definitions/payment_definition">(common#/definitions/payment_definition)</a>


**[⬆ Back to Top](#top)**
## <a name='[response.common]-Transaction-common-information-object'></a> [response.common] Transaction common information object
Исходный файл [response/transaction-common.json](response/transaction-common.json).
```
SCHEMA response.common.transaction-common
```



### Schema

`{object}` 

Additional properties allowed: `true`


Properties:


 - **id**
    `{string}`
 - **type**
    `{number}`
 - **owner**
    <a href="#common--/definitions/owner">(common#/definitions/owner)</a>
 - **agreementId**
    `{string}`
 - **payer**
    `{string}`Constraints: `format`: `email`
 - **date**
    `{number}`
 - **amount**
    `{string}`
 - **description**
    `{string}`
 - **status**
    `{string}`


**[⬆ Back to Top](#top)**
## <a name='[response.common]-Transaction-information-object'></a> [response.common] Transaction information object
Исходный файл [response/transaction-info.json](response/transaction-info.json).
```
SCHEMA response.common.transaction-info
```



### Schema

`{object}` 

Additional properties allowed: `true`


Properties:


 - **transaction_id**
    `{string}`
 - **status**
    `{string}`
 - **transaction_type**
    `{string}`
 - **payer_email**
    `{string}`Constraints: `format`: `email`
 - **payer_name**
    `{string}`
 - **time_stamp**
    `{string}`Constraints: `format`: `date-time`
 - **time_zone**
    `{string}`
 - **amount**
    <a href="#response.common--/definitions/amount">Amount(response.common#/definitions/amount)</a>
 - **fee_amount**
    <a href="#response.common--/definitions/amount">Fee amount(response.common#/definitions/amount)</a>
 - **net_amount**
    <a href="#response.common--/definitions/amount">Net amount(response.common#/definitions/amount)</a>


**[⬆ Back to Top](#top)**
## <a name='[response.common]-Transaction-object'></a> [response.common] Transaction object
Исходный файл [response/transaction.json](response/transaction.json).
```
SCHEMA response.common.transaction
```



### Schema

`{object}` 

Additional properties allowed: `true`


Properties:


 - **agreement**
    `{string}`
 - **payer_email**
    `{string}`Constraints: `format`: `email`
 - **status**
    `{string}`
 - **owner**
    <a href="#common--/definitions/owner">(common#/definitions/owner)</a>
 - **transaction_type**
    `{string}`
 - **transaction**
    <a href="#response.common.transaction-info--">(response.common.transaction-info#)</a>
 - **time_stamp**
    `{number}`


**[⬆ Back to Top](#top)**
# <a name='Transaction'></a> Transaction
## <a name='Aggregate-transaction'></a> Aggregate transaction
<p>Performs aggregate operation on filtered transactions</p>

Исходный файл [src/actions/transaction/aggregate.js](src/actions/transaction/aggregate.js).
```
AMQP &lt;prefix&gt;.transaction.aggregate
```


### Request schema

`{object}` 
Constraints: `required`: `owners,aggregate`

Additional properties allowed: `true`


Properties:


 - **owners**
    `{array}` <a name="transaction.aggregate--/properties/owners"/>
    Constraints: `minItems`: `1`
    
    Each item should be:
    
    
     - <a href="#common--/definitions/owner">(common#/definitions/owner)</a>
    
 - **filter**
    <a href="#common--/definitions/filter">(common#/definitions/filter)</a>
 - **aggregate**
    `{object}` <a name="transaction.aggregate--/properties/aggregate"/>
    Constraints: `minProperties`: `1`
    
    Additional properties allowed: `true`
    
    
    Additional properties should be:
    
    
    
     - `{string}`Constraints: `enum`: `sum`
    
    
    


### Response schema:

`{array}` 

Each item should be:


 - `{object}` 
 - 
    Additional properties allowed: `true`
    
 - 
    Properties:
    
     - **amount**
        `{number}`
    





**[⬆ Back to Top](#top)**
## <a name='Common-transaction-data'></a> Common transaction data
<p>Retrieves common transaction information for filtered transactions</p>

Исходный файл [src/actions/transaction/common.js](src/actions/transaction/common.js).
```
AMQP &lt;prefix&gt;.transaction.common
```


### Request schema

`{object}` 

Additional properties allowed: `true`


Properties:


 - **offset**
    `{integer}`Constraints: `minimum`: `0`
 - **limit**
    `{integer}`Constraints: `minimum`: `1`, `maximum`: `100`
 - **order**
    `{string}`Constraints: `enum`: `ASC,DESC`
 - **criteria**
    `{string}`
 - **owner**
    <a href="#common--/definitions/owner">(common#/definitions/owner)</a>
 - **type**
    `{string}`Constraints: `enum`: `sale,subscription`
 - **filter**
    <a href="#common--/definitions/filter">(common#/definitions/filter)</a>


### Response schema:

`{object}` 
Constraints: `required`: `items,cursor,page,pages`

Additional properties allowed: `true`


Properties:


 - **items**
    `{array}` <a name="response.transaction.common--/properties/items"/>
    
    Each item should be:
    
    
     - <a href="#response.common.transaction-common--">(response.common.transaction-common#)</a>
    
 - **cursor**
    `{number}`
 - **page**
    `{number}`
 - **pages**
    `{number}`





**[⬆ Back to Top](#top)**
## <a name='Get-transaction'></a> Get transaction
<p>Returns selected trasactions common data</p>

Исходный файл [src/actions/transaction/get.js](src/actions/transaction/get.js).
```
AMQP &lt;prefix&gt;.transaction.get
```


### Request schema

`{object}` 
Constraints: `required`: `owners,aggregate`

Additional properties allowed: `true`


Properties:


 - **owners**
    `{array}` <a name="transaction.aggregate--/properties/owners"/>
    Constraints: `minItems`: `1`
    
    Each item should be:
    
    
     - <a href="#common--/definitions/owner">(common#/definitions/owner)</a>
    
 - **filter**
    <a href="#common--/definitions/filter">(common#/definitions/filter)</a>
 - **aggregate**
    `{object}` <a name="transaction.aggregate--/properties/aggregate"/>
    Constraints: `minProperties`: `1`
    
    Additional properties allowed: `true`
    
    
    Additional properties should be:
    
    
    
     - `{string}`Constraints: `enum`: `sum`
    
    
    


### Response schema:

`{array}` 

Each item should be:


 - `{object}` 
 - 
    Additional properties allowed: `true`
    
 - 
    Properties:
    
     - **amount**
        `{number}`
    





**[⬆ Back to Top](#top)**
## <a name='List-transactions'></a> List transactions
<p>Return the list of the agreement transactions data</p>

Исходный файл [src/actions/transaction/list.js](src/actions/transaction/list.js).
```
AMQP &lt;prefix&gt;.transaction.list
```


### Request schema

`{object}` 

Additional properties allowed: `true`


Properties:


 - **offset**
    `{integer}`Constraints: `minimum`: `0`
 - **limit**
    `{integer}`Constraints: `minimum`: `1`, `maximum`: `100`
 - **filter**
    <a href="#common--/definitions/filter">(common#/definitions/filter)</a>
 - **criteria**
    `{string}`Constraints: `minLength`: `1`
 - **order**
    `{string}`Constraints: `enum`: `ASC,DESC`
 - **owner**
    <a href="#common--/definitions/owner">(common#/definitions/owner)</a>


### Response schema:

`{object}` 
Constraints: `required`: `items,cursor,page,pages`

Additional properties allowed: `true`


Properties:


 - **items**
    `{array}` <a name="response.transaction.list--/properties/items"/>
    
    Each item should be:
    
    
     - <a href="#response.common.transaction--">(response.common.transaction#)</a>
    
 - **cursor**
    `{number}`
 - **page**
    `{number}`
 - **pages**
    `{number}`





**[⬆ Back to Top](#top)**
## <a name='Sync-transactions'></a> Sync transactions
<p>Syncs transactions for agreement</p>

Исходный файл [src/actions/transaction/sync.js](src/actions/transaction/sync.js).
```
AMQP &lt;prefix&gt;.transaction.sync
```


### Request schema

`{object}` 
Constraints: `required`: `id`

Additional properties allowed: `true`


Properties:


 - **owner**
    <a href="#common--/definitions/owner">(common#/definitions/owner)</a>
 - **id**
    `{string}`Constraints: `minLength`: `1`
 - **start**
    `{string}`Constraints: `format`: `date`
 - **end**
    `{string}`Constraints: `format`: `date`


### Response schema:

`{object}` 

Additional properties allowed: `true`


Properties:


 - **agreement**
    <a href="#response.common.agreement--">(response.common.agreement#)</a>
 - **transactions**
    `{array}` <a name="response.transaction.sync--/properties/transactions"/>
    
    Each item should be:
    
    
     - <a href="#response.common.transaction-info--">(response.common.transaction-info#)</a>
    





**[⬆ Back to Top](#top)**
## <a name='Sync-Updated-transactions'></a> Sync Updated transactions
<p>Syncs updated transactions for agreement</p>

Исходный файл [src/actions/transaction/sync-updated.js](src/actions/transaction/sync-updated.js).
```
AMQP &lt;prefix&gt;.transaction.sync-updated
```


### Request schema

`{object}` 

Additional properties allowed: `true`


### Response schema:

`{number}`




**[⬆ Back to Top](#top)**
