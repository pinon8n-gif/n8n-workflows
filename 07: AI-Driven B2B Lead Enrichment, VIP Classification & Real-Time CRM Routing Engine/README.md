# 🚀 AI-Driven B2B Lead Enrichment, VIP Classification & Real-Time CRM Routing Engine

Un pipeline empresarial automatizado desarrollado en n8n que intercepta leads en tiempo real, los enriquece con datos firmográficos mediante Apollo.io, evalúa su valor estratégico con Inteligencia Artificial y ejecuta la sincronización en HubSpot CRM junto con alertas prioritarias en Slack.

## ⚙️ Arquitectura del Sistema

El proyecto integra un ciclo completo de enriquecimiento, calificación inteligente y enrutamiento omnicanal:

1. 🔍 Ingestion & B2B Data Enrichment Engine

**Archivo:** `7-workflow.json` Captura en tiempo real y enriquecimiento de datos corporativos.

* **Captura en Tiempo Real:** Intercepta la carga útil de prospectos mediante un nodo **Webhook** de entrada.
* **Enriquecimiento Firmográfico:** Realiza una petición **HTTP Request** a la API de **Apollo.io** para obtener datos clave de la organización (número de empleados, industria y país).

2. 🧠 AI Qualification & Defensive Parsing Engine

**Archivo:** `7-workflow.json` Clasificación con LLM y capa de resiliencia en JavaScript.

* **Evaluación Inteligente (LLM):** Un modelo de lenguaje en **OpenRouter** analiza la firma de la empresa aplicando reglas estrictas para categorizar al prospecto como *High Value* (más de 50 empleados o sectores clave como Software, Tech o Finanzas) o *Low Value*.
* **Sanitización & Fallback:** Un nodo de código en **JavaScript** utiliza expresiones regulares (**Regex**) para extraer el bloque JSON de la respuesta de la IA y cuenta con un bloque de contingencia para evitar fallos por alucinaciones del modelo.

3. 🔀 Smart CRM Routing & Omnichannel Alerts

**Archivo:** `7-workflow.json` Bifurcación condicional y sincronización de datos.

* **Enrutamiento Condicional:** Evalúa la clasificación resultante mediante un nodo **If**.
* **Actualización en HubSpot:** Crea o actualiza el contacto en **HubSpot CRM** asignando sus propiedades corporativas y el razonamiento dictaminado por la IA.
* **Notificaciones VIP:** Para leads clasificados como *High Value*, dispara una alerta en tiempo real en un canal de **Slack** para la atención inmediata del equipo de ventas enterprise.

## 🛠️ Stack Tecnológico

* **Orquestación:** n8n, Webhooks, Condicionales (If Node).
* **Enriquecimiento & APIs:** Apollo.io API (Match Endpoint).
* **Inteligencia Artificial:** OpenRouter API (LLMs), LangChain Chain Engine, Prompt Engineering.
* **CRM & Notificaciones:** HubSpot API (Contacts Management), Slack API.
* **Procesamiento:** JavaScript (Node.js), Regex Parsing, Error Handling.

## 🚀 Cómo importar este flujo

1. Descarga el archivo `.json` de este directorio.
2. En tu instancia de n8n, ve a *Workflows > Import from File...*
3. Configura tus credenciales para Apollo.io, OpenRouter, HubSpot y Slack.
4. Ajusta el canal de Slack y las propiedades personalizadas de HubSpot según tu entorno.
