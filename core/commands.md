# Comandos del Core ($-commands) — go-agent-rules

Cuando el usuario escribe un comando con prefijo `$`, el agente lo reconoce como instrucción explícita y ejecuta el protocolo correspondiente **inmediatamente**, sin esperar bootstrap automático.

---

## Referencia rápida

| Comando | Acción |
|---|---|
| `$boot` | Bootstrap completo del proyecto Go (Microservicio / CLI / Web API / Concurrencia) |
| `$status` | Mostrar estado actual en resumen |
| `$work [descripción]` | Registrar nueva tarea/bug en el proyecto Go |
| `$archi` | Actualizar arquitectura viva conforme a ARCHITECTURE_STANDARD.md (Hub & Spoke) |
| `$learn [texto]` | Registrar aprendizaje general candidato en `overview/learning.md` |
| `$learnagnostico [texto]` | Abstraer a términos genéricos antes de registrar |
| `$close` | Protocolo de cierre de sesión con comprobación de `go test ./...` y `golangci-lint` |

---

## Definición de cada comando

### `$boot`

Dispara el bootstrap completo:
0. Ejecutar `git submodule status`.
1. Leer `core/path_map.md`, `core/communication.md`, `core/brain.md`, `core/commands.md`.
2. **Scaffold incremental desde templates**: Comparar la estructura de `templates/` con `overview/`. Crear carpetas/archivos faltantes sin sobreescribir existentes.
3. Cargar archivos de control de `overview/`.
4. Auditoría de líneas: listar archivos Go (`.go`) >250L; sugerir IDs `deuda` en `overview/work/deuda_tecnica.md`.
5. Reportar resumen compacto en 5 líneas máximo.

### `$status`

Mostrar el estado actual del proyecto sin modificar ningún archivo.

### `$work [descripción]`

Registrar una nueva tarea o bug en `overview/work/`.

### `$archi`

Auditar y mantener la arquitectura del proyecto bajo el estándar Hub & Spoke (`ARCHITECTURE_STANDARD.md`).
Mapear módulos Go en `cmd/`, `internal/` y `pkg/` mediante diagramas Mermaid (`graph LR` / `graph TD`).

### `$learn [texto]` y `$learnagnostico [texto]`

Registrar un aprendizaje en `overview/learning.md` aplicando el **Filtro Agnóstico**.

### `$close`

Protocolo de cierre de sesión:
1. Ejecutar `go test ./...` (y `golangci-lint run` si está presente). Si no hay tests → `no aplica`.
2. Sincronizar simultáneamente todos los archivos de control en `overview/`.
3. Reportar en 1 línea el resumen final.
