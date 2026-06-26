
# FFAA

============================================================
REPORTE — REGRESIÓN LINEAL (BASELINE)
Generado: 2026-06-17 15:39:37
============================================================

[DATOS DE ENTRADA]
  Archivo: dataset_features_FFAA.csv
  Total filas: 35,564

[SPLIT TEMPORAL]
  Train: 28,451 licitaciones (2015-01-02 → 2023-05-09)
  Test:  7,113  licitaciones (2023-05-09 → 2025-12-12)

[MÉTRICAS — TRAIN]
  R² (log):           0.4226
  RMSE (log):         0.7733
  MAE (log):          0.5174
  ─────────────────────────────────
  R² (CLP):           0.2029
  RMSE (CLP):         $36.5M
  MAE (CLP):          $7.2M
  MAPE:               139558.2%
  MdAPE (mediano):    63.5%

[MÉTRICAS — TEST]
  R² (log):           0.3169
  RMSE (log):         0.8056
  MAE (log):          0.5217
  ─────────────────────────────────
  R² (CLP):           0.3568
  RMSE (CLP):         $47.9M
  MAE (CLP):          $12.6M
  MAPE:               206699.6%
  MdAPE (mediano):    62.0%

[INTERPRETACIÓN]
  El modelo se equivoca en mediana un 62.0% del precio real.
  R²=0.3169 significa que el modelo explica el 31.7% de la varianza del target.
  ⚠ R² bajo — esperado para un modelo lineal simple.
    Este número mejorará con Random Forest y LightGBM.
  ⚠ Diferencia train/test >0.1 → posible overfitting leve.

[FEATURES USADAS]
  1. log_MontoEstimado
  2. TipoLicitacion_Ord
  3. sector_FFAA
  4. Mes
  5. Trimestre
  6. Anio
  7. EsDiciembre
  8. EsSegundoSemestre
  9. NumOferentes
  10. EsMonopolio
  11. inst_ratio_hist
  12. inst_log_monto_hist
  13. inst_n_licitaciones
  14. inst_oferentes_hist
  15. inst_dias_hist
  16. rubro_log_monto_hist
  17. rubro_ratio_hist
  18. rubro_n_licitaciones
  19. TamanoProveedorGanador_Ord
  20. EsPrecioReferencial
  21. DiasPublicacionAdjudicacion
  22. HayRechazadas
  23. SpreadRelativoOfertas

[NOTA PARA EL INFORME]
  Este modelo es el BASELINE. Su función no es predecir bien,
  sino establecer el piso mínimo de rendimiento que los
  modelos más complejos deben superar para justificarse.

============================================================

============================================================
REPORTE — LIGHTGBM
Generado: 2026-06-17 15:45:00
============================================================

[DATOS DE ENTRADA]
  Archivo: dataset_features_FFAA.csv
  Total filas: 35,564

[PARÁMETROS]
  n_estimators: 500
  learning_rate: 0.05
  num_leaves: 25
  max_depth: 8
  min_child_samples: 40
  subsample: 0.7
  colsample_bytree: 0.5
  reg_alpha: 0.2
  reg_lambda: 0.2
  random_state: 42
  n_jobs: -1
  verbose: -1
  early_stopping_rounds: 50
  árboles usados: 244 (de 500 máximos)

[SPLIT TEMPORAL]
  Train: 28,451 (2015-01-02 → 2023-05-09)
  Test:  7,113 (2023-05-09 → 2025-12-12)

[MÉTRICAS — TRAIN]
  R² (log):           0.7034
  RMSE (log):         0.5542
  MAE (log):          0.3061
  ─────────────────────────────────
  R² (CLP):           0.3819
  RMSE (CLP):         $32.1M
  MAE (CLP):          $5.1M
  MAPE:               36646.1%
  MdAPE (mediano):    32.9%

[MÉTRICAS — TEST]
  R² (log):           0.5691
  RMSE (log):         0.6398
  MAE (log):          0.3347
  ─────────────────────────────────
  R² (CLP):           0.2844
  RMSE (CLP):         $50.5M
  MAE (CLP):          $10.5M
  MAPE:               200423.3%
  MdAPE (mediano):    32.9%

[COMPARACIÓN vs BASELINE (Regresión Lineal)]
  R2_log           Baseline=0.3505  LightGBM=0.5691  ↑ MEJORA (0.2186)
  RMSE_log         Baseline=0.9008  LightGBM=0.6398  ↑ MEJORA (0.2610)
  MdAPE_%          Baseline=66.3000  LightGBM=32.8940  ↑ MEJORA (33.4060)

[COMPARACIÓN vs RANDOM FOREST]
  R2_log           RF=0.5887  LightGBM=0.5691  ↓ EMPEORA (0.0196)
  RMSE_log         RF=0.7169  LightGBM=0.6398  ↑ MEJORA (0.0771)
  MdAPE_%          RF=38.1000  LightGBM=32.8940  ↑ MEJORA (5.2060)

[FEATURE IMPORTANCE — TOP 15 (Gain)]
  log_MontoEstimado                   80932  ████████████████████████████████████████████████████████████████████████████████
  SpreadRelativoOfertas               50641  ██████████████████████████████████████████████████
  TipoLicitacion_Ord                  35291  ██████████████████████████████████
  rubro_log_monto_hist                9406  █████████
  inst_log_monto_hist                 8951  ████████
  rubro_ratio_hist                    6424  ██████
  NumOferentes                        5214  █████
  inst_ratio_hist                     3394  ███
  inst_oferentes_hist                 2153  ██
  rubro_n_licitaciones                1863  █
  inst_dias_hist                      1810  █
  inst_n_licitaciones                 1654  █
  Anio                                1577  █
  HayRechazadas                       720  
  Mes                                 617  

[INTERPRETACIÓN]
  MdAPE: 32.9% (vs 66.3% del baseline)
  R²:    0.5691 (vs 0.3505 del baseline)
  ✓ Gap train/test = 0.134 → generalización aceptable.

[FEATURES USADAS]
  1. log_MontoEstimado
  2. TipoLicitacion_Ord
  3. sector_FFAA
  4. Mes
  5. Trimestre
  6. Anio
  7. EsDiciembre
  8. EsSegundoSemestre
  9. NumOferentes
  10. EsMonopolio
  11. inst_ratio_hist
  12. inst_log_monto_hist
  13. inst_n_licitaciones
  14. inst_oferentes_hist
  15. inst_dias_hist
  16. rubro_log_monto_hist
  17. rubro_ratio_hist
  18. rubro_n_licitaciones
  19. TamanoProveedorGanador_Ord
  20. EsPrecioReferencial
  21. DiasPublicacionAdjudicacion
  22. HayRechazadas
  23. SpreadRelativoOfertas

============================================================

============================================================
REPORTE — RANDOM FOREST
Generado: 2026-06-17 15:41:26
============================================================

[DATOS DE ENTRADA]
  Archivo: dataset_features_FFAA.csv
  Total filas: 35,564

[HIPERPARÁMETROS]
  n_estimators: 300
  max_depth: 20
  min_samples_leaf: 8
  max_features: 0.6
  random_state: 42
  n_jobs: -1

[SPLIT TEMPORAL]
  Train: 28,451 licitaciones (2015-01-02 → 2023-05-09)
  Test:  7,113  licitaciones (2023-05-09 → 2025-12-12)

[MÉTRICAS — TRAIN]
  R² (log):           0.7695
  RMSE (log):         0.4886
  MAE (log):          0.2512
  ─────────────────────────────────
  R² (CLP):           0.4585
  RMSE (CLP):         $30.1M
  MAE (CLP):          $4.4M
  MAPE:               20477.4%
  MdAPE (mediano):    23.8%

[MÉTRICAS — TEST]
  R² (log):           0.5553
  RMSE (log):         0.6500
  MAE (log):          0.3405
  ─────────────────────────────────
  R² (CLP):           0.3502
  RMSE (CLP):         $48.1M
  MAE (CLP):          $10.2M
  MAPE:               223539.7%
  MdAPE (mediano):    32.3%

[COMPARACIÓN vs BASELINE (Regresión Lineal)]
  R2_log           Baseline=0.3383  RF=0.5553  ↑ MEJORA (0.2170)
  RMSE_log         Baseline=0.9655  RF=0.6500  ↑ MEJORA (0.3155)
  MdAPE_%          Baseline=70.8000  RF=32.2851  ↑ MEJORA (38.5149)

[FEATURE IMPORTANCE — TOP 15]
  log_MontoEstimado                   0.4315  ██████████████████████████████████████████████████████████████████████████████████████
  SpreadRelativoOfertas               0.2544  ██████████████████████████████████████████████████
  TipoLicitacion_Ord                  0.1125  ██████████████████████
  rubro_log_monto_hist                0.0342  ██████
  inst_log_monto_hist                 0.0312  ██████
  rubro_ratio_hist                    0.0204  ████
  inst_ratio_hist                     0.0190  ███
  NumOferentes                        0.0156  ███
  rubro_n_licitaciones                0.0154  ███
  inst_oferentes_hist                 0.0144  ██
  inst_dias_hist                      0.0132  ██
  inst_n_licitaciones                 0.0129  ██
  Mes                                 0.0055  █
  Anio                                0.0044  
  TamanoProveedorGanador_Ord          0.0038  

