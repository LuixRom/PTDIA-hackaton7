# Diagnóstico Operativo – 13 Oct 2026

| Distrito | Pedidos | Kg | Ventana más temprana | Cierre más temprano | Alta |
|----------|---------|----|----------------------|---------------------|------|
| Barranco | P13,P14 | 180 | 11:00 | 14:00 | – |
| Callao   | P11,P12 | 450 | 10:00 | 12:00 | P12 |
| La Molina| P07,P08 | 310 | 08:30 | 10:30 | P07 |
| Miraflores| P01,P02,P15 | 260 | 09:00 | 12:00 | P01 |
| SJL      | P09,P10 | 420 | 09:00 | 13:00 | – |
| San Isidro| P03,P04 | 350 | 09:00 | 11:00 | P03 |
| Surco    | P05,P06 | 270 | 08:30 | 12:00 | – |

**Carga total**: 2 240 kg.  
**Capacidad de la flota**: 2 600 kg por salida (V1 + V2 + V3).  
**Salidas mínimas**: 1 (capacidad suficiente para toda la carga).  

## Pedidos críticos  
- **P07** (La Molina, 08:30‑10:30, alta) – ventana corta y alta.  
- **P03** (San Isidro, 09:00‑11:00, alta) – ventana corta y alta.  
- **P01** (Miraflores, 09:00‑12:00, alta) – ventana amplia pero alta.  
- **P12** (Callao, 10:00‑12:00, alta) – ventana media y alta.  

## Agrupaciones geográficas sugeridas  
1. **Miraflores + Barranco** – 10 min entre distritos.  
2. **San Isidro + La Molina** – 12 min entre distritos.  
3. **Surco + SJL** – 15 min entre distritos.  
4. **Callao** – aislado, pero cercano a San Isidro (35 min).  

Estas agrupaciones minimizan los desplazamientos y respetan las ventanas de los pedidos críticos.

## Alertas de datos  
- No se detectaron inconsistencias en los datos de pedidos, flota ni restricciones.  
- La carga total (2 240 kg) es inferior a la capacidad total de la flota (2 600 kg), por lo que una sola salida es viable.  

**Conclusión**: Con una sola salida, asignando los pedidos críticos a la primera ruta y agrupando los distritos según proximidad, se cumple la política de no incumplir pedidos de alta prioridad y se minimiza el costo total.