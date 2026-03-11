
```mermaid

graph TD
    %% Estilos de Nodos
    classDef central fill:#99cc00,stroke:#333,stroke-width:2px,color:black;
    classDef system fill:#fff4dd,stroke:#d4a017,stroke-width:1.5px,color:black;
    classDef actor fill:#fff,stroke:#333,stroke-width:1px;
    classDef process fill:#e1f5fe,stroke:#01579b,stroke-width:1.5px;

    %% Nodo Central (Anonimizado)
    CORE(("Core-Collections<br/>(Gestión de Cobros)")):::central

    %% Sistemas Externos
    MOSAIC[("MOSAIC<br/>(DB Central)")]:::system
    SWITCH{{"Switch"}}:::system
    AC["AC (Contabilidad)"]:::system
    SAS["SAS (Jerarquía)"]:::system
    SAP["SAP (ERP)"]:::system
    BI["Business Intelligence"]:::system
    
    %% Actores y Entidades
    PAGADOR((Pagador)):::actor
    CAJERO_RSC((Cajero RSC)):::actor
    COBRADOR_PC((Cobrador Suc. con PC)):::actor
    COBRADOR_SIN_PC((Cobrador sin PC)):::actor
    COBRADORA((Cobradora)):::actor
    DEP_PROV((Dependencia o Admin. Provincial)):::actor
    LIQUIDADORA((Liquidadora)):::actor
    CLIENTE((Cliente)):::actor
    TESORERIA((Tesorería)):::actor

    %% Centro Operativo
    SUC_PC[["Sucursales con PC"]]:::process

    %% --- FLUJOS DE INFORMACIÓN ---

    %% Entrada y Captura
    PAGADOR -- "$$, cupón" --> COBRADOR_PC
    PAGADOR -- "$$" --> COBRADOR_SIN_PC
    
    CAJERO_RSC -- "Datos cupón" --> MOSAIC
    CAJERO_RSC -- "Cupón físico" --> COBRADORA
    
    COBRADOR_SIN_PC -- "Cupón físico, planilla" --> COBRADORA
    COBRADORA -- "Cupón físico y planilla" --> DEP_PROV
    
    COBRADOR_PC -- "Datos cupón" --> SUC_PC
    SUC_PC -- "Datos cupón" --> SWITCH
    SWITCH -- "Novedades cliente" --> SUC_PC

    %% Interacción con el Sistema Central (CORE)
    CORE -- "Planilla cobranza" --> SUC_PC
    CORE -- "Maestro clientes" --> MOSAIC
    MOSAIC -- "Planilla cobranza" --> COBRADOR_PC
    MOSAIC -- "Datos cupón" --> SWITCH
    
    SWITCH -- "Cupones del día" --> CORE
    SWITCH -- "Novedades cliente" --> MOSAIC
    
    AC -- "Parámetros contables" --> CORE
    SAS -- "Árbol jerárquico" --> CORE
    
    DEP_PROV -- "Datos cupón, planilla" --> CORE
    CORE -- "Planilla de recaudación" --> DEP_PROV

    %% Salidas y Liquidación
    CORE -- "GL, SD" --> SAP
    SAP -- "Factura" --> TESORERIA
    
    TESORERIA -- "$$ Comisión" --> CLIENTE
    CLIENTE -- "$$ Recaudación y factura" --> TESORERIA
    
    CORE -- "Planilla liquidación" --> LIQUIDADORA
    DEP_PROV -- "Planilla rec. y cupones" --> LIQUIDADORA
    LIQUIDADORA -- "Rendición recaudación" --> DEP_PROV
    LIQUIDADORA -- "Planilla liq., cupones" --> CLIENTE
