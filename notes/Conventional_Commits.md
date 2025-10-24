# 📓 Guía Rápida de Conventional Commits

**Conventional Commits** es una especificación simple y un conjunto de reglas para crear un historial de commits explícito y legible. Su objetivo es hacer que los mensajes de commit sean fáciles de entender tanto para humanos como para máquinas.

---

## ¿Por Qué Usarlos?

* **Legibilidad:** Crean un historial de Git limpio y fácil de navegar. Cualquiera puede entender qué cambió y por qué.
* **Automatización:** Permiten generar automáticamente registros de cambios (`CHANGELOGs`).
* **Control de Versiones:** Ayudan a determinar automáticamente la siguiente versión de tu software (ej., un `fix:` puede ser la versión `1.0.1`, mientras que un `feat!` con *breaking change* sería la `2.0.0`).

---

## La Estructura

El formato general de un mensaje de commit es:

```markdown
<tipo>[<ámbito opcional>]: <descripción>

[<cuerpo opcional>]

[<pie opcional>]
```

## 1. Tipo (Type) - Obligatorio
Esta es la parte más importante. Define la categoría del cambio. Los más comunes son:

- feat: (Feature) -> Añade una nueva característica o funcionalidad.
- fix: (Bug Fix) -> Corrige un error (bug) en el código.
- docs: (Documentation) -> Cambios que solo afectan a la documentación (comentarios, archivos .md, etc.).
- style: (Styling) -> Cambios que no afectan la lógica del código, solo el formato (espacios, punto y coma, etc.).
- refactor: (Refactoring) -> Reestructura el código existente sin cambiar su comportamiento (ej. renombrar una variable, limpiar código).
- test: (Tests) -> Añade o corrige tests (pruebas unitarias, etc.).
- chore: (Chore / Tarea) -> Cambios de mantenimiento que no son ni fix ni feat (ej. actualizar librerías, configurar herramientas).

## 2. Ámbito (Scope) - Opcional
Un sustantivo entre paréntesis que especifica la sección del código que se modificó.

- feat(api): -> Una nueva característica en la API.
- fix(auth): -> Un error corregido en el módulo de autenticación.
- docs(readme): -> Cambios en el archivo README.

## 3. Descripción (Description) - Obligatorio
Una breve descripción del cambio (menos de 50-72 caracteres).

- Empieza con minúscula.
- Está en modo imperativo (ej. "añade" en lugar de "añadido" o "añadiendo"). Piensa en ello como dar una orden: "Este commit añade...".

### Malos Ejemplos:
- fix: Arreglé el bug
- Añadiendo el análisis
- feat: Nueva función para el análisis de keywords con un nombre muy largo que explica todo

### Buenos Ejemplos:
- fix: soluciona el error de división por cero
- feat: añade el script de análisis de Google Ads
- docs(readme): actualiza las instrucciones de instalación

## 4. Cuerpo (Body) - Opcional
Aquí es donde explicas el "por qué" del cambio. Se separa del asunto con una línea en blanco.
```markdown
fix(parser): soluciona el error al procesar fechas nulas

El parser fallaba si la columna 'fecha_compra' contenía un valor NaN,
causando un error en el reporte mensual.

Este commit añade un chequeo .isnull() antes de la conversión.
```
## 5. Pie (Footer) - Opcional
Se usa principalmente para dos cosas:

### I. BREAKING CHANGES (Cambios Rompedores)
Un cambio que rompe la compatibilidad con versiones anteriores. Se indica con BREAKING CHANGE: en el pie. También puedes usar un ! después del tipo para resaltarlo.

```markdown
feat(api)!: cambia el nombre del endpoint de usuarios

BREAKING CHANGE: El endpoint `/users` ahora es `/api/v1/users`.
Todas las aplicaciones cliente deben ser actualizadas.
```

### II. Referenciar Issues (Incidencias)
Para cerrar automáticamente un "issue" o "ticket" en GitHub o Jira.

```markdown
fix(login): corrige el bucle de redirección

Soluciona el problema donde los usuarios quedaban atascados.

Closes: YX123
```

# Ejemplo completo:
feat: añade el script de análisis de Google Ads

Crea el script inicial `analysis_google_ads.py` para cargar
y explorar el set de datos.

Este análisis incluye:
- Carga del CSV a un DataFrame de Pandas.
- Inspección básica con .head() e .info().
- Resumen estadístico con .describe().