[INTERPRETACIÓN]
  El modelo se equivoca en mediana un 32.3% del precio real.
  R²=0.5553 → explica el 55.5% de la varianza del target.
  ⚠ Gap train/test = 0.214 → overfitting moderado.
    Considera reducir max_depth o aumentar min_samples_leaf.

[FEATURES USADAS]
  1. log_MontoEstimado
  2. TipoLicitacion_Ord
  3. sector_FFAA
  4. Mes
  5. Trimestre
  6. Anio
  7. EsDiciembre
  8. EsSegundoSemestre
  9. NumOferentes
  10. EsMonopolio
  11. inst_ratio_hist
  12. inst_log_monto_hist
  13. inst_n_licitaciones
  14. inst_oferentes_hist
  15. inst_dias_hist
  16. rubro_log_monto_hist
  17. rubro_ratio_hist
  18. rubro_n_licitaciones
  19. TamanoProveedorGanador_Ord
  20. EsPrecioReferencial
  21. DiasPublicacionAdjudicacion
  22. HayRechazadas
  23. SpreadRelativoOfertas

[NOTA PARA EL INFORME]
  Random Forest captura relaciones no lineales entre features,
  a diferencia de la regresión lineal del baseline.
  La feature importance reemplaza a los coeficientes y muestra
  qué variables el modelo usa más para reducir el error.
  Siguiente paso: LightGBM para comparar rendimiento y velocidad.

============================================================

# GobCentral

============================================================
REPORTE — REGRESIÓN LINEAL (BASELINE)
Generado: 2026-06-17 15:52:00
============================================================

[DATOS DE ENTRADA]
  Archivo: dataset_features_GOB_CENTRAL.csv
  Total filas: 162,422

[SPLIT TEMPORAL]
  Train: 129,937 licitaciones (2015-01-02 → 2023-06-23)
  Test:  32,485  licitaciones (2023-06-23 → 2025-12-24)

[MÉTRICAS — TRAIN]
  R² (log):           0.4745
  RMSE (log):         0.8471
  MAE (log):          0.5527
  ─────────────────────────────────
  R² (CLP):           0.1698
  RMSE (CLP):         $112.6M
  MAE (CLP):          $18.5M
  MAPE:               427592.3%
  MdAPE (mediano):    65.4%

[MÉTRICAS — TEST]
  R² (log):           0.3647
  RMSE (log):         0.8216
  MAE (log):          0.5143
  ─────────────────────────────────
  R² (CLP):           0.2484
  RMSE (CLP):         $134.6M
  MAE (CLP):          $26.7M
  MAPE:               754842.9%
  MdAPE (mediano):    60.2%

[INTERPRETACIÓN]
  El modelo se equivoca en mediana un 60.2% del precio real.
  R²=0.3647 significa que el modelo explica el 36.5% de la varianza del target.
  ⚠ R² bajo — esperado para un modelo lineal simple.
    Este número mejorará con Random Forest y LightGBM.
  ⚠ Diferencia train/test >0.1 → posible overfitting leve.

[FEATURES USADAS]
  1. log_MontoEstimado
  2. TipoLicitacion_Ord
  3. sector_GOB_CENTRAL
  4. Mes
  5. Trimestre
  6. Anio
  7. EsDiciembre
  8. EsSegundoSemestre
  9. NumOferentes
  10. EsMonopolio
  11. inst_ratio_hist
  12. inst_log_monto_hist
  13. inst_n_licitaciones
  14. inst_oferentes_hist
  15. inst_dias_hist
  16. rubro_log_monto_hist
  17. rubro_ratio_hist
  18. rubro_n_licitaciones
  19. TamanoProveedorGanador_Ord
  20. EsPrecioReferencial
  21. DiasPublicacionAdjudicacion
  22. HayRechazadas
  23. SpreadRelativoOfertas

[NOTA PARA EL INFORME]
  Este modelo es el BASELINE. Su función no es predecir bien,
  sino establecer el piso mínimo de rendimiento que los
  modelos más complejos deben superar para justificarse.

============================================================

============================================================
REPORTE — LIGHTGBM
Generado: 2026-06-17 15:56:09
============================================================

[DATOS DE ENTRADA]
  Archivo: dataset_features_GOB_CENTRAL.csv
  Total filas: 162,422

[PARÁMETROS]
  n_estimators: 500
  learning_rate: 0.05
  num_leaves: 25
  max_depth: 8
  min_child_samples: 40
  subsample: 0.7
  colsample_bytree: 0.5
  reg_alpha: 0.2
  reg_lambda: 0.2
  random_state: 42
  n_jobs: -1
  verbose: -1
  early_stopping_rounds: 50
  árboles usados: 497 (de 500 máximos)

[SPLIT TEMPORAL]
  Train: 129,937 (2015-01-02 → 2023-06-23)
  Test:  32,485 (2023-06-23 → 2025-12-24)

[MÉTRICAS — TRAIN]
  R² (log):           0.7097
  RMSE (log):         0.6296
  MAE (log):          0.3504
  ─────────────────────────────────
  R² (CLP):           0.4481
  RMSE (CLP):         $91.8M
  MAE (CLP):          $11.7M
  MAPE:               106549.0%
  MdAPE (mediano):    36.1%

[MÉTRICAS — TEST]
  R² (log):           0.5559
  RMSE (log):         0.6869
  MAE (log):          0.3579
  ─────────────────────────────────
  R² (CLP):           0.4371
  RMSE (CLP):         $116.5M
  MAE (CLP):          $19.9M
  MAPE:               367336.9%
  MdAPE (mediano):    33.6%

[COMPARACIÓN vs BASELINE (Regresión Lineal)]
  R2_log           Baseline=0.3505  LightGBM=0.5559  ↑ MEJORA (0.2054)
  RMSE_log         Baseline=0.9008  LightGBM=0.6869  ↑ MEJORA (0.2139)
  MdAPE_%          Baseline=66.3000  LightGBM=33.5982  ↑ MEJORA (32.7018)

[COMPARACIÓN vs RANDOM FOREST]
  R2_log           RF=0.5887  LightGBM=0.5559  ↓ EMPEORA (0.0328)
  RMSE_log         RF=0.7169  LightGBM=0.6869  ↑ MEJORA (0.0300)
  MdAPE_%          RF=38.1000  LightGBM=33.5982  ↑ MEJORA (4.5018)

[FEATURE IMPORTANCE — TOP 15 (Gain)]
  log_MontoEstimado                   524887  ████████████████████████████████████████████████████████████████████████████████
  SpreadRelativoOfertas               229532  ██████████████████████████████████
  TipoLicitacion_Ord                  206557  ███████████████████████████████
  rubro_log_monto_hist                103344  ███████████████
  rubro_ratio_hist                    73709  ███████████
  inst_log_monto_hist                 47103  ███████
  inst_ratio_hist                     20823  ███
  NumOferentes                        15661  ██
  inst_dias_hist                      12470  █
  DiasPublicacionAdjudicacion         12304  █
  inst_oferentes_hist                 10620  █
  Anio                                8272  █
  inst_n_licitaciones                 7888  █
  rubro_n_licitaciones                6227  
  TamanoProveedorGanador_Ord          2542  

[INTERPRETACIÓN]
  MdAPE: 33.6% (vs 66.3% del baseline)
  R²:    0.5559 (vs 0.3505 del baseline)
  ⚠ Gap train/test = 0.154 → overfitting moderado.
    Considera aumentar min_child_samples o reducir num_leaves.

[FEATURES USADAS]
  1. log_MontoEstimado
  2. TipoLicitacion_Ord
  3. sector_GOB_CENTRAL
  4. Mes
  5. Trimestre
  6. Anio
  7. EsDiciembre
  8. EsSegundoSemestre
  9. NumOferentes
  10. EsMonopolio
  11. inst_ratio_hist
  12. inst_log_monto_hist
  13. inst_n_licitaciones
  14. inst_oferentes_hist
  15. inst_dias_hist
  16. rubro_log_monto_hist
  17. rubro_ratio_hist
  18. rubro_n_licitaciones
  19. TamanoProveedorGanador_Ord
  20. EsPrecioReferencial
  21. DiasPublicacionAdjudicacion
  22. HayRechazadas
  23. SpreadRelativoOfertas

============================================================

============================================================
REPORTE — RANDOM FOREST
Generado: 2026-06-17 15:54:32
============================================================

[DATOS DE ENTRADA]
  Archivo: dataset_features_GOB_CENTRAL.csv
  Total filas: 162,422

[HIPERPARÁMETROS]
  n_estimators: 300
  max_depth: 20
  min_samples_leaf: 8
  max_features: 0.6
  random_state: 42
  n_jobs: -1

[SPLIT TEMPORAL]
  Train: 129,937 licitaciones (2015-01-02 → 2023-06-23)
  Test:  32,485  licitaciones (2023-06-23 → 2025-12-24)

[MÉTRICAS — TRAIN]
  R² (log):           0.8009
  RMSE (log):         0.5215
  MAE (log):          0.2690
  ─────────────────────────────────
  R² (CLP):           0.5431
  RMSE (CLP):         $83.5M
  MAE (CLP):          $9.4M
  MAPE:               24313.4%
  MdAPE (mediano):    24.6%

[MÉTRICAS — TEST]
  R² (log):           0.5644
  RMSE (log):         0.6803
  MAE (log):          0.3507
  ─────────────────────────────────
  R² (CLP):           0.5332
  RMSE (CLP):         $106.1M
  MAE (CLP):          $18.8M
  MAPE:               547391.8%
  MdAPE (mediano):    30.6%

