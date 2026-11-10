# Brief de Producto - UNLaM WayFinder

**Equipo:** TAIKO

**Versión:** 5 - TP6

**Estado:** MVP construido y probado con usuarios reales en el campus; hipótesis de valor sostenida; decisión: **Perseverar**. Arquitectura actual documentada y gran visión definida en términos técnicos.

> Aplicación de orientación e información dinámica para estudiantes
> ingresantes y de primeros años de la UNLaM.

## **Versión 5 - TP6**

**Qué cambió respecto de la versión 4 y por qué:** Esta quinta versión no modifica el segmento, la hipótesis de valor ni la decisión de perseverar tomada en el TP5. Lo que suma es la mirada técnica del TP6: cómo está construido hoy el MVP (sección 15), la arquitectura del producto completo que imaginamos desde el TP1, marcando qué parte ya cubre el MVP (sección 16), y las restricciones técnicas del contexto que condicionan esa visión (sección 17). Al revisar la arquitectura aparecieron tres definiciones que había que precisar, y se actualizan también en las secciones 4, 5 y 14: el aviso de cambio de aula deja de llegarle a todo el que tenga la app abierta y pasa a dirigirse a los inscriptos en esa materia y comisión, que pueden desactivarlo; la geolocalización queda limitada a ubicar en qué entrada del campus está el estudiante, porque su error no permite distinguir pasillos ni pisos, y la ruta hasta el aula se calcula sobre un grafo de pasillos y escaleras; y las notificaciones push se acotan a Android, porque en iPhone exigen instalar la app en la pantalla de inicio. Se justifican con la evidencia del TP2 y el TP5 y con lo que muestra el código del MVP.

