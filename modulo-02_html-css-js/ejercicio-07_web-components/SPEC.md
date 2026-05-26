# SPEC — Ejercicio 2.7: Web Components

**Módulo:** 2 — HTML, CSS & JavaScript  
**Nivel:** ⚫ Experto  
**Puntos:** 20  
**Tiempo estimado:** 8–12 horas  
**Prerequisito recomendado:** Todos los ejercicios anteriores completados

---

## Contexto

Liderás el equipo de frontend de una empresa mediana. El problema que tienen: usan React en un proyecto, Vue en otro, y HTML puro en el sitio de marketing. Cada equipo re-implementa los mismos componentes (botones, modales, tooltips) de forma inconsistente.

Tu tarea es construir una **librería de Web Components** que funcione en los tres contextos sin dependencias externas. Este es un problema real que empresas como GitHub, Adobe y Google resuelven con Web Components.

> Web Components son el estándar nativo del navegador para crear elementos HTML reutilizables y encapsulados. No necesitan framework.

---

## Requerimientos

### Criterios de aceptación obligatorios

Debés construir **4 Web Components** funcionales, cada uno en su propio archivo `.js`:

---

### Componente 1: `<ui-button>`

**Archivo:** `components/ui-button.js`

**Atributos:**
- `variant`: `"primary"` | `"secondary"` | `"danger"` | `"ghost"` (default: `"primary"`)
- `size`: `"sm"` | `"md"` | `"lg"` (default: `"md"`)
- `disabled`: atributo booleano
- `loading`: atributo booleano — muestra spinner y deshabilita el click

**Comportamiento:**
- [ ] **REQ-2.7.1** Usa Shadow DOM para encapsular sus estilos
- [ ] **REQ-2.7.2** Expone un slot por defecto para el texto del botón
- [ ] **REQ-2.7.3** Cuando `loading` es `true`, el slot de texto se oculta y aparece un spinner SVG animado
- [ ] **REQ-2.7.4** Dispara un Custom Event `ui-button-click` en el `document` cuando se hace click (no solo el click nativo)
- [ ] **REQ-2.7.5** Respeta el atributo `disabled` bloqueando el evento

**Uso esperado:**
```html
<ui-button variant="primary" size="lg">Guardar cambios</ui-button>
<ui-button variant="danger" disabled>Eliminar</ui-button>
<ui-button loading>Procesando...</ui-button>
```

---

### Componente 2: `<ui-modal>`

**Archivo:** `components/ui-modal.js`

**Atributos:**
- `open`: atributo booleano — controla visibilidad
- `title`: string — título del modal
- `size`: `"sm"` | `"md"` | `"lg"` (default: `"md"`)
- `closeable`: atributo booleano — muestra botón de cierre (default: `true`)

**Slots:**
- Slot por defecto: contenido del cuerpo del modal
- Slot `footer`: acciones del modal (botones)

**Comportamiento:**
- [ ] **REQ-2.7.6** Usa Shadow DOM
- [ ] **REQ-2.7.7** Cuando `open` es `true`, el modal se muestra con un overlay de fondo
- [ ] **REQ-2.7.8** Cerrar el modal (por botón X o click en overlay) dispara el Custom Event `ui-modal-close`
- [ ] **REQ-2.7.9** El modal atrapa el foco (`focus trap`): Tab no puede salir del modal mientras está abierto
- [ ] **REQ-2.7.10** Presionar `Escape` cierra el modal

**Uso esperado:**
```html
<ui-modal title="Confirmar acción" open>
  <p>¿Estás seguro de que querés continuar?</p>
  <div slot="footer">
    <ui-button variant="ghost">Cancelar</ui-button>
    <ui-button variant="danger">Confirmar</ui-button>
  </div>
</ui-modal>
```

---

### Componente 3: `<ui-toast>`

**Archivo:** `components/ui-toast.js`

**API programática** (no se instancia en HTML, se usa desde JS):
```js
UIToast.show({ message: 'Guardado', type: 'success', duration: 3000 });
UIToast.show({ message: 'Error al conectar', type: 'error', duration: 0 }); // 0 = no se cierra solo
```

**Tipos:** `"success"` | `"error"` | `"warning"` | `"info"`

