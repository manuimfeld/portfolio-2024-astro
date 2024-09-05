---
layout: '../../layouts/BlogPostLayout.astro'
title: '¿Qué es un Closure en JavaScript? Explicado con ejemplos'
date: '14/01/2024'
img: 'https://midu.dev/images/tags/javascript.png'
tag: javascript
---

¡Hola y bienvenidos a otro post del blog! 🚀

En esta ocasión, quiero hablarles sobre un concepto fundamental en JavaScript: **los closures**. Si alguna vez has tenido dudas sobre cómo funcionan o para qué sirven, este post es para ti. Vamos a desglosar este concepto con explicaciones sencillas y algunos ejemplos prácticos.

## 1. ¿Qué es un closure?

Un closure es una función que recuerda el entorno (o el scope) en el que fue creada, incluso después de que ese entorno haya terminado de ejecutarse. En otras palabras, un closure es una función que puede acceder a variables de su contexto exterior, aunque esa función se ejecute fuera de dicho contexto.

# Ejemplo básico:

```javascript
function crearSaludo(saludo) {
  return function (nombre) {
    return `${saludo}, ${nombre}!`;
  };
}

const saludarEnEspañol = crearSaludo('Hola');
console.log(saludarEnEspañol('Manuel')); // Output: "Hola, Manuel!"
```

En este ejemplo, la función `crearSaludo` devuelve otra función. Esta función "recuerda" la variable `saludo` que estaba en su contexto cuando fue creada, incluso después de que `crearSaludo` haya terminado de ejecutarse. Esto es un closure.

## 2. ¿Cómo funcionan los closures?

Para entender mejor, pensemos en cómo maneja JavaScript el scope de las variables. Cada vez que defines una función, ésta crea un nuevo contexto o "alcance" (scope). Un closure se forma cuando una función interna accede a variables definidas en su función externa.

# Ejemplo más avanzado

```javascript
function contador() {
  let cuenta = 0;

  return function () {
    cuenta += 1;
    return cuenta;
  };
}

const incrementar = contador();
console.log(incrementar()); // Output: 1
console.log(incrementar()); // Output: 2
console.log(incrementar()); // Output: 3
```

En este caso, la variable `cuenta` se mantiene "viva" y accesible para la función que se devuelve, gracias al closure. Cada vez que ejecutas `incrementar`, el valor de `cuenta` se actualiza, y esto es posible porque la función interna sigue recordando el entorno en el que fue creada.

## 3. ¿Por qué son útiles los closures?

Los closures son extremadamente útiles en muchas situaciones, especialmente cuando quieres que una función "recuerde" un estado entre ejecuciones sin necesidad de utilizar variables globales. Aquí algunos casos de uso comunes:

- **Funciones privadas**: Los closures permiten crear funciones que acceden a variables privadas, evitando la manipulación directa desde fuera.
- **Callbacks y eventos**: Cuando se trabajan con funciones asíncronas (como callbacks o manejadores de eventos), los closures permiten que las funciones conserven el acceso a las variables del momento en que fueron creadas.

# Ejemplo práctico con eventos:

```javascript
function asignarEvento(elemento, mensaje) {
  elemento.addEventListener('click', function () {
    alert(mensaje);
  });
}

const boton = document.getElementById('miBoton');
asignarEvento(boton, '¡Has hecho clic en el botón!');
```

En este ejemplo, la función que maneja el evento click es un closure que recuerda la variable `mensaje` y la muestra cuando el botón es clickeado.

## 4. Conclusión

Los closures son una poderosa característica en JavaScript que permite a las funciones recordar y acceder a su contexto exterior, incluso después de que la función externa haya terminado. Esta capacidad puede ser aprovechada para manejar datos de manera elegante, sin necesidad de depender de variables globales.

Si quieres mejorar como desarrollador JavaScript, es fundamental que entiendas bien los closures y cómo usarlos. ¡Experimenta con ellos en tu código y notarás el impacto!
