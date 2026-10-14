# ¿Qué modelos de Groq conviene usar para los agentes?

**Para:** el equipo del Hackathon 7, Caso 3 (Planificador logístico)
**Fuentes:** la página oficial de modelos y la de límites de Groq (`console.groq.com/docs/models` y `/docs/rate-limits`), consultadas el 13/10/2026, y nuestra tabla *Sem9 – Comparación de modelos*.

> ⚠️ Groq cambia su catálogo con frecuencia. El día anterior a la demo hay que revisar `console.groq.com/docs/models` y los límites de la cuenta en `console.groq.com/settings/limits`.

---

## 1. Recomendación

| Agente | Modelo | Por qué |
|---|---|---|
| Analista de operaciones (usa tool) | **`openai/gpt-oss-20b`** | Tiene function calling fiable y es rápido y barato. La tarea es acotada: llamar a la tool y resumir. |
| Planificador | **`openai/gpt-oss-120b`** | Es la tarea que más razonamiento pide: combinar ventanas, capacidad y hora punta. Es el modelo de producción más capaz que ofrece Groq. |
| Evaluador (usa tool) | **`openai/gpt-oss-20b`** | Solo tiene que pasar los planes a la tool y ordenar la tabla. No necesita el modelo grande. |
| Decisor | **`openai/gpt-oss-120b`** | Tiene que ponderar criterios y justificar la decisión. Es la salida que se presenta y se defiende. |

**Por qué alternamos 20b y 120b:** en Groq el límite de **tokens por minuto (TPM)** es **por modelo**. Si alternamos 20b → 120b → 20b → 120b, el consumo se reparte entre dos cuotas, y la demo en vivo tiene menos probabilidad de recibir un error 429.

---

## 2. Modelos de texto que ofrece Groq hoy

| Modelo | Estado | Contexto | Máx. salida | Precio entrada / salida (USD por 1M tokens) | ¿Sirve para nuestros agentes? |
|---|---|---|---|---|---|
| `openai/gpt-oss-120b` | Producción | 131K | 65K | $0.15 / $0.60 | ✅ **Sí: planificador y decisor** |
| `openai/gpt-oss-20b` | Producción | 131K | 65K | $0.075 / $0.30 | ✅ **Sí: analista y evaluador** |
| `llama-3.3-70b-versatile` | Producción | 131K | 32K | "Contact Sales" en la página | ⚠️ No razona. Sirve como alternativa si cae gpt-oss, pero su tool calling es menos consistente. |
| `llama-3.1-8b-instant` | Producción | 131K | 131K | "Contact Sales" en la página | ❌ Es demasiado pequeño para planificar con restricciones. Solo sirve para pruebas rápidas. |
| `qwen/qwen3.8-27b` | **Preview** | 131K | 16K | $0.80 / $4.00 | ❌ Funciona (lo usa el notebook `Sem9_Agente_LangChain`), pero está en *preview*: puede retirarse sin aviso. Además cuesta unas 5 veces más que gpt-oss-120b. |
| `minimaxai/minimax-m2.7` | **Preview** | 196K | 131K | "Contact Sales" | ❌ Es preview y no figura en nuestra tabla comparativa. |
| `openai/gpt-oss-safeguard-20b` | Preview | 131K | 65K | $0.075 / $0.30 | ❌ Es un clasificador de seguridad, no un modelo de chat. Además tiene un límite muy bajo (3 RPM). |
| `meta-llama/llama-prompt-guard-2-*` | Preview | 512 | 512 | $0.03–0.04 | ❌ Solo detecta *prompt injection*. |
| `whisper-large-v3(-turbo)` | Producción | — | — | por hora de audio | ❌ Es para audio, no aplica. |

*Corrección a la auditoría anterior:* `qwen/qwen3.8-27b` **sí existe** en Groq, aunque solo como modelo *preview*.

---

## 3. Límites de uso: lo que más afecta la demo

Valores base que publica Groq para el plan **Developer**. El plan **gratuito** puede tener límites iguales o menores, así que hay que comprobarlos en `/settings/limits`.

| Modelo | Requests/min | Requests/día | **Tokens/min** | Tokens/día |
|---|---|---|---|---|
| `openai/gpt-oss-120b` | 30 | 1 000 | **8 000** | 200 000 |
| `openai/gpt-oss-20b` | 30 | 1 000 | **8 000** | 200 000 |
| `qwen/qwen3.8-27b` | 30 | 1 000 | 8 000 | 200 000 |

**Qué significa para nosotros:**
- Una ejecución de los 4 agentes consume unos **10–20K tokens**, contando los tokens de razonamiento. El límite de **8K tokens por minuto** se alcanza fácilmente, y por eso el notebook:
  - alterna los modelos 20b y 120b;
  - hace una **pausa de 20 s** entre agentes y de **60 s** entre escenarios;
  - fija `reasoning_effort` en *low* (con *medium*, el 120b agotaba los tokens razonando y devolvía respuestas vacías) y limita `max_tokens`;
  - recorta la salida de las tools;
  - configura `num_retries=4` para reintentar si Groq responde 429.
- Con 200K tokens por día y por modelo caben unas **10 a 15 ejecuciones completas al día**. **No hay que ensayar con Groq el día de la demo:** se ensaya con Ollama (`PROVEEDOR_LLM=ollama`) y Groq se deja para la presentación.
- **Conviene tener una key de respaldo** de otro integrante en `GROQ_API_KEY_RESPALDO`.

---

## 4. Por qué gpt-oss y no otro modelo de nuestra tabla comparativa

- En la tabla *Sem9 – Comparación de modelos*, **GPT-oss-20b y GPT-oss-120b** aparecen con *Function Calling: Supported* y *Reasoning: Higher*. Son los únicos modelos de la tabla que Groq sirve en producción con razonamiento.
- La tabla no les asigna precio porque son modelos *open-weight*. En Groq cuestan entre $0.075 y $0.60 por millón de tokens, **más barato que GPT-5-mini ($0.25 / $2.00) o Gemini 2.5 Flash ($0.30 / $2.50)** de la misma tabla. La sección 10 del notebook calcula el costo real por ejecución.
- La propia tabla advierte que los modelos abiertos no actualizan su conocimiento. En nuestro caso eso no importa: todos los datos (pedidos, tiempos) vienen en el prompt y en las tools, no del conocimiento del modelo.

---

## 5. Plan B si Groq falla durante la demo

1. Si aparece un error 429 por TPM, esperar 60 s y volver a ejecutar la celda del escenario.
2. Si se agota la cuota diaria, poner `USAR_RESPALDO = True` en la celda 2.1 y volver a ejecutar desde ahí.
3. Si `gpt-oss-120b` deja de estar disponible, cambiar `MODELO_RAZONADOR = "llama-3.3-70b-versatile"`.
4. Como último recurso, ejecutar con `PROVEEDOR_LLM=ollama`. Según la rúbrica eso vale 2 de 3 puntos, en lugar de 3.
