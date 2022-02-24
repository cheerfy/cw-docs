---
description: >-
  Encuentra aquí toda la información necesaria para la integración de tu tarjeta
  de fidelización con el TPV de tu local.
---

# API Tarjeta de Fidelización

**Índice**

1. Definición Tarjeta de Fidelización
   1. Parámetros
   2. Contenido
   3. Ejemplo\

2. Definición servicio Web
   1. Asignación de un ticket a un usuario en Cheerfy

## 1. Definición Tarjeta de Fidelización

### 1.1. Parámetros

Una tarjeta de fidelización deberá contener obligatoriamente 1 parámetro:

{% hint style="info" %}
**user\_id : Identificador único** que identifica **al cliente** (en Cheerfy).
{% endhint %}

&#x20;**** El formato del user\_id es un campo alfanumérico con un número variable de caracteres.

### 1.2. Contenido

El QR code contendrá el parámetro definido en la sección "Parámetros" sin saltos de línea.

El contenido al escanear un código QR (o de barras) de una tarjeta de fidelización debería ser algo parecido a esto (es un mero ejemplo):

```
7a49cvbg2740mnr3
```

### 1.3. Ejemplo

Adjuntamos un código QR, con el código de ejemplo anterior, por si es necesario hacer una prueba por parte del proveedor del TPV.

