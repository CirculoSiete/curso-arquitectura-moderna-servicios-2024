# Elección de RabbitMQ como broker de mensajería

- **Estado:** Aprobado  
- **Fecha de decisión:** 2024-11-21  

## Contexto y problema  

El sistema requiere un broker de mensajería para implementar patrones de comunicación asincrónica entre servicios, soportando casos de uso como:  
- Envío de mensajes puntuales con confirmación de recepción.  
- Procesamiento distribuido mediante colas de trabajo.  
- Flexibilidad para soportar sistemas event-driven y flujos transaccionales.

Es necesario seleccionar una solución que sea fácil de configurar, flexible y adecuada para escenarios de baja latencia en la entrega de mensajes.

## Decisión  

Se selecciona **RabbitMQ** como broker de mensajería debido a su madurez, flexibilidad y adecuación para patrones tradicionales de mensajería basados en colas y tópicos.

## Justificación  

RabbitMQ fue seleccionado por las siguientes razones:

### Comparación con Kafka  

- **Modelo de mensajería tradicional:** RabbitMQ utiliza un modelo basado en colas y tópicos, lo que lo hace ideal para aplicaciones que necesitan patrones como Pub/Sub o colas de trabajo con distribución equitativa entre consumidores.  
- **Confirmaciones de mensaje:** RabbitMQ permite confirmaciones explícitas de mensajes por parte de los consumidores, lo que asegura que los mensajes no se pierdan y evita reentregas innecesarias.  
- **Flexibilidad en patrones:** Soporta una amplia variedad de patrones de comunicación, como colas punto a punto, enrutamiento complejo y encabezados personalizados. Kafka, por otro lado, está más orientado a casos de uso event streaming y persistencia.  
- **Facilidad de uso:** RabbitMQ tiene una curva de aprendizaje más suave y es más simple de configurar para aplicaciones tradicionales de mensajería.  
- **Compatibilidad:** RabbitMQ utiliza el protocolo AMQP, ampliamente soportado en múltiples lenguajes y frameworks, mientras que Kafka utiliza un protocolo propietario.  

### Características adicionales de RabbitMQ  

- **Extensiones avanzadas:** Ofrece plugins como TTL (Time to Live) para mensajes, priorización de colas y soporte para esquemas personalizados.  
- **Transacciones:** Manejo robusto de transacciones de mensajes para garantizar la consistencia en flujos críticos.  
- **Administración intuitiva:** Incluye un panel de administración gráfico para monitoreo y gestión en tiempo real.  
- **Integración:** Amplia compatibilidad con entornos cloud y herramientas de orquestación como Kubernetes.  

## Otras alternativas  

1. **Kafka:**  
   - **Ventajas:** Ideal para grandes volúmenes de datos y persistencia de logs distribuidos.  
   - **Desventajas:** Menos adecuado para patrones tradicionales de colas o Pub/Sub con confirmación de mensajes.  

2. **ActiveMQ:**  
   - **Ventajas:** Similar a RabbitMQ en funcionalidad y soporte para AMQP.  
   - **Desventajas:** Menos activo en la comunidad y con menor rendimiento en entornos de alto tráfico.  

3. **Redis Streams:**  
   - **Ventajas:** Alto rendimiento y simplicidad para sistemas de baja latencia.  
   - **Desventajas:** Menor flexibilidad para patrones complejos de mensajería y sin soporte robusto para confirmaciones de mensajes.  

## Consecuencias  

**Positivas:**  
- Implementación sencilla de patrones como Pub/Sub y colas de trabajo con enrutamiento flexible.  
- Mayor control sobre el procesamiento de mensajes gracias a confirmaciones explícitas.  
- Facilidad de integración en entornos cloud o híbridos.  
- Panel de monitoreo y administración intuitivo, ideal para la operación diaria.  

**Negativas:**  
- Puede no ser tan eficiente como Kafka para casos de uso de alto volumen y retención histórica de eventos.  
- Requiere monitoreo cuidadoso para evitar cuellos de botella en escenarios con miles de consumidores o colas extremadamente largas.  

## Notas adicionales  

- Se recomienda configurar un mecanismo de reintento y DLQ (Dead Letter Queue) para manejar mensajes que no puedan ser procesados.  
- Es importante monitorear métricas como tasas de entrega, confirmaciones y tiempos de procesamiento para optimizar el rendimiento.  
- Explorar plugins de RabbitMQ según los casos de uso (por ejemplo, para enrutamiento dinámico o control de prioridad).  
- Considerar RabbitMQ como complemento de Kafka en sistemas híbridos donde se necesiten tanto patrones tradicionales como event streaming.  
