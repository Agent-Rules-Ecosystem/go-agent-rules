# Arquitectura Viva del Proyecto (Hub Raíz)

```mermaid
graph TD
    Client[Cliente HTTP / gRPC] --> Delivery[Delivery Layer: Handlers / Routers]
    Delivery --> Usecase[Usecase / Domain Logic]
    Usecase --> Repository[Repository Layer / Storage]
    Repository --> DB[(Base de Datos / PLC / API)]
```

## Subdocumentos de Arquitectura (Spoke)
- [Mapa de Rutas](overview/architecture/routes_map.md)
- [Flujo de Datos](overview/architecture/core/data_flow.md)
- [Reglas de Importación](overview/architecture/core/import_rules.md)