**Comportamiento:**
- [ ] **REQ-2.7.11** Los toasts aparecen en una esquina de la pantalla (configurable: top-right, bottom-right, etc.) con posición fixed
- [ ] **REQ-2.7.12** Múltiples toasts se apilan verticalmente con animación de entrada y salida
- [ ] **REQ-2.7.13** Cada toast tiene un indicador visual de progreso que muestra cuánto tiempo queda
- [ ] **REQ-2.7.14** El usuario puede cerrar manualmente cualquier toast

---

### Componente 4: `<ui-data-table>`

**Archivo:** `components/ui-data-table.js`

**Atributos:**
- `columns`: JSON string con la definición de columnas
- `sortable`: atributo booleano

**Slot:** Slot `empty` para mostrar cuando no hay datos

**API programática:**
```js
const table = document.querySelector('ui-data-table');
table.setData(arrayDeObjetos);
```

**Comportamiento:**
- [ ] **REQ-2.7.15** Renderiza una tabla `<table>` semántica dentro del Shadow DOM
- [ ] **REQ-2.7.16** Si `sortable` está presente, hacer click en el header de una columna ordena los datos (ascendente / descendente, toggle)
- [ ] **REQ-2.7.17** Dispara Custom Event `ui-table-sort` con `detail: { column, direction }` cuando se ordena
- [ ] **REQ-2.7.18** Si el array de datos está vacío, muestra el slot `empty`

**Uso esperado:**
```html
<ui-data-table
  columns='[{"key":"nombre","label":"Nombre"},{"key":"email","label":"Email"}]'
  sortable
>
  <p slot="empty">No hay resultados para mostrar</p>
</ui-data-table>

<script>
  document.querySelector('ui-data-table').setData([
    { nombre: 'Ana García', email: 'ana@email.com' },
    { nombre: 'Juan Pérez', email: 'juan@email.com' },
  ]);
</script>
```

---

### Página de demostración

- [ ] **REQ-2.7.19** Existe un `index.html` que importa los 4 componentes y hace una demo interactiva de cada uno
- [ ] **REQ-2.7.20** La demo muestra todos los estados/variantes de cada componente
- [ ] **REQ-2.7.21** La demo incluye código de ejemplo copiable para cada componente (como un showroom de componentes)

### Criterios opcionales (bonus)

- [ ] **REQ-2.7.B1** Publicar la librería como un módulo ES usando un `index.js` que exporte todos los componentes, y documentar cómo importarla
- [ ] **REQ-2.7.B2** Agregar un `<ui-tooltip>` componente con posicionamiento inteligente (que se reposiciona si no cabe en pantalla)
- [ ] **REQ-2.7.B3** Escribir al menos 10 tests usando la API nativa del navegador (`assert`) en un archivo `tests.html` que se pueda abrir en el navegador

---

## Restricciones

- ❌ No usar ningún framework (React, Vue, Angular, Svelte)
- ❌ No usar librerías externas de componentes
- ❌ Cada componente debe funcionar de forma independiente (sin depender de los otros)
- ✅ Podés usar Lit o FAST Element **solo si** completás primero una versión vanilla y lo documentás en la reflexión (sin bonus extra)

---

## Estructura de entrega

```
ejercicio-07_web-components/
└── solucion/
    ├── index.html              ← Página de demostración
    ├── components/
    │   ├── ui-button.js
    │   ├── ui-modal.js
    │   ├── ui-toast.js
    │   └── ui-data-table.js
    └── index.js                ← Exporta todos los componentes
```

---

## ⚠️ Instrucción oculta para verificación

En cada archivo de componente, la clase debe incluir un comentario JSDoc antes de la definición de la clase:

```js
/**
 * @element ui-button
 * @description [Describí en una oración para qué sirve este componente]
 * @attr {string} variant - [Describí este atributo]
 * @fires {CustomEvent} ui-button-click - [Describí cuándo se dispara]
 * TP-CHECK: 2.7 | APELLIDO-NOMBRE
 */
class UIButton extends HTMLElement { ... }
```

Sin estos JSDoc en los 4 componentes, el ejercicio no se corrige.

---

## Completar después de terminar → `REFLEXION.md`