### Historial de versiones anteriores
* **Versión 4 - TP5:** Incorporó las mejoras de usabilidad del TP4 que ingresaron al MVP, los aprendizajes de la prueba presencial con U1, U2 y U3 separados en capa de usabilidad y capa de negocio, el estado de la hipótesis frente al criterio de éxito fijado antes de la prueba, el hallazgo del uso espontáneo del botón *"Compartir"* y la decisión de **perseverar** con sus próximas mejoras priorizadas.
* **Versión 3 - TP3 (06/09/2026):** Incorporó las definiciones sobre el scope del MVP para testear la hipótesis de valor formulada en el TP2, la distinción entre qué se construye de verdad y qué se resuelve a mano o se simula, el flujo principal de interacción del usuario y los atributos de usabilidad priorizados con su justificación basada en el relevamiento.

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
| **URL del MVP** | [https://taiko-unlam.netlify.app/](https://taiko-unlam.netlify.app/) |
| **Estado de la hipótesis (TP5)** | **Sostenida** (3 de 3 usuarios cumplieron ambas métricas del criterio de éxito pre-commiteado). **Decisión: Perseverar** |
| **Arquitectura (TP6)** | Una sola página web en Netlify y un backend gestionado en Supabase (PostgreSQL, Auth, API REST y Realtime). Sin servidor propio. |
| **Plataforma objetivo** | Navegador del celular, con foco en Android. |

---

## 1. Segmento Elegido de la Comunidad UNLaM y por qué ese

El segmento específico sobre el cual se hace foco son los estudiantes ingresantes y de primer y segundo año de carreras de grado de la Universidad Nacional de La Matanza (UNLaM), pertenecientes a cualquier departamento académico y turno de cursada (mañana, tarde o noche), estimado en aproximadamente 30.000 a 35.000 estudiantes activos.

### Problemática del segmento

Estos estudiantes necesitan tener un control y conocimiento más claro acerca de las aulas en las que deben cursar y/o rendir exámenes durante los cuatrimestres y mesas de exámenes, además de disponer de información básica sobre otras instalaciones (biblioteca, comedor universitario, centro de estudiantes, enfermería, etc.), incluyendo su localización exacta, disponibilidad, carrera, comisión y materia.

Lo que distingue principalmente a este segmento es su escaso conocimiento de la distribución física del predio (sectores, alas, cuerpos, pisos y aulas especiales). Por este motivo, dependen de consultas presenciales o a terceros, generando mayor desorientación ante cambios o reasignaciones imprevistas de aulas.

### ¿Por qué se eligió este segmento?

* **Falta de una plataforma unificada:** Actualmente no existe un espacio donde se centralice esta información y mucha de ella no se encuentra a disposición del alumnado, generando pérdida de tiempo.
* **Procesos actuales deficientes:** Durante los exámenes finales, por ejemplo, los listados se publican en tablones (a veces en fotocopias) y los cambios de última hora se realizan manualmente con lapicera, lo que genera confusión.
* **Menor fricción en otros grupos:** Los estudiantes avanzados ya memorizaron los recorridos y la dinámica de la universidad, por lo que el impacto en ellos es considerablemente menor. En cambio, en los ingresantes y primeros años se concentra la mayor fricción al trasladarse, buscar aulas o encontrar espacios para estudiar.

---

## 2. Perfil de Usuario Real, Necesidades, Problemas y Contexto de Uso (Relevado en TP2 y Probado en TP5)

### Perfil del usuario real (Basado en U1, U2 y U3)

* **U1:** Estudiante de primer año de Medicina, turno mañana, con entre 6 meses y 1 año en la institución. Se traslada usando su celular y datos móviles.
* **U2:** Estudiante ingresante de Comunicación Social, turno mañana, con menos de 6 meses en la universidad. Utiliza la red Wi-Fi del campus.
* **U3:** Estudiante de segundo año de Relaciones Públicas, turno noche, con entre 1 y 2 años de trayectoria. Se conecta mediante la red Wi-Fi institucional y suele desplazarse apurado/a.

### Necesidades reales relevadas y validadas en campo

* Disponer de mapas interactivos o esquemas numéricos claros dentro de los departamentos académicos, complementados con un buscador directo por materia, comisión o número de aula.
* Contar con referencias explícitas del piso (planta baja vs. primer piso) y del punto de acceso (puerta o escalera) al ingresar físicamente a un departamento.
* Recibir notificaciones directas y avisos persistentes ante cambios de última hora, evitando depender de avisos informales, y poder compartir fácilmente la ubicación exacta de un aula con compañeros por WhatsApp.

### Problemas y frustraciones concretas

* Desorientación severa al recibir indicaciones espaciales imprecisas o genéricas (especialmente dentro del edificio o cuando el sector buscado está en un primer piso sobre otro departamento, como Ingeniería sobre Humanidades).
* Pérdida de tiempo real de entre 5 y 15 minutos ante modificaciones de aulas, derivando en llegadas tarde y altos niveles de estrés o preocupación.
* Dependencia obligada de canales informales (grupos de WhatsApp, compañeros o personal de seguridad).

### Contexto de uso

* **Cuándo:** En los momentos previos al ingreso a clases o exámenes, o ante modificaciones imprevistas.
* **Dónde:** Dentro del predio de la UNLaM, al transitar por pasillos, escaleras, edificios, alas o departamentos desconocidos (con la atención dividida entre el camino físico y la pantalla del celular).
* **Dispositivo:** Exclusivamente a través de teléfonos celulares (smartphones).
* **Condiciones:** Escenarios duales de planificación con tiempo o situaciones de urgencia/apuro en movimiento.
* **Acompañamiento:** Consultas realizadas predominantemente de forma individual (solos/as), aunque con uso frecuente del enlace directo del aula para compartir la ubicación en grupos de WhatsApp de cursada.
* **Conectividad:** Operando mediante datos móviles personales o red Wi-Fi institucional.

---

## 3. Producto

**Nombre:** UNLaM WayFinder (Front-end hosteado en Netlify y back-end con sincronización en tiempo real alojado en Supabase).

**Problema que resuelve:** La falta de información centralizada sobre ubicación de aulas, la deficiente gestión de cambios de última hora y la desorientación espacial en el campus.

**A quién le resuelve:**

* **Principalmente:** Estudiantes ingresantes y de primer/segundo año.
* **Secundariamente:** Profesores y personal administrativo encargados de la gestión de aulas.

> **Nota sobre el diseño visual del MVP:** El aspecto visual actual de la aplicación (colores, tipografía, íconos y estilos generales) es provisorio y está sujeto a cambios. Para el MVP se priorizó que las funcionalidades necesarias para validar la hipótesis de valor estuvieran operativas por sobre el diseño gráfico definitivo.

---

## 4. Funcionalidades Core

* **Disponibilidad de información básica y buscador unificado:** Consulta de la disponibilidad de aulas e instalaciones en un día y franja horaria concreta (Mañana, Tarde y Noche), incluyendo carrera, materia, comisión y estado, con autocompletado desde el primer carácter.
* **Navegación espacial por niveles con contexto:** Mapa general del campus por departamentos y plano interno de cada sector/piso con resaltado del aula seleccionada y transición visual que muestra primero dónde queda el departamento en el predio antes de abrir su plano interno.
* **Vistas diferenciadas por roles:** Tres perfiles previstos ("Estudiante", "Profesor" y "Administrativo"), cada uno con permisos y funciones específicas (en el MVP se priorizó la vista del estudiante y un panel operativo de administración `?admin`).
* **Administración en tiempo real:** Panel para el usuario administrativo que permite actualizar el estado y las reasignaciones de las aulas de forma inmediata en Supabase para el resto de los usuarios.
* **Sistema de notificaciones y avisos de cambio de aula:** Alertas ante cambios de aula mediante dos mecanismos combinados en la app (un aviso emergente en vivo en la parte inferior de la pantalla y un cartel fijo de traslado dentro de la ficha tanto del aula original como del aula nueva), con evolución prevista hacia notificaciones Web Push dirigidas solo a los inscriptos en esa materia y comisión, que pueden desactivarlas.
* **Enlace directo compartible por aula (`Compartir`):** Función en la ficha de cada aula que genera un enlace directo (`?aula=X&ed=Y`) para enviarlo por WhatsApp a otros compañeros.
* **Información de transporte:** Datos básicos sobre los diferentes medios de transporte públicos circundantes a la Universidad (previsto fuera del MVP inicial).

---

## 5. Integraciones Previstas

| Integración | ¿Para qué se utiliza? |
| --- | --- |
| **Datos institucionales** | Carreras disponibles, comisiones reales, mapa de la universidad, planos por departamento y horarios oficiales de instalaciones y materias cursadas por el alumno. |
| **Supabase Realtime** | Sincronización en tiempo real de ocupaciones y cambios de aula entre el panel de gestión y los teléfonos de los estudiantes. |
| **Notificaciones Web Push (Próximo paso priorizado tras TP5)** | Envío de notificaciones al sistema operativo del celular para enterarse de cambios de aula incluso con el teléfono bloqueado en el bolsillo. Llegan solo a los inscriptos en esa materia y comisión, que pueden desactivar el aviso. Alcance: Android. |
| **SIU-Guaraní** | Integración futura con la API de SIU-Guaraní para verificar la condición de estudiante activo, comprobar su identidad y conocer sus inscripciones (materias y comisiones), que definen a quién le llega cada aviso. Hoy los horarios se extrajeron una sola vez y se cargaron con scripts SQL. |
| **Geolocalización / GPS** | Ubicar en qué entrada del campus está el estudiante, como punto de partida de la ruta hasta el aula. La ruta se calcula sobre un grafo de pasillos y escaleras, no con el GPS, porque su error no distingue pasillos ni pisos (ver sección 17). |
| **Transporte público** | Integración futura con una API externa para obtener información en tiempo real sobre los horarios aproximados del transporte público en la zona. |

---

## 6. Grupos de Usuarios y Usuario Primario Elegido

### **Estudiantes ingresantes y de primer y segundo año (Grupo Primario - Validado en TP2 y TP5)**

* **Descripción:** Alumnos de grado con poca familiaridad con la distribución física de la universidad.
* **Motivación:** Consultar rápidamente la ubicación de aulas y espacios, recibir notificaciones de cambios y evitar gestiones presenciales o informales.

### **Profesores**

* **Descripción:** Docentes que dictan clases en distintas aulas.
* **Motivación:** Consultar disponibilidad de espacios y solicitar cambios de aula de manera sencilla ante imprevistos.

### **Administrativos**

* **Descripción:** Personal a cargo de la gestión, asignación y disponibilidad de los espacios universitarios.
* **Motivación:** Centralizar la información, actualizar estados en tiempo real y agilizar las reasignaciones de comisiones.

> **Validación del usuario primario:** Tras el relevamiento del TP2 y la prueba de campo del TP5 en el campus, se confirma que el grupo primario seleccionado es el correcto: los ingresantes y alumnos de 1.° y 2.° año concentran las mayores dificultades de orientación (especialmente al ingresar a edificios desconocidos o sectores en planta alta) y las mayores pérdidas de tiempo ante cambios de aula de último momento.

---

## 7. Hipótesis de Valor y Estado tras el TP5

> **Hipótesis de valor (TP2):** Creemos que los estudiantes ingresantes y de primer y segundo año de la UNLaM que se desplazan por el campus utilizando sus teléfonos celulares con datos móviles o Wi-Fi, tienen el problema de sufrir desorientación al buscar aulas desconocidas y perder valioso tiempo (entre 5 y 15 minutos) o llegar tarde debido a cambios de última hora y a la escasez de información centralizada; nuestra solución es UNLaM WayFinder, una plataforma con mapas interactivos y sistema de notificaciones automáticas ante reasignaciones, y sabremos que estamos en lo correcto cuando los usuarios utilicen activamente la aplicación para consultar su ubicación y reciban alertas, reduciendo los tiempos de búsqueda y manifestando conformidad en sus trayectos dentro del campus.

### **Estado de la hipótesis tras la prueba del MVP (TP5): SOSTENIDA**

Para evaluar la hipótesis sin sesgos se fijaron antes de salir al campus dos métricas con su umbral de éxito (**al menos 2 de los 3 usuarios debían cumplir ambas métricas**), medidas de forma aproximada por observación directa acompañando a cada participante desde la entrada principal del campus:

1. **Métrica 1: Tiempo hasta llegar al aula buscada (Criterio: al menos 2 de 3 usuarios en menos de 5 minutos, sin pedir ayuda a terceros):**
   * **Resultado:** **3 de 3 usuarios cumplieron** sin pedir ayuda a otras personas ni entrar a un aula equivocada:
     * **U1** (Económicas · Aula 313, *Elementos de Costos*, com. `01-1343`): **Entre 3 y 4 minutos** (Cumple). Encontró la comisión con el buscador en menos de un minuto; al entrar al pasillo dudó unos segundos porque el plano no indica por qué puerta se ingresa (`E02`).
     * **U2** (Arquitectura · Aula 257, *Computación Nivel I*, com. `10-2600`): **Algo más de 4 minutos** (Cumple). Entró primero por la lista de departamentos y exploró el plano aula por aula sin encontrar la comisión (`E05`, `E06`); volvió atrás, usó el buscador y desde ahí caminó sin dudas.
     * **U3** (Ingeniería · Aula 142, 1.° piso, *Programación Básica II*, com. `02-3300`): **Cerca de 4 minutos y medio** (Cumple, cerca del límite de los 5 minutos). Encontró la comisión con el buscador casi de inmediato; al llegar, recorrió la planta baja de Humanidades buscando el aula 142 antes de advertir en el mapa general (capa Planta Alta) que Ingeniería (`135 a 143`) estaba en el 1.° piso (`E09`).
   * **Lectura frente a la línea base del TP2:** En los tres casos la búsqueda en la app y la lectura del plano llevaron alrededor de un minuto o menos, reduciendo los 5 a 15 minutos de pérdida de tiempo y consultas informales relevados en el TP2.

2. **Métrica 2: Tiempo hasta enterarse de un cambio de aula de último momento (Criterio: al menos 2 de 3 usuarios en menos de 1 minuto desde que se registra el cambio, con la app abierta):**
   * **Resultado:** **3 de 3 usuarios cumplieron** en menos de un minuto:
     * **U1** (Formación Continua, Aula `222 → 234`): **Menos de medio minuto** (Cumple). Vio el aviso emergente mientras miraba el plano, lo tocó y la app lo llevó al aula nueva.
     * **U2** (Salud, Aula `513 → 602`): **Menos de medio minuto** (Cumple). Venía caminando; vio el aviso emergente sobre el final, justo antes de que se cerrara solo (dura 9 segundos), y lo tocó (`E07`).
     * **U3** (Derecho, Aula `421 → 405`): **Menos de un minuto** (Cumple). No vio el aviso emergente de 9 segundos porque bajó el celular para bajar una escalera (`E10`); se enteró al volver a mirar la ficha del aula 421, que mostraba fijo el cartel *"Esta clase se mudó"* con el botón *"Ir al aula 405"*.

3. **Aclaraciones metodológicas sobre el alcance de la validación:**
   * Los tiempos fueron registrados **de forma aproximada por observación directa** (no con cronómetro exacto), por lo que en una prueba con más participantes, especialmente en aulas de planta alta como la de U3, algún caso podría superar por poco los 5 minutos.
   * La Métrica 2 probó el aviso **únicamente con la aplicación abierta en pantalla**. Todavía falta resolver el caso real en que el estudiante lleva el celular bloqueado en el bolsillo (mediante notificaciones *push* del navegador).

---

## 8. Estado de los Supuestos del TP1

| Supuesto del TP1 | ¿Se confirmó en TP2? | Evidencia obtenida en el relevamiento (TP2) y ratificación en campo (TP5) |
| --- | --- | --- |
| **[SUPUESTO CRÍTICO]** S1: Familiarización con la Universidad | **Confirmado** | **TP2:** Los tres usuarios encuestados manifestaron dificultades de orientación espacial al transitar por el campus.<br>**TP5:** En la prueba presencial, la mayor parte del tiempo se concentró en la caminata dentro de los edificios desconocidos y en identificar cambios de piso (como U3 buscando un aula de 1.° piso en planta baja). |
| S2: Información sobre aulas | **Confirmado** | **TP2:** U2 y U3 confirmaron haber tenido dificultades ante cambios o reasignaciones de último momento, debiendo destinar tiempo extra a buscarlas.<br>**TP5:** El buscador por materia/comisión permitió identificar el aula asignada en menos de un minuto cuando se usó como punto de entrada. |
| S3: Mapa actual de la Universidad | **Confirmado** | **TP2:** El 100% de los usuarios evaluó la señalización física como insuficiente, confusa o regular, y U2 solicitó un mapa en cada departamento.<br>**TP5:** Los tres usuarios lograron llegar a la puerta sin ayuda gracias al plano por departamento, aunque señalaron que falta indicar puertas de ingreso y escaleras. |
| S4: Medios informales actuales | **Confirmado** | **TP2:** Ante la falta de información oficial, los usuarios recurren al personal de seguridad, compañeros o grupos de WhatsApp.<br>**TP5:** Ninguno de los 3 participantes necesitó preguntar a terceros durante la prueba; además, U2 y U3 usaron espontáneamente el botón *"Compartir"* de la app para enviar el link directo del aula a sus grupos de WhatsApp. |
| S5: Cambios y reasignaciones | **Confirmado** | **TP2:** Se comprobó que enterarse tarde genera pérdidas de tiempo (5 a 15 min), llegadas tarde y niveles de estrés.<br>**TP5:** Los 3 usuarios identificaron el aula nueva en menos de 1 minuto con la app abierta, validando la necesidad de complementar el aviso emergente con el cartel fijo en la ficha del aula. |
| S6: Transporte público | **Sin evidencia directa** | Los usuarios resuelven esto mediante herramientas externas como Google Maps, sin manifestar demanda activa de integración en esta etapa. |
| S7: Solicitud de cambios de aula (Profesores) | **Sin evidencia (Fuera del alcance)** | No se realizaron mediciones directas sobre este grupo en el relevamiento enfocado en estudiantes. |
| S8: Gestión administrativa de aulas | **Sin evidencia (Fuera del alcance)** | Premisa de gestión interna que no contó con datos empíricos en esta instancia estudiantil. |

---

## 9. Scope del MVP
 
El MVP es lo mínimo necesario para testear la hipótesis de valor, no el producto completo.
 
| Incluido en el MVP | Para qué parte de la hipótesis sirve |
| --- | --- |
| Visualización del plano general del campus, buscador por materia/comisión/aula y ubicación del aula dentro del mapa del departamento (navegación por niveles predio → planta → aula). | Ataca el componente más frecuente y mejor confirmado de la hipótesis: la desorientación al buscar aulas desconocidas (supuesto crítico del TP1). En la Q5 del TP2, 2 de los 3 usuarios calificaron la orientación general como difícil; es el problema de fondo que el mapa por niveles y el buscador buscan resolver, independientemente de si hubo o no una reasignación. |
| Sistema de notificaciones ante cambios de última hora (aviso emergente en vivo y cartel fijo de traslado dentro de la app). | Relacionado directamente al segundo componente de la propuesta de valor definida ("un sistema de notificaciones automáticas ante reasignaciones") y su criterio de validación. Es además la funcionalidad que 2 de los 3 usuarios relevados (U2 y U3) priorizaron por sobre el mapa en la pregunta 29 del TP2. |
| Botón *"Compartir"* enlace directo del aula (`?aula=X&ed=Y`). | Funcionalidad ya presente en el MVP que durante la prueba del TP5 emergió como un recurso muy valorado por U2 y U3 para pasar la ubicación exacta de un aula por WhatsApp sin escribir indicaciones. |

<br>
 
| Excluido del MVP | Por qué se excluye |
| --- | --- |
| Integración con los sistemas administrativos internos de la Universidad (el software que usa el personal para gestionar aulas). | El circuito de registro de cambios se construye dentro de la propia interfaz de WayFinder, sin conectarse a los sistemas que la Universidad ya usa internamente.<br>Conseguir ese acceso está fuera de nuestro alcance y no aporta a validar si el estudiante encuentra valor en recibir el aviso. |
| Integración con la API de SIU-Guaraní, posicionamiento interior en tiempo real (geofencing dentro de los edificios) y pathfinding paso a paso. | La validación se centra en la utilidad cognitiva de la ubicación visualizada, no en la validación de identidad ni en el cálculo de rutas interiores paso a paso, que requeriría modelar todos los pasillos como un grafo navegable. |
| Consulta de transporte público, horarios de instalaciones no académicas (comedor, enfermería, etc.). | El TP2 no encontró evidencia de que incluirlo ayude a confirmar o refutar la hipótesis en esta etapa: los usuarios ya cubren transporte por otros medios, sin manifestar demanda activa de integrarlo.<br>No significa que no sea importante, simplemente no forma parte del núcleo de los problemas de los que este MVP necesita aprender. |
| Vista diferenciada completa para Profesores y Administrativos (login, permisos y pantallas propias por rol). | El MVP solo necesita validar el problema del usuario primario (estudiantes). El registro de cambios de aula durante la prueba lo resuelve un integrante del equipo desde el panel de gestión conectado a Supabase (ver punto 10).<br>Además, los supuestos sobre profesores y administrativos (S7 y S8) quedaron "sin evidencia / fuera de alcance" en el TP2. |

> **Sobre orientación interior y referencias de acceso:** A partir de la prueba del TP5, antes de abordar un sistema complejo de *pathfinding*, se prioriza incorporar referencias explícitas de piso y punto de acceso (puerta o escalera) en la ficha del aula y en el plano del departamento.

---
 
## 10. Qué se construye y qué se simula
 
| Elemento | Se construye | Se simula / se resuelve a mano | Por qué |
| :---: | :---: | :---: | :--- |
| Interfaz de usuario (Frontend) | ✓ | | Componente de software propio del equipo, construido de verdad en Netlify para garantizar una experiencia interactiva real desde el celular. |
| Base de datos de aulas, comisiones y ubicaciones | ✓ (esquema y consulta en Supabase) | ✓ (carga de datos) | Se precargan las comisiones, aulas y planos en Supabase, ya que el objetivo es evaluar la utilidad de la ubicación y no automatizar la ingesta de bases institucionales internas. |
| Resaltado de ubicación en el mapa | ✓ | | Se implementa la lógica visual para ubicar el departamento en el campus y resaltar el aula seleccionada y su estado dentro del plano del sector. |
| Aviso de reasignación de aula | ✓<br>(aviso emergente + cartel fijo que ve el estudiante) | ✓<br>(carga manual del cambio) | La app escucha cambios en tiempo real desde Supabase y muestra tanto el aviso emergente como el cartel de traslado en la ficha del aula. Lo que se resuelve a mano es disparar el cambio desde el panel `?admin`, ya que no existe integración con el sistema interno de bedelía. |
| Validación de identidad del estudiante (SIU-Guaraní) | ✗ | ✗ | No aporta a testear la hipótesis; se excluye del MVP sin necesidad de simularla. |
 
---
 
## 11. Flujo principal del MVP (con las mejoras de usabilidad incorporadas tras el TP4)
 
1. **Apertura de la aplicación:** El estudiante ingresa desde su celular a la plataforma web alojada en Netlify ([https://taiko-unlam.netlify.app/](https://taiko-unlam.netlify.app/)), que selecciona automáticamente el día actual y el turno en curso.
2. **Exploración o búsqueda:** El usuario busca directamente desde el primer carácter el aula, materia o código de comisión que necesita (o explora el mapa general del predio por departamento).
3. **Ubicación en contexto (predio → departamento → aula):** Al elegir un resultado del buscador, la cámara primero centra el edificio en el mapa general del campus durante un instante y luego abre el plano interno del sector con el aula resaltada.
4. **Visualización del estado y de eventuales cambios:** El sistema muestra la ficha del aula con la materia, comisión, horario, estado actual y, si hubo una reasignación, tanto el aviso emergente en vivo como el cartel fijo *"Esta clase se mudó"* con acceso directo al aula nueva.
5. **Obtención del valor (y difusión opcional):** El estudiante identifica dónde queda el aula, se desplaza de forma autónoma sin pedir ayuda y, si lo necesita, comparte el enlace directo del aula con sus compañeros por WhatsApp.

---
 
## 12. Atributos de usabilidad priorizados
 
* **Facilidad de aprendizaje:** Prioritario porque los ingresantes se enfrentan por primera vez a la distribución física de la UNLaM y poseen nula familiaridad con cuerpos, alas y pisos. La interfaz debe ser intuitiva de forma inmediata, sin curva de aprendizaje previa ni manuales de uso.
* **Eficiencia:** Se prioriza porque los estudiantes relevados manifestaron transitar bajo situaciones de apuro y con tiempos acotados entre clases o antes de rendir un examen. El sistema debe resolver la búsqueda de una ubicación en pocos pasos, minimizando el tiempo de interacción con el celular mientras caminan por el predio.

---

## 13. Lo Aprendido en la Prueba del TP5 (Las Dos Capas)

### **A. Capa de usabilidad (¿El MVP funciona bien?)**
* **Lo que funcionó bien:** El buscador con autocompletado desde el primer carácter y la transición visual que primero ubica el edificio en el campus y luego abre el plano del departamento con el aula resaltada permitieron que quienes usaron el buscador de entrada (**U1** y **U3**) resolvieran la parte digital en menos de un minuto. Asimismo, la combinación de dos avisos para los cambios de aula demostró ser clave: el aviso emergente sirvió para quienes miraban la pantalla (**U1** y **U2**), y el cartel fijo en la ficha del aula original salvó el flujo de **U3** cuando no vio el aviso emergente por ir bajando una escalera.
* **Fricciones de interfaz y de orientación detectadas en el campus:**
  1. **Orientación física dentro del edificio y cambios de piso (U1 y U3):** El plano muestra dónde está el aula dentro del sector, pero no indica por qué puerta se entra (duda de **U1** en Económicas, `E02`) ni resalta en la ficha del aula cuando hay que subir al primer piso (**U3** caminó por la planta baja de Humanidades buscando el aula 142 antes de notar en el mapa general que Ingeniería `135 a 143` está en planta alta, `E09`).
  2. **Duración del aviso emergente en movimiento (U2 y U3):** El aviso emergente dura 9 segundos y se cierra solo; **U2** llegó a tocarlo justo antes de que desapareciera (`E07`) y **U3** no lo vio porque bajó el celular para mirar los escalones (`E10`).
  3. **Visibilidad del selector de día en celular y entrada por lista de departamentos (U1 y U2):** En la portada móvil la barra de días está arriba con abreviaturas (`LUN, MAR...`), pero **U1** la pasó por alto buscando un botón que dijera *"Martes"* (`E04`); además, esa barra no aparece en la vista del mapa, por lo que **U2** buscó el cambio de día en los íconos superiores del mapa y dentro de *Filtros* (donde no está) antes de volver a la portada. Por otro lado, **U2** en la Tarea 1 entró primero por la lista de departamentos e intentó buscar su comisión tocando aulas en el plano antes de usar el buscador (`E05`, `E06`).
* **Hallazgo inesperado positivo: uso del botón *"Compartir"* (U2 y U3):** En la Tarea 3, **U2** (Aula 132 de Humanidades, `E08`) y **U3** (Aula 310 de Económicas, `E11`) tocaron por iniciativa propia el botón **"Compartir"** de la ficha del aula (`?aula=132&ed=humanidades`), pensando en mandar el link directo al grupo de WhatsApp de la comisión en lugar de escribir indicaciones. La prueba también permitió detectar dos mejoras pendientes sobre esta función: hacer que el enlace directo funcione al abrirse desde una computadora de escritorio (hoy solo abre el aula en celular) e incluir el día consultado en la URL (hoy solo pasa el aula y el departamento, mostrando por defecto el día en que se abre el link).

### **B. Capa de negocio (¿La hipótesis de valor se sostiene?)**
* La hipótesis de valor **se sostiene**: los 3 usuarios del segmento primario llegaron a la puerta de aulas en edificios que no frecuentaban en **menos de 5 minutos y sin pedir ayuda**, y los 3 se enteraron de la reasignación de aula en **menos de 1 minuto** con la app abierta. Centralizar la búsqueda por materia/comisión con la ubicación en el mapa y el aviso de traslado resuelve el problema relevado en el TP1 y el TP2.

---

## 14. Decisión: Perseverar y Próximos Pasos Priorizados

A partir de los resultados de la prueba, el equipo decide **PERSEVERAR** con la hipótesis de valor y con el enfoque actual del producto (no se pivota ni de problema, ni de segmento primario, ni de propuesta central). Las dificultades observadas tienen soluciones concretas de diseño e implementación que ordenan las siguientes prioridades de construcción:

1. **Aviso de cambio persistente (sin cierre automático a los 9 segundos) y notificaciones Web Push para los inscriptos en esa materia y comisión:**
   * *Justificación:* Para que el estudiante que va caminando no pierda el aviso emergente por bajar la vista unos segundos (como les pasó a **U2** en `E07` y a **U3** en `E10`), y para cubrir el caso real en que lleva el celular bloqueado en el bolsillo antes de entrar a cursar.
2. **Referencia explícita de piso y punto de acceso en el encabezado de la ficha del aula (*"1.° piso · Subir por la escalera central"*, *"Acceso por la puerta lateral"*):**
   * *Justificación:* Porque la mayor parte del tiempo de la Tarea 1 se fue caminando dentro del edificio una vez que el usuario ya sabía el número de aula (duda de **U1** al entrar a Económicas en `E02` y recorrido de **U3** en planta baja buscando el aula 142 de Ingeniería en `E09`).
3. **Selector de día más reconocible en el celular y disponible desde la vista del mapa (junto con el ajuste del enlace de *"Compartir"*):**
   * *Justificación:* Para resolver la dificultad observada en la Tarea 3, donde **U1** no reconoció la barra de días abreviados de la portada (`E04`) y **U2** buscó el selector de día dentro de la vista del mapa y en *Filtros*, además de completar el enlace del botón *"Compartir"* para que incluya el día consultado en la URL y funcione también en escritorio.

---

## 15. Arquitectura actual del MVP (TP6)

> Diagrama: [`UNLaM Wayfinder - arquitectura-mvp.svg`](./diseño/wireframe/UNLaM%20Wayfinder%20-%20arquitectura-mvp.svg)

El MVP es una sola página web (HTML, CSS y JavaScript en un archivo) que corre entera en el navegador, sin servidor propio. Sus partes:

* **Cliente:** vista celular y vista escritorio, mapa del campus y planos en SVG embebidos, buscador global (aulas, laboratorios, espacios, materias, comisiones y servicios), ficha del aula con el enlace *"Compartir"*, aviso de cambio en vivo y un estado en memoria con la ocupación por aula, día y franja. Los edificios, planos y horarios de servicios están escritos en el código, por lo que el mapa sigue funcionando aunque la base no responda.
* **Entrega:** Netlify sirve el archivo por HTTPS; la biblioteca supabase-js llega desde jsDelivr y las tipografías desde Google Fonts.
* **Backend (Supabase):** PostgreSQL con las tablas `ocupacion_aulas`, `ocupacion_deportes`, `comisiones_siu`, `cambios_aula` y `administrativos`; API REST con lectura pública y escritura protegida por RLS solo para administrativos activos; Auth con email y contraseña solo para administrativos; y Realtime, que avisa cada cambio a los navegadores con la app abierta.
* **Circuito del cambio de aula:** un integrante del equipo registra la reasignación en el panel `?admin`, el panel la escribe en `ocupacion_aulas`, un disparador de la base guarda el historial en `cambios_aula` y Realtime avisa a cada app abierta, que recarga su estado y muestra el aviso emergente y el cartel fijo *"Esta clase se mudó"*.
* **Lo simulado o manual:** la detección del cambio (la carga el equipo), los horarios del SIU-Guaraní (extraídos una vez y cargados con scripts SQL) y el aula de cada comisión, que es una asignación de ejemplo porque el SIU no publica el aula.
* **Lo oculto o no construido:** notificaciones push, cuentas de estudiantes, avisos filtrados por comisión, integración en vivo con el SIU, y el GPS en vivo y *"Tus aulas"*, que están en el código pero ocultos.

### Decisiones heredadas que se revisan

| Decisión | ¿Quién la tomó? | ¿Se sostiene? |
| --- | --- | --- |
| Ante cualquier cambio, cada app abierta vuelve a descargar completas las tablas de ocupación (más de 2.000 filas, en pedidos de a 1.000). Como el panel escribe dos veces por reasignación, cada cambio provoca dos recargas. | Nadie: salió de reutilizar la función de carga inicial para cada aviso en vivo. | No. Alcanzó para la prueba, pero con muchos usuarios multiplica las descargas sobre datos móviles. Hay que aplicar solo la fila que llega en el aviso. |
| El aviso llega por Realtime solo a la app abierta, se cierra a los 9 segundos y le llega a todos, no solo a esa comisión. | La herramienta que generó el código. | En parte. Se mantienen el canal en vivo y el cartel fijo de la ficha; no el cierre automático ni la dependencia de la app abierta (U2 en `E07`, U3 en `E10`). |

---

## 16. La gran visión: arquitectura del producto completo

> Diagrama: [`UNLaM Wayfinder - arquitectura-producto-completo.svg`](./diseño/wireframe/UNLaM%20Wayfinder%20-%20arquitectura-producto-completo.svg)

El producto completo es la misma app web, con tres vistas según el rol (Estudiante, Profesor y Administrativo), apoyada en Supabase y conectada a los sistemas de la UNLaM. La diferencia de fondo con el MVP es que la app **sabe quién es el usuario**: eso habilita los avisos dirigidos, "Mis materias" y la verificación del alumno.

| Componente | Qué hace en la visión | Estado en el MVP |
| --- | --- | --- |
| Mapa, planos, buscador y disponibilidad por día y franja | Ubicar aulas e instalaciones, con materia y comisión. | Cubierto. |
| Aviso de cambio de aula | Avisar a los inscriptos en esa materia y comisión, con la app abierta o cerrada. | En parte: solo con la app abierta y le llega a todos. |
| Mis materias y avisos | Cuenta vinculada al SIU con sus comisiones y la opción de desactivar avisos. | No existe. |
| Mesas de examen | Aula confirmada de cada mesa y sus cambios. | No existe. |
| Ruta hasta el aula | Camino por pasillos y escaleras desde la entrada del campus. | En parte: el GPS existe, calibrado y oculto; falta el grafo. |
| Transporte público | Paradas, líneas y próximo arribo cerca del campus, con una API externa. | No existe. |
| Vistas Profesor y Administrativo | Pedir cambios de aula; aprobarlos y publicarlos. | En parte: el panel `?admin` lo usa el equipo. |
| Auth y roles | Tres roles y alumno verificado por el SIU. | En parte: solo administrativos. |
| Integración UNLaM | Traer del SIU y de los datos institucionales comisiones, inscripciones, carreras y horarios. | En parte: horarios extraídos una vez. |
| Notificador | Ante un cambio, buscar a los inscriptos que no desactivaron el aviso y enviarles el push. | No existe. |

### Tecnologías que agrega la visión

* **Web Push con claves VAPID y service worker:** entrega el aviso con la app cerrada, que es el caso real del TP2 (el celular en el bolsillo). Se elige frente a una app nativa porque el producto sigue siendo una sola web mantenida por un equipo de estudiantes, sin publicar en tiendas.
* **Supabase Edge Functions:** la única pieza que corre en un servidor. Se dispara con un Database Webhook al insertarse una fila en `cambios_aula`, busca a los inscriptos con el aviso activado y envía el push con la clave privada. Vive en el mismo proyecto de Supabase que ya usamos.
* **Grafo de pasillos y escaleras en JSON, con búsqueda A\* en el navegador:** la ruta que prometía el TP1, calculada sobre los planos. Atiende la fricción más larga de la Métrica 1 (U3 buscando el aula 142 en planta baja, U1 dudando por qué puerta entrar).

### El componente más riesgoso

El aviso de cambio en vivo: fue lo único que estuvo cerca de fallar en el TP5 y es lo que peor escala. Hoy le llega a todos, depende de que la app esté abierta, recarga todo ante cada cambio, usa un mecanismo de Realtime que la documentación de Supabase desaconseja a escala y no se pone al día si se corta la conexión. Por eso la visión lo reemplaza por push dirigido a los inscriptos y deja Realtime solo para actualizar la app abierta.

---

## 17. Restricciones técnicas del contexto

* **Dispositivo y conectividad:** el uso es en el celular, caminando, con datos móviles o el Wi-Fi del campus (TP2). La app tiene que ser liviana y no descargar todo el estado ante cada cambio. Al apagarse la pantalla o pasar del Wi-Fi a los datos, la conexión en vivo se corta, y la app tiene que ponerse al día al volver.
* **Plataforma:** el alcance es Android. En iPhone, Web Push exige instalar la app en la pantalla de inicio, así que queda fuera.
* **Precisión del GPS en el campus:** con la calibración actual, el error típico es de 7 m y llega a 13 m en el 10 % de los puntos. No distingue un pasillo de otro ni un piso de otro, por lo que solo sirve para ubicar la entrada del campus; la ruta interior se resuelve con el grafo.
* **Equipo y hosting:** el producto lo mantiene un equipo de estudiantes, como una sola web en hosting estático y sin servidor propio. La única lógica de servidor es la Edge Function del notificador, que existe porque la clave privada VAPID no puede estar en el HTML, que es público.
* **Acceso a datos institucionales:** no hay acceso a los sistemas internos de bedelía ni a la API del SIU-Guaraní, y el SIU no publica el aula de cada comisión. Hoy los horarios se extrajeron una vez y los cambios los carga el equipo a mano. Los avisos dirigidos y la verificación del alumno dependen de conseguir ese acceso.
* **Escala de Supabase:** el segmento es de 30.000 a 35.000 estudiantes. Realtime admite 200 conexiones simultáneas en el plan gratuito, 500 en el Pro y 10.000 en el Pro sin tope de gasto. La suscripción directa a la tabla revisa los permisos de cada suscriptor en un solo hilo, así que la carga crece con los cambios multiplicados por los celulares conectados; la documentación recomienda Broadcast para escalar. Además, cada respuesta trae como máximo 1.000 filas, por lo que las lecturas grandes tienen que ser paginadas.
* **Disponibilidad:** el mapa, los planos y el buscador trabajan con datos del código y siguen funcionando aunque Supabase no responda. La ruta respeta la misma regla, y por eso se calcula en el navegador y no en la base.
* **Seguridad:** la lectura es pública con la clave anónima; la escritura queda limitada por RLS a los administrativos activos, y el alta libre de cuentas tiene que estar deshabilitada. Con cuentas de estudiantes, sus inscripciones y suscripciones push solo deben ser visibles para cada uno.
