# Desarrollo de un Sistema de Generación Aumentada por Recuperación (RAG) para la Consulta y Auditoría de Normativas Internacionales de Inteligencia Artificial.

Trabajo de Fin de Máster (TFM) en Deep Learning — Universidad Politécnica de Madrid (UPM).

## Descripción del Proyecto
Implementación de un Sistema de Generación Aumentada por Recuperación (RAG) diseñado para consultar y auditar el Reglamento Europeo de Inteligencia Artificial (AI Act). El sistema prioriza la precisión normativa y la trazabilidad.

## Arquitectura
La arquitectura está dividida en 3 cuadernos de experimentación (`/Notebooks`):
1. **Fase 1 (Ingesta):** Limpieza, normalización y segmentación de textos normativos en español (LangChain).
2. **Fase 2 (Indexación Vectorial):** Modelos Bi-Encoder (`BAAI/bge-m3`, `MiniLM`) y persistencia en ChromaDB, combinado con índices léxicos (BM25).
3. **Fase 3 (Orquestación y Evaluación):** - **HybM-CE:** Fusión de recuperadores mediante Reciprocal Rank Fusion (RRF) y reordenamiento de alta precisión con **Cross-Encoder**.
   - **Generación:** LLaMA 3.1 8B (vía Ollama local).
   - **XAI:** Análisis de atribución post-hoc mediante técnica de perturbación por oclusión.
   - **Evaluación:** Framework LLM-as-a-judge midiendo Faithfulness, Answer Relevancy, Context Precision y Context Recall.

## Reproducibilidad y Entorno
El proyecto está diseñado para ejecutarse en hardware local de consumo probado en GPU de 4GB VRAM.

```bash
git clone [https://github.com/eduardapologallardo-web/TFM-RAG-AI-Act-Auditor.git](https://github.com/eduardapologallardo-web/TFM-RAG-AI-Act-Auditor.git)
cd TFM-RAG-AI-Act-Auditor
python -m venv env_tfm
# En Windows:
env_tfm\Scripts\activate
pip install -r requirements.txt