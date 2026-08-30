# Brief de Producto - Unlam WayFinder<!-- Versión 1 — TP1. Cada versión siguiente abre con un párrafo de qué cambió y por qué. -->

**Equipo:** TAIKO  
**Versión:** 1 — TP1  
**Estado:** Hipótesis inicial

> Aplicación de orientación e información dinámica para estudiantes
> ingresantes y de primeros años de la UNLaM.

## **Versión 1 (TP1)**

Esta es la primera versión del brief del producto UNLAM WayFinder, desarrollado por el equipo TAIKO. Al tratarse de la versión inicial, este documento establece las bases del proyecto definidas en el Trabajo Práctico 1, las cuales irán evolucionando y actualizándose en los próximos trabajos prácticos.

## 0. Resumen del producto

| | |
|---|---|
| **Producto** | UNLaM WayFinder |
| **Equipo** | TAIKO |
| **Segmento** | Ingresantes y Estudiantes 1.º y 2.º año |
| **Usuarios primarios** | Ingresantes y Estudiantes 1.º y 2.º año |
| **Problema central** | Dificultad de los estudiantes ingresantes y de primeros años para ubicarse dentro de la Universidad y acceder rápidamente a información actualizada sobre aulas, horarios, instalaciones, transporte y cambios o reasignaciones de aula. |
| **Usuarios secundarios** | Profesores y administrativos vinculados a la gestión de aulas. |

---
## 1. Segmento Elegido de la Comunidad UNLaM y por qué ese
El segmento específico sobre el cual se hace foco son los estudiantes ingresantes y de primer y segundo año de carreras de grado de la Universidad Nacional de La Matanza (UNLaM), pertenecientes a cualquier departamento académico y turno de cursada (mañana, tarde o noche), estimado en aproximadamente 30.000 a 35.000 estudiantes activos.

### Problemática del segmento
Estos estudiantes necesitan tener un control y conocimiento más claro acerca de las aulas en las que deben cursar y/o rendir exámenes durante los cuatrimestres y mesas de exámenes, además de disponer de información básica sobre otras instalaciones (biblioteca, comedor universitario, centro de estudiantes, enfermería, etc.), incluyendo su localización exacta, disponibilidad, carrera, comisión y materia.

Lo que distingue principalmente a este segmento es su escaso conocimiento de la distribución física del predio (sectores, alas, cuerpos, pisos y aulas especiales). Por este motivo, dependen de consultas presenciales o a terceros, generando mayor desorientación ante cambios o reasignaciones imprevistas de aulas.

### ¿Por qué se eligió este segmento?
- Falta de una plataforma unificada: Actualmente no existe un espacio donde se centralice esta información y mucha de ella no se encuentra a disposición del alumnado, generando pérdida de tiempo.

- Procesos actuales deficientes: Durante los exámenes finales, por ejemplo, los listados se publican en tablones (a veces en fotocopias) y los cambios de última hora se realizan manualmente con lapicera, lo que genera confusión.

- Menor fricción en otros grupos: Los estudiantes avanzados ya memorizaron los recorridos y la dinámica de la universidad, por lo que el impacto en ellos es considerablemente menor. En cambio, en los ingresantes y primeros años se concentra la mayor fricción al trasladarse, buscar aulas o encontrar espacios para estudiar.
---
## 2. Producto
**Nombre:** UNLAM WayFinder (Front-end hosteado en Netlify y back-end alojado en Supabase).

**Problema que resuelve:** La falta de información centralizada, la dificultad en la gestión de las instalaciones universitarias y la desorientación en los desplazamientos dentro del predio.

**A quién le resuelve:**

- **Principalmente:** Estudiantes ingresantes y de primer/segundo año.

- **Secundariamente:** Profesores y personal administrativo encargados de la gestión de aulas.
---
## 3. Funcionalidades Core
- **Disponibilidad de información básica:** Consulta de la disponibilidad de aulas e instalaciones en un día y franja horaria concreta (incluyendo carrera, materia, comisión y docentes asignados).

- **Vistas diferenciadas por roles:** Tres perfiles distintos ("Estudiante", "Profesor" y "Administrativo"), cada uno con permisos y funciones específicas.

- **Administración en tiempo real:** Panel para el usuario administrativo que permite actualizar el estado y la disponibilidad de las aulas de forma inmediata para el resto de los usuarios.

- **Sistema de notificaciones:** Alertas configurables según las preferencias del usuario ante cambios de aula, confirmación de aulas de exámenes, etc.

- **Información de transporte:** Datos básicos sobre los diferentes medios de transporte públicos circundantes a la Universidad.
---
## 4. Integraciones Previstas

| Integración | ¿Para qué se utiliza? |
|---|---|
| **Datos institucionales** | Carreras disponibles, planes de estudio actualizados, mapa de la universidad, horarios oficiales de instalaciones y materias cursadas por el alumno (opcional). |
| **SIU-Guaraní** | Integración con la API de SIU-Guaraní para verificar la condición de estudiante activo y comprobar su identidad. |
| **Geolocalización / GPS** | Integración con un sistema de geolocalización para mostrar rutas en el mapa desde la ubicación actual del usuario hasta el punto de destino dentro de la universidad. |
| **Transporte público** | Integración con una API externa para obtener información en tiempo real sobre los horarios aproximados del transporte público en la zona. |

