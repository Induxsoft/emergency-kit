
# Consideraciones

- En **modo de emergencia**, únicamente se permite realizar ventas desde el módulo de **Punto de Venta (POS)**.

- Cada punto de venta (**POS**) debe tener configurada su **propia serie**, la cual **no debe ser utilizada por la central (V12)**, `Este punto es muy importante`.

- No se debe utilizar el módulo de **Backoffice** para insertar o actualizar información durante este modo.
- **No es posible cancelar ventas (tickets)** mientras el sistema se encuentra en modo de emergencia.

- **No se pueden realizar devoluciones de ventas (tickets)** durante este estado.

- Al exportar las ventas, **solo se enviarán aquellas que hayan sido procesadas** correctamente.

- Todas las operaciones administrativas y de gestión deben realizarse **exclusivamente desde el Backoffice de V12**.

- Todos los productos se descargan como **no inventariables**, con el fin de permitir la realización de ventas sin generar afectaciones en las existencias de la base de datos local.

- Los productos registrados en la central deben contar con existencias suficientes para permitir la salida de inventario correspondiente a las ventas importadas mediante la herramienta del **kit de emergencia**.

- Al subir las ventas desde la base de datos local, si existe un corte de caja abierto, este también se transferirá junto con las ventas. En caso de que en la base de datos central ya haya un corte de caja abierto, se generará una situación en la que **coexistirán dos cortes de caja abiertos**, en la cual puede cerrarlos desde el punto de venta.
