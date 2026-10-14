### E1 – Por zonas  
**Lógica:** Cada vehículo cubre un bloque geográfico contiguo (Norte, Centro, Oeste).  
**Riesgos:** Si la hora punta se extiende, los viajes que atraviesan la zona norte‑sur pueden verse penalizados; dependencia de que la carga de cada bloque respete la capacidad.  

**PLAN E1 =**  
V1: P07 > P08 > P03 > P04 > P05 > P06 ;  
V2: P01 > P02 > P15 > P13 > P14 > P09 > P10 ;  
V3: P12 > P11  

---

### E2 – Por ventanas  
**Lógica:** Se atienden primero los pedidos con ventana más temprana o de alta prioridad, sin importar la zona.  
**Riesgos:** Los cruces de zonas pueden generar viajes más largos en hora punta; riesgo de sobrecargar al vehículo que recibe los pedidos tardíos.  

**PLAN E2 =**  
V1: P07 > P03 > P01 > P12 ;  
V2: P05 > P08 > P09 > P02 > P13 > P04 > P06 > P15 ;  
V3: P10 > P11 > P14  

---

### E3 – Híbrida (vehículo dedicado a Callao + recarga a mediodía)  
**Lógica:** Un vehículo (V3) se dedica exclusivamente a Callao; V1 realiza dos salidas con recarga intermedia para repartir la carga pesada de la mañana y la tarde; V2 cubre el resto.  
**Riesgos:** La recarga intermedia añade 20 min extra y puede acercarse al límite de tiempo de regreso; V3 queda expuesto a la congestión de la ruta a Callao en hora punta.  

**PLAN E3 =**  
V3: P12 > P11 ;  
V1: P07 > P03 > P01 ; ALM ; P05 > P08 > P13 > P14 > P15 ;  
V2: P02 > P04 > P06 > P09 > P10  