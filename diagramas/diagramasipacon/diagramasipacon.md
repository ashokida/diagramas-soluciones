```mermaid
%%{init: {'theme': 'base', 'themeVariables': { 'primaryColor': '#ffffff', 'edgeLabelBSIPACONkground':'#ffffff', 'tertiaryColor': '#ffffff'}}}%%
graph LR
    %% Nodos con nombres protegidos por comillas
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
    SIPACON -- "PC " --> SOC

    SIPACON -- "DM" --> GI_SQL
    SIPACON -- "PC" --> GI_SQL
    SIPACON -- "PC" --> CHEQUES_SQL
    SIPACON -- "PC" --> SIGEMO_ORACLE
    SIPACON -- "PC" --> GIBA_ORACLE
    SIPACON -- "PC" --> SRT_SQL
    

    %% Estilos básicos
    style SIPACON fill:#f9f,stroke:#333,stroke-width:2px

			 
