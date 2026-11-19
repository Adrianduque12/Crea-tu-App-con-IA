# ATHLOS — Entrenamiento y progresión

**Train with purpose. Track your progress.**

ATHLOS es una aplicación Android de seguimiento de entrenamiento de fuerza. Permite organizar rutinas, registrar series, pesos y repeticiones, consultar un catálogo de ejercicios y revisar estadísticas básicas de las sesiones realizadas.

> Proyecto académico individual desarrollado con Kotlin y Jetpack Compose, con apoyo de asistentes de Inteligencia Artificial durante el proceso de programación.

## 1. Concepto de la aplicación

ATHLOS busca centralizar la planificación y el registro del entrenamiento de gimnasio. Su finalidad es que el usuario pueda consultar sus rutinas, registrar el resultado de las series, mantener un historial y visualizar datos básicos de rendimiento sin depender de notas dispersas o apuntes manuales.

- **Nombre:** ATHLOS
- **Plataforma:** Android
- **Tecnologías principales:** Kotlin, Jetpack Compose, Material 3 y SharedPreferences/JSON para persistencia local de esta versión inicial.
- **Público objetivo:** usuarios que realizan entrenamiento de fuerza y desean organizar sus sesiones y seguir su progresión.
- **Identidad visual:** interfaz oscura, superficies en gris carbón y acento verde lima; diseño deportivo, minimalista y orientado a facilitar el uso durante el entrenamiento.

## 2. Funcionalidades que vamos a desarrollar

### Pantalla 1 — Inicio / Dashboard
- Saludo personalizado.
- Acceso a las rutinas.
- Resumen de sesiones registradas y volumen acumulado.
- Objetivo semanal de sesiones y barra de progreso.
- Rutinas de acceso rápido.

### Pantalla 2 — Rutinas
- Listado de rutinas predefinidas (Push, Pull, Legs y Upper).
- Mostrar ejercicios, series y repeticiones previstas.
- Iniciar una rutina.
- Crear una rutina personalizada seleccionando ejercicios.
- Eliminar rutinas personalizadas.

### Pantalla 3 — Entrenamiento activo
- Iniciar una rutina seleccionada.
- Mostrar el ejercicio actual y su objetivo de series/repeticiones.
- Introducir peso y repeticiones de una serie.
- Registrar series completadas.
- Navegar por los ejercicios de la rutina.
- Temporizador de descanso con selección de 60, 90 o 120 segundos.
- Finalizar y guardar la sesión.
- Cálculo del volumen de las series registradas (peso × repeticiones).

### Pantalla 4 — Ejercicios
- Catálogo de ejercicios de ejemplo.
- Búsqueda por nombre.
- Filtro por grupo muscular.
- Consulta de grupo muscular, material y descripción.

### Pantalla 5 — Progreso
- Número de sesiones guardadas.
- Volumen acumulado.
- Número de series registradas.
- Número de ejercicios con registros.
- Historial de sesiones con fecha y resumen.

### Pantalla 6 — Perfil y objetivos
- Cambiar el nombre visible.
- Configurar el objetivo semanal entre 1 y 7 sesiones.
- Guardar la configuración localmente.

### Persistencia
- Rutinas personalizadas, historial de entrenamientos, nombre y objetivo semanal se guardan localmente usando SharedPreferences y JSON.
- No requiere cuenta ni conexión a un servidor.

## 3. Justificación de la aplicación

ATHLOS surge de la necesidad de disponer de una herramienta que permita gestionar los entrenamientos de gimnasio de una manera organizada, sencilla y eficiente. Muchas personas realizan actividad física de forma habitual, pero no llevan un registro adecuado de sus rutinas, cargas utilizadas, repeticiones o progresión a lo largo del tiempo.

La aplicación pretende solucionar este problema centralizando en una única plataforma la planificación de entrenamientos, el registro de ejercicios y el seguimiento del rendimiento. De esta forma, el usuario puede consultar sus sesiones anteriores, conocer sus marcas personales, analizar su evolución y establecer objetivos semanales.

El desarrollo de ATHLOS también permite aplicar conocimientos del ciclo de Desarrollo de Aplicaciones Multiplataforma, especialmente programación, diseño de interfaces, gestión de datos, arquitectura de aplicaciones móviles y persistencia de información.

Para realizar el proyecto se emplean herramientas de Inteligencia Artificial como asistentes de programación, con el objetivo de apoyar el proceso de desarrollo, estudiar soluciones técnicas, detectar errores y mejorar la implementación. El código generado se revisa, adapta y prueba durante el desarrollo.

## 4. Arquitectura y organización del proyecto

Esta primera versión utiliza una estructura sencilla y centralizada para facilitar que el proyecto sea abierto y ejecutable como punto de partida. La siguiente estructura modular es la organización objetivo que puede ampliarse durante el desarrollo:

```text
ATHLOS/
├── app/
│   └── src/main/
│       ├── AndroidManifest.xml
│       ├── java/com/adrian/athlos/
│       │   └── MainActivity.kt
│       └── res/values/strings.xml
├── build.gradle.kts
├── settings.gradle.kts
└── gradle.properties
```

### Responsabilidades principales

- **MainActivity:** punto de entrada Android y alojamiento de la interfaz Compose.
- **Pantallas Compose:** Inicio, Rutinas, Entrenamiento activo, Ejercicios, Progreso y Perfil.
- **Modelos:** `Exercise`, `RoutineExercise`, `Routine`, `SetLog` y `WorkoutLog`, que representan los datos principales.
- **Estado de la aplicación:** estados Compose controlan navegación, rutinas, registros, sesión activa y configuración del usuario.
- **Persistencia:** SharedPreferences almacena cadenas JSON con rutinas e historial, además del perfil y objetivo.
- **Material 3:** componentes de interfaz, botones, tarjetas, campos, filtros y navegación inferior.

La versión de partida prioriza la facilidad de ejecución y comprensión. Como refactorización futura se puede dividir el código en paquetes `data/model`, `data/repository`, `ui/screens`, `ui/components` y `viewmodel`, y evolucionar hacia MVVM y Room.

## 5. Prompts profesionales para utilizar la IA

Los prompts deben conservarse como evidencia del proceso. Se recomienda guardar también las respuestas relevantes, errores de compilación, cambios aplicados y pruebas realizadas. No se deben presentar errores hipotéticos como si hubieran ocurrido; el registro final debe reflejar incidencias reales.

### Prompt 1 — Planificación técnica

> Actúa como desarrollador Android senior especializado en Kotlin, Jetpack Compose y arquitectura de aplicaciones móviles. Quiero desarrollar ATHLOS, una aplicación Android de gestión de entrenamientos de fuerza y seguimiento de progresión. Antes de generar código, planifica las funcionalidades, pantallas, navegación, entidades, tecnologías, estructura de paquetes y fases de implementación. Justifica las decisiones con criterios de simplicidad, mantenibilidad y adecuación a un proyecto académico de DAM. Evita tecnologías innecesariamente complejas y prioriza una versión funcional que pueda comprender y explicar un estudiante.

### Prompt 2 — Diseño de UI/UX

> Define un sistema visual para ATHLOS, una aplicación Android de entrenamiento de fuerza. Utiliza tema oscuro, fondo negro/gris carbón, verde lima de acento, tipografía legible, tarjetas, jerarquía visual clara y navegación inferior. Debe incluir Inicio, Rutinas, Entrenamiento, Ejercicios, Progreso y Perfil. Diseña componentes reutilizables y prioriza usabilidad, coherencia y adaptación a distintas pantallas. Evita elementos decorativos sin función. Primero describe el sistema visual y la composición de pantallas, sin generar todo el proyecto.

### Prompt 3 — Implementación de la base

> Implementa la estructura inicial de ATHLOS en el proyecto Android Studio existente usando Kotlin y Jetpack Compose. Revisa primero la configuración y versiones actuales. Añade navegación, tema oscuro personalizado, componentes reutilizables y estados de pantalla. Mantén la lógica separada de la interfaz y no concentres innecesariamente todo en MainActivity. No cambies dependencias sin justificar compatibilidad. Entrega rutas y contenido completo de cada archivo modificado, con imports y código necesario para compilar.

### Prompt 4 — Rutinas y ejercicios

> Implementa el módulo de rutinas y catálogo de ejercicios. Debe permitir consultar rutinas, crear, editar y eliminar rutinas, asociar ejercicios, configurar series, repeticiones y descanso, buscar ejercicios y filtrarlos por grupo muscular. Define modelos adecuados, validaciones y componentes reutilizables. La implementación debe ser funcional, no una maqueta, y mantener el estilo de ATHLOS. Separa la interfaz de la lógica de datos y entrega todos los archivos completos.

### Prompt 5 — Entrenamiento y cálculos

> Desarrolla el módulo de entrenamiento activo. Permite iniciar una rutina, registrar peso y repeticiones por serie, marcar series completadas, avanzar entre ejercicios, controlar el descanso y finalizar la sesión. Calcula volumen por serie (peso × repeticiones), volumen total, series completadas y duración cuando esté disponible. Valida entradas no negativas y repeticiones positivas. Gestiona los estados correctamente y mantén la lógica de negocio separada de la interfaz. Entrega código completo y explica brevemente las decisiones.

### Prompt 6 — Persistencia local