[COMPARACIÓN vs BASELINE (Regresión Lineal)]
  R2_log           Baseline=0.3383  RF=0.5644  ↑ MEJORA (0.2261)
  RMSE_log         Baseline=0.9655  RF=0.6803  ↑ MEJORA (0.2852)
  MdAPE_%          Baseline=70.8000  RF=30.5705  ↑ MEJORA (40.2295)

[FEATURE IMPORTANCE — TOP 15]
  log_MontoEstimado                   0.4545  ██████████████████████████████████████████████████████████████████████████████████████████
  SpreadRelativoOfertas               0.1764  ███████████████████████████████████
  TipoLicitacion_Ord                  0.1058  █████████████████████
  rubro_log_monto_hist                0.0702  ██████████████
  rubro_ratio_hist                    0.0469  █████████
  inst_ratio_hist                     0.0219  ████
  inst_log_monto_hist                 0.0208  ████
  inst_dias_hist                      0.0166  ███
  inst_oferentes_hist                 0.0154  ███
  inst_n_licitaciones                 0.0128  ██
  NumOferentes                        0.0124  ██
  rubro_n_licitaciones                0.0122  ██
  DiasPublicacionAdjudicacion         0.0116  ██
  Anio                                0.0059  █
  Mes                                 0.0056  █

[INTERPRETACIÓN]
  El modelo se equivoca en mediana un 30.6% del precio real.
  R²=0.5644 → explica el 56.4% de la varianza del target.
  ⚠ Gap train/test = 0.236 → overfitting moderado.
    Considera reducir max_depth o aumentar min_samples_leaf.

[FEATURES USADAS]
  1. log_MontoEstimado
  2. TipoLicitacion_Ord
  3. sector_GOB_CENTRAL
  4. Mes
  5. Trimestre
  6. Anio
  7. EsDiciembre
  8. EsSegundoSemestre
  9. NumOferentes
  10. EsMonopolio
  11. inst_ratio_hist
  12. inst_log_monto_hist
  13. inst_n_licitaciones
  14. inst_oferentes_hist
  15. inst_dias_hist
  16. rubro_log_monto_hist
  17. rubro_ratio_hist
  18. rubro_n_licitaciones
  19. TamanoProveedorGanador_Ord
  20. EsPrecioReferencial
  21. DiasPublicacionAdjudicacion
  22. HayRechazadas
  23. SpreadRelativoOfertas

[NOTA PARA EL INFORME]
  Random Forest captura relaciones no lineales entre features,
  a diferencia de la regresión lineal del baseline.
  La feature importance reemplaza a los coeficientes y muestra
  qué variables el modelo usa más para reducir el error.
  Siguiente paso: LightGBM para comparar rendimiento y velocidad.

============================================================


# LegislativoJudicial

============================================================
REPORTE — REGRESIÓN LINEAL (BASELINE)
Generado: 2026-06-17 15:58:57
============================================================

[DATOS DE ENTRADA]
  Archivo: dataset_features_LEGISLATIVO.csv
  Total filas: 9,485

[SPLIT TEMPORAL]
  Train: 7,588 licitaciones (2015-01-05 → 2022-08-31)
  Test:  1,897  licitaciones (2022-08-31 → 2025-12-23)

[MÉTRICAS — TRAIN]
  R² (log):           0.6011
  RMSE (log):         0.7920
  MAE (log):          0.4298
  ─────────────────────────────────
  R² (CLP):           0.0230
  RMSE (CLP):         $831.3M
  MAE (CLP):          $40.6M
  MAPE:               67388.4%
  MdAPE (mediano):    45.3%

[MÉTRICAS — TEST]
  R² (log):           0.1489
  RMSE (log):         1.4715
  MAE (log):          0.6453
  ─────────────────────────────────
  R² (CLP):           -0.0015
  RMSE (CLP):         $1.77B
  MAE (CLP):          $100.8M
  MAPE:               270553.8%
  MdAPE (mediano):    55.8%

[INTERPRETACIÓN]
  El modelo se equivoca en mediana un 55.8% del precio real.
  R²=0.1489 significa que el modelo explica el 14.9% de la varianza del target.
  ⚠ R² bajo — esperado para un modelo lineal simple.
    Este número mejorará con Random Forest y LightGBM.
  ⚠ Diferencia train/test >0.1 → posible overfitting leve.

[FEATURES USADAS]
  1. log_MontoEstimado
  2. TipoLicitacion_Ord
  3. sector_LEGISLATIVO
  4. Mes
  5. Trimestre
  6. Anio
  7. EsDiciembre
  8. EsSegundoSemestre
  9. NumOferentes
  10. EsMonopolio
  11. inst_ratio_hist
  12. inst_log_monto_hist
  13. inst_n_licitaciones
  14. inst_oferentes_hist
  15. inst_dias_hist
  16. rubro_log_monto_hist
  17. rubro_ratio_hist
  18. rubro_n_licitaciones
  19. TamanoProveedorGanador_Ord
  20. EsPrecioReferencial
  21. DiasPublicacionAdjudicacion
  22. HayRechazadas
  23. SpreadRelativoOfertas

[NOTA PARA EL INFORME]
  Este modelo es el BASELINE. Su función no es predecir bien,
  sino establecer el piso mínimo de rendimiento que los
  modelos más complejos deben superar para justificarse.

============================================================

============================================================
REPORTE — LIGHTGBM
Generado: 2026-06-17 16:01:23
============================================================

[DATOS DE ENTRADA]
  Archivo: dataset_features_LEGISLATIVO.csv
  Total filas: 9,485

[PARÁMETROS]
  n_estimators: 500
  learning_rate: 0.05
  num_leaves: 25
  max_depth: 8
  min_child_samples: 40
  subsample: 0.7
  colsample_bytree: 0.5
  reg_alpha: 0.2
  reg_lambda: 0.2
  random_state: 42
  n_jobs: -1
  verbose: -1
  early_stopping_rounds: 50
  árboles usados: 190 (de 500 máximos)

[SPLIT TEMPORAL]
  Train: 7,588 (2015-01-05 → 2022-08-31)
  Test:  1,897 (2022-08-31 → 2025-12-23)

[MÉTRICAS — TRAIN]
  R² (log):           0.8262
  RMSE (log):         0.5228
  MAE (log):          0.2689
  ─────────────────────────────────
  R² (CLP):           0.0307
  RMSE (CLP):         $828.0M
  MAE (CLP):          $35.0M
  MAPE:               5285.3%
  MdAPE (mediano):    28.1%

[MÉTRICAS — TEST]
  R² (log):           0.6236
  RMSE (log):         0.9785
  MAE (log):          0.5288
  ─────────────────────────────────
  R² (CLP):           -0.0018
  RMSE (CLP):         $1.77B
  MAE (CLP):          $97.7M
  MAPE:               291772.2%
  MdAPE (mediano):    48.9%

[COMPARACIÓN vs BASELINE (Regresión Lineal)]
  R2_log           Baseline=0.3505  LightGBM=0.6236  ↑ MEJORA (0.2731)
  RMSE_log         Baseline=0.9008  LightGBM=0.9785  ↓ EMPEORA (0.0777)
  MdAPE_%          Baseline=66.3000  LightGBM=48.8551  ↑ MEJORA (17.4449)

[COMPARACIÓN vs RANDOM FOREST]
  R2_log           RF=0.5887  LightGBM=0.6236  ↑ MEJORA (0.0349)
  RMSE_log         RF=0.7169  LightGBM=0.9785  ↓ EMPEORA (0.2616)
  MdAPE_%          RF=38.1000  LightGBM=48.8551  ↓ EMPEORA (10.7551)

[FEATURE IMPORTANCE — TOP 15 (Gain)]
  log_MontoEstimado                   57227  ████████████████████████████████████████████████████████████████████████████████
  rubro_log_monto_hist                10221  ██████████████
  TipoLicitacion_Ord                  9731  █████████████
  SpreadRelativoOfertas               6797  █████████
  rubro_ratio_hist                    4666  ██████
  DiasPublicacionAdjudicacion         2135  ██
  inst_n_licitaciones                 1503  ██
  rubro_n_licitaciones                1419  █
  inst_log_monto_hist                 1315  █
  NumOferentes                        1292  █
  inst_ratio_hist                     1101  █
  inst_dias_hist                      814  █
  inst_oferentes_hist                 755  █
  TamanoProveedorGanador_Ord          598  
  Mes                                 480  

[INTERPRETACIÓN]
  MdAPE: 48.9% (vs 66.3% del baseline)
  R²:    0.6236 (vs 0.3505 del baseline)
  ⚠ Gap train/test = 0.203 → overfitting moderado.
    Considera aumentar min_child_samples o reducir num_leaves.

[FEATURES USADAS]
  1. log_MontoEstimado
  2. TipoLicitacion_Ord
  3. sector_LEGISLATIVO
  4. Mes
  5. Trimestre
  6. Anio
  7. EsDiciembre
  8. EsSegundoSemestre
  9. NumOferentes
  10. EsMonopolio
  11. inst_ratio_hist
  12. inst_log_monto_hist
  13. inst_n_licitaciones
  14. inst_oferentes_hist
  15. inst_dias_hist
  16. rubro_log_monto_hist
  17. rubro_ratio_hist
  18. rubro_n_licitaciones
  19. TamanoProveedorGanador_Ord
  20. EsPrecioReferencial
  21. DiasPublicacionAdjudicacion
  22. HayRechazadas
  23. SpreadRelativoOfertas

