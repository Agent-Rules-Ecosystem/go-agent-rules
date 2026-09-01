# 🦫 Go Agent Rules (`go-agent-rules`)

> Repositorio oficial de gobernanza y protocolos de actuación para Agentes de IA en proyectos desarrollados en **Go (Golang)**.

---

## 📌 Descripción

`go-agent-rules` es el núcleo de gobernanza y directivas para cualquier proyecto de software en **Go** (microservicios, CLI, APIs REST/gRPC, comunicación industrial, concurrencia de alto rendimiento). Se instala como submódulo git en `.agents/` dentro del repositorio huésped.

---

## 📁 Estructura del Core

```
go-agent-rules/
├── AGENTS.md               ← Directiva universal de bootstrap
├── README.md               ← Documentación principal
├── adapters/               ← Adaptadores para Gemini, Claude, Cursor, OpenAI
├── core/                   ← Motor operativo de gobernanza
│   ├── brain.md            ← Lógica de decisión, handoffs y triaje
│   ├── commands.md         ← Comandos con prefijo $ ($boot, $work, $archi, $close, etc.)
│   ├── communication.md    ← Modo Cavernícola y reglas de ahorro de tokens
│   ├── learning_protocol.md← Protocolo de 3 Vías y Filtro Agnóstico
│   └── path_map.md         ← Mapa canónico de rutas Go
├── knowledge/              ← Guías técnicas Go (Clean Arch, Concurrencia, Testing)
├── skills/                 ← Catálogo de habilidades Go compatibles
└── templates/              ← Plantillas para scaffold de overview/ en el proyecto
```

---

## ⚡ Comandos Principales

- `$boot`: Inicializa la sesión, ejecuta el scaffold de `overview/`, audita linters (`golangci-lint`, `go test`) y líneas de código (>250L).
- `$work [descripción]`: Registra una nueva tarea/bug con sincronización simultánea en `overview/`.
- `$archi`: Audita y modulariza la arquitectura viva del proyecto bajo el estándar Hub & Spoke (`ARCHITECTURE_STANDARD.md`).
- `$status`: Diagnóstico compacto del estado actual del sistema.
- `$close`: Valida los tests del proyecto (`go test ./...`), actualiza rastreadores y cierra la sesión.

---

## 🚀 Instalación en un Proyecto Go

```bash
git submodule add git@github.com:Agent-Rules-Ecosystem/go-agent-rules.git .agents
```

## ⚡ Quick Start

**1. Instala la gobernanza en tu proyecto**
```bash
git submodule add git@github.com:Agent-Rules-Ecosystem/go-agent-rules.git .agents
```

**2. Inicia el agente**
```text
$boot
```

**3. Registra tu primera tarea**
```text
$work agregar handler HTTP para autenticación de usuarios
```

---
