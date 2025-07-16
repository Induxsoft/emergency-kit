
# Guía para Regresar al Modo Normal

Esta guía tiene como objetivo ayudar a los usuarios a pasar del **modo de emergencia** al **modo normal**, sincronizando nuevamente los datos hacia el sistema central.

---

## Sincronizar datos de una base de datos R5 hacia V12

Para restaurar el funcionamiento normal del sistema, es necesario **enviar los datos generados en modo de emergencia desde R5 hacia V12**, utilizando la herramienta **DevKron**.

---

### Descargar **DevKron**
Si aún no tienes DevKron descargado, puedes descargarlo siguiendo esta guía: https://docs.induxsoft.net/es/devkron/Guias-paso-a-paso/Windows/Instalar-dkl-winx64.md

### 🔧 Configurar herramienta

1. Copie la carpeta `emergency-kit` en la misma ubicación donde se encuentran los binarios de **DevKron**.
2. Copie el archivo `dbr.ftt.dkl` junto a los binarios de **DevKron**.
3. Si es necesario, debe configurar el log:
    3.1. Abrir la herramienta r5-importar-ubicacion.dkl.
    3.2. Colocar la ruta del directorio donde se guardarán los logs en la variable `@PathLog`.
4. Diríjase a la carpeta donde está **DevKron** descargado.
5. Ejecutar el siguiente comando según el sistema operativo utilizado.
    
#### En **CMD** (Windows):
```
dkl ./emergency-kit/r5-enviar-ventas.dkl "qn=MY_QNAME" "uri=URL_DEL_SITIO_V12" "uid=USUARIO V12" "pwd=CONTRASEÑA DEL USUARIO" "ub=CODIGO_UBICACION" "i=AAAA-MM-DD"
```

#### En PowerShell o Terminal (Linux):

```
./dkl ./emergency-kit/r5-enviar-ventas.dkl "qn=MY_QNAME" "uri=URL_DEL_SITIO_V12" "uid=USUARIO V12" "pwd=CONTRASEÑA DEL USUARIO" "ub=CODIGO_UBICACION" "i=AAAA-MM-DD"
```

#### Parámetros del comando:
- `qn` = Nombre cualificado de la conexión a la base de datos R5.
- `uri` = URL del sitio V12, por ejemplo: `http(s)://host/pos/_services/rmt/`.
- `uid` = Usuario con acceso a la base de datos central (V12).
- `pwd` = Contraseña del usuario.
- `ub` = (Opcional) Código de la ubicación.
- `i` = (Opcional) Fecha de inicio para la exportación de ventas. Si no se especifica, se enviarán `todas las ventas pendientes`.

6. Espere a que el proceso finalice correctamente.

---

### No permitir salida de inventario
Para evitar que el servicio de POS realice salidas de inventario, siga estos pasos:

- Ingrese al módulo de **Variables globales**.
- Seleccione la categoría **Punto de venta**.
- Localice la variable global **pos_afectar_existencias (Afectar existencias al importar ventas)** establezca su valor en **No**.