============================================================

============================================================
REPORTE — RANDOM FOREST
Generado: 2026-06-17 15:59:38
============================================================

[DATOS DE ENTRADA]
  Archivo: dataset_features_LEGISLATIVO.csv
  Total filas: 9,485

[HIPERPARÁMETROS]
  n_estimators: 300
  max_depth: 20
  min_samples_leaf: 8
  max_features: 0.6
  random_state: 42
  n_jobs: -1

[SPLIT TEMPORAL]
  Train: 7,588 licitaciones (2015-01-05 → 2022-08-31)
  Test:  1,897  licitaciones (2022-08-31 → 2025-12-23)

[MÉTRICAS — TRAIN]
  R² (log):           0.8264
  RMSE (log):         0.5225
  MAE (log):          0.2372
  ─────────────────────────────────
  R² (CLP):           0.0605
  RMSE (CLP):         $815.2M
  MAE (CLP):          $32.5M
  MAPE:               8707.3%
  MdAPE (mediano):    16.5%

[MÉTRICAS — TEST]
  R² (log):           0.6144
  RMSE (log):         0.9905
  MAE (log):          0.5223
  ─────────────────────────────────
  R² (CLP):           -0.0017
  RMSE (CLP):         $1.77B
  MAE (CLP):          $97.6M
  MAPE:               302754.7%
  MdAPE (mediano):    40.2%

[COMPARACIÓN vs BASELINE (Regresión Lineal)]
  R2_log           Baseline=0.3383  RF=0.6144  ↑ MEJORA (0.2761)
  RMSE_log         Baseline=0.9655  RF=0.9905  ↓ EMPEORA (0.0250)
  MdAPE_%          Baseline=70.8000  RF=40.1969  ↑ MEJORA (30.6031)

[FEATURE IMPORTANCE — TOP 15]
  log_MontoEstimado                   0.6594  ███████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████
  rubro_log_monto_hist                0.0906  ██████████████████
  TipoLicitacion_Ord                  0.0891  █████████████████
  SpreadRelativoOfertas               0.0553  ███████████
  rubro_ratio_hist                    0.0220  ████
  DiasPublicacionAdjudicacion         0.0160  ███
  rubro_n_licitaciones                0.0120  ██
  inst_n_licitaciones                 0.0087  █
  NumOferentes                        0.0076  █
  inst_ratio_hist                     0.0073  █
  inst_oferentes_hist                 0.0069  █
  inst_dias_hist                      0.0064  █
  inst_log_monto_hist                 0.0059  █
  Mes                                 0.0041  
  TamanoProveedorGanador_Ord          0.0030  

[INTERPRETACIÓN]
  El modelo se equivoca en mediana un 40.2% del precio real.
  R²=0.6144 → explica el 61.4% de la varianza del target.
  ⚠ Gap train/test = 0.212 → overfitting moderado.
    Considera reducir max_depth o aumentar min_samples_leaf.

[FEATURES USADAS]
  1. log_MontoEstimado
  2. TipoLicitacion_Ord
  3. sector_LEGISLATIVO
  4. Mes
  5. Trimestre
  6. Anio
  7. EsDiciembre
  8. EsSegundoSemestre
  9. NumOferentes
  10. EsMonopolio
  11. inst_ratio_hist
  12. inst_log_monto_hist
  13. inst_n_licitaciones
  14. inst_oferentes_hist
  15. inst_dias_hist
  16. rubro_log_monto_hist
  17. rubro_ratio_hist
  18. rubro_n_licitaciones
  19. TamanoProveedorGanador_Ord
  20. EsPrecioReferencial
  21. DiasPublicacionAdjudicacion
  22. HayRechazadas
  23. SpreadRelativoOfertas

[NOTA PARA EL INFORME]
  Random Forest captura relaciones no lineales entre features,
  a diferencia de la regresión lineal del baseline.
  La feature importance reemplaza a los coeficientes y muestra
  qué variables el modelo usa más para reducir el error.
  Siguiente paso: LightGBM para comparar rendimiento y velocidad.

============================================================


# Municipalidades

============================================================
REPORTE — REGRESIÓN LINEAL (BASELINE)
Generado: 2026-06-17 16:17:43
============================================================

[DATOS DE ENTRADA]
  Archivo: dataset_features_MUNICIPALIDADES.csv
  Total filas: 401,662

[SPLIT TEMPORAL]
  Train: 321,329 licitaciones (2015-01-02 → 2023-02-03)
  Test:  80,333  licitaciones (2023-02-03 → 2025-12-24)

[MÉTRICAS — TRAIN]
  R² (log):           0.4935
  RMSE (log):         0.7595
  MAE (log):          0.5170
  ─────────────────────────────────
  R² (CLP):           0.0372
  RMSE (CLP):         $61.1M
  MAE (CLP):          $7.3M
  MAPE:               118537.1%
  MdAPE (mediano):    64.2%

[MÉTRICAS — TEST]
  R² (log):           0.4104
  RMSE (log):         0.7702
  MAE (log):          0.4891
  ─────────────────────────────────
  R² (CLP):           0.4607
  RMSE (CLP):         $60.0M
  MAE (CLP):          $12.0M
  MAPE:               131502.5%
  MdAPE (mediano):    57.3%

[INTERPRETACIÓN]
  El modelo se equivoca en mediana un 57.3% del precio real.
  R²=0.4104 significa que el modelo explica el 41.0% de la varianza del target.
  ⚠ R² bajo — esperado para un modelo lineal simple.
    Este número mejorará con Random Forest y LightGBM.

[FEATURES USADAS]
  1. log_MontoEstimado
  2. TipoLicitacion_Ord
  3. sector_MUNICIPALIDADES
  4. Mes
  5. Trimestre
  6. Anio
  7. EsDiciembre
  8. EsSegundoSemestre
  9. NumOferentes
  10. EsMonopolio
  11. inst_ratio_hist
  12. inst_log_monto_hist
  13. inst_n_licitaciones
  14. inst_oferentes_hist
  15. inst_dias_hist
  16. rubro_log_monto_hist
  17. rubro_ratio_hist
  18. rubro_n_licitaciones
  19. TamanoProveedorGanador_Ord
  20. EsPrecioReferencial
  21. DiasPublicacionAdjudicacion
  22. HayRechazadas
  23. SpreadRelativoOfertas

[NOTA PARA EL INFORME]
  Este modelo es el BASELINE. Su función no es predecir bien,
  sino establecer el piso mínimo de rendimiento que los
  modelos más complejos deben superar para justificarse.

============================================================

============================================================
REPORTE — LIGHTGBM
Generado: 2026-06-17 16:21:07
============================================================

[DATOS DE ENTRADA]
  Archivo: dataset_features_MUNICIPALIDADES.csv
  Total filas: 401,662

[PARÁMETROS]
  n_estimators: 500
  learning_rate: 0.05
  num_leaves: 25
  max_depth: 8
  min_child_samples: 40
  subsample: 0.7
  colsample_bytree: 0.5
  reg_alpha: 0.2
  reg_lambda: 0.2
  random_state: 42
  n_jobs: -1
  verbose: -1
  early_stopping_rounds: 50
  árboles usados: 500 (de 500 máximos)

[SPLIT TEMPORAL]
  Train: 321,329 (2015-01-02 → 2023-02-03)
  Test:  80,333 (2023-02-03 → 2025-12-24)

[MÉTRICAS — TRAIN]
  R² (log):           0.7479
  RMSE (log):         0.5359
  MAE (log):          0.3097
  ─────────────────────────────────
  R² (CLP):           0.5926
  RMSE (CLP):         $39.8M
  MAE (CLP):          $4.6M
  MAPE:               35188.3%
  MdAPE (mediano):    33.5%

[MÉTRICAS — TEST]
  R² (log):           0.6646
  RMSE (log):         0.5809
  MAE (log):          0.3089
  ─────────────────────────────────
  R² (CLP):           0.5910
  RMSE (CLP):         $52.3M
  MAE (CLP):          $8.6M
  MAPE:               79023.4%
  MdAPE (mediano):    30.6%

[COMPARACIÓN vs BASELINE (Regresión Lineal)]
  R2_log           Baseline=0.3505  LightGBM=0.6646  ↑ MEJORA (0.3141)
  RMSE_log         Baseline=0.9008  LightGBM=0.5809  ↑ MEJORA (0.3199)
  MdAPE_%          Baseline=66.3000  LightGBM=30.5882  ↑ MEJORA (35.7118)

[COMPARACIÓN vs RANDOM FOREST]
  R2_log           RF=0.5887  LightGBM=0.6646  ↑ MEJORA (0.0759)
  RMSE_log         RF=0.7169  LightGBM=0.5809  ↑ MEJORA (0.1360)
  MdAPE_%          RF=38.1000  LightGBM=30.5882  ↑ MEJORA (7.5118)

[FEATURE IMPORTANCE — TOP 15 (Gain)]
  log_MontoEstimado                   1148692  ████████████████████████████████████████████████████████████████████████████████
  SpreadRelativoOfertas               660929  ██████████████████████████████████████████████
  TipoLicitacion_Ord                  400258  ███████████████████████████
  rubro_log_monto_hist                180675  ████████████
  rubro_ratio_hist                    139825  █████████
  NumOferentes                        84651  █████
  inst_log_monto_hist                 55306  ███
  inst_ratio_hist                     34276  ██
  Anio                                24454  █
  inst_oferentes_hist                 13996  
  inst_dias_hist                      12952  
  EsPrecioReferencial                 10002  
  inst_n_licitaciones                 9670  
  HayRechazadas                       7744  
  rubro_n_licitaciones                7077  

