# SPEC — Ejercicio 1.6: CSS Custom Properties y Sistema de Temas

**Módulo:** 1 — HTML & CSS  
**Nivel:** 🔴 Avanzado  
**Puntos:** 15  
**Tiempo estimado:** 5–7 horas  
**Prerequisito recomendado:** Ejercicios 1.1 al 1.5 completados

---

## Contexto

El cliente de la agencia quiere que su sitio soporte **modo oscuro y modo claro** con un toggle manual. Además, quiere que en el futuro sea fácil cambiar toda la paleta de colores sin tocar cientos de líneas de CSS. Tu tarea es construir un **sistema de diseño** basado en CSS Custom Properties que resuelva esto.

> Este ejercicio simula un requerimiento real de producción: el código debe ser mantenible por otros desarrolladores.

---

## Requerimientos

### Criterios de aceptación obligatorios

**Sistema de tokens de diseño**
- [ ] **REQ-1.6.1** Definir en `:root` un sistema completo de variables CSS que incluya al menos:
  - 5 colores semánticos: `--color-primario`, `--color-secundario`, `--color-fondo`, `--color-superficie`, `--color-texto`, `--color-texto-suave`, `--color-borde`, `--color-acento`
  - 5 tamaños de fuente usando escala tipográfica: `--fs-xs`, `--fs-sm`, `--fs-base`, `--fs-lg`, `--fs-xl`, `--fs-2xl`
  - 4 valores de espaciado: `--sp-xs`, `--sp-sm`, `--sp-md`, `--sp-lg`, `--sp-xl`
  - 3 valores de `border-radius`: `--radius-sm`, `--radius-md`, `--radius-lg`
  - 2 sombras: `--shadow-sm`, `--shadow-md`
  - 2 transiciones: `--transition-rapida`, `--transition-normal`

- [ ] **REQ-1.6.2** **Ningún valor hardcodeado**: todo color, tamaño de fuente, espaciado y sombra en el CSS debe referenciar una variable, no un valor directo. (Excepción: los propios valores definidos en `:root`)

**Sistema de temas**
- [ ] **REQ-1.6.3** Implementar tema oscuro: cuando el `<html>` tenga el atributo `data-theme="dark"`, los valores de las variables de color deben cambiar automáticamente (sin tocar otros estilos)
- [ ] **REQ-1.6.4** El sistema también respeta la preferencia del sistema operativo usando `@media (prefers-color-scheme: dark)`
- [ ] **REQ-1.6.5** Un botón de toggle de tema en el header cambia el atributo `data-theme` del `<html>` usando JavaScript (mínimo JS necesario)
- [ ] **REQ-1.6.6** La preferencia del usuario se guarda en `localStorage` y se aplica al cargar la página (sin flash de tema incorrecto)

**Demostración del sistema**
- [ ] **REQ-1.6.7** La página de demostración debe incluir al menos estos componentes, todos construidos usando las variables:
  - Tipografía: todos los niveles de heading (h1–h4), párrafo, texto pequeño
  - Colores: paleta visual de todos los colores del sistema
  - Botones: primario, secundario, outlined, deshabilitado
  - Tarjeta (card) con imagen, título, texto y botón
  - Input, textarea, select con estados: default, focus, error, disabled
  - Badge/Tag en al menos 3 variantes de color
  - Un alert/notificación en variantes: info, success, warning, error

**Calidad del sistema**
- [ ] **REQ-1.6.8** Las transiciones de cambio de tema son suaves (CSS `transition` en las propiedades de color del `body` o `html`)
- [ ] **REQ-1.6.9** El contraste de colores cumple WCAG AA mínimo (ratio 4.5:1 para texto normal). Podés verificarlo en [coolors.co/contrast-checker](https://coolors.co/contrast-checker)
- [ ] **REQ-1.6.10** El CSS está organizado con comentarios de sección que indiquen dónde están los tokens, la tipografía, los componentes, etc.

### Criterios opcionales (bonus)

- [ ] **REQ-1.6.B1** Implementar un tercer tema ("sepia" o un tema de color personalizado) accesible desde el toggle
- [ ] **REQ-1.6.B2** El sistema de tipografía usa `clamp()` para escala fluida (sin media queries para el tamaño de fuente)
- [ ] **REQ-1.6.B3** Documentar el sistema de diseño en un `DESIGN_SYSTEM.md` dentro de la carpeta de solución, describiendo cada token y cuándo usarlo

---

## Restricciones

- ❌ No usar preprocesadores CSS (SASS, LESS) — solo CSS puro
- ❌ No usar librerías de UI
- ✅ El JavaScript para el toggle debe ser mínimo (menos de 20 líneas), el peso del sistema está en CSS

---

## Estructura de entrega

```
ejercicio-06_variables-css/
└── solucion/
    ├── index.html
    ├── tokens.css          ← Solo variables CSS (los design tokens)
    ├── base.css            ← Estilos base (reset, tipografía, etc.)
    ├── components.css      ← Estilos de cada componente
    └── theme.js            ← Lógica de toggle de tema
```

La separación en múltiples archivos es **obligatoria** — es parte del ejercicio.

---

## Recursos útiles

- [MDN — Using CSS custom properties](https://developer.mozilla.org/es/docs/Web/CSS/Using_CSS_custom_properties)
- [MDN — prefers-color-scheme](https://developer.mozilla.org/es/docs/Web/CSS/@media/prefers-color-scheme)
- [Smashing Magazine — A Complete Guide To Dark Mode](https://www.smashingmagazine.com/2020/04/dark-mode-complete-guide/)
- [WCAG Contrast Checker](https://coolors.co/contrast-checker)
- [Open Props](https://open-props.style/) — Referencia de sistema de tokens (para inspiración, no para copiar)

---

## ⚠️ Instrucción oculta para verificación

En tu archivo `tokens.css`, la **primera línea** debe ser:

```css
/* TP-CHECK: 1.6 | APELLIDO-NOMBRE | sin variables CSS este ejercicio sería imposible porque: [tu razón] */
```

Además, en el `theme.js`, la última línea del archivo debe ser un comentario explicando en una oración qué hace `localStorage`:

```js
// localStorage sirve para: [tu explicación]
```

---

## Completar después de terminar → `REFLEXION.md`
