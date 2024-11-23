# Elección de GitHub Actions como herramienta de CI/CD

- **Estado:** Aprobado  
- **Fecha de decisión:** 2024-11-21  

## Contexto y problema  

El proyecto necesita una herramienta para implementar procesos de **Integración Continua (CI)** y **Entrega Continua (CD)** que permita:  
- Automatizar la construcción, pruebas y despliegue de la aplicación en diferentes entornos.  
- Integrarse de manera fluida con el sistema de control de versiones utilizado, actualmente **GitHub**.  
- Proveer una solución escalable y flexible, adaptándose a los requisitos del proyecto sin necesidad de administrar infraestructura adicional.  

La herramienta debe ofrecer facilidad de configuración, integración con el ecosistema de desarrollo y soporte para despliegues en entornos cloud.

## Decisión  

Se selecciona **GitHub Actions** como la herramienta principal de CI/CD para el proyecto. GitHub Actions proporciona una plataforma nativa dentro de GitHub para construir, probar y desplegar software de forma automatizada.

## Justificación  

### Ventajas principales de GitHub Actions  
- **Integración nativa con GitHub:** GitHub Actions está completamente integrado con GitHub, permitiendo ejecutar workflows directamente en respuesta a eventos como *push*, *pull requests* o *releases*.  
- **Facilidad de configuración:** Workflows definidos mediante archivos YAML permiten configuraciones claras y versionadas dentro del repositorio.  
- **Flexibilidad:** Soporte para múltiples lenguajes, sistemas operativos y configuraciones personalizadas, adaptándose a diferentes tipos de proyectos.  
- **Ecosistema de *actions*:** Amplia biblioteca de *actions* reutilizables creadas por la comunidad para tareas comunes como construcción, pruebas, despliegues y análisis estático.  
- **Escalabilidad:** GitHub Actions soporta flujos simples y complejos, desde pruebas locales hasta despliegues multi-entorno.  
- **Sin infraestructura adicional:** No requiere configurar o administrar servidores dedicados, ya que utiliza runners hospedados por GitHub o personalizados si se necesita.  

### Beneficios específicos para el proyecto  
- **Desempeño mejorado:** Al ser una solución nativa, GitHub Actions elimina la sobrecarga de integrar herramientas externas de CI/CD.  
- **Facilidad de uso:** Los desarrolladores pueden trabajar directamente desde GitHub, lo que reduce la curva de aprendizaje.  
- **Automatización completa:** Construcción automática del código, ejecución de pruebas, validaciones de estilo y despliegues en cada cambio de código.  

## Otras alternativas  

1. **Jenkins:**  
   - **Ventajas:** Altamente personalizable, soporta proyectos de gran escala.  
   - **Desventajas:** Requiere administrar y mantener servidores, mayor complejidad inicial.  

2. **GitLab CI/CD:**  
   - **Ventajas:** Integración nativa con GitLab, flujos similares a GitHub Actions.  
   - **Desventajas:** No es nativo de GitHub, lo que requiere integraciones adicionales.  

3. **CircleCI:**  
   - **Ventajas:** Rápido, fácil de configurar y con buena integración con GitHub.  
   - **Desventajas:** Costos mayores y funcionalidad limitada en planes gratuitos.  

## Consecuencias  

**Positivas:**  
- Alineación completa con el flujo de trabajo de desarrollo basado en GitHub.  
- Reducción de costos y complejidad operativa al eliminar la necesidad de administrar infraestructura CI/CD.  
- Gran flexibilidad para configurar pipelines personalizados y reutilizar acciones existentes.  
- Escalabilidad para soportar proyectos simples y complejos sin necesidad de migrar a otra herramienta.  

**Negativas:**  
- Dependencia de GitHub como plataforma principal, lo que podría ser una limitación si se considera un cambio futuro de sistema de control de versiones.  
- Costos asociados a runners adicionales en proyectos de gran escala, aunque manejables en proyectos medianos o pequeños.  

## Notas adicionales  

- Configurar *runners* auto-hospedados si se requiere mayor control sobre la infraestructura de ejecución.  
- Definir pipelines CI/CD claros para cubrir las fases de construcción, pruebas, análisis estático y despliegue.  
- Aprovechar *actions* existentes de la comunidad para tareas comunes y personalizar solo cuando sea necesario.  
- Monitorizar los costos asociados a los minutos de ejecución de workflows para optimizar el uso.  
