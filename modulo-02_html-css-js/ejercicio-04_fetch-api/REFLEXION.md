# REFLEXION — Ejercicio 2.4: Fetch API y Programación Asíncrona

> **Instrucciones:** Completá este archivo DESPUÉS de terminar tu solución. Escribí con tus propias palabras.  
> Tiempo esperado: 30–40 minutos.

---

## Sección 1 — Explicación de mi solución

*Describí en 200–300 palabras cómo funciona tu aplicación. Explicá el flujo completo: qué pasa desde que el usuario abre la página hasta que ve los personajes. Incluí cómo manejaste los estados (cargando, error, éxito).*

> ✏️ **Tu respuesta aquí:**

---

## Sección 2 — Preguntas conceptuales

### 2.1 — ¿Qué significa que JavaScript sea "single-threaded"? ¿Cómo puede entonces hacer operaciones asíncronas sin "congelarse"?

*Pista: investigá sobre el Event Loop*

> ✏️ **Tu respuesta:**

---

### 2.2 — Explicá la diferencia entre estas tres formas de manejar asincronismo. ¿Cuándo usarías cada una?

```js
// Forma 1: Callbacks
fetch(url, function(data) { ... })

// Forma 2: Promises
fetch(url).then(data => ...).catch(err => ...)

// Forma 3: async/await
const data = await fetch(url)
```

> ✏️ **Tu respuesta:**

---

### 2.3 — Tu función de fetch tiene un `try/catch`. ¿Qué tipos de errores puede atrapar? ¿Hay algún error de la Fetch API que `try/catch` NO atrapa por defecto? (Pista: ¿qué pasa con las respuestas HTTP 404 o 500?)

> ✏️ **Tu respuesta:**

---

### 2.4 — Implementaste debounce en la búsqueda. Explicá con tus palabras qué es el debounce, por qué es necesario aquí, y cuál es la diferencia con "throttle".

> ✏️ **Tu respuesta:**

---

### 2.5 — Analizá este código y explicá qué problema tiene. ¿Cómo lo resolverías?

```js
async function cargarDatos() {
  const personajes = await fetch('/api/characters').then(r => r.json());
  const episodios = await fetch('/api/episodes').then(r => r.json());
  const ubicaciones = await fetch('/api/locations').then(r => r.json());
  
  mostrarDatos(personajes, episodios, ubicaciones);
}
```

> ✏️ **Tu respuesta:**

---

### 2.6 — CORS: tu aplicación hace un fetch desde `localhost:5500` a `rickandmortyapi.com`. ¿Por qué funciona? ¿Qué es CORS y en qué situación habrías tenido un error de CORS?

> ✏️ **Tu respuesta:**

---

## Sección 3 — Decisiones técnicas

### 3.1 — ¿Cómo implementaste el debounce? Pegá el fragmento de código y explicá cada línea.

```js
// Pegá tu implementación de debounce aquí
```

> ✏️ **Explicación línea por línea:**

---

### 3.2 — ¿Cómo manejaste el estado de "cargando" en la UI? ¿Usaste variables de estado, clases CSS, o algún otro mecanismo?

> ✏️ **Tu respuesta:**

---

### 3.3 — Si tuvieras que agregar un caché simple (no volver a hacer fetch si ya tenés los datos de esa página), ¿cómo lo implementarías? No tenés que hacerlo, solo describí la estrategia.

> ✏️ **Tu respuesta:**

---

## Sección 4 — Lo que salió mal (y cómo lo resolví)

*Describí al menos un bug o problema que encontraste durante el desarrollo y cómo lo debuggeaste y resolviste. Si todo fue perfecto a la primera, eso es sospechoso 🙂*

> ✏️ **Tu respuesta:**

---

## Sección 5 — Declaración de uso de IA

```
[ ] Resolví el ejercicio completamente sin ayuda de IA
[ ] Usé IA para entender algún concepto, pero escribí el código yo
[ ] Usé IA para generar un borrador que luego modifiqué y entendí
[ ] Usé IA extensamente y completé la reflexión para entender lo que hice
```

*Si usaste IA: ¿qué parte fue más difícil de entender aunque la IA te la haya generado?*

> ✏️ **Tu respuesta:**

---

## Sección 6 — Autoevaluación

En una escala del 1 al 5, ¿cuánto entendés ahora la programación asíncrona en JavaScript?

```
[ ] 1 — Muy poco
[ ] 2 — Lo básico
[ ] 3 — Lo entiendo bien
[ ] 4 — Puedo explicárselo a otro
[ ] 5 — Podría dar una clase sobre esto
```

*¿Qué harías diferente si empezaras este ejercicio de nuevo?*

> ✏️ **Tu respuesta:**
