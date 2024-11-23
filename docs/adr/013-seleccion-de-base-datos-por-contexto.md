
# Elección de una base de datos centralizada por contexto

- **Estado:** Aprobado  
- **Fecha de decisión:** 2024-11-21  

## Contexto y problema  

El sistema está diseñado bajo los principios de **Domain-Driven Design (DDD)**, que establece que cada **Bounded Context** debe ser una unidad autónoma e independiente. Esto incluye la gestión de datos, donde la base de datos utilizada para cada contexto debe alinearse con sus necesidades específicas.

El problema surge al decidir entre tener una única base de datos compartida para todos los contextos o mantener bases de datos separadas por contexto, con el objetivo de evitar dependencias entre ellos y garantizar su independencia.

## Decisión  

Se adopta una estrategia de **base de datos centralizada por contexto**, donde cada **Bounded Context** tendrá su propia base de datos independiente. Esta base de datos estará centralizada para el contexto, pero no se compartirá entre múltiples contextos.

## Justificación  

La elección de bases de datos centralizadas por contexto se basa en los siguientes puntos:

### Ventajas de bases de datos centralizadas por contexto  
- **Aislamiento de contextos:** Cada Bounded Context tiene control total sobre su esquema y modelo de datos, eliminando el riesgo de dependencias entre contextos.  
- **Escalabilidad:** Permite que cada contexto escale de forma independiente, eligiendo tecnologías o configuraciones específicas según sus necesidades.  
- **Flexibilidad tecnológica:** Cada contexto puede elegir la tecnología de base de datos que mejor se adapte a sus requerimientos (por ejemplo, SQL para uno, NoSQL para otro).  
- **Evolución independiente:** Cambios en el modelo de datos de un contexto no afectan a otros, reduciendo el riesgo de regresiones y conflictos.  
- **Alineación con DDD:** Refuerza la separación conceptual de los contextos, facilitando la aplicación de los principios de diseño.  

### Desafíos de una base de datos única compartida  
- **Dependencias acopladas:** Los contextos estarían forzados a compartir un modelo de datos común, lo que podría introducir restricciones en su evolución.  
- **Riesgos de gobernanza:** Cambios en un contexto podrían romper otros contextos que dependen del mismo esquema.  
- **Complejidad en el diseño:** Un modelo único tendría que incluir reglas específicas para cada contexto, lo que incrementaría su complejidad.  

## Otras alternativas  

1. **Base de datos compartida única:**  
   - **Ventajas:** Centralización de datos, simplificación de infraestructura.  
   - **Desventajas:** Introduce acoplamiento entre contextos, dificultando su evolución y autonomía.  

2. **Base de datos separada por entidad:**  
   - **Ventajas:** Flexibilidad extrema al nivel más granular.  
   - **Desventajas:** Complejidad operativa innecesaria, dado que las entidades suelen estar dentro de un mismo contexto.  

3. **Base de datos federada:**  
   - **Ventajas:** Integración de múltiples bases de datos con acceso unificado.  
   - **Desventajas:** Incrementa la complejidad en la consulta y sincronización de datos.  

## Consecuencias  

**Positivas:**  
- Refuerza la autonomía de los contextos, alineándose con los principios de DDD.  
- Simplifica el mantenimiento y la evolución de cada contexto al reducir las dependencias intercontextuales.  
- Permite optimizar el diseño y la implementación de cada base de datos según los requerimientos específicos del contexto.  
- Facilita la transición a microservicios si el sistema decide adoptar esta arquitectura en el futuro.  

**Negativas:**  
- Incremento en la complejidad operativa debido a la gestión de múltiples bases de datos.  
- Requiere mayor inversión en monitoreo, seguridad y estrategias de respaldo para cada base de datos individual.  
- Puede aumentar la latencia si se necesitan integraciones entre contextos, dado que los datos estarán distribuidos.  

## Notas adicionales  

- Cada contexto debe tener acceso exclusivo a su base de datos, evitando accesos directos por parte de otros contextos.  
- Las integraciones entre contextos deben manejarse a través de APIs públicas o eventos, en lugar de consultas directas a las bases de datos.  
- Se recomienda monitorear el desempeño y la complejidad operativa de esta estrategia para asegurar que sigue siendo adecuada a medida que el sistema crece.  
- Las decisiones sobre la tecnología de cada base de datos deben tomarse por separado y alinearse con los requerimientos específicos del contexto correspondiente.  

