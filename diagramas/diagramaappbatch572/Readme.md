```mermaid

%%{init: {'theme': 'neutral', 'themeVariables': { 'primaryColor': '#ffffff', 'edgeLabelBackground':'#ffffff'}}}%%
graph TD
    %% Entidades Externas
    AFIP["<b>ARCA (SiRADIG)</b><br/>Proveedor de Datos de Origen"]
    SAP_HCM["<b>SISTEMA SAP HCM</b><br/>Destino de Cargas Familiares"]
    DENARIUS["<b>SISTEMA DENARIUS</b><br/>Destino de Deducciones y Retenciones"]
    LIQUIDADOR["<b>SECTOR DE LIQUIDACIÓN DE HABERES</b><br/>Administrador y Controlador"]

    %% Proceso Principal (Contenedor)
    subgraph APP [APLICACIÓN BATCH F572WEB - Proceso en C]
        direction LR
        P1["1. REGISTRO DE EXCEPCIONES<br/>Filtrado de Casos Especiales"]
        P2["2. TRANSFORMACIÓN<br/>Normalización de Códigos AFIP"]
        P3["3. CONVERSIÓN<br/>Traduce a formatos SAP/DENARIUS"]
        P4["4. GENERACIÓN<br/>Crea archivos de salida (.txt)"]
        
        P1 --> P2 --> P3 --> P4
    end

    %% Flujos de Datos Externos e Internos
    AFIP -- "Declaraciones Juradas (XML)" --> P1
    
    P4 -- "Archivo Final Normalizado (.txt)" --> SAP_HCM
    P4 -- "Archivo con Montos de Deducciones (.txt)" --> DENARIUS
    
    P1 -- "Reportes de Control, Excepciones y Logs" --> LIQUIDADOR
    LIQUIDADOR -- "Tablas de Conversión (.txt)" --> P2

    %% Estilos de Nodos
    style AFIP fill:#fff,stroke:#000,stroke-width:2px
    style SAP_HCM fill:#fff,stroke:#000,stroke-width:2px
    style DENARIUS fill:#fff,stroke:#000,stroke-width:2px
    style LIQUIDADOR fill:#fff,stroke:#000,stroke-width:2px
    style APP fill:#f9f9f9,stroke:#333,stroke-dasharray: 5 5
    
    style P1 fill:#fff,stroke:#000
    style P2 fill:#fff,stroke:#000
    style P3 fill:#fff,stroke:#000
    style P4 fill:#fff,stroke:#000
