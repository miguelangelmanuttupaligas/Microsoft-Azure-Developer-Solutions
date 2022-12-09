# **Microsoft Certified: Azure Developer Associate - Creación de aplicaciones web de Azure App Service**
## **Temario**
- [**Microsoft Certified: Azure Developer Associate - Creación de aplicaciones web de Azure App Service**](#microsoft-certified-azure-developer-associate---creación-de-aplicaciones-web-de-azure-app-service)
  - [**Temario**](#temario)
  - [**Explorar Azure App Service**](#explorar-azure-app-service)
    - [**Compatibilidad integrada con el escalado automático**](#compatibilidad-integrada-con-el-escalado-automático)
    - [**Compatibilidad con integración e implementación continuas**](#compatibilidad-con-integración-e-implementación-continuas)
    - [**Ranuras de implementación**](#ranuras-de-implementación)
    - [**App Service en Linux**](#app-service-en-linux)
      - [**Limitaciones**](#limitaciones)
    - [**Examen de los planes de Azure App Service**](#examen-de-los-planes-de-azure-app-service)
    - [**Implementación en App Service**](#implementación-en-app-service)
      - [**Implementación automatizada (Integración continua)**](#implementación-automatizada-integración-continua)
      - [**Implementación manual**](#implementación-manual)
      - [**Uso de ranuras de implementación**](#uso-de-ranuras-de-implementación)
    - [**Exploración de la autenticación y autorización en App Service**](#exploración-de-la-autenticación-y-autorización-en-app-service)
      - [**¿Por qué usar la autenticación integrada?**](#por-qué-usar-la-autenticación-integrada)
      - [**Proveedores de identidades**](#proveedores-de-identidades)
      - [**Funcionamiento**](#funcionamiento)
      - [**Flujo de autenticación**](#flujo-de-autenticación)
      - [**Comportamiento de la autorización**](#comportamiento-de-la-autorización)
    - [**Detección de características de redes de App Service**](#detección-de-características-de-redes-de-app-service)
      - [**Características de redes de App Service multiinquilino**](#características-de-redes-de-app-service-multiinquilino)
      - [**Comportamiento predeterminado de la redes**](#comportamiento-predeterminado-de-la-redes)
      - [**Direcciones de salida**](#direcciones-de-salida)
  - [**Configurar aplicaciones web**](#configurar-aplicaciones-web)
    - [**Configuración de la aplicación**](#configuración-de-la-aplicación)
    - [**Configurar las opciones generales**](#configurar-las-opciones-generales)
    - [**Configurar asignaciones de ruta de acceso**](#configurar-asignaciones-de-ruta-de-acceso)
      - [**Windows**](#windows)
      - [**Linux y en contenedor**](#linux-y-en-contenedor)
    - [**Activación del registro de diagnóstico**](#activación-del-registro-de-diagnóstico)
      - [**Habilitación del registro de aplicaciones (Windows)**](#habilitación-del-registro-de-aplicaciones-windows)
      - [**Habilitación del registro de aplicaciones (Linux o contenedor)**](#habilitación-del-registro-de-aplicaciones-linux-o-contenedor)
      - [**Transmisión de registros**](#transmisión-de-registros)
      - [**Acceso a los archivos de registro**](#acceso-a-los-archivos-de-registro)
    - [**Configuración de certificados de seguridad**](#configuración-de-certificados-de-seguridad)
      - [**Requisitos de certificados privados**](#requisitos-de-certificados-privados)
    - [**Administración de las características de la aplicación**](#administración-de-las-características-de-la-aplicación)
      - [**Conceptos básicos**](#conceptos-básicos)
      - [**Declaración de la marca de características**](#declaración-de-la-marca-de-características)
      - [**Repositorio de marcas de características**](#repositorio-de-marcas-de-características)
  - [**Escalado de aplicaciones en Azure App Service**](#escalado-de-aplicaciones-en-azure-app-service)
      - [**Condiciones de la escalabilidad automática**](#condiciones-de-la-escalabilidad-automática)
      - [**Métricas para las reglas de escalabilidad**](#métricas-para-las-reglas-de-escalabilidad)
  - [**Exploración de entornos de ensayo**](#exploración-de-entornos-de-ensayo)

## **Explorar Azure App Service**
- Servicio basado en HTTP
- Hospeda app webs, API REST, Back-ends para móviles.
- Soporta múltiples lenguajes (NET, .NET Core, Java, Ruby, Node.js, PHP y Python)
- Entornos Windows y Linux

### **Compatibilidad integrada con el escalado automático**
- Escalado vertical (Mejora en App Service)
- Escalado horizontal (Creación de más instancias en el mismo App Service)
**El escalado se aplica a más MÁQUINAS SUBYACENTES en la que se hospeda la App Web**  
Los recursos a escalar son:
- Número de núcleos
- Cantidad de RAM

### **Compatibilidad con integración e implementación continuas**
- Azure DevOps
- GitHub
- Bitbucket
- FTP
- Git local, etc.

### **Ranuras de implementación**
**Plan Estándar, Premium o Aislado de App Service**
- Espacios aislados (incluido ranura de producción)
- Cada ranura es una aplicación activa con nombre de host propio
- Elementos de contenido y configuración de aplicaciones pueden ser intercambiados entre ranuras de implementación

### **App Service en Linux**
- Contenedores de Linux personalizados (Web App for Containers)
- Si los lenguajes compatibles no satisfacen la aplicación, se puede implementar en un contenedor personalizado 

#### **Limitaciones**
- No se admite en plan de tarifa Compartido
- No se mezcla Windows y Linux en un mismo plan

### **Examen de los planes de Azure App Service**
- Una aplicación siempre se ejecuta en un plan **App Service**
- Un plan es un conjunto de recursos de proceso (CPU,RAM y otros).
- Una o varias aplicaciones pueden ejecutarse en el mismo plan
- **Azure Functions** puede ejecutarse en un plan de **App Service**

**Plan de App Service**:
- Región
- Número de instancias de VM
- Tamaño de las instancias de VM (pequeño, mediano, grande)
- Plan de tarifa (Gratis, Compartido, Básico, Estándar, Premium/V2/V3 y Aislado)

**Categorías de Plan de tarifa**:
Categoría|Plan|Descripción
---|---|---
Proceso compartido|Gratis, Compartido|Comparten grupos de recursos con otros clientes. Asignan cuota de CPU a cada app que se ejecuta. No escalan horizontalmente
Proceso dedicado(Dedicated compute)|Básico, Estándar, Premium/V2/V3|Ejecutan apps en VM dedicadas. Solo las app del mismo plan comparten los mismos recursos de proceso. Mayor plan, más instancias de VM disponibles para escalar horizontalmente
Aislado|VM de Azure dedicadas en instancias de Virtual Network|Aislamiento de red, de proceso(computacional) a sus aplicaciones. Máxima posibilidad de escalabilidad horizontal
Consumo|Aplicaciones de funciones|Escala de manera dinámica según carga de trabajo 

**¿Cómo se ejecuta y escala mi aplicación?**
- La aplicación se ejecutaría en todas las instancias de la VM en el plan de App Service
- Si hay varias app, comparten las mismas instancias de VM
- Si hay varias ranuras para una app, todas las ranuras se ejecutan en las mismas instancias de VM
- Registros de diagnóstico, copias de seguridad y WebJobs también consumen CPU y memoría en las instancias de VM

**¿Qué ocurre si mi aplicación necesita más funcionalidades o características?**
- Puede escalar verticalmente el plan de App Service
- Puede aislar una aplicación del App Service hacia otro.

### **Implementación en App Service**
Puede ser: **Automatizada** y **Manual**
#### **Implementación automatizada (Integración continua)**
- Insertar nuevas características
- Corrección de errores
- En un patrón repetitivo y rápido con impacto mínimo en usuarios finales
- Origenes: **Azure DevOps**, **GitHub** y **BitBucket**
#### **Implementación manual**
- Origenes:
  - **Git**: App Service incluye una dirección URL de Git como repositorio
  - **CLI**: `az webapp up` puede empaquetar la aplicación e implementar. O bien, crear una aplicación web si no se ha creado una. 
  - **Implementación desde un archivo Zip**: A través de `curl` u otra utilidad HTTP, enviando el .zip hacia los archivos de aplicación de App Service
  - **FTP/S**: Manera tradicional de insertar código

#### **Uso de ranuras de implementación**
Siempre que sea posible usar ranuras. Implementar la aplicación en un entorno de ensayo e, intercambiar los espacios de ensayo y producción cuando se requiera.

### **Exploración de la autenticación y autorización en App Service**
**Azure App Service** es compatible con autenticación y autorización. Puede proporcionar inicio de sesión a usuarios y accesos a datos con una cantidad mínima de código. Incluso en Azure Functions.

#### **¿Por qué usar la autenticación integrada?**
- La característica integrada puede ahorrar tiempo y esfuerzo
- Se encuentra integrada  con proveedores de identidades federados
**Ventajas**:
  - Integrar muchas funcionalidades nativas de autenticación o implementarlas las suyas
  - Integrado en la plataforma, y no depende de ningún lenguaje, SDK o experiencia en seguridad
  - Proveedores de inicio de sesión: Azure AD, Facebook, Google y Twitter.

#### **Proveedores de identidades**
Identidad federada. Un tercero almacena las identidades de usuario y el flujo de autenticación para usted.
Proveedor| Punto de conexión de inicio de sesión
---|---
Plataforma de identidad de Microsoft|`/.auth/login/aad`
Facebook|`/.auth/login/facebook`
Google|`/.auth/login/google`
Twitter|`/.auth/login/twitter`
Nuevo proveedor de OpenID Conenct|`/.auth/login/<providerName>`

#### **Funcionamiento**
El módulo de autenticación y autorización se ejecuta en el mismo espacio aislado que el código de aplicación, pero en distintos procesos (S.O).  
Una solicitud HTTP pasa primero en el módulo antes que el código lo controle.:
  - Autentica a los usuarios
  - Valida, almacena y actualiza tokens
  - Administra la sesión autenticada
  - Inyecta información de identidad en encabezados

> En Linux y su servicio de contenedores. El módulo de AuthN y AuthZ se ejecuta en un contenedor independiente.

#### **Flujo de autenticación**
1. Sin el SDK del proveedor: La aplicación delega el inicio de sesión a App Service (Dentro está el proveedor). El código del servidor administra el proceso de iniciar sesión, llamado *flujo dirigido por el servidor*.
2. Con el SDK del proveedor: La aplicación inicia manualmente la sesión usando SDK. Enviando el token de autenticación para su validación en App Service. *flujo dirigido por el cliente*.

Paso|Sin SDK|Con SDK
---|---|---
Inicio de sesión|Redirige el cliente a `/.auth/login/<provider>`|Código de cliente da inicio de sesión usando SDK.
Autenticación posterior|Proveedor redirige el cliente a `/.auth/login/<provider>/callback`|El código del cliente publica el token del proveedor en `/.auth/login/<provider>` para validar.
Establecer la sesión autenticada|App Service agrega cookie autenticada a la respuesta|App Service devuelve su token de autenticación al código de cliente.
Servir contenido autenticado|Cliente incluye la cookie de autenticación en las solicitudes|Código de cliente presenta el token de autenticación en encabezado `X-ZUMO-AUTH` 

> Se puede redigir a los usuarios no autenticados a `/.auth/login/<provider>` y se puede presentar varios vínculos `/.auth/login/<provider>` para iniciar sesión.
#### **Comportamiento de la autorización**
***Si la solicitud entrante no está autenticada...***  
- **Permitir solicitudes no autenticadas**: La solicitud llega directamente al código de aplicación, aplazando la del proveedor.
- **Requerir autenticación**: Rechazará todo tráfico no autenticado. El rechazo puede ser un redireccionamiento a un proveedor. **En móvil** la respuesta es `HTTP 401 Unauthorized`.

### **Detección de características de redes de App Service**
App Service permite el acceso a través de internet de forma predeterminada y estás solo pueden acceder a puntos de conexión hospedados en internet (No privadas).  
**¿Cómo controlar el tráfico de red entrante y saliente?**: Hay 2 tipos.  
- **Servicio público multiinquilino**: Hospeda planes de App Services en todas las SKU (Gratis, Compartido, Básico, ...) menos la Aislada.
- **App Service Environment (ASE) de un único inquilino**:  Hospeda planes de App Service de SKU aislada directamente en su red virtual de Azure.

#### **Características de redes de App Service multiinquilino**
- Azure App Service es un **Sistema distribuido**
- Servidores front-end: Controlan las solicitudes HTTP o HTTPS entrantes.
- Roles de trabajo: Hospedan la carga de trabajo del cliente.
Todos los roles de una implementación de App Service existen en una red de varios inquilinos.  
Debido a que hay muchos clientes diferentes en la misma **Unidad de escalado de App Service**, no se puede conectar la red de App Service directamente a su red.

En lugar de brindar conexión a redes, se brindan características para administrar aspectos de la comunicación de aplicaciones.

Características de entrada|Características de salida
---|---
Dirección asignada a las aplicaciones|Conexiones híbridas
Restricciones de acceso|Integración de red virtual con requisito de puerta de enlace
Puntos de conexión del servicio|Integración de la red virtual
Puntos de conexión privados

#### **Comportamiento predeterminado de la redes**
- Unidades de escalado de Azure App Service admiten muchos clientes en cada implementación.
- Plan SKU Gratis y Compartido: Hospedan cargas de trabajo de clientes en **roles de trabajo** multiinquilino. 
- Plan SKU Básico y superiores: Hospendan cargas de trabajo dedicadas a un único plan de App Service.
- Plan SKU Estándar: Todas las aplicaciones de este plan se ejecutarán en el mismo rol de trabajo.

Si el rol de trabajo se escala horizontalmente, todas las aplicaciones de ese plan se replicarán en un **rol de trabajo** nuevo para cada instancia del plan.

#### **Direcciones de salida**
- Las VM de trabajo son del tipo según el plan de App Service.
- Planes Gratis, Compartido, Básico, Estándar y Premium usan un tipo de VM.
- Plan Premium V2 usa otro tipo de VM.
- Plan Premium V3 usa otro tipo más de VM.

## **Configurar aplicaciones web**
### **Configuración de la aplicación**
La configuración son variables que se pasan como variables de entorno al código.  
En caso de Linux y sus contenedores personalizados, la marca `--env` establece la variable de entorno en el contenedor.  

- La configuración de la aplicación siempre se cifra cuando se almacena (cifrado en reposo).
- Requiere nombre, valor (cadena de conexión o configuración de aplicación), tipo y configuración de la ranura.

```json
[
  {
    "name": "name-1",
    "value": "conn-string-1",
    "type": "SQLServer",
    "slotSetting": false
  },
  {
    "name": "name-2",
    "value": "conn-string-2",
    "type": "PostgreSQL",
    "slotSetting": false
  },
  ...
]
```
### **Configurar las opciones generales**
Algunas opciones comunes de la **aplicación**.  
Algunas configuraciones requieren escalar verticalmente hasta los planes de tarifa superiores.
Lista de opciones disponibles:  
- **Configuración de stack**: Lenguaje y versión del SDK. Para aplicaciones de Linux y de contenedor personalizadas, puede establecer archivo o comando de inicio opcional.
- **Configuración de plataforma**: Opciones para el entorno de alojamiento
  - Valor de bits: 32 o 64
  - Protocolo de WebSocket: SignalR o socket.io, por ejemplo.
  - Always On: Mantener cargada la aplicación, incluso cuando no hay tráfico.
  - Versión de canalización administrada
  - Versión de HTTP: Establecida en 2.0 para compatibilidad con HTTPS/2
  - Afinidad ARR: Si hay varias instancias, se asegura que el cliente está enruta a la misma instancia de la vida de la sesión. Si lo desactiva, será para aplicaciones sin estado.
- **Depuración**: Depuración remota para aplicaciones ASP.NET, ASP.NET Core o Node.js. Se desactiva después de 48hrs
- **Certificados de cliente entrantes**: Certificados de cliente en la autenticación mutua TLS usada para restringir acceso a la aplicación mediante la habilitación de diferentes tipos de autenticación

### **Configurar asignaciones de ruta de acceso**
- Asignaciones de controladores
- Asignaciones de directorios y aplicaciones virtuales
- Las opciones varian según el tipo de S.O.

#### **Windows**
- Asignaciones de controlador de IIS
- Asignaciones de directorios y aplicaciones virtuales

Las asignaciones de controlador **permiten agregar procesadores de script personalizados para controlar solicitudes de extensiones de archivo específicas**.  
El controlador se configura:
  - Extensión: Como `*.php` o `handler.fcgi`
  - Procesador de scripts: Ruta de acceso absoluta
  - Argumentos: de línea de comandos

Ruta predeterminada de una aplicación: `D:\home\site\wwwroot`. Si la raíz está en una carpeta diferente, o el repositorio tiene más de una aplicación, puede editar o agregar directorios y aplicaciones virtuales. Para marcar un directorio virtual como aplicación web, desactiva la casilla **"Directorio"**.

#### **Linux y en contenedor**
**Un contenedor personalizado puede tener Windows o Linux**.  
Posibilidad de agregar almacenamiento personalizado para la aplicación en contenedor.  
**Nuevo montaje de Azure Storage** requiere la configuración:
- Nombre
- Opciones de configuración
- Cuentas de almacenamiento
- Tipo de almacenamiento: Blobs o Files. (En Windows solo Files)
- Contenedor de almacenamiento
- Nombre del recurso compartido
- Clave de acceso
- Ruta de acceso de montaje

### **Activación del registro de diagnóstico**
- Diagnóstico integrado que ayudan a depurar una aplicación. 
- Habilitar el registro y agregar instrumentación a la aplicación
- Acceder a la información que registra Azure.

Tipo|Plataforma|Location|Descripción
---|---|---|---
Registro de aplicaciones|Windows, Linux|Sistema de archivos de App Service o Blobs de Storage|Mensajes generados por el código de aplicación. Categoría: Crítico, Error, Advertencia, Información, Depuración y Seguimiento.
Registro del servidor web|Windows|Sistema de archivos de App Service o Blobs de Storage|Datos de solicitud HTTP sin procesar en el formato de archivo de registro extendido W3C
Registro de errores detallado|Windows|Sistema de archivos de App Service|Copias de las páginas de error .html que se habrían enviado al explorador del cliente
Seguimiento de solicitudes con error|Windows|Sistema de archivos de App Service|Información de seguimiento detallada sobre las solicitudes con error. Se genera una carpeta para cada solicitud con error.
Registro de implementación|Windows, Linux|Sistema de archivos de App Service|Ayuda a determinar por qué se ha producido un error en la implementación.

#### **Habilitación del registro de aplicaciones (Windows)**
- En App Service: Supervisión: Registros de App Service -> Activado:
  1. Registro de la aplicación (Sistema de archivos): Se desactiva en 12 horas
  2. Registro de la aplicación (Blob): Largo plazo y requiere un contenedor de blobs
- Puede establecer el nivel de detalles

#### **Habilitación del registro de aplicaciones (Linux o contenedor)**
- En Supervisión: Registros de App Service: Sistema de archivos
  1. Asignar Cuota(MB)
  2. Período de retención (días)
  3. Adición de mensajes de registro en el código con librería específica.

#### **Transmisión de registros**
En tiempo real, y se debe habilitar el tipo de registro que quiera. Transmite cualquier información de archivos en .txt, .log o .htm de `/LogFiles` (`d:/home/logfiles`)

#### **Acceso a los archivos de registro**
- Si se almacenan en Azure Storage, se debe acceder con una herramienta de cliente
- Si se almacenan en Sistema de archivos de App Service:
  - Linux o contenedor = `https://<app-name>.scm.azurewebsites.net/api/logs/docker/zip`
  - Windows = `https://<app-name>.scm.azurewebsites.net/api/dump`
>Linux o contenedor: Si hay aplicaciones escaladas horizontalmente, ZIP contiene conjunto de registros para cada instancia.

### **Configuración de certificados de seguridad**
Herramientas que permiten crear,cargar o importar un certificado privado o público en App Service.  
- Los certificados cargados se almacenan en **unidad de implementación** enlazada a la región y grupo de recursos del **plan de App Service**. Así los certificados son accesibles por otras aplicaciones de región y grupo de recursos.

Opción|Descripción
---|---
Crear un cert. administrado de App Service gratuito|Si solo necesita proteger el dominio personalizado de App Service
Comprar un cert. de App Service|Administrado por Azure. Automatiza renovación y exportación
Importación de un cert. de Key Vault|Delega a Key Vault la administración
Carga de un cert. privado|Puede cargarlo
Carga de un cert. público|Púbicos no protegen dominios personalizados, pero se pueden cargar en código si necesita acceder a recursos remotos.

#### **Requisitos de certificados privados**
- Archivo PFX protegido por contraseña. Cifrado con Triple DES
- Contener una clave privada con longitud minima de 2048 bits
- Contener certificados intermedios de la cadena de certificados
**Si trata de proteger un dominio personalizado en un enlace TLS...debe cumplir:**
- Contener un uso mejorado de clave para la autenticación de servidor (OID = 1.3.6.1.5.5.7.3.1)
- Firmado por una entidad de certificación de confianza

Si se quiere conocer más a fondo, visualizar la documentación:
https://docs.microsoft.com/es-es/learn/modules/configure-web-app-settings/6-configure-security-certificates

### **Administración de las características de la aplicación**
Es una práctica moderna. Separa lanzamiento de las características de la implementación del código.  
Permite hacer cambios rápidos con la disponibilidad de las características a petición.
- Técnica: Marcas de características (activa/desactiva funcionalidad) para administrar ciclo de vida de una característica.

#### **Conceptos básicos**
- Marca de característica: Variable con estado binario. Bloque de código asociado. El estado se desencadena sin depender del bloque necesariamente.
- Administrador de características: Paquete de aplicación que controla ciclo de vida de todas las marcas de una aplicación. Da funcionalidades extra como almacenamiento en caché de las marcas y actualiza sus estados.
- Filtro: Regla para evaluar estado de una marca.

#### **Declaración de la marca de características**
Cada marca consta de dos partes: nombre y una lista de filtros que evaluan el estado.
- Un filtro define un cas de uso en el que debe activarse una característica.
- El administrador de la característica configura el origen en digamos un "appsettings.json"

```json
"FeatureManagement": {
    "FeatureA": true, // Feature flag set to on
    "FeatureB": false, // Feature flag set to off
    "FeatureC": {
        "EnabledFor": [
            {
                "Name": "Percentage",
                "Parameters": {
                    "Value": 50
                }
            }
        ]
    }
}
```
#### **Repositorio de marcas de características**
Para el uso eficaz, se deben externalizar. Permitiendo cambiar estados sin modificar la propia aplicación.

Azure App Configuration está diseñado para ser el repositorio centralizado para las marcas. Luego usar bibliotecas de App Configuration para acceder a estas marcas desde su aplicación.

## **Escalado de aplicaciones en Azure App Service**
- Escalado automático se acitva en función de una programación o evaluando métricas de recursos(uso de CPU, memoria, solicitudes entrantes u otros).
- El escalado automático **REDUCE HORIZONTALMENTE**.
- Funciona mediante adición o eliminación de servidores web

**¿Cuándo debería considerar el escalado automático?**  
- Los cambios en la carga de la aplicación que son predecibles son buenos candidatos para el escalado automático.
- Carga de trabajo varíe en función de fecha y hora.

El escalado automático no es el enfoque óptimo para controlar el crecimiento a largo plazo. Ya que tiene una sobrecarga en costo asociada a la supervisión de recursos y determinar si se debe desencadenar un evento de escalado.

- **El escalado automático es una característica del plan de App Service** que usa la aplicación web.

#### **Condiciones de la escalabilidad automática**
- Escalado basado en métrica
- Escalado programado.
Ambos pueden combinarse

#### **Métricas para las reglas de escalabilidad**
- Porcentaje de CPU
- Porcentaje de memoría
- Longitud de cola de disco: solicitudes de E/S pendientes
- Longitud de cola HTTP: Solicitudes en espera de procesamiento
- Entrada de datos
- Salida de datos

Mayor información: https://docs.microsoft.com/es-es/learn/modules/scale-apps-app-service/3-app-service-autoscale-conditions-rules

## **Exploración de entornos de ensayo**
Ranura de implementación independiente: Aplicaciones activas con sus propios nombres de host.  
Los elementos y configuraciones de aplicaciones se pueden intercambiar entre dos ranuras (producción incluida).
- Su uso no tiene costo adicional
- Clonar ranuras, solo copia la configuración, no el contenido

Mayor información: https://docs.microsoft.com/es-es/learn/modules/understand-app-service-deployment-slots/2-app-service-staging-environments