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

## **Examen de los planes de Azure App Service**
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

## **Implementación en App Service**