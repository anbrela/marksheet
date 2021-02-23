---
layout: post
title: "CSS <strong>transiciones</strong>"
subtitle: "De una regla a otra"
section: css
---

Las <strong>transiciones</strong> en CSS permiten pasar sin problemas del estado de un elemento a otro. Funciona de manera en que las propiedades **individuales** se animan de un estado **inicial** a uno **final**.

Puedes definir:

- `transition-property`: las **propiedades** a animar
- `transition-duration`: **cuanto dura** la animación
- `transition-timing-function`: como se calcula el **cálculo intermediario**
- `transition-delay`: para empezar la animación **después** de un tiempo determinado

Puede establecer cada propiedad CSS individualmente o utilizar la versión abreviada: 'transición'. En ese caso, solo la duración **es obligatoria**.

Tenga en cuenta que una **transición es un tipo específico de _animation_, donde solo hay un inicio y un estado final**

.### Ejemplo Rápido

Las transiciones se utilizan a menudo en **hover states**.

{% highlight css %}
a{ background: lightgrey; color: grey;}
a:hover{ background: yellow; color: red;}
a.with-transition{ transition: 1s;}
{% endhighlight %}

<div class="result" id="result-841">
  <a>Without transition</a>
  <a class="with-transition">With transition</a>
</div>

En lugar de que las reglas CSS flotantes sean **instantáneas**, tanto el fondo _como_ los colores de texto se animan lentamente.

### transition-duration

La duración de una transición es la única propiedad CSS necesaria para crear una transición.Se puede establecer en **segundos** '2s' o **milisegundos** '100ms'.

Si quieres que tu transición dure **medio segundo**, puedes escribir '0.5s' o '500ms'. Dependiendo de lo rápido que desee que sean sus transiciones, una unidad podría ser más fácil y/o más rápida de escribir.

{% highlight css %}
a{ background: lightgrey; color: grey;}
a:hover{ background: yellow; color: green;}
a.with-fast-transition{ transition-duration: 0.5s;}
a.with-slow-transition{ transition: 3s;}
{% endhighlight %}

<div class="result" id="result-842">
  <a>Sin transición</a>
  <a class="with-fast-transition">Transición de 0.5s</a>
  <a class="with-slow-transition">3s de transición</a>
</div>

### transition-property

Solo se puede animar **1/3** de las propiedades CSS. Mozilla tiene una [lista completa](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_animated_properties).

De forma predeterminada, la propiedad 'transition-property' tiene un valor de 'all', lo que simplemente significa que animará todas las propiedades posibles.

Solo puede decidir animar 1 o varias propiedades.

{% highlight css %}
a{ background: lightgrey; color: grey;}
a:hover{ background: yellow; border: 5px solid blue; color: green;}
a.with-background-transition{ transition-duration: 2s; transition-property: background;}
a.with-all-transition{ transition-duration: 2s;}
{% endhighlight %}

<div class="result" id="result-843">
  <a>Sin transición</a>
  <a class="with-background-transition">Con una transición de fondo</a>
  <a class="with-all-transition">Con todas las transiciones</a>
</div>

La propiedad 'border' es totalmente animable y permite visualizar fácilmente la transición lenta (2 segundos).

### transition-timing-function

La función de sincronización determina cómo se calcula **value** de cada propiedad **durante la transición**.

De forma predeterminada, la transición es **eased**: se acelera al principio y se ralentiza al final.

Puede asegurarse de que la transición se realizará a una velocidad constante **.Las funciones de sincronización pueden hacer que la transición **accelerate** y/o **slow down\*\*.

La forma más fácil de visualizar las funciones de sincronización es alterando las propiedades **position**, como 'left'.

{% highlight css %}
div{ left: 0; position: relative; transition: 1s;}
main:hover div{ left: 200px;}
.ease{ transition-timing-function: ease;} /_ Default behavior _/
.linear{ transition-timing-function: linear;} /_ Constant speed _/
.ease-in{ transition-timing-function: ease-in;}
.ease-out{ transition-timing-function: ease-out;}
.ease-in-out{ transition-timing-function: ease-out;}
{% endhighlight %}

{% highlight html %}

<main>
  <p><strong>Ease</strong>: empieza lento, rápido en la mitad, final lento</p>
  <div class="ease"></div>
  <p><strong>Linear</strong>: velocidad lineal</p>
  <div class="linear"></div>
  <p><strong>Ease In</strong>: inicio lento, rápido final</p>
  <div class="ease-in"></div>
  <p><strong>Ease Out</strong>: inicio lento, final lento</p>
  <div class="ease-out"></div>
  <p><strong>Ease In Out</strong>: como el **ease**, but with more pronounced acceleration/deceleration curves</p>
  <div class="ease-in-out"></div>
