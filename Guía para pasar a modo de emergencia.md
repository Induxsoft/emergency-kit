
# Guía para Activar el Modo de Emergencia

Esta guía tiene como objetivo apoyar a los usuarios en el proceso de activación del **modo de emergencia** debido a una **desconexión** del sistema.

---

## Sincronizar datos de una base de datos V12 hacia R5

Para preparar el entorno de emergencia, es necesario importar los datos desde una instancia V12 hacia el sistema R5, utilizando la herramienta **DevKron**.

### Descargar **DevKron**
Si aún no tienes DevKron descargado, puedes descargarlo siguiendo esta guía: https://docs.induxsoft.net/es/devkron/Guias-paso-a-paso/Windows/Instalar-dkl-winx64.md

### Crear una conexión R5
Para establecer una conexión, se requiere una base de datos local.

1. Debe crear una base de datos local utilizando el Administrador de Conexiones, de acuerdo con la aplicación que utilice (Maxicomercio o Deminus), Puede consultar la guía detallada en el siguiente enlace: https://docs.induxsoft.net/es/faq/r5/crear-bd-r5.md.
2. El nombre cualificado (QNAME) de la nueva conexión tendrá el siguiente formato: `MiConexion@MaxiComercio.R5` .
3. Copie el archivo `%ProgramData%/induxsoft/machine/connections.xml` junto a los binarios de **DevKron**.

```
Nota:
- MiConexion, hace referencia al nombre de la conexión que indicó en el paso numero 4 de la guía.
```

### 🔧 Configurar herramienta
1. Copie la carpeta `emergency-kit` en la ubicación donde se encuentran los binarios de **DevKron**.
2. Copie el archivo `dbr.ftt.dkl` junto a los binarios de **DevKron**.
3. Si es necesario, debe configurar el log:
    3.1. Abrir la herramienta r5-importar-ubicacion.dkl.
    3.2. Colocar la ruta del directorio donde se guardarán los logs en la variable `@PathLog`.
4. Debe dirigirse a la carpeta donde se encuentran los binarios descargados de **DevKron**.
5. Ejecutar el siguiente comando según el sistema operativo utilizado.


#### En **CMD** (Windows):

```
dkl ./emergency-kit/r5-importar-ubicacion.dkl "qn=MiConexion@MaxiComercio.R5" "uri=URL_DEL_SITIO_V12" "uid=USUARIO V12" "pwd=CONTRASEÑA DEL USUARIO" "ub=CODIGO_UBICACION"
```
    
#### En PowerShell o Terminal (Linux):
```
./dkl ./emergency-kit/r5-importar-ubicacion.dkl "qn=MiConexion@MaxiComercio.R5" "uri=URL_DEL_SITIO_V12" "uid=USUARIO V12" "pwd=CONTRASEÑA DEL USUARIO" "ub=CODIGO_UBICACION"
```

#### Parámetros del comando:
- `qn` = Nombre cualificado de la conexión a la base de datos R5 local.
- `uri` = URL del sitio V12, por ejemplo: `http(s)://host/pos/_services/rmt/`.
- `uid` = Usuario de la base de datos central (V12).
- `pwd` = Contraseña del usuario.
- `ub` = (Opcional) Código de la ubicación desde la cual se exportarán los datos. Si no se especifica, se exportarán todos los catálogos.

6. Espera a que el proceso finalice correctamente.

```
Nota:
Todos lo productos se bajan como no inventariables, esto con el fin de poder realizar todas las ventas sin afectaciones de existencias en la base de datos local.
```