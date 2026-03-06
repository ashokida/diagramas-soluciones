graph TD
    PDC((Sistema Central PDC))

    subgraph Roles de Usuario
        Operacion[Operación y Supervisión] -- "Cargas y Reportes" --> PDC
        Gestion[Gestión y Control] -- "Maestros y Seguimiento" --> PDC
        Seguridad[Seguridad y Finanzas] -- "Límites y Usuarios" --> PDC
    end

    subgraph Entidades Externas
        PDC -- "Asientos GL/SD" --> SAP[SAP A]
        SAP -- "Maestros Materiales/Cuentas" --> PDC
        NIS[Conexión NIS] -- "Info Maestra Sucursales" --> PDC
        SAS[MOSAIC / SAS] -- "Ajustes Contables" --> PDC
    end

    %% Estilo para resaltar el núcleo
    style PDC fill:#f9f,stroke:#333,stroke-width:4px
