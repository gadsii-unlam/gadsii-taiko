# Brief de Producto - UNLaM WayFinder

**Equipo:** TAIKO

**Versión:** 3 — TP3 (05/09/2026)

**Estado:** Scope de MVP definido, con hipótesis de valor validada en TP2

> Aplicación de orientación e información dinámica para estudiantes
> ingresantes y de primeros años de la UNLaM.

## **Versión 3 — TP3 (05/09/2026)**

**Qué cambió respecto de la versión anterior y por qué:** Esta tercera versión del brief incorpora las definiciones sobre el scope del MVP que permite testear la hipótesis de valor formulada en el TP2, la distinción entre qué se construye de verdad y qué se resuelve a mano o se simula, el flujo principal de interacción del usuario, y los atributos de usabilidad priorizados con su justificación basada en el relevamiento.

---

## 0. Resumen del producto

|  |  |
| --- | --- |
| **Producto** | UNLaM WayFinder |
| **Equipo** | TAIKO |
| **Segmento** | Ingresantes y Estudiantes 1.º y 2.º año |
| **Usuarios primarios** | Ingresantes y Estudiantes 1.º y 2.º año |
| **Problema central** | Dificultad de los estudiantes ingresantes y de primeros años para ubicarse dentro de la Universidad y acceder rápidamente a información actualizada sobre aulas, horarios, instalaciones y cambios o reasignaciones de última hora. |
| **Usuarios secundarios** | Profesores y administrativos vinculados a la gestión de aulas. |

---

## 1. Segmento Elegido de la Comunidad UNLaM y por qué ese

El segmento específico sobre el cual se hace foco son los estudiantes ingresantes y de primer y segundo año de carreras de grado de la Universidad Nacional de La Matanza (UNLaM), pertenecientes a cualquier departamento académico y turno de cursada (mañana, tarde o noche), estimado en aproximadamente 30.000 a 35.000 estudiantes activos.

### Problemática del segmento

Estos estudiantes necesitan tener un control y conocimiento más claro acerca de las aulas en las que deben cursar y/o rendir exámenes durante los cuatrimestres y mesas de exámenes, además de disponer de información básica sobre otras instalaciones (biblioteca, comedor universitario, centro de estudiantes, enfermería, etc.), incluyendo su localización exacta, disponibilidad, carrera, comisión y materia.

Lo que distingue principalmente a este segmento es su escaso conocimiento de la distribución física del predio (sectores, alas, cuerpos, pisos y aulas especiales). Por este motivo, dependen de consultas presenciales o a terceros, generando mayor desorientación ante cambios o reasignaciones imprevistas de aulas.

### ¿Por qué se eligió este segmento?

* Falta de una plataforma unificada: Actualmente no existe un espacio donde se centralice esta información y mucha de ella no se encuentra a disposición del alumnado, generando pérdida de tiempo.
* Procesos actuales deficientes: Durante los exámenes finales, por ejemplo, los listados se publican en tablones (a veces en fotocopias) y los cambios de última hora se realizan manualmente con lapicera, lo que genera confusión.
* Menor fricción en otros grupos: Los estudiantes avanzados ya memorizaron los recorridos y la dinámica de la universidad, por lo que el impacto en ellos es considerablemente menor. En cambio, en los ingresantes y primeros años se concentra la mayor fricción al trasladarse, buscar aulas o encontrar espacios para estudiar.

---

## 2. Perfil de Usuario Real, Necesidades, Problemas y Contexto de Uso (Relevado)

### Perfil del usuario real (Basado en U1, U2 y U3)

* **U1:** Estudiante de primer año de Medicina, turno mañana, con entre 6 meses y 1 año en la institución. Se traslada usando su celular y datos móviles.
* **U2:** Estudiante ingresante de Comunicación Social, turno mañana, con menos de 6 meses en la universidad. Utiliza la red Wi-Fi del campus.
* **U3:** Estudiante de segundo año de Relaciones Públicas, turno noche, con entre 1 y 2 años de trayectoria. Se conecta mediante la red Wi-Fi institucional.

### Necesidades reales relevadas

* Disponer de mapas interactivos o esquemas numéricos claros dentro de los departamentos académicos.
* Contar con notificaciones automáticas y directas ante cambios de última hora, evitando depender de avisos informales.

### Problemas y frustraciones concretas

