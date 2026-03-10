```mermaid

graph TD
    %% Definición de Estilos
    classDef nucleus fill:#f9f,stroke:#333,stroke-width:2px;
    classDef external fill:#e1f5fe,stroke:#01579b,stroke-width:1.5px;

    %% Nodo Central
    SGOJ(("S.G.O.J.<br/>(Sistema de Gestion de Oficios Judiciales)")):::nucleus

    %% Entidades Externas
    JUDGADOS["Juzgados (Poder Judicial)"]:::external
    SUCURSALES["Sucursales (Puntos de Atención)"]:::external
    MESA["Mesa de Entrada / Archivo"]:::external
    RS["Sistema Rastreo & Seguimiento (Satélite)"]:::external
    PVTA["Sistema Punto de Venta (Base de Datos)"]:::external

    %% Flujos de Información
    JUDGADOS -- "Oficios Judiciales" --> SGOJ
    SGOJ -- "Respuestas Impresas" --> JUDGADOS

    SGOJ -- "Pedidos de información (ASCII)" --> SUCURSALES
    SUCURSALES -- "Respuestas automáticas" --> SGOJ

    SGOJ -- "Pedidos vía FTP" --> RS
    RS -- "Recepción de respuestas" --> SGOJ

    MESA -- "Oficios físicos (Carga manual)" --> SGOJ
    SGOJ -- "Guía para archivo" --> MESA

    PVTA -- "Carga diaria (ASCII)" --> SGOJ
    SGOJ -. "Validación/Cotejo" .-> PVTA

    %% Subproceso representativo
    subgraph Gestion_Interna [Procesamiento Interno]
        SGOJ
    end
