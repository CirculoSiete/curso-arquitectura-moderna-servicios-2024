# Elección de mecanismo de seguridad para el tráfico East-West con gRPC

- **Estado:** Aprobado  
- **Fecha de decisión:** 2024-11-21  

## Contexto y problema  

El tráfico **East-West**, que corresponde a la comunicación interna entre servicios, es fundamental para el correcto funcionamiento del sistema. Aunque este tráfico no está directamente expuesto al exterior, sigue siendo vulnerable a:  
- Interceptaciones internas no autorizadas.  
- Accesos no autenticados entre servicios.  
- Manipulación de mensajes.  

Es necesario implementar un mecanismo de seguridad que:  
- Garantice la autenticación y autorización entre servicios.  
- Proteja la confidencialidad e integridad de los mensajes en tránsito.  
- Sea compatible con las características de alto rendimiento y eficiencia que proporciona gRPC.  

## Decisión  

Se adopta el siguiente mecanismo de seguridad para el tráfico East-West:  
1. **TLS Mutuo (mTLS):** Para cifrar todo el tráfico gRPC y autenticar tanto el cliente como el servidor.  
2. **Validación de Identidades entre Servicios:** Uso de certificados únicos o JWT (convergen a mTLS o como alternativa adicional) para garantizar que solo servicios autorizados puedan comunicarse.  
3. **Control de Autorización:** Aplicación de políticas de autorización explícitas en los servidores gRPC para controlar los accesos según roles o reglas predefinidas.  

## Justificación  

Este enfoque fue seleccionado por las siguientes razones:

### Uso de mTLS  
- **Confidencialidad:** Protege todos los mensajes gRPC en tránsito con cifrado de extremo a extremo.  
- **Autenticación mutua:** Cada extremo (cliente y servidor) se autentica mediante certificados, eliminando riesgos de identidad falsa.  
- **Estándar probado:** mTLS es ampliamente utilizado en sistemas distribuidos y compatible con el protocolo HTTP/2 utilizado por gRPC.  

### Uso de validación de identidades  
- **Control de acceso:** Garantiza que solo servicios autorizados puedan conectarse mediante certificados o tokens.  
- **Compatibilidad con entornos dinámicos:** Herramientas como Istio o Envoy pueden generar y renovar certificados automáticamente, simplificando la gestión en entornos como Kubernetes.  

### Control de autorización  
- **Políticas granulares:** Permite definir reglas de acceso precisas por servicio, método o recurso, reduciendo el riesgo de accesos indebidos.  
- **Compatibilidad nativa con gRPC:** gRPC permite implementar interceptores para validar roles, permisos y tokens en cada solicitud.  

## Otras alternativas  

1. **TLS unidireccional:**  
   - **Ventajas:** Proporciona cifrado y autentica el servidor.  
   - **Desventajas:** No autentica el cliente, dejando abierta la posibilidad de accesos no autorizados.  

2. **Validación de tokens sin mTLS:**  
   - **Ventajas:** Simplicidad en la gestión inicial.  
   - **Desventajas:** Sin cifrado nativo, los mensajes pueden ser vulnerables a intercepciones si no están dentro de una red segura.  

3. **Sin seguridad adicional (confianza en red interna):**  
   - **Ventajas:** Reduce la complejidad operativa inicial.  
   - **Desventajas:** Riesgo de ataques internos si se compromete la red, además de falta de cumplimiento de estándares modernos de seguridad.  

## Consecuencias  

**Positivas:**  
- Garantía de que solo servicios autenticados puedan comunicarse dentro del sistema.  
- Cifrado de extremo a extremo que protege los datos en tránsito de accesos no autorizados.  
- Reducción del riesgo de manipulaciones o intercepciones en el tráfico interno.  
- Cumplimiento con estándares modernos de seguridad para sistemas distribuidos.  

**Negativas:**  
- Aumenta la complejidad operativa inicial, especialmente al configurar y gestionar certificados para mTLS.  
- Impacto menor en el rendimiento debido al cifrado, aunque manejable con configuraciones modernas.  
- Requiere monitoreo y rotación de certificados para evitar expiraciones o compromisos de seguridad.  

## Notas adicionales  

- Se recomienda utilizar herramientas como **Istio**, **Linkerd**, o **Envoy** para gestionar mTLS y certificados automáticamente en entornos Kubernetes.  
- Configurar la validación de identidades mediante un sistema centralizado, como un proveedor de identidad o un servicio de gestión de certificados (por ejemplo, SPIFFE/SPIRE).  
- Definir políticas explícitas de autorización utilizando interceptores gRPC o herramientas externas como OPA (Open Policy Agent).  
- Monitorear métricas de seguridad y rendimiento para asegurar que las configuraciones sean óptimas para el tráfico interno.  
