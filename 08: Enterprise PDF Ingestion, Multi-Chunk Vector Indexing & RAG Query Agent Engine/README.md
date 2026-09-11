# 🚀 Enterprise PDF Ingestion, Multi-Chunk Vector Indexing & RAG Query Agent Engine

Un pipeline empresarial automatizado desarrollado en n8n que ingiere documentos PDF de auditoría, realiza fragmentación semántica recursiva, genera embeddings locales, almacena datos en Qdrant y orquesta un agente de consulta RAG en tiempo real sin alucinaciones[cite: 13, 14].

## ⚙️ Arquitectura del Sistema

El proyecto integra un ciclo completo de ingestión de documentos, procesamiento vectorial local y orquestación de agentes con retrieval semántico[cite: 13, 14].

1. 📁 Enterprise PDF Ingestion & Multi-Chunk Vector Indexing

**Archivo:** `Proyecto 8.0_ Enterprise PDF Ingestion & Multi-Chunk Vector Indexing Pipeline.json`[cite: 13]

* **Lectura Local & Ingesta:** Intercepta y lee archivos PDF desde el sistema de archivos local especificando el selector de documentos[cite: 13].
* **Parsing & Chunking Recursivo:** Extrae el contenido binario del PDF y aplica segmentación (*Chunk Size: 1000*, *Overlap: 200*) para preservar la cohesión e integridad del contexto[cite: 13].
* **Vectorización Local e Indexación:** Genera vectores densos de 768 dimensiones mediante Ollama (`nomic-embed-text`) e inserta los registros en la colección `auditorias_internas` dentro de Qdrant[cite: 13].

2. 🧠 Multi-Source RAG Query Agent Engine

**Archivo:** `Proyecto 8.5_ Multi-Source RAG Query Agent with OpenRouter Free Tier & Qdrant Vector Search Engine.json`[cite: 14]

* **Recepción vía Webhook:** Expone una API HTTP POST que intercepta el payload dinámico enviado por el usuario en el parámetro `{{ $json.body.pregunta }}`[cite: 14].
* **Orquestación del Agente IA:** Utiliza un Agente Senior de Auditoría con Prompt de Sistema estricto conectado al modelo de lenguaje en OpenRouter (`openrouter/free`)[cite: 14].
* **Búsqueda Semántica (Retrieval):** El agente consulta la colección en Qdrant utilizando Embeddings homogéneos con Ollama para fundamentar sus respuestas únicamente en los datos cargados[cite: 13, 14].

## 🛠️ Stack Tecnológico

* **Orquestación:** n8n, Webhook POST, Dynamic Manual Triggers[cite: 13, 14].
* **Vector Database:** Qdrant Vector Store (Terminal-Hosted / Instancia Local)[cite: 13, 14].
* **LLM & Embeddings:** OpenRouter API (`openrouter/free`), Ollama Embeddings (`nomic-embed-text`, 768d)[cite: 13, 14].
* **Procesamiento de Datos:** Document DataLoader, PDF Loader, Recursive Character Text Splitter[cite: 13].

## 🚀 Cómo importar este flujo

1. Descarga los archivos `.json` correspondientes al Proyecto 8.0 y 8.5 de este repositorio[cite: 13, 14].
2. En tu instancia de n8n, dirígete a **Workflows > Import from File...** e importa ambos archivos.
3. Configura las credenciales locales para **Ollama API**, **Qdrant API** y **OpenRouter API**[cite: 13, 14].
4. Especifica la ruta del archivo PDF local en el nodo *Read/Write Files* y ejecuta el flujo de ingesta para poblar la base de datos[cite: 13].
5. Activa el Webhook del Agente RAG para comenzar a realizar consultas en tiempo real[cite: 14].
