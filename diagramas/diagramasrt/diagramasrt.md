
```mermaid

graph TD
    %% Configuración de Estilo Global para alto contraste
    classDef default fill:#ffffff,stroke:#000000,stroke-width:2px,color:#000000,font-weight:bold;
    
    %% Nodo Central Destacado (Borde más grueso)
    classDef central fill:#ffffff,stroke:#000000,stroke-width:4px,color:#000000,font-weight:bold;

    %% --- NODOS ---
    
    SRT(("SRT-SISTEMA DE RECAUDACION DE TERCEROS<br/>(Sistema Central)")):::central

    %% Sistemas
    PVTA[("PVTA<br/>(Base de Datos)")]
    SWITCH{{"SWITCH<br/>(Intercambio)"}}
    SIPACON["SIPACON<br/>(Parametria Contable)"]
    SSUC["SSUC<br/>(Estructura)"]
    SAP["SAP<br/>(ERP)"]
 
    
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
    
    CAJERO_RSC -->|"Datos Cupón"| PVTA
    CAJERO_RSC -->|"Cupón Físico"| COBRADORA
    
    COBRADOR_SIN_PC -->|"Cupón y Planilla"| COBRADORA
    COBRADORA -->|"Cupón y Planilla"| DEP_PROV
    
    COBRADOR_PC -->|"Datos Cupón"| SUC_PC
    SUC_PC -->|"Datos Cupón"| SWITCH
    SWITCH -->|"Novedades"| SUC_PC

    %% Relaciones con el SRT
    SRT -->|"Planilla Cobranza"| SUC_PC
    SRT -->|"Maestro Clientes"| PVTA
    PVTA -->|"Planilla Cobranza"| COBRADOR_PC
    PVTA -->|"Datos Cupón"| SWITCH
    
    SWITCH -->|"Cupones del Día"| SRT
    SWITCH -->|"Novedades"| PVTA
    
    SIPACON -->|"Parámetros"| SRT
    SSUC -->|"Jerarquía"| SRT
    
    DEP_PROV -->|"Datos Cupón"| SRT
    SRT -->|"Planilla Recaudación"| DEP_PROV

    %% Salidas y Liquidación
    SRT -->|"Asientos Contables"| SAP
    SAP -->|"Factura"| TESORERIA
    
    TESORERIA -->|"$$ Comisión"| CLIENTE
    CLIENTE -->|"$$ Recaudación"| TESORERIA
    
    SRT -->|"Planilla Liquidación"| LIQUIDADORA
    DEP_PROV -->|"Planilla y Cupones"| LIQUIDADORA
    LIQUIDADORA -->|"Rendición"| DEP_PROV
    LIQUIDADORA -->|"Planilla y Cupones"| CLIENTE



    %% Nota / Leyenda (Usando strings con comillas y saltos de línea estándar)
    subgraph L [Referencia de Acrónimos]
        Leyenda["<b>SIPACON:</b> Sist. Parametría Contable<br/><b>SSUC:</b> Sist. de Sucursales<br/><b>PVTA:</b> Sist. Punto de Venta<br/><b>TESORERIA:</b> Área de Tesorería<br/><b>SAP:</b> Sist. SAP<br/><b>SRT:</b> Sist. Recaudación de Terceros"]
    end
