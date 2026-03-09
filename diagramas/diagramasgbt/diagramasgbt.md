## 🗺️ Diagrama de Contexto del Sistema
Este diagrama representa el ecosistema de la **Gestión de Beneficios por Tarjeta ** y cómo interactúan los diversos datastores y actores con el núcleo del sistema

```mermaid

flowchart TD

    %% Entidades y Procesos
    SGBT((Sistema de Gestion de Beneficios por Tarjeta))
    EMP[Empresas]
    ARC[Area de control]
    SITA([Tarjetera Sistema TARJ])
    FTP([FTP TARJ])
    
    %% Bases de Datos
    DB_SGBT[(SGBT BD)]
    DB_SCON[(SCON BD)]
    DB_SSUC[(SSUC BD)]
    DB_SAP[(SAP BD)]

    %% Flujos de Datos
    EMP -- Solicitud Alta Cuenta --> SGBT
    SGBT -- Confirmación Alta --> EMP
    EMP -- Solicitud Adicionales --> SGBT
    
    SGBT -- Consultas Seguimiento --> ARC
    SGBT -- Informes Estadísticas --> ARC
    
    DB_SCON -. Modelos Contables TP .-> SGBT
    DB_SSUC -. Datos Sucursales .-> SGBT
    SGBT -- Batch Imput Asientos --> DB_SAP
    
    SGBT -- Registrar Cuentas/Adicionales --> DB_SGBT
    DB_SGBT -- Consumo Liquidación Compensación --> SGBT
    
    SITA -- Respuesta Cuenta --> SGBT
    SITA -- Respuesta Adicional --> SGBT
    SGBT -- Alta Cuenta --> FTP
    SGBT -- Alta Adicional --> FTP
    SGBT -- Cargas / Descargas --> FTP
    
    FTP -- Saldo Cuenta --> SGBT
    FTP -- Confirmacion Altas/Cargas/Modificacion Beneficiario --> SGBT
    FTP -. Archivos Diarios / Mensual .-> SGBT


%% Nota / Leyenda de Acrónimos CORREGIDA
    Leyenda["<b>SGBT:</b> Sist. de Gestión de Beneficios por Tarjeta<br/><b>SCON:</b> Sist. Parametría Contable<br/><b>SSUC:</b> Sist. de Sucursales<br/><b>SITA:</b> Sist. de Tarjetera<br/><b>TARJ:</b> Empresa administradora de medios de pagos"]
