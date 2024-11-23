# Elección de herramienta para la definición de contratos en el tráfico North-South (enfoque contract-first)

- **Estado:** Aprobado  
- **Fecha de decisión:** 2024-11-21  

## Contexto y problema  

El tráfico **North-South**, que conecta clientes externos con los servicios del sistema, requiere contratos claros y bien definidos que aseguren:  
- **Consistencia:** Los clientes y servicios interactúan de manera predecible, reduciendo errores y malentendidos en las integraciones.  
- **Evolución controlada:** Los contratos deben gestionarse de manera que los cambios no rompan la compatibilidad con clientes existentes.  
- **Desarrollo alineado:** Permitir que equipos trabajen en paralelo, basándose en contratos previamente acordados.  

Se busca adoptar un enfoque **contract-first**, donde los contratos de la API se definen antes de implementar el servicio, asegurando que las necesidades del cliente se prioricen y que las implementaciones cumplan exactamente con los contratos definidos.

## Decisión  

Se selecciona **OpenAPI** (anteriormente Swagger) como herramienta principal para definir, documentar y validar los contratos de las APIs expuestas en el tráfico North-South, adoptando un enfoque contract-first.

## Justificación  

### Enfoque contract-first con OpenAPI  
El enfoque **contract-first** con OpenAPI fue seleccionado por las siguientes razones:  

1. **Definición inicial:** Los contratos OpenAPI, al ser definidos desde el inicio, actúan como una fuente única de verdad para los equipos de desarrollo y los consumidores de la API.  
2. **Documentación instantánea:** Las definiciones OpenAPI generan automáticamente documentación interactiva (Swagger UI, ReDoc), mejorando la comunicación con los clientes externos.  
3. **Validación desde el principio:** La implementación del servicio se valida contra el contrato definido, garantizando que se cumplan las expectativas de los consumidores.  
4. **Generación de código:** OpenAPI permite generar código base para clientes y servidores, acelerando el desarrollo y reduciendo inconsistencias.  

### Ventajas principales de OpenAPI  
- **Estándar de facto:** Amplia adopción y soporte por parte de herramientas, frameworks y lenguajes, facilitando la interoperabilidad.  
- **Flexibilidad:** Permite definir esquemas detallados, métodos HTTP, códigos de estado y autenticación, cubriendo todos los aspectos necesarios para un contrato completo.  
- **Gestión de cambios:** A través del versionado de contratos, permite gestionar la evolución de las APIs sin romper la compatibilidad hacia atrás (*backward compatibility*).  
- **Integración con herramientas:** Soporte para generación automática de SDKs y pruebas contractuales mediante herramientas como Swagger Codegen, OpenAPI Generator y Dredd.  

### Beneficios para el proyecto  
- **Desarrollo paralelo:** Los equipos de clientes y servidores pueden trabajar en paralelo basándose en un contrato previamente definido.  
- **Aseguramiento de calidad:** Las definiciones contractuales facilitan la automatización de pruebas para validar la conformidad de las implementaciones con el contrato.  
- **Alineación con el cliente:** Los contratos contract-first priorizan los requisitos del cliente antes de la implementación.  

## Otras alternativas  

1. **Code-first con OpenAPI:**  
   - **Ventajas:** Deriva automáticamente el contrato desde el código implementado.  
   - **Desventajas:** El contrato refleja lo que el servicio implementa, en lugar de priorizar las necesidades del cliente.  

2. **GraphQL:**  
   - **Ventajas:** Flexibilidad en consultas, ideal para clientes que necesitan datos dinámicos.  
   - **Desventajas:** No promueve el enfoque contract-first de manera nativa y puede ser excesivamente complejo para APIs REST tradicionales.  

3. **gRPC con Protocol Buffers:**  
   - **Ventajas:** Contratos binarios eficientes y adecuados para tráfico interno.  
   - **Desventajas:** Menor adopción en APIs orientadas a clientes externos, con herramientas de documentación menos avanzadas.  

## Consecuencias  

**Positivas:**  
- Contratos bien definidos desde el inicio, alineando las expectativas entre desarrolladores y consumidores.  
- Documentación de la API generada automáticamente y accesible para los clientes.  
- Reducción de errores y malentendidos en integraciones gracias a validaciones automatizadas contra los contratos.  
- Compatibilidad hacia adelante gestionada a través del versionado explícito de los contratos.  
- Habilitación de un desarrollo paralelo eficiente entre equipos de cliente y servidor.  

**Negativas:**  
- Requiere una fase inicial de diseño más detallada, lo que puede incrementar el tiempo para iniciar el desarrollo.  
- Necesidad de disciplina para mantener los contratos actualizados cuando se realizan cambios en la API.  

## Notas adicionales  

- Integrar validaciones contractuales en el pipeline CI/CD para asegurar que las implementaciones cumplen con las definiciones de OpenAPI.  
- Usar herramientas como Swagger Codegen o OpenAPI Generator para generar bases de código cliente y servidor directamente desde los contratos.  
- Promover un proceso claro de versionado y gestión de contratos para evitar inconsistencias entre entornos o versiones de clientes.  
- Considerar la integración con plataformas de gestión de APIs (por ejemplo, Kong, Apigee) para mejorar el monitoreo y control del ciclo de vida de las APIs basadas en OpenAPI.  