</main>
{% endhighlight %}

<div class="result" id="result-844">
  <p><strong>Ease</strong>: slow start, fast middle, slow end</p>
  <div class="ease"></div>
  <p><strong>Linear</strong>: constant speed</p>
  <div class="linear"></div>
  <p><strong>Ease In</strong>: slow start, fast end</p>
  <div class="ease-in"></div>
  <p><strong>Ease Out</strong>: fast start, slow end</p>
  <div class="ease-out"></div>
  <p><strong>Ease In Out</strong>: like ease, but with more pronounced acceleration/deceleration curves</p>
  <div class="ease-in-out"></div>
</div>

Keep in mind that all transitions take the **same amount of time** (1 second).

If you want to visualize how other timing functions work, check out this [Easing Functions Cheat Sheet](https://easings.net/).

#### cubic-bezier

If all these **pre-defined** timing functions don't suit you, you can write your own using **cubic bezier** functions.

The website [cubic-bezier.com](https://cubic-bezier.com/) is a simple tool to visually write your own curves.

### transition-delay

A **delay** will define how long the transitions has to **wait** _before_ actually starting.

Like `transition-duration`, you can either use seconds `s` or milliseconds `ms`.

{% highlight css %}
a{ background: blue; color: white; transition: all 1s;}
div:hover a{ background: red;}
a.with-delay{ transition-delay: 1s;}
{% endhighlight %}

{% highlight html %}

<div>
  <p>Hover the grey area</p>
  <a>Without any delay</a>
  <a class="with-delay">With a second delay</a>
</div>
{% endhighlight %}

<div class="result" id="result-845">
  <div>
    <p>Hover the grey area</p>
    <a>Without any delay</a>
    <a class="with-delay">With a second delay</a>
  </div>
</div>

<style type="text/css">
#result-841{ padding: 1rem;}
#result-841 a{ background: lightgrey; color: grey; margin-right: 10px; padding: 5px 10px; transition: none;}
#result-841 a:hover{ background: yellow; color: red;}
#result-841 .with-transition{ transition: 1s}
#result-842{ padding: 1rem;}
#result-842 a{ background: lightgrey; color: grey; margin-right: 10px; padding: 5px 10px; transition: none;}
#result-842 a:hover{ background: yellow; color: green;}
#result-842 .with-fast-transition{ transition: 0.5s;}
#result-842 .with-slow-transition{ transition: 3s;}
#result-843{ padding: 1rem;}
#result-843 a{ background: lightgrey; color: grey; margin-right: 10px; padding: 5px 10px; transition: none;}
#result-843 a:hover{ background: yellow; border: 5px solid blue; color: green;}
#result-843 .with-background-transition{ transition: 2s; transition-property: background;}
#result-843 .with-all-transition{ transition: 2s;}
#result-844{ padding-bottom: 1rem;}
#result-844 div{ background: crimson; height: 20px; left: 0; margin-top: -1rem; position: relative; transition: 1s; width: 20px;}
#result-844:hover div{ left: 200px;}
#result-844 p{ color: grey;}
#result-844 p strong{ font-weight: bold;}
#result-844 .ease{ transition-timing-function: ease;} /* Default behavior */
#result-844 .linear{ transition-timing-function: linear;} /* Constant speed */
#result-844 .ease-in{ transition-timing-function: ease-in;}
#result-844 .ease-out{ transition-timing-function: ease-out;}
#result-844 .ease-in-out{ transition-timing-function: ease-in-out;}
#result-844 p:nth-child(1) strong{ color: crimson;}
#result-844 div:nth-child(2){ background: crimson;}
#result-844 p:nth-child(3) strong{ color: midnightblue;}
#result-844 div:nth-child(4){ background: midnightblue;}
#result-844 p:nth-child(5) strong{ color: mediumseagreen;}
#result-844 div:nth-child(6){ background: mediumseagreen;}
#result-844 p:nth-child(7) strong{ color: orangered;}
#result-844 div:nth-child(8){ background: orangered;}
#result-844 p:nth-child(9) strong{ color: darkviolet;}
#result-844 div:nth-child(10){ background: darkviolet;}
#result-845{ padding: 1rem;}
#result-845 div{ background: lightgrey; padding: 1rem; width: 400px;}
#result-845 div p{ color: grey; margin-top: 0;}
#result-845 a{ background: blue; color: white; padding: 5px 10px; text-decoration: none; transition: all 1s;}
#result-845 div:hover a{ background: red;}
#result-845 a.with-delay{ transition-delay: 1s;}
</style>
