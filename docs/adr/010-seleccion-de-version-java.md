# Elección de Java 23 como versión del lenguaje y estrategia de actualización semestral

- **Estado:** Aprobado  
- **Fecha de decisión:** 2024-11-21  

## Contexto y problema  

El proyecto requiere definir la versión de Java para el desarrollo y ejecución de aplicaciones. La selección debe balancear las necesidades de acceso a las últimas características del lenguaje y la estabilidad requerida en un entorno productivo.

Dado el tren de liberaciones semestral de Java, se debe adoptar una estrategia que permita aprovechar las nuevas versiones regularmente sin comprometer la estabilidad del sistema.

## Decisión  

Se adopta **Java 23** como versión del lenguaje para el proyecto, siguiendo una estrategia de actualización cada 6 meses de acuerdo con el tren de liberaciones de Java.  

Esta decisión asegura que el equipo aproveche las últimas características del lenguaje y del JDK, manteniendo el sistema alineado con las mejores prácticas del ecosistema Java.

## Justificación  

La elección de Java 23 y la estrategia de actualización semestral se basan en los siguientes puntos:

### Ventajas de Java 23  
- **Acceso a las últimas características:** Java 23 incluye mejoras en rendimiento, nuevos APIs y optimizaciones que benefician la productividad y la calidad del código.  
- **Compatibilidad hacia adelante:** Las aplicaciones son compatibles con versiones más recientes, facilitando la migración a futuras versiones.  
- **Seguridad mejorada:** Cada nueva versión incluye parches y mejoras de seguridad, reduciendo riesgos en entornos productivos.  

### Estrategia de actualización semestral  
- **Ecosistema moderno:** Mantenerse actualizado con las versiones regulares permite aprovechar rápidamente las mejoras del lenguaje y el JDK, evitando la obsolescencia tecnológica.  
- **Compatibilidad incremental:** Las actualizaciones semestrales tienen cambios menores en comparación con versiones LTS (Long-Term Support), reduciendo el esfuerzo de migración.  
- **Alineación con la comunidad:** Facilita la integración con herramientas, frameworks y bibliotecas que adoptan rápidamente las nuevas versiones de Java.  

## Otras alternativas  

1. **Adoptar Java 21 (LTS):**  
   - **Ventajas:** Soporte extendido hasta 2029, ideal para entornos que priorizan la estabilidad a largo plazo.  
   - **Desventajas:** Retrasa el acceso a nuevas características y optimizaciones del lenguaje, lo que puede limitar la productividad del equipo.  

2. **Actualizar solo a versiones LTS:**  
   - **Ventajas:** Reducción de esfuerzo en actualizaciones frecuentes.  
   - **Desventajas:** Las actualizaciones cada 3 años pueden generar saltos tecnológicos grandes, haciendo las migraciones más complejas.  

3. **Adoptar versiones intermedias sin estrategia clara de actualización:**  
   - **Ventajas:** Flexibilidad en la adopción.  
   - **Desventajas:** Falta de consistencia y riesgo de quedarse atrapado en una versión sin soporte adecuado.  

## Consecuencias  

**Positivas:**  
- Acceso continuo a las mejoras y nuevas características del lenguaje y del JDK.  
- Simplificación de las migraciones, ya que las actualizaciones semestrales tienen un alcance limitado y bien definido.  
- Mantenimiento de la seguridad y estabilidad del sistema gracias a los parches regulares.  
- Alineación con la estrategia de innovación de la comunidad Java y de herramientas de terceros.  

**Negativas:**  
- Requiere un esfuerzo de actualización semestral, aunque reducido debido a la naturaleza incremental de las versiones.  
- Es necesario asegurarse de que todas las bibliotecas y herramientas utilizadas sean compatibles con las versiones de Java recientes.  

## Notas adicionales  

- Se recomienda incluir pruebas automatizadas extensivas para detectar problemas al migrar entre versiones.  
- Definir un proceso estándar de evaluación y adopción de nuevas versiones cada 6 meses para minimizar riesgos.  
- Monitorear las bibliotecas críticas del proyecto para garantizar que sigan el tren de liberaciones de Java.  
- Documentar los cambios y nuevas características relevantes en cada migración para facilitar la adopción por parte del equipo.  
