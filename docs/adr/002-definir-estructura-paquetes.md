
# 002: Definir estructura de paquetes para Arquitectura Hexagonal en Java

## Contexto y Problema
El equipo ha decidido implementar **Arquitectura Hexagonal** en el proyecto (ver ADR-001). Sin embargo, no existe un consenso claro sobre cómo organizar los paquetes en el código fuente para reflejar los principios de esta arquitectura, lo que podría llevar a inconsistencias y confusión.

Se necesita una convención para estructurar los paquetes que:
- Refleje la separación de responsabilidades en la arquitectura hexagonal.
- Facilite la localización de clases según su rol (puertos, adaptadores, dominio).
- Mantenga la modularidad y escalabilidad del proyecto.

## Decisión
Adoptar la siguiente estructura de paquetes para el proyecto Java basado en Arquitectura Hexagonal:

### **Estructura propuesta**
```plaintext
com.c7.project
│
├── domain            // Núcleo de la lógica de negocio
│   ├── model         // Entidades y objetos de dominio
│   ├── repository    // Interfaces para acceso a datos (puertos de salida)
│   └── service       // Lógica de dominio
│
├── application       // Casos de uso (orquestan el dominio)
│   └── port          // Definición de puertos
│       ├── in        // Puertos de entrada (interfaces de casos de uso)
│       └── out       // Puertos de salida (interfaces para adaptadores externos)
│
├── infrastructure    // Adaptadores técnicos
│   ├── persistence   // Implementaciones de acceso a datos (bases de datos)
│   ├── messaging     // Integraciones con sistemas de mensajería/eventos
│   ├── external      // Conexiones con APIs externas
│   └── configuration // Configuración técnica (e.g., Spring)
│
└── interfaces        // Adaptadores de entrada (interfaces de usuario)
    ├── rest          // Controladores REST
    ├── graphql       // Controladores GraphQL
    └── cli           // Interfaces de línea de comandos
```

## Justificación
- **Principios de la Arquitectura Hexagonal**:
  - Separación clara entre lógica de negocio (dominio), casos de uso (aplicación), y adaptadores externos (infraestructura e interfaces).
  - Uso de **puertos** para definir contratos de entrada y salida, y **adaptadores** para implementar esos contratos.
- **Beneficios**:
  - Modularidad: Permite que cada componente (puertos, adaptadores) evolucione de manera independiente.
  - Independencia tecnológica: El dominio no depende de detalles técnicos como frameworks, bases de datos o interfaces externas.
  - Claridad: La estructura refleja los principios de la arquitectura, facilitando la comprensión del diseño.

### Alternativas consideradas
1. **Estructura plana (sin paquetes específicos para puertos/adaptadores)**:
   - **Pros**: Menor complejidad inicial.
   - **Contras**: Difícil de mantener y escalar en proyectos más grandes.
2. **Agrupar por módulos funcionales (en lugar de capas)**:
   - **Pros**: Buena opción para proyectos modulares grandes (bounded contexts).
   - **Contras**: Puede ser confuso para equipos que no estén familiarizados con este enfoque.

## Consecuencias
- **Positivas**:
  - Claridad en la separación de responsabilidades.
  - Modularidad y facilidad para integrar o reemplazar adaptadores externos.
  - Facilita el testing unitario y de integración.
- **Negativas**:
  - Mayor esfuerzo inicial para diseñar y respetar las capas y contratos.
  - Curva de aprendizaje para desarrolladores no familiarizados con Arquitectura Hexagonal.

## Estado
Aceptada

## Notas
- Implementar validaciones automáticas con herramientas como **ArchUnit** para garantizar que las dependencias respeten los principios de la arquitectura.
- Proveer ejemplos prácticos para el uso de puertos y adaptadores (e.g., cómo modelar un repositorio o un controlador REST).
- Considerar una estructura adicional para bounded contexts si el proyecto crece significativamente.


### **Próximos pasos**
1. **Definir contratos iniciales**: Crear puertos de entrada y salida para los primeros casos de uso.
2. **Implementar adaptadores**: Desarrollar adaptadores concretos para bases de datos, APIs externas y otras interfaces necesarias.
3. **Documentar buenas prácticas**: Asegurarse de que todos los desarrolladores entiendan cómo aplicar esta estructura en nuevos desarrollos.
