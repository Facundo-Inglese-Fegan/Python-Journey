# Manual Avanzado de Fundamentos de Git & GitHub

---

## Índice
0. Notas originales
1. Conceptos clave
2. Comandos esenciales (ampliados)
3. Flujo de trabajo y estrategias de branching
4. Reescritura de historial y recuperación
5. Git internals (resumen práctico)
6. GitHub: características avanzadas y flujo colaborativo
7. Seguridad, autenticación y tokens
8. Herramientas complementarias y casos prácticos
9. Buenas prácticas ampliadas
10. Alias, configuración y rendimiento
11. Solución de conflictos (pasos rápidos)
12. Casos prácticos y recetas rápidas
13. Checklist de calidad para PRs
14. Recursos finales (sugeridos)

---

## 1) Conceptos clave (resumen rápido)
- **Working Directory (Computador)**. Archivos editables. Git no sigue automáticamente todo. En esta etapa escribimos nuestro código en VSC.
- **Staging Area (Stage / Index)**. Seleccionas los cambios que entrarán al commit.
- **Commit**. Foto del estado del index. Contiene autor, mensaje, y SHA-1.
- **Remote (Server)**. Repositorio alojado (GitHub, GitLab).
- **Branch**. Puntero móvil a commits. Facilita trabajo aislado.
- **Tag**. Marca fija para releases.
- **HEAD**. Referencia al commit actual o a la rama actual.

- **Token**. Cuando operemos por primera vez con un equipo, Git nos va a pedir nuestro usuario de GitHub y una contraseña que debemos obtener de *GitHub-> Profile-> Settings-> Developer settings-> Personal access tokens-> Tokens(classic)-> Generate new token (classic)* para poder conectarnos con el servidor. Al crear el Token, podemos seleccionar los permisos y alcance (scope). El scope repo es el básico para acceder al repositorio, pero también podemos otorgarle el scope workflow para automatizaciónes y BOTs en GitHub.

---

## 2) Comandos esenciales (ampliados y ejemplos prácticos)

### Configuración inicial
```bash
git --version # conocer la versión de Git que tenemos
git config --global user.name "Tu Nombre" # establecer el nombre de usuario
git config --global user.email "tu@correo.com" # establecer el correo electrónico
git config --global core.editor "code --wait" # seleccionar el editor de texto predeterminado
git config --global -e # abrir el editor de texto predeterminado
git config --global core.autocrlf true   # Windows -> LF/CRLF handling saltos de línea
git config --global credential.helper cache  # opcional
```

### Inicializar, clonar e ignore
```bash
# iniciar repo local
init
git init

# clonar repo remoto
git clone git@github.com:usuario/repo.git
git clone https://github.com/usuario/repo.git
git remote add origin https://github.com/usuario/repo.git
```
- Se puede crear un archivo .gitignore al crear un repositorio en GitHub o directamente en VSC y colocar en cada línea aquellos archivos o rutas que queremos que Git no siga.

### Flujo básico
```bash
git status  # saber el estado actual del directorio donde nos encontramos
git status -s # saber el estado actual del directorio donde nos encontramos de forma resumida
git add . # pasar todos los archivos a stage
git add .txt # pasar todos los archivos .txt a stage
git add file1.txt file2.txt # pasar archivos a stage 
git add -p # agregar cambios interactivos por hunk
git restore --staged file1.txt file2.txt  # quitar del stage
git commit -m "Mensaje claro y conciso" # comprometer los archivos en stage
git log # ver el historial de cambios
git log --oneline --graph --decorate --all # distintas formas de ver el log
ls # listar archivos y carpetas de la ubicación
ls -a # listar archivos y carpetas de la ubicación incluídos los ocultos
pwd # conocer nuestra ubicación actual
cd Desktop # acceder a una carpeta
cd .. # salir de una carpeta 
mkdir # crear nueva carpeta (proyecto)
cat file1.txt # ver el contenido del archivo
```

### Ramas y trabajo en features
```bash
git branch # listar ramas
git checkout -b feat/nombre # crear una nueva rama
git branch -m master main # renombrar rama
git merge feat/nombre # unificar la rama con main (debemos estar en main)
git push # subimos nuestro trabajo de Git a GitHub
git push -u origin main # subimos nuestros cambios de Git a GitHub creando la rama main
git fetch origin 
git pull # bajamos el trabajo de GitHub a Git
git pull --rebase # rebase al traer cambios
```

### Ver diferencias y cambios
```bash
git diff # detalle de cambios no staged (q para salir del menu)
git diff --staged # detalle de cambios staged
git show <commit> # ver contenido de un commit
```

