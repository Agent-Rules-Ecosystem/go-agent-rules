# Clean Architecture y Standard Project Layout en Go

> Guía técnica de arquitectura para proyectos de producción en Go.

---

## 🏗️ Estructura Standard (`golang-standards/project-layout`)

```
/
├── cmd/
│   └── app/
│       └── main.go          # Entrypoint de la aplicación
├── internal/
│   ├── domain/              # Entidades puras y contratos (Interfaces)
│   ├── usecase/             # Lógica de negocio / Casos de uso
│   ├── repository/          # Implementación de acceso a datos (DB, Redis, API)
│   └── delivery/            # Handlers (HTTP/Gin/Fiber, gRPC, CLI)
├── pkg/                     # Librerías expuestas para otros proyectos (si aplica)
├── config/                  # Carga de variables de entorno y Viper/envconfig
├── go.mod
└── go.sum
```

---

## 🛡️ Reglas Inviolables de Capas

1. **`domain` no depende de nada**: Solo define estructuras (`struct`) e interfaces.
2. **`usecase` depende de `domain`**: Utiliza interfaces para interactuar con bases de datos o servicios externos.
3. **Inyección de Dependencias manual**: Inicializar dependencias en `main.go` o mediante generadores como `google/wire`.
4. **Manejo de Errores Idiomático**: Retornar `(T, error)`. Utilizar wrapping con `%w` (`fmt.Errorf("usecase failed: %w", err)`).
