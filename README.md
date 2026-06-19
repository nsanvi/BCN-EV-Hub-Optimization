# Optimización de la Red de Hubs de Carga para Vehículos Eléctricos en Barcelona

**Presentación interactiva de resultados →** [Ver visualización](https://htmlpreview.github.io/?https://github.com/nsanvi/WIP-EV_hub_optimization/blob/main/entregable_proyecto/visualizacion_y_presentacion/index_v3_standalone.html)

---

Barcelona cuenta con 75.410 vehículos eléctricos distribuidos en 73 barrios y solo 383 puntos de recarga (ratio: 197 EVs por cargador). Este proyecto aplica K-Means ponderado por demanda no satisfecha para determinar las ubicaciones óptimas de nuevos hubs de carga, validado mediante un test A/B de 300 iteraciones frente a una estrategia de asignación proporcional a la población.

**Resultado principal:** con 25 hubs, la estrategia basada en demanda cubre 13.400 EVs con una mejora del 45,9 % sobre el baseline, superándolo en el 100 % de las simulaciones.

---

## Resultados

| Escenario | EVs cubiertos (Smart) | Mejora vs. baseline | Win rate |
|-----------|----------------------|---------------------|----------|
| 10 hubs   | 4.991                | +11,8 %             | 76 %     |
| 25 hubs   | 13.400               | +45,9 %             | 100 %    |
| 50 hubs   | 22.576               | +58,5 %             | 100 %    |

Barrios con mayor déficit de infraestructura: Sant Gervasi–Galvany, Sant Pere / Sta. Caterina / la Ribera, la Nova Esquerra de l'Eixample, la Dreta de l'Eixample y la Marina del Prat Vermell.

---

## Contenido del repositorio

```
entregable_proyecto/
├── memoria_proyecto_eada.pdf                  ← memoria escrita del proyecto
├── data/
│   ├── raw/                                   ← datasets fuente (Open Data BCN)
│   └── processed/                             ← outputs: GeoJSON + 3 CSVs
├── notebooks_src/
│   ├── notebooks/   (01_setup → 05_ab_simulation)
│   ├── src/         (config, data_loader, preprocessing, optimization, visualization)
│   └── requirements.txt
└── visualizacion_y_presentacion/
    └── index_v3_standalone.html               ← presentación interactiva de resultados
```

---

## Ejecutar el análisis

```bash
cd entregable_proyecto/notebooks_src
python -m venv venv && source venv/bin/activate
pip install -r requirements.txt
jupyter notebook notebooks/
```

Los notebooks se ejecutan en orden (01 → 05). Todos los datos necesarios están incluidos en `data/`.

---

## Fuentes de datos

Open Data Ajuntament de Barcelona:

| Dataset | Descripción | Año |
|---------|-------------|-----|
| Límites de barrios | Geometrías poligonales de 73 barrios | 2023 |
| Punts de Recàrrega VE | Ubicaciones de cargadores existentes | Q2 2023 |
| Parc de vehicles per propulsió | Recuento por tipo (EV, híbrido, gasolina, diésel) | 2024 |
| Renda disponible per persona | Ingreso disponible medio por persona y barrio | 2022 |

---

Nicolás San Vicente · Máster en Data Analytics · EADA Business School · Junio 2026
