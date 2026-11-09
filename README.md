# Agentic RAG System using LangGraph & Groq

Un système de **RAG Agentique (Retrieval-Augmented Generation)** autonome et gratuit, construit avec **LangGraph**, **LangChain**, **Groq** (`llama-3.3-70b-versatile`) et **HuggingFace Embeddings** en local avec **ChromaDB**.

Ce projet permet à un agent intelligent de décider dynamiquement quand interroger une base documentaire vectorielle privée (documents PDF) pour répondre précisément à des requêtes complexes sur les initiatives stratégiques et projets d'IA des entreprises.

---

## Fonctionnalités

- **Workflow Agentique (LangGraph)** : Boucle de décision autonome (LLM Node $\rightarrow$ Tool Node $\rightarrow$ Conditional Edge) pour exécuter des outils dynamiquement.
- **Inférence Ultra-Rapide (Groq API)** : Utilisation de `llama-3.3-70b-versatile` pour le raisonnement et le *tool calling*.
- **Embeddings Locals & Gratuits** : Vectorisation via `sentence-transformers/all-MiniLM-L6-v2` (HuggingFace) sans coût d'API.
- **Vector Store Local (ChromaDB)** : Indexation et recherche par similarité sémantique.
- **Gestion Robuste des PDF** : Extraction et découpage de documents avec gestion de la tolérance aux erreurs de flux PDF (`silent_errors`).

---

##  Architecture du Workflow

```mermaid
graph TD
    START([START]) --> Agent[Agent Node / LLM]
    Agent --> ShouldContinue{Outil Nécessaire ?}
    ShouldContinue -- Oui --> Tools[Tool Node / Retriever]
    Tools --> Agent
    ShouldContinue -- Non --> END([END])


    🛠️ Stack Technique
Framework Agentique : LangGraph, LangChain

LLM Provider : Groq (llama-3.3-70b-versatile)

Embeddings : HuggingFace (sentence-transformers/all-MiniLM-L6-v2)

Base Vectorielle : ChromaDB

Document Loading & Splitting : PyPDFDirectoryLoader, RecursiveCharacterTextSplitter

 Installation & Configuration
1. Cloner le dépôt

git clone [https://github.com/votre-username/nom-du-repo.git](https://github.com/votre-username/nom-du-repo.git)
cd nom-du-repo
2. Créer un environnement virtuel et installer les dépendances

python -m venv .venv
source .venv/bin/activate  # Sur Linux/macOS
# .venv\Scripts\activate   # Sur Windows

pip install langchain-groq langchain-huggingface sentence-transformers chromadb pypdf langgraph
3. Variables d'environnement
Créez un fichier .env à la racine du projet ou définissez votre clé API Groq :

GROQ_API_KEY="votre_cle_api_groq"
Structure du Projet
├── ressources/                # Fichiers PDF sources pour le RAG
│   └── *.pdf
├── notebooks/
│   ├── Notebook_1_Agent_LangGraph.ipynb
│   └── Tp6_RAG_Agentique.ipynb
├── .env                       # Variables d'environnement
├── README.md                  # Documentation du projet
└── requirements.txt           # Dépendances Python
📄 Licence
Ce projet est sous licence MIT.


---

### 💡 Description courte (pour l'en-tête GitHub / « About »)
Si tu cherches juste le texte court à mettre dans la case **About** sur la page principale du dépôt GitHub :

> **Agentic RAG pipeline built with LangGraph, Groq (Llama 3.3 70B), HuggingFace Embeddings, and ChromaDB for intelligent PDF document retrieval.**