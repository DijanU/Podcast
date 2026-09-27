---
title: "La Computación Paralela en el Aula y en la Profesión"
subtitle: "Plan de entrevista"
author:
  - Luis Francisco Padilla
  - Estuardo Castro
date: "26 de septiembre de 2026"
lang: es
documentclass: article
fontsize: 11pt
geometry: margin=2.5cm
toc: true
numbersections: true
colorlinks: true
---

# Objetivo de la entrevista

Mostrar cómo los conceptos del curso Computación Paralela y Distribuida se usan en la práctica profesional de un exalumno de la Universidad del Valle de Guatemala que trabaja en *machine learning*. Queremos que el oyente vea la relación entre la teoría (hilos, sincronización, condiciones de carrera, ley de Amdahl, memoria compartida y paso de mensajes) y las decisiones que un ingeniero toma en proyectos reales con restricciones de tiempo, costo y negocio.

# Perfil del entrevistado

| Campo | Detalle |
|---|---|
| Nombre | Daniel Valdez |
| Formación | Ingeniería en Ciencias de la Computación y Tecnologías de la Información, UVG |
| Puesto actual | Machine Learning Engineer en Improgress (Guatemala) |
| Área de trabajo | Automatización, productos para clientes y puesta en producción de modelos de IA |
| Por qué lo elegimos | Aplica paralelismo y computación distribuida para servir modelos, cumplir requisitos de latencia y escalar sistemas |

# Estructura del episodio

La duración objetivo es de 30 a 45 minutos.

| Bloque | Duración estimada | Responsable | Contenido |
|---|---|---|---|
| 1. Introducción | 2 min | Estuardo | Bienvenida, tema del episodio y presentación de los anfitriones |
| 2. Presentación del invitado | 5 min | Luis y el invitado | Trayectoria y rol actual |
| 3. Aplicaciones del paralelismo | 12 min | Ambos | Ejemplos concretos en su trabajo |
| 4. Herramientas y tecnologías | 8 min | Estuardo | Librerías, frameworks y técnicas |
| 5. Desafíos y beneficios | 8 min | Luis | Límites, costos y decisiones de diseño |
| 6. Tendencias futuras | 6 min | Estuardo | Hacia dónde va el paralelismo |
| 7. Cierre | 2 min | Luis y Estuardo | Agradecimientos y mensaje final |

# Preguntas planificadas

Cada bloque tiene preguntas principales, puntos clave que esperamos cubrir y preguntas de seguimiento por si la respuesta necesita más detalle.

## Bloque 1: Introducción del entrevistado y su profesión

**P1. ¿Quién eres y a qué te dedicas actualmente?**

Puntos clave esperados:

- Formación en la UVG y año de graduación.
- Empresa y puesto actual.
- Tipo de proyectos en los que participa.

**P2. ¿Qué hace un Machine Learning Engineer y en qué se diferencia de un *data scientist* o de un desarrollador *backend*?**

Puntos clave esperados:

- El ciclo de vida de un modelo: diseño, puesta en producción, consumo y mantenimiento.
- El ML Engineer como puente entre quien diseña el modelo y quien lo consume.
- Las ventajas de tener un rol especializado en lugar de tratar el modelo como un *endpoint* más.

Seguimiento:

- ¿Qué problemas aparecen cuando un equipo no tiene esta figura y el modelo llega "en crudo" al *backend*?
- ¿Qué métricas vigilas? ¿En qué se diferencian las métricas de un sistema de las de un modelo?

## Bloque 2: Aplicaciones de la computación paralela en su campo

**P3. ¿En qué momentos de tu trabajo el paralelismo o la computación distribuida te facilitan la vida?**

Puntos clave esperados:

- Requisitos de latencia: modelos que responden en milisegundos frente a procesos que tardan minutos.
- Tareas largas que no deben bloquear el hilo principal de una API.
- Colas de tareas y *workers* en segundo plano.
- *Pipelines* de limpieza y procesamiento de datos.

Seguimiento:

- ¿Cómo evitas que una tarea pesada congele un servicio como FastAPI?
- ¿Tienes un ejemplo concreto de un proyecto donde paralelizar haya cambiado el resultado?

**P4. ¿Qué técnicas usas para que los procesos corran lo más rápido posible y con el menor *delay*?**

Puntos clave esperados:

- Por qué no basta con agregar más hilos.
- El *overhead* y el consumo de recursos por hilo.
- La relación con la **ley de Amdahl**: la parte secuencial limita la aceleración.

Seguimiento:

- ¿Cómo detectas que llegaste al punto en que agregar hilos ya no ayuda?

**P5. En demos y pruebas de concepto, ¿la optimización es opcional? ¿Alguna vez la paralelización fue lo que le dio valor al producto?**

Puntos clave esperados:

- Qué prioriza una demo frente a un sistema en producción.
- Ejemplos de sistemas donde la latencia es crítica, como el *streaming*.
- Casos en que optimizar desde el inicio ahorra tiempo de desarrollo.
- Diseño de arquitectura y topología para producción.

