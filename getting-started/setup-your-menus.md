---
description: >-
  Crea y gestiona todos tus menús en la sección "Menus" en el Dashboard del
  restaurante.
---

# Configura tu Menú

## Proceso de creación

Los menús están organizados en una estructura de árbol. Los menús contienen categorías y las categorías contienen platos. El proceso de configuración general es el siguiente.

1. Crea un menú
2. Crea todas las categorías en el menú
3. Crea los platos correspondientes en cada categoría
4. Crea las opciones "option-sets" de personalización de los platos
5. Cree etiquetas "dish tags" para resaltar los atributos de los platos

{% hint style="info" %}
Es probable que solo necesites un menú. Múltiples menús son útiles si ciertos elementos están restringidos de formas particulares. Por ejemplo: un menú "Desayuno" o un menú para cada servicio: Delivery, Take Away, Dinein.
{% endhint %}

## Ejemplo de la estructura de un menú

```text
- Menu: Menú principal
-- Category: Pizzas
---- Dish: Ham & Cheese
---- Dish: Margrita
---- Dish: Veggie Supreme
-- Category: Entrantes
---- Dish: Chicken Wings
---- Dish: Fries
-- Category: Bebidas
---- Dish: Iced Tea
---- Dish: Cola
---- Dish: Water
```

## Menus

Muchas tiendas tienen un solo menú principal que siempre está disponible. Otras pueden tener un menú para el desayuno y la cena o un menú solo para un determinado servicio. Necesitarás al menos un menú para que tu tienda online funcione.

La disponibilidad del menú puede depender de diferentes condiciones, como los tipos de pedidos \(Delivery o Take Away\), los tiempos de los pedidos "order-timings" \(por ejemplo, solo pedidos por adelantado\). También se pueden restringir a determinados días y horarios.

{% hint style="info" %}
Si solo tienes un menú disponible, no es necesario que le impongas restricciones. El menú funcionará de acuerdo a los ajustes generles. Solo es necesario restringir un menú a determinadas condiciones si tiene varios menús distintos.
{% endhint %}

## Categories

Las categorías representan una subsección de un menú y constan de platos. Por ejemplo, si tienes un menú estándar, sus categorías podrían ser:

* Entrantes
* Principales
* Para acompañar
* Bebidas
* Postres

{% hint style="info" %}
En algunos casos, es posible que debas crear un menú separado en lugar de utilizar una categoría. Por ejemplo, si tienes muchas categorías diferentes de bebidas, como licores, vinos, cervezas, refrescos, etc. Es posible que prefieras crear un menú de bebidas separado para todas esas categorías en lugar de agregarlo a su menú de comida.
{% endhint %}

## Dishes

Los platos representan los artículos que se pueden comprar. Hay 2 tipos de platos:

#### Standard Dishes

Los paltos estándar funcionan de forma normal. Lo usaría para crear artículos tales como:

* Sandwich
* Pizza Prosciutto
* Helado de Vainilla

**Dish Ingredients**

Los platos estándar pueden contener una lista de ingredientes. El propósito de esto es permitir que los clientes eliminen fácilmente ciertos ingredientes. Un cliente puede eliminar los ingredientes deseados cuando selecciona el plato.

#### Combo Dishes

Los combos son un tipo especial de plato que contiene otros platos. Te permite crear una lista de opciones para que los clientes seleccionen varios platos estándar. Por ejemplo:

* Elige 3 pizzas, 2 entrantes y 2 bebidas
* Elije una hamburguesa, un entrante y una bebida

To do this you will first need to have created some standard dishes. Then when creating your combo, you can create 4 choices, 3 pizza choices and one drink choice. You can then assign dish choices to the pizzas and drinks for customers to choose from.

Para hacer esto, primero deberás haber creado algunos platos estándar. Luego, al crear tu combo, puedes crear 4 opciones, por ejemplo, 3 opciones de pizza y una opción de bebida. También puedes asignar opciones de platos a las pizzas y bebidas para que los clientes elijan.

{% hint style="info" %}
Los platos combinados no pueden contener conjuntos de opciones o ingredientes directamente. En cambio, cuando un cliente elige un plato estándar dentro de un combo, si el plato estándar elegido tiene algún conjunto de opciones asignado, el usuario puede personalizarlo en consecuencia.
{% endhint %}

#### Disponibilidad de los platos

Existen tres estados para cada plato:

* Hidden - esconde tu plato para que el cliente no pueda pedirlo
* Not available - no permite que el plato se pida y muestra que no está disponible
* Out of stock - no permite que el plato se pida y mustra que no quedan unidades

En el Dashboard, puedes editar el estado de un plato marcando la casilla de verificación a la izquierda. Luego, seleccione el estado deseado en el menú emergente.

## Option Sets

Toda la personalización de platos se realiza mediante los "option sets". Estos son un conjunto configurable de opciones que se pueden asignar a cualquier plato. Puedes crear opciones tales como:

* Selecciona el tamaño
* Seleciona la salsa
* Selecciona el acompañamiento

{% hint style="info" %}
Para crear tus opciones, dentro de "Menu", ve a "Option Sets", dale a "Create New Option Set", añade las opciones, la diferencia en el precio si esta existe, y asigna el combo a los platos correspondientes.
{% endhint %}

## Dish Tags

Las etiquetas te permiten resaltar atributos muy particulares sobre un plato con un indicador visual totalmente personalizable. Puedes crear etiquetas tales como:

* Picante
* Vegano
* Sin Gluten

## Posibles Problemas

### **No se muestran los menús ni las categorías**

Para que tu menú se muestre en tu tienda online, asegúrate de agregarle al menos una categoría y un plato.

### **Las imágenes son demasiado grandes**

Tamaño obligatorio del archivo &lt;1MB, idealmente rectangulares y con el plato en el centro de la imagen, con un tamaño recomendado de imagen de 16:9 para las fotos del menú, y de 19:5 para el header.

Todas las fotos deben de tener un tamaño máximo de 1MB. Te recomendamos que uses [esta web](https://bulkresizephotos.com/es) para comprimir tus fotos, cargando tus fotos primero y luego eligiendo la opción "Tamaño del archivo" en el menú de la izquierda, para comprimir tus fotos a 980 KBs o menos.

{% hint style="info" %}
El nombre de archivo de las fotos no debe contener caracteres especiales, de lo contrario, podrían no cargarse correctamente.
{% endhint %}

### Descripciones de los platos

Utilizar campo “Subtitle” para las descripciones

### Alérgenos

Tenemos dos opciones:

1. Usar el campo “Description” para añadir los alérgenos de cada plato
2. Añadir un enlace debajo del header que apunte directamente a una carta/documento de alérgenos

