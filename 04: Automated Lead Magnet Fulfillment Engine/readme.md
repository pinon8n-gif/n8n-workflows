# ⚡ Automated Lead Magnet Fulfillment & Notification Engine

Un pipeline avanzado construido en **n8n** que captura prospectos en tiempo real, valida estrictamente sus datos de contacto y automatiza la entrega de recursos digitales (Lead Magnets), protegiendo la base de datos contra inyecciones de spam.

## ⚙️ Arquitectura del Sistema

El flujo de trabajo opera bajo una estructura de validación estricta antes de ejecutar cualquier acción de cumplimiento:

### 1. 🛡️ Ingestión, Limpieza y Control de Errores
**Archivo:** `04-lead-magnet-fulfillment.json`
* **Captura en Tiempo Real:** Recibe payloads a través de un Webhook configurado para peticiones POST[cite: 7].
* **Sanitización y Validación:** Ejecuta código JavaScript personalizado para limpiar los datos (trimming, lowercase) y aplica una validación Regex para confirmar la legitimidad del correo electrónico[cite: 7].
* **Exception Handler (Protección Anti-Spam):** Un nodo de enrutamiento condicional evalúa la validez del contacto[cite: 7]. Si el formato es incorrecto, el sistema rechaza la solicitud y devuelve de forma nativa un código de error HTTP 400 (Bad Request) en formato JSON[cite: 7].

### 2. 🚀 Fulfillment & Distribución Omnicanal
Una vez que el prospecto supera la barrera de validación, el sistema ejecuta las acciones de entrega:
* **Registro Dinámico:** Almacena o actualiza (Upsert) el registro del lead en una base de datos de Google Sheets[cite: 7].
* **Extracción de Recursos:** Realiza una petición HTTP GET para descargar en memoria el archivo binario del Lead Magnet (PDF)[cite: 7].
* **Despacho Automatizado:** Envía un correo electrónico personalizado de bienvenida con el documento adjunto utilizando la API de Gmail[cite: 7].
* **Alertas de Alta Prioridad:** Dispara una notificación instantánea al equipo comercial mediante un bot de Telegram informando la captura exitosa[cite: 7].

## 🛠️ Stack Tecnológico
* **Orquestación:** n8n, Webhooks (POST Requests & Webhook Responses).
* **Lógica & Procesamiento:** JavaScript / Node.js (Regex, Sanitización, Control Booleano).
* **Bases de Datos & APIs:** Google Sheets API, Gmail API, Telegram API.
* **Manejo de Archivos:** HTTP Requests (Procesamiento de binarios en memoria).

## 🚀 Cómo importar este flujo
1. Descarga el archivo `.json` de este repositorio.
2. En tu instancia de n8n, ve a *Workflows* > *Import from File...*
3. Selecciona el archivo descargado.
4. Configura tus credenciales (Google OAuth2, Gmail OAuth2 y Telegram Bot) en los nodos correspondientes para activar el sistema[cite: 7].
