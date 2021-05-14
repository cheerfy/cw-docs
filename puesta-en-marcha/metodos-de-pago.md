---
description: >-
  Encuentra aquí todas las opciones para la gestión de los pagos de tus clientes
  y cómo configurarlas.
---

# Métodos de Pago

## Tarjeta

{% tabs %}
{% tab title="Stripe" %}
{% hint style="success" %}
Opción recomendada por su facilidad y rapidez de configuración.
{% endhint %}

**Proceso de configuración:**

1. Abre una cuenta de Stripe [aquí](https://dashboard.stripe.com/register).
2. Una vez creada tu cuenta, dentro de Stripe, ve a "Desarrolladores" - "Claves de API".
3. Añade en Cheerfy Shop tus Claves de API de Stripe: Clave Secreta y Clave Publicable.
4. Para ello, ve a "Settings" - "Payments" - "Add Payment Method" - "Stripe".
5. Rellena el campo "Label" para ponerle el nombre que verán tus clientes al sistema de pago. Ejemplo: "Pago con Tarjeta".
6. Pincha en "Enabled" para activar y dale a "Save".

> Aquí puedes encontrar dónde añadir tus claves de API

![](../.gitbook/assets/image%20%2827%29.png)
{% endtab %}

{% tab title="Checkout" %}
**Proceso de configuración:**

1. Abre tu cuenta de Checkout [aquí](https://go.checkout.com/variants/es/connected-payments?creative=504908625344&keyword=checkout%20espa%C3%B1a&matchtype=e&network=g&device=c&utm_campaign=gl_always_on_ggl&utm_source=google&utm_medium=paid_search&utm_term=checkout%20espa%C3%B1a&gclid=Cj0KCQjwmIuDBhDXARIsAFITC_5t5B8geww2r3MAdntB9TWgkVfZHYQwaQl1GZPVP3YOkfm-o458adUaAsayEALw_wcB).
2. Te pedirán una serie de datos de tu empresa y se pondrán en contacto contigo.
3. Añade en Cheerfy Shop tus Claves de API de Checkout: Clave Secreta y Clave Publicable.
4. Para ello, ve a "Settings" - "Payments" - "Add Payment Method" - "Checkout".
5. Rellena el campo "Label" para ponerle el nombre que verán tus clientes al sistema de pago. Ejemplo: "Pago con Tarjeta".
6. Pincha en "Enabled" para activar y dale a "Save".

> Aquí puedes encontrar dónde añadir tus Claves de API:

![](../.gitbook/assets/image%20%2835%29.png)
{% endtab %}
{% endtabs %}

## Apple Pay y Google Pay

**Proceso de configuración:**

{% hint style="warning" %}
Es necesario haber configurado Stripe.
{% endhint %}

1. Configura Stripe como método de pago \(paso anterior\).
2. Una vez configurado, pincha en "Add Payment Method" - "Stripe Digital Wallet \(Google Pay, Apple Pay\)".
3. De forma automática, aparecerá configurado.
4. Rellena el campo "Label" para ponerle el nombre con el que verán tus clientes el sistema de pago. Ejemplo: "Apple Pay \| Google Pay".
5. Pincha en "Enabled" para activar y dale a "Save".

![](../.gitbook/assets/image%20%2877%29.png)

## Efectivo

**Proceso de configuración:**

1. Ve a "Settings" - "Payments" - "Add Payment Method" - "Custom".
2. En el campo "Service" indica en qué servicios quieres añadir este método de pago. Si dejas este campo vacío se incluirá por defecto en todos los servicios.
3. Rellena el campo "Label" para ponerle el nombre que verán tus clientes al sistema de pago. Ejemplo: "Pago en el local".
4. Pincha en "Enabled" para activar y dale a "Save".

![](../.gitbook/assets/image%20%2876%29.png)

