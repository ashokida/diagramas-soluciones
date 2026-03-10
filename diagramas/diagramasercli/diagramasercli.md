```mermaid
graph LR
    %% Definición del Servidor Central con Markdown
    Principal["`*Servidor Servicio de Clientes* (Principal)`"]

    %% Conexiones a los 7 servidores
    Principal --dblink--> S1[Servidor Paises]  
    Principal <-.txt/FTP.-> S2[Servidor Rastreo & Seguimiento]
    Principal <-.txt/FTP.-> S3[Servidor Telegrafia]
    S4[Servidor P. Venta] -.txt.-> Principal 
    Principal --dblink--> S5[Servidor Sucursales]
    S6[Servidor SAP] -. SAP PO .-> Principal 
    Principal --txt--> S7[Servidor Servicio Internacional]

    %% Estilo para darle un toque visual
    style Principal fill:#f96,stroke:#333,stroke-width:4px
