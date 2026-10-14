# Diagnóstico Operativo – 13 Oct 2026

| Distrito | Pedidos | Kg | Ventana más temprana | Cierre más temprano | Alta prioridad |
|----------|---------|----|----------------------|---------------------|----------------|
| Barranco | P13,P14 | 180 | 11:00 | 14:00 | – |
| Callao   | P11,P12,P16 | 600 | 09:30 | 11:30 | P12,P16 |
| La Molina| P07,P08 | 310 | 08:30 | 10:30 | P07 |
| Miraflores| P01,P02,P15 | 260 | 09:00 | 12:00 | P01 |
| SJL      | P09,P10 | 420 | 09:00 | 13:00 | – |
| San Isidro| P03,P04,P17 | 440 | 09:00 | 11:00 | P03,P17 |
| Surco    | P05,P06 | 270 | 08:30 | 12:00 | – |

**Total**: 17 pedidos, 2 480 kg.

---

## 2. Capacidad frente a demanda  
- **Vehículos disponibles**: V1 (1 000 kg) + V3 (600 kg) = **1 600 kg por salida**.  
- **Carga total**: 2 480 kg → **mínimo 2 salidas** (1 600 kg + 880 kg).  
- **Recarga necesaria**: Sí, al menos una recarga en almacén (20 min) antes de la segunda salida.  
- **Capacidad restante en segunda salida**: 880 kg (≈ 58 % de V1 + V3).

---

## 3. Pedidos críticos  
- **Alta prioridad**: P01, P03, P07, P12, P16, P17.  
- **Ventana cerrada ≤ 11:00**: P01, P03, P07, P12, P16, P17.  
- **Urgentes (entraron 07:30)**: P16, P17.  
- **Conclusión**: Todos los pedidos críticos deben ser atendidos en la primera salida para evitar penalidades y garantizar el nivel de servicio.

---

## 4. Agrupaciones geográficas sugeridas  
| Grupo | Distritos | Distancia media (min) | Comentario |
|-------|-----------|-----------------------|------------|
| **A** | Miraflores, Barranco, San Isidro | 10–12 min | Muy cercanos, pueden agruparse en una ruta única. |
| **B** | La Molina, Surco | 20 min | Distancia media 20 min, ruta separada. |
| **C** | Callao | 35–40 min | Distancia mayor, ruta propia. |
| **D** | SJL | 30–45 min | Ruta independiente. |

**Recomendación**:  
1. **Salida 1**: Grupo A (P01, P03, P07, P12, P16, P17, P13, P14, P11).  
2. **Recarga**: 20 min en ALM.  
3. **Salida 2**: Grupos B, C y D (P02, P15, P05, P06, P08, P09, P10).  

---

## 5. Alertas de datos  
- **V2** está en mantenimiento; no se incluye en la capacidad.  
- **P16 y P17** son urgentes; su ventana se superpone a la hora punta (08:00‑09:30), lo que incrementa el tiempo de viaje en 1.4×.  
- No se detectaron inconsistencias en los datos de pedidos, flota ni restricciones.