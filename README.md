# Manual de Datos de Productos e Imágenes

Este manual describe cómo estructurar la información de sus productos en `products.json` y cómo organizar sus imágenes de productos para su uso con un sistema de publicación automatizado.

## Estructura de `products.json`

El archivo `products.json` debe ser un array de objetos de producto, donde cada objeto representa un único producto a ser publicado. Cada objeto de producto debe seguir esta estructura:

```json
[
  {
    "id": 1,
    "title": "TV SMART TV MARCA CHALLENGER",
    "description": "TRAEN 2 MANDOS Y SOPORTE FIJO DE LA PARED SON TECNOLOGÍA ANDROID REBAJA ‼️ ‼️",
    "price": 180,
    "currency": "USD",
    "is_published": false,
    "is_sold": false,
    "phone1_is_whatsapp": true,
    "phone1_prefix": "53",
    "phone1_number": "53543210",
    "province_id": 1,
    "municipality_id": 43,
    "image_urls": ["tv_challenger.jpg", "tv_challenger_side.jpg"],
    "category_id": 30,
    "subcategory_id": 214
  },
  {
    "id": 2,
    "title": "SMART TV marca Premier de 32 pulgadas",
    "description": "Con mensajería incluida a lugares céntricos",
    "price": 185,
    "currency": "USD",
    "is_published": false,
    "is_sold": false,
    "phone1_is_whatsapp": true,
    "phone1_prefix": "53",
    "phone1_number": "53543210",
    "province_id": 1,
    "municipality_id": 43,
    "image_urls": ["tv_premier_32.jpg"],
    "category_id": 30,
    "subcategory_id": 214
  }
]
```

**Descripción de los Campos:**

*   `id` (Número): Un identificador único para el producto. Esto ayuda a rastrear y gestionar listados de productos individuales.
*   `title` (Cadena de texto): El título principal de su publicación de producto. Manténgalo conciso y descriptivo.
*   `description` (Cadena de texto): Una descripción detallada del producto, incluyendo características, condición y cualquier otra información relevante.
*   `price` (Número): El precio de venta del producto.
*   `currency` (Cadena de texto): La moneda en la que se cotiza el producto (por ejemplo, "USD", "CUP", "MLC").
*   `is_published` (Booleano): Un indicador que muestra si el producto ha sido publicado. (Para fines de seguimiento).
*   `is_sold` (Booleano): Un indicador que muestra si el producto ha sido vendido. (Para fines de seguimiento).
*   `phone1_is_whatsapp` (Booleano): Establezca en `true` si el número de teléfono principal es un número de WhatsApp, `false` en caso contrario.
*   `phone1_prefix` (Cadena de texto): El código de marcación internacional o prefijo local para el número de teléfono principal (por ejemplo, "53").
*   `phone1_number` (Cadena de texto): El número de teléfono principal para contacto.
*   `province_id` (Número): El ID numérico correspondiente a la provincia donde se encuentra el producto. Consulte la sección "IDs de Ubicación" a continuación.
*   `municipality_id` (Número): El ID numérico correspondiente al municipio dentro de la provincia seleccionada. Consulte la sección "IDs de Ubicación" a continuación.
*   `image_urls` (Array de Cadenas de texto): Una lista de nombres de archivo para las imágenes asociadas con el producto. **Estos nombres de archivo deben coincidir exactamente con los archivos de imagen en su directorio de imágenes local designado.**
*   `category_id` (Número): El ID numérico para la categoría principal del producto. Consulte la sección "IDs de Categoría y Subcategoría" a continuación.
*   `subcategory_id` (Número): El ID numérico para la subcategoría del producto, dependiente del `category_id` elegido. Consulte la sección "IDs de Categoría y Subcategoría" a continuación.

## Organización de Imágenes

Para asegurar que las imágenes de sus productos puedan ser cargadas automáticamente, necesita organizarlas de una manera específica en su sistema de archivos local.

1.  **Cree un Directorio de Imágenes:** Cree una carpeta dedicada en su computadora donde se almacenarán todas las imágenes de sus productos. Por ejemplo:
    `C:\Users\Ricco\Desktop\Publisher\images\`

2.  **Coloque Sus Imágenes:** Ponga todos los archivos de imagen (por ejemplo, `tv_challenger.jpg`, `calentador_milexus_80l.jpg`) directamente en este directorio de imágenes.

3.  **Referencia en `products.json`:** En su archivo `products.json`, el array `image_urls` para cada producto debe contener solo los nombres de archivo de las imágenes, sin ninguna información de ruta. Por ejemplo: `"image_urls": ["tv_challenger.jpg", "tv_challenger_side.jpg"]`.

**Nota Importante sobre el Protocolo `file://` para Acceso a Imágenes (Limitaciones Potenciales):**

