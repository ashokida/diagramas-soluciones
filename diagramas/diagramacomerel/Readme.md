```mermaid
graph LR
    %% Definición de Nodos
    T_AND_T("Track&Trace")
    MELI("MELI - WS REST")
    DS_ECOM["<<datastore>><br/>ECOM (SqlServer)"]
    PI_PN["PI - Plataforma de Notificacion"]
    JBOSS["JBoss"]
    DRUPAL["Drupal"]

    %% Conexiones
    T_AND_T -.-> PI_PN
    DS_ECOM -.-> JBOSS
    PI_PN -.->|SOAP| DRUPAL
    DRUPAL -.->|REST| MELI
    JBOSS -.-> DS_ECOM
    JBOSS -.->|OK| PI_PN
    PI_PN -.->|REST| MELI

    %% Estilos de Nodos
    style T_AND_T fill:#FEFBDA,stroke:#C6B89A,stroke-width:1px
    style MELI fill:#FEFBDA,stroke:#C6B89A,stroke-width:1px
    style DS_ECOM fill:#DDF3F1,stroke:#B5D4E1,stroke-width:1px
    style PI_PN fill:#DDF3F1,stroke:#B5D4E1,stroke-width:1px
    style JBOSS fill:#DDF3F1,stroke:#B5D4E1,stroke-width:1px
    style DRUPAL fill:#DDF3F1,stroke:#B5D4E1,stroke-width:1px

    %% Estilos de Líneas (Colores y grosores)
    linkStyle 0,1,2,3,4,5 stroke:#607D8B,stroke-width:2px,stroke-dasharray: 5 5
    linkStyle 6 stroke:#F44336,stroke-width:4px,stroke-dasharray: 5 5
