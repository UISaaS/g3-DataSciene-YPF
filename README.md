# Análisis de producción de pozos no convencionales en Vaca Muerta

## Grupo 3 — Data Science YPF

**Integrantes:** Hugo Espinosa · Martina Sarmiento · Paula Pérez Gianolini  
**Entrega:** Análisis exploratorio, transformación y visualización de datos con Pandas

---

## Pregunta de investigación

> **¿Cómo varía la producción mensual de los pozos no convencionales de YPF en Vaca Muerta según el área, el yacimiento, la formación y el período de producción?**

El análisis busca comparar la producción de petróleo, gas y agua entre distintas zonas de desarrollo, considerando también la cantidad de pozos, la antigüedad productiva y la evolución temporal.

---

## Objetivo general

Analizar el comportamiento productivo mensual de los pozos no convencionales de YPF asociados a la formación Vaca Muerta, integrando información técnica de los pozos con sus registros históricos de producción.

El trabajo se concentra en el **Análisis Exploratorio de Datos (AED)** para:

- comprender la estructura y calidad de las fuentes;
- integrar información técnica y productiva mediante `idpozo`;
- comparar la producción entre áreas, yacimientos y formaciones;
- distinguir producción total de producción promedio por pozo;
- estudiar la evolución de la producción a través del tiempo;
- dejar una base preparada para una etapa posterior de Machine Learning.

> Esta entrega no desarrolla modelos predictivos de Machine Learning.

---

## Alcance del análisis

El universo principal está compuesto por pozos que cumplen simultáneamente:

- empresa cuya razón social contiene `YPF`;
- recurso `NO CONVENCIONAL`;
- formación `vaca muerta`.

`YSUR` queda excluida deliberadamente porque aparece identificada por separado en las fuentes. Por lo tanto, los resultados representan la operación directa identificada como `YPF S.A.` y no necesariamente al grupo económico completo.

---

## Fuentes de datos

Las fuentes son datasets públicos de la Secretaría de Energía de la Nación.

### Capítulo IV — Pozos

Contiene información técnica y descriptiva, con una fila por pozo:

- `idpozo`;
- área;
- yacimiento;
- formación;
- cuenca;
- provincia;
- profundidad;
- tipo de pozo;
- sistema de extracción;
- fechas de perforación y terminación;
- coordenadas.

[Consultar dataset Capítulo IV — Pozos](https://datos.energia.gob.ar/dataset/produccion-de-petroleo-y-gas-por-pozo/archivo/cb5c0f04-7835-45cd-b982-3e25ca7d7751)

### Producción de pozos no convencionales

Contiene registros mensuales, con una fila por pozo y mes:

- `idpozo`;
- año y mes;
- `prod_pet`;
- `prod_gas`;
- `prod_agua`;
- `tef`;
- tipo de recurso;
- clasificación;
- provincia;
- coordenadas.

[Consultar dataset de producción no convencional](https://datos.energia.gob.ar/dataset/produccion-de-petroleo-y-gas-por-pozo/archivo/b5b58cdc-9e07-41f9-b392-fb9ec68b0725)

Ambas fuentes se relacionan mediante el identificador `idpozo`.

---

## Metodología

1. Exploración inicial de las fuentes.
2. Revisión de tipos de datos, valores faltantes y duplicados.
3. Verificación de la granularidad de cada dataset.
4. Conversión y validación de fechas.
5. Cálculo de duraciones operativas.
6. Construcción de variables temporales, incluido el mes de vida productiva.
7. Separación de meses activos mediante `tef > 0`.
8. Cálculo de caudales normalizados por días efectivos.
9. Transformación `log1p` para explorar distribuciones asimétricas.
10. Integración de las fuentes mediante `idpozo`.
11. Comparación de producción por área, tipo de pozo y sistema de extracción.
12. Análisis temporal de producción total y producción por pozo.
13. Comparación complementaria de la producción acumulada durante los primeros 24 meses.

---

## Criterios de comparación

No se comparan únicamente los volúmenes totales, porque un área con más pozos naturalmente puede producir más. Por eso se consideran conjuntamente:

- producción total;
- cantidad de pozos;
- producción media por pozo;
- producción mediana por pozo;
- dispersión de la producción;
- evolución mensual;
- antigüedad productiva.

Las diferencias observadas son descriptivas y no se interpretan automáticamente como relaciones causales.

---

## Resultados exploratorios actuales

- El universo técnico contiene **1.818 pozos únicos**.
- El universo productivo integrado contiene **141.920 registros mensuales**.
- Se identifican **1.818 pozos presentes en ambas fuentes**.
- No se detectan duplicados en la combinación `idpozo`–año–mes.
- Las variables productivas presentan fuerte asimetría y una proporción importante de registros iguales a cero.
- El análisis por área se concentra en siete áreas con al menos 50 pozos, que representan aproximadamente el **94,92 %** del universo activo de esa comparación.
- La producción acumulada durante los primeros 24 meses muestra una dispersión considerable entre pozos.

---

## Limitaciones

- La producción disponible es principalmente mensual.
- La base pública no informa necesariamente capacidad máxima o potencial del pozo.
- No se dispone de presión de fondo, geometría completa de fracturas ni eventos operativos detallados.
- Las diferencias entre áreas pueden estar influenciadas por antigüedad, cantidad de pozos, tipo de pozo y sistema de extracción.
- Los meses más recientes pueden estar parcialmente cargados.
- El análisis de interferencia entre pozos, incluido en el notebook como exploración complementaria, no confirma causalidad ni *frac-hits*.

---

## Próximos pasos

- Profundizar la comparación por `area`, `yacimiento` y `formacion`.
- Analizar por separado petróleo y gas, respetando sus unidades.
- Incorporar intervalos de incertidumbre y tamaños de muestra.
- Evaluar diferencias entre áreas controlando por antigüedad y cantidad de pozos.
- Definir, después del AED, si existe una pregunta adecuada para una etapa de Machine Learning.

---

## Estructura del repositorio

```text
.
├── README.md
└── grupo_3_data_science.ipynb
```

## Notebook principal

[ Abrir notebook de análisis exploratorio ](./grupo_3_data_science.ipynb)
