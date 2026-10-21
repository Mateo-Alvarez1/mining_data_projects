# ⛏️ Mining Data Projects

**Análisis de datos y machine learning aplicados a la industria minera.**

Portfolio de proyectos prácticos que resuelven problemas reales de una operación minera: abastecimiento, inventario, proveedores, demanda y, próximamente, análisis geoespacial. Cada proyecto parte de una **pregunta de negocio** y termina en **conclusiones y recomendaciones para la operación**, no solo en código.

![Python](https://img.shields.io/badge/Python-3776AB?logo=python&logoColor=white)
![pandas](https://img.shields.io/badge/pandas-150458?logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-013243?logo=numpy&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?logo=scikitlearn&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-F37626?logo=jupyter&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-4479A1?logo=postgresql&logoColor=white)
![Estado](https://img.shields.io/badge/estado-en%20desarrollo-yellow)

---

## 🎯 Por qué la minería

En una mina, los datos tienen consecuencias directas sobre la operación:

- Un **repuesto crítico** que falta puede detener un camión, un molino o toda la planta.
- El **exceso de stock** inmoviliza capital en almacenes alejados, a veces a más de 4.000 m de altura.
- Un **proveedor que entrega tarde** genera compras urgentes, fletes aéreos y paradas no planificadas.

Este repositorio aborda estos problemas con datos de **13 almacenes que abastecen 7 operaciones de litio, oro y cobre** en Argentina (Jujuy, Salta, Catamarca, San Juan y Santa Cruz), con un almacén central en Buenos Aires.

---

## 📂 Proyectos

| # | Proyecto | Pregunta de negocio | Técnicas | Estado |
|---|----------|---------------------|----------|--------|
| 01 | [Gestión de inventario](./01_gestion_inventario) | ¿Qué materiales concentran el consumo y cuáles ponen en riesgo la operación? | Clasificación ABC, matriz ABC × criticidad, análisis de quiebres de stock | 🟢 Terminado |
| 02 | [Desempeño de proveedores](./02_desempeno_proveedores) | ¿Qué proveedores entregan tarde o incompleto y cuánto le cuesta a la mina? | KPIs de OTIF, fill rate, lead time, calidad y flete | ⚪ Próximo |
| 03 | [Predicción de entregas tardías](./03_prediccion_atrasos) | ¿Podemos anticipar qué órdenes de compra van a llegar tarde? | Clasificación con machine learning, validación temporal, prevención de *data leakage* | ⚪ Planificado |
| 04 | [Demanda y riesgo de quiebre](./04_demanda_quiebres) | ¿Cuánto material van a consumir las minas y cuándo nos vamos a quedar sin stock? | Series de tiempo, pronóstico de demanda, stock de seguridad | ⚪ Planificado |
| 05 | [Tablero integrador](./05_tablero_abastecimiento) | ¿Cómo impactan los atrasos de proveedores en los quiebres de stock de cada mina? | Integración de datasets, dashboard interactivo | ⚪ Planificado |
| 06+ | Análisis geoespacial | Geoquímica, sondajes y estimación de leyes | geopandas, variogramas, kriging | 🔜 Futuro |

---

## 🔍 Hallazgos destacados

> Esta sección se actualiza a medida que se completa cada proyecto.

**01 · Gestión de inventario**
- El **30% de los materiales concentra el 80% del consumo** (USD 136,7 M en despachos a mina, oct 2023 a sep 2026).
- El ABC por consumo coincide solo en un **56%** con la clasificación vigente: **no alcanza para gestionar un almacén minero**.
- Se identificaron **22 materiales "trampa"** (bajo consumo y criticidad alta), como componentes de molienda y chancado, motores de potencia y equipos contra incendio, además de un **repuesto de seguro** sin despachos en tres años.

<!-- Descomentá cuando tengas la imagen:
![Curva ABC](./01_gestion_inventario/imagenes/curva_abc.png)
-->

---

## 🗂️ Estructura del repositorio

```
mining_data_projects/
├── README.md
├── data/                          # Datasets comprimidos (.zip)
│   ├── mining_warehouse_movements.zip
│   └── mining_purchase_orders_supplier_performance.zip
├── 01_gestion_inventario/
│   ├── README.md                  # Resumen, hallazgos y recomendaciones
│   ├── notebooks/
│   └── imagenes/
├── 02_desempeno_proveedores/
├── 03_prediccion_atrasos/
├── 04_demanda_quiebres/
└── 05_tablero_abastecimiento/
```

Cada proyecto tiene su propio `README.md` con el problema, la metodología, los hallazgos y las recomendaciones.

---

## 📊 Datasets

| Dataset | Registros | Período | Contenido |
|---------|-----------|---------|-----------|
| Movimientos de almacén | 129.093 | oct 2023 a sep 2026 | Recepciones, despachos a mina, transferencias entre almacenes, ajustes y devoluciones, con stock antes/después del movimiento |
| Órdenes de compra y proveedores | 22.574 | oct 2023 a sep 2026 | Líneas de OC con lead time, atrasos, OTIF, fill rate, inspección de calidad, flete e incoterms |

Ambos comparten llaves de **material, proveedor, almacén y mina**, lo que permite cruzarlos.

> **Nota:** los datos son **sintéticos**: simulan la operación de abastecimiento de un grupo minero. Los hallazgos ilustran la metodología de análisis y no describen una empresa real. Las limitaciones detectadas en los datos se documentan en cada proyecto.

---

## 🚀 Cómo ejecutar

```bash
git clone https://github.com/TU-USUARIO/mining_data_projects.git
cd mining_data_projects
pip install -r requirements.txt
jupyter notebook
```

Los notebooks leen los `.zip` directamente con pandas, sin descomprimir:

```python
df = pd.read_csv("../data/mining_warehouse_movements.zip", sep=";")
```

---

## 🧭 Enfoque de trabajo

1. **Pregunta de negocio:** qué problema de la operación se quiere resolver.
2. **Calidad de datos:** verificar hipótesis con código antes de analizar.
3. **Análisis:** métricas e indicadores usados en la industria (ABC, OTIF, fill rate, lead time).
4. **Conclusiones:** cada hallazgo con un número que lo respalde y su impacto operativo.
5. **Recomendaciones:** qué hacer, con qué área y con qué prioridad.

---

## 👤 Sobre mí

Me estoy especializando en análisis de datos y data science aplicados a la industria minera.

- 💼 LinkedIn: [linkedin.com/in/TU-USUARIO](https://www.linkedin.com/in/mateoaalvarez/)
- 🌐 Observatorio Minero: *próximamente*
- 📧 Contacto: mateoalvarez384@gmail.com

⭐ Si te interesa el cruce entre datos y minería, ¡no dudes en escribirme!
