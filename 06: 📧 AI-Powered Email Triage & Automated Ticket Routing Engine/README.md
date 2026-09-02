# 📧 AI-Powered Email Triage & Automated Ticket Routing Engine

Un sistema inteligente de clasificación y enrutamiento de correos electrónicos desarrollado en n8n que combina Modelos de Lenguaje (LLMs) y la API de Gmail para auditar la bandeja de entrada, categorizar solicitudes de soporte o facturación en Trello y eliminar automáticamente el spam[cite: 9].

## ⚙️ Arquitectura del Sistema

El proyecto consta de una canalización integral de triaje y enrutamiento:

1. 📩 Email Ingestion & AI Triage Engine

**Archivo:** `6-workflow.json` Monitoreo activo e inteligencia conversacional para el análisis de correos[cite: 9].

* **Ingesta en Tiempo Real:** Captura correos no leídos en la bandeja de entrada mediante polling continuo en la API de Gmail[cite: 9].
* **Análisis de Lenguaje Natural (LLM):** Utiliza un **AI Agent** conectado a **OpenRouter** para analizar el asunto y cuerpo del mensaje, extrayendo el nombre del cliente, un resumen ejecutivo del problema y categorizando la intención en *Soporte Técnico*, *Facturación* o *Spam*[cite: 9].
* **Sanitización de Datos (ETL):** Ejecuta código en **JavaScript (Node.js)** para limpiar la respuesta del modelo, remover bloques Markdown/JSON y parsear la información en un objeto limpio libre de errores de sintaxis[cite: 9].

2. 🔀 Smart Routing & Automated Actions

**Archivo:** `6-workflow.json` Enrutamiento condicional y ejecución multitarea[cite: 9].

* **Enrutamiento Inteligente:** Evalúa la categoría asignada mediante un nodo **Switch** para bifurcar la ejecución en tiempo real[cite: 9].
* **Gestión de Tickets (Soporte & Facturación):** Genera tarjetas estructuradas automáticamente en tableros de **Trello** con los detalles del cliente, resumen del problema e ID del hilo de Gmail[cite: 9].
* **Mitigación de Spam:** Envía automáticamente las conversaciones clasificadas como publicidad o spam a la papelera de Gmail a través de la API[cite: 9].

## 🛠️ Stack Tecnológico

* **Orquestación:** n8n, Polling Triggers, Enrutamiento Condicional (Switch)[cite: 9].
* **Inteligencia Artificial:** OpenRouter API (LLMs), LangChain Agent, Prompt Engineering[cite: 9].
* **Integraciones & APIs:** Gmail API, Trello API[cite: 9].
* **Procesamiento:** JavaScript (Node.js), JSON Parsing, Sanitización con Regex[cite: 9].

## 🚀 Cómo importar este flujo

1. Descarga el archivo `.json` de este directorio[cite: 9].
2. En tu instancia de n8n, ve a *Workflows > Import from File...*
3. Configura tus credenciales para Gmail, OpenRouter y Trello[cite: 9].
4. Ajusta los IDs de las listas de Trello para tus tableros de Soporte y Facturación[cite: 9].
