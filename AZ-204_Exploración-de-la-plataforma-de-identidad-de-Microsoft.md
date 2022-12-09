# **Microsoft Certified: Azure Developer Associate - Exploración de la plataforma de identidad de Microsoft**
## **Temario**
- [**Microsoft Certified: Azure Developer Associate - Exploración de la plataforma de identidad de Microsoft**](#microsoft-certified-azure-developer-associate---exploración-de-la-plataforma-de-identidad-de-microsoft)
  - [**Temario**](#temario)
  - [**Exploración de la plataforma de identidad de Microsoft**](#exploración-de-la-plataforma-de-identidad-de-microsoft)
    - [**Exploración de las entidades de servicio**](#exploración-de-las-entidades-de-servicio)
      - [**Objeto de aplicación**](#objeto-de-aplicación)
      - [**Objeto de entidad de servicio**](#objeto-de-entidad-de-servicio)
        - [**Aplicación**](#aplicación)
        - [**Identidad administrada**](#identidad-administrada)
        - [**Heredado**](#heredado)
      - [**Relación entre objetos de aplicación y las entidades de servicio**](#relación-entre-objetos-de-aplicación-y-las-entidades-de-servicio)
    - [**Información sobre los permisos y el consentimiento**](#información-sobre-los-permisos-y-el-consentimiento)
      - [**Tipos de permisos**](#tipos-de-permisos)
      - [**Tipos de consentimiento**](#tipos-de-consentimiento)
        - [**Consentimiento del usuario estático**](#consentimiento-del-usuario-estático)
        - [**Consentimiento del usuario incremental**](#consentimiento-del-usuario-incremental)
        - [**Consentimiento del administrador**](#consentimiento-del-administrador)
      - [**Solicitud de consentimiento de usuario individual**](#solicitud-de-consentimiento-de-usuario-individual)
    - [**Información sobre el acceso condicional**](#información-sobre-el-acceso-condicional)
      - [**¿Cómo el acceso condicional afecta a una aplicación?**](#cómo-el-acceso-condicional-afecta-a-una-aplicación)

## **Exploración de la plataforma de identidad de Microsoft**
- Ayuda a compilar aplicaciones en que usuarios y clientes inician sesión mediante identidades de Microsoft o cuentas de redes sociales.
- Así como proporcionar acceso autorizado a sus API o API de Microsoft

Compuesta por varios componentes:
- Servicio de autenticación compatible con los estándares OAuth 2.0 y OpenID Connect: Autenticar varios tipos de identidades
  - Profesionales o educativas -> Azure Active Directory
  - Personas de Microsoft (Skype,Xbox,Outlook)
  - Sociales o locales mediante Azure Active Directory B2C
- Bibliotecas de código abierto: (MSAL) y otras
- Portal de administración de aplicaciones: Registro y configuración en Azure Portal
- PowerShell y API de configuración de aplicaciones: GraphAPI y PowerShell, para que se pueda automatizar las tareas de DevOps.

### **Exploración de las entidades de servicio**
Para delegar funciones de indeitidad y acceso a Azure AD
- Debe registrar una aplicación con un inquilino de Azure AD
- Asi se crea una configuración de identidad para la aplicación
- Al registrar una aplicación en Azure Portal, se debe elegir:
  - Inquilino único: Solo accesible en el inquilino
  - Multiinquilino: Accesible en otros inquilinos

Al registrar, se crearán automáticamente un objeto de aplicación y de entidad de servicio en el inquilino principal.

#### **Objeto de aplicación**
Una aplicación de Azure AD se define en un objeto único, reside en el iniquilino de Azure AD donde se registró.
- Este objeto se usa como plantilla o plano técnico para crear uno o varios objetos de **entidad de servicio**.

- De forma similar a una clave (obj de aplicación), tiene algunas propiedades estáticas que se aplican a todas las **entidades de servicio** creadas (o instancias de aplicacón).

#### **Objeto de entidad de servicio**
- Para acceder a lso recursos que protege un inquilino de Azure AD, la entidad que requiere acceso debe estar representada por una entidades de seguridad (de usuario, de servicio).
-  La entidad de servicio es para aplicaciones.
-  La entidad de seguridad define directiva de acceso y los permisos.
-  Habilita así características como AuthN de usuario o aplicación durante inicio de sesión y AuthZ durante acceso a los recursos

- Hay tres tipos de entidades de servicio  
##### **Aplicación**
Instancia de aplicación de un objeto de aplicación global en un único inquilino. 
- la entidad de servicio se crea en cada inquilino donde se usa la aplicación y hace referencia al objeto de aplicación único global.
- Define lo que la aplicación puede hacer en el inquilino específico
##### **Identidad administrada**
- Más información: https://docs.microsoft.com/es-es/learn/modules/explore-microsoft-identity-platform/3-app-service-principals
##### **Heredado**
- Más información: https://docs.microsoft.com/es-es/learn/modules/explore-microsoft-identity-platform/3-app-service-principals

#### **Relación entre objetos de aplicación y las entidades de servicio**
- Objeto de aplicación: Representación global de la aplicación para su uso en todos los inquilinos
- Entidad de servicio: Representación local para su uso en un inquilino específico.

Obj de aplicación actúa como plantilla
Obj de entidad de servicio recibe propiedades comunes y predeterminadas que derivan de plantilla.

### **Información sobre los permisos y el consentimiento**
La plataforma de identidad de Microsoft implemente **OAuth 2.0**.  
Cualquier recurso hospedado en Web que se integre con la plataforma tiene un identificador de recursos o un URI de identificador de aplicación.  
Mayor información: https://docs.microsoft.com/es-es/training/modules/explore-microsoft-identity-platform/4-permission-consent

#### **Tipos de permisos**
La Plataforma de identidad de Microsoft admite dos:
- Permisos delegados: Aplicaciones que tienen usuario con sesión iniciada. Usuario o administrador dan su consentimiento para los permisos que la aplicación requiere.
- Permisos de aplicación: Aplicaciones que se ejecutan sin presencia de un usuario con sesión iniciada. Ejm: demonios o servicios en segundo plano. Solo un administrador puede dar consentimiento

#### **Tipos de consentimiento**
Las aplicaciones de la Plataforma de identidad de Microsoft dependen del consentimiento para poder acceder a los recursos o las API necesarios.
- Consentimiento del usuario estático
- Consentimiento del usuario incremental
- Consentimiento del administrador

##### **Consentimiento del usuario estático**
Especificar todos los permisos que necesita en la configuración de la aplicación en Azure Portal.
##### **Consentimiento del usuario incremental**
Solicitar conjunto mínimo de permisos por adelantado y solicitar más con el tiempo.
- Solo se aplica a permisos delegados
- El conjunto de permisos se considera bajo un `scope`.
##### **Consentimiento del administrador**
Si aplicación necesita acceder a permisos con privilegios elevados.  
Garantiza que administradores dispongan de algunos controles adicionales antes de autorizar a las aplicaciones o usuarios.

#### **Solicitud de consentimiento de usuario individual**
Más información: https://docs.microsoft.com/es-es/training/modules/explore-microsoft-identity-platform/4-permission-consent

### **Información sobre el acceso condicional**
Acceso condicional de Azure AD ofrece:
- Desarrolladores y cliente empresariales protejan los servicios bajo:
  - Autenticación multifactor
  - Autorización para que solo dispotivos inscritos en Intune accedan a servicios especificados
  - Restricción de ubicaciones de usuario e intervalos IP

#### **¿Cómo el acceso condicional afecta a una aplicación?**
- Acceso condicional no cambia el comportamiento de una aplicación
- Determinados casos cuando una aplicación solicita indirectamente o de forma silenciosa un token para un servicio, requiere cambios de código para controlar los desafíos del acceso condicional.

Más información: https://docs.microsoft.com/es-es/training/modules/explore-microsoft-identity-platform/5-conditional-access