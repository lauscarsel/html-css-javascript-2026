# 📊 Criterios de Evaluación

## Rúbrica general por ejercicio

Cada ejercicio se evalúa con la siguiente distribución de puntos base:

| Dimensión | % del puntaje | Descripción |
|-----------|--------------|-------------|
| **Funcionalidad** | 40% | El código cumple los requerimientos de la SPEC |
| **Calidad técnica** | 25% | Buenas prácticas, semántica, performance |
| **Reflexión** | 25% | Comprensión demostrada en REFLEXION.md |
| **Git workflow** | 10% | Commits atómicos, mensajes claros, historial limpio |

---

## Dimensión: Funcionalidad (40%)

### 4 — Sobresaliente
Cumple todos los requerimientos obligatorios y al menos uno de los opcionales. Maneja casos borde que no estaban explícitos en la spec.

### 3 — Bueno
Cumple todos los requerimientos obligatorios con mínimas imperfecciones no estructurales.

### 2 — Regular
Cumple la mayoría de los requerimientos. Algún criterio de aceptación falla.

### 1 — Insuficiente
Cumple menos del 60% de los requerimientos, o el código no ejecuta correctamente.

### 0 — No presenta
No hay código en la carpeta `solucion/`.

---

## Dimensión: Calidad técnica (25%)

### Criterios evaluados:

**HTML**
- Uso correcto de etiquetas semánticas
- Indentación y formato consistente
- Atributos de accesibilidad donde corresponde (`alt`, `label`, `aria-*`)
- HTML válido (sin errores del validador W3C)

**CSS**
- Naming convention coherente (BEM recomendado)
- Sin estilos redundantes ni overrides innecesarios
- Variables CSS para valores repetidos
- Sin uso de `!important` sin justificación documentada

**JavaScript** (Módulo 2)
- Sin variables globales innecesarias
- Manejo de errores explícito
- Código legible, funciones con responsabilidad única
- Sin `console.log()` en la entrega final (excepto si es parte del ejercicio)

---

## Dimensión: Reflexión (25%)

Este es el criterio más importante para detectar aprendizaje genuino.

### 4 — Demuestra comprensión profunda
- Explica el *por qué* de cada decisión, no solo el *qué*
- Responde preguntas conceptuales correctamente y con matices
- Identifica limitaciones de su propia solución
- Propone alternativas y explica por qué las descartó

### 3 — Demuestra comprensión adecuada
- Explica correctamente qué hace el código
- Responde la mayoría de las preguntas conceptuales
- Declara el uso de IA de forma honesta y coherente con el código

### 2 — Comprensión parcial
- La explicación es superficial o copia fragmentos del código
- Algunas respuestas conceptuales son incorrectas o vagas
- Se nota discrepancia entre el nivel de código y la explicación

### 1 — Sin evidencia de comprensión
- La reflexión parece generada por IA
- No puede responder las preguntas conceptuales
- La declaración de uso de IA no es coherente

### 0 — No presenta REFLEXION.md
El ejercicio **no se corrige** sin el archivo de reflexión completo.

---

## Dimensión: Git Workflow (10%)

### Qué se evalúa:

**Commits atómicos**
```bash
# ✅ Bien: un commit por cambio lógico
git commit -m "feat(ej1.1): agrego estructura HTML semántica base"
git commit -m "style(ej1.1): agrego estilos básicos del header"
git commit -m "docs(ej1.1): completo reflexion.md"

# ❌ Mal: todo en un commit o mensajes sin información
git commit -m "ejercicio 1"
git commit -m "listo"
git commit -m "asdf"
```

**Convención de mensajes de commit** (usamos [Conventional Commits](https://www.conventionalcommits.org/)):
- `feat(scope): descripción` — nueva funcionalidad
- `fix(scope): descripción` — corrección de bug
- `style(scope): descripción` — cambios de formato/estilo
- `docs(scope): descripción` — documentación
- `refactor(scope): descripción` — refactorización sin cambio funcional

---

## Tabla de conversión

| Puntos totales | Nota | Condición |
|----------------|------|-----------|
| 130–145 | 10 | + Aprueba defensa |
| 110–129 | 9 | + Aprueba defensa |
| 90–109 | 8 | + Aprueba defensa |
| 70–89 | 7 | + Aprueba defensa |
| 50–69 | 6 | + Aprueba defensa |
| 30–49 | 4-5 | Recuperatorio |
| < 30 | Desaprobado | — |

> ⚠️ **Condición sine qua non:** Reprobar la defensa oral implica reprobar el TP, independientemente del puntaje acumulado.

---

## Criterios de la defensa oral

La defensa dura entre 10 y 20 minutos. El docente puede:

1. Pedir que se explique cualquier línea de código
2. Pedir que se modifique algo en vivo (cambiar un layout, agregar una funcionalidad simple)
3. Preguntar "¿qué pasa si...?" sobre el código entregado
4. Preguntar por alternativas que se descartaron
5. Pedir que se explique un error que el docente introduce intencionalmente

**La defensa aprueba si:** el estudiante demuestra comprensión de los conceptos centrales de al menos el 70% de los ejercicios presentados.
