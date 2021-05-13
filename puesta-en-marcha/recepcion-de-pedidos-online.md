---
description: >-
  Encuentra aquí todas las opciones para la gestión de la recepción de pedidos y
  cómo configurarlas.
---

# Recepción de Pedidos Online

## Integración con el POS

{% hint style="success" %}
Opción recomendada siempre que sea posible
{% endhint %}

**Encuentra aquí la lista de softwares con los que estamos integrados:**

1. Deliverect
2. Ordatic
3. Revel
4. Last
5. Revo
6. Sinqro
7. Tierra
8. Nextt
9. Agora

### Parámetros necesarios para la integración de cada POS

{% tabs %}
{% tab title="Deliverect" %}
![](../.gitbook/assets/image%20%2811%29.png)
{% endtab %}

{% tab title="Ordatic" %}
![](../.gitbook/assets/image%20%2812%29.png)
{% endtab %}

{% tab title="Revel" %}
![](../.gitbook/assets/image%20%2817%29.png)
{% endtab %}

{% tab title="Last" %}
![](../.gitbook/assets/image%20%2820%29.png)
{% endtab %}

{% tab title="Revo" %}
![](../.gitbook/assets/image%20%2813%29.png)
{% endtab %}

{% tab title="Sinqro" %}
![](../.gitbook/assets/image%20%2818%29.png)
{% endtab %}

{% tab title="Tierra" %}
![](../.gitbook/assets/image%20%2821%29.png)
{% endtab %}

{% tab title="Nextt" %}
![](../.gitbook/assets/image%20%2814%29.png)
{% endtab %}

{% tab title="Agora" %}
![](../.gitbook/assets/image%20%2810%29.png)

![](../.gitbook/assets/image%20%2816%29.png)
{% endtab %}
{% endtabs %}

## Conectarnos a vuestras impresoras

{% hint style="success" %}
Recomendamos esta opción en caso de no poder proceder con la integración anterior.
{% endhint %}

**Requisitos de configuración:**

* Impresoras conectadas por red, usb o cable serie**.**
* Equipo Android o Windows.
* Este equipo tiene que estar conectado a la red o conectado por cable a la impresora. 
* El equipo tiene que estar siempre activo porque va a hacer de servidor de impresión.

**Proceso de configuración en Cheerfy Shop:**

* Abre Cheerfy Shop.
* Ve a "Settings" - "System" - "Receipt Printing", y configurar los siguientes parámetros:
* En el apartado "General", configura:
  1. Name = Nombrar impresora
  2. Auto Print Orders = ON
  3. Receipt Language & Locale = Spanish o English

![](../.gitbook/assets/image%20%2842%29.png)

* En el apartado "Printer Settings", configura:
  1. Printing Method = ESCPOS
  2. ESCPOS Printing Type = ESCPOS Image

{% hint style="danger" %}
Después de configurar Push Printer \(siguiente paso\), si el ticket saliese cortado o sin verse del todo bien, habrá que jugar con el parámetro “Paper Scale Factor”. Por defecto viene en “2”, si fallase, el “1,6” suele funcionar.
{% endhint %}

![](../.gitbook/assets/image%20%2841%29.png)

**Proceso de configuración en equipo Android o Windows:**

1. Instalar la aplicación [PushPrinter](https://t.sidekickopen80.com/s1t/c/5/f18dQhb0S7lM8dDMPbW2n0x6l2B9nMJN7t5X-FfhMynW2z8MG-8qlTmnW56dR0l4tbXZv102?te=W3R5hFj4cm2zwW45W42x45TQMlW4fGCmn3Fbt5S0&si=7000000002009724&pi=232c4efc-392a-4384-f408-610d3d88b369) en el equipo que va a hacer de servidor de impresión.
2. Al abrir la aplicación, ir al menú de ajustes \("Settings"\) y marcar la opción de “arrancar el servicio siempre”.
3. En settings, marcar la opción de servicio "Default".
4. Ir a la opción "impresoras" y crear una nueva impresora.
5. Cuando se crea la impresora hay que poner el nombre de la impresora \(en Windows y con impresoras conectadas por USB, puede que haya que añadir la impresora a "Impresoras Compartidas" para que funcione\).
6. Seleccionar "Printing Type" de un combo, dependiendo del tipo de conexión a la impresora. Según la opción seleccionada habrá que rellenar algún campo adicional como IP o Puerto de impresora.
7. Configurar nuestros tokens en cada una de vuestras impresoras. Podéis encontrarlos en "System" - "Receipt Printing":

![](../.gitbook/assets/image%20%2838%29.png)

{% hint style="warning" %}
Realiza pruebas de impresión para comprobar que todo funciona correctamente.
{% endhint %}

## Utiliza nuestro Dashboard de Gestión de Pedidos

Nuestro Dashboard de Gestión de Pedidos siempre está disponible independientemente de haber realizado alguna de las opciones anteriores. Será tu única opción en caso de no poder proceder con ninguna de las ateriores.

> Accesible en "Cheerfy Shop" - "Orders":

![](../.gitbook/assets/image%20%2829%29.png)

