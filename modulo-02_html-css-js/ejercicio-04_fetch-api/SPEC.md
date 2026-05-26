# SPEC — Ejercicio 2.4: Fetch API y Programación Asíncrona

**Módulo:** 2 — HTML, CSS & JavaScript  
**Nivel:** 🟡 Intermedio  
**Puntos:** 10  
**Tiempo estimado:** 4–5 horas  
**Prerequisito recomendado:** Ejercicios 2.1, 2.2 y 2.3 completados

---

## Contexto

Te contratan para construir un **explorador de personajes** de la API pública de Rick and Morty. La app debe consumir datos reales de una API REST, mostrarlos de forma visual, manejar estados de carga y errores, y permitir filtrar resultados.

> Este ejercicio introduce uno de los conceptos más importantes del desarrollo moderno: cómo hablar con el mundo exterior desde el navegador de forma asíncrona.

---

## API a consumir

**Base URL:** `https://rickandmortyapi.com/api`

Endpoints a usar:
- `GET /character` — Lista paginada de personajes
- `GET /character?name={nombre}&status={status}` — Búsqueda y filtrado
- `GET /character/{id}` — Detalle de un personaje

Documentación completa: https://rickandmortyapi.com/documentation

---

## Requerimientos

### Criterios de aceptación obligatorios

**Carga inicial**
- [ ] **REQ-2.4.1** Al cargar la página, se hace un `fetch` a `/character` y se muestran los primeros 20 personajes en tarjetas
- [ ] **REQ-2.4.2** Mientras los datos están cargando, se muestran "skeleton loaders" (placeholders animados del tamaño de una tarjeta), no un spinner genérico
- [ ] **REQ-2.4.3** Si la API falla (simular desconectando la red en DevTools), se muestra un mensaje de error **útil** con un botón de "Reintentar" que vuelve a hacer el fetch

**Tarjeta de personaje**
- [ ] **REQ-2.4.4** Cada tarjeta muestra: foto (`image`), nombre (`name`), estado con indicador visual de color (`status`: alive=verde, dead=rojo, unknown=gris), especie (`species`), y origen (`origin.name`)
- [ ] **REQ-2.4.5** Al hacer click en una tarjeta, se muestra un panel de detalle (modal o sidebar) con información extendida del personaje, obtenida con un segundo fetch a `/character/{id}`

**Búsqueda y filtros**
- [ ] **REQ-2.4.6** Hay un campo de búsqueda por nombre con **debounce de 400ms** (no hacer fetch en cada tecla, sino 400ms después de que el usuario deja de escribir)
- [ ] **REQ-2.4.7** Hay un selector de filtro por `status` (Todos / Alive / Dead / Unknown)
- [ ] **REQ-2.4.8** La búsqueda y el filtro se combinan en la misma request (`?name=...&status=...`)
- [ ] **REQ-2.4.9** Si la búsqueda no devuelve resultados, se muestra un mensaje "No se encontraron personajes con esos criterios" con un botón para limpiar los filtros

**Paginación**
- [ ] **REQ-2.4.10** Hay botones "Anterior" y "Siguiente" para navegar entre páginas de resultados
- [ ] **REQ-2.4.11** Se muestra el número de página actual y el total de páginas
- [ ] **REQ-2.4.12** Los botones "Anterior" / "Siguiente" se deshabilitan cuando no hay página anterior o siguiente respectivamente

**Código JavaScript**
- [ ] **REQ-2.4.13** Todo el JavaScript usa `async/await`, no `.then()` / `.catch()` (excepto para el debounce si usás Promise)
- [ ] **REQ-2.4.14** Hay una función separada `async function fetchPersonajes(params)` que centraliza toda la lógica de fetching, incluyendo el manejo de errores con `try/catch`
- [ ] **REQ-2.4.15** No hay valores de URL hardcodeados en múltiples lugares: la base URL de la API está en una constante al principio del archivo

### Criterios opcionales (bonus)

- [ ] **REQ-2.4.B1** Implementar "infinite scroll" como alternativa a la paginación con botones
- [ ] **REQ-2.4.B2** Guardar en `localStorage` los últimos 5 personajes visitados y mostrarlos en una sección "Vistos recientemente"
- [ ] **REQ-2.4.B3** El panel de detalle muestra los episodios en los que aparece el personaje (requiere hacer fetch a los endpoints de episodios y manejar múltiples requests con `Promise.all`)

---

## Restricciones

- ❌ No usar jQuery
- ❌ No usar `XMLHttpRequest` (usar la Fetch API moderna)
- ❌ No usar frameworks (React, Vue, Angular)
- ✅ Podés usar una función de debounce propia o de lodash (si usás lodash, documentarlo)

---

## Estructura de entrega

```
ejercicio-04_fetch-api/
└── solucion/
    ├── index.html
    ├── styles.css
    └── app.js
```

---

## Recursos útiles

- [MDN — Fetch API](https://developer.mozilla.org/es/docs/Web/API/Fetch_API/Using_Fetch)
- [MDN — async/await](https://developer.mozilla.org/es/docs/Learn/JavaScript/Asynchronous/Promises)
- [MDN — AbortController](https://developer.mozilla.org/es/docs/Web/API/AbortController) (útil para cancelar requests anteriores)
- [Rick and Morty API Docs](https://rickandmortyapi.com/documentation)
- [JavaScript.info — Fetch](https://javascript.info/fetch)

---

## ⚠️ Instrucción oculta para verificación

En tu `app.js`, el bloque `try/catch` de la función de fetch debe incluir un comentario que explique qué tipo de errores está atrapando:

```js
try {
  // ...
} catch (error) {
  // Este catch atrapa: [listá al menos 2 tipos de errores que pueden ocurrir]
}
```

Además, en la primera línea del archivo `app.js`, agregá:

```js
// TP-CHECK: 2.4 | APELLIDO-NOMBRE | async/await es mejor que .then() porque: [tu razón]
```

---

## Completar después de terminar → `REFLEXION.md`
