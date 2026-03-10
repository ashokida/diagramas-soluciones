```mermaid

graph TD
    %% Definición de Estilos
    classDef nucleus fill:#f9f,stroke:#333,stroke-width:2px;
    classDef external fill:#e1f5fe,stroke:#01579b,stroke-width:1.5px;

    %% Nodo Central
    AGOJ(("A.G.O.J.<br/>(Administración de Oficios)")):::nucleus

    %% Entidades Externas
    JUDGADOS["Juzgados (Poder Judicial)"]:::external
    SUCURSALES["Sucursales (Puntos de Atención)"]:::external
    MESA["Mesa de Entrada / Archivo"]:::external
    TT["Sistema T&T (Satélite)"]:::external
    MOSAIC["Sistema MOSAIC (Base de Datos)"]:::external

    %% Flujos de Información
    JUDGADOS -- "Oficios Judiciales" --> AGOJ
    AGOJ -- "Respuestas Impresas" --> JUDGADOS

    AGOJ -- "Pedidos de información (ASCII)" --> SUCURSALES
    SUCURSALES -- "Respuestas automáticas" --> AGOJ

    AGOJ -- "Pedidos vía FTP" --> TT
    TT -- "Recepción de respuestas" --> AGOJ

    MESA -- "Oficios físicos (Carga manual)" --> AGOJ
    AGOJ -- "Guía para archivo" --> MESA

    MOSAIC -- "Carga diaria (ASCII)" --> AGOJ
    AGOJ -. "Validación/Cotejo" .-> MOSAIC

    %% Subproceso representativo
    subgraph Gestion_Interna [Procesamiento Interno]
        AGOJ
    end
