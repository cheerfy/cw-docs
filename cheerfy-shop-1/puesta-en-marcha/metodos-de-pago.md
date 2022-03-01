---
description: >-
  Encuentra aquí todas las opciones para la gestión de los pagos de tus clientes
  y cómo configurarlas.
---

# Métodos de Pago

## Tarjeta

{% tabs %}
{% tab title="Stripe Connect NEW" %}
{% hint style="success" %}
Opción recomendada por rapidez de configuración y mejora de las condiciones económicas.
{% endhint %}



**Proceso de configuración:**

1\. Accede a [Cheerfy Loyalty](https://admin.cheerfy.com/login/).&#x20;

{% hint style="info" %}
En caso de no tener acceso por favor contáctanos en soporte@cheerfy.com, indícanos con qué mail deseas acceder, y te enviamos un mail con el acceso.
{% endhint %}

2\. Ve a "Ajustes" - "Shop" - "Integraciones" y selecciona tu local.

3\. Pincha en "Payments" - "Añadir método de pago" - "Tarjeta de Crédito Stripe".

4\. Deberás haber accedido a una página de Stripe en la que completar tus datos fiscales sobre la empresa o el autónomo y de añadir la cuenta bancaria en la que deseas recibir el dinero de tus ventas.

{% hint style="info" %}
Algunas consideraciones para completar el formulario de Stripe:

* Pon un teléfono móvil: se usará para enviar SMS de autenticación.
* Revisa como se mostrarán los cargos en la cuenta de los clientes.
{% endhint %}

5\. Todavía en Stripe, entra en "Datos de Soporte" y actualiza este campo con el nombre de tu restaurante.

{% hint style="warning" %}
**En caso de tener varios locales, dispones de dos opciones:**

1\. **** Cuentas Stripe separadas para cada local: repite estos pasos para cada local.

2\. Cuenta Stripe común a varios o todos los locales: una vez has creado una cuenta para un local, puedes asociarla a otro repitiendo los pasos anteriores y, en el paso 3, usando el mismo email y el mismo teléfono que antes. No tendrás que rellenar todo otra vez.
{% endhint %}
{% endtab %}

{% tab title="Stripe" %}
**Proceso de configuración:**

1. Abre una cuenta de Stripe [aquí](https://dashboard.stripe.com/register).
2. Una vez creada tu cuenta, dentro de Stripe, ve a "Desarrolladores" - "Claves de API".
3. Añade en Cheerfy Shop tus Claves de API de Stripe: Clave Secreta y Clave Publicable.
4. Para ello, ve a "Settings" - "Payments" - "Add Payment Method" - "Stripe".
5. Rellena el campo "Label" para ponerle el nombre que verán tus clientes al sistema de pago. Ejemplo: "Pago con Tarjeta".
6. Pincha en "Enabled" para activar y dale a "Save".

> Aquí puedes encontrar dónde añadir tus claves de API

![](<../../.gitbook/assets/image (27).png>)
{% endtab %}

{% tab title="Checkout" %}
**Proceso de configuración:**

1. Abre tu cuenta de Checkout [aquí](https://go.checkout.com/variants/es/connected-payments?creative=504908625344\&keyword=checkout+espa%C3%B1a\&matchtype=e\&network=g\&device=c\&gclid=Cj0KCQjwmIuDBhDXARIsAFITC\_5t5B8geww2r3MAdntB9TWgkVfZHYQwaQl1GZPVP3YOkfm-o458adUaAsayEALw\_wcB).
2. Te pedirán una serie de datos de tu empresa y se pondrán en contacto contigo.
3. Añade en Cheerfy Shop tus Claves de API de Checkout: Clave Secreta y Clave Publicable.
4. Para ello, ve a "Settings" - "Payments" - "Add Payment Method" - "Checkout".
5. Rellena el campo "Label" para ponerle el nombre que verán tus clientes al sistema de pago. Ejemplo: "Pago con Tarjeta".
6. Pincha en "Enabled" para activar y dale a "Save".

> Aquí puedes encontrar dónde añadir tus Claves de API:

![](<../../.gitbook/assets/image (35).png>)
{% endtab %}
{% endtabs %}

## Apple Pay y Google Pay

**Proceso de configuración:**

{% hint style="warning" %}
Es necesario haber configurado Stripe.
{% endhint %}

1. Configura Stripe como método de pago (paso anterior).
2. Una vez configurado, pincha en "Add Payment Method" - "Stripe Digital Wallet (Google Pay, Apple Pay)".
3. De forma automática, aparecerá configurado.
4. Rellena el campo "Label" para ponerle el nombre con el que verán tus clientes el sistema de pago. Ejemplo: "Apple Pay | Google Pay".
5. Pincha en "Enabled" para activar y dale a "Save".

![](<../../.gitbook/assets/image (84).png>)

## Efectivo

**Proceso de configuración:**

1. Ve a "Settings" - "Payments" - "Add Payment Method" - "Custom".
2. En el campo "Service" indica en qué servicios quieres añadir este método de pago. Si dejas este campo vacío se incluirá por defecto en todos los servicios.
3. Rellena el campo "Label" para ponerle el nombre que verán tus clientes al sistema de pago. Ejemplo: "Pago en el local".
4. Pincha en "Enabled" para activar y dale a "Save".

![](<../../.gitbook/assets/image (81).png>)
