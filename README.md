# StackIA_v1 🚀
> **Taller OpenWebUI sobre Docker:** Monitorización en Python con RAG reforzado y soberanía de datos 100% On-Premise.

Este proyecto nace como un entorno de pruebas para comparar el rendimiento de modelos en **LM Studio**, **AnythingLLM** y **OpenWebUI**, consolidando una plataforma privada, eficiente y escalable.

---

## 🛠️ Herramientas y Stack Tecnológico

* **Interfaz y Orquestación:** OpenWebUI (Portal unificado e interactivo).
* **Procesamiento Documental:** Docling (Extracción fina de datos estructurados).
* **Motor de Inferencia:** Ollama (Gestión dinámica e importación nativa GGUF desde LM Studio).
* **Base de Datos Vectorial:** Qdrant (Indexación rápida de embeddings).
* **Meta-buscador Privado:** SearXNG (Consultas web sin rastreo comercial).
* **Monitorización Personalizada:** Dashboard desarrollado en *Python + HTML/CSS* para la gestión transparente de actualizaciones, estados del stack y reinicios de contenedores (Puerto `8765`).

---

## 🏗️ Arquitectura del Sistema y Capacidades

### 🧩 Pilares Clave
1.  **Chat IA Local:** Interacción directa con LLMs de manera 100% privada y segura.
2.  **RAG de Alto Rendimiento:** Flujo completo con *chunking* de 1024 tokens, solape (*overlap*) de 200 y almacenamiento indexado.
3.  **Privacidad Absoluta:** Arquitectura de microservicios autónomos sin dependencias ni fugas de datos externas.

### 💻 Infraestructura de Hardware
* **GPU:** NVIDIA RTX 4060 Ti (16 GB VRAM) con aceleración **NVIDIA Container Toolkit** (Passthrough GPU nativo).
* **CPU:** AMD Ryzen 7 7700X
* **RAM:** 32 GB DDR5

---

## 🤖 Ecosistema de Modelos en Uso

| Tipo de Modelo | Modelos Desplegados / Cuantizados | Notas de Configuración |
| :--- | :--- | :--- |
| **Razonamiento y Lógica** | `deepseek-r1:14b` | Razonamiento avanzado profundo. |
| **Modelos Generales y Código**| `gemma-4-12b-it-q8`, `qwen2.5:32b`, `qwen2.5-coder:14b`, `mistral-small3.2:24b` | Inferencia mixta y desarrollo local. |
| **Visión** | `qwen2.5vl` | Procesamiento multimodal local. |
| **Embeddings** | `bge-m3`, `nomic-embed-text` | Generación precisa de vectores densos. |

---

## 🐳 Análisis del Despliegue (Docker Compose)

El ciclo de vida, aislamiento y red de los servicios clave se gestionan mediante el archivo `compose.yml`:

| Servicio | Imagen de Docker | Puertos Expuestos | Variables de Entorno Clave / Notas |
| :--- | :--- | :--- | :--- |
| **`open-webui`** | `ghcr.io/open-webui:main` | `3000:8080` | `ENABLE_WEB_SEARCH=true`<br>`RAG_EMBEDDING_ENGINE=ollama` |
| **`qdrant`** | `qdrant/qdrant:latest` | `6333`, `6334` | Mapeado local para APIs vectoriales y comunicación gRPC. |
| **`ollama`** | *(Inferencia Local)* | `11434` | Ubicado en el host, integrado mediante la red local de Docker y con persistencia estricta de volúmenes. |

---

## 🛡️ Conclusiones de la Infraestructura

**StackIA_v1** demuestra la viabilidad de desplegar entornos de IA generativa profesional en local. Al unificar redes de Docker, persistencia vectorial estricta y aceleración por hardware nativa, se logra una solución que no solo **garantiza la soberanía absoluta de los datos**, sino que además posee un alto valor pedagógico para la experimentación de entornos híbridos de IA.
