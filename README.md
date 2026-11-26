# Observatorio de Seguridad Ciudadana — Colombia (2015–2025)

## 1. Descripción del Proyecto
Repositorio estructurado con datos oficiales de la Policía Nacional de Colombia (2015–2025), limpiados, estandarizados y consolidados en un panel departamental-anual (33 entidades territoriales × 11 años) para el análisis estadístico y modelado predictivo de la seguridad ciudadana.

## 2. Estructura del Repositorio

    repositorio_observatorio/
    ├── data/
    │   └── clean/
    │       ├── eventos_seguridad_unificado.parquet   # Base transaccional unificada (6 delitos)
    │       └── panel_departamental_seguridad.csv     # Panel maestro (33 deptos x 11 años)
    ├── docs/
    │   ├── diccionario_datos.md                      # Definición y rol estadístico de variables
    │   ├── heatmap_correlaciones.png                 # Matriz de correlación de Spearman
    │   └── tendencia_delitos_2015_2025.png           # Evolución anual de delitos
    ├── notebooks/                                    # Notebooks de ETL y análisis exploratorio
    └── README.md

## 3. Decisiones de Limpieza (ETL)
1. **Exclusión controlada:** Se excluyó `Hurto.xlsx` por corrupción de archivo; se integraron las 6 bases íntegras (`Amenazas`, `Delitos Sexuales`, `HomicidioIntencional`, `HurtoComercio`, `Secuestro`, `Terrorismo`).
2. **Estandarización de esquema:** Unificación de nombres de columnas con espacios residuales y nomenclaturas heterogéneas.
3. **Normalización de fechas:** Rescate de formatos mixtos (`YYYYMMDD` y `YYYY-MM-DD`) en `HomicidioIntencional` y filtrado de registros anómalos (ej. año 1905 en `Terrorismo`) al periodo 2015–2025.
4. **Precisión territorial (DANE):** Normalización del código DANE a 8 dígitos y separación de **Bogotá D.C.** (`cod_depto = 11`) respecto a Cundinamarca.
5. **Conservación de registros:** No se eliminaron filas idénticas porque en registros policiales representan denuncias independientes ocurridas el mismo día en el mismo municipio.

## 4. Selección Estadística de Variables
Debido a la asimetría positiva de los conteos delictivos, se utilizó correlación no paramétrica de **Spearman**:
- **Variables Dependientes (Y):** `homicidio_intencional` (violencia letal) y `hurto_comercio` (delito patrimonial).
- **Variables Independientes (X):** `amenazas`, `delitos_sexuales`, `secuestro`, `terrorismo`, `municipios_afectados`, `pct_arma_fuego`, `pct_arma_blanca`, `pct_victima_femenina`, `pct_victima_menores`.
- **Hallazgo clave:** `pct_arma_fuego` presenta una correlación fuerte con `homicidio_intencional` (ρ = 0.539) frente a una correlación débil con `hurto_comercio` (ρ = 0.112).
