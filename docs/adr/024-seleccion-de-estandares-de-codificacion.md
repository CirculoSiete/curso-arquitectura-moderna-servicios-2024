# Elección de estándares de codificación

- **Estado:** Aprobado  
- **Fecha de decisión:** 2024-11-21  

## Contexto y problema  

El proyecto requiere un conjunto claro de estándares de codificación para:  
- **Mejorar la calidad del código:** Asegurar consistencia, claridad y mantenibilidad en todo el código base.  
- **Facilitar la colaboración:** Establecer un lenguaje común entre desarrolladores, reduciendo malentendidos y conflictos.  
- **Cumplir con las mejores prácticas:** Alinear el proyecto con los estándares de la industria, facilitando auditorías y revisiones externas.  

Sin estándares claros, el código puede volverse inconsistente y difícil de mantener a medida que el equipo y el proyecto crecen.

## Decisión  

Se adopta el uso de **estándares de codificación específicos para Java**, basados en las guías de estilo de **Google Java Style Guide** y los lineamientos de **SonarLint**, con ajustes personalizados según las necesidades del proyecto.

## Justificación  

### Beneficios de adoptar estándares de codificación  

1. **Consistencia:**  
   - Define reglas comunes sobre nomenclatura, formateo, uso de comentarios y organización de clases y paquetes.  
   - Facilita la lectura y comprensión del código entre miembros del equipo.  

2. **Prevención de errores:**  
   - Reduce la introducción de errores comunes al seguir prácticas recomendadas.  
   - Mejora la identificación temprana de problemas mediante herramientas automatizadas.  

3. **Compatibilidad con herramientas:**  
   - Los estándares seleccionados son compatibles con herramientas como Checkstyle, PMD y SonarQube, lo que permite automatizar la verificación del cumplimiento.  
   - Integración con IDEs como IntelliJ IDEA, Eclipse y VS Code para aplicar formateo automático y validaciones en tiempo real.  

4. **Mejores prácticas:**  
   - Alineación con estándares reconocidos en la comunidad Java, lo que asegura que el código sea mantenible y fácilmente comprensible por desarrolladores externos.  

### Personalización para el proyecto  
- Ajustes para alinearse con las necesidades específicas del equipo, como la longitud máxima de líneas de código o reglas para las pruebas automatizadas.  
- Inclusión de prácticas específicas para el uso de frameworks adoptados en el proyecto, como Spring Boot y JPA.  

## Otras alternativas  

1. **Estándares internos personalizados:**  
   - **Ventajas:** Total flexibilidad para definir reglas.  
   - **Desventajas:** Mayor esfuerzo inicial para definir, documentar y mantener las reglas.  

2. **Uso de linters sin estándares formales:**  
   - **Ventajas:** Detección automática de problemas con mínima configuración.  
   - **Desventajas:** Falta de alineación con una guía clara y dificultad para mantener consistencia.  

3. **Sin estándares formales:**  
   - **Ventajas:** Máxima libertad para los desarrolladores.  
   - **Desventajas:** Código inconsistente, difícil de entender y de mantener a largo plazo.  

## Consecuencias  

**Positivas:**  
- Mejora de la calidad del código a través de guías claras y consistentes.  
- Reducción del tiempo en revisiones de código al basarse en estándares predefinidos.  
- Alineación con herramientas automáticas que simplifican la validación y aplicación de los estándares.  
- Fácil incorporación de nuevos miembros al equipo gracias a documentación clara y un código predecible.  

**Negativas:**  
- Requiere capacitación inicial para que los desarrolladores adopten los estándares.  
- Puede generar resistencia al cambio por parte de miembros del equipo acostumbrados a estilos de codificación diferentes.  

## Notas adicionales  

- Configurar herramientas como **Checkstyle** o **SpotBugs** en el pipeline CI/CD para validar automáticamente el cumplimiento de los estándares.  
- Implementar configuraciones predefinidas de formateo en los IDEs utilizados por el equipo.  
- Documentar los estándares en un archivo accesible dentro del repositorio, como `CONTRIBUTING.md` o `STYLE_GUIDE.md`.  
- Revisar periódicamente los estándares para ajustarlos a las necesidades cambiantes del proyecto.  
