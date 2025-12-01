# Modelo-SIR-Zoo-para-transmisi-n-SARS-CoV-2-Humano-Animal

Este repositorio contiene un análisis simple de la transmisión de SARS-CoV-2 desde humanos hacia animales mediante un modelo epidemiológico tipo SIR (Susceptible-Infectado-Recuperado), adaptado al contexto zoonótico.

El proyecto utiliza datos reales de reportes de infección en animales (por ejemplo, perros en Estados Unidos) y compara dichos datos con las curvas generadas por el modelo. Además, incluye un ajuste paramétrico para intentar aproximar los parámetros del modelo a la tendencia observada en los datos.
## 📊 Descripción general del análisis

El código realiza:

1. **Carga y filtrado del dataset**, seleccionando únicamente perros en Estados Unidos.
2. **Procesamiento temporal** para obtener casos acumulados por fecha.
3. **Simulación del modelo SIR-Zoo**, donde:
   - β: transmisión humano → animal  
   - γ: recuperación  
   - α: mortalidad / remoción
4. **Visualización de**:
   - Curvas S, I, R del modelo
   - Curva de infectados
   - Datos reales vs modelo
   - Panel explicativo de parámetros
5. **Ajuste de parámetros** utilizando mínimos cuadrados para aproximar el modelo a los datos reales.
6. **Resumen de distribución por especie** dentro del dataset.

---

## 🐾 ¿Qué es el Modelo SIR-Zoo?

Es una simplificación epidemiológica que asume:

- La transmisión ocurre **solo humano → animal**.
- No hay transmisión animal → animal.
- Población animal cerrada.
- Humanos infectados (Ih) se mantienen constantes.

El sistema de ecuaciones es:

- dS/dt = −β·S·Ih  
- dI/dt = β·S·Ih − γ·I − α·I  
- dR/dt = γ·I  

---

## 📁 Datos: `sars_ani_data.csv`

El CSV debe ubicarse en:

data/sars_ani_data.csv

yaml
Copiar código

y debe contener las columnas utilizadas por el script, incluyendo:

- `host_com_orig`
- `country_name`
- `date_confirmed`
- Otros metadatos originales del dataset

---

## ▶️ Cómo ejecutar el script

### **1. Clonar el repositorio**
```bash
git clone <URL-del-repo>
cd <nombre-del-repo>

