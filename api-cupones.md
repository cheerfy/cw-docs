---
description: >-
  Encuentra aquí toda la información necesaria para la integración del canjeo de
  cupones con el TPV de tu local.
---

# API Cupones

**Índice**

1. Definición código QR
   1. Parámetros
   2. Contenido
   3. Ejemplo 
2. Definición servicio Web
   1. Comprobación validez de un código de cupón
   2. Confirmación uso de un código de cupón

## 1. Definición código QR

### 1.1. Parámetros

Un código QR deberá contener obligatoriamente 2 parámetros:

* **promotion\_id**: Código **promoción único y existente** en el sistema de **Proveedor de TPV**.

Con este identificador, el Proveedor de TPV debe **reconocer que promoción tiene que aplicar** sobre el ticket actual y mostrar un mensaje de información al empleado si la promoción no se puede aplicar \(en el caso que el producto promocionado no esté incluido en el ticket actual\). 

El **formato** del promotion\_id es un campo numérico de hasta 9 caracteres.

* **voucher\_id**: Identificador del código de descuento, es un **identificador** **único** y estará asociado **a un único cliente** \(en el sistema de Cheerfy\). 

Este parámetro es el que se va a utilizar desde Proveedor de TPV para:

1. Saber si el código es válido
2. Confirmar su uso una vez aplicada la promoción y confirmado el ticket por parte del empleado

El **formato** del voucher\_id es un campo **alfanumérico de hasta 32 caracteres** de longitud.

### 1.2. Contenido

El QR code contendrá los 2 parámetros definidos en la sección "Parámetros" sin saltos de línea, ni otros caracteres adicionales. Existe un separador definido como $$$$$ para separar los 2 campos.

El contenido al escanear un código QR debería ser algo parecido a esto \(los identificadores de promoción y voucher son un ejemplo\):

```text
123456789$$$$$gh9d46cafafd4b6bad604762ab87caa6
```

### 1.3. Ejemplo

Adjuntamos un código QR, con el código de ejemplo anterior, por si es necesario hacer una prueba por parte de Proveedor de TPV.