[INTERPRETACIÓN]
  MdAPE: 30.6% (vs 66.3% del baseline)
  R²:    0.6646 (vs 0.3505 del baseline)
  ✓ Gap train/test = 0.083 → generalización aceptable.

[FEATURES USADAS]
  1. log_MontoEstimado
  2. TipoLicitacion_Ord
  3. sector_MUNICIPALIDADES
  4. Mes
  5. Trimestre
  6. Anio
  7. EsDiciembre
  8. EsSegundoSemestre
  9. NumOferentes
  10. EsMonopolio
  11. inst_ratio_hist
  12. inst_log_monto_hist
  13. inst_n_licitaciones
  14. inst_oferentes_hist
  15. inst_dias_hist
  16. rubro_log_monto_hist
  17. rubro_ratio_hist
  18. rubro_n_licitaciones
  19. TamanoProveedorGanador_Ord
  20. EsPrecioReferencial
  21. DiasPublicacionAdjudicacion
  22. HayRechazadas
  23. SpreadRelativoOfertas

============================================================

============================================================
REPORTE — RANDOM FOREST
Generado: 2026-06-17 16:20:31
============================================================

[DATOS DE ENTRADA]
  Archivo: dataset_features_MUNICIPALIDADES.csv
  Total filas: 401,662

[HIPERPARÁMETROS]
  n_estimators: 300
  max_depth: 20
  min_samples_leaf: 8
  max_features: 0.6
  random_state: 42
  n_jobs: -1

[SPLIT TEMPORAL]
  Train: 321,329 licitaciones (2015-01-02 → 2023-02-03)
  Test:  80,333  licitaciones (2023-02-03 → 2025-12-24)

[MÉTRICAS — TRAIN]
  R² (log):           0.8393
  RMSE (log):         0.4278
  MAE (log):          0.2317
  ─────────────────────────────────
  R² (CLP):           0.7313
  RMSE (CLP):         $32.3M
  MAE (CLP):          $3.3M
  MAPE:               9007.5%
  MdAPE (mediano):    22.3%

[MÉTRICAS — TEST]
  R² (log):           0.6666
  RMSE (log):         0.5792
  MAE (log):          0.3057
  ─────────────────────────────────
  R² (CLP):           0.5615
  RMSE (CLP):         $54.1M
  MAE (CLP):          $9.1M
  MAPE:               76876.8%
  MdAPE (mediano):    27.7%

[COMPARACIÓN vs BASELINE (Regresión Lineal)]
  R2_log           Baseline=0.3383  RF=0.6666  ↑ MEJORA (0.3283)
  RMSE_log         Baseline=0.9655  RF=0.5792  ↑ MEJORA (0.3863)
  MdAPE_%          Baseline=70.8000  RF=27.6863  ↑ MEJORA (43.1137)

[FEATURE IMPORTANCE — TOP 15]
  log_MontoEstimado                   0.4859  █████████████████████████████████████████████████████████████████████████████████████████████████
  SpreadRelativoOfertas               0.2529  ██████████████████████████████████████████████████
  TipoLicitacion_Ord                  0.0770  ███████████████
  rubro_log_monto_hist                0.0374  ███████
  rubro_ratio_hist                    0.0240  ████
  NumOferentes                        0.0196  ███
  inst_ratio_hist                     0.0168  ███
  inst_log_monto_hist                 0.0162  ███
  inst_oferentes_hist                 0.0123  ██
  inst_dias_hist                      0.0111  ██
  rubro_n_licitaciones                0.0109  ██
  inst_n_licitaciones                 0.0108  ██
  Anio                                0.0064  █
  DiasPublicacionAdjudicacion         0.0046  
  Mes                                 0.0041  

[INTERPRETACIÓN]
  El modelo se equivoca en mediana un 27.7% del precio real.
  R²=0.6666 → explica el 66.7% de la varianza del target.
  ⚠ Gap train/test = 0.173 → overfitting moderado.
    Considera reducir max_depth o aumentar min_samples_leaf.

[FEATURES USADAS]
  1. log_MontoEstimado
  2. TipoLicitacion_Ord
  3. sector_MUNICIPALIDADES
  4. Mes
  5. Trimestre
  6. Anio
  7. EsDiciembre
  8. EsSegundoSemestre
  9. NumOferentes
  10. EsMonopolio
  11. inst_ratio_hist
  12. inst_log_monto_hist
  13. inst_n_licitaciones
  14. inst_oferentes_hist
  15. inst_dias_hist
  16. rubro_log_monto_hist
  17. rubro_ratio_hist
  18. rubro_n_licitaciones
  19. TamanoProveedorGanador_Ord
  20. EsPrecioReferencial
  21. DiasPublicacionAdjudicacion
  22. HayRechazadas
  23. SpreadRelativoOfertas

[NOTA PARA EL INFORME]
  Random Forest captura relaciones no lineales entre features,
  a diferencia de la regresión lineal del baseline.
  La feature importance reemplaza a los coeficientes y muestra
  qué variables el modelo usa más para reducir el error.
  Siguiente paso: LightGBM para comparar rendimiento y velocidad.

============================================================

# Obras_Publicas

============================================================
REPORTE — REGRESIÓN LINEAL (BASELINE)
Generado: 2026-06-17 16:23:56
============================================================

[DATOS DE ENTRADA]
  Archivo: dataset_features_OBRAS_PUBLICAS.csv
  Total filas: 8,927

[SPLIT TEMPORAL]
  Train: 7,141 licitaciones (2015-01-04 → 2023-04-12)
  Test:  1,786  licitaciones (2023-04-12 → 2025-12-12)

[MÉTRICAS — TRAIN]
  R² (log):           0.4895
  RMSE (log):         0.8406
  MAE (log):          0.4964
  ─────────────────────────────────
  R² (CLP):           0.0532
  RMSE (CLP):         $259.4M
  MAE (CLP):          $23.3M
  MAPE:               289958.5%
  MdAPE (mediano):    54.2%

[MÉTRICAS — TEST]
  R² (log):           0.2252
  RMSE (log):         0.9777
  MAE (log):          0.5448
  ─────────────────────────────────
  R² (CLP):           0.2209
  RMSE (CLP):         $202.5M
  MAE (CLP):          $37.4M
  MAPE:               159552.0%
  MdAPE (mediano):    57.8%

[INTERPRETACIÓN]
  El modelo se equivoca en mediana un 57.8% del precio real.
  R²=0.2252 significa que el modelo explica el 22.5% de la varianza del target.
  ⚠ R² bajo — esperado para un modelo lineal simple.
    Este número mejorará con Random Forest y LightGBM.
  ⚠ Diferencia train/test >0.1 → posible overfitting leve.

[FEATURES USADAS]
  1. log_MontoEstimado
  2. TipoLicitacion_Ord
  3. sector_OBRAS_PUBLICAS
  4. Mes
  5. Trimestre
  6. Anio
  7. EsDiciembre
  8. EsSegundoSemestre
  9. NumOferentes
  10. EsMonopolio
  11. inst_ratio_hist
  12. inst_log_monto_hist
  13. inst_n_licitaciones
  14. inst_oferentes_hist
  15. inst_dias_hist
  16. rubro_log_monto_hist
  17. rubro_ratio_hist
  18. rubro_n_licitaciones
  19. TamanoProveedorGanador_Ord
  20. EsPrecioReferencial
  21. DiasPublicacionAdjudicacion
  22. HayRechazadas
  23. SpreadRelativoOfertas

[NOTA PARA EL INFORME]
  Este modelo es el BASELINE. Su función no es predecir bien,
  sino establecer el piso mínimo de rendimiento que los
  modelos más complejos deben superar para justificarse.

============================================================

============================================================
REPORTE — LIGHTGBM
Generado: 2026-06-17 16:25:03
============================================================

[DATOS DE ENTRADA]
  Archivo: dataset_features_OBRAS_PUBLICAS.csv
  Total filas: 8,927

[PARÁMETROS]
  n_estimators: 500
  learning_rate: 0.05
  num_leaves: 25
  max_depth: 8
  min_child_samples: 40
  subsample: 0.7
  colsample_bytree: 0.5
  reg_alpha: 0.2
  reg_lambda: 0.2
  random_state: 42
  n_jobs: -1
  verbose: -1
  early_stopping_rounds: 50
  árboles usados: 240 (de 500 máximos)

[SPLIT TEMPORAL]
  Train: 7,141 (2015-01-04 → 2023-04-12)
  Test:  1,786 (2023-04-12 → 2025-12-12)

[MÉTRICAS — TRAIN]
  R² (log):           0.7974
  RMSE (log):         0.5295
  MAE (log):          0.3026
  ─────────────────────────────────
  R² (CLP):           0.1244
  RMSE (CLP):         $249.5M
  MAE (CLP):          $16.3M
  MAPE:               5863.3%
  MdAPE (mediano):    35.3%

[MÉTRICAS — TEST]
  R² (log):           0.5352
  RMSE (log):         0.7573
  MAE (log):          0.4161
  ─────────────────────────────────
  R² (CLP):           0.2374
  RMSE (CLP):         $200.4M
  MAE (CLP):          $30.6M
  MAPE:               132460.2%
  MdAPE (mediano):    43.0%

