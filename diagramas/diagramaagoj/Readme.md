´´´mermaid

graph TD
    %% Estilo del núcleo central
    classDef nucleus fill:#f9f,stroke:#333,stroke-width:2px,color:black, rx:10, ry:10;
    
    %% Definición del Sistema Central
    AGOJ((Sistema A.G.O.J.<br/>Administración de Oficios Judiciales)):::nucleus

    %% Definición de Entidades Externas (Cajas)
    JUDGADOS[Juzgados (Poder Judicial)]:::external
    SUCURSALES[Sucursales (Puntos de Atención)]:::external
    MESA[Mesa de Entrada / Archivo]:::external
    T&T[Sistema T&T (Satélite/Comunicaciones)]:::external
    MOSAIC[Sistema MOSAIC (Base de Datos)]:::external

    %% Interacciones (Flujos de Información)
    AGOJ --"Envío de Respuestas Impresas"--> JUDGADOS
    JUDGADOS --"Solicitud de Oficios Judiciales (Originales)"--> AGOJ

    SUCURSALES --"Generación automática de Respuestas"--> AGOJ
    AGOJ --"Envío de Pases (Pedidos de Información)"--> SUCURSALES

    AGOJ --"Pedidos de Información (vía T&T)"--> T&T
    T&T --"Recepción automática de Respuestas"--> AGOJ

    MESA --"Recepción de Oficios Físicos (Carga Manual)"--> AGOJ
    AGOJ --"Datos de Guía para Archivo (Anual/Trienal)"--> MESA

    MOSAIC --"Carga automática diaria de datos (Archivos ASCII)"--> AGOJ
    AGOJ --"Cotejo de datos con documentación física"--> MOSAIC

    %% Subprocesos Internos Clave (Indicados en el flujo)
    subgraph Procesos Internos de A.G.O.J.
    I(Ingreso/Gestión de Pases)
    P(Procesamiento/Carga de Piezas)
    O(Salida/Gestión de Alertas)
    end
    
    I -.-> AGOJ
    P -.-> AGOJ
    O -.-> AGOJ

    %% Estilos de las entidades externas
    classDef external fill:#e1f5fe,stroke:#01579b,stroke-width:1.5px,rx:5,ry:5,color:black;
