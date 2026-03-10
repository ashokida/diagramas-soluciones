```mermaid
%%{init: {'theme': 'base', 'themeVariables': { 'primaryColor': '#ffffff', 'edgeLabelBackground':'#ffffff', 'tertiaryColor': '#ffffff'}}}%%
graph LR
%% Nodos del Diagrama
    SAS_TXT([SAS (TXT)])
    MOSAIC_TXT([MOSAIC (TXT)])
    TESORERIA_TXT([TESORERIA (TXT)])
    SAP_TXT([SAP (TXT)])
    PDC_AUTO([PDC_AUTO])
    AC(ASIGNACION CONTABLE (AC))
    GME_SQL([GME (SQL)])
    POL_PCT_CHQ_SQL([POL, PCT, CHQ (SQL)])
    SIMON_PCT_ORACLE([SIMON PCT (ORACLE)])
    ADMITEL_ORACLE([ADMITEL (ORACLE)])
    GIROS_txt_ORACLE([GIROS txt (ORACLE)])
    SACCT_SQL([SACCT (SQL)])
    IFS_SQL([IFS (SQL)])

%% Conexiones con etiquetas
    %% Entradas a PDC_AUTO y AC
    SAS_TXT -- MAESTROS (5) --> PDC_AUTO
    MOSAIC_TXT -- MAESTROS (9) --> PDC_AUTO
    MOSAIC_TXT -- MAESTROS (9) --> AC
    SAP_TXT -- MAESTROS (5) --> PDC_AUTO
    SAP_TXT -- MAESTROS (9) --> AC
    TESORERIA_TXT -- MAESTRO --> AC

    %% Interacciones entre PDC_AUTO y AC
    PDC_AUTO -->|MAESTROS (2)| AC
    AC -->|CONTABLE (27)| PDC_AUTO

    %% Salidas de AC
    AC -->|MAESTROS(4)| GME_SQL
    AC -->|CONTABLE| GME_SQL
    AC -->|CONTABLE (10)| POL_PCT_CHQ_SQL
    AC -->|CONTABLE (7)| SIMON_PCT_ORACLE
    AC -->|CONTABLE (4)| ADMITEL_ORACLE
    AC -->|CONTABLE (2)| GIROS_txt_ORACLE
    AC -->|CONTABLE (8)| SACCT_SQL
    AC -->|CONTABLE (2)| IFS_SQL

%% Estilos para simular óvalos
    classDef oval rx:20,ry:20,fill:#fff,stroke:#333,stroke-width:1px;
    classDef rect fill:#fff,stroke:#333,stroke-width:1px;

    class SAS_TXT,MOSAIC_TXT,TESORERIA_TXT,SAP_TXT,PDC_AUTO,GME_SQL,POL_PCT_CHQ_SQL,SIMON_PCT_ORACLE,ADMITEL_ORACLE,GIROS_txt_ORACLE,SACCT_SQL,IFS_SQL rect;
    class AC oval;
