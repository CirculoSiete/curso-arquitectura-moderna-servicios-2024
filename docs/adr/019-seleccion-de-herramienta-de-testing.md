# Elección de JUnit como herramienta de testing

- **Estado:** Aprobado  
- **Fecha de decisión:** 2024-11-21  

## Contexto y problema  

El proyecto necesita una herramienta de testing para garantizar la calidad del código a través de pruebas automatizadas. La solución debe:  
- Soportar pruebas unitarias, de integración y funcionales.  
- Integrarse fácilmente con el ecosistema Java y herramientas como Maven, Gradle y pipelines CI/CD.  
- Ser flexible y extensible, permitiendo el uso de diferentes estrategias y frameworks complementarios.  

Dado que las pruebas son una parte esencial del ciclo de desarrollo, la herramienta seleccionada debe ser ampliamente adoptada, bien documentada y capaz de soportar necesidades avanzadas en el futuro.

## Decisión  

Se selecciona **JUnit** como la herramienta principal de testing para el proyecto. JUnit es un framework de testing ampliamente utilizado en el ecosistema Java, conocido por su flexibilidad, facilidad de uso e integración con otras herramientas.

## Justificación  

JUnit fue seleccionado debido a las siguientes razones:

### Ventajas principales de JUnit  
- **Popularidad y adopción:** JUnit es el framework de testing más utilizado en la comunidad Java, con un ecosistema bien desarrollado.  
- **Compatibilidad con herramientas:** Integración nativa con Maven, Gradle y entornos CI/CD como Jenkins, GitHub Actions y GitLab CI.  
- **Flexibilidad:** Soporta pruebas unitarias, de integración y funcionales, adaptándose a diferentes niveles de testing.  
- **Extensibilidad:** Compatible con frameworks complementarios como Mockito para pruebas con mocks, AssertJ para aserciones enriquecidas y Spring Test para pruebas de aplicaciones Spring.  
- **Soporte para JUnit 5 (JUnit Jupiter):** Proporciona características avanzadas como pruebas parametrizadas, configuraciones dinámicas y extensiones personalizadas.  

### Beneficios específicos para el proyecto  
- **Consistencia:** Proporciona un estándar claro para escribir y ejecutar pruebas, facilitando la colaboración en el equipo.  
- **Ecosistema:** Su amplia adopción asegura compatibilidad con bibliotecas y herramientas adicionales que se puedan requerir en el futuro.  
- **Simplicidad inicial:** Fácil de aprender para desarrolladores nuevos en el framework, con una curva de aprendizaje progresiva para características avanzadas.  

## Otras alternativas  

1. **TestNG:**  
   - **Ventajas:** Más flexible en configuraciones avanzadas y soporte nativo para pruebas paralelas.  
   - **Desventajas:** Menor adopción en comparación con JUnit y con un ecosistema menos desarrollado.  

2. **Spock:**  
   - **Ventajas:** Sintaxis concisa y expresiva, ideal para pruebas de comportamiento.  
   - **Desventajas:** Requiere Groovy, lo que puede no alinearse con un proyecto Java puro.  

3. **Arquillian:**  
   - **Ventajas:** Orientado a pruebas de integración en contenedores Java EE.  
   - **Desventajas:** Enfocado a pruebas de integración específicas, menos versátil para pruebas unitarias.  

## Consecuencias  

**Positivas:**  
- Reducción de la curva de aprendizaje gracias a la familiaridad de JUnit en la comunidad Java.  
- Facilita la creación de un ecosistema robusto de pruebas al integrarse con herramientas como Mockito, AssertJ y Spring Test.  
- Compatibilidad inmediata con los procesos de construcción y despliegue existentes basados en Maven o Gradle.  
- Soporte a largo plazo debido a su adopción masiva y desarrollo continuo.  

**Negativas:**  
- Algunas configuraciones avanzadas, como pruebas paralelas, pueden ser menos intuitivas en comparación con otras herramientas como TestNG.  
- Requiere aprender características nuevas de JUnit 5 si el equipo está acostumbrado a versiones anteriores (JUnit 4).  

## Notas adicionales  

- Se recomienda utilizar **JUnit 5 (JUnit Jupiter)** para aprovechar características modernas como extensiones personalizadas y pruebas parametrizadas.  
- Complementar con herramientas como **Mockito** para pruebas con mocks, y **AssertJ** para mejorar la legibilidad de las aserciones.  
- Integrar los tests en el pipeline CI/CD para garantizar que se ejecuten automáticamente en cada cambio del código.  
- Documentar las convenciones de pruebas en el proyecto para asegurar consistencia en el equipo.  
