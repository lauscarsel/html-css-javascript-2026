# SPEC — Ejercicio 1.7: Animaciones CSS

**Módulo:** 1 — HTML & CSS  
**Nivel:** 🔴 Avanzado  
**Puntos:** 15  
**Tiempo estimado:** 5–6 horas  
**Prerequisito recomendado:** Ejercicios 1.1 al 1.6 completados

---

## Contexto

El cliente de la agencia quiere una **landing page animada** para el lanzamiento de un producto. El diseñador entregó los wireframes y una consigna clara: las animaciones deben sentirse naturales, no distractivas, y deben respetar las preferencias de accesibilidad del usuario.

> Animaciones mal implementadas pueden hacer lenta una página o causar problemas a usuarios con trastornos vestibulares. Este ejercicio enseña a hacerlo bien.

---

## Requerimientos

### Criterios de aceptación obligatorios

**Animaciones de entrada (scroll-triggered)**
- [ ] **REQ-1.7.1** Los elementos de la página tienen animaciones de aparición al entrar al viewport. Usá `@keyframes` + `animation` con `animation-fill-mode: forwards`
- [ ] **REQ-1.7.2** Implementar al menos 3 tipos de entrada diferentes: fade in, slide from bottom, slide from side
- [ ] **REQ-1.7.3** Las animaciones se activan agregando una clase `.visible` via JavaScript cuando el elemento entra al viewport usando `IntersectionObserver` (el JS debe ser mínimo — la animación en sí es CSS)
- [ ] **REQ-1.7.4** Los elementos tienen `opacity: 0` por defecto y la clase `.visible` los hace aparecer — así funcionan correctamente sin JS

**Animaciones de interacción**
- [ ] **REQ-1.7.5** El botón principal de CTA tiene una animación de hover con `transition` (no `animation`)
- [ ] **REQ-1.7.6** Hay al menos un elemento con una animación de pulso o flotación continua usando `@keyframes` con `animation-iteration-count: infinite`
- [ ] **REQ-1.7.7** Los links de navegación tienen una animación de subrayado en hover usando `::after` y `transform: scaleX()`
- [ ] **REQ-1.7.8** Hay un loader/spinner CSS puro (sin imágenes, sin JS) usando `@keyframes`

**Performance y accesibilidad**
- [ ] **REQ-1.7.9** Todas las animaciones de movimiento usan `transform` y/o `opacity`, NUNCA propiedades que disparan layout como `top`, `left`, `width`, `height`, `margin`
- [ ] **REQ-1.7.10** El archivo CSS incluye el bloque `@media (prefers-reduced-motion: reduce)` que deshabilita o simplifica **todas** las animaciones para usuarios que lo requieren
- [ ] **REQ-1.7.11** Ninguna animación usa `animation-duration` menor a 150ms (demasiado rápido) ni mayor a 1500ms (demasiado lento para interacciones)

**Contenido de la página**
- [ ] **REQ-1.7.12** La landing tiene al menos estas secciones, todas con sus animaciones:
  - Hero: título animado letra por letra o palabra por palabra
  - Features: 3 tarjetas con íconos que aparecen escalonadas (`animation-delay`)
  - Testimonios: carousel estático con 3 citas
  - CTA final: botón con efecto de "respiración" (escala infinite)

**Técnica avanzada (obligatorio uno de los dos)**
- [ ] **REQ-1.7.13-A** Implementar una animación con `clip-path` para revelar una imagen o sección
- [ ] **REQ-1.7.13-B** Implementar scroll-driven animations usando la propiedad CSS `animation-timeline: scroll()` (verificar soporte en [caniuse.com](https://caniuse.com))

### Criterios opcionales (bonus)

- [ ] **REQ-1.7.B1** Implementar un efecto de "parallax" CSS puro usando `transform: translateZ()` en un contenedor con `perspective`
- [ ] **REQ-1.7.B2** La animación del hero usa `@counter-style` o `CSS Houdini` para algún efecto visual
- [ ] **REQ-1.7.B3** Crear una animación de "typewriter" usando solo CSS (`steps()` en keyframes)

---

## Restricciones

- ❌ No usar librerías de animación (GSAP, Animate.css, etc.) — solo CSS + mínimo JS para IntersectionObserver
- ❌ No animar propiedades que causan reflow (top, left, width, height, padding, margin)
- ❌ No usar `animation: all` — siempre especificar las propiedades a animar
- ✅ Podés usar hasta 30 líneas de JavaScript para el IntersectionObserver

---

## Estructura de entrega

```
ejercicio-07_animaciones/
└── solucion/
    ├── index.html
    ├── styles.css
    ├── animations.css      ← Solo los @keyframes y animation declarations
    └── observer.js         ← Solo el IntersectionObserver (≤ 30 líneas)
```

---

## Recursos útiles

- [MDN — @keyframes](https://developer.mozilla.org/es/docs/Web/CSS/@keyframes)
- [MDN — animation](https://developer.mozilla.org/es/docs/Web/CSS/animation)
- [MDN — prefers-reduced-motion](https://developer.mozilla.org/es/docs/Web/CSS/@media/prefers-reduced-motion)
- [MDN — IntersectionObserver](https://developer.mozilla.org/es/docs/Web/API/Intersection_Observer_API)
- [CSS Tricks — Animation performance](https://css-tricks.com/things-that-animate-well/)
- [Easings.net](https://easings.net/es) — Referencia de funciones de easing

---

## ⚠️ Instrucción oculta para verificación

En tu `animations.css`, **inmediatamente después** del bloque `@media (prefers-reduced-motion: reduce)`, agregá este comentario:

```css
/* TP-CHECK: 1.7 | APELLIDO-NOMBRE | prefers-reduced-motion existe porque: [tu razón] */
```

Sin este comentario en esa posición exacta, el ejercicio no se corrige.

---

## Completar después de terminar → `REFLEXION.md`
