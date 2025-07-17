
# Consideraciones

- En **modo de emergencia**, únicamente se permite realizar ventas(Ticket) desde el módulo de **Punto de Venta (POS)**.

- Cada punto de venta (**POS**) debe tener configurada su **propia serie**, la cual **no debe ser utilizada por la central (V12)**, `Este punto es muy importante`.

- No se debe utilizar el módulo de **Backoffice** para insertar o actualizar información durante este modo.
- **No es posible cancelar ventas (tickets)** mientras el sistema se encuentra en modo de emergencia.

- **No se pueden realizar devoluciones de ventas (tickets)** durante este estado.

- Al exportar las ventas, **solo se enviarán aquellas que hayan sido procesadas** correctamente.

- Todas las operaciones administrativas y de gestión deben realizarse **exclusivamente desde el Backoffice de V12**.

- Todos los productos se descargan como **no inventariables**, con el fin de permitir la realización de ventas sin generar afectaciones en las existencias de la base de datos local.

- Los productos registrados en la central deben contar con existencias suficientes para permitir la salida de inventario correspondiente a las ventas importadas mediante la herramienta del **kit de emergencia**.

- No se podrá hacer retiros en el punto de venta.

- Antes de subir todas las ventas y regresar al modo normal debe realizar el corte de caja, `Este punto es muy importante`.