[COMPARACIÓN vs BASELINE (Regresión Lineal)]
  R2_log           Baseline=0.3505  LightGBM=0.5352  ↑ MEJORA (0.1847)
  RMSE_log         Baseline=0.9008  LightGBM=0.7573  ↑ MEJORA (0.1435)
  MdAPE_%          Baseline=66.3000  LightGBM=43.0184  ↑ MEJORA (23.2816)

[COMPARACIÓN vs RANDOM FOREST]
  R2_log           RF=0.5887  LightGBM=0.5352  ↓ EMPEORA (0.0535)
  RMSE_log         RF=0.7169  LightGBM=0.7573  ↓ EMPEORA (0.0404)
  MdAPE_%          RF=38.1000  LightGBM=43.0184  ↓ EMPEORA (4.9184)

[FEATURE IMPORTANCE — TOP 15 (Gain)]
  log_MontoEstimado                   34794  ████████████████████████████████████████████████████████████████████████████████
  SpreadRelativoOfertas               15218  ██████████████████████████████████
  TipoLicitacion_Ord                  9789  ██████████████████████
  rubro_log_monto_hist                6042  █████████████
  rubro_ratio_hist                    3419  ███████
  NumOferentes                        1716  ███
  inst_log_monto_hist                 1522  ███
  inst_dias_hist                      1211  ██
  inst_oferentes_hist                 1163  ██
  rubro_n_licitaciones                1081  ██
  inst_n_licitaciones                 995  ██
  inst_ratio_hist                     869  █
  DiasPublicacionAdjudicacion         791  █
  TamanoProveedorGanador_Ord          579  █
  Anio                                334  

[INTERPRETACIÓN]
  MdAPE: 43.0% (vs 66.3% del baseline)
  R²:    0.5352 (vs 0.3505 del baseline)
  ⚠ Gap train/test = 0.262 → overfitting moderado.
    Considera aumentar min_child_samples o reducir num_leaves.

[FEATURES USADAS]
  1. log_MontoEstimado
  2. TipoLicitacion_Ord
  3. sector_OBRAS_PUBLICAS
  4. Mes
  5. Trimestre
  6. Anio
  7. EsDiciembre
  8. EsSegundoSemestre
  9. NumOferentes
  10. EsMonopolio
  11. inst_ratio_hist
  12. inst_log_monto_hist
  13. inst_n_licitaciones
  14. inst_oferentes_hist
  15. inst_dias_hist
  16. rubro_log_monto_hist
  17. rubro_ratio_hist
  18. rubro_n_licitaciones
  19. TamanoProveedorGanador_Ord
  20. EsPrecioReferencial
  21. DiasPublicacionAdjudicacion
  22. HayRechazadas
  23. SpreadRelativoOfertas

============================================================

============================================================
REPORTE — RANDOM FOREST
Generado: 2026-06-17 16:24:35
============================================================

[DATOS DE ENTRADA]
  Archivo: dataset_features_OBRAS_PUBLICAS.csv
  Total filas: 8,927

[HIPERPARÁMETROS]
  n_estimators: 300
  max_depth: 20
  min_samples_leaf: 8
  max_features: 0.6
  random_state: 42
  n_jobs: -1

[SPLIT TEMPORAL]
  Train: 7,141 licitaciones (2015-01-04 → 2023-04-12)
  Test:  1,786  licitaciones (2023-04-12 → 2025-12-12)

[MÉTRICAS — TRAIN]
  R² (log):           0.7860
  RMSE (log):         0.5442
  MAE (log):          0.2749
  ─────────────────────────────────
  R² (CLP):           0.1189
  RMSE (CLP):         $250.3M
  MAE (CLP):          $14.4M
  MAPE:               24023.4%
  MdAPE (mediano):    25.3%

[MÉTRICAS — TEST]
  R² (log):           0.5014
  RMSE (log):         0.7843
  MAE (log):          0.4041
  ─────────────────────────────────
  R² (CLP):           0.2172
  RMSE (CLP):         $203.0M
  MAE (CLP):          $28.7M
  MAPE:               170779.0%
  MdAPE (mediano):    34.8%

[COMPARACIÓN vs BASELINE (Regresión Lineal)]
  R2_log           Baseline=0.3383  RF=0.5014  ↑ MEJORA (0.1631)
  RMSE_log         Baseline=0.9655  RF=0.7843  ↑ MEJORA (0.1812)
  MdAPE_%          Baseline=70.8000  RF=34.7835  ↑ MEJORA (36.0165)

[FEATURE IMPORTANCE — TOP 15]
  log_MontoEstimado                   0.5217  ████████████████████████████████████████████████████████████████████████████████████████████████████████
  SpreadRelativoOfertas               0.1995  ███████████████████████████████████████
  TipoLicitacion_Ord                  0.0869  █████████████████
  rubro_log_monto_hist                0.0577  ███████████
  rubro_ratio_hist                    0.0226  ████
  rubro_n_licitaciones                0.0167  ███
  inst_log_monto_hist                 0.0124  ██
  inst_dias_hist                      0.0119  ██
  inst_n_licitaciones                 0.0109  ██
  inst_oferentes_hist                 0.0101  ██
  inst_ratio_hist                     0.0098  █
  NumOferentes                        0.0098  █
  DiasPublicacionAdjudicacion         0.0089  █
  TamanoProveedorGanador_Ord          0.0051  █
  EsMonopolio                         0.0046  

[INTERPRETACIÓN]
  El modelo se equivoca en mediana un 34.8% del precio real.
  R²=0.5014 → explica el 50.1% de la varianza del target.
  ⚠ Gap train/test = 0.285 → overfitting moderado.
    Considera reducir max_depth o aumentar min_samples_leaf.

[FEATURES USADAS]
  1. log_MontoEstimado
  2. TipoLicitacion_Ord
  3. sector_OBRAS_PUBLICAS
  4. Mes
  5. Trimestre
  6. Anio
  7. EsDiciembre
  8. EsSegundoSemestre
  9. NumOferentes
  10. EsMonopolio
  11. inst_ratio_hist
  12. inst_log_monto_hist
  13. inst_n_licitaciones
  14. inst_oferentes_hist
  15. inst_dias_hist
  16. rubro_log_monto_hist
  17. rubro_ratio_hist
  18. rubro_n_licitaciones
  19. TamanoProveedorGanador_Ord
  20. EsPrecioReferencial
  21. DiasPublicacionAdjudicacion
  22. HayRechazadas
  23. SpreadRelativoOfertas

[NOTA PARA EL INFORME]
  Random Forest captura relaciones no lineales entre features,
  a diferencia de la regresión lineal del baseline.
  La feature importance reemplaza a los coeficientes y muestra
  qué variables el modelo usa más para reducir el error.
  Siguiente paso: LightGBM para comparar rendimiento y velocidad.

============================================================

# Otros

============================================================
REPORTE — REGRESIÓN LINEAL (BASELINE)
Generado: 2026-06-17 16:27:08
============================================================

[DATOS DE ENTRADA]
  Archivo: dataset_features_OTROS.csv
  Total filas: 12,128

[SPLIT TEMPORAL]
  Train: 9,702 licitaciones (2015-01-02 → 2024-10-25)
  Test:  2,426  licitaciones (2024-10-25 → 2025-12-24)

[MÉTRICAS — TRAIN]
  R² (log):           0.2424
  RMSE (log):         1.0148
  MAE (log):          0.7169
  ─────────────────────────────────
  R² (CLP):           0.0548
  RMSE (CLP):         $93.8M
  MAE (CLP):          $16.0M
  MAPE:               374831.5%
  MdAPE (mediano):    79.9%

[MÉTRICAS — TEST]
  R² (log):           0.2586
  RMSE (log):         0.9523
  MAE (log):          0.6272
  ─────────────────────────────────
  R² (CLP):           0.1063
  RMSE (CLP):         $85.0M
  MAE (CLP):          $26.2M
  MAPE:               1499311.1%
  MdAPE (mediano):    73.0%

[INTERPRETACIÓN]
  El modelo se equivoca en mediana un 73.0% del precio real.
  R²=0.2586 significa que el modelo explica el 25.9% de la varianza del target.
  ⚠ R² bajo — esperado para un modelo lineal simple.
    Este número mejorará con Random Forest y LightGBM.

[FEATURES USADAS]
  1. log_MontoEstimado
  2. TipoLicitacion_Ord
  3. sector_OTROS
  4. Mes
  5. Trimestre
  6. Anio
  7. EsDiciembre
  8. EsSegundoSemestre
  9. NumOferentes
  10. EsMonopolio
  11. inst_ratio_hist
  12. inst_log_monto_hist
  13. inst_n_licitaciones
  14. inst_oferentes_hist
  15. inst_dias_hist
  16. rubro_log_monto_hist
  17. rubro_ratio_hist
  18. rubro_n_licitaciones
  19. TamanoProveedorGanador_Ord
  20. EsPrecioReferencial
  21. DiasPublicacionAdjudicacion
  22. HayRechazadas
  23. SpreadRelativoOfertas

[NOTA PARA EL INFORME]
  Este modelo es el BASELINE. Su función no es predecir bien,
  sino establecer el piso mínimo de rendimiento que los
  modelos más complejos deben superar para justificarse.

============================================================

============================================================
REPORTE — LIGHTGBM
Generado: 2026-06-17 16:27:57
============================================================

