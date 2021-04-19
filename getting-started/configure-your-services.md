---
description: >-
  Los servicios de tu restaurante representan los distintos tipos de pedidos que
  aceptas.
---

# Configura los servicios

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

## Apuntes del servicio

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

Automated statuses change an order's status after a set period of time has passed. This will allow you to do things such as:

* Automatically confirm new orders
* Mark orders as ready after a period of time
* Mark orders as complete after a period of time

This is very helpful if you know your business timings well and don't want to manually be updating order statuses. Auto status updates can also be enabled or disabled on a per status basis. This way you can provide estimated wait times without auto-updating statuses. Or you can just instantly confirm orders and handle the rest manually.

For automated status updates to work, you will need to enable it for a particular status and ensure the timing settings are added to that particular status.

#### How automated statuses work

Status updates are dependent on your timing settings, the type of order and the order due time. It's best explained through a series of examples.

For the examples, we will assume our timing settings are as follows

* Time till confirm - 10 minutes
* Time till ready - 10 minutes
* Time till on route - 10 minutes
* Time till complete - 60 minutes

#### Pickup and dine-in examples

If a customer places an order at 7:00pm for pickup or dine in which is due immediately

| Time | Action |
| :--- | :--- |
| 7:00pm | Order has been placed, status unconfirmed |
| 7:10pm | Status updated to confirmed because time till confirm is 10 minutes |
| 7:20pm | Status updated to ready because time till ready is 10 minutes. This would also be the estimated order ready time as shown to the customer. |
| 8:20pm | Status updated to complete because time till complete is 60 minutes |

In the event that you added an extra 10 minutes onto the customers estimated order ready time, it will play out as follows:

| Time | Action |
| :--- | :--- |
| 7:00pm | Order has been placed, status unconfirmed, you add 10 minutes to estimated ready time |
| 7:10pm | Status updated to confirmed because time till confirm is 10 minutes |
| 7:30pm | Status updated to ready because the old ready time was 7:20pm, since you added an extra 10 minutes, that becomes 7:30pm |
| 8:30pm | Status updated to complete because time till complete is 60 minutes |

If we are unable to calculate an estimated ready time for the order, for example if the time till confirm was missing, it would play out as follows

| Time | Action |
| :--- | :--- |
| 7:00pm | Order has been placed, status unconfirmed |
| 7:05pm | You manually update the order status to confirmed |
| 7:15pm | Status updated to ready, because the time till ready is 10 minutes |
| 8:15pm | Status updated to complete because time till complete is 60 minutes |

If a customer places an order at 6:00pm for pickup or dine in which is due at 7:00pm, the following would occur

| Time | Action |
| :--- | :--- |
| 6:00pm | Order has been placed, status unconfirmed |
| 6:10pm | Status updated to confirmed because time till confirm is 10 minutes |
| 7:00pm | Status updated to ready, because this is when the customer scheduled the order for |
| 8:00pm | Status updated to complete because time till complete is 60 minutes |

#### Delivery examples

For the delivery examples, we will assume the driving time between your store and the delivery address is calculated as 10 minutes.

If a customer places a delivery order at 7:00pm which is due immediately

| Time | Action |
| :--- | :--- |
| 7:00pm | Order has been placed, status unconfirmed |
| 7:10pm | Status updated to confirmed because time till confirm is 10 minutes |
| 7:20pm | Status updated to ready because time till ready is 10 minutes |
| 7:30pm | Status updated to on route because time till on route is 10 minutes. This would also be shown to you as the driver pickup time |
| 7:40pm | Order will have been delivered to customer since the driving time is 10 minutes |
| 8:40pm | Order marked as completed because time till complete is 60 minutes |

If we were unable to calculate the estimated delivery time and driver pickup time, say if the time till on route was missing, the following would occur

| Time | Action |
| :--- | :--- |
| 7:00pm | Order has been placed, status unconfirmed |
| 7:10pm | Status updated to confirmed because time till confirm is 10 minutes |
| 7:20pm | Status updated to ready because time till ready is 10 minutes |
| 7:40pm | You manually mark the order an on route for delivery |
| 7:50pm | Order will have been delivered to customer since the driving time is 10 minutes |
| 8:50pm | Order marked as completed because time till complete is 60 minutes |

If a customer places a delivery order at 6:00pm which is due at 7:00pm, the following would occur

| Time | Action |
| :--- | :--- |
| 6:00pm | Order has been placed, status unconfirmed |
| 6:10pm | Status updated to confirmed because time till confirm is 10 minutes |
| 6:40pm | Status updated to ready because delivery time is 10 minutes and time till on route is 10 minutes, which means that the order must be ready by this time if it is going to reach your customer at 7:00pm |
| 6:50pm | Status updated to on route because the delivery time is 10 minutes, so it has to leave your store at this time. This is also the estimated driver pickup time. |
| 7:00pm | Order will have been delivered to customer |
| 8:00pm | Order marked as completed because time till complete is 60 minutes |

If a delivery order is scheduled for a later time but the estimated delivery time could not be calculated, then the ready and on route status will not update automatically.

{% hint style="info" %}
If ever in doubt about how the auto status timings will work for you scenario, just think about how it would logically work in a way that makes sense to your customer and you. That is how we have designed it to work.
{% endhint %}