* Desorientación severa al recibir indicaciones espaciales imprecisas o genéricas.
* Pérdida de tiempo real de entre 5 y 15 minutos ante modificaciones de aulas, derivando en llegadas tarde y altos niveles de estrés o preocupación.
* Dependencia obligada de canales informales (grupos de WhatsApp, compañeros o personal de seguridad).

### Contexto de uso

* **Cuándo:** En los momentos previos al ingreso a clases o exámenes, o ante modificaciones imprevistas.
* **Dónde:** Dentro del predio de la UNLaM, al transitar por pasillos, edificios, alas o departamentos desconocidos.
* **Dispositivo:** Exclusivamente a través de teléfonos celulares (smartphones).
* **Condiciones:** Escenarios duales de planificación con tiempo o situaciones de urgencia/apuro.
* **Acompañamiento:** Consultas realizadas predominantemente de forma individual (solos/as).
* **Conectividad:** Operando mediante datos móviles personales o red Wi-Fi institucional.

---

## 3. Producto

**Nombre:** UNLaM WayFinder (Front-end hosteado en Netlify y back-end alojado en Supabase).

**Problema que resuelve:** La falta de información centralizada sobre ubicación de aulas, la deficiente gestión de cambios de última hora y la desorientación espacial en el campus.

**A quién le resuelve:**

* **Principalmente:** Estudiantes ingresantes y de primer/segundo año.
* **Secundariamente:** Profesores y personal administrativo encargados de la gestión de aulas.

---

## 4. Funcionalidades Core

* **Disponibilidad de información básica:** Consulta de la disponibilidad de aulas e instalaciones en un día y franja horaria concreta (incluyendo carrera, materia, comisión y docentes asignados).
* **Vistas diferenciadas por roles:** Tres perfiles distintos ("Estudiante", "Profesor" y "Administrativo"), cada uno con permisos y funciones específicas.
* **Administración en tiempo real:** Panel para el usuario administrativo que permite actualizar el estado y la disponibilidad de las aulas de forma inmediata para el resto de los usuarios.
* **Sistema de notificaciones:** Alertas configurables según las preferencias del usuario ante cambios de aula, confirmación de aulas de exámenes, etc.
* **Información de transporte:** Datos básicos sobre los diferentes medios de transporte públicos circundantes a la Universidad.

---

## 5. Integraciones Previstas

| Integración | ¿Para qué se utiliza? |
| --- | --- |
| **Datos institucionales** | Carreras disponibles, planes de estudio actualizados, mapa de la universidad, horarios oficiales de instalaciones y materias cursadas por el alumno (opcional). |
| **SIU-Guaraní** | Integración con la API de SIU-Guaraní para verificar la condición de estudiante activo y comprobar su identidad. |
| **Geolocalización / GPS** | Integración con un sistema de geolocalización para mostrar rutas en el mapa desde la ubicación actual del usuario hasta el punto de destino dentro de la universidad. |
| **Transporte público** | Integración con una API externa para obtener información en tiempo real sobre los horarios aproximados del transporte público en la zona. |

---

## 6. Grupos de Usuarios y Usuario Primario Elegido

### **Estudiantes ingresantes y de primer y segundo año (Grupo Primario - Validado)**

* **Descripción:** Alumnos de grado con poca familiaridad con la distribución física de la universidad.
* **Motivación:** Consultar rápidamente la ubicación de aulas y espacios, recibir notificaciones de cambios y evitar gestiones presenciales o informales.

### **Profesores**

* **Descripción:** Docentes que dictan clases en distintas aulas.
* **Motivación:** Consultar disponibilidad de espacios y solicitar cambios de aula de manera sencilla ante imprevistos.

### **Administrativos**

* **Descripción:** Personal a cargo de la gestión, asignación y disponibilidad de los espacios universitarios.
* **Motivación:** Centralizar la información, actualizar estados en tiempo real y agilizar las reasignaciones de comisiones.

> **Validación del usuario primario:** Tras el relevamiento del TP2, se confirma que el grupo primario seleccionado sigue siendo el correcto, ya que los ingresantes y alumnos de 1.° y 2.° año concentran las mayores dificultades de orientación y fricciones ante cambios de aula.

---

## 7. Hipótesis de Valor

