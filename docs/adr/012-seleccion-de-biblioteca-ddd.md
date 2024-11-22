# Elección de jMolecules para construir el modelo de dominio

- **Estado:** Aprobado  
- **Fecha de decisión:** 2024-11-21  

## Contexto y problema  

El proyecto se desarrolla siguiendo los principios de **Domain-Driven Design (DDD)** y utiliza una arquitectura hexagonal. Para alinear el código con estos principios, es necesario estructurar el modelo de dominio de manera explícita, manteniendo una separación clara entre conceptos como entidades, agregados, valores, y repositorios.

El equipo busca una herramienta que ayude a estructurar el modelo de dominio de manera uniforme, mejore la comprensión del código y facilite su integración con frameworks como Spring o Jakarta EE sin acoplar la lógica del dominio con el framework.

## Decisión  

Se selecciona **jMolecules** como librería para construir el modelo de dominio del proyecto. jMolecules proporciona anotaciones y conceptos bien definidos para aplicar los principios de DDD en el código, manteniendo independencia del framework utilizado.

## Justificación  

jMolecules fue seleccionado debido a las siguientes razones:

### Ventajas principales de jMolecules  
- **Definición clara del modelo de dominio:** Proporciona anotaciones para conceptos fundamentales de DDD como `@AggregateRoot`, `@Entity`, `@ValueObject`, y `@Repository`.  
- **Independencia del framework:** Las anotaciones de jMolecules son puramente conceptuales, lo que permite mantener el modelo de dominio desacoplado de frameworks específicos como Spring o Jakarta EE.  
- **Integración flexible:** jMolecules puede integrarse con frameworks como Spring para mapear conceptos del dominio sin introducir dependencias directas en el modelo. Por ejemplo, `@Repository` de jMolecules puede mapearse al estereotipo de Spring.  
- **Documentación implícita:** El uso de jMolecules mejora la legibilidad del código al hacer explícitos los roles de las clases dentro del modelo de dominio.  
- **Alineación con la arquitectura hexagonal:** Facilita la separación entre el núcleo del dominio y las capas de infraestructura y aplicación.  

## Otras alternativas  

1. **Definir el modelo de dominio manualmente sin librerías:**  
   - **Ventajas:** Total control sobre el diseño del modelo de dominio sin dependencias externas.  
   - **Desventajas:** Requiere convenciones internas y disciplina del equipo para mantener la coherencia. La falta de estandarización puede dificultar la colaboración.  

2. **Utilizar anotaciones propias del framework (por ejemplo, Spring):**  
   - **Ventajas:** Simplifica la configuración inicial al reutilizar conceptos del framework.  
   - **Desventajas:** Introduce un acoplamiento entre el modelo de dominio y el framework, violando los principios de DDD y arquitectura hexagonal.  

3. **Librerías específicas como Axon Framework:**  
   - **Ventajas:** Integración avanzada con patrones como Event Sourcing y CQRS.  
   - **Desventajas:** Mayor complejidad y enfoque en conceptos específicos, lo que puede ser innecesario si solo se necesita modelar el dominio.  

## Consecuencias  

**Positivas:**  
- Modelo de dominio alineado con los principios de DDD y claramente definido, mejorando la legibilidad y mantenibilidad del código.  
- Desacoplamiento del modelo de dominio respecto a los frameworks de infraestructura.  
- Facilita la colaboración entre desarrolladores al utilizar conceptos bien establecidos de DDD.  
- Incrementa la capacidad de evolución del sistema sin comprometer la lógica del dominio.  

**Negativas:**  
- Introducción de una dependencia adicional en el proyecto, aunque sea ligera y conceptual.  
- Requiere que los desarrolladores estén familiarizados con los principios de DDD y las convenciones de jMolecules.  

## Notas adicionales  

- Se recomienda capacitar al equipo en el uso de jMolecules y en los principios fundamentales de DDD para maximizar su adopción efectiva.  
- Definir reglas arquitectónicas (por ejemplo, con ArchUnit) para validar que el modelo de dominio sigue las convenciones establecidas por jMolecules.  
- Documentar cómo se mapean los conceptos de jMolecules a los requisitos específicos del proyecto y a los frameworks utilizados (por ejemplo, repositorios de Spring Data).  
- Revisar periódicamente el modelo de dominio para asegurar que las anotaciones de jMolecules reflejan fielmente la intención del diseño.  
