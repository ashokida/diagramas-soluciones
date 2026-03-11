```mermaid

graph LR
    %% Configuración de Estilo Global para alto contraste
    classDef default fill:#ffffff,stroke:#000000,stroke-width:2px,color:#000000,font-weight:bold;

    %% Definición de Nodos con fondo blanco
    R_Y_S("Rastreo&Seguimiento (R&S)")
    PCEL("PCEL - WS REST")
    BD_COMER["<<datastore>><br/>BD_COMER (SqlServer)"]
    SN["PI - Servicio de Notificacion"]
    JBOSS["JBoss"]
    DRUPAL["Drupal"]

    %% Conexiones (Bordes y flechas en negro por defecto en tema neutral)
    R_Y_S -.-> SN
    BD_COMER -.-> JBOSS
    SN -.->|SOAP| DRUPAL
    DRUPAL -.->|REST| PCEL
    JBOSS -.-> BD_COMER
    JBOSS -.->|OK| SN
    SN -.->|REST| PCEL

    %% Nota / Leyenda
    subgraph L [Referencia de Acrónimos]
        Leyenda["<b>PCEL:</b> Plataforma de Comercio Electrónico<br/><b>BD_COMER:</b> Base de datos MSSQL<br/><b>SN:</b> Servicio de Notificaciones"]
    end
