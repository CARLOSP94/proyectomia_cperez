# OptiPick-3D: IA Prescriptiva para la Optimización de Picking en DISLOG

![Python](https://img.shields.io/badge/Python-3.10-blue)
![Framework](https://img.shields.io/badge/Kernel-OR--Tools-orange)
![Status](https://img.shields.io/badge/Status-Finalizado-brightgreen)

## 📌 1. Descripción del Problema y Solución
En el Centro de Distribución de **DISLOG (Sucursal Iñaquito)**, la productividad del picking manual presentaba un estancamiento en **126 Cajas por Hora (CPH)**. La complejidad de las rutas y la rigurosidad de los protocolos de **segregación química e inocuidad alimentaria** generaban cuellos de botella operativos.

**OptiPick-3D** es una solución de **IA Prescriptiva** que optimiza simultáneamente:
1. **Ruteo de Manhattan:** Minimiza la distancia recorrida por el operario.
2. **Estiba 3D:** Asegura pallets estables (1.70m / 750kg) aplicando *Gravity Loading*.
3. **Segregación:** Garantiza el cumplimiento normativo entre productos químicos y alimentarios.

## ⚙️ 2. Arquitectura del Pipeline
El prototipo está estructurado en tres capas modulares:

* **Capa de Ingesta:** Carga y limpieza de datos maestros de ítems y pedidos CSV.
* **Kernel IA (Procesamiento):**
    * *Graph Construction:* Representación matemática del layout de la bodega.
    * *Path Sequencing:* Uso de **Google OR-Tools** para resolver la secuencia óptima.
    * *Constraints Engine:* Validación en tiempo real de restricciones físicas y normativas.
* **Capa de Salida:** Generación de la **Secuencia Lógica de Picking** y dashboard de métricas.

## 📊 3. Resultados y Validación
El modelo fue validado con un dataset real de **414 transferencias**, obteniendo resultados superiores a los objetivos planteados:

| Métrica | Baseline (Manual) | OptiPick-3D (IA) | Mejora |
| :--- | :---: | :---: | :---: |
| **Productividad (CPH)** | 126.00 | **266.07** | **+111.17%** |
| **Distancia Recorrida** | - | - | **-19.46%** |
| **Cumplimiento Normativo** | Variable | **100%** | Crítico |

## ⚖️ 4. Ética e IA Responsable
- **Bienestar:** Reducción de la fatiga del operario mediante trayectorias ergonómicas.
- **Inocuidad:** Eliminación del error humano en la segregación de contaminantes.
- **Transparencia:** El sistema es totalmente auditable y explicable en sus decisiones de ruteo.

## 🚀 5. Instrucciones de Ejecución
Siga estos pasos para reproducir los resultados en **Google Colab**:

1.  **Clonar** el repositorio o descargar el archivo `proyecto_mia_cperez.ipynb`.
2.  **Cargar** el notebook en el entorno de Colab.
3.  **Subir** los archivos de la carpeta `/data` (`MAESTRO_FINAL_LAYOUT_ESPEJO.csv` y `TRANSFERENCIA_4TO_TRIMESTRE_2025.csv`).
4.  **Instalar dependencias:**
    ```python
    pip install ortools pandas numpy matplotlib plotly
    ```
5.  **Ejecutar todas las celdas** para visualizar el reporte de performance y los pallets generados.

## 📂 6. Estructura de Carpetas
```text
├── data/               # Archivos CSV (Maestros, Pedidos, nuevo pedido)
├── notebooks/          # proyecto_mia_cperez.ipynb (Código principal)
└── README.md           # Documentación del proyecto
