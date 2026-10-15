# MigraRing Bio — LATAMinds

Prototipo navegable de interfaz para pacientes. Primera iteración con datos simulados.

## Cómo usar

1. Abrí `index.html` con Chrome, Edge, Firefox o Safari.
2. Navegá por Resumen, Monitoreo, Episodios, Medicamentos, Informes y Configuración.
3. Agregá valores fisiológicos, episodios y medicamentos; los datos se conservan usando `localStorage` del navegador.
4. Desde Informes, exportá CSV o usá **Imprimir / guardar PDF** desde el navegador. Podés exportar un respaldo JSON desde Configuración.

No hace falta instalar dependencias, ejecutar un servidor ni conectarse a internet. Se recomienda abrirlo en un navegador actualizado. Para integraciones futuras con hardware Bluetooth, sí hará falta un contexto seguro (HTTPS o localhost) y desarrollo adicional de la conexión BLE.

## Funciones del prototipo

- Dashboard de riesgo **simulado**, indicadores, evolución de biomarcadores y actividad reciente.
- Monitoreo con gráficos y carga manual de frecuencia cardíaca, VFC, temperatura, sueño y actividad.
- Simulación de alertas predictivas y registro del resultado/seguimiento de las recomendaciones.
- Diario de episodios: fecha, intensidad, duración, síntomas, posibles desencadenantes y medicación.
- Gestión de medicamentos y registro de tomas sin recomendaciones de dosis.
- Informes con estadísticas, impresión/PDF del navegador y descarga CSV.
- Ajustes de preferencias y exportación de respaldo JSON.
- Diseño adaptable a móvil, tablet y escritorio.

## Aviso importante

Toda lectura inicial y alerta es **inventada para demostrar la interfaz**. El cálculo de riesgo mostrado no es un algoritmo médico, ni debe interpretarse como predicción clínica. No existe conexión real con el anillo, backend, IA ni sincronización médica. Los datos de usuario se guardan **solo en el almacenamiento local del navegador**, que **no es adecuado para almacenar datos médicos sensibles en producción**. La aplicación requeriría arquitectura segura, consentimiento, autenticación, validación clínica y cumplimiento normativo antes de uso real.


## Iteración 2: MigraRing Bio y catálogo de biomarcadores

La pestaña **Monitoreo** ahora permite abrir un explorador interactivo con **39 parámetros**, agrupados en 7 categorías: cardiovasculares (6), térmicos (3), sistema nervioso autónomo (5), movimiento y sueño (7), bioquímicos experimentales (7), mecánicos (3) e indicadores IA (8).

Podés buscar, filtrar, inspeccionar tendencias y registrar manualmente un valor con fecha, unidad, nota y origen. Las variables experimentales solo pueden registrarse como resultado de una fuente externa o laboratorio; los indicadores de IA son de solo lectura. Las nuevas muestras de prueba se rotulan como **Demostración**. Se mantiene compatibilidad con el almacenamiento local de la iteración anterior.

La exportación CSV de **Informes** agrega ahora una sección de biomarcadores con sus valores, unidades y procedencias. En **Informes** también se incluye una tarjeta de cobertura del catálogo.

**Advertencia:** la lista representa una propuesta de capacidades, NO mediciones verificadas del anillo. Sensores electroquímicos, SpO₂, HRV derivada, CGRP, análisis de riesgos y correlaciones exigen viabilidad de hardware, protocolos, validación y calidad de los datos. El sistema no aprende ni hace predicciones clínicas.

## Iteración 3: requisitos de la matriz de necesidades y riesgos

Se cotejaron los IDs 1–13 de la matriz entregada.

- **Modo prodrómico / calma** (ID 7): botón rápido en cabecera y configuración persistente; paleta oscura atenuada, menos estímulos, tipografía y botones mayores, respeto de reducción de movimiento. Prototipo: cumplimiento WCAG AA y puntuación SUS no medidos.
- **Alertas (ID 1–4)**: simulación de una ventana de 60 minutos alineada como *demostración* con la anticipación objetivo de 30–60 minutos. No hay sensibilidad 85 %, especificidad 80 %, ni modelo entrenado. El circuito de respuesta y el registro de episodios sin alerta permanecen. Vibración/tono de navegador optativos, sin conexión con el anillo.
- **Seguimiento (ID 5–6, 8, 11)**: objetivos de muestreo, buffer 48 h, batería 5 días, carga 45 min, IP68/5 ATM y biocompatibilidad visibles explícitamente como *pendientes de validar*. No se presentan falsas lecturas de batería ni conectividad.
- **Informes (ID 9 y 12)**: período de 7/30/90 días o fechas personalizadas, filtros de síntomas y biomarcadores, gráfica de densidad semanal, tabla de episodios y exportación CSV filtrada. PDF via impresión del navegador. HL7 FHIR no implementado.
- **Privacidad (ID 10)**: consentimiento explícito requerido cada vez que se exporta CSV, JSON o PDF; no existe intercambio con terceros. LocalStorage **no está cifrado ni apto para historia clínica real**. No alegar GDPR/HIPAA/E2EE.
- **Información (ID 13)**: nueva sección Aprender, con vínculos a OMS y MedlinePlus, sin noticias en tiempo real.

Las 39 métricas de la iteración 2 se conservan. Estas correcciones constituyen cambios de interfaz y flujo, no pruebas de hardware, seguridad, usabilidad o efectividad clínica.

- **Planificación (ID 2)**: agenda personal con carga, marcado y eliminación de actividades. No se replanifica automáticamente en base a una predicción no validada.
