# 🤖 01 - AI-Powered Tech Intelligence Pipeline: Automated RSS Curation & Scoring

Sistema automatizado de vigilancia e inteligencia de contenido tecnológico. El flujo extrae noticias vía feeds RSS en intervalos programados, limpia los datos mediante scripts personalizados, procesa y califica la relevancia del contenido usando modelos de lenguaje (OpenRouter LLMs), almacena el historial estructurado en Google Sheets y notifica las novedades más relevantes en tiempo real a Telegram.

---

## 🛠️ Arquitectura del Pipeline

El flujo está estructurado en 4 etapas principales:

1. **[ETAPA 1] Ingesta & Data Cleansing:**
   * **Schedule Trigger:** Ejecución cronometrada periódica.
   * **RSS Read:** Lectura automática de fuentes (ej. MIT Technology Review).
   * **Remove Duplicates:** Filtrado de entradas repetidas por título.
   * **JavaScript Code Node:** Limpieza y normalización de texto.

2. **[ETAPA 2] AI-Powered Curation Engine:**
   * **LangChain / OpenRouter Chat Model:** Evaluación del impacto del artículo.
   * Generación de análisis en español, scoring (1 al 10) y recomendaciones en JSON.

3. **[ETAPA 3] Smart Routing & Data Processing:**
   * **Edit Fields (Code):** Parsing defensivo del JSON de la IA.
   * **Sort & Limit:** Ordenamiento por mayor puntuación.

4. **[ETAPA 4] Data Destination & Storage:**
   * **Google Sheets:** Guardado de registros estructurados.
   * **Telegram Bot:** Envío inmediato de alertas en Markdown.

---

## 📥 Instrucciones de Importación

1. Descarga el archivo `workflow.json` de esta carpeta.
2. Abre tu n8n, crea un nuevo flujo e importa el archivo `.json`.
3. Vincula tus credenciales de OpenRouter, Google Sheets y Telegram.
