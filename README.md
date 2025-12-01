# Modelos Epidemiológicos de SARS-CoV-2 en Animales  
Este repositorio contiene dos modelos matemáticos independientes que analizan la transmisión de SARS-CoV-2 en animales usando datos reales de un archivo CSV (`sars_ani_data.csv`). Ambos modelos son aproximaciones simplificadas para entender patrones zoonóticos y dinámica de brotes.

---

## 📁 Estructura del repositorio

├── README.md
├── data/
│ └── sars_ani_data.csv
└── src/
├── modelo_sir_zoo.py # Modelo 1: SIR adaptado a transmisión humano→animal
└── modelo_superpropagacion.py # Modelo 2: Superpropagación en animales (L–H–S)

markdown
Copiar código

---

## 📌 MODELO 1: SIR-Zoo (Transmisión Humano → Animal)  
**Archivo:** `modelo_sir_zoo.py`

Este script adapta un modelo SIR clásico para estudiar transmisión desde humanos infectados hacia animales susceptibles. No considera transmisión animal→animal; asume una presión de infección constante desde humanos.

### Funciones principales del código:
- Carga el CSV y filtra datos (por ejemplo, perros en EE.UU.).
- Calcula casos diarios y acumulados.
- Implementa un sistema SIR con:
  - **S:** animales susceptibles  
  - **I:** animales infectados  
  - **R:** animales recuperados  
  - Fuerza de infección causada únicamente por humanos (Ih constante).
- Simula el modelo.
- Ajusta parámetros con mínimos cuadrados.
- Genera gráficos:
  - Curvas S, I, R del modelo.
  - Infectados reales vs modelo.
  - Panel descriptivo de parámetros.
- Muestra:
  - Parámetros ajustados.
  - Especies más frecuentes del dataset.

### Ejecución:
pip install numpy pandas scipy matplotlib
python src/modelo_sir_zoo.py

markdown
Copiar código

---

## 📌 MODELO 2: Superpropagación (L–H–S)  
**Archivo:** `modelo_superpropagacion.py`

Este modelo divide los animales en tres clases:

- **L:** baja transmisión (perros, gatos)
- **H:** alta transmisión (visones, hurones)
- **S:** brotes de superpropagación (granjas infectadas)

Modela una dinámica no lineal donde H y S se refuerzan mutuamente.

### Qué hace el código:
- Calcula a partir del CSV:
  - Proporción de animales L.
  - Proporción de animales H.
  - Número de brotes S (granjas).
- Simula la evolución de L, H y S durante 300 días.
- Grafica:
  - Evolución temporal.
  - Espacio de fases 3D (L–H–S).
  - L vs H.
  - Diagrama de bifurcación variando β₂.
- Calcula el jacobiano y autovalores.
- Interpreta estabilidad y significado biológico.

### Ejecución:
pip install numpy pandas scipy matplotlib
python src/modelo_superpropagacion.py

yaml
Copiar código

---

## 📊 Requisitos del archivo CSV (`sars_ani_data.csv`)

Los códigos utilizan las columnas:

- `host_com_orig `
- `country_name`
- `date_confirmed`
- `epidemiological_unit`

Debe estar en:

data/sars_ani_data.csv

yaml
Copiar código

---

## 🧪 Propósito del repositorio
- Explorar transmisión zoonótica del SARS-CoV-2.
- Comparar especies de baja vs alta transmisión.
- Analizar formación de brotes.
- Generar visualizaciones epidemiológicas.
- Ajustar modelos simples a datos reales.

