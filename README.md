# 🚗 Análisis del Mercado Automotriz Ecuatoriano (2019–2025)

> Dashboard de Business Intelligence desarrollado en **Power BI Desktop** con datos oficiales del **Servicio de Rentas Internas (SRI)** del Ecuador.

![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=flat&logo=powerbi&logoColor=black)
![DAX](https://img.shields.io/badge/DAX-217346?style=flat&logo=microsoft&logoColor=white)
![Power Query](https://img.shields.io/badge/Power%20Query-376C6D?style=flat&logo=microsoft&logoColor=white)
![Status](https://img.shields.io/badge/Status-Completo-brightgreen)
![License](https://img.shields.io/badge/Datos-P%C3%BAblicos%20SRI-blue)

---

## 📊 Resumen del Proyecto

Este proyecto analiza **3.477.557 transacciones de registro vehicular** entre 2019 y 2025, con un avalúo total aproximado de **USD 53.000 millones**. El análisis identifica tres fenómenos simultáneos que están redefiniendo el mercado automotriz ecuatoriano:

- Consolidación de **CHEVROLET** como líder histórico, con presión creciente de marcas asiáticas
- Concentración geográfica en **GUAYAS y PICHINCHA** (47,8% del mercado)
- Inicio de una **transición energética** hacia vehículos híbridos y eléctricos

---

## 🎯 Objetivos del Análisis

- Identificar tendencias de volumen y valor del mercado en el período 2019–2025
- Analizar la distribución geográfica de transacciones por provincia y cantón
- Estudiar el comportamiento por marca, clase de vehículo y tipo de combustible
- Detectar oportunidades estratégicas para fabricantes, importadoras y política pública

---

## 🔍 Hallazgos Principales

| #   | Hallazgo                            | Insight clave                                                                                                                      |
| --- | ----------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| 1   | **Recuperación post-pandemia**      | Caída del 15% en 2020 seguida de una recuperación acelerada en 2021, la más rápida de la región                                    |
| 2   | **Irrupción de marcas chinas**      | SHINERAY alcanzó el segundo lugar del mercado; DAYTONA creció un 33,73% YoY                                                        |
| 3   | **Anomalía geográfica en Imbabura** | La provincia supera a Manabí en transacciones (472.250) pese a tener menor población, sugiriendo una estrategia comercial efectiva |
| 4   | **Electrificación acelerada**       | Los vehículos eléctricos registran la mayor tasa de crecimiento YoY del mercado, impulsados por incentivos tributarios del SRI     |
| 5   | **Dominio de motocicletas**         | Segmento dominante por clase, vinculado al crecimiento del delivery y la movilidad urbana accesible                                |
| 6   | **Alta valorización**               | Crecimiento de 16,5% YoY en avalúo total refleja un mercado dinámico y en expansión                                                |

---

## 🛠️ Stack Técnico

| Herramienta          | Uso                                            |
| -------------------- | ---------------------------------------------- |
| **Power BI Desktop** | Modelado, visualización e informes             |
| **Power Query (M)**  | Ingesta y transformación de 7 archivos CSV     |
| **DAX**              | Medidas calculadas (YoY, acumulados, rankings) |
| **Modelo Estrella**  | Arquitectura del modelo de datos               |

### Modelo de Datos

```
Vehículos (Tabla de Hechos)
    ├── Dim_Cantones     → Decodifica cantón y provincia (jerarquía geográfica)
    ├── Dim_Colores      → Decodifica color del vehículo
    ├── Calendario       → Dimensión tiempo (jerarquía Año > Mes)
    └── Medidas          → Tabla centralizada de métricas DAX
```

Se eligió el **esquema estrella** sobre un modelo plano por: (1) rendimiento en memoria, (2) optimización nativa de Power BI sobre tablas relacionadas, y (3) la necesidad de jerarquías geográficas y temporales para drill-down.

---

## 📁 Estructura del Repositorio

```
📦 analisis-automotriz-ecuador
 ┣ 📂 data/                       → Datasets fuente (CSV del SRI, comprimidos)
 ┃ ┗ SRI_Vehiculos_Nuevos_2019-2025.zip   → 7 CSV (2019–2025), ~570 MB descomprimidos
 ┣ 📂 docs/                       → Documentación técnica
 ┃ ┗ SRI_Vehiculos_DD.xlsx        → Diccionario de datos (campos, tipos, descripciones)
 ┣ 📂 screenshots/                → Capturas del dashboard
 ┣ 📄 AnalisisAutomotriz.pbix     → Archivo Power BI del proyecto
 ┗ 📄 README.md
```

---

## ▶️ Cómo visualizar el dashboard

1. Descarga e instala [**Power BI Desktop**](https://powerbi.microsoft.com/desktop/) (gratuito, solo Windows)
2. Clona este repositorio o descarga el ZIP
3. Descomprime `data/SRI_Vehiculos_Nuevos_2019-2025.zip` en la misma carpeta `data/` (los CSV se comprimen para respetar el límite de 100 MB de GitHub)
4. Abre `AnalisisAutomotriz.pbix` con Power BI Desktop. Si Power Query pide refrescar la fuente, apunta las rutas a la carpeta `data/`
5. Si te interesa el análisis sin instalar nada, revisa las capturas en **`screenshots/`**

---

## 📚 Diccionario de Datos

El archivo `docs/SRI_Vehiculos_DD.xlsx` documenta cada campo del dataset original del SRI: nombre, tipo de dato, descripción y valores admitidos. Es la referencia para entender el modelo y replicar transformaciones.

---

## 📌 Notas Metodológicas

- Los datos corresponden a **registros oficiales del SRI Ecuador** (fuente pública)
- El dataset original incluía archivos desde 2020; el archivo de **2019 fue incorporado manualmente** ajustando encabezados y derivando la columna `Año` del nombre del archivo para garantizar consistencia
- Se aplicó **CRISP-DM** como marco metodológico (Comprensión del negocio → Comprensión de los datos → Preparación → Modelado → Evaluación → Despliegue)
- Las transformaciones se ejecutan en Power Query antes de la carga al modelo (limpieza, tipado y unión de los 7 CSV)

---

## 📈 Vista Previa

| Sección                          | Archivo                                  |
| -------------------------------- | ---------------------------------------- |
| Resumen ejecutivo                | `screenshots/01_resumen_ejecutivo.jpeg`  |
| Tendencia por marca              | `screenshots/02_tendencia_marca.jpeg`    |
| Tendencia por provincia          | `screenshots/03_tendencia_provincia.jpeg`|

## 📄 Fuente de Datos

Los datos son de acceso público y provienen del portal oficial del **Servicio de Rentas Internas (SRI) del Ecuador**.
🔗 [https://www.sri.gob.ec](https://www.sri.gob.ec)
