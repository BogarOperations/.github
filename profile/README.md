# 🏗️ BoGar - AI-Driven Construction Document Assistant  

BoGar is an AI-powered assistant designed to streamline construction workflows by enabling foremen, field workers, and project managers to interact with construction documents through natural language queries. The system leverages retrieval-augmented generation (RAG), multimodal understanding, and mobile-first access to provide intelligent insights on plans, scopes, and specs.  

---

## 📦 Modules (Aligned with Repositories)  

### 🔐 1. [bogar-access](https://github.com/BogarOperations/bogar-access) — Authentication Management Layer  
Provides authentication and authorization across the entire system via Clerk.dev.  

**Features:**  
- User sign-in, sign-up, token refresh, and logout  
- Role-based access control (Foreman, Field Worker, PM, Management)  
- Secure token issuance for service-to-service communication  
- Syncs user metadata with orchestrator and MongoDB  

**Tech Stack:** Node.js, Clerk SDK, MongoDB  

---

### 📂 2. [bogar-fetch](https://github.com/BogarOperations/bogar-fetch) — External Data Adapter Service  
Connects BoGar with external construction systems and project data sources.  

**Features:**  
- Integrations with File Server (blueprints, scope docs), Accubuild (payroll/accounting), and Basecamp (project threads/tasks)  
- Normalizes incoming data for internal use  
- Supports scheduled and event-driven syncs  
- Triggers catalog/indexing updates on data changes  

**Tech Stack:** Node.js, REST/Webhooks, MongoDB  

---

### 📇 3. [bogar-catalog](https://github.com/BogarOperations/bogar-catalog) — Context Builder & Indexing Service  
Core service for parsing and indexing construction documents into a searchable knowledge base.  

**Features:**  
- Parses PDFs, DWG, images, and structured documents  
- Generates embeddings and stores them in Qdrant  
- Organizes content by project/section for contextual retrieval  
- Monitors source changes and triggers re-indexing  

**Tech Stack:** Python, Qdrant, Unstructured.io, PyMuPDF, LangChain  

---

### 🔧 4. [bogar-services](https://github.com/BogarOperations/bogar-services) — Backend Orchestration / API Layer  
Orchestrator and API gateway for the BoGar ecosystem.  

**Features:**  
- Exposes REST APIs to mobile frontend  
- Manages conversation/session data in MongoDB  
- Token validation via `bogar-access`  
- Connects with:  
  - `bogar-fetch` for synced data  
  - `bogar-iq` for inference responses  
  - `bogar-catalog` for context indexing  

**Tech Stack:** Node.js / Express, MongoDB, Clerk SDK, JWT  

---

### 🧠 5. [bogar-iq](https://github.com/BogarOperations/bogar-iq) — AI Inference & Response Engine  
The intelligence layer powering BoGar’s RAG capabilities.  

**Features:**  
- Retrieves contextual chunks from Qdrant  
- Composes prompts and queries LLMs/VLMs (e.g., OpenAI, CLIP)  
- Handles text and multimodal queries (e.g., image-based)  
- Supports evaluation pipelines and response quality scoring  

**Tech Stack:** Python, FastAPI, HuggingFace Transformers, OpenAI API, CLIP embeddings  

---

### 📱 6. [bogar-app](https://github.com/BogarOperations/bogar-app) — Mobile Application  
The field-facing mobile interface for construction teams.  

**Features:**  
- Built in React Native (Android & iOS)  
- Chat interface to “Ask BoGar” with persisted conversation history  
- Auth via `bogar-access`  
- Displays documents, project data, and tasks  
- Offline support with local caching  
- Native viewer for PDFs, images, and DWG previews  

**Tech Stack:** React Native, Redux, NativeWind (Tailwind), Clerk, Axios  

---