![](https://lh3.googleusercontent.com/EI6QziAolIYMx_goCA5qjE-vvI3xEFoQVFWeELizi4mYlVSErwvjkkKiF9IvUt_urbZZYUrxYjX184B5Guv-UWr79expW_zqmlSRZNqHl5JwCx4JmYp3NLCQcHlXtih6YpxN90-w=s0)

## 2. Definición servicio WEB

Las llamadas desde el sistema Proveedor de TPV a Cheerfy se harán mediante servicios Web de tipo REST y con contenido definido en formato JSON. 

Cada llamada deberá contener una serie de parámetros obligatorios en la cabecera \(además de los propios parámetros del servicio que se invoque\), estos parámetros de la cabecera indicarán:

* El contenido tiene formato JSON**:**

```text
Content-Type: application/json
```

* Los datos de autenticación de la llamada:

```text
Authorization: Token replace_by_your_token_code_here
```

### 2.1. **Comprobación validez de un código de cupón**

Una vez el Proveedor de TPV escanea un código de cupón \(voucher\_id\), tiene que confirmar con Cheerfy que ese código es válido, para ello, necesita consultar un servicio Web REST. 

La respuesta en el caso de error, por ahora no contendrá datos del estado del cupón \(expirado o redimido\), ya que Cheerfy muestra esa información en la landing page del código, no obstante, es un dato que podría incluirse en próximas versiones.

* URL:

```text
https://backend.cheerfy.com/gift-promotion/:id/
```

* Método HTTP:

```text
PUT
```

* **Parámetros de la cabecera:**

| **Field** | **Type** | **Description** |
| :--- | :--- | :--- |
| Content-Type | String | Data application raw type. |
| Authorization | String | Admin unique access-key \(Content must start by Token\). |

* **Parámetros de la llamada:**

| **Field** | **Type** | **Description** |
| :--- | :--- | :--- |
| id | String | Voucher unique identifier \(included as part of the URL\) |
| action | Number | Action to be executed. Values: 1 - CHECK, 2 - REDEEM |
| client\_data optional | Object | Client data belongs to the app which invokes the service. The parameter must include at least these parameters \(you can include as much as you need for debugging\): client\_type \(ANDROID, WEB,  IOS, Proveedor de TPV\) and client\_version |
| promotion\_id optional | String | Unique Promotional code at Client POS to validate if valid and match with Voucher id. |

* **Ejemplo llamada:**

```text
curl -X PUT https://backend.cheerfy.com/gift-promotion/678d46cafafd4b6bad604762ab87caa6/ 
-d '{
	"action": 1,
	"client_data": {
    	"client_type": "Proveedor de TPV",
    	"client_version": "0.1"
	},
	"promotion_id": "123456789"
    }' 
-H "Content-Type: application/json" 
-H "Authorization: Token 18bb308a19064d869734f8"
```

* **Parámetros de la respuesta \(código 200 OK\):**

| **Field** | **Type** | **Description** |
| :--- | :--- | :--- |
| user | String | Cheerfy user ID |
| public\_profile | Object | Public profile user object |
|   id | String | Unique user identifier |
|   avatar optional | String | User avatar url |
|   name optional | String | User full name |
|   first\_name optional | String | User first name |
|   surname optional | String | User surname |
|   birthdate optional | Long | User birthdate, format UNIX epoch |
|   language optional | String | User language is the 2 characters language ISO code \(lower case\) |

* **Ejemplo respuesta \(200 OK\):**

```text
HTTP/1.1 200 OK 
{
   “user”: “01234567”,
   "public_profile": 
    {
        "id": "01234567".
        "avatar": "http://images.com/my_image.png",
        "name": "Carlos Gomez",
        "first_name": "Carlos",
        "surname": "Gomez",
        "birthdate": 1419992910,
        "language": "es",
    }
}


```

* **Parámetros respuesta \(código 400 Invalid Request\):**

| **Name** | **Description** |
| :--- | :--- |
| InvalidData | The given data is not valid |

* **Ejemplo respuesta \(400 Invalid data\):**

```text
HTTP/1.1 400 Bad Request
{
    "error": "Invalid request"
}
```

* **Parámetros respuesta \(código 400 Invalid Request\):**

| **Name** | **Description** |
| :--- | :--- |
| InvalidData | The given data is not valid |

* **Ejemplo respuesta \(400 Invalid promotion\):**

```text
HTTP/1.1 400 Bad Request
{
    “errors”: “Invalid promotion”
}
```

* **Parámetros respuesta \(código 400 Invalid promotion\):**

| **Name** | **Description** |
| :--- | :--- |
| InvalidPromotion | The given promotion ID is not valid |

* **Ejemplo respuesta \(400 Expired promotion\):**

```text
HTTP/1.1 400 Bad Request
{
    "error": "Expired promotion"
}
```

* **Parámetros respuesta \(código 400 Expired promotion\):**

| **Name** | **Description** |
| :--- | :--- |
| ExpiredPromotion | The given promotion is expired |

* **Ejemplo respuesta \(400 Used promotion\):**

```text
HTTP/1.1 400 Bad Request
{
    "error": "Used promotion"
}
```

* **Parámetros respuesta \(código 400 Used promotion\):**

| **Name** | **Description** |
| :--- | :--- |
| UsedPromotion | The given promotion is already used |

* **Parámetros respuesta \(código 500 Internal Error\):**

| **Name** | **Description** |
| :--- | :--- |
| InternalServer | The server failed. Try again. |

* **Ejemplo respuesta \(500 Internal Error\):**

```text
HTTP/1.1 500 Internal Server Error
{
    "errors": "Internal server error"
}
```

### 2.2. **Confirmación uso de un código de cupón**

Una vez Proveedor de TPV aplica una promoción sobre un ticket válido, tiene que confirmar con Cheerfy que ese código ha sido usado, para ello, necesita consultar un servicio Web REST. 

* En caso de error 500 \(recibiendo anteriormente un 200 de la llamada de chequeo\), Proveedor de TPV internamente intentará volver a llamar 3 veces \(una vez cada 1 segundo\), en caso de seguir recibiendo error 500, Proveedor de TPV dará por bueno el cupón, y Cheerfy tendrá que recuperar esa información de uso por otro mecanismo \(a definir como\).  ****
* En caso de error 400, el código ha expirado o se ha usado en ese momento, \(recibiendo anteriormente un 200 de la llamada de chequeo\), Proveedor de TPV dará por bueno el código, asumiendo que se ha podido usar 2 veces o ya expiró. 
* URL:

```text
https://backend.cheerfy.com/gift-promotion/:id/
```

* Método HTTP:

```text
PUT
```

* **Parámetros de la cabecera:**

| **Field** | **Type** | **Description** |
| :--- | :--- | :--- |
| Content-Type | String | Data application raw type. |
| Authorization | String | Admin unique access-key \(Content must start by Token\). |

* **Parámetros de la llamada:**

| **Field** | **Type** | **Description** |
| :--- | :--- | :--- |
| id | String | Voucher unique identifier \(included as part of the URL\) |
| action | Number | Action to be executed. Values: 1 - CHECK, 2 - REDEEM |
| client\_data optional | Object | Client data belongs to the app which invokes the service. The parameter must include at least these parameters \(you can include as much as you need for debugging\): client\_type \(ANDROID, WEB,  IOS, Proveedor de TPV\) and client\_version |

* **Ejemplo de llamada:**

```text
curl -X PUT https://backend.cheerfy.com/gift-promotion/678d46cafafd4b6bad604762ab87caa6/ 
-d '{
“action”: 2,
"client_data":{"client_type":"Proveedor de TPV", "client_version":"0.1"},
    }' 
-H "Content-Type: application/json" 
-H "Authorization: Token 18bb308a19064d869734f8b"
```

* **Parámetros de la respuesta \(código 200 OK\):**

| **Field** | **Type** | **Description** |
| :--- | :--- | :--- |
| user | String | Cheerfy user ID |
| public\_profile | Object | Public profile user object |
|   id | String | Unique user identifier |
|   avatar optional | String | User avatar url |
|   name optional | String | User full name |
|   first\_name optional | String | User first name |
|   surname optional | String | User surname |
|   birthdate optional | Long | User birthdate, format UNIX epoch |
|   language optional | String | User language is the 2 characters language ISO code \(lower case\) |

* **Ejemplo respuesta \(200 OK\):**

```text
HTTP/1.1 200 OK 
{
   “user”: “01234567”,
   "public_profile": 
    {
        "id": "01234567".
        "avatar": "http://images.com/my_image.png",
        "name": "Carlos Gomez",
        "first_name": "Carlos",
        "surname": "Gomez",
        "birthdate": 1419992910,
        "language": "es",
    }
}
```

* **Parámetros respuesta \(código 400 Invalid Request\):**

| **Name** | **Description** |
| :--- | :--- |
| InvalidData | The given data is not valid |

* **Ejemplo respuesta \(400 Invalid data\):**

```text
HTTP/1.1 400 Bad Request
{
    "error": "Invalid request"
}
```

* **Parámetros respuesta \(código 500 Internal Error\):**

| **Name** | **Description** |
| :--- | :--- |
| InternalServer | The server failed. Try again. |

* **Ejemplo respuesta \(500 Internal Error\):**

```text
HTTP/1.1 500 Internal Server Error
{
    "errors": "Internal server error"
}
```

