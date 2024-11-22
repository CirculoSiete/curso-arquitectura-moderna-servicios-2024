# 003: Uso de ArchUnit para validar las reglas de arquitectura

- **Estado:** Aprobado  
- **Fecha de decisión:** 2024-11-21  

## Contexto y problema  

El proyecto requiere una forma automatizada de garantizar que se cumplan las reglas de arquitectura definidas, como la separación de capas, dependencias entre módulos y el uso correcto de anotaciones. Actualmente, estas validaciones se realizan manualmente, lo que resulta en errores inadvertidos, inconsistencias y retrabajo.

Es fundamental que las reglas arquitectónicas sean verificables de manera consistente, especialmente en un equipo con múltiples desarrolladores trabajando simultáneamente en el código base.

## Decisión  

Se utilizará **ArchUnit**, una biblioteca de Java, para definir y validar las reglas de arquitectura. ArchUnit permite escribir pruebas arquitectónicas como código, integrándolas en el pipeline de pruebas existente y asegurando que las validaciones se realicen automáticamente.

## Justificación  

ArchUnit fue seleccionado porque:  
- Ofrece una sintaxis clara y expresiva para definir reglas arquitectónicas en Java.  
- Permite una integración directa con frameworks de pruebas como JUnit, reduciendo la necesidad de introducir herramientas adicionales al ecosistema existente.  
- Es ampliamente adoptado en la comunidad Java, lo que facilita encontrar documentación, ejemplos y soporte.  
- Se adapta bien al enfoque de pruebas automatizadas que el equipo ya utiliza.  
- No impone dependencias significativas en el proyecto, lo que lo hace ligero y no intrusivo.  

## Otras alternativas  

1. **SonarQube:**  
   - **Ventajas:** Detecta violaciones de estándares y patrones en el código, incluyendo algunas reglas arquitectónicas.  
   - **Desventajas:** Más enfocado en análisis de código estático que en validaciones específicas de arquitectura. Carece de la flexibilidad que ofrece ArchUnit para definir reglas personalizadas.

2. **Custom scripts:**  
   - **Ventajas:** Total control sobre las validaciones.  
   - **Desventajas:** Mayor esfuerzo de desarrollo y mantenimiento. Requiere reinventar funcionalidades que ya están disponibles en ArchUnit.

3. **Revisiones manuales:**  
   - **Ventajas:** No requiere herramientas externas.  
   - **Desventajas:** Propenso a errores humanos y difícil de escalar en un equipo grande.  

## Consecuencias  

**Positivas:**  
- Validación automatizada de las reglas de arquitectura en tiempo de compilación y en cada ejecución de pruebas.  
- Fácil integración con el ecosistema existente de herramientas Java (JUnit, Maven/Gradle).  
- Reduce errores humanos y asegura el cumplimiento continuo de las decisiones arquitectónicas.  
- Escrito en código Java, lo que permite flexibilidad para definir reglas específicas según las necesidades del proyecto.  
- Documentación implícita de las reglas arquitectónicas, ya que estas están definidas en las pruebas.  

**Negativas:**  
- Incremento inicial en el esfuerzo de configuración y definición de reglas.  
- Curva de aprendizaje para los desarrolladores que no estén familiarizados con ArchUnit.  
- Las validaciones pueden extender el tiempo de ejecución de las pruebas en el pipeline de CI/CD, aunque esto es manejable.  

## Notas adicionales  

- Se recomienda empezar definiendo reglas simples (por ejemplo, dependencias entre capas) y expandirlas gradualmente según las necesidades del proyecto.  
- El equipo debe recibir una breve capacitación sobre el uso básico de ArchUnit para acelerar la adopción.  
- Monitorear el impacto en el tiempo de ejecución de las pruebas y ajustar la granularidad de las reglas si es necesario.  
- Revisar periódicamente las reglas para asegurarse de que siguen siendo relevantes a medida que evoluciona la arquitectura. 

