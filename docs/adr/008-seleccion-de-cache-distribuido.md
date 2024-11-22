# Elección de Redis como caché distribuido

- **Estado:** Aprobado  
- **Fecha de decisión:** 2024-11-21  

## Contexto y problema  

El sistema necesita una solución de caché distribuido para:  
- Reducir la latencia en las operaciones que requieren acceso frecuente a datos costosos de calcular o recuperar.  
- Descentralizar el almacenamiento en memoria para garantizar la escalabilidad en entornos con múltiples instancias de aplicación.  
- Soportar casos como almacenamiento temporal de sesiones, resultados de consultas y datos de configuración frecuentemente accedidos.

La solución debe ser confiable, rápida y capaz de integrarse con el ecosistema tecnológico existente.

## Decisión  

Se selecciona **Redis** como caché distribuido para el sistema. Redis es una base de datos en memoria de alta velocidad que soporta múltiples estructuras de datos y patrones de uso.

## Justificación  

Redis fue seleccionado por las siguientes razones:

### Características principales de Redis  
- **Velocidad:** Redis opera completamente en memoria, con tiempos de respuesta en el rango de microsegundos, lo que la convierte en una de las soluciones más rápidas para almacenamiento de datos temporal.  
- **Estructuras de datos avanzadas:** Además de claves y valores simples, soporta listas, conjuntos, hashes, streams y más, proporcionando flexibilidad para diversos casos de uso.  
- **Compatibilidad distribuida:** Redis ofrece soporte nativo para réplicas y particionamiento a través de Redis Cluster, asegurando escalabilidad horizontal.  
- **Persistencia opcional:** Aunque es principalmente una solución en memoria, Redis puede persistir datos en disco si se requiere.  
- **Fácil integración:** Compatible con casi todos los lenguajes y frameworks modernos, incluyendo soporte directo en Spring Boot.  

### Casos específicos de uso  
- **Cacheo de resultados de consultas:** Almacenar resultados de consultas frecuentes para evitar accesos repetitivos a la base de datos principal.  
- **Gestión de sesiones:** Utilizar Redis para manejar sesiones distribuidas en sistemas con múltiples nodos.  
- **Rate Limiting y Token Buckets:** Utilizar estructuras de datos para implementar límites de solicitudes por usuario o IP.  

## Otras alternativas  

1. **Memcached:**  
   - **Ventajas:** Más simple y ligero para claves y valores simples.  
   - **Desventajas:** Carece de soporte para estructuras de datos avanzadas y persistencia, lo que limita su flexibilidad.  

2. **Hazelcast:**  
   - **Ventajas:** Proporciona caché distribuido y capacidades de computación distribuida.  
   - **Desventajas:** Más complejo de configurar y no tan rápido como Redis en operaciones de lectura/escritura.  

3. **Caffeine:**  
   - **Ventajas:** Excelente para almacenamiento en memoria local en una sola JVM.  
   - **Desventajas:** No es distribuido, por lo que no se escala fácilmente en sistemas con múltiples instancias.  

## Consecuencias  

**Positivas:**  
- Reducción significativa de la latencia en operaciones frecuentes gracias a la velocidad en memoria de Redis.  
- Escalabilidad horizontal para soportar un creciente volumen de datos y usuarios.  
- Flexibilidad para implementar múltiples patrones de uso debido al soporte de estructuras avanzadas.  
- Integración sencilla con herramientas y frameworks del ecosistema existente.  

**Negativas:**  
- Redis opera principalmente en memoria, lo que puede limitar la capacidad si el almacenamiento no se maneja cuidadosamente.  
- Requiere configuración y monitoreo adicional en entornos distribuidos para evitar problemas como "hot keys" o particionamiento ineficiente.  
- Persistencia opcional puede ser más lenta en comparación con bases de datos diseñadas específicamente para almacenamiento persistente.  

## Notas adicionales  

- Es importante implementar políticas de expiración de claves (`TTL`) para evitar el crecimiento no controlado del caché.  
- Considerar el uso de Redis Sentinel o Redis Cluster para alta disponibilidad y failover automático.  
- Monitorear métricas como tasas de aciertos, tasas de expiración y latencias para optimizar el rendimiento del caché.  
- Evaluar el uso de Redis como complemento para otras soluciones en casos avanzados, como procesamiento en tiempo real con streams.  