## Bloque 3: Herramientas y tecnologías paralelas

**P6. Además de PyTorch, ¿qué librerías o tecnologías usas para paralelizar el manejo de datos?**

Puntos clave esperados:

- Hilos de Python, subprocesos y Pthreads en C.
- Colas de trabajo y *thread pools* con asignación dinámica.
- Semáforos y otros mecanismos de sincronización.
- SDKs específicos del dominio, como los de cámaras.

Seguimiento:

- ¿Tienes un proyecto actual que ilustre estas herramientas? ¿Cómo lo vas a escalar?
- ¿Cómo evitas las condiciones de carrera cuando varios hilos procesan fuentes de datos distintas?
- ¿Usas herramientas como OpenMP, CUDA o MPI, o frameworks distribuidos en la nube?

## Bloque 4: Desafíos y beneficios

**P7. ¿Cuáles son los principales desafíos de llevar el paralelismo a un sistema real?**

Puntos clave esperados:

- Condiciones de carrera, memoria compartida y paso de mensajes.
- El costo económico de una mala decisión, como el tiempo de servidor facturado en AWS.
- El balance entre latencia, costo, complejidad y funcionalidad.

**P8. ¿Cómo justificas una decisión de arquitectura paralela ante personas no técnicas?**

Puntos clave esperados:

- Decisiones respaldadas con datos, no con la opinión de una herramienta de IA.
- Explicar los *trade-offs* en términos de negocio: si quieres X, sacrificas B.
- Las reglas del negocio como guía del diseño.
- Criterios claros para saber cuándo el trabajo está terminado.

Seguimiento:

- ¿Tienes un ejemplo de cliente en que tuviste que explicar este tipo de *trade-off*?

## Bloque 5: Tendencias futuras

**P9. ¿Cómo ves el futuro del paralelismo y del *machine learning*? ¿Qué nos espera a quienes estamos por graduarnos?**

Puntos clave esperados:

- La vigencia del paralelismo como técnica de optimización.
- Planificación y asignación dinámica de tareas asistida por IA.
- La computación cuántica y su impacto en la forma de diseñar sistemas.
- Qué habilidades conviene desarrollar desde ahora.

Seguimiento:

- ¿Crees que una IA podría encargarse de balancear cargas y reducir condiciones de carrera?
- Si la computación cuántica llega al mercado, ¿qué cambiaría en nuestro trabajo como ingenieros?

## Cierre

**P10. ¿Algún mensaje final para quienes nos escuchan?**

# Preguntas de reserva

Estas preguntas se usan si sobra tiempo o si algún bloque se agota antes de lo previsto:

1. ¿Qué tema del curso de Computación Paralela y Distribuida te ha servido más en tu trabajo?
2. ¿Usas GPU en tus proyectos? ¿Cuándo conviene entrenar o hacer inferencia en GPU frente a CPU?
3. ¿Qué diferencia práctica ves entre usar hilos y procesos en Python, considerando el GIL?
4. ¿Qué consejo le darías a un estudiante que quiere especializarse en MLOps o *machine learning engineering*?
5. ¿Qué recurso (libro, curso o documentación) recomendarías para profundizar en paralelismo?

# Cobertura de los temas requeridos

| Tema requerido por la rúbrica | Preguntas que lo cubren |
|---|---|
| Introducción del entrevistado y su profesión | P1, P2 |
| Ejemplos de aplicación de la computación paralela | P3, P4, P5 |
| Herramientas y tecnologías paralelas | P6 |
| Desafíos y beneficios | P4, P5, P7, P8 |
| Tendencias futuras | P9 |

# Resumen de los puntos clave que esperamos cubrir

- **Rol profesional**: el ML Engineer como puente entre el diseño del modelo y su consumo en producción.
- **Métricas**: la diferencia entre métricas del sistema (latencia, carga, tráfico) y métricas del modelo (calidad de las predicciones y KPIs de negocio).
- **Aplicación práctica**: colas de tareas, *workers* y ejecución en segundo plano para no bloquear servicios.
- **Límites teóricos**: la ley de Amdahl y el *overhead* de crear hilos sin necesidad.
- **Sincronización**: semáforos para prevenir condiciones de carrera.
- **Caso real**: escalar un sistema de visión por computadora de 5 a 50 cámaras sin perder latencia.
- **Negocio**: decisiones técnicas fundamentadas y alineadas con las reglas del negocio.
- **Futuro**: asignación dinámica de tareas con IA y el impacto de la computación cuántica.

# Logística de grabación

| Aspecto | Plan |
|---|---|
| Modalidad | Videollamada con grabación local de video y transcripción automática |
| Grabación | OBS en la computadora de Estuardo |
| Prueba de audio | Revisar eco y niveles con el invitado antes de empezar |
| Edición | Recortar la charla previa a la introducción de Estuardo y todo lo que sigue a la frase final del invitado, eliminar pausas y ruido, normalizar niveles y agregar música de entrada y salida |
| Respaldo | Guardar la transcripción de la llamada para las notas del show |