[DATOS DE ENTRADA]
  Archivo: dataset_features_OTROS.csv
  Total filas: 12,128

[PARÁMETROS]
  n_estimators: 500
  learning_rate: 0.05
  num_leaves: 25
  max_depth: 8
  min_child_samples: 40
  subsample: 0.7
  colsample_bytree: 0.5
  reg_alpha: 0.2
  reg_lambda: 0.2
  random_state: 42
  n_jobs: -1
  verbose: -1
  early_stopping_rounds: 50
  árboles usados: 181 (de 500 máximos)

[SPLIT TEMPORAL]
  Train: 9,702 (2015-01-02 → 2024-10-25)
  Test:  2,426 (2024-10-25 → 2025-12-24)

[MÉTRICAS — TRAIN]
  R² (log):           0.6015
  RMSE (log):         0.7360
  MAE (log):          0.4725
  ─────────────────────────────────
  R² (CLP):           0.2511
  RMSE (CLP):         $83.5M
  MAE (CLP):          $11.9M
  MAPE:               29979.6%
  MdAPE (mediano):    55.6%

[MÉTRICAS — TEST]
  R² (log):           0.4622
  RMSE (log):         0.8111
  MAE (log):          0.4626
  ─────────────────────────────────
  R² (CLP):           0.2185
  RMSE (CLP):         $79.4M
  MAE (CLP):          $21.0M
  MAPE:               1027358.0%
  MdAPE (mediano):    47.8%

[COMPARACIÓN vs BASELINE (Regresión Lineal)]
  R2_log           Baseline=0.3505  LightGBM=0.4622  ↑ MEJORA (0.1117)
  RMSE_log         Baseline=0.9008  LightGBM=0.8111  ↑ MEJORA (0.0897)
  MdAPE_%          Baseline=66.3000  LightGBM=47.7769  ↑ MEJORA (18.5231)

[COMPARACIÓN vs RANDOM FOREST]
  R2_log           RF=0.5887  LightGBM=0.4622  ↓ EMPEORA (0.1265)
  RMSE_log         RF=0.7169  LightGBM=0.8111  ↓ EMPEORA (0.0942)
  MdAPE_%          RF=38.1000  LightGBM=47.7769  ↓ EMPEORA (9.6769)

[FEATURE IMPORTANCE — TOP 15 (Gain)]
  log_MontoEstimado                   25693  ████████████████████████████████████████████████████████████████████████████████
  SpreadRelativoOfertas               20236  ███████████████████████████████████████████████████████████████
  TipoLicitacion_Ord                  6332  ███████████████████
  rubro_log_monto_hist                4765  ██████████████
  inst_log_monto_hist                 4059  ████████████
  rubro_ratio_hist                    2975  █████████
  inst_dias_hist                      2708  ████████
  inst_n_licitaciones                 2498  ███████
  NumOferentes                        2460  ███████
  inst_oferentes_hist                 2274  ███████
  inst_ratio_hist                     1946  ██████
  rubro_n_licitaciones                1544  ████
  TamanoProveedorGanador_Ord          1006  ███
  Anio                                901  ██
  Mes                                 605  █

[INTERPRETACIÓN]
  MdAPE: 47.8% (vs 66.3% del baseline)
  R²:    0.4622 (vs 0.3505 del baseline)
  ✓ Gap train/test = 0.139 → generalización aceptable.

[FEATURES USADAS]
  1. log_MontoEstimado
  2. TipoLicitacion_Ord
  3. sector_OTROS
  4. Mes
  5. Trimestre
  6. Anio
  7. EsDiciembre
  8. EsSegundoSemestre
  9. NumOferentes
  10. EsMonopolio
  11. inst_ratio_hist
  12. inst_log_monto_hist
  13. inst_n_licitaciones
  14. inst_oferentes_hist
  15. inst_dias_hist
  16. rubro_log_monto_hist
  17. rubro_ratio_hist
  18. rubro_n_licitaciones
  19. TamanoProveedorGanador_Ord
  20. EsPrecioReferencial
  21. DiasPublicacionAdjudicacion
  22. HayRechazadas
  23. SpreadRelativoOfertas

============================================================

============================================================
REPORTE — RANDOM FOREST
Generado: 2026-06-17 16:27:37
============================================================

[DATOS DE ENTRADA]
  Archivo: dataset_features_OTROS.csv
  Total filas: 12,128

[HIPERPARÁMETROS]
  n_estimators: 300
  max_depth: 20
  min_samples_leaf: 8
  max_features: 0.6
  random_state: 42
  n_jobs: -1

[SPLIT TEMPORAL]
  Train: 9,702 licitaciones (2015-01-02 → 2024-10-25)
  Test:  2,426  licitaciones (2024-10-25 → 2025-12-24)

[MÉTRICAS — TRAIN]
  R² (log):           0.6703
  RMSE (log):         0.6695
  MAE (log):          0.4070
  ─────────────────────────────────
  R² (CLP):           0.3177
  RMSE (CLP):         $79.7M
  MAE (CLP):          $10.6M
  MAPE:               25082.4%
  MdAPE (mediano):    46.6%

[MÉTRICAS — TEST]
  R² (log):           0.4597
  RMSE (log):         0.8130
  MAE (log):          0.4501
  ─────────────────────────────────
  R² (CLP):           0.3350
  RMSE (CLP):         $73.3M
  MAE (CLP):          $19.5M
  MAPE:               2515722.2%
  MdAPE (mediano):    43.0%

[COMPARACIÓN vs BASELINE (Regresión Lineal)]
  R2_log           Baseline=0.3383  RF=0.4597  ↑ MEJORA (0.1214)
  RMSE_log         Baseline=0.9655  RF=0.8130  ↑ MEJORA (0.1525)
  MdAPE_%          Baseline=70.8000  RF=42.9960  ↑ MEJORA (27.8040)

[FEATURE IMPORTANCE — TOP 15]
  log_MontoEstimado                   0.3344  ██████████████████████████████████████████████████████████████████
  SpreadRelativoOfertas               0.2644  ████████████████████████████████████████████████████
  TipoLicitacion_Ord                  0.0550  ███████████
  rubro_log_monto_hist                0.0535  ██████████
  inst_log_monto_hist                 0.0450  █████████
  rubro_ratio_hist                    0.0363  ███████
  inst_dias_hist                      0.0326  ██████
  inst_oferentes_hist                 0.0304  ██████
  rubro_n_licitaciones                0.0270  █████
  inst_n_licitaciones                 0.0269  █████
  inst_ratio_hist                     0.0258  █████
  NumOferentes                        0.0214  ████
  Mes                                 0.0112  ██
  TamanoProveedorGanador_Ord          0.0110  ██
  Anio                                0.0094  █

[INTERPRETACIÓN]
  El modelo se equivoca en mediana un 43.0% del precio real.
  R²=0.4597 → explica el 46.0% de la varianza del target.
  ⚠ Gap train/test = 0.211 → overfitting moderado.
    Considera reducir max_depth o aumentar min_samples_leaf.

[FEATURES USADAS]
  1. log_MontoEstimado
  2. TipoLicitacion_Ord
  3. sector_OTROS
  4. Mes
  5. Trimestre
  6. Anio
  7. EsDiciembre
  8. EsSegundoSemestre
  9. NumOferentes
  10. EsMonopolio
  11. inst_ratio_hist
  12. inst_log_monto_hist
  13. inst_n_licitaciones
  14. inst_oferentes_hist
  15. inst_dias_hist
  16. rubro_log_monto_hist
  17. rubro_ratio_hist
  18. rubro_n_licitaciones
  19. TamanoProveedorGanador_Ord
  20. EsPrecioReferencial
  21. DiasPublicacionAdjudicacion
  22. HayRechazadas
  23. SpreadRelativoOfertas

[NOTA PARA EL INFORME]
  Random Forest captura relaciones no lineales entre features,
  a diferencia de la regresión lineal del baseline.
  La feature importance reemplaza a los coeficientes y muestra
  qué variables el modelo usa más para reducir el error.
  Siguiente paso: LightGBM para comparar rendimiento y velocidad.

============================================================

# Salud

============================================================
REPORTE — REGRESIÓN LINEAL (BASELINE)
Generado: 2026-06-17 16:34:24
============================================================

[DATOS DE ENTRADA]
  Archivo: dataset_features_SALUD.csv
  Total filas: 178,514

[SPLIT TEMPORAL]
  Train: 142,811 licitaciones (2015-01-02 → 2022-09-22)
  Test:  35,703  licitaciones (2022-09-22 → 2025-12-24)

[MÉTRICAS — TRAIN]
  R² (log):           0.4255
  RMSE (log):         1.0137
  MAE (log):          0.7308
  ─────────────────────────────────
  R² (CLP):           0.1714
  RMSE (CLP):         $147.0M
  MAE (CLP):          $22.9M
  MAPE:               130085.6%
  MdAPE (mediano):    82.5%

[MÉTRICAS — TEST]
  R² (log):           0.3381
  RMSE (log):         1.1748
  MAE (log):          0.8398
  ─────────────────────────────────
  R² (CLP):           0.2114
  RMSE (CLP):         $216.8M
  MAE (CLP):          $50.2M
  MAPE:               455966.8%
  MdAPE (mediano):    84.7%

[INTERPRETACIÓN]
  El modelo se equivoca en mediana un 84.7% del precio real.
  R²=0.3381 significa que el modelo explica el 33.8% de la varianza del target.
  ⚠ R² bajo — esperado para un modelo lineal simple.
    Este número mejorará con Random Forest y LightGBM.

