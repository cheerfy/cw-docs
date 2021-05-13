---
description: >-
  Encuentra aquí todas las opciones para la gestión de los envíos a domicilio y
  cómo configurarlas.
---

# Gestión de Envíos

## Integración con Empresa de Couriers

{% tabs %}
{% tab title="Stuart" %}
**Proceso de configuración:**

1. Abre tu cuenta de Stuart [aquí](https://dashboard.stuart.com/).
2. Envíanos el API Client Id y el API Secret para cada cuenta de Stuart a [soporte@cheerfy.com](mailto:soporte@cheerfy.com) para conectarlas a Cheerfy.
3. Configura el webhook de Cheerfy en tu cuenta de Stuart. Para ello, añade la URL [https://webhook.cheerfy.com/delivery-notification/](https://webhook.cheerfy.com/delivery-notification/) en donde te mostramos en la imagen:

![](../.gitbook/assets/image%20%2860%29.png)
{% endtab %}

{% tab title="Mox" %}
**Proceso de configuración:**

1. Abre tu cuenta de Mox.
2. Envíanos el API Key y los Site IDs para tu cuenta de Mox a [soporte@cheerfy.com](mailto:soporte@cheerfy.com) para conectarlas a Cheerfy.
{% endtab %}
{% endtabs %}

## Radio de Cobertura

{% hint style="success" %}
Es fundamental dibujar el mapa exacto con la zona a la que quieres llegar desde tu restaurante para garantizar que todos tus clientes dentro de ese radio reciban correctamente sus pedidos.
{% endhint %}

### Cómo dibujar el mapa

1. Crea y  Gestiona tus mapas en [custom Google Maps](https://www.google.com/maps/d/u/0/).
2. Si quieres crear un polígono a mano, puedes hacerlo directamente desde Google Maps.
3. Si quieres crear un círculo, entonces usa [KML circle polygon generator](https://t.sidekickopen80.com/s1t/c/5/f18dQhb0S7lM8dDMPbW2n0x6l2B9nMJN7t5X-FfhMynW4Y92Qn3M2hXxW56dPbl4gz_sd102?te=W3R5hFj4cm2zwW3X-05h3F7-KLW3ZV6hS3K76ZWW3zhsHl1JzBqYW43Sm-p45SVD94mLXp1&si=7000000001726662&pi=3b31b7c5-8b91-4630-bc18-765dfa0800c0) ya que Google Maps solo permite la creación de polígonos.
4. Si quieres dar cobertura a un determinado código postal, usa este enlace para descargar los kml ya creados: [www.codigospostales.com/kml/28/28001.kml](http://www.codigospostales.com/kml/28/28001.kml). Siguiendo con este ejemplo, el primer 28 serían los primeros 2 dígitos del CP, y 28001 sería el CP entero que deseas obtener.
5. Para poder importar en Cheerfy, necesitas tener todas las figuras en un único fichero kml \(uno por restaurante\). Para ello, usa [KML file merger](https://t.sidekickopen80.com/s1t/c/5/f18dQhb0S7lM8dDMPbW2n0x6l2B9nMJN7t5X-FfhMynW4Y92Qn3M2hXxW56dPbl4gz_sd102?te=W3R5hFj4cm2zwW3X-06t3K8Q1Gw49hBZt48S2&si=7000000001726662&pi=3b31b7c5-8b91-4630-bc18-765dfa0800c0) para unir múltiples ficheros kml en uno solo.
6. Una vez tienes un fichero kml unificado, impórtalo en Google Maps, donde podrás renombrar y ordenar a tu gusto.
7. Para terminar, exporta un fichero por local desde Google Maps, e importa ese fichero en Cheerfy Shop en "Settings" - "Services" - "Delivery" - "Zones". 

#### Te mostramos en estos dos pantallazos cómo realizar este último paso

![](../.gitbook/assets/image%20%2869%29.png)

![](../.gitbook/assets/image%20%2868%29.png)

