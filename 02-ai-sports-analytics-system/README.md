# 🏆 AI-Powered Sports Analytics & Broadcaster System

Un ecosistema automatizado construido en **n8n** diseñado para gestionar, analizar y reportar partidos de fútbol (enfocado en el Mundial 2026). El sistema se divide en dos flujos interconectados que combinan bases de datos, Inteligencia Artificial y consumo de APIs deportivas en tiempo real.

## ⚙️ Arquitectura del Sistema

El proyecto consta de dos flujos de trabajo (Workflows) principales:

### 1. 🎙️ AI Sports Broadcaster (Match Previews)
**Archivo:** `01-ai-sports-preview.json`
Un narrador deportivo automatizado que se ejecuta todas las mañanas (8:00 AM).
* **Ingesta de Datos:** Consulta el calendario de partidos del día en Google Sheets.
* **Análisis con IA:** Utiliza **OpenRouter (LLMs)** y LangChain para redactar una previa táctica y emocionante del partido, como un periodista deportivo real.
* **Distribución:** Actualiza la base de datos con el análisis generado y envía una alerta visual con la previa, hora y canal de TV a un canal de **Telegram**.

### 2. 📊 Real-Time Sports Analytics (Result Engine)
**Archivo:** `02-realtime-sports-results.json`
Un motor de extracción de datos que se ejecuta al final de la jornada (9:00 PM).
* **Extracción HTTP:** Realiza un request a la API REST de `football-data.org` para obtener los marcadores oficiales de los partidos del día.
* **Transformación (ETL):** Procesa el JSON de respuesta utilizando **JavaScript** y el nodo Split Out para normalizar los datos de cada equipo y sus goles.
* **Actualización:** Mapea los resultados exactos y actualiza las filas correspondientes en Google Sheets.
* **Reporte Final:** Construye un resumen dinámico de la jornada y lo envía por **Telegram**.

## 🛠️ Stack Tecnológico
* **Orquestación:** n8n, Webhooks, Cron Jobs (Schedule Trigger).
* **IA & LLMs:** OpenRouter API, LangChain (Prompt Engineering).
* **Bases de Datos & APIs:** Google Sheets API, API REST (`football-data.org`), Telegram Bot API.
* **Procesamiento:** JavaScript, manipulación avanzada de JSON.

## 🚀 Cómo importar estos flujos
1. Descarga los archivos `.json` de este directorio.
2. En tu instancia de n8n, ve a *Workflows* > *Import from File...*
3. Configura tus propias credenciales para Google Sheets, Telegram y OpenRouter.
4. Ajusta los IDs de las hojas de cálculo y el `chatId` de tu bot de Telegram.
