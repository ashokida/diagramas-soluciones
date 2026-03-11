```mermaid

%%{init: {'theme': 'neutral', 'themeVariables': { 'primaryColor': '#ffffff', 'edgeLabelBackground':'#ffffff'}}}%%
graph LR
    %% Definición de Nodos con fondo blanco
    T_AND_T("Track&Trace")
    MELI("MELI - WS REST")
    DS_ECOM["<<datastore>><br/>ECOM (SqlServer)"]
    PI_PN["PI - Plataforma de Notificacion"]
    JBOSS["JBoss"]
    DRUPAL["Drupal"]

    %% Conexiones (Bordes y flechas en negro por defecto en tema neutral)
    T_AND_T -.-> PI_PN
    DS_ECOM -.-> JBOSS
    PI_PN -.->|SOAP| DRUPAL
    DRUPAL -.->|REST| MELI
    JBOSS -.-> DS_ECOM
    JBOSS -.->|OK| PI_PN
    PI_PN -.->|REST| MELI

    %% Estilos de Nodos (Fondo blanco, bordes negros, letras negras)
    style T_AND_T fill:#fff,stroke:#000,color:#000
    style MELI fill:#fff,stroke:#000,color:#000
    style DS_ECOM fill:#fff,stroke:#000,color:#000
    style PI_PN fill:#fff,stroke:#000,color:#000
    style JBOSS fill:#fff,stroke:#000,color:#000
    style DRUPAL fill:#fff,stroke:#000,color:#000

    %% Estilos de Líneas
    %% Todas las líneas normales en negro (stroke:#000)
    linkStyle 0,1,2,3,4,5 stroke:#000,stroke-width:2px,stroke-dasharray: 5 5
    
    %% Mantenemos la línea de MELI destacada pero en negro sólido o más gruesa 
    %% (Si la preferís negra, cambiá stroke:#F44336 por #000)
    linkStyle 6 stroke:#000,stroke-width:4px,stroke-dasharray: 5 5
