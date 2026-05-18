# Parte 2: Comunicación con el servidor

Ejercicios correspondientes a la [Parte 2](https://fullstackopen.com/es/part2) del curso Full Stack Open.

## Objetivo

Aprender a renderizar colecciones de datos con `map` y `reduce`, manejar formularios en React, consumir APIs externas con `axios` y `useEffect`, y realizar operaciones CRUD completas contra un servidor backend.

---

## Ejercicios

### [courseinfo](./courseinfo/)
**Ejercicios 2.1 – 2.5**

Continuación de la aplicación de información de cursos de la Parte 1, ahora refactorizada para soportar múltiples cursos.

- Renderizado de listas con `map` y atributo `key`
- Cálculo del total de ejercicios con `reduce`
- Componente `Course` separado en su propio módulo (`components/Course.jsx`)
- La app funciona con cualquier número de partes por curso

---

### [phonebook](./phonebook/)
**Ejercicios 2.6 – 2.17**

Agenda telefónica completa con operaciones CRUD contra un servidor simulado con `json-server`.

- Formulario controlado para agregar contactos (nombre y número)
- Filtro en tiempo real de contactos por nombre
- Prevención de duplicados con confirmación para actualizar número existente
- Eliminación de contactos con confirmación
- Comunicación con servidor via `axios` (GET, POST, PUT, DELETE)
- `useEffect` para cargar datos iniciales desde el servidor
- Componente `Notification` para mensajes de éxito y error con estilos diferenciados
- Separación en componentes: `Filter`, `PersonForm`, `Persons`
- Manejo de errores cuando un contacto ya fue eliminado del servidor

---

### [countries](./countries/)
**Ejercicios 2.18 – 2.20**

Buscador de países que consume la REST Countries API y muestra información detallada incluyendo el clima actual.

- Búsqueda dinámica con filtrado en tiempo real
- Renderizado condicional según número de resultados (>10 / lista / detalle único)
- Botón "show" para ver detalles de un país específico desde la lista
- Datos del país: capital, área, idiomas, bandera
- Integración con OpenWeatherMap API para mostrar temperatura, ícono y viento del clima actual de la capital
- Manejo de efectos secundarios con `useEffect` para fetch a APIs externas

---

## Lo aprendido

Esta parte amplió significativamente el alcance de las aplicaciones React al conectarlas con el mundo exterior. El uso de `useEffect` para sincronizar la UI con fuentes de datos externas fue el concepto más importante: entender que los efectos se ejecutan después del renderizado y cómo manejar sus dependencias correctamente.

El phonebook fue el ejercicio más completo: combinar formularios controlados, validaciones, comunicación HTTP y manejo de errores en una sola aplicación obligó a pensar en la arquitectura del código y en cómo separar responsabilidades en componentes y servicios (`services/persons.js`).

En countries, el reto fue coordinar múltiples llamadas a APIs distintas (REST Countries y OpenWeatherMap) y manejar el renderizado condicional de forma clara y limpia.

---

## Desafíos técnicos superados

- Entender el flujo asíncrono de `axios` con promesas y `.then()`
- Manejar el caso donde un recurso fue eliminado del servidor mientras el usuario interactuaba con él (error 404 en PUT)
- Coordinar múltiples `useEffect` en el mismo componente sin generar efectos indeseados
- Usar `reduce` correctamente para acumular valores desde un array de objetos
- Estructurar el proyecto en módulos (`services/`, `components/`) para mantener el código organizado