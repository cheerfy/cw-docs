---
description: >-
  Una de las partes más importantes de la configuración de un mensaje es la de
  configurar un cupón y entender su funcionamiento.
---

# Funcionamiento de los cupones

## ¿Cómo funcionan nuestros cupones?

{% hint style="info" %}
Es importante resaltar que los cupones son utilizables tanto en tu local físico como en tu tienda online.   
  
Además, son descargables en el Apple Wallet o Google Pay sin necesidad de Apps para que el cliente siempre lo tenga localizado.
{% endhint %}

### 1. Proceso de canjeo en tu tienda online

1. El cliente recibe el SMS o Email con el enlace del cupón.

2. El cliente accede a vuestra tienda online para realizar un pedido.

3. El cliente añade su email en la pasarela de pago y hace clic en "Aplicar".

4. Le aparecen todos los cupones activos que tenga disponibles para que seleccione el que desee.

![](../../.gitbook/assets/image%20%28124%29.png)

{% hint style="warning" %}
Para que tu tienda online sea capaz de identificar a través del email qué cupones tiene activos, deberás configurar correctamente tanto la promoción en tu shop, como el cupón en el mensaje.

* En la documentación de [Cheerfy Shop](https://docs.cheerfy.com/puesta-en-marcha/crea-promociones) puedes ver cómo configurar una promoción. 
* En esta misma página, más adelante, te explicamos cómo configurar un cupón.
{% endhint %}

### 2. Proceso de canjeo en tu local físico

1. El cliente recibe el SMS o Email con el enlace del cupón. 
2. El cliente abre el cupón y lo muestra al camarero.  
3. El empleado sella digitalmente el cupón a través de nuestro escáner.

![](../../.gitbook/assets/image%20%28118%29.png)

#### ¿Cómo accedo y utilizo el escáner?

{% page-ref page="../../instalacion-escaner.md" %}

#### Integración con tu TPV

{% hint style="success" %}
Si lo deseas, tenemos la capacidad de integrarnos con tu TPV para que cuando leas el QR a través del escaner, se refleje la promoción de forma automática en tu TPV o se asocie el ticket automáticamente al usuario correspondiente.
{% endhint %}

Encuentra aquí la información necesaria sobre nuestra API para la integración:

{% page-ref page="../../api-cupones.md" %}

## ¿Cómo configuro un cupón?

Lo primero es ir al mensaje en el que deseas incrustar el cupón. Una vez dentro, en la fase de "Contenido", haz clic sobre "Cupón".

![](../../.gitbook/assets/image%20%28117%29.png)

Una vez has hecho clic en "Cupón", apareces en la página que mostramos a continuación, y sobre la que explicamos todos los parámetros configurables:

![](../../.gitbook/assets/image%20%28144%29.png)

#### Parámetros configurables:

1. **Texto de enlace al cupón**: escribe el texto sobre el que quieres que se incruste el cupón en tu mensaje.

2. **Título del cupón**: escribe el título que verán tus clientes en el cupón.

3. **Imagen**: elige entre utilizar la misma imagen que en el mensaje o que en el proceso de registro.

4. **Método de canjeo**: elije si deseas canjear vía código QR, código de barras, o mediante un botón en el cupón.

5. **Código de promoción en el TPV**: tendrá que ser exactamente el mismo que el que hayas configurado en la promoción de tu Cheerfy Shop o tu TPV para que ambas sean capaces de identificarlo.

6. **Términos y condiciones**: puedes añadir un texto que tus clientes verán en el reverso de los cupones en Apple Wallet o Google Pay, o en forma de pop-up en la versión Web.

7. **Validez**: indica el número de días que el cupón estará activo desde que se envía el mensaje que lo contiene.

8. **Número de usos**: define cuantas veces puede usar tu cliente ese cupón.

9. **Limitación de usos**: define con qué frecuencia puede usar tu cliente el cupón.

{% hint style="info" %}
Ejemplo 1: si en "Número de usos" has definido un único uso, y en "Limitación de usos" no defines ninguna limitación, solo se podrá utilizar una vez.

Ejemplo 2: si en "Número de usos" has definido un único uso, y en "Limitación de usos" has definido "usos semanales", el cupón podrá utilizarse una vez a la semana.

Ejemplo 3: si en "Número de usos" has definido un único uso, y en "Limitación de usos" has definido "usos mensuales", el cupó podrá utilizarse una vez al mes.
{% endhint %}

10. **Fuente del cupón**: elige el tipo de letra que desees para tu cupón.

11. **Colores**: utiliza tus colores corporativos para diseñar el cupón.

12. **Logo del cupón**: incluye el logo de tu restaurante en la parte superior del cupón.

{% hint style="warning" %}
IMPORTANTE: en la esquina superior derecha haz clic en "Guardar".
{% endhint %}

Una vez hayas guardado, volverás a la fase de contenido en la edición del mensaje. Podrás ver el cupón sobre el texto que hayas incluído en el punto número 1.

![](../../.gitbook/assets/image%20%28114%29.png)

