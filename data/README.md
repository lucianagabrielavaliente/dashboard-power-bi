# Datos del proyecto

Esta carpeta reúne la documentación de las fuentes utilizadas en el proyecto **Rendimiento de vendedores | 2018-2020**. Los datos describen operaciones comerciales, clientes, productos, vendedores, territorios y medios de pago de una empresa distribuidora con operación en Argentina.

## Archivos fuente

| Archivo | Contenido principal | Uso en el modelo |
|---|---|---|
| `Base de datos.xlsx` | Clientes, productos, vendedores y ventas históricas | Fuente de las dimensiones principales y de las operaciones anteriores a 2020 |
| `Ventas 2020.xlsx` | Operaciones comerciales correspondientes a 2020 | Se normaliza y se anexa a la tabla histórica de ventas |
| `Ventas por Zona.xlsx` | Valores territoriales distribuidos por año | Se transforma desde columnas anuales hacia una estructura de período y monto |
| `Territorio.txt` | Identificador territorial, país, continente, ciudad, latitud y longitud | Dimensión geográfica utilizada para filtrar y describir las ventas |
| `Medios de pago.pdf` | Identificadores, formas de pago, descripciones y descuentos | Dimensión de medios de pago |

## Organización sugerida

Cuando las fuentes puedan publicarse, pueden almacenarse de la siguiente manera:

```text
data/
├── README.md
└── raw-o-muestra/
    ├── Base de datos.xlsx
    ├── Ventas 2020.xlsx
    ├── Ventas por Zona.xlsx
    ├── Territorio.txt
    └── Medios de pago.pdf
```

La carpeta `raw-o-muestra/` puede contener los archivos originales o una muestra representativa. Los nombres y la estructura de las columnas deben conservarse para facilitar la actualización del modelo.

## Preparación de los datos

La preparación se realizó en Power Query e incluyó:

1. Promoción y normalización de encabezados.
2. Eliminación de filas y columnas completamente vacías.
3. Estandarización de nombres de campos e identificadores.
4. Corrección de tipos de datos para fechas, cantidades, importes y coordenadas.
5. Homologación de valores categóricos y correcciones ortográficas.
6. Separación de campos que contenían más de un atributo.
7. Transformación de las columnas anuales de Ventas por Zona mediante anulación de dinamización.
8. Creación de las columnas `Prioridad` y `Tipo de Período`.
9. Homologación del esquema de Ventas históricas y Ventas 2020.
10. Anexado de ambas fuentes en la consulta final `Ventas Completo`.

## Tablas resultantes

El modelo utiliza las siguientes tablas de negocio:

- `Ventas Completo`: tabla de hechos con el detalle transaccional.
- `Cliente`: datos descriptivos y segmentación de clientes.
- `Producto`: catálogo y características de productos.
- `Vendedor`: información del vendedor, sucursal, segmento y zona.
- `Territorio`: ubicación geográfica de las operaciones.
- `Medios de pago`: clasificación y descripción de las formas de pago.
- `Calendario`: dimensión temporal creada dentro de Power BI.
- `_Medidas`: tabla destinada a organizar las medidas DAX.

## Campos de relación

Las relaciones principales utilizan:

- `Id Cliente`.
- `Id Producto`.
- `Id Vendedor`.
- `Id Ubicación` / `Id Territorio`.
- `Id Pago`.
- `Fecha Compra` / `Calendario[Date]`.

Las dimensiones se relacionan con `Ventas Completo` mediante relaciones de uno a varios y filtros en una sola dirección.

## Actualización en Power BI

Para actualizar el proyecto con una copia local de las fuentes:

1. Colocar los archivos dentro de `data/raw-o-muestra/`.
2. Abrir el archivo PBIX.
3. Ingresar en **Transformar datos > Configuración de origen de datos**.
4. Reemplazar las rutas originales por la ubicación local de cada archivo.
5. Revisar que los nombres de hojas, tablas y columnas coincidan con los documentados.
6. Aplicar los cambios y ejecutar **Actualizar**.

## Publicación y uso

Antes de publicar los datos en un repositorio abierto, se debe comprobar que no contengan información personal, confidencial o sujeta a restricciones de distribución. Si los archivos originales no pueden compartirse, esta documentación puede acompañarse con datos anonimizados o con una muestra que conserve únicamente la estructura necesaria para comprender el proyecto.

Los datos se utilizan con fines educativos y de portfolio.