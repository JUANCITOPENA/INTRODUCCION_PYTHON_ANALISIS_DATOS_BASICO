
# 🧾 Manual de Proyecto: Análisis de Ventas - Vision Metrics

## 📌 Objetivo del Proyecto
Este proyecto tiene como objetivo simular un conjunto de datos de ventas, analizarlo y visualizar métricas clave de desempeño comercial usando Python y librerías de análisis de datos.

---

## 🛠️ Configuración del Entorno en Visual Studio Code

### 1. Instalación de Python y Visual Studio Code
- Descargar e instalar Python desde: https://www.python.org/downloads/
- Descargar Visual Studio Code desde: https://code.visualstudio.com/

### 2. Crear un Entorno Virtual
Abre una terminal en Visual Studio Code y ejecuta:
```bash
python -m venv env

```

### 3. Activar el Entorno Virtual
- En Windows:
```bash
.\env\Scripts\activate

```


### 4. Instalar Librerías Necesarias
Una vez activado el entorno, instala las siguientes librerías:
```bash
pip install pandas numpy matplotlib seaborn
```

---

## 🧠 Narrativa de los Datos Simulados

Se genera un conjunto de 200 registros de ventas simuladas para el año 2024, usando productos tecnológicos y vendedores ficticios. Cada venta incluye: fecha, producto, categoría, vendedor, cantidad, precio unitario y total de la venta.

---

## 📦 Librerías Importadas

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
from datetime import datetime
import random
```

- `pandas`: Manejo de datos en estructuras tipo tabla (DataFrame).
- `numpy`: Cálculos numéricos y generación aleatoria.
- `matplotlib` y `seaborn`: Visualización de datos.
- `datetime`: Manejo de fechas.
- `random`: Generación de valores aleatorios.

---

## ⚙️ Configuración Inicial del Entorno

```python
sns.set(style="whitegrid", palette=["skyblue", "salmon", "lightgreen", "gold"])
plt.rcParams["figure.figsize"] = (10, 5)
np.random.seed(24)
```

Establece estilos visuales y configura el tamaño por defecto de los gráficos.

---

## 🧪 Simulación del Dataset

```python
fechas = pd.date_range(start="2024-01-01", end="2024-12-31", freq="D")
productos = [(...)]
vendedores = ["Francisco Junior", "Eliant Ortiz", "Dariel Vásquez", "Luis Santos"]
```

Se generan fechas diarias, productos y vendedores para crear registros aleatorios.

---

## 🖼️ Visualizaciones

### 1. Ventas Totales por Mes
```python
df["Mes"] = df["Fecha"].dt.to_period("M").astype(str)
ventas_mes = df.groupby("Mes")["Total Venta"].sum().reset_index()
sns.lineplot(data=ventas_mes, x="Mes", y="Total Venta", marker="o", color="royalblue")
```

### 2. Top 5 Productos Más Vendidos
```python
top_productos = df.groupby("Producto")["Cantidad"].sum().sort_values(ascending=False).head(5)
sns.barplot(x=top_productos.values, y=top_productos.index, palette="viridis")
```

### 3. Ventas por Vendedor
```python
ventas_vendedor = df.groupby("Vendedor")["Total Venta"].sum().reset_index()
sns.barplot(data=ventas_vendedor, x="Vendedor", y="Total Venta", palette="pastel")
```

### 4. Ingresos por Categoría
```python
ventas_categoria = df.groupby("Categoría")["Total Venta"].sum().reset_index()
sns.barplot(data=ventas_categoria, x="Total Venta", y="Categoría", palette="cubehelix")
```

---

## ✅ Conclusión

Este proyecto es ideal para principiantes que desean entender el flujo completo de un análisis de ventas en Python: desde la creación de datos ficticios hasta la obtención de insights mediante visualización.


