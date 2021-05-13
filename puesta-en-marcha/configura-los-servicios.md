---
description: >-
  Los servicios de tu restaurante representan los distintos tipos de pedidos que
  aceptas.
---

# Configura los Servicios

Hay 4 tipos de servicios disponibles:

* Pickup - pedidos de Take Away o para recoger en tienda
* Delivery - pedidos a domicilio
* Dine-in - pedidos producidos en el restaurante
* Table booking - reserva de una mesa a una fecha y hora

## Cómo configurar los servicios

1. Visita el Dashboard de tu restaurante y ve a "Settings"
2. Selecciona la pestaña "Services" y edita su configuración según sea necesario

## Activa o desactiva un servicio

Puedes habilitar o deshabilitar servicios según sea necesario. Ve a la configuración de servicio deseada y simplemente cambie el interruptor "Enabled" para habilitarlo o deshabilitarlo.

{% hint style="info" %}
Para que la tienda funcione tienes que tener al menos un servicio activado
{% endhint %}

## Notas del servicio

Puedes agregar notas personalizadas en "Pickup notes" para cada servicio que se mostrarán al cliente cuando se seleccione. Útil si necesitas transmitir un mensaje importante a tu cliente.

## Tiempos de pedido

Un cliente solo puede realizar un pedido con vencimiento inmediato si su tienda está abierta. Los pedidos para una fecha posterior deben programarse dentro de su horario de apertura. Como tal, los horarios de los pedidos están controlados principalmente por el horario de apertura de su tienda. A partir de ahí, cada servicio tiene su propia configuración de tiempo de pedido por separado que le permite un control más profundo.

### Activar y desactivar los tiempos de pedido

En la pestaña "Order Timings" en la configuración del servicio, puedes habilitar y deshabilitar tanto los pedidos inmediatos \("Enable Immediate Orders"\) como los programados \("Enable Later Orders"\).

### First Order Offset

Este es el período de tiempo desde que su tienda abre hasta que acepta el primer pedido. Por ejemplo, si aquí añades 30 minutos y tu tienda abre a las 9:00am, el primer pedido se podrá realizar o programar a las 9:30am.

### Last Order Offset

Este es el período de tiempo desde que tu tienda cierra hasta que se acepta el último pedido. Por ejemplo, si aqué añades 30 minutos y tu tienda cierra a las 9:00pm, el último pedido se podrá realizar o programar a las 8:30pm.

### Order Offset

Esto solo afecta a los pedidos programados. Este es el tiempo a partir de ahora en el que se puede realizar un pedido programado. Es para evitar que los clientes programen un pedido en los próximos 10 minutos en lugar de que lo pida para ahora.

Por ejemplo, si añades aquí 30 minutos y la hora actual son las 6:00pm, la próxima vez que un cliente puede programar un pedido sería a las 7:00pm. Si lo quieren antes de las 7:00pm, lo pedirán para ahora. Si añadieses 15 minutos, el cliente podría programar un pedido para las 6:30 pm.

Este campo también sirve como punto de corte para dar tiempo a cumplir con la hora programada de los pedidos. Por ejemplo, si son las 6:00pm, has añadido 30 minutos, y el cliente está programando un pedido para las 7:00 pm, debe realizar el pedido antes de las 6:30 pm. Esto es para que tengas tiempo a cumplir con la hora programada.

## Personaliza las horas de cada servicio

Cada servicio puede tener su propio horario de funcionamiento independiente. Establecer horas de funcionamiento personalizadas para un servicio en particular anulará las horas de funcionamiento generales establecidas para tu restaurante.

## Tiempos de espera estimados y estados automáticos

Para ayudarte a administrar mejor los pedidos y las expectativas de los clientes, proporcionamos una forma simplificada de calcular los tiempos de espera actualizando los estados automáticamente. Hay 6 estados de pedido:

* Un-confirmed
* Confirmed
* Ready
* On Route \(Solo para Delivery\)
* Complete
* Cancelled

Tanto los tiempos de espera estimados como las actualizaciones de estado automatizadas están sincronizados. Esto evita cualquier confusión del cliente. Estos ajustes de tiempo son:

| Setting \(minutes\) | Del Estado | Al Estado |
| :--- | :--- | :--- |
| Time till confirm | Unconfirmed | Confirmed |
| Time till ready | Confirmed | Ready |
| Time till on route \(solo para Delivery\) | Ready | On Route |
| Time till complete | Ready | Complete |

{% hint style="info" %}
* Time till confirm es el tiempo que transcurre desde que se realiza un pedido hasta que se confirma. Establecer el tiempo hasta la confirmación en "0" dará como resultado la confirmación instantánea del pedido. 
* Time till ready es el tiempo que le lleva preparar un pedido una vez confirmado.
* Time till on route es el tiempo entre el momento en que se prepara un pedido y el momento en que el conductor de entrega lo recoge.
* Time till complete es útil para marcar automáticamente los pedidos como completos.
{% endhint %}

{% hint style="success" %}
* Para que esto funcione de forma automática, debes activar que los servicios se actualicen automáticamente en "Enable Automated Order Statuses".
* Configura solo los parámetros que necesites.
{% endhint %}

### Estimated Wait Times

Los tiempos de espera del cliente se calculan utilizando los ajustes de tiempo anteriores.

#### Cómo se calcula el tiempo de espera estimado para los pedidos de Take Away o Dine-in

El tiempo de espera estimado se calcula por la suma del **time till confirm** con **time till ready**. Por ejemplo, si tu **time till confirm** es de 5 minutos y tu **time till ready** es de 20, el cliente obtendría un tiempo de espera estimado de 20 + 5 = 25 minutos.

If you have not added a value for time till confirm or time till ready, the estimated wait time would not be calculated.

Si no has agregado ningún valor para el time til confirm o time till ready, no se calculará el tiempo de espera estimado.

#### Cómo se calcula el tiempo de espera estimado para los pedidos de Delivery

For deliveries, the wait time is calculating by adding the **time till confirm** + **time till ready** + **time till on route** together. Then the **driving time** is added onto that. The driving time is determined using an external service that takes into account traffic data. This provides the customer with an extremely accurate wait time for their order to be delivered. Assuming

El tiempo de espera se calcula sumando el **time till confirm** + **time till ready** + **time till on route**. Luego, el **tiempo de conducción** se suma a eso. El tiempo de conducción se determina mediante un servicio externo que tiene en cuenta los datos del tráfico. Esto proporciona al cliente un tiempo de espera extremadamente preciso para que se entregue su pedido. 

Si no ha agregado un valor para el **time till confirm**, **time till ready** o **time till on route**, no se calculará.

### Automated Statuses

Los estados automatizados cambian el estado de un pedido una vez transcurrido un período de tiempo determinado. Esto te permitirá hacer cosas como:

* Confirmar automáticamente nuevos pedidos.
* Marcar tus pedidos como listos después de un periodo de tiempo.
* Marcar tus pedidos como completados después de un periodo de tiempo.

Esto es muy útil si conoces bien los tiempos de tu negocio y no quieres tener que actualizar manualmente los estados de los pedidos. Las actualizaciones de estado automáticas también se pueden habilitar o deshabilitar según el estado. De esta manera, puedes proporcionar tiempos de espera estimados sin actualizar automáticamente los estados. O simplemente puedes confirmar los pedidos instantáneamente y manejar el resto manualmente.

Para que las actualizaciones de estado automáticas funcionen, deberás habilitarlas para un estado en particular y asegurarte de añadir los tiempos correspondientes.

#### Cómo funcionan los estados automatizados

Las actualizaciones de estado dependen de la configuración de tiempo, el tipo de pedido y la fecha de vencimiento del pedido. Se entiende mejor a través de una serie de ejemplos.

Para los ejemplos, asumimos que nuestra configuración de tiempo es la siguiente:

* Time till confirm - 10 minutos
* Time till ready - 10 minutos
* Time till on route - 10 minutos
* Time till complete - 60 minutos

#### Ejemplos de Pickup y dine-in

Un cliente realiza un pedido a las 7:00 pm para recogerlo o tomar en el local, para ya mismo en el que vence de inmediato.