---
## 5. Grupos de Usuarios y Usuario Primario Elegido
### **Estudiantes ingresantes y de primer y segundo año (Grupo Primario)**

- **Descripción:** Alumnos de grado con poca familiaridad con la distribución física de la universidad.

- **Motivación:** Consultar rápidamente la ubicación de aulas y espacios, recibir notificaciones de cambios y evitar gestiones presenciales o informales.

### **Profesores**

- **Descripción:** Docentes que dictan clases en distintas aulas.

- **Motivación:** Consultar disponibilidad de espacios y solicitar cambios de aula de manera sencilla ante imprevistos (por ejemplo, falta de espacio).

### **Administrativos**

- **Descripción:** Personal a cargo de la gestión, asignación y disponibilidad de los espacios universitarios.

- **Motivación:** Centralizar la información, actualizar estados en tiempo real y agilizar las reasignaciones de comisiones.

> ⚠️ **Aclaración:** La selección del usuario primario es una hipótesis inicial basada en la información disponible y en los supuestos planteados por el equipo. Esta elección será validada y, de ser necesario, modificada a partir de la evidencia obtenida durante el relevamiento del TP2.
---
### Usuarios reales elegidos

### U1 — Estudiante de primer año

**Rol:** Estudiante de primer año de Medicina de la UNLaM.

**Cómo llegamos a la persona:** A través de un amigo de uno de los integrantes del equipo.

**Relación previa con el equipo:** Amigo.

**Por qué pertenece al segmento:** Pertenece al grupo de estudiantes de primer año definido como segmento y se encuentra en una etapa inicial de su carrera, por lo que todavía posee una experiencia limitada con la distribución de las instalaciones de la Universidad.

---

### U2 — Estudiante ingresante

**Rol:** Estudiante ingresante de Comunicación Social de la UNLaM.

**Cómo llegamos a la persona:** A través de un contacto personal de uno de los integrantes del equipo que actualmente cursa en la Universidad.

**Relación previa con el equipo:** Conocido de uno de los integrantes del equipo.

**Por qué pertenece al segmento:** Es un estudiante recientemente incorporado a la Universidad y todavía se encuentra familiarizándose con la ubicación de las aulas, sectores y demás instalaciones.

---

### U3 — Estudiante de segundo año

**Rol:** Estudiante de segundo año de Relaciones Públicas de la UNLaM.

**Cómo llegamos a la persona:** A través de un integrante del equipo que mantiene una relación personal con la persona.

**Relación previa con el equipo:** Conocido de uno de los integrantes del equipo.

**Por qué pertenece al segmento:** Pertenece al grupo seleccionado y cuenta con mayor experiencia dentro de la Universidad que un ingresante, pero todavía puede experimentar dificultades ante cambios de aula, reasignaciones o la búsqueda de instalaciones que no utiliza habitualmente.

> **Nota:** Las personas seleccionadas pertenecen al grupo de usuarios primario definido para el producto. La relación previa con los integrantes del equipo se explicita para considerar posibles sesgos durante el análisis de los resultados del relevamiento.

> **Disponibilidad:** Se confirma la disponibilidad, tanto para el relevamiento del TP2 como para la prueba del MVP del TP5, de las tres personas que fueron elegidas.

---

## 6. Supuestos

### S1 — Supuesto crítico: Familiarización con la Universidad

> Asumimos que a los estudiantes ingresantes y de los primeros años les cuesta familiarizarse con las instalaciones de la Universidad y conocer su disponibilidad según el día y horario.

### S2 — Información sobre aulas

> Asumimos que los estudiantes tienen dificultades para conocer qué aula les corresponde cuando cursan o rinden un examen, especialmente cuando se producen cambios o reasignaciones.

### S3 — Mapa actual de la Universidad

> Asumimos que el mapa actualmente disponible de la Universidad no resulta suficiente para que los estudiantes se orienten de manera rápida y sencilla dentro de las instalaciones.

### S4 — Medios utilizados actualmente para el acceso a la información

> Asumimos que los estudiantes recurren a otras personas o medios informales para obtener información que no encuentran fácilmente sobre aulas, horarios, instalaciones, servicios o cambios de ubicación dentro de la Universidad.

### S5 — Cambios y reasignaciones

> Asumimos que los estudiantes pueden enterarse tarde de cambios o reasignaciones de aulas y que esto puede generarles inconvenientes.

### S6 — Transporte público

> Asumimos que los estudiantes necesitan información sobre las opciones de transporte público cercanas a la Universidad y que actualmente deben recurrir a medios externos para obtenerla.

### S7 — Solicitud de cambios de aula

> Asumimos que los profesores necesitan un medio más sencillo para solicitar cambios de aula ante imprevistos.

### S8 — Gestión administrativa sobre asignación y reasignación de aulas

> Asumimos que el proceso actual de asignación y reasignación de aulas por parte de los administrativos es poco eficiente.