[FEATURES USADAS]
  1. log_MontoEstimado
  2. TipoLicitacion_Ord
  3. sector_SALUD
  4. Mes
  5. Trimestre
  6. Anio
  7. EsDiciembre
  8. EsSegundoSemestre
  9. NumOferentes
  10. EsMonopolio
  11. inst_ratio_hist
  12. inst_log_monto_hist
  13. inst_n_licitaciones
  14. inst_oferentes_hist
  15. inst_dias_hist
  16. rubro_log_monto_hist
  17. rubro_ratio_hist
  18. rubro_n_licitaciones
  19. TamanoProveedorGanador_Ord
  20. EsPrecioReferencial
  21. DiasPublicacionAdjudicacion
  22. HayRechazadas
  23. SpreadRelativoOfertas

[NOTA PARA EL INFORME]
  Este modelo es el BASELINE. Su función no es predecir bien,
  sino establecer el piso mínimo de rendimiento que los
  modelos más complejos deben superar para justificarse.

============================================================

============================================================
REPORTE — LIGHTGBM
Generado: 2026-06-17 16:35:37
============================================================

[DATOS DE ENTRADA]
  Archivo: dataset_features_SALUD.csv
  Total filas: 178,514

[PARÁMETROS]
  n_estimators: 500
  learning_rate: 0.05
  num_leaves: 25
  max_depth: 8
  min_child_samples: 40
  subsample: 0.7
  colsample_bytree: 0.5
  reg_alpha: 0.2
  reg_lambda: 0.2
  random_state: 42
  n_jobs: -1
  verbose: -1
  early_stopping_rounds: 50
  árboles usados: 474 (de 500 máximos)

[SPLIT TEMPORAL]
  Train: 142,811 (2015-01-02 → 2022-09-22)
  Test:  35,703 (2022-09-22 → 2025-12-24)

[MÉTRICAS — TRAIN]
  R² (log):           0.6567
  RMSE (log):         0.7836
  MAE (log):          0.5211
  ─────────────────────────────────
  R² (CLP):           0.6617
  RMSE (CLP):         $93.9M
  MAE (CLP):          $14.0M
  MAPE:               55803.3%
  MdAPE (mediano):    63.6%

[MÉTRICAS — TEST]
  R² (log):           0.5151
  RMSE (log):         1.0055
  MAE (log):          0.6377
  ─────────────────────────────────
  R² (CLP):           0.6623
  RMSE (CLP):         $141.9M
  MAE (CLP):          $33.8M
  MAPE:               536736.5%
  MdAPE (mediano):    67.3%

[COMPARACIÓN vs BASELINE (Regresión Lineal)]
  R2_log           Baseline=0.3505  LightGBM=0.5151  ↑ MEJORA (0.1646)
  RMSE_log         Baseline=0.9008  LightGBM=1.0055  ↓ EMPEORA (0.1047)
  MdAPE_%          Baseline=66.3000  LightGBM=67.2909  ↓ EMPEORA (0.9909)

[COMPARACIÓN vs RANDOM FOREST]
  R2_log           RF=0.5887  LightGBM=0.5151  ↓ EMPEORA (0.0736)
  RMSE_log         RF=0.7169  LightGBM=1.0055  ↓ EMPEORA (0.2886)
  MdAPE_%          RF=38.1000  LightGBM=67.2909  ↓ EMPEORA (29.1909)

[FEATURE IMPORTANCE — TOP 15 (Gain)]
  log_MontoEstimado                   404037  ████████████████████████████████████████████████████████████████████████████████
  inst_log_monto_hist                 360988  ███████████████████████████████████████████████████████████████████████
  SpreadRelativoOfertas               310358  █████████████████████████████████████████████████████████████
  TipoLicitacion_Ord                  234187  ██████████████████████████████████████████████
  inst_ratio_hist                     86661  █████████████████
  NumOferentes                        72678  ██████████████
  rubro_log_monto_hist                53305  ██████████
  inst_oferentes_hist                 47206  █████████
  rubro_ratio_hist                    42042  ████████
  inst_n_licitaciones                 32807  ██████
  inst_dias_hist                      27056  █████
  rubro_n_licitaciones                14640  ██
  DiasPublicacionAdjudicacion         10326  ██
  TamanoProveedorGanador_Ord          5685  █
  Anio                                5214  █

[INTERPRETACIÓN]
  MdAPE: 67.3% (vs 66.3% del baseline)
  R²:    0.5151 (vs 0.3505 del baseline)
  ✓ Gap train/test = 0.142 → generalización aceptable.

[FEATURES USADAS]
  1. log_MontoEstimado
  2. TipoLicitacion_Ord
  3. sector_SALUD
  4. Mes
  5. Trimestre
  6. Anio
  7. EsDiciembre
  8. EsSegundoSemestre
  9. NumOferentes
  10. EsMonopolio
  11. inst_ratio_hist
  12. inst_log_monto_hist
  13. inst_n_licitaciones
  14. inst_oferentes_hist
  15. inst_dias_hist
  16. rubro_log_monto_hist
  17. rubro_ratio_hist
  18. rubro_n_licitaciones
  19. TamanoProveedorGanador_Ord
  20. EsPrecioReferencial
  21. DiasPublicacionAdjudicacion
  22. HayRechazadas
  23. SpreadRelativoOfertas

============================================================

============================================================
REPORTE — RANDOM FOREST
Generado: 2026-06-17 16:35:25
============================================================

[DATOS DE ENTRADA]
  Archivo: dataset_features_SALUD.csv
  Total filas: 178,514

[HIPERPARÁMETROS]
  n_estimators: 300
  max_depth: 20
  min_samples_leaf: 8
  max_features: 0.6
  random_state: 42
  n_jobs: -1

[SPLIT TEMPORAL]
  Train: 142,811 licitaciones (2015-01-02 → 2022-09-22)
  Test:  35,703  licitaciones (2022-09-22 → 2025-12-24)

[MÉTRICAS — TRAIN]
  R² (log):           0.7829
  RMSE (log):         0.6231
  MAE (log):          0.3963
  ─────────────────────────────────
  R² (CLP):           0.7670
  RMSE (CLP):         $78.0M
  MAE (CLP):          $10.2M
  MAPE:               12189.2%
  MdAPE (mediano):    49.6%

[MÉTRICAS — TEST]
  R² (log):           0.5149
  RMSE (log):         1.0057
  MAE (log):          0.6491
  ─────────────────────────────────
  R² (CLP):           0.4655
  RMSE (CLP):         $178.5M
  MAE (CLP):          $42.6M
  MAPE:               482673.3%
  MdAPE (mediano):    66.6%

[COMPARACIÓN vs BASELINE (Regresión Lineal)]
  R2_log           Baseline=0.3383  RF=0.5149  ↑ MEJORA (0.1766)
  RMSE_log         Baseline=0.9655  RF=1.0057  ↓ EMPEORA (0.0402)
  MdAPE_%          Baseline=70.8000  RF=66.5792  ↑ MEJORA (4.2208)

[FEATURE IMPORTANCE — TOP 15]
  log_MontoEstimado                   0.2664  █████████████████████████████████████████████████████
  inst_log_monto_hist                 0.2411  ████████████████████████████████████████████████
  SpreadRelativoOfertas               0.1822  ████████████████████████████████████
  TipoLicitacion_Ord                  0.0584  ███████████
  inst_ratio_hist                     0.0388  ███████
  inst_oferentes_hist                 0.0317  ██████
  rubro_log_monto_hist                0.0312  ██████
  rubro_ratio_hist                    0.0251  █████
  inst_n_licitaciones                 0.0245  ████
  inst_dias_hist                      0.0230  ████
  NumOferentes                        0.0211  ████
  rubro_n_licitaciones                0.0196  ███
  DiasPublicacionAdjudicacion         0.0112  ██
  Mes                                 0.0062  █
  TamanoProveedorGanador_Ord          0.0053  █

[INTERPRETACIÓN]
  El modelo se equivoca en mediana un 66.6% del precio real.
  R²=0.5149 → explica el 51.5% de la varianza del target.
  ⚠ Gap train/test = 0.268 → overfitting moderado.
    Considera reducir max_depth o aumentar min_samples_leaf.

[FEATURES USADAS]
  1. log_MontoEstimado
  2. TipoLicitacion_Ord
  3. sector_SALUD
  4. Mes
  5. Trimestre
  6. Anio
  7. EsDiciembre
  8. EsSegundoSemestre
  9. NumOferentes
  10. EsMonopolio
  11. inst_ratio_hist
  12. inst_log_monto_hist
  13. inst_n_licitaciones
  14. inst_oferentes_hist
  15. inst_dias_hist
  16. rubro_log_monto_hist
  17. rubro_ratio_hist
  18. rubro_n_licitaciones
  19. TamanoProveedorGanador_Ord
  20. EsPrecioReferencial
  21. DiasPublicacionAdjudicacion
  22. HayRechazadas
  23. SpreadRelativoOfertas

[NOTA PARA EL INFORME]
  Random Forest captura relaciones no lineales entre features,
  a diferencia de la regresión lineal del baseline.
  La feature importance reemplaza a los coeficientes y muestra
  qué variables el modelo usa más para reducir el error.
  Siguiente paso: LightGBM para comparar rendimiento y velocidad.

============================================================






