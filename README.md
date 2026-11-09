# Proyecto: efecto del salario mínimo en el desempleo en Chile (jóvenes vs. adultos)

## Contenido de la carpeta

```
proyecto/
├── README.md                       ← este archivo
├── construccion_variables.ipynb    ← código + justificación de cada variable (Markdown)
├── datos_originales/               ← archivos tal como se descargaron de las fuentes
│   ├── indicadores_principales_edad.xlsx   INE, ENE: indicadores por tramo etario (trimestres móviles)
│   ├── tabulado_ir_empalmado.xlsx          INE: Índice Nominal de Remuneraciones, serie empalmada (2023=100)
│   ├── salario_minimo_chile_2010_2026.xlsx Leyes de reajuste del Ingreso Mínimo Mensual
│   ├── IPC_EMP_2023.xlsx                   BCCh/INE: IPC general empalmado (2023=100)
│   ├── IPC_VAREMP_2023.xlsx                BCCh/INE: IPC, variación en 12 meses
│   └── CCNN2018_IMACEC_01_A.xlsx           BCCh: Imacec empalmado, serie original (2018=100)
└── datos_procesados/               ← salidas del notebook
    ├── base_trimestral.csv         una fila por trimestre, 2010-T1 a 2026-T3 (67 obs.)
    ├── base_apilada.csv            dos filas por trimestre (15–24 y 25+), para el modelo con interacción
    ├── base_datos.xlsx             las dos bases anteriores en un Excel
    └── grafico_series.png          desempleo por grupo e índice de Kaitz
```

## Cómo usarlo

1. Abre `construccion_variables.ipynb` en Jupyter, VS Code o Google Colab (sube la carpeta completa).
2. Ejecuta todas las celdas en orden ("Run All"). El notebook lee `datos_originales/` y vuelve a generar `datos_procesados/`.
3. Requisitos: `pandas`, `numpy`, `matplotlib`, `statsmodels`, `openpyxl` y `python-calamine`
   (`pip install pandas numpy matplotlib statsmodels openpyxl python-calamine`).

## Pendiente

- **Inflación 2010:** el archivo `IPC_VAREMP_2023.xlsx` comienza en enero 2011. Vuelve a descargarlo desde el
  Banco Central (Precios → IPC General y medidas subyacentes → Variación mensual y anual) con **fecha de inicio 2010**,
  reemplázalo en `datos_originales/` y vuelve a correr el notebook. Sin ese cambio, los 4 trimestres de 2010 quedan
  sin inflación y se pierden en las regresiones que la incluyan.

## Fuentes

- INE, Encuesta Nacional de Empleo: https://www.ine.gob.cl/estadisticas/sociales/mercado-laboral/ocupacion-y-desocupacion
- INE, Remuneraciones y costos laborales: https://www.ine.gob.cl/estadisticas/sociales/mercado-laboral/remuneraciones-y-costos-laborales
- Banco Central de Chile, Base de Datos Estadísticos: https://si3.bcentral.cl/siete
- Leyes de reajuste del Ingreso Mínimo Mensual: https://www.bcn.cl/leychile
