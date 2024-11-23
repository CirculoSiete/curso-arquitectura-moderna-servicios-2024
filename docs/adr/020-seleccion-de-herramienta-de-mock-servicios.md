# Elección de Microcks como herramienta de mock de servicios externos

- **Estado:** Aprobado  
- **Fecha de decisión:** 2024-11-21  

## Contexto y problema  

El proyecto interactúa con múltiples servicios externos, lo que introduce desafíos en los procesos de desarrollo y pruebas:  
- La dependencia de servicios externos durante las pruebas puede ser poco confiable debido a su disponibilidad o tiempo de respuesta.  
- Simular diferentes respuestas, errores y escenarios de servicios externos es esencial para pruebas robustas.  
- Requiere mantener consistencia entre los contratos definidos y los mocks utilizados en las pruebas.  

Es necesario adoptar una herramienta que permita crear y gestionar mocks de servicios externos de manera eficiente, compatible con estándares de definición de APIs como OpenAPI, AsyncAPI o WSDL.

## Decisión  

Se selecciona **Microcks** como herramienta para la creación y gestión de mocks de servicios externos. Microcks proporciona un enfoque basado en contratos para simular servicios HTTP, REST, SOAP, gRPC y mensajería.

## Justificación  

### Ventajas principales de Microcks  
- **Contract-first:** Microcks utiliza definiciones estándar como OpenAPI, AsyncAPI o WSDL para generar mocks automáticamente, asegurando consistencia entre los contratos y las simulaciones.  
- **Compatibilidad multiplataforma:** Soporta múltiples protocolos de comunicación, incluyendo HTTP, gRPC, Kafka y AMQP, permitiendo simular servicios RESTful, SOAP y sistemas event-driven.  
- **Gestión centralizada:** Proporciona una interfaz web para administrar y visualizar los servicios simulados, facilitando la colaboración y la trazabilidad.  
- **Simulación dinámica:** Permite configurar respuestas dinámicas basadas en reglas o patrones, simulando diferentes escenarios y comportamientos de servicios externos.  
- **Integración con CI/CD:** Compatible con pipelines de integración continua, permitiendo ejecutar pruebas contra servicios simulados en entornos de desarrollo y prueba.  

### Beneficios específicos para el proyecto  
- **Aceleración de pruebas:** Los desarrolladores pueden realizar pruebas locales o integradas sin depender de los servicios externos en tiempo real.  
- **Flexibilidad en escenarios:** Permite simular respuestas exitosas, errores y tiempos de espera configurables, cubriendo una amplia gama de casos de prueba.  
- **Consistencia:** Al estar basado en contratos, asegura que los mocks reflejen fielmente la estructura y el comportamiento esperado de los servicios reales.  

## Otras alternativas  

1. **WireMock:**  
   - **Ventajas:** Ligero y fácil de configurar para simulaciones locales de servicios REST.  
   - **Desventajas:** No ofrece soporte nativo para contratos o protocolos como gRPC o mensajería.  

2. **Hoverfly:**  
   - **Ventajas:** Ideal para pruebas de captura y reproducción de tráfico HTTP.  
   - **Desventajas:** No tiene soporte nativo para contratos como OpenAPI o AsyncAPI.  

3. **Custom Mocks (implementación propia):**  
   - **Ventajas:** Total control sobre los detalles de simulación.  
   - **Desventajas:** Requiere desarrollo y mantenimiento manual, incrementando la complejidad operativa.  

## Consecuencias  

**Positivas:**  
- Reducción de la dependencia de servicios externos durante las pruebas, mejorando la velocidad y confiabilidad del proceso de desarrollo.  
- Consistencia entre los contratos definidos y los servicios simulados, alineando las expectativas entre equipos.  
- Soporte para múltiples protocolos, permitiendo pruebas integrales en diferentes escenarios y contextos de comunicación.  
- Gestión centralizada de mocks que facilita la colaboración en equipos grandes y distribuidos.  

**Negativas:**  
- Requiere configuración inicial y familiarización con la interfaz de Microcks para optimizar su uso.  
- Introduce una dependencia adicional en el ecosistema del proyecto, aunque ligera y de bajo riesgo.  

## Notas adicionales  

- Integrar Microcks en los pipelines CI/CD para ejecutar pruebas automatizadas contra los servicios simulados en entornos de desarrollo y prueba.  
- Usar definiciones contractuales estándar como OpenAPI y AsyncAPI para generar automáticamente los mocks de los servicios externos.  
- Configurar respuestas dinámicas en Microcks para simular errores comunes, tiempos de espera y escenarios excepcionales en los servicios externos.  
- Monitorear los contratos y actualizar los mocks automáticamente cuando cambien los contratos de los servicios reales.  