![](https://lh6.googleusercontent.com/FJo2yJawg3W3FU-4MFSgH8\_tcpsmzOmnSOlBmAEPmMuRcIfB50X7G9kjL-gC60sB09k1i9p2QZPs9jSRcisAMHashBYaso0GV\_w1F7SY90ugdkiuMsgZwm4CChaoef0CUXXDOXm7=s0)

## 2. Definición servicios Web

Las llamadas desde el TPV a Cheerfy se harán mediante servicios Web de tipo REST y con contenido definido en formato JSON.&#x20;

Cada llamada deberá contener una serie de parámetros obligatorios en la cabecera (además de los propios parámetros del servicio que se invoque), estos parámetros de la cabecera indicarán:

1\. El contenido tiene formato JSON

```
Content-Type: application/json
```

2\. Los datos de autenticación de la llamada

```
Authorization: Token replace_by_your_token_code_here
```

### **2.1. Asignación de un ticket a un usuario en Cheerfy**

Una vez el TPV escanea un código de tarjeta de fidelización (user\_id), se lo tiene que comunicar a Cheerfy conjuntamente con el ticket de su transacción. Y, para ello, necesita llamar a un servicio Web REST.&#x20;

La respuesta en el caso de error, por ahora no contendrá datos del estado de la tarjeta de fidelización (ej. cancelada), ya que Cheerfy muestra esa información en la tarjeta de fidelización, no obstante, es un dato que podría incluirse en próximas versiones.

* URL

```
https://backend.cheerfy.com/ticket/
```

* Método HTTP

```
POST
```

* **Parámetros de la cabecera:**

| **Field**     | **Type** | **Description**                                        |
| ------------- | -------- | ------------------------------------------------------ |
| Content-Type  | String   | Data application raw type.                             |
| Authorization | String   | Admin unique access-key (Content must start by Token). |

* **Parámetros de la llamada:**

| **Field**                               | **Type**  | **Description**                                                                                                                                                                                                                |
| --------------------------------------- | --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| id                                      | String    | Ticket unique identifier. Can be a string, it should be unique within the organization                                                                                                                                         |
| ticket\_numberoptional                  | Number    | Ticket identifier. Not necessarily unique                                                                                                                                                                                      |
| rectification\_idoptional               | String    | Ticket unique identifier from the rectification ticket (total or partial refund). Can be a string, it should be unique within the organization                                                                                 |
| created\_atoptional                     | Long      | Timestamp when the ticket was created, format UNIX epoch, Example: 1419992910. If not present, set current datetime                                                                                                            |
| status                                  | Number    | Ticket current status. Values: TICKET\_STATUS\_REQUESTED = 3, TICKET\_STATUS\_CANCELLED = 2, TICKET\_STATUS\_CONFIRMED = 4, TICKET\_STATUS\_READY = 5, TICKET\_STATUS\_ON\_ROUTE = 6, TICKET\_STATUS\_COMPLETED = 1            |
| channeloptional                         | Number    | API request origin. Values: 1- SHOP (TPV) (default), 2 - ONLINE (Web, APP, etc)                                                                                                                                                |
| nameoptional                            | String    | Given name (human readable) to the ticket                                                                                                                                                                                      |
| additional\_dataoptional                | String    | Place here any relevant information you want to persist into the system                                                                                                                                                        |
| summary                                 | Object    | Ticket summary data                                                                                                                                                                                                            |
|   subtotal                              | Number    | Total amount before taxes and fees (only apply to ticket items. Format is a number. Value unit is in cents, it means that if you have 10.56€ value will be 1056, while a value of 15€ will be 1500                             |
|   service\_feeoptional                  | Number    | Service fee amount before taxes. Format is a number. Value unit is in cents, it means that if you have 1.60€ value will be 160, while a value of 0.95€ will be 95                                                              |
|   other\_feesoptional                   | Number    | Other fees not included into subtotal or service fee. Format is a number. Value unit is in cents, it means that if you have 0.30€ value will be 30, while a value of 0.05€ will be 5                                           |
|   taxes                                 | Number    | Taxes amount applied to all the ticket items and fees. Format is a number. Value unit is in cents, it means that if you have 2.75€ value will be 275, while a value of 1.9€ will be 190                                        |
|   tipoptional                           | Number    | Tips amount, this value does not implies taxes. Format is a number. Value unit is in cents, it means that if you have 5€ value will be 500, while a value of 2.99€ will be 299                                                 |
|   total                                 | Number    | Total amount including taxes, fees and tips, it is the price which the user has to pay. Format is a number. Value unit is in cents, it means that if you have 150.20€ value will be 15020, while a value of 75.79 will be 7579 |
|   due                                   | Number    | Amount given by the user. Format is a number. Value unit is in cents, it means that if you have 150.20€ value will be 15020, while a value of 75.79 will be 7579                                                               |
|   discount\_amountoptional              | Number    | Total discount applied to the ticket. Format is a number. Value unit is in cents, it means that if you have 150.20€ value will be 15020, while a value of 75.79 will be 7579                                                   |
|   currency                              | String    | 3 letters ISO 4217 Code for currencies, upper case value. https://www.iso.org/iso-4217-currency-codes.html                                                                                                                     |
| deliveryoptional                        | Object    | Ticket delivery data if any                                                                                                                                                                                                    |
|   pick\_up\_address                     | String    | Address where the order needs to be picked up. Exclude fields typically added as address line 2 such as building block or door number                                                                                          |
|   pick\_up\_atoptional                  | Long      | Timestamp when the order has to be picked up, format UNIX epoch, Example: 1419992910. If not present, set current datetime                                                                                                     |
|   drop\_off\_address                    | String    | Address where the order needs to be dropped off                                                                                                                                                                                |
|   drop\_off\_address\_latitudeoptional  | Float     | Geo latitude of the drop off address                                                                                                                                                                                           |
|   drop\_off\_address\_longitudeoptional | Float     | Geo longitude of the drop off address                                                                                                                                                                                          |
|   drop\_off\_atoptional                 | Long      | Timestamp when the order has to be dropped off, format UNIX epoch, Example: 1419992910. If not present, set current datetime                                                                                                   |
|   drop\_off\_notesoptional              | String    | Address or delivery additional notes                                                                                                                                                                                           |
|   contact\_phone\_numberoptional        | String    | Contact user phone for courier usage                                                                                                                                                                                           |
| serviceoptional                         | Object    | Ticket service data                                                                                                                                                                                                            |
|   service\_type                         | Number    | Service type. Values: 1 - DELIVERY, 2 - TAKE AWAY, 3 - DINE IN, 4 - BOOKING                                                                                                                                                    |
|   table\_id                             | String    | Shop table id, usually attached to Dine in service type                                                                                                                                                                        |
|   ready\_at                             | Long      | Timestamp when the order needs to be ready, format UNIX epoch, Example: 1419992910. If not present, set current datetime                                                                                                       |
|   now                                   | Boolean   | Service type now true or false                                                                                                                                                                                                 |
| payments                                | Object\[] | List of payment items included into the ticket                                                                                                                                                                                 |
|   type                                  | Number    | Values: 1 - CASH, 2 - CREDIT CARD, 3 - OTHERS                                                                                                                                                                                  |
|   amount                                | Number    | Total amount paid by the user. Format is a number. Value unit is in cents, it means that if you have 10.56€ value will be 1056, while a value of 15€ will be 1500                                                              |
|   card\_detailsoptional                 | String    | Credit card details (masked) in case type is 2                                                                                                                                                                                 |
|   idoptional                            | Number    | Payment unique identifier, if available                                                                                                                                                                                        |
|   useroptional                          | Object    | User information - optional field                                                                                                                                                                                              |
|     idoptional                          | String    | Unique user identifier                                                                                                                                                                                                         |
|     external\_idoptional                | String    | Unique external user identifier                                                                                                                                                                                                |
|     emailoptional                       | String    | User email                                                                                                                                                                                                                     |
|     phoneoptional                       | String    | User phone number                                                                                                                                                                                                              |
|     nameoptional                        | String    | User first name, utf-8 encoding                                                                                                                                                                                                |
|     surnameoptional                     | String    | User surname, utf-8 encoding                                                                                                                                                                                                   |
|     addressoptional                     | String    | User full address                                                                                                                                                                                                              |
|     cityoptional                        | String    | Address city                                                                                                                                                                                                                   |
|     zipcodeoptional                     | String    | Address zipcode                                                                                                                                                                                                                |
|     countryoptional                     | String    | Address country. Format ISO 3166 alpha 2 codes (UPPERCASE) https://www.iso.org/iso-3166-country-codes.html                                                                                                                     |
|     languageoptional                    | String    | User language. Format ISO 639 alpha 2 codes (LOWERCASE) https://www.iso.org/iso-639-language-codes.html                                                                                                                        |
|     genderoptional                      | Number    | User gender. Values: 1 - MALE, 2 - FEMALE, 3 - OTHER, 4 - N/A                                                                                                                                                                  |
| items                                   | Object\[] | List of items included into the ticket                                                                                                                                                                                         |
|   item\_idoptional                      | String    | Unique product item identifier from the list of items. Example: item order from ticket                                                                                                                                         |
|   ref\_item\_idoptional                 | String    | Reference to unique product item id, in case, current item is attached to another ticket item. Example: Promotion applied to a parent item id                                                                                  |
|   sku\_codeoptional                     | String    | External product item identifier                                                                                                                                                                                               |
|   nameoptional                          | String    | Human readable product item name                                                                                                                                                                                               |
|   voucher\_codeoptional                 | String    | Promotion unique identifier. Example: User has a promotional code and attached to the ticket order                                                                                                                             |
|   quantity                              | Number    | Number of same items into the ticket                                                                                                                                                                                           |
|   subtotal                              | Number    | Total amount before taxes applied to the current ticket item. Format is a number. Value unit is in cents, it means that if you have 10.56€ value will be 1056, while a value of 15€ will be 1500                               |
|   taxes                                 | Number    | Taxes amount applied to the current ticket item. Format is a number. Value unit is in cents, it means that if you have 2.75€ value will be 275, while a value of 1.9€ will be 190                                              |
|   total                                 | Number    | Total amount after taxes applied to the current ticket item. Format is a number. Value unit is in cents, it means that if you have 10.56€ value will be 1056, while a value of 15€ will be 1500                                |
|   modifiersoptional                     | Object\[] | List of item modifiers included into the ticket item                                                                                                                                                                           |
|     sku\_codeoptional                   | String    | External product modifier identifier                                                                                                                                                                                           |
|     nameoptional                        | String    | Human readable product modifier name                                                                                                                                                                                           |
|     quantity                            | Number    | Number of same modifier into the item                                                                                                                                                                                          |
|     subtotaloptional                    | Number    | Total amount before taxes applied to the current item modifier. Format is a number. Value unit is in cents, it means that if you have 10.56€ value will be 1056, while a value of 15€ will be 1500                             |
|     taxesoptional                       | Number    | Taxes amount applied to the current item modifier. Format is a number. Value unit is in cents, it means that if you have 2.75€ value will be 275, while a value of 1.9€ will be 190                                            |
|     totaloptional                       | Number    | Total amount after taxes applied to the current item modifier. Format is a number. Value unit is in cents, it means that if you have 10.56€ value will be 1056, while a value of 15€ will be 1500                              |
| combos                                  | Object\[] | List of combos included into the ticket                                                                                                                                                                                        |
|   item\_idoptional                      | String    | Unique combo item identifier from the list of items. Example: item order from ticket                                                                                                                                           |
|   ref\_item\_idoptional                 | String    | Reference to unique combo item id, in case, current item is attached to another ticket item. Example: Promotion applied to a parent item id                                                                                    |
|   sku\_codeoptional                     | String    | External combo item identifier                                                                                                                                                                                                 |
|   nameoptional                          | String    | Human readable combo item name                                                                                                                                                                                                 |
|   voucher\_codeoptional                 | String    | Promotion unique identifier. Example: User has a promotional code and attached to the ticket order                                                                                                                             |
|   quantity                              | Number    | Number of same combo into the ticket                                                                                                                                                                                           |
|   subtotal                              | Number    | Total amount before taxes applied to the current ticket combo. Format is a number. Value unit is in cents, it means that if you have 10.56€ value will be 1056, while a value of 15€ will be 1500                              |
|   taxes                                 | Number    | Taxes amount applied to the current ticket combo. Format is a number. Value unit is in cents, it means that if you have 2.75€ value will be 275, while a value of 1.9€ will be 190                                             |
|   total                                 | Number    | Total amount after taxes applied to the current ticket combo. Format is a number. Value unit is in cents, it means that if you have 10.56€ value will be 1056, while a value of 15€ will be 1500                               |
|   modifiersoptional                     | Object\[] | List of item modifiers included into the ticket combo                                                                                                                                                                          |
|     sku\_codeoptional                   | String    | External combo modifier identifier                                                                                                                                                                                             |
|     nameoptional                        | String    | Human readable combo modifier name                                                                                                                                                                                             |
|     quantity                            | Number    | Number of same modifier into the item                                                                                                                                                                                          |
|     subtotaloptional                    | Number    | Total amount before taxes applied to the current combo modifier. Format is a number. Value unit is in cents, it means that if you have 10.56€ value will be 1056, while a value of 15€ will be 1500                            |
|     taxesoptional                       | Number    | Taxes amount applied to the current combo modifier. Format is a number. Value unit is in cents, it means that if you have 2.75€ value will be 275, while a value of 1.9€ will be 190                                           |
|     totaloptional                       | Number    | Total amount after taxes applied to the current combo modifier. Format is a number. Value unit is in cents, it means that if you have 10.56€ value will be 1056, while a value of 15€ will be 1500                             |
|     itemsoptional                       | Item\[]   | List of items included into the combo - same definition than Item object                                                                                                                                                       |
| ticket\_promotion\_listoptional         | Object    | List of promotions included into the ticket                                                                                                                                                                                    |
|   code                                  | String    | Code of the promotion                                                                                                                                                                                                          |
|   generated\_idoptional                 | String    | Unique ID generated after user apply a promotion code                                                                                                                                                                          |
|   nameoptional                          | String    | Name of the promotion                                                                                                                                                                                                          |
|   promotion\_type                       | Number    | Promotion type. Values: 1 - FIXED\_DISCOUNT, 2 - PERCENT\_DISCOUNT                                                                                                                                                             |
|   valueoptional                         | String    | Percentage or fixed value depending on promotion\_type                                                                                                                                                                         |
| client\_dataoptional                    | Object    | Client data belongs to the app which invokes the service. The parameter must include at least these parameters (you can include as much as you need for debugging): client\_type (ANDROID, WEB or IOS) and client\_version     |
| scope                                   | Object    | Virtual geographical scope belong to the given request                                                                                                                                                                         |
|   locations                             | Number\[] | List of selected locations                                                                                                                                                                                                     |

* **Ejemplo llamada:**

```
curl -X POST https://backendbeta.cheerfy.com/ticket/ 
-d 
'
{
  "id":"12345ABCDE",
  "ticket_number":12345,
  "rectification_id":"12345AAAAA",
  "created_at":1419992910,
  "channel":1,
  "status":1,
  "name":"lunch meal",
  "additional_data":"here you can place any info you want",
  "summary":{
    "subtotal":1000,
    "service_fee":100,
    "other_fees":0,
    "taxes":110,
    "tip":200,
    "total":1410,
    "due":1410,
    "discount_amount":100,
    "currency":"EUR"
  },
  "delivery":{
    "pick_up_address":"Avenida Ciudad de Barcelona 5, 28007 Madrid",
    "pick_up_at":1419992910,
    "drop_off_address":"Avenida Canillejas a Vicálvaro 15, 28022 Madrid",
    "drop_off_address_latitude":40.4625427,
    "drop_off_address_longitude":-3.6886626,
    "drop_off_at":1419993910,
    "drop_off_notes":"Block 5, 4th floor. Ask Tommy",
    "contact_phone_number":"+33999999888"
  },
  "service":{
    "service_type":1,
    "table_id":"Table 1",
    "ready_at":1419992910,
    "now":true
  },
  "payments":[
    {
      "type":1,
      "card_details":"1234*****5678****",
      "amount":1410,
      "payment_id":"987654321ABCD",
      "summary":"processed with my epayment platform",
      "user":{
        "id":"786GHJKL323",
        "external_id":"external_23434-434kjkdrf",
        "email":"user@email.com",
        "phone":"+33999999888",
        "name":"John",
        "surname":"Smith",
        "address":"Fifth Avenue 123, 34A, New York",
        "city":"Madrid",
        "zipcode":"28006",
        "country":"ES",
        "language":"es",
        "gender":1
      }
    },
    {
      "type":2,
      "card_details":"1234*****5678****",
      "amount":1410,
      "payment_id":"987654321ABCD",
      "summary":"processed with my epayment platform",
      "user":{
        "id":"786GHJKL323",
        "external_id":"external_23434-434kjkdrf",
        "email":"user@email.com",
        "phone":"+33999999888",
        "name":"John",
        "surname":"Smith",
        "address":"Fifth Avenue 123, 34A, New York",
        "city":"Madrid",
        "zipcode":"28006",
        "country":"ES",
        "language":"es",
        "gender":1
      }
    }
  ],
  "items":[
    {
      "item_id":"1",
      "ref_item_id":null,
      "sku_code":"DRINK_001_LIGHT",
      "name":"Pepsi Light 33cl",
      "voucher_code":"123456abcd",
      "quantity":2,
      "subtotal":400,
      "taxes":80,
      "total":480,
      "modifiers":[
        {
          "sku_code":"MODIFIER_ID_001",
          "name":"Extra ice",
          "quantity":1,
          "subtotal":10,
          "taxes":1,
          "total":11
        }
      ]
    },
    {
      "item_id":"2",
      "ref_item_id":null,
      "sku_code":"SANDWICH_047_SALT",
      "name":"Bacon and cheese sandwich",
      "voucher_code":null,
      "quantity":1,
      "subtotal":200,
      "taxes":20,
      "total":220
    }
  ],
  "combos":[
    {
      "item_id":"1",
      "ref_item_id":null,
      "sku_code":"COMBO_001",
      "name":"Daily menu",
      "voucher_code":"123456abcd",
      "quantity":1,
      "subtotal":4000,
      "taxes":800,
      "total":4800,
      "modifiers":[
        {
          "sku_code":"MODIFIER_ID_001",
          "name":"Extra ice",
          "quantity":1,
          "subtotal":10,
          "taxes":1,
          "total":11
        }
      ],
      "items":[
        {
          "item_id":"1",
          "ref_item_id":null,
          "sku_code":"DRINK_001_LIGHT",
          "name":"Pepsi Light 33cl",
          "voucher_code":"123456abcd",
          "quantity":2,
          "subtotal":400,
          "taxes":80,
          "total":480,
          "modifiers":[
            {
              "sku_code":"MODIFIER_ID_001",
              "name":"Extra ice",
              "quantity":1,
              "subtotal":10,
              "taxes":1,
              "total":11
            }
          ]
        },
        {
          "item_id":"2",
          "ref_item_id":null,
          "sku_code":"SANDWICH_047_SALT",
          "name":"Bacon and cheese sandwich",
          "voucher_code":null,
          "quantity":1,
          "subtotal":200,
          "taxes":20,
          "total":220
        }
      ]
    }
  ],
  "ticket_promotion_list":[
    {
      "generated_id":"u2l0DJUs1",
      "code":"50BOGOFF",
      "name":"50% Bogoff",
      "value":"50",
      "promotion_type":2
    }
  ],
  "user":{
    "id":"786GHJKL323",
    "external_id":"external_23434-434kjkdrf",
    "email":"user@email.com",
    "phone":"+33999999888",
    "name":"John",
    "surname":"Smith",
    "address":"Fifth Avenue 123, 34A, New York",
    "city":"Madrid",
    "zipcode":"28006",
    "country":"ES",
    "language":"es",
    "gender":1
  },
  "scope":{
    "organizations":[
      
    ],
    "locations":[
      6
    ],
    "areas":[
      
    ]
  },
  "client_data":{
    "client_type":"TPV-001",
    "client_version":"0.1-beta"
  }
}
' 
-H "Content-Type: application/json" 
-H "Authorization: Token 18bb308a19064d869734f8be3c84"

```

* **Parámetros de la respuesta (código 200 OK):**

| **Field**                               | **Type**  | **Description**                                                                                                                                                                                                                |
| --------------------------------------- | --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| ticket                                  | Object    |                                                                                                                                                                                                                                |
|  id                                     | String    | Ticket unique identifier. Can be a string, it should be unique within the organization                                                                                                                                         |
|  ticket\_numberoptional                 | Number    | Ticket identifier. Not necessarily unique                                                                                                                                                                                      |
|  rectification\_idoptional              | String    | Ticket unique identifier from the rectification ticket (total or partial refund). Can be a string, it should be unique within the organization                                                                                 |
|  created\_atoptional                    | Long      | Timestamp when the ticket was created, format UNIX epoch, Example: 1419992910. If not present, set current datetime                                                                                                            |
|  status                                 | Number    | Ticket current status. Values: TICKET\_STATUS\_REQUESTED = 3, TICKET\_STATUS\_CANCELLED = 2, TICKET\_STATUS\_CONFIRMED = 4, TICKET\_STATUS\_READY = 5, TICKET\_STATUS\_ON\_ROUTE = 6, TICKET\_STATUS\_COMPLETED = 1            |
|  channeloptional                        | Number    | API request origin. Values: 1- SHOP (TPV) (default), 2 - ONLINE (Web, APP, etc)                                                                                                                                                |
|  nameoptional                           | String    | Given name (human readable) to the ticket                                                                                                                                                                                      |
|  additional\_dataoptional               | String    | Place here any relevant information you want to persist into the system                                                                                                                                                        |
|  ticket\_summary                        | Object    | Ticket summary data                                                                                                                                                                                                            |
|   subtotal                              | Number    | Total amount before taxes and fees (only apply to ticket items. Format is a number. Value unit is in cents, it means that if you have 10.56€ value will be 1056, while a value of 15€ will be 1500                             |
|   service\_feeoptional                  | Number    | Service fee amount before taxes. Format is a number. Value unit is in cents, it means that if you have 1.60€ value will be 160, while a value of 0.95€ will be 95                                                              |
|   other\_feesoptional                   | Number    | Other fees not included into subtotal or service fee. Format is a number. Value unit is in cents, it means that if you have 0.30€ value will be 30, while a value of 0.05€ will be 5                                           |
|   taxes                                 | Number    | Taxes amount applied to all the ticket items and fees. Format is a number. Value unit is in cents, it means that if you have 2.75€ value will be 275, while a value of 1.9€ will be 190                                        |
|   tipoptional                           | Number    | Tips amount, this value does not implies taxes. Format is a number. Value unit is in cents, it means that if you have 5€ value will be 500, while a value of 2.99€ will be 299                                                 |
|   total                                 | Number    | Total amount including taxes, fees and tips, it is the price which the user has to pay. Format is a number. Value unit is in cents, it means that if you have 150.20€ value will be 15020, while a value of 75.79 will be 7579 |
|   due                                   | Number    | Amount given by the user. Format is a number. Value unit is in cents, it means that if you have 150.20€ value will be 15020, while a value of 75.79 will be 7579                                                               |
|   discount\_amountoptional              | Number    | Total discount applied to the ticket. Format is a number. Value unit is in cents, it means that if you have 150.20€ value will be 15020, while a value of 75.79 will be 7579                                                   |
|   currency                              | String    | 3 letters ISO 4217 Code for currencies, upper case value. https://www.iso.org/iso-4217-currency-codes.html                                                                                                                     |
|  ticket\_deliveryoptional               | Object    | Ticket delivery data if any                                                                                                                                                                                                    |
|   pick\_up\_address                     | String    | Address where the order needs to be picked up. Exclude fields typically added as address line 2 such as building block or door number                                                                                          |
|   pick\_up\_atoptional                  | Long      | Timestamp when the order has to be picked up, format UNIX epoch, Example: 1419992910. If not present, set current datetime                                                                                                     |
|   drop\_off\_address                    | String    | Address where the order needs to be dropped off                                                                                                                                                                                |
|   drop\_off\_address\_latitudeoptional  | Float     | Geo latitude of the drop off address                                                                                                                                                                                           |
|   drop\_off\_address\_longitudeoptional | Float     | Geo longitude of the drop off address                                                                                                                                                                                          |
|   drop\_off\_atoptional                 | Long      | Timestamp when the order has to be dropped off, format UNIX epoch, Example: 1419992910. If not present, set current datetime                                                                                                   |
|   drop\_off\_notesoptional              | String    | Address or delivery additional notes                                                                                                                                                                                           |
|   contact\_phone\_numberoptional        | String    | Contact user phone for courier usage                                                                                                                                                                                           |
|  ticket\_serviceoptional                | Object    | Ticket service data                                                                                                                                                                                                            |
|   service\_type                         | Number    | Service type. Values: 1 - DELIVERY, 2 - TAKE AWAY, 3 - DINE IN, 4 - BOOKING                                                                                                                                                    |
|   table\_id                             | String    | Shop table id, usually attached to Dine in service type                                                                                                                                                                        |
|   ready\_at                             | Long      | Timestamp when the order needs to be ready, format UNIX epoch, Example: 1419992910. If not present, set current datetime                                                                                                       |
|   now                                   | Boolean   | Service type now true or false                                                                                                                                                                                                 |
| ticket\_payment\_list                   | Object\[] | List of payment items included into the ticket                                                                                                                                                                                 |
|   type                                  | Number    | Values: 1 - CASH, 2 - CREDIT CARD, 3 - OTHERS                                                                                                                                                                                  |
|   amount                                | Number    | Total amount paid by the user. Format is a number. Value unit is in cents, it means that if you have 10.56€ value will be 1056, while a value of 15€ will be 1500                                                              |
|   card\_detailsoptional                 | String    | Credit card details (masked) in case type is 2                                                                                                                                                                                 |
|   idoptional                            | Number    | Payment unique identifier, if available                                                                                                                                                                                        |
|   useroptional                          | Object    | User information - optional field                                                                                                                                                                                              |
|     idoptional                          | String    | Unique user identifier                                                                                                                                                                                                         |
|     external\_idoptional                | String    | Unique external user identifier                                                                                                                                                                                                |
|     emailoptional                       | String    | User email                                                                                                                                                                                                                     |
|     phoneoptional                       | String    | User phone number                                                                                                                                                                                                              |
|     nameoptional                        | String    | User first name, utf-8 encoding                                                                                                                                                                                                |
|     surnameoptional                     | String    | User surname, utf-8 encoding                                                                                                                                                                                                   |
|     addressoptional                     | String    | User full address                                                                                                                                                                                                              |
|     cityoptional                        | String    | Address city                                                                                                                                                                                                                   |
|     zipcodeoptional                     | String    | Address zipcode                                                                                                                                                                                                                |
|     countryoptional                     | String    | Address country. Format ISO 3166 alpha 2 codes (UPPERCASE) https://www.iso.org/iso-3166-country-codes.html                                                                                                                     |
|     languageoptional                    | String    | User language. Format ISO 639 alpha 2 codes (LOWERCASE) https://www.iso.org/iso-639-language-codes.html                                                                                                                        |
|     genderoptional                      | Number    | User gender. Values: 1 - MALE, 2 - FEMALE, 3 - OTHER, 4 - N/A                                                                                                                                                                  |
|  ticket\_item\_list                     | Object\[] | List of items included into the ticket                                                                                                                                                                                         |
|   item\_idoptional                      | String    | Unique product item identifier from the list of items. Example: item order from ticket                                                                                                                                         |
|   ref\_item\_idoptional                 | String    | Reference to unique product item id, in case, current item is attached to another ticket item. Example: Promotion applied to a parent item id                                                                                  |
|   sku\_codeoptional                     | String    | External product item identifier                                                                                                                                                                                               |
|   nameoptional                          | String    | Human readable product item name                                                                                                                                                                                               |
|   voucher\_codeoptional                 | String    | Promotion unique identifier. Example: User has a promotional code and attached to the ticket order                                                                                                                             |
|   quantity                              | Number    | Number of same items into the ticket                                                                                                                                                                                           |
|   subtotal                              | Number    | Total amount before taxes applied to the current ticket item. Format is a number. Value unit is in cents, it means that if you have 10.56€ value will be 1056, while a value of 15€ will be 1500                               |
|   taxes                                 | Number    | Taxes amount applied to the current ticket item. Format is a number. Value unit is in cents, it means that if you have 2.75€ value will be 275, while a value of 1.9€ will be 190                                              |
|   total                                 | Number    | Total amount after taxes applied to the current ticket item. Format is a number. Value unit is in cents, it means that if you have 10.56€ value will be 1056, while a value of 15€ will be 1500                                |
|   modifiersoptional                     | Object\[] | List of item modifiers included into the ticket item                                                                                                                                                                           |
|     sku\_codeoptional                   | String    | External product modifier identifier                                                                                                                                                                                           |
|     nameoptional                        | String    | Human readable product modifier name                                                                                                                                                                                           |
|     quantity                            | Number    | Number of same modifier into the item                                                                                                                                                                                          |
|     subtotaloptional                    | Number    | Total amount before taxes applied to the current item modifier. Format is a number. Value unit is in cents, it means that if you have 10.56€ value will be 1056, while a value of 15€ will be 1500                             |
|     taxesoptional                       | Number    | Taxes amount applied to the current item modifier. Format is a number. Value unit is in cents, it means that if you have 2.75€ value will be 275, while a value of 1.9€ will be 190                                            |
|     totaloptional                       | Number    | Total amount after taxes applied to the current item modifier. Format is a number. Value unit is in cents, it means that if you have 10.56€ value will be 1056, while a value of 15€ will be 1500                              |
|  ticket\_combo\_list                    | Object\[] | List of combos included into the ticket                                                                                                                                                                                        |
|   item\_idoptional                      | String    | Unique combo item identifier from the list of items. Example: item order from ticket                                                                                                                                           |
|   ref\_item\_idoptional                 | String    | Reference to unique combo item id, in case, current item is attached to another ticket item. Example: Promotion applied to a parent item id                                                                                    |
|   sku\_codeoptional                     | String    | External combo item identifier                                                                                                                                                                                                 |
|   nameoptional                          | String    | Human readable combo item name                                                                                                                                                                                                 |
|   voucher\_codeoptional                 | String    | Promotion unique identifier. Example: User has a promotional code and attached to the ticket order                                                                                                                             |
|   quantity                              | Number    | Number of same combo into the ticket                                                                                                                                                                                           |
|   subtotal                              | Number    | Total amount before taxes applied to the current ticket combo. Format is a number. Value unit is in cents, it means that if you have 10.56€ value will be 1056, while a value of 15€ will be 1500                              |
|   taxes                                 | Number    | Taxes amount applied to the current ticket combo. Format is a number. Value unit is in cents, it means that if you have 2.75€ value will be 275, while a value of 1.9€ will be 190                                             |
|   total                                 | Number    | Total amount after taxes applied to the current ticket combo. Format is a number. Value unit is in cents, it means that if you have 10.56€ value will be 1056, while a value of 15€ will be 1500                               |
|   modifiersoptional                     | Object\[] | List of item modifiers included into the ticket combo                                                                                                                                                                          |
|     sku\_codeoptional                   | String    | External combo modifier identifier                                                                                                                                                                                             |
|     nameoptional                        | String    | Human readable combo modifier name                                                                                                                                                                                             |
|     quantity                            | Number    | Number of same modifier into the item                                                                                                                                                                                          |
|     subtotaloptional                    | Number    | Total amount before taxes applied to the current combo modifier. Format is a number. Value unit is in cents, it means that if you have 10.56€ value will be 1056, while a value of 15€ will be 1500                            |
|     taxesoptional                       | Number    | Taxes amount applied to the current combo modifier. Format is a number. Value unit is in cents, it means that if you have 2.75€ value will be 275, while a value of 1.9€ will be 190                                           |
|     totaloptional                       | Number    | Total amount after taxes applied to the current combo modifier. Format is a number. Value unit is in cents, it means that if you have 10.56€ value will be 1056, while a value of 15€ will be 1500                             |
|     itemsoptional                       | Item\[]   | List of items included into the combo - same definition than Item object                                                                                                                                                       |
|  ticket\_promotion\_listoptional        | Object    | List of promotions included into the ticket                                                                                                                                                                                    |
|   code                                  | String    | Code of the promotion                                                                                                                                                                                                          |
|   generated\_idoptional                 | String    | Unique ID generated after user apply a promotion code                                                                                                                                                                          |
|   nameoptional                          | String    | Name of the promotion                                                                                                                                                                                                          |
|   promotion\_type                       | Number    | Promotion type. Values: 1 - FIXED\_DISCOUNT, 2 - PERCENT\_DISCOUNT                                                                                                                                                             |
|   valueoptional                         | String    | Percentage or fixed value depending on promotion\_type                                                                                                                                                                         |
| client\_dataoptional                    | Object    | Client data belongs to the app which invokes the service. The parameter must include at least these parameters (you can include as much as you need for debugging): client\_type (ANDROID, WEB or IOS) and client\_version     |
| scope                                   | Object    | Virtual geographical scope belong to the given request                                                                                                                                                                         |
|   locations                             | Number\[] | List of selected locations                                                                                                                                                                                                     |

* **Ejemplo respuesta (200 OK):**

```
HTTP/1.1 200 OK 
{
  "ticket":{
	"id":"12345ABCDE",
	"ticket_number":12345,
	"ticket_id":"1454sdsd45787855sdffbhn",
	"ticket_datetime":1419992910,
	"created":1419992910,
	"channel":1,
	"status":1,
	"name":"lunch meal",
	"notes":"here you can place any info you want",
	"ticket_service":{
  	"service_type":1,
  	"table_id":"Table 1",
  	"ready_at":1419992910,
  	"now":true
	},
	"ticket_delivery":{
  	"pick_up_name":"Restaurante SinBarril",
  	"pick_up_address":"Avenida Ciudad de Barcelona 5, 28007 Madrid",
  	"pick_up_phone":"+3491254578",
  	"pick_up_at":1419992910,
  	"drop_off_address":"Avenida Canillejas a Vicálvaro 15, 28022 Madrid",
  	"drop_off_address_latitude":40.4625427,
  	"drop_off_address_longitude":-3.6886626,
  	"drop_off_at":1419993910,
  	"drop_off_notes":"Block 5, 4th floor. Ask Tommy"
	},
	"ticket_summary":{
  	"subtotal":1000,
  	"service_fee":100,
  	"other_fees":0,
  	"taxes":110,
  	"tip":200,
  	"total":1410,
  	"due":1410,
  	"discount_amount":100,
  	"currency":"EUR"
	},
	"ticket_payment_list":[
  	{
    	"type":1,
    	"card_details":"1234*****5678****",
    	"amount":1410,
    	"payment_id":"987654321ABCD",
    	"summary":"processed with my epayment platform",
    	"user":{
      	"id":"786GHJKL323",
      	"external_id":"external_23434-434kjkdrf",
      	"email":"user@email.com",
      	"phone":"+33999999888",
      	"name":"John",
      	"surname":"Smith",
      	"address":"Fifth Avenue 123, 34A, New York",
      	"city":"Madrid",
      	"zipcode":"28006",
      	"country":"ES",
      	"language":"es",
      	"gender":1
    	}
  	},
  	{
    	"type":2,
    	"card_details":"1234*****5678****",
    	"amount":1410,
    	"payment_id":"987654321ABCD",
    	"summary":"processed with my epayment platform",
    	"user":{
      	"id":"786GHJKL323",
      	"external_id":"external_23434-434kjkdrf",
      	"email":"user@email.com",
      	"phone":"+33999999888",
      	"name":"John",
      	"surname":"Smith",
      	"address":"Fifth Avenue 123, 34A, New York",
      	"city":"Madrid",
      	"zipcode":"28006",
      	"country":"ES",
      	"language":"es",
      	"gender":1
    	}
  	}
	],
	"ticket_item_list":[
  	{
    	"item_id":"1",
    	"ref_item_id":null,
    	"sku_code":"DRINK_001_LIGHT",
    	"name":"Pepsi Light 33cl",
    	"voucher_code":"123456abcd",
    	"quantity":2,
    	"subtotal":400,
    	"taxes":80,
    	"total":480,
    	"modifiers":[
      	{
        	"sku_code":"MODIFIER_ID_001",
        	"name":"Extra ice",
        	"quantity":1,
        	"subtotal":10,
        	"taxes":1,
        	"total":11
      	}
    	]
  	},
  	{
    	"item_id":"2",
    	"ref_item_id":null,
    	"sku_code":"SANDWICH_047_SALT",
    	"name":"Bacon and cheese sandwich",
    	"voucher_code":null,
    	"quantity":1,
    	"subtotal":200,
    	"taxes":20,
    	"total":220
  	}
	],
	"ticket_combo_list":[
  	{
    	"item_id":"1",
    	"ref_item_id":null,
    	"sku_code":"COMBO_001",
    	"name":"Daily menu",
    	"voucher_code":"123456abcd",
    	"quantity":1,
    	"subtotal":4000,
    	"taxes":800,
    	"total":4800,
    	"modifiers":[
      	{
        	"sku_code":"MODIFIER_ID_001",
        	"name":"Extra ice",
        	"quantity":1,
        	"subtotal":10,
        	"taxes":1,
        	"total":11
      	}
    	],
    	"items":[
      	{
        	"item_id":"1",
        	"ref_item_id":null,
        	"sku_code":"DRINK_001_LIGHT",
        	"name":"Pepsi Light 33cl",
        	"voucher_code":"123456abcd",
        	"quantity":2,
        	"subtotal":400,
        	"taxes":80,
        	"total":480,
        	"modifiers":[
          	{
            	"sku_code":"MODIFIER_ID_001",
            	"name":"Extra ice",
            	"quantity":1,
            	"subtotal":10,
            	"taxes":1,
            	"total":11
          	}
        	]
      	},
      	{
        	"item_id":"2",
        	"ref_item_id":null,
        	"sku_code":"SANDWICH_047_SALT",
        	"name":"Bacon and cheese sandwich",
        	"voucher_code":null,
        	"quantity":1,
        	"subtotal":200,
        	"taxes":20,
        	"total":220
      	}
    	]
  	}
	],
	"ticket_promotion_list":[
  	{
    	"generated_id":"u2l0DJUs1",
    	"code":"50BOGOFF",
    	"name":"50% Bogoff",
    	"value":"50",
    	"promotion_type":2
  	}
	]
  },
  "scope":{
	"organizations":[
 	 
	],
	"locations":[
  	6
	],
	"areas":[
 	 
	],
	"additional_data":{
  	"location":[
    	{
      	"id":6,
      	"name":"Charles rue"
    	}
  	]
	}
  }
}
```

* **Parámetros respuesta (código 400 Invalid Request):**

| **Name**    | **Description**             |
| ----------- | --------------------------- |
| InvalidData | The given data is not valid |

* **Ejemplo respuesta (400 Invalid data):**

```
HTTP/1.1 400 Bad Request
{
    "error": "Invalid request"
}
```

* **Parámetros respuesta (código 500 Internal Error)**

| **Name**       | **Description**               |
| -------------- | ----------------------------- |
| InternalServer | The server failed. Try again. |

* **Ejemplo respuesta (500 Internal Error):**

```
HTTP/1.1 500 Internal Server Error
{
    "errors": "Internal server error"
}
```

{% hint style="info" %}
* En caso de error 500, el TPV internamente intentará volver a llamar 3 veces (una vez cada 1 segundo), en caso de seguir recibiendo error 500, el TPV dejará de intentarlo.&#x20;
{% endhint %}

{% hint style="info" %}
* En caso de error 400, la tarjeta está cancelada o el usuario dado de baja, Cheerfy no realizará ninguna asignación del ticket al usuario en cuestión.
{% endhint %}