> Añade persistencia local para rutinas, entrenamientos, series, pesos, repeticiones, fechas, nombre y objetivo semanal. Evalúa Room si es compatible con el proyecto; si el alcance o configuración aconseja una alternativa, explica las ventajas y limitaciones. Evita perder información al cerrar la aplicación. Centraliza el acceso a datos, gestiona errores y proporciona archivos completos. No alteres funcionalidades existentes que ya se hayan probado.

### Prompt 7 — Progreso y estadísticas

> Implementa estadísticas basadas en entrenamientos guardados: sesiones, volumen acumulado, series, historial, evolución de cargas y récords por ejercicio. No muestres datos ficticios cuando existan registros reales. Si el historial está vacío, crea un estado vacío informativo. Analiza librerías de gráficas compatibles antes de añadir dependencias. Mantén la interfaz legible y entrega una implementación funcional con los archivos completos.

### Prompt 8 — Depuración

> Analiza el código actual de ATHLOS y el error de compilación o ejecución que te proporcionaré. Identifica el origen probable y clasifícalo (sintaxis, dependencias, configuración, tipos, estado, navegación, persistencia o lógica). Explica por qué ocurre y propone la corrección mínima. Comprueba compatibilidad con las versiones actuales. No reescribas archivos ajenos al problema, no inventes APIs y solicita la información que falte si no se puede diagnosticar con certeza. Proporciona los archivos corregidos completos cuando sea necesario.

### Prompt 9 — Revisión y pruebas

> Realiza una revisión técnica de ATHLOS. Comprueba compilación, navegación, validación, CRUD, persistencia, cálculos de volumen, temporizador, estados, botones sin acción, organización y compatibilidad de dependencias. Genera una checklist de pruebas manuales reproducibles para cada módulo. Clasifica hallazgos por prioridad (crítico, recomendable y opcional). No consideres una funcionalidad terminada solo porque tenga interfaz: verifica que la acción produce el resultado esperado.

## 6. Principales aprendizajes adquiridos

Este apartado se debe actualizar al terminar el proyecto con aprendizajes comprobados. Como objetivos de aprendizaje se incluyen:

- Desarrollar interfaces Android utilizando Kotlin y Jetpack Compose.
- Organizar pantallas y componentes reutilizables.
- Gestionar estados y navegación entre secciones.
- Modelar rutinas, ejercicios, sesiones y series mediante clases.
- Aplicar lógica de cálculo y validación de datos.
- Guardar y recuperar información local.
- Diagnosticar errores de compilación y ejecución.
- Utilizar asistentes de IA de manera crítica: revisar, adaptar, probar y comprender el código generado, en lugar de aceptarlo automáticamente.

## 7. Limitaciones encontradas y mejoras futuras

### Limitaciones de la versión inicial

- La aplicación está pensada para un solo usuario y almacenamiento local.
- No dispone de sincronización entre dispositivos ni cuenta de usuario.
- Las estadísticas dependen de los datos registrados manualmente.
- El catálogo de ejercicios es limitado y está predefinido.
- El temporizador de descanso es básico y permite seleccionar una cuenta atrás; no dispone de controles avanzados de pausa/reanudación.
- En esta primera versión no se ha implementado edición de rutinas ya creadas; se pueden crear y eliminar.
- La duración de sesión no se calcula todavía como cronómetro completo.
- No hay integración con wearables ni servicios externos.
- La estructura de partida concentra parte del código en un archivo y puede modularizarse más.

### Mejoras futuras

- Refactorizar hacia MVVM con ViewModel y Repository por módulos.
- Migrar almacenamiento a Room.
- Añadir registro de duración real de cada entrenamiento.
- Implementar gráficas de evolución por ejercicio.
- Añadir edición de rutinas y personalización avanzada de series.
- Incorporar notificaciones de descanso y recordatorios.
- Añadir autenticación y sincronización en la nube.
- Integrar dispositivos deportivos o smartwatch.
- Exportar historial y estadísticas.
- Añadir planificación semanal y objetivos más detallados.

## Ejecutar el proyecto

1. Descomprime el proyecto y abre la carpeta `ATHLOS` en Android Studio (Open).
2. Acepta la sincronización de Gradle.
3. Si Android Studio solicita instalar Android SDK 35, instala el SDK desde SDK Manager.
4. Selecciona un emulador Android o conecta un dispositivo con depuración USB habilitada.
5. Pulsa Run (▶).

La configuración utiliza Android Gradle Plugin 8.9.2, Kotlin 2.0.21, compile SDK 35 y mínimo Android 8.0 (API 26). Si el entorno de Android Studio propone una actualización o presenta incompatibilidades, revisa primero los mensajes de Gradle y el SDK instalado.

## Nota de desarrollo

Este repositorio contiene una base inicial funcional para continuar desarrollando ATHLOS. Antes de entregar, ejecutar en Android Studio, probar cada flujo y actualizar el README con las funcionalidades realmente verificadas, errores encontrados y correcciones aplicadas.
