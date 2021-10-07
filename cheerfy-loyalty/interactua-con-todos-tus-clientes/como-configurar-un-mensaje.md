---
description: >-
  Si has llegado hasta aquí es porque ya conoces los diferentes puntos de
  contacto con tus clientes y los tipos de mensajes con los que abordarlos.
  Ahora es el momento de aprender a crear un mensaje.
---

# Cómo configurar un mensaje

## Configuración de un mensaje automático

Lo primero será ir a "Mensajes" - "Crear".

![](../../.gitbook/assets/image%20%2898%29.png)

Si quieres basarte en un mensaje existente, puedes copiar desde un mensaje ya creado para configurar un nuevo mensaje. 

![](../../.gitbook/assets/image%20%28164%29.png)

En ambos casos, habrás aparecido en página como la que mostramos, y que divide el proceso de creación en tres fases:

1. **Contexto**: definiremos cuándo y dónde enviar el mensaje.
2. **Contenido**: definiremos qué contenido enviar.
3. **Audiencia**: definiremos a quién enviar el mensaje dentro de tu base de datos.

![](../../.gitbook/assets/image%20%2897%29.png)

## Parámetros configurables en la fase de Contexto

1. **Envío**: elige el tipo de mensaje que deseas.

![](../../.gitbook/assets/image%20%28132%29.png)

2. **Plan de Envío**: elige qué días y a qué horas enviar el mensaje.

![](../../.gitbook/assets/image%20%28100%29.png)

{% hint style="info" %}
Pincha en "Plan de Envío". A la derecha se abrirán las opciones. 

* Selecciona "Todos los días" y "Todas las horas" si así deseas enviarlo. 
* Si quieres enviarlo solo algunos días o a algunas horas determinadas especifícalas.
{% endhint %}

3. **Retardo**: puedes retardar el envío del mensaje.

![](../../.gitbook/assets/image%20%28108%29.png)

{% hint style="info" %}
 Ejemplo añadiendo un retardo de 10 minutos para cada tipo de mensaje:

* En llegada: se enviaría 10 minutos después de la entrada o pedido del cliente. 
* En transacción: se enviaría 10 minutos después del pago o escaneo de la tarjeta del cliente. 
* En salida: se enviaría 10 minutos después de la salida o pedido del cliente.
{% endhint %}

En el caso del mensaje de cumpleaños lo que te preguntará es si quieres adelantar el envío. En caso afirmativo podrás indicar cuántos días adelantar el envío.

![](../../.gitbook/assets/image%20%28130%29.png)

4. **Frecuencia**: elige cada cuánto enviar el mensaje. Por ejemplo, puedes querer enviarlo cada visita o cada 10 visitas.

![](../../.gitbook/assets/image%20%28141%29.png)

5. **Definir localizaciones**: elige en qué localizaciones enviar el mensaje. Puedes querer enviarlo a nivel organización, o solo en una o varias de tus localizaciones.

![](../../.gitbook/assets/image%20%28154%29.png)

### Aspectos configurables en la fase de Contenido

1. **Nombre**: es de carácter interno para ubicar el mensaje en la plataforma.

2. **Asunto**: se trata del título o asunto del mensaje como en cualquier email "normal".

3. **Foto**: se trata de la creatividad que desees añadir. Puede ser una imagen estática o un GIF.

{% hint style="info" %}
Relación de aspecto de la foto: 16:9 \(ej. 1024px x 576 px\).
{% endhint %}

![](../../.gitbook/assets/image%20%28103%29.png)

4. **Resumen**: se trata del contenido como tal.

![](../../.gitbook/assets/image%20%28115%29.png)

Objetos incrustables:

* **Nombre del cliente**: saluda a cada cliente por su nombre.
* **Nombre del Negocio**: si vas a utilizar un mismo mensaje para todas tus marcas, lo puedes firmar con cada nombre de cada una de ellas.
* **Añadir enlace**: añade enlaces a tu web, redes sociales...
* **Cupón**: para premiar a tus clientes. 
* **Tarjeta de fidelización**: incluye tu tarjeta en el mensaje para que el cliente pueda descargarla en su Wallet.

