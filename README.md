# ⚡ n8n Workflows & Automations

> Colección de flujos de trabajo inteligentes, integraciones de APIs y automatizaciones con IA desarrolladas en n8n.

---

## 📌 Índice de Proyectos

| # | Proyecto / Flujo | Integraciones principales | Estado |
|---|------------------|---------------------------|--------|
| 01 | [AI-Powered Tech Intelligence Pipeline](./01-tech-intelligence-pipeline) | n8n, OpenRouter (LLMs), RSS, Google Sheets, Telegram | 🟢 Completado |

---

## 🚀 ¿Cómo importar y usar estos flujos?

1. **Elige un proyecto** de la lista superior e ingresa a su carpeta.
2. Descarga o copia el contenido del archivo `workflow.json`.
3. Abre tu instancia de **n8n**.
4. En el menú superior de un nuevo flujo, selecciona **Import from JSON** (o usa el atajo `Ctrl + V` / `Cmd + V`).
5. **Configura las credenciales:** Asigna tus propias claves de API (OpenRouter, Google Sheets OAuth2, Telegram Bot) en los nodos correspondientes.

---

## 🔒 Buenas Prácticas de Seguridad

* Todos los archivos `.json` en este repositorio han sido higienizados y **no contienen credenciales, claves de API ni tokens privados**.
* Se utilizan variables de entorno o marcadores de posición (placeholders) como `TU_API_KEY_AQUI`.

---

## 👤 Autor

Desarrollado por **Andrés Pino**
* **GitHub:** [@pinon8n-gif](https://github.com/pinon8n-gif)  
* **Especialidad:** n8n Developer & AI Automation Engineer