> Creemos que los estudiantes ingresantes y de primer y segundo año de la UNLaM que se desplazan por el campus utilizando sus teléfonos celulares con datos móviles o Wi-Fi, tiene el problema de sufrir desorientación al buscar aulas desconocidas y perder valioso tiempo (entre 5 y 15 minutos) o llegar tarde debido a cambios de última hora y a la escasez de información centralizada, nuestra solución es UNLaM WayFinder, una plataforma con mapas interactivos y sistema de notificaciones automáticas ante reasignaciones, y sabremos que estamos en lo correcto cuando los usuarios utilicen activamente la aplicación para consultar su ubicación y reciban alertas, reduciendo los tiempos de búsqueda y manifestando conformidad en sus trayectos dentro del campus.

---

## 8. Estado de los Supuestos del TP1

| Supuesto del TP1 | ¿Se confirmó? | Evidencia obtenida en el relevamiento (TP2) |
| --- | --- | --- |
| **[SUPUESTO CRITICO]** S1 — Familiarización con la Universidad | **Confirmado** | Los tres usuarios encuestados manifestaron dificultades de orientación espacial al transitar por el campus. |
| S2 — Información sobre aulas | **Confirmado** | U2 y U3 confirmaron haber tenido dificultades ante cambios o reasignaciones de último momento, debiendo destinar tiempo extra a buscarlas. |
| S3 — Mapa actual de la Universidad | **Confirmado** | El 100% de los usuarios evaluó la señalización física como insuficiente, confusa o regular, y U2 solicitó un mapa en cada departamento. |
| S4 — Medios informales actuales | **Confirmado** | Ante la falta de información oficial, los usuarios recurren al personal de seguridad, compañeros o grupos de WhatsApp. |
| S5 — Cambios y reasignaciones | **Confirmado** | Se comprobó que enterarse tarde genera pérdidas de tiempo (5 a 15 min), llegadas tarde y niveles de estrés. |
| S6 — Transporte público | **Sin evidencia directa** | Los usuarios resuelven esto mediante herramientas externas como Google Maps, sin manifestar demanda activa de integración en esta etapa. |
| S7 — Solicitud de cambios de aula (Profesores) | **Sin evidencia (Fuera del alcance)** | No se realizaron mediciones directas sobre este grupo en el relevamiento enfocado en estudiantes. |
| S8 — Gestión administrativa de aulas | **Sin evidencia (Fuera del alcance)** | Premisa de gestión interna que no contó con datos empíricos en esta instancia estudiantil. |

---

## 9. Scope del MVP
 
El MVP es lo mínimo necesario para testear la hipótesis de valor, no el producto completo.
 
| Incluido en el MVP | Para qué parte de la hipótesis sirve |
| --- | --- |
| Visualización del plano general del campus y selección de destinos (aulas, dependencias y servicios). | Testea si los ingresantes logran identificar visualmente su punto de partida y llegada sin depender de indicaciones verbales de terceros. |
| Visualización de la ubicación del aula dentro del mapa del campus (navegación por niveles predio → planta → aula). | Ataca el componente más frecuente y mejor confirmado de la hipótesis: la desorientación al buscar aulas desconocidas (supuesto crítico del TP1). En la Q5 del TP2, 2 de los 3 usuarios calificaron la orientación general como difícil, es el problema de fondo que el mapa por niveles busca resolver, independientemente de si hubo o no una reasignación. |
| Sistema de notificaciones ante cambios de última hora (aviso dentro de la app). | Relacionado directamente a el segundo componente de la propuesta de valor definida ("un sistema de notificaciones automáticas ante reasignaciones") y su criterio de validación. Es además la funcionalidad que 2 de los 3 usuarios relevados (U2 y U3) priorizaron por sobre el mapa en la pregunta 29 del TP2. |

<br>
 
