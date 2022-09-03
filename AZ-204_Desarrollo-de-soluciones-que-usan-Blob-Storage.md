# **Microsoft Certified: Azure Developer Associate - Desarrollo de soluciones que usan Blob Storage**
## **Temario**
- [**Microsoft Certified: Azure Developer Associate - Desarrollo de soluciones que usan Blob Storage**](#microsoft-certified-azure-developer-associate---desarrollo-de-soluciones-que-usan-blob-storage)
  - [**Temario**](#temario)

## **Exploración de Azure Blob Storage**
Diseñado para:
- Visualización de imágenes o documentos directamente en un explorador
- Streaming de audio y vídeo
- Escribir en archivos de registro

Las aplicaciones cliente o usuarios pueden acceder a objetos en Blob Storage a través de HTTP/HTTPS. Mediante API REST, Azure PowerShell, CLI o biblioteca cliente.

### **Tipos de cuentas de almacenamiento**
Dos niveles:
- Estándar: Uso general v2 Estándar.
- Premium: Uso de unidades de estado sólido. 3 tipos de cuenta: Blobs en bloques, páginas o recursos compartidos de archivos.

### **Detección de los tipos de recursos de Azure Blob Storage**
Ofrece tres tipos:
- Cuenta de almacenamiento
- Contenedor en una cuenta
- Blob en un contenedor

#### **Cuentas de almacenamiento**
Espacio de nombres único en Azure para sus datos. 
#### **Contenedor en una cuenta**
Organiza conjunto de blobs, similar a un directorio.
- Una cuenta puede contener ilimitados contenedores y un contenedor ilimitados blobs.
#### **Blob en un contenedor**
Tres tipos:
- En bloque: Texto y datos binarios. Hasta 4.7 GB. Se pueden administrar de forma individual.
- Anexos: Mismo bloque pero optimiado para operaciones de anexión. Conveniente para escenarios como registro de datos en VM.
- Páginas: Archivos de acceso aleatorio con un tamaño de hasta 8 TB. Sirven como discos para VM de Azure.

### **Exploración de las características de seguridad de Azure Storage**
Brinda funcionalidades de seguridad:
- Todos los datos y metadatos se cifran con Storage Service Encryption (SSE)
- Azure Active Directory (Azure AD) y RBAC son compatibles con Azure Storage
- Datos protegidos en tránsico por cifrado de cliente, HTTPS o SMB 3.0.
- Cifrado de los discos de datos y del S.O. por Azure Virtual Machines mediante Azure Disk Encryption.
- Acceso delegado a objetos mediante firmas de acceso compartido.

### **Cifrado de Azure Storage para datos en reposo**
- Mediante el cifrado AES de 256 bits
- Compatible con FIPS 140-2.
- No se puede deshabilitar

#### **Administración de claves de cifrado**
- Puede administrar cifrado con sus propias claves
- O confiar en claves administradas por Microsoft.

### **Evaluación de las opciones de redundancia de Azure Storage**
- Siempre se almacena varias copias de los datos.

#### **Redundancia en la región primaria**
Replican 3 veces en región primaria. Ofrece 2 opciones:
- Almacenamiento con redundancia local (LRS): Copia datos de forma sincrónica tres veces dentro de una ÚNICA ubicación física en la región primaria.
- Almacenamiento con redundancia de zona geográfica (ZRS): Lo mismo pero en 3 zonas de disponibilidad en la región primaria.

#### **Redundancia en una región secundaria**
Para aplicaciones que requieren alta durabilidad.
- La región secundaria se determina según primaria y no se cambia.
2 opciones:
- Almacenamiento con redundancia geográfica (GRS): Aplica LRS y luego copia los datos de forma asincrónica en una única ubicación física en la región secundaria. En esta última también se aplica LRS
- Almacenamiento con redundancia de zona geográfica (GZRS): Aplica ZRS, y luego copia asincronicamente en una ÚNICA ubicación física en la región secundaria. Aplica LRS a esta última.

## **Administración del ciclo de vida de Azure Blob Storage**
Datos tienen ciclos de vida únicas. La necesidad de acceso cambia en el tiempo hasta que estes no se necesiten ni ver en el tiempo.
- A nivel de cuenta se puede establecer : frecuente y esporádico. El de archivo a nivel de Blob
- Acceso de archivo se almacenan sin conexión. 
- Nivel de archivo solo admite opciones e LRS, GRS y RA-GRS.

### **Administración del ciclo de vida de los datos**
- Eliminar los blobs al final de sus ciclos de vida
- Definir reglas que se ejecutarán una vez al día en el nivel de cuenta de almacenamiento
- Aplicar reglas a contenedores o a un subconjunto de blobs (mediante prefijos como filtros)

### **Detección de directivas de ciclo de vida de Blob Storage**
Directiva de administración del ciclo de vida: Colección de reglas en un documento JSON.
- Cada definición de regla incluye un conjunto de filtros y conjunto de acciones. 
- El filtro limita las acciones de regla a un conjunto de objetos de un contenedor o nombres de objetos. 

```json
{
  "rules": [
    {
      "name": "rule1",
      "enabled": true,
      "type": "Lifecycle",
      "definition": {...}
    },
    {
      "name": "rule2",
      "type": "Lifecycle",
      "definition": {...}
    }
  ]
}
```
- Una directiva puede contener hasta 100 reglas
- Cada regla tiene parámetros:
  - `name`: String - Obligatorio
  - `enabled`: Boolean - No Obligatorio
  - `type`: Valor de enumeración - Obligatorio
  - `definition`: Objeto que define la regla del ciclo de vida - Obligatorio

#### **Reglas**
- Cada definición incluye un conj. de filtros y un conj. de acciones
- El conj. de acciones aplica acciones de nivel o eliminación

Ejemplo: 
- Filtra la cuenta para ejecutar las acciones en objetos que existen dentro de `container1` y empiezan por `foo`.
  1. Establecer el nivel de blob en nivel esporádico 30 días después de la última modificación
  2. Establecer el nivel de blob en nivel de almacenamiento de archivo 90 días después de la última modificación
  3. Eliminar el blob 2555 días (siete años) después de la última modificación
  4. Eliminar instantáneas de blob 90 días después de la creación de las instantáneas

```json
{
  "rules": [
    {
      "name": "ruleFoo",
      "enabled": true,
      "type": "Lifecycle",
      "definition": {
        "filters": {
          "blobTypes": [ "blockBlob" ],
          "prefixMatch": [ "container1/foo" ]
        },
        "actions": {
          "baseBlob": {
            "tierToCool": { "daysAfterModificationGreaterThan": 30 },
            "tierToArchive": { "daysAfterModificationGreaterThan": 90 },
            "delete": { "daysAfterModificationGreaterThan": 2555 }
          },
          "snapshot": {
            "delete": { "daysAfterCreationGreaterThan": 90 }
          }
        }
      }
    }
  ]
}
```
Más información: https://docs.microsoft.com/es-es/learn/modules/manage-azure-blob-storage-lifecycle/3-blob-storage-lifecycle-policies

### **Rehidratación de los datos de blob desde el nivel de archivo**
Si el blob está en nivel de acceso de archivo: Se le dice que está sin conexión y no se puede leer ni modificar.
- Para leer o modificar: debe rehidratar el blob en un nivel en línea (frecuento o esporádico).
- Dos formas de rehidratar:
    1. Copiar un blob archivado en un nivel en línea (Opción recomendada)
    2. Cambio del nivel de acceso de un blob a un nivel en línea

#### **Prioridad de la rehidratación**
- Prioridad estándar: Procesará en el orden que se recibió y puede tardar hasta 15 horas
- Alta prioridad: Podría completar en menos de 1 hora con objetos < 10GB 

### **Trabajo con Azure Blob Storage**
Espacio de nombres (Azure.Storage.Blobs):
Clase|Descripción
---|---
`BlobClient`|Manipular blobs
`BlobClientOptions`|Opciones de configuración de cliente para conectarse a Blob Storage
`BlobContainerClient`|Manipular contenedores y sus blobs
`BlobServiceClient`|Manipular recursos de servicio y contenedores
`BlobUriBuilder`|Modificar contenido de una instancia de URI para que apunte a una cuenta, contenedor o un blob.

### **Administración de metadatos y propiedades de contenedor mediante .NET**
Contenedores de blobs admiten propiedades del sistema y metadatos definidos por el usuario.
- Propiedades del sistema
- Metadatos definidos por el usuario

Mayor información: https://docs.microsoft.com/es-es/learn/modules/work-azure-blob-storage/4-manage-container-properties-metadata-dotnet

### **Establecimiento y recuperación de propiedades y metadatos para recursos de blob mediante REST**
Mayor información: https://docs.microsoft.com/es-es/learn/modules/work-azure-blob-storage/5-set-retrieve-properties-metadata-rest