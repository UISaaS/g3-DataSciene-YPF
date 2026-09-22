# 🛢️ Producción de pozos no convencionales en Vaca Muerta

## Grupo 3 · Data Science YPF

**Integrantes:** Hugo Espinosa · Martina Sarmiento · Paula Pérez Gianolini  
**Entrega:** AED, transformación y visualización con Pandas

> **Estado del proyecto:** exploración de datos · sin modelo predictivo en esta entrega

---

## 🎯 Pregunta de investigación

> **¿Cómo varía la producción mensual de los pozos no convencionales de YPF en Vaca Muerta según el área, el yacimiento, la formación y el período de producción?**

Buscamos comparar petróleo, gas y agua considerando también la cantidad de pozos, su antigüedad productiva y la evolución temporal.

## 🔎 Objetivos

- Comprender la estructura y calidad de los datasets.
- Integrar información técnica y productiva mediante `idpozo`.
- Comparar la producción entre áreas, yacimientos y formaciones.
- Diferenciar producción total de producción por pozo.
- Analizar la evolución mensual y dejar una base preparada para una etapa posterior de Machine Learning.

---

## 🧭 Alcance

El universo incluye pozos que cumplen simultáneamente:

| Criterio | Selección |
|---|---|
| Empresa | Razón social que contiene `YPF` |
| Recurso | `NO CONVENCIONAL` |
| Formación | `vaca muerta` |

> `YSUR` se excluye deliberadamente porque aparece identificada por separado. Por eso, los resultados representan la operación directa identificada como `YPF S.A.` y no necesariamente al grupo económico completo.

---

## 🗃️ Fuentes de datos

| Dataset | Granularidad | Información principal |
|---|---|---|
| **Capítulo IV — Pozos** | Una fila por pozo | Área, yacimiento, formación, profundidad, fechas, coordenadas y tipo de pozo |
| **Producción no convencional** | Una fila por pozo y mes | Petróleo, gas, agua, `tef`, año, mes y variables operativas |

- [📍 Capítulo IV — Pozos](https://datos.energia.gob.ar/dataset/produccion-de-petroleo-y-gas-por-pozo/archivo/cb5c0f04-7835-45cd-b982-3e25ca7d7751)
- [📈 Producción de pozos no convencionales](https://datos.energia.gob.ar/dataset/produccion-de-petroleo-y-gas-por-pozo/archivo/b5b58cdc-9e07-41f9-b392-fb9ec68b0725)

Ambas fuentes se integran mediante `idpozo`.

---

## ⚙️ Metodología

```text
Explorar → Auditar → Transformar → Integrar → Comparar → Visualizar
```

### Principales transformaciones

- ✅ Conversión y validación de fechas.
- ✅ Duración de perforación y terminación.
- ✅ Mes de vida productiva.
- ✅ Separación de meses activos mediante `tef > 0`.
- ✅ Caudales normalizados por días efectivos.
- ✅ Transformación `log1p` para distribuciones asimétricas.
- ✅ Integración de datasets por `idpozo`.
- ✅ Comparación por área, tipo de pozo y sistema de extracción.

---

## 📊 Criterios de comparación

No comparamos solamente los totales: un área con más pozos naturalmente puede producir más. Por eso analizamos conjuntamente:

- producción total;
- cantidad de pozos;
- media y mediana por pozo;
- dispersión;
- evolución mensual;
- antigüedad productiva.

Las diferencias observadas son **descriptivas** y no se interpretan automáticamente como relaciones causales.

---

## 📌 Resultados exploratorios actuales

- **1.818** pozos técnicos únicos.
- **141.920** registros mensuales integrados.
- **1.818** pozos presentes en ambas fuentes.
- Sin duplicados en la combinación `idpozo`–año–mes.
- Siete áreas concentran aproximadamente el **94,92 %** del universo activo utilizado en la comparación por área.
- La producción presenta fuerte asimetría y una proporción importante de registros iguales a cero.
- La producción acumulada en los primeros 24 meses presenta una dispersión considerable entre pozos.

---

## ⚠️ Limitaciones

- La producción disponible es principalmente mensual.
- La base pública no informa necesariamente la capacidad máxima o potencial del pozo.
- No se dispone de presión de fondo, geometría completa de fracturas ni eventos operativos detallados.
- Las diferencias entre áreas pueden estar influenciadas por antigüedad, cantidad de pozos, tipo de pozo y sistema de extracción.
- Los meses más recientes pueden estar parcialmente cargados.
- El análisis exploratorio de interferencia no confirma causalidad ni *frac-hits*.

---

## 🚀 Próximos pasos

1. Profundizar la comparación por `area`, `yacimiento` y `formacion`.
2. Analizar petróleo y gas por separado, respetando sus unidades.
3. Controlar diferencias de antigüedad y cantidad de pozos.
4. Incorporar intervalos de incertidumbre y tamaños de muestra.
5. Evaluar, después del AED, si corresponde construir un modelo de Machine Learning.

---

## 📁 Estructura del repositorio

```text
.
├── README.md
└── grupo_3_data_science.ipynb
```

## 📓 Notebook principal

[▶️ Abrir el notebook de análisis exploratorio](./grupo_3_data_science.ipynb)
