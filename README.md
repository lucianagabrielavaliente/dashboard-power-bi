La exploración se amplía mediante una página de detalle de vendedores y un tooltip contextual con los cinco vendedores de mayor aporte para cada sucursal.

## Hallazgo principal

Occidente registra aproximadamente **$352 millones en ventas**, **422 pedidos** y un margen cercano al **80,01 %**. La rentabilidad relativa se mantiene saludable; por lo tanto, la oportunidad principal consiste en aumentar el volumen comercial. Oriente, con aproximadamente $423 millones, se utiliza como primera referencia de comparación y permite identificar una brecha de alrededor de $71 millones.

## Modelo de datos

El modelo utiliza una estructura en estrella:

- **Tabla de hechos:** `Ventas Completo`.
- **Dimensiones:** Cliente, Producto, Vendedor, Territorio, Medios de pago y Calendario.
- **Relaciones:** uno a varios desde las dimensiones hacia la tabla de hechos, con dirección de filtro simple.
- **Dimensión temporal:** tabla Calendario marcada como tabla de fechas y organizada mediante la jerarquía Año > Trimestre > Mes.
- **Organización de cálculos:** medidas centralizadas en la tabla `_Medidas`.

## Medidas principales

El reporte incluye, entre otras, las siguientes medidas DAX:

- Ventas Totales.
- Costos Totales.
- Margen Bruto.
- % Margen.
- Cantidad de Pedidos.
- Cantidad Vendida.
- Ventas Año Anterior.
- Variación interanual.
- Ventas acumuladas YTD.
- Categoría de Rendimiento.

Un parámetro de campo permite alternar entre Ventas Totales, Cantidad Vendida y Margen Bruto dentro del mismo gráfico temporal.

## Interacción y accesibilidad

- Segmentadores de Zona y Período sincronizados entre páginas.
- Botones y bookmarks para recorrer las tres escenas narrativas.
- Tooltip por sucursal y página fija de Detalle de Vendedores.
- Títulos dinámicos según la métrica seleccionada.
- Paleta de colores limitada, fondos neutros y etiquetas comprensibles.
- Texto alternativo previsto para los objetos visuales del reporte.

## Estructura del repositorio

```text
Proyecto-Integrador-PowerBI/
├── dashboard/
│   └── Valiente_Luciana_Proyecto_Final.pbix
├── data/
│   ├── README.md
│   └── raw-o-muestra/
├── docs/
│   └── Valiente_Luciana_Proyecto_Integrador_Final.pdf
└── README.md
```

La carpeta `data/` documenta las fuentes y el proceso de preparación. Cuando los archivos originales no puedan publicarse, puede incluirse una muestra representativa o únicamente la descripción de su estructura.

## Cómo abrir el proyecto

1. Descargar o clonar el repositorio.
2. Abrir `dashboard/Valiente_Luciana_Proyecto_Final.pbix` con Power BI Desktop.
3. Si Power BI solicita las fuentes, actualizar sus rutas desde **Transformar datos > Configuración de origen de datos**.
4. Ejecutar **Actualizar** para cargar la información.
5. Comenzar en Vista General y utilizar los botones del reporte para recorrer la historia.

La versión en PDF se encuentra en `docs/Valiente_Luciana_Proyecto_Integrador_Final.pdf`. El PDF conserva todas las páginas del reporte y agrega la documentación técnica al final, aunque las interacciones permanecen disponibles únicamente en el archivo PBIX.

## Datos

Las fuentes, los campos principales y las transformaciones aplicadas se describen en [`data/README.md`](data/README.md).

## Herramientas utilizadas

- Power BI Desktop.
- Power Query.
- DAX.
- Microsoft Excel y archivos de texto como fuentes de datos.
