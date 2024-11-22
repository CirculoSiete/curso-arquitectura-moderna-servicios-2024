# Elección de Jib para construir contenedores de aplicaciones Java

- **Estado:** Aprobado  
- **Fecha de decisión:** 2024-11-21  

## Contexto y problema  

El proyecto requiere una herramienta para construir imágenes de contenedores Docker para aplicaciones Java. La solución debe:  
- Simplificar el proceso de creación de imágenes sin necesidad de escribir manualmente archivos Dockerfile.  
- Optimizar la construcción y el tamaño de las imágenes generadas.  
- Integrarse con las herramientas de construcción existentes, como Maven o Gradle, para minimizar la sobrecarga en el flujo de trabajo de desarrollo.  

La solución debe ser eficiente, fácil de usar y compatible con pipelines de CI/CD.

## Decisión  

Se selecciona **Jib** como herramienta para construir contenedores de las aplicaciones Java del proyecto. Jib es un plugin diseñado específicamente para aplicaciones Java que elimina la necesidad de Docker en la etapa de construcción.

## Justificación  

Jib fue seleccionado por las siguientes razones:

### Ventajas principales de Jib  
- **Sin necesidad de Dockerfile:** Jib construye imágenes de contenedores directamente a partir del proyecto Java, eliminando la complejidad de escribir y mantener archivos Dockerfile.  
- **Construcción optimizada:** Jib separa la aplicación en capas (dependencias, recursos y código), lo que permite reconstruir y cargar solo las capas que cambian. Esto acelera las iteraciones de desarrollo.  
- **Integración con herramientas de construcción:** Soporte nativo para Maven y Gradle a través de plugins oficiales, facilitando la adopción sin herramientas adicionales.  
- **Imágenes más ligeras:** Genera imágenes optimizadas que solo contienen los artefactos necesarios para ejecutar la aplicación.  
- **Compatibilidad con registries:** Soporte nativo para registries populares como Docker Hub, Google Container Registry (GCR) y Amazon Elastic Container Registry (ECR).  

### Beneficios específicos para el proyecto  
- **Eficiencia en CI/CD:** Jib elimina la necesidad de instalar Docker en servidores de CI/CD, lo que simplifica la configuración y mejora los tiempos de construcción.  
- **Fácil adopción:** Los desarrolladores pueden usar Jib directamente desde sus herramientas de construcción habituales, reduciendo la curva de aprendizaje.  

## Otras alternativas  

1. **Docker con Dockerfile:**  
   - **Ventajas:** Flexibilidad total en la configuración de la imagen.  
   - **Desventajas:** Mayor complejidad y propensión a errores en la configuración manual. No optimiza capas automáticamente.  

2. **Buildpacks (como Spring Boot Buildpacks):**  
   - **Ventajas:** Proporciona una forma estandarizada de construir imágenes sin necesidad de Dockerfile.  
   - **Desventajas:** Menos control sobre la optimización de las capas específicas para aplicaciones Java.  

3. **Kaniko:**  
   - **Ventajas:** Permite construir imágenes en entornos sin privilegios de root.  
   - **Desventajas:** Requiere un Dockerfile y no está optimizado específicamente para aplicaciones Java.  

## Consecuencias  

**Positivas:**  
- Reducción del tiempo de configuración y mantenimiento de las imágenes de contenedor.  
- Iteraciones más rápidas en el desarrollo gracias a la construcción incremental de capas.  
- Simplificación de los pipelines de CI/CD al eliminar la dependencia de Docker en la etapa de construcción.  
- Imágenes ligeras y optimizadas para entornos productivos.  

**Negativas:**  
- Menor flexibilidad para personalizaciones avanzadas que requerirían un Dockerfile explícito.  
- Dependencia de Jib como herramienta externa, lo que podría ser una limitación si se necesitan funcionalidades no soportadas.  

## Notas adicionales  

- Se recomienda usar Jib en combinación con registries seguros y configuraciones optimizadas para el entorno de despliegue (como uso de imágenes base pequeñas).  
- Monitorear las actualizaciones del plugin de Jib para asegurar compatibilidad con las versiones más recientes de Maven y Gradle.  
- Documentar el proceso de configuración inicial para facilitar la adopción por parte del equipo.  
- Si en el futuro se requieren configuraciones avanzadas no soportadas por Jib, considerar la transición a Dockerfile o Buildpacks.  
