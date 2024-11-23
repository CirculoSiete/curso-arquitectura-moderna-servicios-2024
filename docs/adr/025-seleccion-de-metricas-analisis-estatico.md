# Elección de métricas de análisis estático

- **Estado:** Aprobado  
- **Fecha de decisión:** 2024-11-21  

## Contexto y problema  

El proyecto necesita establecer un conjunto de métricas de análisis estático para garantizar la calidad del código. Estas métricas deben:  
- Detectar posibles errores y vulnerabilidades antes de la ejecución.  
- Proveer una visión clara de la salud del código, incluyendo complejidad, mantenibilidad y adherencia a estándares de calidad.  
- Medir la cobertura de pruebas para asegurar que el código esté bien probado.  

Sin métricas definidas y herramientas automatizadas, el proyecto corre el riesgo de degradar la calidad del código, aumentar la deuda técnica y exponer vulnerabilidades.

## Decisión  

Se selecciona el conjunto de métricas de análisis estático a continuación, con un enfoque en cobertura de pruebas, mantenibilidad y seguridad:

1. **Cobertura de pruebas:**  
   - Porcentaje de líneas de código cubiertas por pruebas unitarias.  
   - Porcentaje de ramas de decisión cubiertas (cobertura de ramas).  

2. **Complejidad ciclomática:**  
   - Mide el número de caminos independientes en el código para identificar módulos complejos y susceptibles a errores.  

3. **Mantenibilidad:**  
   - Calculada con base en factores como la duplicación de código, complejidad y tamaño de los archivos.  

4. **Duplicación de código:**  
   - Identifica bloques de código repetidos para reducir la redundancia y facilitar el mantenimiento.  

5. **Vulnerabilidades de seguridad:**  
   - Detecta patrones peligrosos en el código, como inyecciones SQL, desbordamientos de buffer o uso de datos no sanitizados.  

6. **Estilo de codificación:**  
   - Verificación de adherencia a estándares definidos en el proyecto (por ejemplo, Google Java Style Guide).  

## Justificación  

Estas métricas fueron seleccionadas por su capacidad para:  
- **Cobertura de pruebas:** Asegurar que el código esté suficientemente probado, reduciendo el riesgo de errores en producción.  
- **Complejidad y mantenibilidad:** Identificar módulos difíciles de entender o de cambiar, previniendo deuda técnica.  
- **Seguridad:** Proteger el sistema contra vulnerabilidades conocidas en la etapa más temprana posible.  

## Herramientas recomendadas  

Para calcular y monitorear estas métricas, se recomienda usar:  

1. **SonarQube:**  
   - Soporte completo para métricas de calidad como cobertura, complejidad, duplicación y seguridad.  
   - Integración con pipelines CI/CD para análisis automático.  

2. **JaCoCo:**  
   - Herramienta de cobertura de código para proyectos Java, compatible con SonarQube.  
   - Fácil integración con Maven y Gradle.  

3. **SpotBugs:**  
   - Identificación de errores comunes y posibles vulnerabilidades mediante análisis estático.  

4. **Checkstyle:**  
   - Verificación de adherencia a estándares de estilo de codificación.  

## Otras alternativas  

1. **PMD:**  
   - **Ventajas:** Identifica patrones de código propensos a errores y puede personalizarse fácilmente.  
   - **Desventajas:** Menor integración nativa con cobertura de código y análisis de seguridad.  

2. **Codecov:**  
   - **Ventajas:** Especializado en cobertura de pruebas, con reportes visuales detallados.  
   - **Desventajas:** Requiere integración adicional para combinar métricas de calidad distintas.  

3. **Sin métricas automatizadas:**  
   - **Ventajas:** Simplicidad en el corto plazo.  
   - **Desventajas:** Incrementa el riesgo de errores, deuda técnica y falta de visibilidad sobre la calidad del código.  

## Consecuencias  

**Positivas:**  
- Mejora la calidad del código al identificar problemas en etapas tempranas.  
- Asegura que el código esté suficientemente probado mediante métricas claras de cobertura.  
- Permite priorizar esfuerzos en módulos con alta complejidad o vulnerabilidades críticas.  
- Facilita la adopción de mejores prácticas y estándares de calidad de la industria.  

**Negativas:**  
- Configuración inicial y curva de aprendizaje para integrar herramientas como SonarQube y JaCoCo.  
- Posibles costos asociados al uso de herramientas avanzadas o planes premium.  
- Necesidad de disciplina para actuar sobre los reportes generados por las métricas.  

## Notas adicionales  

- Integrar el análisis estático con los pipelines CI/CD para garantizar que las métricas se evalúen automáticamente en cada cambio del código.  
- Definir umbrales mínimos para las métricas clave, como cobertura de pruebas (por ejemplo, 80%) y complejidad ciclomática aceptable.  
- Revisar regularmente los resultados de las métricas y abordar las áreas críticas en reuniones de revisión de calidad.  
- Documentar las métricas y herramientas utilizadas para facilitar su adopción por nuevos miembros del equipo.
