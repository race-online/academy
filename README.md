# Tienda de coches — Assetto Corsa Evo

Sistema completo: Google Sheet como base de datos + Google Apps Script como
motor de compra/venta/carreras + una Web App con interfaz bonita para tus
pilotos.

## Archivos incluidos
- `Tienda_AC_Evo_Plantilla.xlsx` → plantilla de la base de datos (Coches, Pilotos, Propiedad, Historial, Resultados_Carreras, Config).
- `Code.gs` → backend (Google Apps Script).
- `Index.html` → interfaz web que ven los pilotos.

## Paso 1 — Sube la plantilla a Google Sheets
1. Sube `Tienda_AC_Evo_Plantilla.xlsx` a tu Google Drive.
2. Clic derecho → **Abrir con → Google Sheets**. Se convierte automáticamente a Sheet nativo.
3. Rellena las celdas en **amarillo**: tus coches en la pestaña `Coches` y tus pilotos en `Pilotos` (borra las filas de ejemplo).

## Paso 2 — Añade el script
1. En el Sheet: menú **Extensiones → Apps Script**.
2. Borra el contenido de `Code.gs` que aparece por defecto y pega el contenido del archivo `Code.gs` que te he generado.
3. Crea un archivo nuevo: **Archivo → Nuevo → Archivo HTML**, llámalo exactamente `Index` (sin extensión, Apps Script añade `.html` solo) y pega el contenido de `Index.html`.
4. Guarda el proyecto (icono de disquete).

## Paso 3 — Publica la Web App
1. En el editor de Apps Script: **Implementar → Nueva implementación**.
2. Tipo: **Aplicación web**.
3. "Ejecutar como": **Yo (tu cuenta)**.
4. "Quién tiene acceso": elige **Cualquier usuario** (si quieres que cualquiera con el enlace entre sin cuenta de Google) o **Cualquier usuario de tu organización**.
5. Clic en **Implementar**, autoriza los permisos que pida Google (accede a tu propio Sheet) y copia la **URL de la aplicación web**. Esa es la URL que compartes con tus pilotos.

## Paso 4 — Prueba
- Abre la URL: verás la tienda, la lista de pilotos y el historial.
- Selecciona un piloto arriba a la derecha ("Soy: ...") y prueba a comprar un coche.
- Haz clic en una tarjeta de piloto para abrir su ficha, ver su garaje y vender un coche.

## Registrar resultados de carrera (créditos)
1. Vuelve al Google Sheet (no a la web app) y abre la pestaña `Resultados_Carreras`.
2. Añade una fila por piloto con `Fecha`, `Carrera`, `ID_Piloto` y `Posicion` (deja `Creditos_Ganados` y `Procesado` en blanco / "NO").
3. En el Sheet, usa el menú **Tienda AC Evo → Procesar resultados de carrera pendientes**. Esto reparte los créditos automáticamente según la tabla de la pestaña `Config` y lo apunta en el Historial.

## Notas importantes / limitaciones de esta primera versión
- **No hay login real**: cualquiera con el enlace puede elegir cualquier piloto en el desplegable y comprar/vender en su nombre. Para un grupo cerrado de confianza (tu liga) suele ser suficiente, pero si quieres, puedo añadir después un PIN por piloto o restringir el acceso a "solo usuarios de tu organización de Google".
- **Precio fijo (tienda oficial)**: los pilotos no negocian precio entre ellos; solo compran a la tienda y pueden "devolver" el coche a la tienda a cambio de créditos (por defecto el 80% del precio de compra, configurable en la pestaña `Config`, celda `Porcentaje_Reventa_A_Tienda`).
- **Créditos por carrera**: la tabla de créditos por posición está en `Config` y es totalmente editable.
- El Sheet y la Web App comparten los mismos datos en tiempo real: todo lo que pase en la web se refleja al instante en el Sheet, y viceversa.

## Posibles mejoras futuras (dímelo si las quieres)
- PIN/contraseña por piloto.
- Límite de coches por piloto o por categoría.
- Subastas o mercado libre entre pilotos (en vez de precio fijo).
- Gráficos de evolución de créditos.
