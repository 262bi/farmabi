# oltp-mysql

Origen transaccional MySQL del proyecto `farmabi`, usado desde S1 para explorar
el caso de negocio (ver `docs/sesiones/S01_Fundamentos_BI_Problema_Negocio.md`).
Las tablas de este origen son las mismas que referencia la matriz
pregunta-fuente de S1: `clientes`, `vendedores`, `familias`, `categorias`,
`productos`, `pedidos`, `pedido_detalles`.

## Configuración clave

- contenedor: `farmabi-oltp-mysql`
- puerto host: `53306`
- base: `farma_oltp_db`
- usuario root: `root`
- password root: `root`
- compose: `compose.yml`

## Operación mínima

```powershell
cd oltp-mysql
docker compose up -d
docker compose ps
```

Acceso opcional:

```powershell
docker exec -it farmabi-oltp-mysql mysql -uroot -proot farma_oltp_db
```

## Documentación

Las guías de clase están en [`../docs/sesiones/`](../docs/sesiones/).
