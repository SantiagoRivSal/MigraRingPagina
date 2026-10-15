# MigraRing Bio — comparación con matriz de necesidades y riesgos

**Base:** documento aportado «MATRIZ DE NECESIDADES, CRITERIOS DE DISPOSITIVO Y GESTIÓN DE RIESGOS» (13 ID de necesidad, dos páginas).

**Alcance:** prototipo web offline, sin hardware conectado, sin servidor de datos sanitarios ni algoritmo clínico validado.

| ID | Necesidad principal | Cambio implementado en iteración 3 | Estado / límite |
|---:|---|---|---|
| 1 | Alerta de posible migraña | Flujo de alerta simulada y respuesta posterior; se explicita el objetivo de 30–60 min | Solo interfaz; sensibilidad ≥85 % y especificidad ≥80 % **no demostradas** |
| 2 | Continuar y planificar rutina | Agenda de actividades con registro, marcado y eliminación | Planificación manual; no se reorganiza en función de supuestos pronósticos |
| 3 | Apoyo para prevención | Recomendaciones generales tras la alerta | No sustituye una pauta clínica |
| 4 | Aviso anticipado | Ventana ilustrativa de 60 min | No hay predicción real; no se garantizan 30–60 min |
| 5 | Almacenar seguimiento | Conserva 39 variables y registros de síntomas; área de metas de conectividad | Sin hardware: no hay muestreo a 60 s, buffer ≥48 h ni autonomía medida |
| 6 | Monitoreo sin acción manual | Estado explícito de anillo no conectado, carga de valores manuales | Sin BLE ni proceso automático |
| 7 | Bajo esfuerzo/uso sin estímulos | Modo prodrómico/calmo (paleta atenuada, menor animación, controles mayores); vibración y tono opcionales del navegador | No hay evaluación SUS ≥85, conformidad WCAG 2.1 AA certificada, ni alertas hápticas en anillo |
| 8 | Resistencia agua/sudor | Se muestran objetivos de IP68, ensayo independiente 5 ATM, materiales biocompatibles y control de humedad | **Hardware no validado**. IP68 y 5 ATM no son equivalentes; certificaciones no otorgadas |
| 9 | Reporte para neurólogo | Informe con evolución, conteo semanal, historial filtrado; CSV y opción de guardar PDF del navegador | HL7 FHIR aún no disponible; informe no validado clínicamente |
| 10 | Confidencialidad y autorización | Confirmación obligatoria para exportación CSV/JSON/PDF; ningún envío automático | `localStorage` sin cifrado; NO cumple aún AES-256, TLS 1.3, OAuth, GDPR/HIPAA ni E2EE |
| 11 | Autonomía/carga | Metas de autonomía ≥5 días y carga ≤45 min visibles como pendientes | No se monitorizan batería, temperatura de carga o corte térmico |
| 12 | Informe semanal/mensual por síntomas | Rangos 7/30/90 días y fechas manuales; selector de síntomas/biomarcador y densidad semanal | Exploración descriptiva, no inferencia causal |
| 13 | Avances sobre migraña | Sección Aprender con fuentes OMS/MedlinePlus y orientación para consulta | No hay buscador/feed científico ni actualización automática |

## Riesgos y decisiones de interfaz

- Los riesgos de **falsos positivos/negativos** se mitigan en esta etapa rotulando las alertas y porcentajes como ficticios. La validez del algoritmo requiere estudios y datos de verdad-terreno adecuados.
- El riesgo de **fotofobia o carga cognitiva** motiva un modo de menor estímulo. Este cambio no acredita el resultado de pruebas de accesibilidad/usabilidad.
- El riesgo de **filtración de datos** se explicita con advertencias y consentimiento antes de descarga. No cargue datos clínicos reales sensibles en un prototipo sin protección.
- La matriz mezcla requisitos de **hardware** y **software**. Se diferencian visualmente los objetivos todavía no implementados.
- La matriz de riesgo no constituye por sí sola evidencia de conformidad con ISO 14971; faltan análisis de peligros completos, verificación de mitigaciones y evaluación de riesgo residual.

## Cómo verificar

Abrir `index.html` y probar: Resumen (agenda), Monitoreo (39 parámetros), Mis episodios, Medicamentos, Informes (filtros y CSV con confirmación), Aprender y Configuración (Modo calma y requisitos de anillo). El HTML único incluido fuera del ZIP puede usarse sin archivos externos.
