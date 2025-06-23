
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
python -m venv venv
```

### 3. Activar el Entorno Virtual
- En Windows:
```bash
venv\Scripts\activate
```
- En macOS/Linux:
```bash
source venv/bin/activate
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







## 🐍 Proyecto: Análisis de Ventas - Vision Metrics (Python)

### 11.1 Importación de librerías

\`\`\`python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
from datetime import datetime
import random
\`\`\`

### 11.2 Configuración general

\`\`\`python
sns.set(style="whitegrid", palette=["skyblue", "salmon", "lightgreen", "gold"])
plt.rcParams["figure.figsize"] = (10, 5)
np.random.seed(24)
\`\`\`

### 11.3 Simulación del dataset

\`\`\`python
fechas = pd.date_range(start="2024-01-01", end="2024-12-31", freq="D")
n_registros = 200

productos = [
    ("Laptop Dell Inspiron", "Tecnología"),
    ("Nokia 4090 128GB", "Telefonía"),
    ("Audífonos Sony", "Accesorios"),
    ("Procesador Intel i9 14900K", "Tecnología"),
    ("Xbox Serie X", "Tecnología"),
    ("Teclado Logitech", "Tecnología"),
    ("Memoria RAM 8GB", "Accesorios"),
    ("Router TP-Link 4200 DRS", "Redes"),
    ("Disco Duro Kingston", "Almacenamiento"),
    ("Power Bank 20000mAh", "Accesorios")
]

vendedores = ["Francisco Junior", "Eliant Ortiz", "Dariel Vásquez", "Luis Santos"]

data = []
for _ in range(n_registros):
    fecha = random.choice(fechas)
    producto, categoria = random.choice(productos)
    vendedor = random.choice(vendedores)
    cantidad = random.randint(1, 5)
    precio_unitario = random.randint(1000, 5000)
    total_venta = cantidad * precio_unitario

    data.append({
        "Fecha": fecha,
        "Producto": producto,
        "Categoría": categoria,
        "Vendedor": vendedor,
        "Cantidad": cantidad,
        "Precio Unitario": precio_unitario,
        "Total Venta": total_venta
    })

df = pd.DataFrame(data)
\`\`\`

### 11.4 Análisis y visualización

#### 11.4.1 Línea: Ventas por mes

\`\`\`python
df["Mes"] = df["Fecha"].dt.to_period("M").astype(str)
ventas_mes = df.groupby("Mes")["Total Venta"].sum().reset_index()
plt.figure(figsize=(10, 4))
sns.lineplot(data=ventas_mes, x="Mes", y="Total Venta", marker="o", color="royalblue")
plt.title("Ventas Totales por Mes")
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()
\`\`\`

#### 11.4.2 Top 5 productos más vendidos

\`\`\`python
top_productos = df.groupby("Producto")["Cantidad"].sum().sort_values(ascending=False).head(5)
plt.figure(figsize=(8, 4))
sns.barplot(x=top_productos.values, y=top_productos.index, palette="viridis")
plt.title("Top 5 Productos más Vendidos (Cantidad)")
plt.xlabel("Unidades Vendidas")
plt.tight_layout()
plt.show()
\`\`\`

#### 11.4.3 Ventas por vendedor

\`\`\`python
ventas_vendedor = df.groupby("Vendedor")["Total Venta"].sum().reset_index().sort_values("Total Venta", ascending=False)
plt.figure(figsize=(8, 4))
sns.barplot(data=ventas_vendedor, x="Vendedor", y="Total Venta", palette="pastel")
plt.title("Ventas Totales por Vendedor")
plt.tight_layout()
plt.show()
\`\`\`

#### 11.4.4 Ingresos por categoría

\`\`\`python
ventas_categoria = df.groupby("Categoría")["Total Venta"].sum().reset_index()
plt.figure(figsize=(8, 4))
sns.barplot(data=ventas_categoria, x="Total Venta", y="Categoría", palette="cubehelix")
plt.title("Ingresos por Categoría")
plt.tight_layout()
plt.show()
\`\`\`
