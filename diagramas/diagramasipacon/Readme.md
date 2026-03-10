```mermaid
%%{init: {'theme': 'base', 'themeVariables': { 'primaryColor': '#ffffff', 'edgeLabelBackground':'#ffffff', 'tertiaryColor': '#ffffff'}}}%%
graph LR
    %% Nodos con nombres protegidos por comillas
    SAS_TXT["SAS (TXT)"]
    MOSAIC_TXT["MOSAIC (TXT)"]
    TESORERIA_TXT["TESORERIA (TXT)"]
    SAP_TXT["SAP (TXT)"]
    PDC_AUTO["PDC_AUTO"]
    AC(("ASIGNACION CONTABLE (AC)"))
    GME_SQL["GME (SQL)"]
    POL_PCT_CHQ_SQL["POL, PCT, CHQ (SQL)"]
    SIMON_PCT_ORACLE["SIMON PCT (ORACLE)"]
    ADMITEL_ORACLE["ADMITEL (ORACLE)"]
    GIROS_TXT_ORACLE["GIROS txt (ORACLE)"]
    SACCT_SQL["SACCT (SQL)"]
    IFS_SQL["IFS (SQL)"]

    %% Conexiones
    SAS_TXT -- "MAESTROS (5)" --> PDC_AUTO
    MOSAIC_TXT -- "MAESTROS (9)" --> PDC_AUTO
    MOSAIC_TXT -- "MAESTROS (9)" --> AC
    SAP_TXT -- "MAESTROS (5)" --> PDC_AUTO
    SAP_TXT -- "MAESTROS (9)" --> AC
    TESORERIA_TXT -- "MAESTRO" --> AC

    PDC_AUTO -- "MAESTROS (2)" --> AC
    AC -- "CONTABLE (27)" --> PDC_AUTO

    AC -- "MAESTROS (4)" --> GME_SQL
    AC -- "CONTABLE" --> GME_SQL
    AC -- "CONTABLE (10)" --> POL_PCT_CHQ_SQL
    AC -- "CONTABLE (7)" --> SIMON_PCT_ORACLE
    AC -- "CONTABLE (4)" --> ADMITEL_ORACLE
    AC -- "CONTABLE (2)" --> GIROS_TXT_ORACLE
    AC -- "CONTABLE (8)" --> SACCT_SQL
    AC -- "CONTABLE (2)" --> IFS_SQL

    %% Estilos básicos
    style AC fill:#f9f,stroke:#333,stroke-width:2px
