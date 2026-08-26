# 🧠 AI-Driven Lead Qualification & Routing Engine

Un ecosistema automatizado construido en **n8n** diseñado para capturar, calificar mediante Inteligencia Artificial y enrutar dinámicamente prospectos comerciales (leads) de múltiples canales.

## ⚙️ Arquitectura del Sistema

El proyecto consta de un flujo de trabajo centralizado que procesa los leads en tiempo real:

### 1. 🤖 Smart Lead Triage & Routing
**Archivo:** `03-ai-lead-scoring.json`
Un motor de decisión automatizado que se activa al recibir nuevos registros comerciales.
* **Ingesta Omnicanal:** Captura leads directamente desde **Meta Ads (Facebook Lead Ads)** o como respaldo desde **Google Sheets**.
* **Calificación con IA (Scoring):** Utiliza **OpenRouter (LLMs)** y LangChain para analizar el perfil corporativo del prospecto y determinar si califica como "Empresa Grande" (VIP).
* **Procesamiento y Sanitización:** Emplea **JavaScript** para forzar respuestas en JSON estricto, limpiar alucinaciones del modelo y estandarizar las variables de entrada.
* **Enrutamiento Inteligente:** Segmenta la base de datos (Leads VIP vs. Comunes) y alerta al equipo de ventas vía **Telegram** con resúmenes ejecutivos y deep links (`wa.me`) para contacto inmediato por WhatsApp.

## 🛠️ Stack Tecnológico
* **Orquestación:** n8n, Webhooks, Triggers de Formularios (Meta).
* **IA & LLMs:** OpenRouter API, LangChain (Prompt Engineering).
* **Bases de Datos & APIs:** Meta Ads API, Google Sheets API, Telegram API.
* **Procesamiento:** JavaScript / Node.js (manipulación avanzada de JSON y control de flujo condicional).

## 🚀 Cómo importar este flujo
1. Descarga el archivo `.json` de este repositorio.
2. En tu instancia de n8n, ve a *Workflows* > *Import from File...*
3. Selecciona el archivo descargado.
4. Configura tus credenciales (OpenRouter, Telegram, Google Sheets y Meta Ads) en los nodos correspondientes para activar el sistema.
