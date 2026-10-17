# Adaptador de almacenamiento BunnyCDN para Ghost

[ENGLISH](README.md) | **ESPAÑOL**

Fork de [betschki/ghost-bunny-cdn-storage](https://github.com/betschki/ghost-bunny-cdn-storage), usado en criptonautas.co. Sin afiliación ni respaldo de la Ghost Foundation.

BunnyCDNAdapter es un adaptador de almacenamiento para Ghost CMS que guarda los archivos multimedia en [BunnyCDN Storage](https://bunny.net/storage/).

Implementa la [documentación de Ghost sobre adaptadores de almacenamiento](https://ghost.org/docs/config/#storage-adapters).

## Instalación con git

1. Entra a la carpeta de contenido dentro de la raíz de Ghost (probablemente `./content`).
2. Crea una carpeta `adapters/storage` dentro de ella, si no existe.
3. Entra con `cd adapters/storage`.
4. Clona este repositorio con `git clone https://github.com/betschki/ghost-bunny-cdn-storage.git bunny-cdn`.

## Configuración

Se configura editando el archivo de configuración o con variables de entorno. Completa los valores según tu configuración de BunnyCDN; `configuration.example.json` y `example.env` muestran cómo debe quedar.

Con la configuración de ejemplo, la URL final sería:

```
https://cdn.your-pull-zone-hostname.com/folder/file.jpg
```

### Archivo de configuración

En tu archivo de configuración (por ejemplo `config.production.json`), agrega:

```json
"storage":  {
  "active":  "bunny-cdn",
  "bunny-cdn":  {
    "endpoint":  "https://storage.bunnycdn.com",
    "storageZone":  "your-storage-zone",
    "hostname":  "cdn.your-pull-zone-hostname.com",
    "folder":  "a-folder-you-want-to-use",
    "accessKey":  "your-access-key"
  }
}
```

### Variables de entorno

```bash
BUNNYCDN_ENDPOINT="https://storage.bunnycdn.com"
BUNNYCDN_STORAGE_ZONE="your-storage-zone"
BUNNYCDN_HOSTNAME="cdn.your-pull-zone-hostname.com"
BUNNYCDN_FOLDER="a-folder-you-want-to-use"
BUNNYCDN_ACCESS_KEY="your-access-key"
```

### Carpeta

El adaptador se desarrolló para los sitios de clientes de [magicpages.co](https://magicpages.co), que necesitaban poder elegir una carpeta, como en la URL de ejemplo. Para guardar en la raíz de la zona de almacenamiento, pon `folder` en `null`.

## Licencia

[MIT](LICENSE), según lo declara el proyecto original.
