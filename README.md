# ⚡ n8n Workflows & Automations

> Colección de flujos de trabajo inteligentes, integraciones de APIs y automatizaciones con IA desarrolladas en n8n.

---

## 📌 Índice de Proyectos

| # | Proyecto / Flujo | Integraciones principales | Estado |
|---|---|---|---|
| 01 | [AI-Powered Tech Intelligence Pipeline](./01-tech-intelligence) | n8n, OpenRouter (LLMs), RSS, Google Sheets, Telegram | 🟢 Completado |
| 02 | [AI-Powered Sports Analytics & Broadcaster System](./02-sports-analytics) | n8n, API REST (football-data), OpenRouter (LLMs), Google Sheets, Telegram | 🟢 Completado |
| 03 | [AI-Driven Lead Qualification & Routing Engine](./03-lead-scoring) | n8n, Meta Ads, OpenRouter (LLMs), Google Sheets, Telegram, Node.js | 🟢 Completado |
| 04 | [Automated Lead Magnet Fulfillment & Notification Engine](./04-lead-magnet-fulfillment) | n8n, Webhooks, Google Sheets, Gmail, Telegram, Node.js (Regex) | 🟢 Completado |
| 05 | [Automated B2B CRM-to-Billing Pipeline](./05-crm-stripe-billing) | n8n, HubSpot API, Stripe API, Node.js (Regex) | 🟢 Completado |
| 06 | *Proyecto 6 (Arquitectura en desarrollo)* | *Definiendo herramientas...* | 🟡 En proceso |

---

## 🚀 ¿Cómo importar y usar estos flujos?

1. Elige un proyecto de la lista superior e ingresa a su carpeta.
2. Descarga o copia el contenido del archivo `workflow.json`.
3. Abre tu instancia de n8n.
4. En el menú superior de un nuevo flujo, selecciona **Import from JSON** (o usa el atajo `Ctrl + v` / `Cmd + v`).
5. **Configura las credenciales:** Asigna tus propias claves de API en los nodos correspondientes.

---

## 🔒 Buenas Prácticas de Seguridad

* Todos los archivos `.json` en este repositorio han sido higienizados y no contienen credenciales, claves de API ni tokens privados.
* Se utilizan variables de entorno o marcadores de posición (placeholders) como `TU_API_KEY_AQUI`.

---

## 👤 Autor

Desarrollado por **Andrés Pino**

* **GitHub:** [@pinon8n-gif](https://github.com/pinon8n-gif)
* **Especialidad:** n8n Developer & AI Automation Engineer