| Excluido del MVP | Por qué se excluye |
| --- | --- |
| Integración con los sistemas administrativos internos de la Universidad (el software que usa el personal para gestionar aulas). | El circuito de registro de cambios se construye dentro de la propia interfaz de WayFinder, sin conectarse a los sistemas que la Universidad ya usa internamente.<br>Conseguir ese acceso está fuera de nuestro alcance y no aporta a validar si el estudiante encuentra valor en recibir el aviso. |
| Integración con la API de SIU-Guaraní, posicionamiento en tiempo real (GPS al aire libre, geofencing dentro de los edificios) y pathfinding. | La validación se centra en la utilidad cognitiva de la ruta visualizada, no en la validación de identidad ni en la tecnología de geolocalización en vivo ya que suman complejidad técnica innecesaria para esta etapa. Pathfinding requeriría modelar los pasillos como un grafo navegable. |
| Consulta de transporte público, horarios de instalaciones no académicas (comedor, enfermería, etc.). | El TP2 no encontró evidencia de que incluirlo ayude a confirmar o refutar la hipótesis en esta etapa: los usuarios ya cubren transporte por otros medios, sin manifestar demanda activa de integrarlo.<br>No significa que no sea importante, simplemente no forma parte del núcleo de los problemas de los que este MVP necesita aprender. |
| Vista diferenciada para Profesores y Administrativos (login, permisos y pantallas propias por rol). | El MVP solo necesita validar el problema del usuario primario (estudiantes). El registro de cambios de aula durante la prueba lo resuelve un integrante del equipo directamente en Supabase (ver punto 10), sin necesitar una interfaz de administrador construida.<br>Además, los supuestos sobre profesores y administrativos (S7 y S8) quedaron "sin evidencia / fuera de alcance" en el TP2: no hay todavía evidencia real sobre esos grupos que justifique construirles una vista en esta etapa. |

> **Sobre pathfinding:** En una versión futura del producto, se planea implementar el pathfinding junto con la selección de origen, resolviendo la limitación de tener que reconocer el propio edificio/deparamento por nombre en el mapa general en vez de que la app lo indique directamente.

---
 
## 10. Qué se construye y qué se simula
 
| Elemento | Se construye | Se simula / se resuelve a mano | Por qué |
| :---: | :---: | :---: | :---: |
| Interfaz de usuario (Frontend) | ✓ | | Componente de software propio del equipo, debe estar construido de verdad en Netlify para garantizar una experiencia interactiva real. |
| Base de datos de aulas y ubicaciones | | ✓ | Se precargan los datos de las ubicaciones y los trayectos manualmente en Supabase o en un archivo estático, ya que el objetivo es evaluar la utilidad de la ruta y no automatizar la ingesta de bases institucionales masivas. |
| Resaltado de ubicación en el mapa | ✓ | | Se implementa la lógica visual para resaltar el aula seleccionada y su estado, sin calcular una ruta desde un origen |
| Aviso de reasignación de aula | ✓<br>(pantalla/banner que ve el estudiante) | ✓<br>(detección del cambio) | La consulta siempre trae el estado actual del aula y avisa si difiere de la habitual. Lo que no se automatiza es enterarse del cambio: hoy no hay fuente digital, un integrante del equipo actualiza el registro en Supabase cuando el profesor lo pide. |
| Validación de identidad del estudiante (SIU-Guaraní) | ✗ | ✗ | No aporta a testear la hipótesis; se excluye del MVP sin necesidad de simularla. |
 
---
 
## 11. Flujo principal del MVP
 
1. **Apertura de la aplicación:** El estudiante ingresa desde su celular a la plataforma web alojada en Netlify.
2. **Exploración o búsqueda:** El usuario navega el mapa general del predio por pabellón, o busca directamente el aula, materia o comisión que necesita.
3. **Selección del aula:** Si el edificio tiene más de un piso, elige la planta correspondiente; luego selecciona el aula específica.
4. **Visualización del estado:** El sistema muestra el aula resaltada en el mapa, con su estado y, si corresponde, el aviso de reasignación.
5. **Obtención del valor:** El estudiante identifica con claridad dónde queda el aula y se desplaza de forma autónoma, evitando pérdidas de tiempo y llegadas tarde.
---
 
## 12. Atributos de usabilidad priorizados
 
* **Facilidad de aprendizaje:** Prioritario porque los ingresantes se enfrentan por primera vez a la distribución física de la UNLaM y poseen nula familiaridad con cuerpos, alas y pisos. La interfaz debe ser intuitiva de forma inmediata, sin curva de aprendizaje previa ni manuales de uso.
  
* **Eficiencia:** Se prioriza porque los estudiantes relevados manifestaron transitar bajo situaciones de apuro y con tiempos acotados entre clases o antes de rendir un examen. El sistema debe resolver la búsqueda de una ubicación en pocos pasos, minimizando el tiempo de interacción con el celular mientras caminan por el predio.


