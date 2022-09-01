# **Microsoft Certified: Azure Developer Associate**
## **Temario**
- [**Microsoft Certified: Azure Developer Associate**](#microsoft-certified-azure-developer-associate)
  - [**Temario**](#temario)
  - [**AZ-204: Creación de aplicaciones web de Azure App Service**](#az-204-creación-de-aplicaciones-web-de-azure-app-service)
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

## **AZ-204: Creación de aplicaciones web de Azure App Service**
- Servicio basado en HTTP
- Hospeda app webs, API REST, Back-ends para móviles.
- Soporta múltiples lenguajes (NET, .NET Core, Java, Ruby, Node.js, PHP y Python)
- Entornos Windows y Linux

### **Compatibilidad integrada con el escalado automático**
- Escalado vertical (Mejora en App Service)
- Escalado horizontal (Creación de más instancias en el mismo App Service)
**El escalado se aplica en la MÁQUINA SUBYACENTE en la que se hospeda la App Web**  
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
- Elementos de contenido y configuración de aplicaciones pueden ser intercambios entre ranuras de implementación

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

