# Evidencia TP5 — Prueba del MVP con usuarios reales

Prueba de campo ejecutada en el campus de la Universidad Nacional de La Matanza (UNLaM) con tres usuarios del segmento primario, con el mismo perfil que los usuarios **U1**, **U2** y **U3** relevados en el TP1 y el TP2.

- **Aplicación evaluada (MVP):** [https://taiko-unlam.netlify.app/](https://taiko-unlam.netlify.app/)
- **Fecha de ejecución:** 25/09/2026
- **Lugar de inicio de cada sesión:** entrada principal del campus (Av. Pres. Juan Domingo Perón 2320, San Justo).
- **Modalidad:** prueba presencial *in situ* desde el teléfono celular de cada participante, sin explicación previa de la interfaz y con observación sin asistencia del equipo.
- **Sobre los tiempos:** se tomaron por observación directa, siguiendo a cada participante y con el reloj del celular como referencia, no con un cronometraje exacto. Por eso se registran de forma aproximada. Alcanzan para contrastar cada resultado con los umbrales del Punto 1 (5 minutos y 1 minuto) y para ver en qué tramo se concentró la demora.

## Archivos de esta carpeta

1. [`tiempos_y_metricas.csv`](./tiempos_y_metricas.csv): planilla con los tiempos aproximados por tramo para la **Métrica 1** (búsqueda en la app, lectura de mapa y plano, caminata hasta la puerta), la **Métrica 2** (desde que se carga el cambio en `?admin` hasta que el usuario identifica el aula nueva) y la **Tarea 3** (consulta de otro día), contrastados con el criterio de éxito del Punto 1.
2. [`registro_fricciones_y_eventos.csv`](./registro_fricciones_y_eventos.csv): bitácora de los eventos observados durante las sesiones, clasificados en *Duda*, *Error*, *Pedido de ayuda* y *Camino distinto del esperado*.
3. [`U1_sesion_notas.md`](./U1_sesion_notas.md): registro de la sesión con **U1** (estudiante de 1.° año de Medicina): tiempos aproximados, eventos observados y respuestas a las preguntas finales.
4. [`U2_sesion_notas.md`](./U2_sesion_notas.md): registro de la sesión con **U2** (estudiante ingresante de Comunicación Social): tiempos aproximados, eventos observados y respuestas a las preguntas finales.
5. [`U3_sesion_notas.md`](./U3_sesion_notas.md): registro de la sesión con **U3** (estudiante de 2.° año de Relaciones Públicas): tiempos aproximados, eventos observados y respuestas a las preguntas finales.

## Resumen de resultados frente al criterio de éxito

| Usuario | Perfil | Métrica 1: tiempo aproximado hasta la puerta (< 5 min, sin ayuda) | Dónde se concentró el tiempo | Métrica 2: tiempo aproximado hasta saber el aula nueva (< 1 min) | Pedidos de ayuda | Resultado frente al criterio |
| :---: | :--- | :---: | :--- | :---: | :---: | :---: |
| **U1** | 1.° año de Medicina (turno mañana, datos móviles) | Entre 3 y 4 min | Búsqueda y plano en menos de un minuto; la mayor parte fue la caminata | Menos de medio minuto (por el aviso emergente) | 0 | **Cumple ambas** |
| **U2** | Ingresante de Comunicación Social (turno mañana, Wi-Fi UNLaM) | Algo más de 4 min | Algo más de un minuto en la búsqueda (entró primero por la lista de departamentos); después, la caminata | Menos de medio minuto (por el aviso emergente) | 0 | **Cumple ambas** |
| **U3** | 2.° año de Relaciones Públicas (turno noche, Wi-Fi UNLaM, apurado) | Cerca de 4 min y medio | Búsqueda muy rápida; la caminata, larga, porque buscó el aula en la planta baja | Menos de un minuto (no vio el aviso; se enteró por el cartel de la ficha) | 0 | **Cumple ambas** (Métrica 1, cerca del límite) |
| **Resultado** | **3 usuarios del segmento primario** | **3 de 3 en menos de 5 min** | **La caminata dentro del edificio fue el tramo más largo** | **3 de 3 en menos de 1 min** | **0** | **Hipótesis sostenida (al menos 2 de 3 en ambas)** |
