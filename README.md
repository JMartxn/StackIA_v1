# StackIA_v1 - Taller Openweb UI montado sobre Docker. Monitorizado en python con RAG reforzado.
En este taller de pruebas, comparé modelos y rendimiento en LM Studio, Anything LLM y Openweb UI.

HERRAMIENTAS EMPLEADAS: Openweb UI,Docling, Python, fundamentalmente.

MONITORIZACION PERSONALIZADA : Para la gestion de Openweb UI, desarrollé con Claude-Sonet 4.6, un monitor en python+ html/css para gestionar actualizaciones, reinicios , etc del sistema de contenedores , de modo transparente para el usuario. 

GESTIÓN DE MODELOS Y CUANTIZACIÓN
Volúmenes Persistencia estricta para índices vectoriales y UI gemma-4-12b-it-q8
qwen2.5:32b deepseek-r1:14b qwen2.5-coder:14b qwen2.5vl (Vision)

AceleraciónNVIDIA Container Toolkit
(Passthrough GPU nativo)Especialización en entornos de ejecución mixtos mediante importación
aya-expanse:8b nativa de formatos GGUF (de LM Studio a Ollama). Modelos embebidos
configurados con bge-m3 y nomic-embed-text para la generación precisa de vectores densos.

# Mi Plataforma de IA Privada

**ON-PREMISE & LOCAL**

Despliegue local de arquitecturas RAG, microservicios autónomos y procesamiento documental sin dependencia externa.

## Pilares y Capacidades

Una suite integral orientada a salvaguardar la privacidad, optimizar el rendimiento por hardware y potenciar la experimentación con LLMs.

## Servicios y Pilares Clave

### Chat IA Local
Interacción directa con modelos de lenguaje grandes (LLMs) de manera 100% privada y segura.

### RAG & Documentos
Generación enriquecida mediante recuperación de información desde bases vectoriales locales.

### Búsqueda Privada
Uso de SearXNG como metabuscador local para consultas sin rastreo de motores comerciales.

## Infraestructura Hardware

**16 GB**
**VRAM en GPU RTX 4060 Ti**

### Potencia de Cálculo Local

Capacidad optimizada para ejecutar localmente la inferencia de modelos medianos y pesados sin estrangular el sistema host.

Soporte de cómputo robusto basado en un procesador **AMD Ryzen 7 7700X** y **32 GB DDR5** de memoria RAM principal.

## Arquitectura de Software

### Inferencia y Control

He configurado Ollama para la inferencia, descarga y orquestación dinámica de múltiples LLMs locales.

La experiencia de usuario se centraliza en Open WebUI como portal unificado, interactivo y con gestión granular.

### Indexación y Búsqueda

Para el núcleo RAG, utilizo la base de datos vectorial Qdrant para indexar rápidamente los vectores o embeddings de texto.

El procesamiento nativo de documentos se asiste con Docling para la extracción fina de datos estructurados.

## Ecosistema de Modelos en Uso

Gama Versátil de LLMs: Modelos optimizados para razonamiento científico y codificación (`gemma3:12b`, `qwen2.5:14b`, `deepseek-r1:14b` y `mistral-small3.2:24b`).

Modelos de Embeddings: Generación estructurada de vectores mediante los motores optimizados `bge-m3` y `nomic-embed-text`.

Pipeline RAG Integrado: Flujo completo de chunking de 1024 tokens, solape de 200 y almacenamiento en BD vectorial.

Observabilidad Activa: Supervisión del estado del stack y GPU con script dedicado en el puerto 8765.

## Análisis del Docker Compose

Desglose y análisis del archivo `compose.yml` que gestiona y aísla el ciclo de vida de los servicios del ecosistema.

## Configuración de Servicios

| Servicio | Imagen de Docker | Puertos Expuestos | Variables de Entorno Clave |
| :--- | :--- | :--- | :--- |
| open-webui | ghcr.io/open-webui:main | 3000:8080 | ENABLE_WEB_SEARCH=true, RAG_EMBEDDING_ENGINE=ollama |
| qdrant | qdrant/qdrant:latest | 6333, 6334 | (Mapeado a puerto local para gRPC y APIs vectoriales) |
| ollama | (Inferencia local) | 11434 | Ubicado en el host e integrado a través de red Docker local |

## Conclusiones de la Infraestructura

He desarrollado una solución basada en microservicios reales que, además de garantizar la soberanía de los datos, posee un alto valor pedagógico al unificar redes Docker, aceleración por hardware (NVIDIA Container Toolkit), persistencia vectorial e IA generativa local.

🛡️ Privacidad de Datos Garantizada On-Premise
