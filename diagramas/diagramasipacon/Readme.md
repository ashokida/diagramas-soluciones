```mermaid
%%{init: {'theme': 'base', 'themeVariables': { 'primaryColor': '#ffffff', 'edgeLabelBackground':'#ffffff', 'tertiaryColor': '#ffffff'}}}%%
graph LR
    %% Nodos principales
    SSUC_TXT["SSUC (TXT)"]
    PVTA_TXT["PVTA (TXT)"]
    TESORERIA_TXT["TESORERIA (TXT)"]
    SAP_TXT["SAP (TXT)"]
    SOC["SOC"]
    SIPACON(("SIST. PARAMETRIA CONTABLE (SIPACON)"))
    GI_SQL["GI (SQL)"]
    CHEQUES_SQL["CHEQUES (SQL)"]
    SIGEMO_ORACLE["SIGEMO (ORACLE)"]
    GIBA_ORACLE["GIBA (ORACLE)"]
    SRT_SQL["SRT (SQL)"]

    %% Conexiones
    SSUC_TXT -- "DM" --> SOC
    PVTA_TXT -- "DM" --> SOC
    PVTA_TXT -- "DM" --> SIPACON
    SAP_TXT -- "DM" --> SOC
    SAP_TXT -- "DM" --> SIPACON
    TESORERIA_TXT -- "DM" --> SIPACON
    SOC -- "DM" --> SIPACON
    SIPACON -- "PC" --> SOC

    SIPACON -- "DM" --> GI_SQL
    SIPACON -- "PC" --> GI_SQL
    SIPACON -- "PC" --> CHEQUES_SQL
    SIPACON -- "PC" --> SIGEMO_ORACLE
    SIPACON -- "PC" --> GIBA_ORACLE
    SIPACON -- "PC" --> SRT_SQL

    %% Estilos
    style SIPACON fill:#f9f,stroke:#333,stroke-width:2px
    style Leyenda fill:#fffef0,stroke:#d4d4d4,stroke-dasharray: 5 5

    %% Nota / Leyenda (Usando strings con comillas y saltos de línea estándar)
    subgraph L [Referencia de Acrónimos]
        Leyenda["<b>SIPACON:</b> Sist. Parametría Contable<br/><b>SSUC:</b> Sist. de Sucursales<br/><b>PVTA:</b> Sist. Punto de Venta<br/><b>TESORERIA:</b> Área de Tesorería<br/><b>SAP:</b> Sistema SAP<br/><b>SOC:</b> Sist. Operaciones de Caja<br/><b>GI:</b> Gastos Internos<br/><b>CHEQUES:</b> Gestión de Cheques<br/><b>SIGEMO:</b> Gestión Monetaria<br/><b>GIBA:</b> Giros Bancarios<br/><b>SRT:</b> Recaudación Terceros<br/><b>DM:</b> Datos Maestros<br/><b>PC:</b> Parametría Contable"]
    end
