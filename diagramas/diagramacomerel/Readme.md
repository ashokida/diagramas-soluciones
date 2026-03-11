```mermaid

graph LR
    %% Configuración de Estilo Global para alto contraste
    classDef default fill:#ffffff,stroke:#000000,stroke-width:2px,color:#000000,font-weight:bold;

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

