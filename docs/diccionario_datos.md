# Diccionario de Datos — `panel_departamental_seguridad.csv`

| Variable | Tipo | Rol | Descripción |
| :--- | :--- | :--- | :--- |
| `cod_depto` | string (2 dígitos) | Identificador | Código DANE departamental estandarizado (`11` = Bogotá D.C.). |
| `departamento` | string | Identificador | Nombre del departamento o Distrito Capital (33 territorios). |
| `anio` | int | Identificador / X | Año del hecho delictivo (2015–2025). |
| `homicidio_intencional` | int | **Dependiente (Y1)** | Total anual de homicidios intencionales registrados. |
| `hurto_comercio` | int | **Dependiente (Y2)** | Total anual de hurtos a comercio registrados. |
| `amenazas` | int | Independiente (X) | Total anual de denuncias por amenazas. |
| `delitos_sexuales` | int | Independiente (X) | Total anual de delitos sexuales registrados. |
| `secuestro` | int | Independiente (X) | Total anual de casos de secuestro. |
| `terrorismo` | int | Independiente (X) | Total anual de actos de terrorismo. |
| `total_delitos` | int | Agregado | Suma total de eventos de las 6 bases en el departamento y año. |
| `municipios_afectados` | int | Independiente (X) | Número de municipios distintos con al menos un delito en el año. |
| `pct_arma_fuego` | float (%) | Independiente (X) | Porcentaje de delitos cometidos con arma de fuego. |
| `pct_arma_blanca` | float (%) | Independiente (X) | Porcentaje de delitos cometidos con arma blanca/cortopunzante. |
| `pct_victima_femenina` | float (%) | Independiente (X) | Porcentaje de casos con víctima de género femenino. |
| `pct_victima_menores` | float (%) | Independiente (X) | Porcentaje de casos con víctimas menores o adolescentes. |
