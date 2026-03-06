# challenge2-data-science-LATAM
desafio 2.  TelecomX


# 📊 Análisis de Evasión de Clientes (Churn) - Telecom X

Este repositorio contiene el análisis exploratorio de datos realizado para **Telecom X**, una empresa de telecomunicaciones que enfrenta una alta tasa de cancelación de clientes (churn). El objetivo principal es identificar los factores que más influyen en la decisión de los clientes de darse de baja y proponer estrategias accionables para reducir esta tasa.

---

## 📝 Descripción del Proyecto

Telecom X necesita comprender por qué sus clientes se están yendo. A partir de un conjunto de datos con información de facturación, servicios contratados, demográficos y de antigüedad, se realizó un proceso completo de extracción, limpieza, transformación y análisis exploratorio. Los resultados permiten segmentar a los clientes de alto riesgo y diseñar acciones de retención focalizadas.

---

## 🎯 Objetivos del Análisis

- Identificar las variables con mayor impacto en la cancelación de clientes.
- Caracterizar el perfil de los clientes que abandonan el servicio.
- Generar recomendaciones basadas en datos para disminuir la tasa de churn.

---

## 📁 Datos

La fuente de datos es un archivo JSON público disponible en el repositorio de Alura Cursos:  
[TelecomX_Data.json](https://raw.githubusercontent.com/alura-cursos/challenge2-data-science-LATAM/refs/heads/main/TelecomX_Data.json)

El conjunto de datos contiene **7032 registros** después de la limpieza, con **21 variables originales** que describen:

- **Datos demográficos:** género, edad (senior citizen), si tiene pareja, dependientes.
- **Antigüedad:** meses como cliente (tenure).
- **Servicios contratados:** teléfono, múltiples líneas, internet (DSL / fibra óptica), seguridad online, backup, soporte técnico, streaming TV y películas.
- **Datos de cuenta:** tipo de contrato (mensual, anual, bianual), facturación electrónica, método de pago, cargos mensuales y totales.
- **Variable objetivo:** Churn (Si/No).

Adicionalmente, se creó la variable `cuentas_diarias` (cargo mensual / 30) para facilitar la comunicación del costo diario.

---

## 🔍 Proceso de Análisis

El trabajo se desarrolló en un notebook de Jupyter (Google Colab) con las siguientes etapas:

1. **Extracción:**  
   - Descarga del JSON mediante `requests`.  
   - Normalización de la estructura anidada con `pandas.json_normalize()`.

2. **Transformación y Limpieza:**  
   - Renombrado de columnas para mejor legibilidad.  
   - Identificación y eliminación de registros con valores nulos o inconsistentes (clientes nuevos con cargo total vacío).  
   - Conversión de tipos de datos (`total_charges` a float).  
   - Limpieza de caracteres especiales en `payment_method`.  
   - Estandarización de variables categóricas a formato numérico (0/1) para facilitar el análisis.

3. **Análisis Exploratorio:**  
   - Estadísticas descriptivas de todas las variables.  
   - Visualizaciones comparativas entre clientes que cancelaron y los que permanecieron, tanto para variables categóricas (género, tipo de contrato, método de pago, servicios) como numéricas (tenure, cargos mensuales y totales).

4. **Conclusiones y Propuestas:**  
   - Se identificaron los segmentos de mayor riesgo y se formularon estrategias de retención.

---

## 📈 Principales Hallazgos

- La tasa de cancelación global es del **26,6%** (1869 clientes).
- **Tipo de contrato:**  
  - El 88,5% de los que cancelan tenían contrato **mes a mes**.
- **Método de pago:**  
  - El 57,3% de los que cancelan usaban **cheque electrónico** (método no automático).
- **Antigüedad:**  
  - Los clientes que cancelan tienen una permanencia media mucho menor (mediana de 10 meses) que los que se quedan (mediana de 38 meses).
- **Cargos mensuales:**  
  - Los clientes que cancelan pagan, en promedio, una factura mensual más alta ($80,75 vs $65,0).
- **Paquetes de servicios:**  
  - El 84,8% de los que cancelan tienen contratados **ambos servicios** (internet + teléfono).

---

## 💡 Estrategias de Retención Propuestas

1. **Fidelizar con contratos más largos:**  
   Ofrecer incentivos (descuentos, meses gratis) a clientes con contrato mensual para migrar a contratos anuales o bianuales.

2. **Promover el pago automático:**  
   Motivar a los usuarios de cheque electrónico a cambiar a débito automático mediante un pequeño descuento recurrente.

3. **Acompañar a los clientes nuevos:**  
   Implementar un programa de onboarding durante el primer año: llamadas de bienvenida, consejos de uso y oferta de renovación anticipada.

4. **Revisar la relación precio‑valor:**  
   Evaluar si los precios de los paquetes (especialmente fibra óptica) son competitivos y si los clientes que pagan más perciben la calidad esperada.

5. **Equipo especial para clientes con múltiples servicios:**  
   Crear un equipo de retención con capacidad de ofrecer mejoras o descuentos a quienes tengan contratados internet y teléfono y soliciten la baja.

6. **Modelo predictivo de churn:**  
   Utilizar los datos limpios para construir un modelo de machine learning que identifique clientes con alta probabilidad de cancelación, permitiendo acciones preventivas.

---

## 🛠 Tecnologías Utilizadas

- **Python 3**  
- **Pandas** – manipulación y limpieza de datos.  
- **NumPy** – operaciones numéricas.  
- **Matplotlib** – visualizaciones.  
- **Requests** – descarga del dataset.

Todo el código está contenido en un único notebook de Jupyter (`.ipynb`), preparado para ejecutarse en Google Colab o en cualquier entorno local con las librerías instaladas.

---

## 🚀 Cómo Ejecutar el Proyecto

1. Clona este repositorio:
   ```bash
   git clone https://github.com/tu-usuario/telecom-churn-analysis.git
   ```
2. Instala las dependencias necesarias:
   ```bash
   pip install pandas numpy matplotlib requests
   ```
3. Abre el notebook `TelecomX_LATAM.ipynb` con Jupyter Notebook o Google Colab.
4. Ejecuta las celdas en orden. El notebook descargará automáticamente los datos desde la URL indicada.

---

**Nota:** Este análisis fue desarrollado como parte de un challenge de data science y puede servir como base para estudios más profundos o para la implementación de un sistema de alerta temprana de churn.
