# Elección de Testcontainers como herramienta para el uso de contenedores en pruebas

- **Estado:** Aprobado  
- **Fecha de decisión:** 2024-11-21  

## Contexto y problema  

El proyecto requiere un entorno de pruebas que permita:  
- Probar interacciones con componentes externos (bases de datos, brokers de mensajería, APIs externas) de manera confiable y reproducible.  
- Evitar dependencias de entornos compartidos en pruebas locales, integradas y de integración continua.  
- Simular entornos reales utilizando contenedores, pero con una configuración simple y dinámica.  

Es necesario que la solución sea flexible, fácil de integrar con los frameworks de pruebas existentes y eficiente en términos de tiempo de configuración.

## Decisión  

Se selecciona **Testcontainers** como herramienta para el uso de contenedores en pruebas. Testcontainers es una biblioteca de Java que permite ejecutar contenedores Docker de manera programática como parte de los tests.

## Justificación  

### Ventajas principales de Testcontainers  

1. **Entornos realistas:**  
   - Proporciona contenedores configurados dinámicamente para pruebas, incluyendo bases de datos, brokers de mensajería, caches y más.  
   - Los contenedores reflejan los servicios utilizados en producción, garantizando confiabilidad en las pruebas.  

2. **Integración con frameworks de pruebas:**  
   - Soporte nativo para JUnit 4, JUnit 5 y Spock, lo que simplifica su adopción en proyectos Java.  
   - Configuración de contenedores directamente en las pruebas, eliminando la necesidad de scripts externos.  

3. **Aislamiento de pruebas:**  
   - Cada prueba puede ejecutarse en un entorno aislado, evitando interferencias entre tests y aumentando su confiabilidad.  

4. **Flexibilidad:**  
   - Soporte para múltiples servicios y tecnologías: bases de datos (PostgreSQL, MySQL), Kafka, RabbitMQ, Redis, y más.  
   - Configuración dinámica de puertos, redes y volúmenes para simular escenarios avanzados.  

5. **Eficiencia:**  
   - Usa contenedores persistentes entre ejecuciones de tests cuando es posible, reduciendo el tiempo de inicialización.

6. **Reproducibilidad:** 
   - Cada prueba se ejecuta en un contenedor fresco, asegurando que no haya interferencias entre pruebas.  
   

### Beneficios específicos para el proyecto  
- **Pruebas confiables:** Las pruebas integradas con bases de datos, mensajería o APIs externas serán consistentes y reproducibles.  
- **Simulación de errores:** Permite simular fallos de red, desconexiones o tiempos de espera para probar la resiliencia del sistema.  
- **Desarrollo local:** Los desarrolladores pueden ejecutar pruebas completas sin necesidad de servicios locales configurados manualmente.  

## Otras alternativas  

1. **Docker Compose para pruebas:**  
   - **Ventajas:** Permite configurar múltiples servicios como un entorno único para pruebas.  
   - **Desventajas:** No está diseñado para pruebas dinámicas y requiere configuraciones manuales.  

2. **Mock de servicios:**  
   - **Ventajas:** Simula servicios externos sin necesidad de contenedores.  
   - **Desventajas:** No refleja el comportamiento real de los servicios externos.  

3. **Entornos compartidos:**  
   - **Ventajas:** Menor complejidad inicial en pruebas locales.  
   - **Desventajas:** Riesgo de interferencia entre pruebas, falta de aislamiento y necesidad de acceso constante a entornos compartidos.  

## Consecuencias  

**Positivas:**  
- Aumenta la confiabilidad de las pruebas al utilizar servicios reales en contenedores aislados.  
- Facilita la adopción de prácticas de integración continua con entornos de pruebas consistentes en cualquier máquina o pipeline.  
- Alineación con entornos de producción al usar las mismas tecnologías y configuraciones en pruebas.  
- Reducción de errores relacionados con diferencias entre entornos de desarrollo y producción.  

**Negativas:**  
- Dependencia de Docker para ejecutar contenedores, lo que puede requerir configuraciones específicas en entornos CI/CD.  
- Curva de aprendizaje inicial para configuraciones avanzadas o personalizadas.  
- Incremento del tiempo de ejecución de pruebas si no se optimizan contenedores persistentes.  

## Notas adicionales  

- Integrar Testcontainers en los tests existentes utilizando JUnit 5 y configurar contenedores reutilizables para reducir tiempos de inicialización.  
- Documentar ejemplos comunes de uso, como inicialización de bases de datos con datos semilla, simulación de fallos y pruebas de mensajería.  
- Monitorear el rendimiento de las pruebas en pipelines CI/CD para identificar oportunidades de optimización.  
- Usar Testcontainers junto con herramientas como Flyway o Liquibase para preparar esquemas de base de datos consistentes en cada prueba.  
