# Elección de flujo de trabajo de Git

- **Estado:** Aprobado  
- **Fecha de decisión:** 2024-11-21  

## Contexto y problema  

El proyecto utiliza Git como sistema de control de versiones, y es necesario establecer un flujo de trabajo claro para:  
- Facilitar la colaboración entre desarrolladores.  
- Gestionar cambios en el código de manera eficiente, con un control explícito sobre las versiones.  
- Soportar desarrollo paralelo de nuevas características, corrección de errores y despliegues.  

El flujo de trabajo debe minimizar conflictos, ser intuitivo y adaptarse tanto a proyectos pequeños como a equipos grandes distribuidos.

## Decisión  

Se adopta el flujo de trabajo **GitFlow**, con adaptaciones según las necesidades del equipo. Este modelo utiliza ramas dedicadas para el desarrollo, integración y despliegues, proporcionando un esquema claro y organizado para gestionar el código.

## Justificación  

### Características principales de GitFlow  
- **Rama principal (`main`):** Contiene el código en producción, asegurando estabilidad y consistencia.  
- **Rama de desarrollo (`develop`):** Punto de integración para nuevas características antes de llegar a producción.  
- **Ramas de características (`feature/*`):** Usadas para desarrollar nuevas funcionalidades, separadas del código estable.  
- **Ramas de correcciones rápidas (`hotfix/*`):** Permiten resolver errores críticos directamente en producción.  
- **Ramas de lanzamiento (`release/*`):** Ayudan a preparar una nueva versión, asegurando que se realicen pruebas finales y ajustes menores antes del despliegue.  

### Beneficios específicos para el proyecto  
- **Organización clara:** Proporciona un flujo de trabajo estructurado que separa el código en diferentes etapas de desarrollo.  
- **Colaboración eficiente:** Facilita el trabajo en equipo, permitiendo a los desarrolladores trabajar en diferentes ramas sin interferencias.  
- **Control de versiones:** Ayuda a gestionar versiones estables y a realizar despliegues controlados mediante ramas de lanzamiento.  
- **Adaptabilidad:** Es flexible y puede ajustarse a proyectos con diferentes ritmos de desarrollo.  

## Otras alternativas  

1. **GitHub Flow:**  
   - **Ventajas:** Simplicidad al trabajar directamente con ramas de características y la rama principal.  
   - **Desventajas:** Menor control sobre entornos de integración y preproducción, y menos adecuado para proyectos complejos.  

2. **GitLab Flow:**  
   - **Ventajas:** Combina características de GitFlow y GitHub Flow, con ramas alineadas a entornos (desarrollo, staging, producción).  
   - **Desventajas:** Mayor complejidad si no se usan herramientas de integración específicas como GitLab.  

3. **Trunk-Based Development:**  
   - **Ventajas:** Favorece la integración continua con cambios frecuentes en una sola rama principal.  
   - **Desventajas:** Requiere procesos de prueba rigurosos y equipo disciplinado para evitar inestabilidad.  

## Consecuencias  

**Positivas:**  
- Mejora la trazabilidad del trabajo realizado, separando desarrollo, integración y despliegues en ramas específicas.  
- Permite la coexistencia de múltiples versiones en desarrollo o producción.  
- Facilita la resolución de conflictos al centralizar el trabajo en ramas específicas para cada propósito.  
- Compatible con prácticas de integración continua y entrega continua (CI/CD).  

**Negativas:**  
- Introduce complejidad adicional en la gestión de ramas, especialmente para equipos pequeños o proyectos simples.  
- Requiere capacitación para asegurarse de que todos los desarrolladores entiendan y sigan el flujo.  

## Notas adicionales  

- Configurar reglas en Git (por ejemplo, protección de la rama `main`) para evitar cambios directos en ramas críticas sin revisiones.  
- Integrar herramientas de CI/CD que automaticen las pruebas y despliegues basados en las ramas GitFlow (por ejemplo, despliegues automáticos desde `release/*`).  
- Documentar las prácticas específicas del equipo, incluyendo convenciones para nombres de ramas y frecuencia de fusiones a `develop` o `main`.  
- Revisar periódicamente si GitFlow sigue siendo adecuado para el proyecto, especialmente si el equipo o los requisitos cambian.  