| Time | Action |
| :--- | :--- |
| 7:00pm | Se realiza el pedido. El estado sigue siendo "unconfirmed". |
| 7:10pm | Estado actualizado a "confirmed" porque el "time till confirm" es de 10 minutos. |
| 7:20pm | El estado se actualiza a "ready" porque el "time till ready" es de 10 minutos. Este también sería el tiempo estimado de preparación que se muestra al cliente. |
| 8:20pm | El estado se actualiza a "complete" porque el "time till complete" es de 60 minutos. |

Un cliente realiza a las 6:00pm un pedido programado para recogerlo o tomar en el local a las 7:00pm:

| Time | Action |
| :--- | :--- |
| 6:00pm | Se realiza el pedido. El estado sigue siendo "unconfirmed". |
| 6:10pm | Estado actualizado a "confirmed" porque el "time till confirm" es de 10 minutos. |
| 7:00pm | El estado se actualiza a "ready" porque es para cuando el cliente programó el pedido. |
| 8:00pm | El estado se actualiza a "complete" porque el "time till complete" es de 60 minutos. |

#### Ejemplos de Delivery

Para este ejemplo, asumimos que el tiempo de conducción entre tu local y la dirección de entrega es de 10 minutos.

Un cliente hace un pedido de Delivery a las 7:00pm para ya mismo

| Time | Action |
| :--- | :--- |
| 7:00pm | Se realiza el pedido. El estado sigue siendo "unconfirmed". |
| 7:10pm | Estado actualizado a "confirmed" porque el "time till confirm" es de 10 minutos. |
| 7:20pm | El estado se actualiza a "ready" porque el "time till ready" es de 10 minutos. |
| 7:30pm | El estado se actualiza a "on route" porque el "time till on route" es de 10 minutos. Esta también sería la hora a la que el rider recogería el pedido. |
| 7:40pm | El pedido se habrá entregado al cliente ya que el tiempo de conducción es de 10 minutos. |
| 8:40pm | El estado se actualiza a "complete" porque el "time till complete" es de 60 minutos. |

Un cliente realiza a las 6:00pm un pedido programado para ser recibido a las 7:00pm:

<table>
  <thead>
    <tr>
      <th style="text-align:left">Time</th>
      <th style="text-align:left">Action</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">6:00pm</td>
      <td style="text-align:left">Se realiza el pedido. El estado sigue siendo &quot;unconfirmed&quot;.</td>
    </tr>
    <tr>
      <td style="text-align:left">6:10pm</td>
      <td style="text-align:left">Estado actualizado a &quot;confirmed&quot; porque el &quot;time till confirm&quot;
        es de 10 minutos.</td>
    </tr>
    <tr>
      <td style="text-align:left">6:40pm</td>
      <td style="text-align:left">
        <p>Status updated to ready because delivery time is 10 minutes and time till
          on route is 10 minutes, which means that the order must be ready by this
          time if it is going to reach your customer at 7:00pm</p>
        <p>El estado se actualiza a &quot;ready&quot; porque el &quot;time till ready&quot;
          es de 10 minutos y el tiempo de conducci&#xF3;n es de 10 minutos, lo que
          significa que el pedido debe estar listo a esta hora para que pueda llegar
          a las 7:00 p.m.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">6:50pm</td>
      <td style="text-align:left">El estado se actualiza a &quot;on route&quot; porque el tiempo de conducci&#xF3;n
        es de 10 minutos. Esta tambi&#xE9;n ser&#xED;a la hora a la que el rider
        recoger&#xED;a el pedido.</td>
    </tr>
    <tr>
      <td style="text-align:left">7:00pm</td>
      <td style="text-align:left">El pedido se habr&#xE1; entregado al cliente.</td>
    </tr>
    <tr>
      <td style="text-align:left">8:00pm</td>
      <td style="text-align:left">El estado se actualiza a &quot;complete&quot; porque el &quot;time till
        complete&quot; es de 60 minutos.</td>
    </tr>
  </tbody>
</table>

{% hint style="info" %}
Si tienes dudas sobre cómo funcionarán los tiempos de estado automático para tu escenario, piensa en cómo funcionaría lógicamente de una forma que tenga sentido para tu cliente y para tu restaurante. Así es como lo hemos diseñado para que funcione.
{% endhint %}

