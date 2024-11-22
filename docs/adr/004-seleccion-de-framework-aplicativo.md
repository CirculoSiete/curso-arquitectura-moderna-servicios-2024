# Selección de Spring Boot como framework aplicativo

- **Estado:** Aprobado  
- **Fecha de decisión:** 2024-11-21  

## Contexto y problema  

El proyecto requiere un framework que facilite la implementación de una arquitectura hexagonal (puertos y adaptadores) y ofrezca soporte para diversos protocolos de comunicación:  
- HTTP para comunicación REST.  
- gRPC para servicios internos de alto rendimiento.  
- Mensajería basada en AMQP (RabbitMQ) y/o Kafka para sistemas event-driven.  

Adicionalmente, es necesario que el framework sea ampliamente adoptado, cuente con una comunidad activa y permita escalar de manera efectiva.

## Decisión  

Se ha decidido utilizar **Spring Boot** como framework aplicativo para desarrollar la solución.  

Spring Boot proporciona un conjunto de herramientas robustas y preconfiguradas que permiten desarrollar rápidamente aplicaciones basadas en Java, alineándose perfectamente con los principios de la arquitectura hexagonal y soportando los protocolos requeridos.

## Justificación  

Spring Boot fue seleccionado debido a las siguientes razones:  
- **Soporte para arquitectura hexagonal:**  
  - Permite una clara separación de las capas de dominio, infraestructura y aplicación gracias a su flexibilidad en la organización del código y el uso de dependencias.  
  - Es compatible con principios como Inversión de Control y programación orientada a interfaces, esenciales para implementar puertos y adaptadores.  

- **Protocolos de comunicación:**  
  - **HTTP:** Soporte nativo y avanzado para REST a través de Spring Web.  
  - **gRPC:** Integración fluida mediante bibliotecas como `spring-boot-starter-grpc` y herramientas de terceros.  
  - **AMQP:** Soporte completo para RabbitMQ mediante `spring-amqp`.  
  - **Kafka:** Integración nativa con `spring-kafka` para sistemas basados en eventos.  

- **Ecosistema maduro:** Amplia comunidad de desarrolladores, documentación completa y disponibilidad de recursos educativos.  
- **Facilidad de configuración:** La configuración basada en propiedades simplifica la conexión con tecnologías externas.  
- **Escalabilidad:** Soporte para microservicios y despliegues en la nube, con herramientas como Spring Cloud.  

## Otras alternativas  

1. **Quarkus:**  
   - **Ventajas:** Arranque rápido y bajo consumo de memoria.  
   - **Desventajas:** Comunidad más pequeña en comparación con Spring Boot y menor integración nativa con herramientas como Kafka o RabbitMQ.  

2. **Micronaut:**  
   - **Ventajas:** Buen soporte para microservicios y bajo overhead.  
   - **Desventajas:** Menor flexibilidad para proyectos de gran escala y menos ejemplos de implementación para gRPC.  

3. **Dropwizard:**  
   - **Ventajas:** Simplicidad y ligereza.  
   - **Desventajas:** Enfoque principal en REST, con soporte limitado para otros protocolos como Kafka o gRPC.  

## Consecuencias  

**Positivas:**  
- Productividad acelerada gracias a las herramientas preconfiguradas y el soporte integrado para múltiples protocolos.  
- Alineación con los principios de la arquitectura hexagonal, facilitando la mantenibilidad y evolución del sistema.  
- Reducción del tiempo de desarrollo inicial y facilidad de integración con sistemas externos.  
- Comunidad activa que asegura soporte y actualizaciones frecuentes.  

**Negativas:**  
- Curva de aprendizaje inicial para desarrolladores que no estén familiarizados con Spring Boot.  
- La configuración y uso de gRPC puede requerir bibliotecas adicionales, ya que no está soportado de manera nativa por el core de Spring Boot.  
- Tiempo de arranque de la aplicación y uso de recursos ligeramente superiores comparado con alternativas como Quarkus o Micronaut.  

## Notas adicionales  

- Se recomienda crear un conjunto inicial de configuraciones reutilizables para cada protocolo (HTTP, gRPC, Kafka, RabbitMQ).  
- Es importante asegurar que las configuraciones no acoplen la infraestructura con el núcleo del dominio, respetando los principios de la arquitectura hexagonal.  
- Se explorará el uso de Spring Cloud para la gestión de configuración y descubrimiento de servicios en futuros desarrollos.  
