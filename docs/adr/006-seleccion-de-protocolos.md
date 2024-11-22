# Selección de HTTP para tráfico North-South y gRPC para tráfico East-West

- **Estado:** Aprobado  
- **Fecha de decisión:** 2024-11-21  

## Contexto y problema  

En el diseño de la arquitectura del sistema, es necesario definir los protocolos de comunicación para dos tipos de tráfico:  
- **North-South:** Comunicación entre clientes externos y el sistema.  
- **East-West:** Comunicación interna entre servicios dentro del ecosistema.  

El tráfico **North-South** necesita ser accesible a través de protocolos estándar y ampliamente compatibles para asegurar la interoperabilidad con diversos clientes externos, como navegadores, aplicaciones móviles y otros sistemas. Por otro lado, el tráfico **East-West** requiere un protocolo eficiente y de alto rendimiento para minimizar la latencia y el consumo de recursos entre microservicios.

## Decisión  

- **HTTP/REST** será utilizado para el tráfico **North-South**, aprovechando su estándar universal y facilidad de uso.  
- **gRPC** será utilizado para el tráfico **East-West**, priorizando su rendimiento y soporte para comunicación binaria eficiente.  

## Justificación  

La combinación de HTTP y gRPC fue seleccionada por las siguientes razones:

### HTTP para tráfico North-South  
- **Compatibilidad universal:** HTTP/REST es el estándar de facto para la comunicación entre sistemas externos, ampliamente soportado por navegadores, herramientas de API y bibliotecas cliente.  
- **Facilidad de uso:** Los desarrolladores y equipos externos están familiarizados con REST, facilitando la integración.  
- **Herramientas maduras:** Amplio ecosistema de herramientas para testing, documentación (Swagger/OpenAPI) y monitoreo de APIs REST.  

### gRPC para tráfico East-West  
- **Alto rendimiento:** gRPC utiliza comunicación binaria basada en HTTP/2, reduciendo la latencia y el tamaño de los mensajes.  
- **Contratos estrictos:** Definición de interfaces claras mediante archivos `.proto`, que aseguran consistencia entre servicios.  
- **Streaming bidireccional:** Soporte para casos avanzados como transmisión de datos en tiempo real.  
- **Integración fácil:** gRPC se adapta bien a sistemas que operan en entornos de alto rendimiento, como microservicios orquestados con Kubernetes.  

## Otras alternativas  

1. **Usar HTTP para ambos tipos de tráfico:**  
   - **Ventajas:** Simplifica la pila tecnológica al usar un solo protocolo.  
   - **Desventajas:** Mayor latencia y consumo de recursos en la comunicación entre servicios, especialmente en entornos de alto tráfico.  

2. **Usar gRPC para ambos tipos de tráfico:**  
   - **Ventajas:** Proporciona un protocolo eficiente tanto para comunicación interna como externa.  
   - **Desventajas:** Menor adopción y compatibilidad en clientes externos, especialmente navegadores, lo que requeriría proxies o conversiones adicionales.  

3. **AMQP o Kafka para ambos tipos de tráfico:**  
   - **Ventajas:** Excelentes para sistemas event-driven o asincrónicos.  
   - **Desventajas:** No son ideales para tráfico síncrono y requieren configuraciones adicionales.  

## Consecuencias  

**Positivas:**  
- Adopción de un estándar universal (HTTP/REST) para la comunicación con clientes externos.  
- Reducción de latencia y mejora de rendimiento en la comunicación entre microservicios con gRPC.  
- Escalabilidad y claridad en la definición de interfaces internas gracias al uso de `.proto` en gRPC.  
- Flexibilidad para evolucionar las APIs internas sin afectar directamente a los clientes externos.  

**Negativas:**  
- Complejidad añadida al mantener dos protocolos distintos en el sistema.  
- La adopción de gRPC requiere una curva de aprendizaje para equipos que no estén familiarizados con sus conceptos y herramientas.  
- Dependencia de herramientas específicas para generar código a partir de archivos `.proto`.  

## Notas adicionales  

- Los endpoints HTTP/REST deben ser diseñados siguiendo estándares como RESTful y documentados con herramientas como Swagger o OpenAPI.  
- Los servicios internos deben implementar gRPC con contratos bien definidos y versionados para garantizar compatibilidad entre servicios.  
- Monitorear el rendimiento de ambas capas de comunicación (HTTP y gRPC) y realizar ajustes según las necesidades del sistema.  
- En el futuro, se explorará el uso de proxies (como Envoy) para manejar la traducción entre protocolos si se requieren conexiones híbridas.  
