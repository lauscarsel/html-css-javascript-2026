# SPEC — Ejercicio 2.1: Manipulación básica del DOM

**Módulo:** 2 — HTML, CSS & JavaScript  
**Nivel:** 🟢 Novato  
**Puntos:** 5  
**Tiempo estimado:** 2–3 horas  
**Prerequisito recomendado:** Módulo 1 completado

---

## Contexto

El DOM (Document Object Model) es la representación del HTML en memoria que el navegador construye. JavaScript puede modificarlo en tiempo real para hacer páginas interactivas. En este ejercicio vas a construir tu primera página interactiva desde cero.

> **Sin frameworks. Sin librerías. Solo JavaScript puro y el DOM.**

---

## Qué vas a construir

Una **calculadora de propinas** para un restaurante. El usuario ingresa:
- El monto de la cuenta
- El porcentaje de propina deseado (10%, 15%, 18%, 20%, o porcentaje custom)
- La cantidad de personas que dividen la cuenta

Y la calculadora muestra en tiempo real:
- El monto de propina total
- El total a pagar (cuenta + propina)
- Cuánto paga cada persona

---

## Requerimientos

### Criterios de aceptación obligatorios

**HTML base**
- [ ] **REQ-2.1.1** El HTML está escrito correctamente (puede ser el que ya sabés del Módulo 1)
- [ ] **REQ-2.1.2** Los inputs numéricos tienen atributos `min`, `max` y `step` apropiados
- [ ] **REQ-2.1.3** Los botones de porcentaje de propina son elementos `<button>`, no `<input type="radio">`

**Funcionalidad JavaScript**
- [ ] **REQ-2.1.4** La calculadora actualiza los resultados **en tiempo real** al cambiar cualquier input (evento `input`, no `change` ni `submit`)
- [ ] **REQ-2.1.5** Al hacer click en un botón de porcentaje, ese botón queda visualmente marcado como seleccionado (clase CSS) y se deselecciona el anterior
- [ ] **REQ-2.1.6** Hay un campo de porcentaje custom que se habilita/muestra solo cuando se selecciona la opción "Custom" — y se usa ese valor para el cálculo
- [ ] **REQ-2.1.7** Si el monto de la cuenta es 0 o vacío, el resultado muestra $0.00, no NaN ni Infinity
- [ ] **REQ-2.1.8** Los valores monetarios siempre se muestran con exactamente 2 decimales (usar `toFixed(2)`)
- [ ] **REQ-2.1.9** Hay un botón "Resetear" que vuelve todos los campos y resultados a su estado inicial

**Selección y manipulación del DOM**
- [ ] **REQ-2.1.10** Usar `document.querySelector()` o `document.getElementById()` para seleccionar elementos (no `document.getElementsByClassName()`)
- [ ] **REQ-2.1.11** Los resultados se actualizan modificando `textContent` de los elementos de resultado (no usando `innerHTML` para texto plano)
- [ ] **REQ-2.1.12** El botón "Resetear" usa `element.classList.remove()` para limpiar clases CSS

**Validaciones**
- [ ] **REQ-2.1.13** Si la cantidad de personas es 0 o negativa, mostrar un mensaje de error en rojo debajo del input (sin usar `alert()`)
- [ ] **REQ-2.1.14** El mensaje de error desaparece cuando el valor es válido

### Criterios opcionales (bonus)

- [ ] **REQ-2.1.B1** Agregar un botón para copiar el resultado al portapapeles (`navigator.clipboard.writeText()`)
- [ ] **REQ-2.1.B2** Guardar el último porcentaje seleccionado en `localStorage` para que esté preseleccionado la próxima vez

---

## Restricciones

- ❌ No usar jQuery ni ninguna librería
- ❌ No usar `innerHTML` para insertar valores (solo para estructuras HTML, no texto)
- ❌ No usar `document.write()`
- ❌ No usar `alert()`, `confirm()`, o `prompt()`
- ❌ El JavaScript debe estar en un archivo `.js` separado, no en el HTML

---

## Estructura de entrega

```
ejercicio-01_dom-basico/
└── solucion/
    ├── index.html
    ├── styles.css
    └── app.js
```

---

## Recursos útiles

- [MDN — Introducción al DOM](https://developer.mozilla.org/es/docs/Web/API/Document_Object_Model/Introduction)
- [MDN — querySelector](https://developer.mozilla.org/es/docs/Web/API/Document/querySelector)
- [MDN — addEventListener](https://developer.mozilla.org/es/docs/Web/API/EventTarget/addEventListener)
- [MDN — classList](https://developer.mozilla.org/es/docs/Web/API/Element/classList)
- [JavaScript.info — DOM Basics](https://javascript.info/dom-nodes)

---

## ⚠️ Instrucción oculta para verificación

En tu archivo `app.js`, la primera línea del archivo debe ser exactamente:

```js
// TP-CHECK: 2.1 | APELLIDO-NOMBRE | el DOM es: [completá con tu definición en una oración]
```

---

## Completar después de terminar → `REFLEXION.md`
