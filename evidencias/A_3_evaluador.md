## Tabla comparativa de estrategias

| Estrategia | Factible | Costo S/ | Km | Último regreso | Pedidos fuera de ventana | Complejidad | Riesgo |
|------------|----------|----------|----|----------------|--------------------------|-------------|--------|
| **E1** | ❌ INFACTIBLE | 725.03 (penalidades 90) | 158.0 | 17:30 | P03 (+45 min, alta), P05 (+90 min, normal), P13 (+80 min, normal), P09 (+215 min, normal) | **Alta** (3 vehículos, 1 recarga, 3 cruces zona‑norte‑sur) | **Alto** (holgura insuficiente en ventana alta, tramos en hora punta, regreso 17:30) |
| **E2** | ✅ FACTIBLE | 776.07 (penalidades 0) | 236.0 | 16:50 | Ninguno | **Media** (3 vehículos, 0 recarga, 2 cruces zona‑norte‑sur) | **Medio** (holgura adecuada, tramos en hora punta moderados, regreso 16:50) |
| **E3** | ❌ INFACTIBLE | 559.24 (penalidades 30) | 162.0 | 15:50 | P09 (+115 min, normal) | **Media** (3 vehículos, 1 recarga, 1 vehículo dedicado a Callao) | **Alto** (recarga intermedia, riesgo de congestión Callao, regreso 15:50) |

---

## Observaciones por estrategia

### E1 – Por zonas  
- **Infactibilidad**: P03, P05, P13 y P09 exceden sus ventanas de entrega, con P03 siendo de alta prioridad.  
- **Costo**: 725.03 S/ (incluye penalidades de 90 S/).  
- **Riesgo**: Cruces de zona norte‑sur en hora punta y falta de holgura para pedidos de alta prioridad.  
- **Complejidad**: 3 vehículos, 1 recarga, 3 cruces de zona.

### E2 – Por ventanas  
- **Factible**: No hay pedidos fuera de ventana.  
- **Costo**: 776.07 S/ (sin penalidades).  
- **Riesgo**: Tramos en hora punta moderados; último regreso a las 16:50, lo que deja margen de seguridad.  
- **Complejidad**: 3 vehículos, sin recargas, 2 cruces de zona norte‑sur.

### E3 – Híbrida  
- **Infactibilidad**: P09 excede su ventana (115 min). Además, la herramienta indica bloques sin vehículo (`ALM` y la secuencia de pedidos después de la recarga).  
- **Costo**: 559.24 S/ (penalidades 30 S/).  
- **Riesgo**: Recarga intermedia añade 20 min extra y la ruta a Callao puede verse afectada por congestión.  
- **Complejidad**: 3 vehículos, 1 recarga, 1 vehículo dedicado a Callao.

---

## Ranking preliminar según objetivo (minimizar costo sin incumplir alta prioridad)

1. **E2** – Factible, sin penalidades, costo 776.07 S/.  
2. **E3** – Menor costo total (559.24 S/) pero infactible por incumplimiento de ventana y bloques sin vehículo.  
3. **E1** – Infactible y con penalidades altas (90 S/).  

> **Conclusión**: La única estrategia que cumple con la política de no incumplir pedidos de alta prioridad es **E2**. Las estrategias **E1** y **E3** deben ser revisadas o descartadas.