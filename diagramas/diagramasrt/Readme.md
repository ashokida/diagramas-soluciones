
```mermaid

graph TD
    %% Configuración de Estilo Global para alto contraste
    classDef default fill:#ffffff,stroke:#000000,stroke-width:2px,color:#000000,font-weight:bold;
    
    %% Nodo Central Destacado (Borde más grueso)
    classDef central fill:#ffffff,stroke:#000000,stroke-width:4px,color:#000000,font-weight:bold;

    %% --- NODOS ---
    
    CORE(("CORE-COLLECTIONS<br/>(Sistema Central)")):::central

    %% Sistemas
    MOSAIC[("MOSAIC<br/>(Base de Datos)")]
    SWITCH{{"SWITCH<br/>(Intercambio)"}}
    AC["AC<br/>(Contabilidad)"]
    SAS["SAS<br/>(Estructura)"]
    SAP["SAP<br/>(ERP)"]
    BI["Business Intelligence"]
    
    %% Actores
    PAGADOR(("PAGADOR"))
    CAJERO_RSC(("CAJERO RSC"))
    COBRADOR_PC(("COBRADOR SUC.<br/>CON PC"))
    COBRADOR_SIN_PC(("COBRADOR<br/>SIN PC"))
    COBRADORA(("COBRADORA"))
    DEP_PROV(("DEPENDENCIA<br/>PROVINCIAL"))
    LIQUIDADORA(("LIQUIDADORA"))
    CLIENTE(("CLIENTE"))
    TESORERIA(("TESORERÍA"))

    %% Centros Operativos
    SUC_PC[["SUCURSALES<br/>CON PC"]]

    %% --- FLUJOS DE INFORMACIÓN ---

    %% Entradas
    PAGADOR -->|"$$, Cupón"| COBRADOR_PC
    PAGADOR -->|"$$"| COBRADOR_SIN_PC
    
    CAJERO_RSC -->|"Datos Cupón"| MOSAIC
    CAJERO_RSC -->|"Cupón Físico"| COBRADORA
    
    COBRADOR_SIN_PC -->|"Cupón y Planilla"| COBRADORA
    COBRADORA -->|"Cupón y Planilla"| DEP_PROV
    
    COBRADOR_PC -->|"Datos Cupón"| SUC_PC
    SUC_PC -->|"Datos Cupón"| SWITCH
    SWITCH -->|"Novedades"| SUC_PC

    %% Relaciones con el CORE
    CORE -->|"Planilla Cobranza"| SUC_PC
    CORE -->|"Maestro Clientes"| MOSAIC
    MOSAIC -->|"Planilla Cobranza"| COBRADOR_PC
    MOSAIC -->|"Datos Cupón"| SWITCH
    
    SWITCH -->|"Cupones del Día"| CORE
    SWITCH -->|"Novedades"| MOSAIC
    
    AC -->|"Parámetros"| CORE
    SAS -->|"Jerarquía"| CORE
    
    DEP_PROV -->|"Datos Cupón"| CORE
    CORE -->|"Planilla Recaudación"| DEP_PROV

    %% Salidas y Liquidación
    CORE -->|"Asientos (GL, SD)"| SAP
    SAP -->|"Factura"| TESORERIA
    
    TESORERIA -->|"$$ Comisión"| CLIENTE
    CLIENTE -->|"$$ Recaudación"| TESORERIA
    
    CORE -->|"Planilla Liquidación"| LIQUIDADORA
    DEP_PROV -->|"Planilla y Cupones"| LIQUIDADORA
    LIQUIDADORA -->|"Rendición"| DEP_PROV
    LIQUIDADORA -->|"Planilla y Cupones"| CLIENTE
    
    CORE -- "Planilla liquidación" --> LIQUIDADORA
    DEP_PROV -- "Planilla rec. y cupones" --> LIQUIDADORA
    LIQUIDADORA -- "Rendición recaudación" --> DEP_PROV
    LIQUIDADORA -- "Planilla liq., cupones" --> CLIENTE
