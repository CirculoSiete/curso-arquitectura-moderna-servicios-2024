# Elección de Flyway como herramienta de migraciones de base de datos

- **Estado:** Aprobado  
- **Fecha de decisión:** 2024-11-21  

## Contexto y problema  

El proyecto requiere una estrategia robusta para gestionar los cambios en los esquemas de base de datos de forma controlada y repetible. Las migraciones deben:  
- Ser aplicables de manera consistente en todos los entornos (desarrollo, prueba, producción).  
- Garantizar la trazabilidad y revertibilidad de los cambios realizados.  
- Integrarse fácilmente con el proceso de construcción y despliegue del sistema.  

Es necesario seleccionar una herramienta que permita implementar estas migraciones de forma eficiente, escalable y compatible con múltiples bases de datos.

## Decisión  

Se selecciona **Flyway** como herramienta para gestionar las migraciones de base de datos. Flyway proporciona un enfoque basado en scripts de migración versionados que asegura consistencia en la evolución del esquema de datos.

## Justificación  

Flyway fue seleccionado debido a las siguientes razones:

### Ventajas principales de Flyway  
- **Simplicidad:** Utiliza un enfoque basado en scripts SQL o Java versionados (`V1__initial_schema.sql`), lo que facilita su comprensión y adopción.  
- **Consistencia:** Garantiza que todos los entornos ejecuten las mismas migraciones en el mismo orden, minimizando errores humanos.  
- **Integración:** Compatible con herramientas de construcción como Maven y Gradle, así como con pipelines de CI/CD.  
- **Compatibilidad multiplataforma:** Soporta una amplia gama de bases de datos relacionales, lo que lo hace ideal para proyectos con diferentes tecnologías de base de datos.  
- **Reversibilidad:** Permite definir migraciones de rollback (`undo scripts`) opcionales para escenarios críticos.  
- **Monitoreo:** Incluye tablas internas que registran las migraciones aplicadas, facilitando la auditoría y la trazabilidad.  

### Beneficios específicos para el proyecto  
- **Control del esquema:** Los cambios en el esquema de la base de datos estarán versionados, documentados y centralizados en el repositorio de código.  
- **Despliegues automatizados:** Las migraciones se pueden ejecutar automáticamente como parte del proceso de despliegue, asegurando sincronización entre el código y la base de datos.  

## Otras alternativas  

1. **Liquibase:**  
   - **Ventajas:** Ofrece más funcionalidades avanzadas, como generación automática de changelogs.  
   - **Desventajas:** Mayor complejidad de configuración y curva de aprendizaje más pronunciada.  

2. **Migraciones manuales:**  
   - **Ventajas:** Total control sobre las migraciones.  
   - **Desventajas:** Propenso a errores humanos, difícil de escalar y mantener en equipos grandes.  

3. **Esquemas generados automáticamente por frameworks (ej., Hibernate):**  
   - **Ventajas:** Menor esfuerzo inicial para configurar el esquema.  
   - **Desventajas:** Menor control sobre los cambios, difícil de auditar y no recomendado para entornos productivos.  

## Consecuencias  

**Positivas:**  
- Mayor control sobre la evolución del esquema de la base de datos.  
- Reducción de errores en entornos de despliegue gracias a la automatización y la consistencia de las migraciones.  
- Facilidad de adopción y aprendizaje por parte del equipo, gracias a su enfoque simple basado en scripts SQL.  
- Flexibilidad para definir y gestionar cambios en múltiples bases de datos.  

**Negativas:**  
- Requiere disciplina del equipo para mantener los scripts organizados y versionados adecuadamente.  
- Las migraciones complejas pueden requerir scripts SQL detallados, lo que puede aumentar el esfuerzo en comparación con enfoques automatizados.  

## Notas adicionales  

- Se recomienda establecer una convención de nombres para los scripts de migración (por ejemplo, `V1__description.sql`, `V2__add_column.sql`).  
- Integrar Flyway en el proceso de construcción del proyecto (Maven o Gradle) para garantizar que las migraciones se ejecuten automáticamente.  
- Configurar pruebas automatizadas para validar que las migraciones aplicadas en desarrollo funcionen correctamente en otros entornos.  
- Documentar el flujo de migraciones para nuevos miembros del equipo y definir un proceso de revisión para evitar conflictos entre migraciones.  
