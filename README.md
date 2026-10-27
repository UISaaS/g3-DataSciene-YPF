Análisis de producción mensual de pozos de YPF en Vaca Muerta
Proyecto grupal de Data Science — Fundación YPF  
Estado: trabajo en elaboración
Este proyecto explora cómo varía a lo largo del tiempo la producción mensual de los pozos no convencionales de YPF en Vaca Muerta y qué diferencias descriptivas se observan entre áreas y yacimientos.
> Esta es una etapa de análisis exploratorio y desarrollo. Los resultados son descriptivos: las diferencias observadas no permiten, por sí solas, identificar causas.
Pregunta de análisis
¿Cómo varía la producción mensual de petróleo de los pozos no convencionales de YPF en Vaca Muerta, y qué diferencias se observan entre áreas y yacimientos al considerar también los meses registrados sin actividad efectiva?
Como preguntas complementarias se exploran la producción total y por pozo, las diferencias entre meses con y sin actividad efectiva y la evolución de petróleo, gas y agua por separado.
Datos y alcance
Se integran dos fuentes públicas de la Secretaría de Energía de la Nación:
Capítulo IV — Listado de pozos: información técnica y descriptiva de los pozos.
Producción mensual de pozos de gas y petróleo no convencional: registros mensuales de producción y tiempo efectivo.
La relación entre ambas fuentes se realiza mediante el identificador del pozo (`idpozo`). El universo de trabajo se limita a pozos operados por YPF, no convencionales, asociados a Vaca Muerta y presentes en ambos conjuntos de datos. No representa a todas las operadoras de la formación ni al grupo económico completo de YPF.
En el corte utilizado actualmente por la notebook, el universo integrado incluye 1.818 pozos y 141.920 registros mensuales. Estas cantidades dependen de la versión de los archivos fuente y pueden cambiar en futuras actualizaciones.
Trabajo realizado
Revisión de estructura, tipos de datos, valores faltantes, duplicados y consistencia entre fuentes.
Preparación de variables técnicas y temporales, conservando los registros originales para mantener trazabilidad.
Exploración de las distribuciones de producción y revisión contextual de valores extremos, sin eliminarlos automáticamente.
Comparación descriptiva por período, área y yacimiento.
Análisis de petróleo, gas y agua por separado e incorporación de los meses registrados sin actividad efectiva.
Los meses sin actividad efectiva se describen como registros; no se les atribuye una causa específica. Los casos ambiguos se revisan y no se cuentan automáticamente como interrupciones confirmadas.
Notebook
La notebook de Google Colab contiene el desarrollo, las transformaciones, visualizaciones y resultados exploratorios:
📓 Abrir la notebook en Google Colab
Los CSV se leen desde una carpeta de Google Drive del grupo; no están incluidos en este repositorio. Para reproducir el análisis se necesitan los archivos fuente y ajustar la ruta de acceso en la notebook.
Nota sobre el bloque predictivo
La notebook conserva un anexo de experimentación predictiva desarrollado en una etapa anterior. Ese anexo aborda una pregunta distinta y no constituye el objetivo principal de esta versión descriptiva. Sus resultados no deben confundirse con las conclusiones del análisis mensual actual ni interpretarse como un modelo validado para uso operativo.
Equipo
Hugo Espinosa
Martina Sarmiento
Paula Perez Gianolini
Proyecto desarrollado en el marco del curso Data Science — Katherine Johnson, de Fundación YPF. El trabajo continúa en elaboración; el alcance, los datos y las conclusiones pueden actualizarse a medida que avance el análisis.
