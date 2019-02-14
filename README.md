
# Demo Service Endpoint Details

[![N|Solid](https://cldup.com/dTxpPi9lDf.thumb.png)](https://nodesource.com/products/nsolid)

[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)

![alt text](https://github.com/gazi-opu/Files/blob/master/paymentGateway.png)

![Image of Yaktocat](https://octodex.github.com/images/yaktocat.png)

## Demo Service
   - IP  : 192.168.1.217
   - Context-Path: /demo-service
  
## Simulator Service
   - IP  : 192.168.1.217
   - Context-Path: /simulator-service
    
   ## JSON Production Test API
   ```sh
 Endpoint: http://192.168.1.217:demo-service/testJson 
   Request Type: GET
   Response Sample:  {
    "id": 1,
    "name": "Australia",
    "isStateExist": true
}
   Content-Type : application/json
```
  
  ## JSON Consumes API Test
   ```sh
 Endpoint: http://192.168.1.217:demo-service/testJson 
   Request Type: POST
   Request Body: {"id":"5","name":"BD","isStateExist":"false"}
   Response Sample:  {
    "id": 5,
    "name": "BD",
    "isStateExist": false
}
   Content-Type : application/json
```

## Simulator Service Running Test API

  ```sh
 Endpoint: http://192.168.1.217:demo-service/simulator
   Request Type: GET
   Response Sample:  Simulation service is running on the background
   Content-Type : application/json
```

## User sample Request with Audit
  ```sh
   Endpoint: http://192.168.1.217:demo-service/addInfo
   Request Type: POST
    Request Body: {"body":"Message"}
   Response Sample:  {
    "id": 74,
    "serviceName": "demo-service",
    "apiEndpoint": "/demo-service/addInfo",
    "headers": null,
    "body": "ApiInfo(id=null, serviceName=demo-service, apiEndpoint=/demo-service/addInfo, headers=null, body=Message, responseCode=200, remoteIp=0:0:0:0:0:0:0:1, destinationIp=null, date=null)",
    "responseCode": 200,
    "remoteIp": "0:0:0:0:0:0:0:1",
    "destinationIp": null,
    "date": null
}
   Content-Type : application/json
```

 ## Redirect User Request to Another Service or API (A GET Request Sample)
 
   ```sh
   Endpoint: http://192.168.1.217:demo-service/redirectGetToGET
   Request Type: GET
   Response Sample:  Service has been redirected to another api and business successfully processed
   Content-Type : application/json
```
 ## Redirect User Request to Another Service or API (A Post To Post Request Sample)
 
   ```sh
   Endpoint: http://192.168.1.217:demo-service/redirectToAnotherApi
   Request Type: POST
   Request Body: {"id":"5","name":"BD","isStateExist":"false"}
   Response Sample:  Service has been redirected to another post api and business successfully processed
   Content-Type : application/json
```


## Paypal Demo Service integration
   - IP  : 192.168.1.217
   - Context-Path: /paypal
  
 ## Purchase items from store and paying the bills sample api 

   ```sh
   Endpoint: http://192.168.1.217:paypal/order-details
   Request Type: POST
   Request Body: {  
            "items":[  
               {  
                  "name":"hat",
                  "description":"Brown hat.",
                  "quantity":5,
                  "price":3.0,
                  "tax":0.01,
                  "sku":"1",
                  "currency":"USD"
               },
               {  
                  "name":"handbag",
                  "description":"Black handbag.",
                  "quantity":1,
                  "price":15.0,
                  "tax":0.02,
                  "sku":"product34",
                  "currency":"USD"
               }
            ],
            "shipping_address":{  
               "recipient_name":"Brian Robinson",
               "line1":"4th Floor",
               "line2":"Unit #34",
               "city":"San Jose",
               "country_code":"US",
               "postal_code":"95131",
               "state":"CA",
               "phone":"011862212345678"
            }
         }
   Response Sample:  {
    "id": "PAYID-LRQRJ5I0WC2851103080803T",
    "create_time": "2019-02-11T06:23:49Z",
    "state": "created",
    "intent": "sale",
    "payer": {
        "payment_method": "paypal"
    },
    "transactions": [
        {
            "amount": {
                "total": "30.11",
                "currency": "USD",
                "details": {
                    "subtotal": "30.00",
                    "tax": "0.07",
                    "shipping": "0.03",
                    "handling_fee": "1.00",
                    "shipping_discount": "-1.00",
                    "insurance": "0.01"
                }
            },
            "description": "The payment transaction description.",
            "custom": "EBAY_EMS_90048630024435",
            "invoice_number": "48787589673",
            "payment_options": {
                "allowed_payment_method": "INSTANT_FUNDING_SOURCE"
            },
            "soft_descriptor": "ECHI5786786",
            "item_list": {
                "items": [
                    {
                        "name": "hat",
                        "description": "Brown hat.",
                        "quantity": "5",
                        "price": "3.00",
                        "tax": "0.01",
                        "sku": "1",
                        "currency": "USD"
                    },
                    {
                        "name": "handbag",
                        "description": "Black handbag.",
                        "quantity": "1",
                        "price": "15.00",
                        "tax": "0.02",
                        "sku": "product34",
                        "currency": "USD"
                    }
                ],
                "shipping_address": {
                    "recipient_name": "Brian Robinson",
                    "line1": "4th Floor",
                    "line2": "Unit #34",
                    "city": "San Jose",
                    "country_code": "US",
                    "postal_code": "95131",
                    "state": "CA",
                    "phone": "011862212345678"
                }
            }
        }
    ],
    "note_to_payer": "Contact us for any questions on your order.",
    "links": [
        {
            "href": "https://api.sandbox.paypal.com/v1/payments/payment/PAYID-LRQRJ5I0WC2851103080803T",
            "rel": "self",
            "method": "GET"
        },
        {
            "href": "https://www.sandbox.paypal.com/cgi-bin/webscr?cmd=_express-checkout&token=EC-8YY68119P3664330N",
            "rel": "approval_url",
            "method": "REDIRECT"
        },
        {
            "href": "https://api.sandbox.paypal.com/v1/payments/payment/PAYID-LRQRJ5I0WC2851103080803T/execute",
            "rel": "execute",
            "method": "POST"
        }
    ]
}
   Content-Type : application/json
```
