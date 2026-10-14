## Tabla comparativa de las estrategias

| Estrategia | Factible | Costo S/ | Km | Último regreso | Fuera de ventana | Complejidad | Riesgo |
|------------|----------|----------|----|----------------|------------------|-------------|--------|
| **E1** | ❌ INFACTIBLE | 742.17 (penalidades 30) | 248.0 | 17:08 | P09 (+50 min, normal) | **Alta** (2 vehículos, 2 recargas, 2 cruces de ciudad) | **Alto** (holgura mínima, regreso antes de 19:00, tramos en hora punta) |
| **E2** | ✅ | 838.03 (penalidades 60) | 279.0 | 18:45 | P09 (+51 min, normal), P10 (+53 min, normal) | **Media** (2 vehículos, 2 recargas, 2 cruces de ciudad) | **Medio** (holgura moderada, regreso antes de 19:00, tramos en hora punta) |
| **E3** | ✅ | 691.03 (penalidades 90) | 201.0 | 16:55 | P13 (+75 min, normal), P02 (+125 min, normal), P09 (+50 min, normal) | **Baja** (2 vehículos, 2 recargas, 1 cruce de ciudad) | **Bajo** (holgura amplia, regreso temprano, sin tramos en hora punta) |

---

## Observaciones por estrategia

### E1
- **Infactible**: Falta asignar el pedido **P10** y el último regreso es a las 17:08, antes de la ventana de alta prioridad.
- **Penalidades**: 30 S/ por pedidos fuera de ventana (solo P09).
- **Carga**: V1 excede la capacidad máxima (950 kg de 1000 kg) y espera 62 min; V3 excede la capacidad máxima (400 kg de 600 kg) y espera 131 min.
- **Riesgo**: Alta exposición a hora punta y falta de holgura para pedidos de alta prioridad.

### E2
- **Factible**: Todos los pedidos asignados, pero 2 pedidos (P09 y P10) salen fuera de ventana.
- **Penalidades**: 60 S/ por los pedidos fuera de ventana.
- **Carga**: V1 casi alcanza la capacidad (820 kg de 1000 kg) con espera mínima; V3 excede la capacidad (510 kg de 600 kg) y espera 188 min.
- **Riesgo**: Moderado; último regreso a 18:45, justo antes de la hora punta, con holgura limitada.

### E3
- **Factible**: Todos los pedidos asignados, aunque 3 pedidos (P13, P02, P09) salen fuera de ventana.
- **Penalidades**: 90 S/ por los pedidos fuera de ventana.
- **Carga**: V1 y V3 operan dentro de sus límites de capacidad y con esperas razonables (127 min y 61 min respectivamente).
- **Riesgo**: Bajo; último regreso a 16:55, con holgura suficiente y sin tramos en hora punta.

---

## Ranking preliminar según el objetivo de la gerencia

1. **E3** – Menor costo total y menor número de entregas fuera de ventana, con riesgo operativo bajo.  
2. **E2** – Factible pero con mayor número de entregas fuera de ventana y penalidades más altas que E3.  
3. **E1** – Infactible, por lo que no se considera viable bajo el objetivo de servicio.