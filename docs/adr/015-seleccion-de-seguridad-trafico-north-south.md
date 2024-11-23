# Elección de mecanismo de seguridad para el tráfico North-South

- **Estado:** Aprobado  
- **Fecha de decisión:** 2024-11-21  

## Contexto y problema  

El tráfico **North-South**, que corresponde a la comunicación entre clientes externos y el sistema, enfrenta riesgos significativos relacionados con la seguridad. Este tráfico es el principal punto de entrada al sistema, lo que lo hace vulnerable a ataques como:  
- Intercepción de datos (e.g., ataques de hombre en el medio, *MITM*).  
- Accesos no autorizados a los recursos.  
- Falsificación de identidades (*spoofing*).  

Por lo tanto, es necesario implementar un mecanismo de seguridad que garantice:  
- La confidencialidad e integridad de los datos en tránsito.  
- La autenticación y autorización de los usuarios que interactúan con el sistema.  
- La protección contra ataques comunes, como inyección de código o fuerza bruta.  

## Decisión  

Se adopta el siguiente mecanismo de seguridad para el tráfico North-South:  
1. **TLS (Transport Layer Security):** Para cifrar todo el tráfico entre los clientes y los servicios expuestos.  
2. **OAuth 2.0 y OpenID Connect:** Para gestionar la autenticación y autorización de los usuarios y aplicaciones externas.  
3. **Validación de solicitudes:** Aplicación de medidas como *rate limiting*, verificación de firmas en mensajes y validaciones de entrada para prevenir ataques.  

## Justificación  

Este enfoque fue seleccionado debido a las siguientes razones:

### Uso de TLS  
- **Confidencialidad:** Protege los datos en tránsito, asegurando que no puedan ser interceptados o alterados.  
- **Estándar probado:** TLS es ampliamente adoptado y soportado por navegadores, clientes y herramientas modernas.  
- **Facilidad de implementación:** Configurable en servidores web y proxies inversos con certificación de CA confiables (Let’s Encrypt, AWS ACM, etc.).

### Uso de OAuth 2.0 y OpenID Connect  
- **Autenticación robusta:** OpenID Connect extiende OAuth 2.0 para incluir autenticación basada en tokens, como JWT.  
- **Autorización granular:** OAuth 2.0 permite definir permisos y límites precisos sobre los recursos que las aplicaciones externas pueden acceder.  
- **Estándar interoperable:** Facilita la integración con sistemas externos como APIs de terceros y proveedores de identidad (Google, Okta, etc.).  

### Validación de solicitudes  
- **Rate limiting:** Previene ataques de fuerza bruta o abuso mediante la limitación de solicitudes por cliente/IP.  
- **Verificación de firmas:** Garantiza que los mensajes sean enviados por entidades confiables y no hayan sido manipulados.  
- **Sanitización de entradas:** Mitiga riesgos de inyección SQL/XXS al validar los datos enviados por los clientes.  

## Otras alternativas  

1. **HTTP Basic Authentication con TLS:**  
   - **Ventajas:** Sencillez en la configuración inicial.  
   - **Desventajas:** Carece de flexibilidad y escalabilidad para aplicaciones modernas.  

2. **API Keys con TLS:**  
   - **Ventajas:** Fácil de implementar y gestionar.  
   - **Desventajas:** No soporta autenticación de usuarios ni autorización granular.  

3. **JWT sin OAuth 2.0:**  
   - **Ventajas:** Tokens ligeros y fáciles de transportar.  
   - **Desventajas:** Sin un marco de autorización como OAuth, se pierde control sobre los permisos y flujos de autenticación.  

## Consecuencias  

**Positivas:**  
- Tráfico cifrado, protegiendo los datos contra intercepciones y ataques.  
- Sistema de autenticación y autorización robusto que se adapta a aplicaciones modernas.  
- Prevención de ataques comunes mediante validaciones adicionales y controles en el tráfico.  
- Compatibilidad con servicios y estándares ampliamente soportados, asegurando interoperabilidad.  

**Negativas:**  
- Aumento en la complejidad inicial de configuración, especialmente al integrar OAuth 2.0 y OpenID Connect.  
- Necesidad de renovar y gestionar certificados TLS de manera periódica.  
- Dependencia en proveedores de autenticación externa si se integran servicios de terceros.  

## Notas adicionales  

- Se recomienda utilizar **Let’s Encrypt** o servicios de gestión de certificados como **AWS Certificate Manager** para la implementación y renovación automática de certificados TLS.  
- Configurar un proxy inverso (como NGINX o Envoy) para centralizar la gestión de TLS y validación de solicitudes.  
- Integrar un proveedor de identidad confiable (por ejemplo, Keycloak, Okta o Auth0) para gestionar OAuth 2.0 y OpenID Connect.  
- Implementar políticas de *rate limiting* en la puerta de entrada para mitigar abusos en el tráfico.  
