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

    %% Nota / Leyenda  
    Leyenda["<b>SIPACON:</b> Sistema de Parametría Contable<br/> 
	         <b>SSUC:</b> Sistema de Sucursales<br/> 
			 <b>PVTA:</b> Sistema de Punto de Venta<br/> 
			 <b>TESORERIA:</b> Area de Tesoreria<br/> 
			 <b>SAP:</b> Sistema SAP<br/> 
			 <b>SOC:</b> Sistema de Operaciones de Caja<br/> 
			 <b>GI:</b> Sistema de Gastos Internos<br/> 
			 <b>CHEQUES:</b> Sistema de Gestion de Cheques<br/> 
			 <b>SIGEMO:</b> Sistema de Gestion Monetaria<br/> 
			 <b>GIBA:</b> Sistema de Giros Bancarios<br/> 
			 <b>SRT:</b> Sistema de Recaudacion para Terceros<br/> 
			 <b>DM:</b> Datos maestros<br/> 
			 <b>PC:</b> Parametria Contable<br/>]
			 
