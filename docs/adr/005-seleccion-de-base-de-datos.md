# Elección de PostgreSQL como base de datos relacional

- **Estado:** Aprobado  
- **Fecha de decisión:** 2024-11-21  

## Contexto y problema  

El sistema requiere una base de datos relacional que soporte:  
- Datos estructurados con relaciones claras y normalización.  
- Almacenamiento y consulta eficiente de datos semiestructurados (como JSON) para casos flexibles o poco estructurados.  
- Operaciones avanzadas con tipos escalares y extensibilidad para necesidades futuras.  

Además, la solución debe ser madura, escalable y ampliamente adoptada, con herramientas de soporte integradas y compatibilidad con el ecosistema tecnológico existente.

## Decisión  

Se selecciona **PostgreSQL** como la base de datos relacional principal del sistema. PostgreSQL es una base de datos robusta, madura y flexible que soporta datos relacionales y semiestructurados, ofreciendo herramientas avanzadas para manejar ambos tipos de datos de manera eficiente.

## Justificación  

PostgreSQL fue seleccionado debido a las siguientes razones:

### Soporte para datos estructurados y semiestructurados  
- **Soporte para JSON y JSONB:**  
  - Permite almacenar y consultar datos JSON con operaciones eficientes.  
  - `JSONB` ofrece un almacenamiento binario optimizado para consultas y filtrados frecuentes.  

- **Datos relacionales tradicionales:**  
  - Excelentes herramientas para modelado de datos relacional, con soporte completo para claves foráneas, vistas, índices avanzados, etc.

### Tipos escalares y extensibilidad  
- Amplio soporte para tipos de datos personalizados, como enumeraciones y arrays.  
- Soporte para funciones avanzadas como operadores matemáticos, geométricos y funciones agregadas.  
- Extensibilidad para añadir nuevos tipos y funciones específicas mediante extensiones (por ejemplo, PostGIS para datos espaciales).  

### Características adicionales  
- **Escalabilidad:** Manejo eficiente de grandes volúmenes de datos, con soporte para replicación y particionamiento.  
- **Transacciones ACID:** Garantiza la integridad de datos incluso en escenarios complejos.  
- **Madurez y estabilidad:** Es una base de datos probada en múltiples industrias y aplicaciones críticas.  
- **Comunidad activa:** Amplia documentación, herramientas de soporte y extensiones disponibles.  

## Otras alternativas  

1. **MySQL:**  
   - **Ventajas:** Ligera, ampliamente utilizada, buen rendimiento para cargas OLTP.  
   - **Desventajas:** Soporte limitado para JSON (sin JSONB), menor flexibilidad en extensibilidad y operaciones avanzadas.  

2. **MongoDB:**  
   - **Ventajas:** Excelente para datos completamente no estructurados y grandes volúmenes de documentos JSON.  
   - **Desventajas:** Carece de la robustez y funcionalidad relacional que PostgreSQL ofrece.  

3. **MariaDB:**  
   - **Ventajas:** Alternativa open-source a MySQL con mejoras en algunas funcionalidades.  
   - **Desventajas:** Similar a MySQL, con soporte limitado para JSON y operaciones avanzadas.  

## Consecuencias  

**Positivas:**  
- Flexibilidad para manejar datos estructurados y semiestructurados, lo que reduce la necesidad de usar múltiples bases de datos.  
- Alto rendimiento en consultas JSONB, ideal para casos que requieren almacenar datos heterogéneos o flexibles.  
- Herramientas avanzadas de optimización de consultas y administración de datos.  
- Soporte para operaciones complejas y datos escalares, asegurando adaptabilidad a futuros requisitos.  

**Negativas:**  
- Configuración inicial más compleja en comparación con bases de datos más simples como MySQL.  
- Curva de aprendizaje para desarrolladores menos familiarizados con las características avanzadas de PostgreSQL.  
- El uso intensivo de JSONB puede requerir un diseño cuidadoso para evitar sobrecarga en las consultas.  

## Notas adicionales  

- Se recomienda utilizar índices específicos (como `GIN`) para optimizar consultas sobre columnas JSONB.  
- Es importante definir una estrategia clara de particionamiento y replicación para garantizar el rendimiento a medida que los datos crezcan.  
- Revisar extensiones relevantes para las necesidades del proyecto (por ejemplo, `PostGIS` si se utilizan datos espaciales).  
- Incluir métricas y monitoreo del rendimiento para ajustar configuraciones según el crecimiento del sistema. 
