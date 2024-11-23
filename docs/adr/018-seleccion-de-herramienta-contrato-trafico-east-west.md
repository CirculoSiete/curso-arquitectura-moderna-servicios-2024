# Elección de herramienta para la definición de contratos en el tráfico East-West

- **Estado:** Aprobado  
- **Fecha de decisión:** 2024-11-21  

## Contexto y problema  

El tráfico **East-West**, que corresponde a la comunicación interna entre servicios, requiere contratos claros y estrictos que:  
- Garanticen la compatibilidad entre servicios en comunicación directa.  
- Permitan una evolución controlada de los contratos para evitar interrupciones en el sistema distribuido.  
- Faciliten la validación automatizada del cumplimiento de los contratos en tiempo de desarrollo y despliegue.  

Debido a la naturaleza de este tráfico, que prioriza la eficiencia y la integridad de los datos, se necesita una herramienta que soporte contratos binarios de alto rendimiento, compatible con el protocolo gRPC.

## Decisión  

Se selecciona **Protocol Buffers (Protobuf)** como herramienta para la definición de contratos en el tráfico East-West, aprovechando su integración nativa con gRPC.

## Justificación  

Protocol Buffers fue seleccionado debido a las siguientes razones:

### Ventajas principales de Protobuf  
- **Formato binario eficiente:** Protobuf genera contratos binarios compactos que minimizan la latencia y el consumo de ancho de banda en la comunicación entre servicios.  
- **Soporte nativo para gRPC:** Protobuf se integra directamente con gRPC, facilitando la generación de código para clientes y servidores en múltiples lenguajes.  
- **Esquema versionado:** Proporciona mecanismos claros para la evolución de los contratos, permitiendo agregar o modificar campos sin romper la compatibilidad con versiones anteriores.  
- **Compatibilidad multiplataforma:** Admite la generación de código en diversos lenguajes (Java, Go, Python, etc.), asegurando interoperabilidad en sistemas heterogéneos.  
- **Validación estricta:** Los contratos definidos en Protobuf actúan como fuente única de verdad, eliminando inconsistencias entre servicios.  

### Beneficios para el tráfico East-West  
- **Alto rendimiento:** La serialización binaria de Protobuf reduce significativamente la latencia en comparación con formatos de texto como JSON o XML.  
- **Comunicación fiable:** La definición estricta de los contratos asegura que los datos intercambiados entre servicios sean consistentes y predecibles.  
- **Desarrollo paralelo:** Equipos pueden trabajar en paralelo sobre contratos predefinidos, generando clientes y servidores automáticamente a partir de los archivos `.proto`.  

## Otras alternativas  

1. **JSON Schema:**  
   - **Ventajas:** Familiaridad y legibilidad para desarrolladores.  
   - **Desventajas:** Menor rendimiento debido al formato de texto, y falta de integración nativa con gRPC.  

2. **Avro (Apache Avro):**  
   - **Ventajas:** Similar a Protobuf en eficiencia y soporte para contratos binarios.  
   - **Desventajas:** Menor adopción y menos soporte nativo en comparación con Protobuf en el ecosistema gRPC.  

3. **Thrift (Apache Thrift):**  
   - **Ventajas:** Soporte para múltiples lenguajes y comunicación eficiente.  
   - **Desventajas:** Más complejo de configurar y con menor adopción en sistemas modernos que usan gRPC.  

## Consecuencias  

**Positivas:**  
- Contratos estrictos que mejoran la confiabilidad y la interoperabilidad entre servicios.  
- Reducción de latencia y optimización del tráfico gracias a la serialización binaria compacta de Protobuf.  
- Facilidad para la generación automática de clientes y servidores en múltiples lenguajes, acelerando el desarrollo.  
- Mecanismos integrados para manejar la evolución de contratos, reduciendo el riesgo de rupturas en el sistema distribuido.  

**Negativas:**  
- Requiere que los desarrolladores estén familiarizados con Protobuf y sus mecanismos de serialización.  
- Introducción de una etapa adicional en el proceso de desarrollo: la definición y mantenimiento de los archivos `.proto`.  
- Puede no ser ideal para casos donde se priorice la legibilidad humana sobre la eficiencia del tráfico.  

## Notas adicionales  

- Integrar validaciones automáticas de los contratos en pipelines CI/CD para asegurar que los servicios cumplen con las definiciones en los archivos `.proto`.  
- Documentar los contratos y versionarlos cuidadosamente para garantizar compatibilidad hacia atrás en un entorno distribuido.  
- Explorar herramientas como **Buf** para gestionar y mantener contratos Protobuf de manera eficiente, incluyendo validaciones de estilo y reglas de linting.  
- Considerar el uso de proxies como Envoy para manejar la seguridad y el monitoreo de tráfico gRPC basado en contratos definidos por Protobuf.  
