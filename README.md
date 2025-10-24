# 🧹 Proceso de Limpieza, Transformación y Normalización de Datos

Este proyecto se desarrolló en **Power BI (Power Query)** con el objetivo de preparar los datos para el análisis de ventas, contactos y productos.  
A continuación, se detallan las decisiones y transformaciones aplicadas en cada fase del proceso.

---

## 1. Carga inicial de datos
Se realizó la **importación de múltiples archivos fuente** (ventas, contactos, productos y pedidos).  
Se verificó que las estructuras se reconocieran correctamente en Power Query, validando encabezados, tipos de columnas y consistencia entre tablas.

---

## 2. Estandarización de columnas
- Se ajustaron los **nombres de campos** para mantener un formato uniforme y claro (ejemplo: `Fecha_Venta`, `ID_Producto`, `Valor_Total`, `TipoContacto`).
- Se corrigieron mayúsculas/minúsculas y se eliminaron espacios o caracteres especiales.
- Se homogenizaron formatos de fecha y número para facilitar la transformación posterior.

---

## 3. Depuración de filas y columnas
- Se eliminaron columnas no relevantes para el análisis (campos redundantes o vacíos).
- Se filtraron registros incompletos o duplicados.
- Se ajustaron valores inconsistentes en variables clave (por ejemplo, tipos de producto y nombres de cliente).

---

## 4. Transformación de series temporales
- Las columnas con periodos fueron **convertidas en un formato largo (unpivot)**, permitiendo un análisis **temporal y categórico**.
- Se crearon campos derivados para **año, mes y trimestre**, habilitando comparaciones de tendencias.

---

## 5. Control de tipos de datos
- Se revisaron y corrigieron los **tipos de datos**:
  - Fechas → tipo *Date*
  - Valores numéricos → tipo *Decimal Number*
  - Códigos y nombres → tipo *Text*
- Se validó la correcta detección de formato regional para montos y separadores decimales.

---

## 6. Tratamiento de valores atípicos y nulos
- Se identificaron valores nulos en columnas de contacto y ventas.
- Se aplicaron los siguientes criterios:
  - Valores faltantes en texto → reemplazo por `"Desconocido"`.
  - Valores nulos en campos numéricos → `0`.
  - Registros con inconsistencias críticas → eliminados.
- Esta estrategia garantiza integridad sin alterar las métricas generales.

---

## 7. Unificación de contactos
- Se **anexaron** las tablas de clientes, proveedores y empleados en una única tabla denominada **`ContactosConsolidados`**.
- Se añadió una columna **`TipoContacto`** que indica el origen del registro (Cliente, Proveedor o Empleado).
- Se conservaron atributos clave: `ID_Contacto`, `Nombre`, `Correo`, `Teléfono`, `País` y `TipoContacto`.

---

## 8. Enriquecimiento de datos
- Se establecieron **relaciones entre las tablas**:
  - `Ventas` ↔ `Productos` (por `ID_Producto`)
  - `Ventas` ↔ `ContactosConsolidados` (por `ID_Contacto`)
- Estas uniones permiten explorar análisis cruzados por categoría, tiempo y tipo de contacto.

---

## 9. Evaluación de la calidad de datos
- Se utilizó el **perfilador de datos de Power Query** para detectar:
  - Duplicados
  - Valores atípicos
  - Distribuciones irregulares
- Se documentaron las anomalías corregidas y se validó la consistencia final del modelo.

---

## 10. Revisión del código M
- Se revisó el **Editor avanzado** para comprender y optimizar los pasos registrados por Power Query.
- Se ajustó la secuencia de transformaciones para mantener un flujo limpio, documentado y reproducible.

---

# 📊 Resultados Finales

- ✅ **Tabla de Ventas normalizada** lista para análisis temporal y categórico.  
- ✅ **Tabla consolidada de Contactos**, unificando clientes, proveedores y empleados.  
- ✅ **Relaciones establecidas** entre ventas, productos y contactos.  
- ✅ **Informe documentado** describiendo los criterios y decisiones aplicadas en limpieza y transformación.

---

📅 *Proyecto elaborado en Power BI como práctica de integración, normalización y preparación de datos para análisis.*
