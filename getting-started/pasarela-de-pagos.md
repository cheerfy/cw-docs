---
description: >-
  Encuentra aquí todas las opciones para la gestión de los pagos de tus clientes
  y cómo configurarlas.
---

# Pasarela de Pagos

## Stripe

{% hint style="info" %}
Opción recomendada por su facilidad y rápidez de configuración.
{% endhint %}

1. Entra en la [web oficial de Stripe](https://stripe.com/es). 
2. Pincha en el botón \[Empezar ahora\] o selecciona «Iniciar sesión» en el menú superior izquierdo, y haz clic en el texto «Crea una cuenta». 
3. Rellena tus datos en el formulario \(correo electrónico, nombre completo, contraseña segura\), pincha en el reCAPTCHA para confirmar que no eres un robot y haz clic en el botón \[Crea tu cuenta de Stripe\]. 
4. En este momento recibirás un email de confirmación en tu correo. Pincha en él e identifícate para activar tu cuenta. 
5. A continuación llegarás a tu panel de inicio en Stripe. 
6. Dale un nombre a la cuenta haciendo clic en «Añadir un nombre» bajo «Cuenta sin nombre» arriba a la izquierda. Podrás cambiarlo cuando quieras. Te ayudará a diferenciar entre varias cuentas si necesitas crear más de una. 
7. Para terminar de activar tu cuenta necesitas introducir tus datos personales o de empresa. Para ello pincha en el botón \[Iniciar\] que aparece en «Activa tu cuenta de Stripe» o en el elemento «Activa tu cuenta» del menú lateral izquierdo.

![](https://lh3.googleusercontent.com/bsWi9JfiCQmslHQxV15vTUuqKXxilKU2vYUbfQ2um4825w7yCX1uQ3EkxofHAqqqMm8mYAbETH0-ZD_sR-C4FOLiG2i3Y18PzRefWDi8SAtOpOobSx5x1Im8cLK1M2ngaFbQT0nJ)

#### En esta sección deberás indicar

1. País de residencia
2. Tu producto:
   * Web
   * Descripción de tu empresa
3. Datos fiscales de tu negocio:
   * Tipo \(autónomo, SA, SL…\)
   * CIF
   * Dirección
4. Datos personales:
   * Nombre
   * Fecha de nacimiento
   * NIF
   * Dirección
5. Información que aparece en el extracto de la tarjeta de crédito de tus clientes:
   * Descripción
   * Número de teléfono
6. Datos bancarios para recibir los pagos:
   * Moneda
   * País
   * IBAN
7. Elección de autentificación en dos pasos \(para mayor seguridad\) entre:
   * Mensaje de texto
   * Google Authenticator

{% hint style="success" %}
Poco después de \[Enviar solicitud\] tu cuenta quedará activada y lista. 

**¡Ya solo queda añadir tu método de pago a Cheerfy Shop!**
{% endhint %}

1. Entra en [Cheerfy Shop](https://admin.cheerfy.shop/), y en el apartado de “Settings” -&gt; “Payments” -&gt; “Add payment method” -&gt; “Stripe”. 
2. Pincha en “Enabled” y “Disable E-Mail Receipt” como ves en la foto de abajo, y rellena los campos de “Stripe Secret Key” y “Stripe Publishable Key” con los códigos que encontrarás en tu cuenta de Stripe en el apartado “Desarrolladores” -&gt; “Claves de API”. Deberás asegurarte que son las claves “live” y no “test”. Esto se comprueba rápido: En el código debe ser algo como: ew\_live\_dq2dwq2dqwd312 
3. Rellenar el campo “Label” para ponerle un nombre el sistema de pago \(Ejemplo: “Tarjeta”\)  


   ![](https://lh5.googleusercontent.com/mCiOHhdGoqsrwYQuU_AjR90lkHG3ItomCr64zkruWkvKw_6vs-JaxJyjlUfmgZ6qPKDlRWkalV-3cIpj4a6a_soKv0OgDT8aM35Wd_58clYNO5pKiXInbwpRBXOEIWHXzBGf7qlO)

