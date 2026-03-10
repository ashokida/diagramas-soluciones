```mermaid

graph TD
    SOC((Sistema de Operaciones de Caja SOC))

    subgraph Roles de Usuario
        Operacion[Operación y Supervisión] -- "Cargas y Reportes" --> SOC
        Gestion[Gestión y Control] -- "Maestros y Seguimiento" --> SOC
        Seguridad[Seguridad y Finanzas] -- "Límites y Usuarios" --> SOC
    end

    subgraph Entidades Externas
        SOC -- "Asientos Contables" --> SAP[SAP]
        SAP -- "Maestros Materiales/Cuentas" --> SOC
        SSUC[Conexión SSUC] -- "Info Maestra Sucursales" --> SOC
        PVTA -- "Ajustes Contables" --> SOC
    end

    %% Estilo para resaltar el núcleo
    style SOC fill:#f9f,stroke:#333,stroke-width:4px