Su sistema intentará acceder a estas imágenes directamente desde su sistema de archivos local utilizando el protocolo `file://` (por ejemplo, `file:///C:/Users/Ricco/Desktop/Publisher/images/tv_challenger.jpg`). Aunque este método está diseñado para el acceso directo a archivos locales, los navegadores web modernos y las políticas de seguridad a menudo restringen el acceso programático a URLs `file://` arbitrarias desde contextos web (como las extensiones del navegador). Esto significa que la carga automática de imágenes a través de `file://` podría ser bloqueada por la configuración de seguridad de su navegador, lo que provocaría errores durante el proceso de publicación.

Si encuentra problemas con la carga de imágenes, considere servir sus imágenes a través de un servidor web local (por ejemplo, usando `http-server` para Node.js) y actualice la configuración de la ruta de la imagen en el sistema de publicación para usar una URL `http://` o `https://` en su lugar.

## IDs de Categoría, Subcategoría, Moneda, Provincia y Municipio

Estos IDs son específicos de la plataforma de publicación de destino. Siempre debe verificar estos valores inspeccionando el sitio web de la plataforma si encuentra problemas o si la plataforma se actualiza.

### Categorías

*   `30`: Compra / Venta
*   `1`: Computadora

### Subcategorías (para "Compra / Venta" - `category_id: 30`)

*   `31`: Celulares/Líneas/Accesorios
*   `32`: Reproductor MP3/MP4/IPOD
*   `33`: Reproductor DVD/VCD/DVR
*   `214`: Televisor
*   `34`: Cámara Foto/Video
*   `213`: Aire Acondicionado
*   `39`: Consola Videojuego/Juegos
*   `43`: Satélite
*   `35`: Electrodomésticos
*   `36`: Muebles/Decoración
*   `37`: Ropa/Zapato/Accesorios
*   `40`: Intercambio/Regalo
*   `41`: Mascotas/Animales
*   `42`: Divisas
*   `38`: Libros/Revistas
*   `211`: Joyas/Relojes
*   `217`: Antiguedades/Colección
*   `219`: Implementos Deportivos
*   `221`: Arte
*   `44`: Otros

### Subcategorías (para "Computadora" - `category_id: 1`)

*   `2`: PC de Escritorio
*   `3`: Laptop
*   `5`: Microprocesador
*   `4`: Monitor
*   `6`: Motherboard
*   `7`: Memoria RAM/FLASH
*   `8`: Disco Duro Interno/Externo
*   `9`: Chasis/Fuente
*   `11`: Tarjeta de Video
*   `12`: Tarjeta de Sonido/Bocinas
*   `13`: Quemador/Lector DVD/CD
*   `14`: Backup/UPS
*   `15`: Impresora/Cartuchos
*   `16`: Modem/Wifi/Red
*   `18`: Webcam/Microf/Audífono
*   `19`: Teclado/Mouse
*   `216`: Internet/Email
*   `218`: CD/DVD Virgen
*   `20`: Otros

### Moneda

*   `CUP`
*   `USD`
*   `MLC`

### Provincias

*   `4`: Pinar del Río
*   `2`: Artemisa
*   `3`: Mayabeque
*   `1`: La Habana
*   `5`: Isla de la Juventud
*   `6`: Matanzas
*   `7`: Cienfuegos
*   `8`: Villa Clara
*   `9`: Sancti Spíritus
*   `10`: Ciego de Ávila
*   `11`: Camagüey
*   `12`: Las Tunas
*   `13`: Holguín
*   `14`: Granma
*   `15`: Santiago de Cuba
*   `16`: Guantánamo

### Municipios (Ejemplo para "La Habana" - `province_id: 1`)

*   `34`: Arroyo Naranjo
*   `35`: Boyeros
*   `36`: Centro Habana
*   `37`: Cerro
*   `38`: Cotorro
*   `39`: Diez de Octubre
*   `40`: Guanabacoa
*   `41`: Habana del Este
*   `42`: Habana Vieja
*   `43`: La Lisa
*   `44`: Marianao
*   `45`: Playa
*   `46`: Plaza
*   `47`: Regla
*   `48`: San Miguel del Padrón

### Municipios (Ejemplo para "Artemisa" - `province_id: 2`)

*   `12`: Alquízar
*   `13`: Artemisa
*   `14`: Bauta
*   `15`: Caimito
*   `16`: Guanajay
*   `17`: Güira de Melena
*   `18`: Mariel
*   `19`: San Antonio de los Baños
*   `20`: Bahía Honda
*   `21`: San Cristóbal
*   `22`: Candelaria

### Municipios (Ejemplo para "Mayabeque" - `province_id: 3`)

*   `23`: Batabanó
*   `24`: Bejucal
*   `25`: Güines
*   `26`: Jaruco
*   `27`: Madruga
*   `28`: Melena del Sur
*   `29`: Nueva Paz
*   `30`: Quivicán
*   `31`: San José de las Lajas
*   `32`: San Nicolás de Bari
*   `33`: Santa Cruz del Norte
