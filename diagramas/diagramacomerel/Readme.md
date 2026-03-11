```mermaid
%%{init: {
  'theme': 'base',
  'themeVariables': {
    'primaryTextColor': '#222',
    'lineColor': '#444'
  },
  'flowchart': {
    'nodeSpacing': 50,
    'rankSpacing': 70
  }
}%%}

graph LR
    %% Definición de Nodos
    %% Estilo redondeado amarillo pálido
    T_AND_T("Track&Trace")
    MELI("MELI - WS REST")

    %% Estilo rectangular azul/celeste pálido
    DS_ECOM["<<datastore>><br/>ECOM (SqlServer)"]
    PI_PN["PI - Plataforma de<br/>Notificacion"]
    JBOSS["JBoss"]
    DRUPAL["Drupal"]

    %% Definición de Conexiones y Estilos de Línea
    %% Línea punteada simple con flecha simple
    T_AND_T -.-> PI_PN
    DS_ECOM -.-> JBOSS
    PI_PN -.->|SOAP| DRUPAL
    DRUPAL -.->|REST| MELI

    %% Línea punteada doble (con flecha a ambos lados)
    JBOSS <==.=> DS_ECOM

    %% Línea punteada simple con etiqueta 'OK'
    JBOSS -.->|OK| PI_PN

    %% Línea ROJA gruesa punteada con flecha gruesa y etiqueta 'REST'
    PI_PN -..-x|REST| MELI

    %% Estilos de Nodos (Colores de fondo y bordes)
    %% Nodos Amarillos (T&T, MELI)
    style T_AND_T fill:#FEFBDA,stroke:#C6B89A,stroke-width:1px,rx:15,ry:15
    style MELI fill:#FEFBDA,stroke:#C6B89A,stroke-width:1px,rx:15,ry:15

    %% Nodos Celestes (ECOM, PI, JBoss, Drupal)
    style DS_ECOM fill:#DDF3F1,stroke:#B5D4E1,stroke-width:1px
    style PI_PN fill:#DDF3F1,stroke:#B5D4E1,stroke-width:1px
    style JBOSS fill:#DDF3F1,stroke:#B5D4E1,stroke-width:1px
    style DRUPAL fill:#DDF3F1,stroke:#B5D4E1,stroke-width:1px

    %% Estilos específicos de líneas (para coincidir con la imagen)
    %% Hacemos la línea de T&T y PI más gruesa y gris
    linkStyle 0 stroke:#607D8B,stroke-width:2px,stroke-dasharray: 5 5;
    %% Hacemos la línea doble de JBoss y ECOM gris
    linkStyle 1 stroke:#607D8B,stroke-width:2px,stroke-dasharray: 5 5;
    %% Hacemos la línea de SOAP gris
    linkStyle 2 stroke:#607D8B,stroke-width:2px,stroke-dasharray: 5 5;
    %% Hacemos la línea de REST (Drupal) gris
    linkStyle 3 stroke:#607D8B,stroke-width:2px,stroke-dasharray: 5 5;
    %% Hacemos la línea simple de JBoss y DS gris
    linkStyle 4 stroke:#607D8B,stroke-width:2px,stroke-dasharray: 5 5;
    %% Hacemos la línea de 'OK' gris
    linkStyle 5 stroke:#607D8B,stroke-width:2px,stroke-dasharray: 5 5;

    %% ESTILO CLAVE: Línea ROJA punteada gruesa
    %% stroke:#F44336 (rojo), stroke-width:4px (grueso), stroke-dasharray: 5 5 (punteado)
    linkStyle 6 stroke:#F44336,stroke-width:4px,stroke-dasharray: 5 5;
```
