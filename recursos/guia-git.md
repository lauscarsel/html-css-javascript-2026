# 🔧 Guía de Git para el TP

## Comandos esenciales

### Setup inicial (una sola vez)

```bash
# 1. Cloná TU fork (no el repositorio original)
git clone https://github.com/TU-USUARIO/tp-frontend.git
cd tp-frontend

# 2. Configurá tu identidad
git config user.name "Tu Nombre"
git config user.email "tu-email@ejemplo.com"

# 3. Creá tu rama personal
git checkout -b tp/apellido-nombre
# Ejemplo: git checkout -b tp/garcia-maria

# 4. Verificá que estás en la rama correcta
git branch
# Debería mostrar: * tp/garcia-maria
```

### Flujo de trabajo diario

```bash
# Ver qué archivos modificaste
git status

# Ver los cambios exactos
git diff

# Agregar cambios al staging
git add nombre-del-archivo.html    # Un archivo específico
git add modulo-01_html-css/ejercicio-01_estructura-semantica/  # Una carpeta
# NO usar: git add . (evitá agregar archivos no deseados)

# Hacer commit con mensaje descriptivo
git commit -m "feat(ej1.1): agrego estructura HTML semántica"

# Subir a GitHub
git push origin tp/apellido-nombre
```

### Mensajes de commit — Convención

Formato: `tipo(scope): descripción en presente`

```bash
# ✅ Ejemplos correctos
git commit -m "feat(ej1.1): agrego estructura HTML base con nav y footer"
git commit -m "style(ej1.3): ajusto gap y flex-basis en tarjetas"
git commit -m "fix(ej2.4): corrijo manejo de error 404 en fetch"
git commit -m "docs(ej1.1): completo reflexion.md con preguntas conceptuales"
git commit -m "refactor(ej2.6): extraigo función fetchPersonajes a módulo separado"

# ❌ Ejemplos incorrectos
git commit -m "cambios"
git commit -m "listo el ejercicio 3"
git commit -m "arregle un bug"
git commit -m "WIP"
```

**Tipos válidos:**
- `feat` — nueva funcionalidad
- `fix` — corrección de bug
- `style` — CSS, formato, sin cambio de lógica
- `docs` — documentación, reflexión
- `refactor` — mejora de código sin cambio de comportamiento
- `test` — tests

---

## Cómo hacer el Pull Request

### Cuando terminés un módulo:

1. **Asegurate de tener todo pusheado:**
```bash
git status          # No debe haber cambios pendientes
git push origin tp/apellido-nombre
```

2. **Andá a GitHub** → Tu fork → "Pull requests" → "New pull request"

3. **Configuración del PR:**
   - Base repository: `[repositorio-de-la-catedra]/tp-frontend`
   - Base: `main`
   - Head: `tu-usuario/tp-frontend`
   - Compare: `tp/apellido-nombre`

4. **Completá el template** que aparece automáticamente

---

## Mantener tu fork actualizado

Si el docente actualiza el repositorio original (correcciones, nuevos ejercicios):

```bash
# Agregar el repositorio original como "upstream" (una sola vez)
git remote add upstream https://github.com/[catedra]/tp-frontend.git

# Traer los cambios
git fetch upstream

# Mergeá en tu rama
git merge upstream/main

# Si hay conflictos, resolverlos y luego:
git add .
git commit -m "merge: actualizo desde repositorio de cátedra"
git push origin tp/apellido-nombre
```

---

## Errores comunes y soluciones

### "rejected — non-fast-forward"
```bash
# Alguien (o vos desde otra máquina) pusheó cambios que no tenés localmente
git pull origin tp/apellido-nombre
# Resolvé conflictos si los hay, luego volvé a hacer push
```

### "Your branch is ahead of 'origin' by N commits"
```bash
# Tenés commits locales que no subiste — solo hacer push
git push origin tp/apellido-nombre
```

### "Changes not staged for commit"
```bash
# Tenés cambios sin agregar al staging
git add archivo-modificado
git commit -m "tu mensaje"
```

### Quiero deshacer el último commit (sin perder los cambios)
```bash
git reset --soft HEAD~1
# Los cambios vuelven a staging, el commit desaparece
```

### Quiero ver el historial de commits
```bash
git log --oneline    # Vista compacta
git log --graph      # Vista con árbol de ramas
```

---

## Recursos adicionales

- [Git - La guía sencilla](https://rogerdudler.github.io/git-guide/index.es.html)
- [Learn Git Branching](https://learngitbranching.js.org/?locale=es_AR) — Interactivo
- [Conventional Commits](https://www.conventionalcommits.org/es/v1.0.0/)
- [Oh Shit, Git!](https://ohshitgit.com/es) — Soluciones a errores comunes
