---
description: >-
  Una vez has completado la configuración de tu tienda, ya estás en disposición
  de recibir pedidos. Serán claves todas las acciones destinadas a atraer a tus
  clientes a tu web.
---

# Optimiza tu Tienda Online

## Los 7 pecados capitales de la venta online

Te compartimos [en este enlace](https://www.es.cheerfy.com/academy/los-7-pecados-capitales-de-la-venta-online) un artículo realizado por la [Cheerfy Academy](https://www.es.cheerfy.com/academy), en el que se describen diferentes acciones que debes llevar a cabo.

## Paid Media

Recomendamos la utilización de Facebook o Google Ads para atraer clientes a tu tienda ya que suponen una forma "barata" y sencilla de impactar a tu público objetivo.

### Facebook Pixel

Añade tu Pixel de Facebook a tu tienda online para rastrear visitantes y analizar conversiones.

**Proceso de configuración:**

1. Ve a "Settings" - "Website" - "Custom CSS & Javascript".
2. Verás de cajas: "HTML Head Code" y HTML Body Code".
3. Añade en "HTML Head Code" el siguiente script. Incluye tu Pixel sustituyédolo por lo marcado en negrita:  
  
   _&lt;!-- Facebook Pixel Code --&gt;_

   _&lt;script&gt;_

     _!function\(f,b,e,v,n,t,s\)_

     _{if\(f.fbq\)return;n=f.fbq=function\(\){n.callMethod?_

     _n.callMethod.apply\(n,arguments\):n.queue.push\(arguments\)};_

     _if\(!f.\_fbq\)f.\_fbq=n;n.push=n;n.loaded=!0;n.version='2.0';_

     _n.queue=\[\];t=b.createElement\(e\);t.async=!0;_

     _t.src=v;s=b.getElementsByTagName\(e\)\[0\];_

     _s.parentNode.insertBefore\(t,s\)}\(window, document,'script',_

     _'https://connect.facebook.net/en\_US/fbevents.js'\);_

     _fbq\('init', '**{your-pixel-id-goes-here}**'\);_

     _fbq\('track', 'PageView'\);_

   _&lt;/script&gt;_

   _&lt;!-- End Facebook Pixel Code --&gt;_  

4. Añade en "HTML Body Code" el siguiente script. Incluye tu Pixel sustituyédolo por lo marcado en negrita:  
  
   &lt;script src="[https://static.cheerfy.com/integration/cheerfy\_cw\_facebook\_analytics.js](https://static.cheerfy.com/integration/cheerfy_cw_facebook_analytics.js)"&gt;&lt;/script&gt;  
   &lt;noscript&gt;

     &lt;img height="1" width="1" style="display:none" 

          src="https://www.facebook.com/tr?id=**{your-pixel-id-goes-here}**&ev=PageView&noscript=1"/&gt;

   &lt;/noscript&gt;&lt;!-- End Facebook Pixel Code --&gt;

![](.gitbook/assets/image%20%2892%29.png)

{% hint style="danger" %}
Recuerda no borrar los scripts que ya estuviesen añadidos. Añádelos debajo de los que ya estaban.
{% endhint %}

### Google Analytics

Añade el seguimiento de Google Analytics a tu tienda online para rastrear a tus visitantes.

**Proceso de configuración:**

1. Ve a "Settings" - "Website" - "Custom CSS & Javascript".
2. Verás de cajas: "HTML Head Code" y HTML Body Code".
3. Añade en "HTML Head Code" el siguiente script. Incluye tu GTM Id sustituyédolo por lo marcado en negrita:  
  
   &lt;!-- Google Tag Manager --&gt;

   &lt;script&gt;\(function\(w,d,s,l,i\){w\[l\]=w\[l\]\|\|\[\];w\[l\].push\({'gtm.start':

   new Date\(\).getTime\(\),event:'gtm.js'}\);var f=d.getElementsByTagName\(s\)\[0\],

   j=d.createElement\(s\),dl=l!='dataLayer'?'&l='+l:'';j.async=true;j.src=

   'https://www.googletagmanager.com/gtm.js?id='+i+dl;f.parentNode.insertBefore\(j,f\);

   }\)\(window,document,'script','dataLayer','**your-gtm-id-goes-here**'\);&lt;/script&gt;

   &lt;!-- End Google Tag Manager --&gt;  
   __

4. Añade en "HTML Body Code" el siguiente script:  
  
   &lt;script src="https://static.cheerfy.com/integration/cheerfy\_cw\_google\_analytics.js"&gt;&lt;/script&gt;  
   &lt;!-- Google Tag Manager \(noscript\) --&gt;

   &lt;noscript&gt;&lt;iframe src="https://www.googletagmanager.com/ns.html?id=GTM-PXJDSZ7"

   height="0" width="0" style="display:none;visibility:hidden"&gt;&lt;/iframe&gt;&lt;/noscript&gt;

   &lt;!-- End Google Tag Manager \(noscript\) --&gt;  

![](.gitbook/assets/image%20%2893%29.png)

{% hint style="danger" %}
Si la propiedad fue creada reciéntemente, se requieren 24 horas para que Google Analytics comience a reportar datos
{% endhint %}

