# SPEC — Ejercicio 2.6: Módulos ES6 y Patrones de Diseño

**Módulo:** 2 — HTML, CSS & JavaScript  
**Nivel:** 🔴 Avanzado  
**Puntos:** 15  
**Tiempo estimado:** 6–8 horas  
**Prerequisito recomendado:** Ejercicios 2.1 al 2.5 completados

---

## Contexto

Llevás el ejercicio 2.5 (la app con localStorage) al siguiente nivel. El código quedó en un solo archivo JS de 200+ líneas y es difícil de mantener. Tu tarea es **refactorizarlo** usando módulos ES6 y aplicar patrones de diseño que hacen el código escalable.

> Este ejercicio simula algo que pasa en todos los equipos de desarrollo: código que creció sin estructura y necesita ser reorganizado sin romper la funcionalidad.

---

## Punto de partida

Tomá tu solución del ejercicio 2.5 (o la provista en `starter/`) como base. La funcionalidad no debe cambiar — lo que cambia es la arquitectura del código.

---

## Requerimientos

### Criterios de aceptación obligatorios

**Módulos ES6**
- [ ] **REQ-2.6.1** La aplicación está dividida en módulos con `import` / `export`. No puede existir código de lógica en el HTML (ni `<script>` inline ni archivos JS acoplados al HTML)
- [ ] **REQ-2.6.2** El `index.html` carga un único archivo JS de entrada (`main.js`) con `<script type="module">`
- [ ] **REQ-2.6.3** La aplicación tiene al menos esta estructura de módulos:

```
solucion/
├── index.html
├── styles.css
├── main.js                     ← Entry point, solo inicialización
└── src/
    ├── store/
    │   └── store.js            ← Estado y persistencia
    ├── services/
    │   └── storageService.js   ← Abstracción de localStorage
    ├── components/
    │   ├── taskList.js         ← Renderizado de lista
    │   ├── taskForm.js         ← Lógica del formulario
    │   └── filters.js          ← Lógica de filtros
    └── utils/
        ├── validators.js       ← Funciones de validación puras
        └── helpers.js          ← Funciones utilitarias puras
```

**Patrón Observer / Event Emitter**
- [ ] **REQ-2.6.4** Implementar una clase `EventEmitter` propia (sin librerías) con métodos `on(evento, callback)`, `off(evento, callback)`, y `emit(evento, datos)`
- [ ] **REQ-2.6.5** El Store usa el EventEmitter: cuando el estado cambia, emite un evento `'change'` y los componentes que escuchan se actualizan solos
- [ ] **REQ-2.6.6** No puede haber comunicación directa entre componentes (taskForm no llama a taskList directamente — ambos hablan a través del Store)

**Patrón Singleton para el Store**
- [ ] **REQ-2.6.7** El Store es un Singleton: solo puede existir una instancia. Implementar usando un módulo ES6 (el módulo en sí es un singleton) o usando el patrón explícito con instancia privada

**Funciones puras en utils**
- [ ] **REQ-2.6.8** Las funciones en `validators.js` y `helpers.js` son **funciones puras**: dado el mismo input, siempre devuelven el mismo output, sin efectos secundarios
- [ ] **REQ-2.6.9** Todas las funciones en `utils/` están testeadas en un archivo `utils.test.js` usando `console.assert()` — mínimo 3 tests por función

**Inmutabilidad del estado**
- [ ] **REQ-2.6.10** El estado del Store nunca se muta directamente. Se usan métodos del Store para actualizar: `store.agregarTarea(tarea)`, `store.completarTarea(id)`, etc. Cada actualización crea un nuevo objeto/array, no modifica el existente
- [ ] **REQ-2.6.11** El Store expone el estado solo a través de un getter que devuelve una copia (no la referencia original): `get state() { return { ...this.#state }; }`

**JavaScript moderno obligatorio**
- [ ] **REQ-2.6.12** Usar al menos: destructuring, spread operator, optional chaining (`?.`), nullish coalescing (`??`), y al menos un uso de `Array.prototype.reduce()`
- [ ] **REQ-2.6.13** Usar private class fields (`#`) para datos privados en al menos una clase

### Criterios opcionales (bonus)

- [ ] **REQ-2.6.B1** Implementar el patrón **Command** para las acciones del usuario: cada acción (agregar, completar, eliminar) es un objeto comando, lo que permite implementar Undo/Redo
- [ ] **REQ-2.6.B2** Agregar un middleware al Store (al estilo Redux): una función que se ejecuta antes de cada cambio de estado y puede loguear, validar, o transformar la acción
- [ ] **REQ-2.6.B3** Publicar el módulo `EventEmitter` como un módulo ES independiente y documentarlo con JSDoc completo

---

## Restricciones

- ❌ No usar frameworks (React, Vue, etc.)
- ❌ No usar bundlers (Webpack, Vite, etc.) — solo módulos ES nativos del navegador
- ❌ No usar librerías de gestión de estado (Redux, Zustand, etc.)
- ❌ No usar `var` — solo `const` y `let`
- ✅ Para servir la app localmente (los módulos requieren un servidor), usar `npx serve .` o la extensión Live Server de VS Code

---

## Recursos útiles

- [MDN — JavaScript modules](https://developer.mozilla.org/es/docs/Web/JavaScript/Guide/Modules)
- [MDN — Private class features](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Classes/Private_class_fields)
- [Refactoring Guru — Observer Pattern](https://refactoring.guru/es/design-patterns/observer)
- [Refactoring Guru — Singleton Pattern](https://refactoring.guru/es/design-patterns/singleton)
- [JavaScript.info — Modules](https://javascript.info/modules)

---

## ⚠️ Instrucción oculta para verificación

En tu archivo `src/store/store.js`, la primera línea de código (después de imports) debe ser:

```js
// TP-CHECK: 2.6 | APELLIDO-NOMBRE
// El patrón Observer resuelve el problema de: [describí el problema que resuelve]
// El patrón Singleton garantiza: [describí qué garantiza]
```

En `utils/validators.js`, antes de cada función pura, debe haber un comentario indicando:
```js
// PURA: sí — porque [razón] / no depende de [qué]
```

---

## Completar después de terminar → `REFLEXION.md`