Aquí un ejemplo del mismo mensaje anterior con los objetos incrustados:

![](../../.gitbook/assets/image%20%28139%29.png)

{% page-ref page="funcionamiento-de-los-cupones.md" %}

{% page-ref page="tarjeta-de-fidelizacion.md" %}

## Parámetros configurables en la fase de Audiencia

Podremos segmentar por diferentes parámetros divididos en:

**1. Perfil de negocio:**

1. **Etiquetas**: se refiere a las etiquetas de la encuesta inicial del proceso de registro.
2. **Fecha de registro**: según la fecha en la que el cliente se registró.
3. **Último rating**: en función de la última puntuación que te hayan dejado al mensaje de valoraciones.
4. **Número de visitas**: en función de las visitas que haya realizado un cliente.
5. **Duración de última visita.**
6. **Última visita**: en función de cuándo te visitó por última vez.
7. **Última vista de campaña**: en función de cuándo vieron la última campaña.
8. **VIP**: puedes marcar algunos clientes como VIP e impactar sólo a ellos.
9. **Número de teléfono móvil**: en función de si tenemos o no su número de teléfono.
10. **Saldo actual tarjeta**: en función del avance en la tarjeta actual.
11. **Saldo acumulado tarjeta**: en función del avance en el total de tarjetas que haya utilizado.

{% hint style="info" %}
Los puntos 10 y 11 se entenderán mejor en el punto donde detallamos todo lo necesario con respecto a la tarjeta de fidelización.
{% endhint %}

**2. Perfil demográfico:**

1. Edad.
2. Sexo.
3. Idioma.
4. Cumpleaños.

![](../../.gitbook/assets/image%20%28129%29.png)

Ejemplificamos desgranando en detalle uno de estos parámetros. Todos funcionan igual. Para ello filtraremos por "Número de visitas".

Lo primero es elegir alguna de las opciones que nos ofrece.

![](../../.gitbook/assets/image%20%28159%29.png)

¿Qué significa cada una de ellas?

**1. Cualquier número de visitas**: significa que no segmentaremos por este parámetro ya que el mensaje se enviará a todos tus clientes independientemente de cuántas veces te hayan visitado.

**2. Número fijo de visitas**: significa que se enviará únicamente en la visita seleccionada.

![](../../.gitbook/assets/image%20%28134%29.png)

**3. Rango de visitas**: significa que se enviará a los clientes que estén dentro del rango seleccionado. 

{% hint style="info" %}
Ejemplos: 

* Si pones 5 visitas o más significa que ese mensaje se enviará a todos aquellos clientes que tengan de 5 visitas en adelante. Es decir, alguien que tenga 7 tambien lo recibiría. 
* También podes poner desde 5 visitas hasta 10, lo que querría decir que se enviaria a todos aquellos que tengan 5, 6, 7, 8, 9 o 10 visitas.
{% endhint %}

![](../../.gitbook/assets/image%20%28146%29.png)

### Últimos tres pasos

1. Haz clic en el botón de "Terminar". 

{% hint style="info" %}
Esto guardará el mensaje pero no lo activará.
{% endhint %}

2. Prioriza tu mensaje.

{% hint style="info" %}
Con el objetivo de no convertirnos en correo no deseado, contamos con algoritmos internos anti-spam.   
  
Por eso, si un cliente, cumple con las condiciones para que se le envíen dos mensajes a la vez, solo se le enviará el que más prioridad tenga.
{% endhint %}

![](../../.gitbook/assets/image%20%28142%29.png)

3. Una vez has comprobado que tanto el contenido como el resto de parámetros está como deseas, es el momento de **activar el mensaje**.

{% hint style="success" %}
Se enviará automáticamente cada vez que el cliente cumpla con todas las condiciones configuradas.
{% endhint %}

{% page-ref page="funcionamiento-de-los-cupones.md" %}

