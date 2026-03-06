## 🗺️ Diagrama de Contexto del Sistema
Este diagrama representa el ecosistema de **Tarjeta Prepaga Social** y cómo interactúan los diversos datastores y actores con el núcleo del sistema.

```mermaid
graph TD
    TPS((Tarjeta Prepaga Social))

    %% Sistemas Externos / Datastores
    TPS --- SAS[datastore: SAS]
    TPS --- Simon[datastore: Simon]
    TPS --- SAP[datastore: SAP]
    TPS --- AC[datastore: AC]
    TPS --- TT[datastore: T&T]
    TPS --- CABAL[datastore: CABAL]
    TPS --- ANSES[ANSES]
    TPS --- AdmSimon[Adm Beneficiario Simon]

    %% Actores / Roles
    Sucursales((Sucursales)) --- TPS
    Contabilidad((Contabilidad Sucursales)) --- TPS
    Impuestos((Impuestos)) --- TPS
    Facturacion((Facturación)) --- TPS
    Ventas((Consulta de Ventas)) --- TPS
    AdminSist((Administrador Sist)) --- TPS
    GDBCtrl((GDBP Control)) --- TPS
    PAS((PAS)) --- TPS
    GDBPGestor((GDBP Gestor)) --- TPS
    SucursalBO((Sucursal/Back-Office)) --- TPS
    OperadorBP((Operador Banca Postal)) --- TPS