### Borrar, mover, restaurar
```bash
rm file.txt # eliminar un archivo del repositorio
mv file.txt newfile.txt # cambiar el nombre de un archivo (no compromete la acción)
git rm file.txt  
git mv file.txt newfile.txt # cambiar el nombre de un archivo y comprometer la acción
git restore file.txt # recuperar versión HEAD en working dir
git restore --source HEAD~1 file.txt
```
---

## 3) Flujo de trabajo y estrategias de branching

### Modelos comunes
- **GitHub Flow**: main siempre desplegable. Feature branches cortas. PR + review.
- **GitLab / GitFlow**: ramas `develop`, `release`, `hotfix`. Útil en proyectos con releases formales.
- **Trunk-based**: ramas muy cortas. Integración continua frecuente.

### Recomendaciones prácticas
- Nombres claros: `feat/`, `fix/`, `chore/`, `hotfix/`.
- PRs pequeños. Commits atómicos.
- Rebase interactivo para limpiar commits antes de merge si el equipo lo acepta.
- Protege `main` con reglas en GitHub (branch protection) y checks obligatorios.

---

## 4) Reescritura de historial y recuperación

### Reset, Revert y Reflog
- `git revert <commit>`: crea un nuevo commit que invierte los cambios. Seguro para repos remotos.
- `git reset --soft <commit>`: mueve HEAD pero mantiene index y working tree.
- `git reset --mixed <commit>` (por defecto): mueve HEAD y index.
- `git reset --hard <commit>`: descarta index y working tree. Peligroso.
- `git reflog`: historial de referencias locales. Útil para recuperar commits perdidos.
  ```bash
  git reflog
  git checkout -b fix-recover <sha>
  ```

### Rebase interactivo
```bash
git rebase -i HEAD~5
# reordenar, squash, fixup, drop
```
- Útil para limpiar commits antes de publicar.
- **No** reescribir commits ya push si otros los usan.

### Cherry-pick
```bash
git cherry-pick <commit>
```
- Copia un commit específico a la rama actual.

### Stash
```bash
git stash push -m "work in progress"
git stash list
git stash apply stash@{0}
git stash pop
git stash branch nueva-rama stash@{0}  # convertir stash a rama
```

### Git bisect
- Búsqueda binaria para encontrar commit que introdujo bug.
```bash
git bisect start
git bisect bad
git bisect good <commit>
# test y marcar good/bad hasta hallar commit culpable
git bisect reset
```

---

## 5) Git internals (práctico)
- Objetos: **blob** (archivo), **tree** (directorio), **commit** (metadatos), **tag** (referencia).
- SHA1/SHA256 identifican objetos.
- HEAD apunta a una rama. Las ramas son punteros a commits.
- Index es un archivo binario que almacena la “staging area”.
- Reflog guarda movimientos locales de HEAD y ramas por 90 días por defecto.

---

## 6) GitHub: características avanzadas y flujo colaborativo

### Pull Requests (PR)
- Crear PR desde branch feature a main.
- Usar plantillas de PR para estandarizar descripción, checklist, QA steps.
- Añadir reviewers y asignar labels.
- Requerir checks (unit tests, lint, build) antes de merge.

### Branch protection
- Requerir PRs revisadas.
- Requerir checks verdes.
- Aprobar por X reviewers.
- Bloquear force-push.

### CODEOWNERS
- Archivo `CODEOWNERS` para asignar revisores automáticos según paths.

### Releases y tags
```bash
git tag -a v1.2.0 -m "Release v1.2.0"
git push origin v1.2.0
```
- Usar tags semánticos y changelogs.

### GitHub Actions (CI)
- Automatizar tests, linters, despliegues.
- Archivo: `.github/workflows/ci.yml`
- Recomiendo un workflow que ejecute `checkout`, deps, tests, y publique artefactos.

### Seguridad y automatizaciones
- Dependabot para actualizaciones de dependencias.
- Secret scanning y Dependabot alerts.
- Revisión de tokens y escaneo de vulnerabilidades vía Security tab.

---

## 7) Seguridad, autenticación y tokens

### SSH vs HTTPS
- **SSH**: configurar claves en `~/.ssh/id_rsa` y añadir al GitHub account.
- **HTTPS + PAT**: usar Personal Access Token (PAT) con scopes mínimos (`repo`, `workflow` si aplica).
  - Crear token en GitHub -> Settings -> Developer settings -> Personal access tokens.
  - Usar `git credential-manager` o `credential.helper store` para no ingresar el token cada vez.

### Firmar commits
```bash
# generar clave GPG y configurar
git config --global user.signingkey <GPG_KEY>
git config --global commit.gpgsign true
git commit -S -m "Mensaje"
```

### 2FA
- Activar 2FA en GitHub. Usar PATs o SSH para autenticación desde Git.

---

## 8) Herramientas complementarias y casos prácticos

### Git LFS (Large File Storage)
```bash
git lfs install
git lfs track "*.pb"
git add .gitattributes
```
- Mover archivos binarios a LFS.

### Submodules vs Subtrees
- **Submodules**: referencian otro repo exacto. Necesitan `git submodule update --init --recursive`.
- **Subtree**: permitir integrar código sin dependencia separada. Más simple para deploy.

### Worktrees
```bash
git worktree add ../other-branch other-branch
```
- Permite múltiples working trees desde un repo.

### .gitattributes
- Controla EOL, diff para binarios, merge drivers.
```text
*.jpg binary
*.md text
```

---

## 9) Buenas prácticas ampliadas

### Modificación del código
- Cualquier cambio que hagamos con un archivo en la etapa del Computador, incluso la eliminación de un archivo, debe ser agregada al Stage mediante el comando "git add" para mayor visibilidad y seguimiento.
- Salvo excepciones, no debemos usar el comando `git add .` y pasar a Stage todos los archivos untracked, ya que se pierde el control y seguimiento de los archivos subidos pudiendo producirse errores graves.

### Mensajes de commit
- Línea subject <= 50 chars. Blank line. Descripción detallada si aplica.
- Usar estilo: `type(scope): short summary` (Conventional Commits).
  - Ej: `feat(parser): agregar manejo de nulls`
- Mensajes claros. Explicar el *por qué* no solo el *qué*.

### Tamaño de PRs
- PRs pequeños. 200-400 líneas idealmente.
- Incluir checklist de QA, pasos para reproducir, pruebas unitarias.

### Revisiones de código
- Revisiones centradas en seguridad, tests, legibilidad, complejidad.
- Evitar cambios masivos no relacionados.

### Branch naming
- `feat/`, `fix/`, `chore/`, `hotfix/`, `refactor/`.

---

## 10) Alias, configuración y rendimiento

### Alias recomendados
```bash
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.st status
git config --global alias.lg "log --oneline --graph --decorate --all"
```

### Configuración útil
```bash
git config --global pull.rebase false   # o true si prefieres rebase al pull
git config --global core.editor "code --wait"
git config --global init.defaultBranch main
```

### Mantenimiento y rendimiento
```bash
git gc --aggressive --prune=now
git repack -a -d --depth=250 --window=250
git remote prune origin
```
- Usar `git fetch --prune` para limpiar refs remotas obsoletas.
- Evitar commits gigantescos que afecten packfiles.

---

## 11) Solución de conflictos (pasos rápidos)
1. `git pull` o `git merge`: si hay conflicto, Git lo marca en archivos.
2. Abrir archivos conflictivos. Buscar marcadores `<<<<<<<`, `=======`, `>>>>>>>`.
3. Resolver manualmente.
4. `git add <archivo>`
5. `git commit` (o `git rebase --continue` si estabas en rebase).
6. `git push`

---

## 12) Casos prácticos y recetas rápidas

### Cambio urgente en main remoto (hotfix)
```bash
git checkout main
git pull
git checkout -b hotfix/bug-123
# arreglar
git add .
git commit -m "fix: corregir fallo X"
git push origin hotfix/bug-123
# abrir PR y merge a main
```

### Limpiar commits antes de push
```bash
# reescribir últimos 3 commits
git rebase -i HEAD~3
# squash/fixup y luego
git push --force-with-lease origin feat/branch
```

### Recuperar archivo borrado por accidente
```bash
git checkout HEAD -- path/to/file
```

### Recuperar commit perdido
```bash
git reflog
git checkout -b recover <sha>
```

---

## 13) Checklist de calidad para PRs
- [ ] Tests unitarios pasan.
- [ ] Linter sin errores.
- [ ] Mensaje de commit y PR claros.
- [ ] No hay secretos en el diff.
- [ ] Tamaño manejable.
- [ ] Documentación actualizada.

---

## 14) Recursos finales (sugeridos)
- Documentación oficial de Git (pro Git book).
- GitHub Docs para Actions, Security, Releases.
- Guías sobre Git internals y mejores prácticas (buscar “Pro Git”, “Git from the bottom up”).
- Repositorios de referencia con templates de PR y issue templates.

---

### Fin del archivo `.md`.
