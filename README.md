# 🏗️ BoGar - AI-Driven Construction Document Assistant

BoGar is an AI-powered assistant designed to streamline construction workflows by enabling foremen, field workers, and project managers to interact with construction documents through natural language queries. The system leverages retrieval-augmented generation (RAG), multimodal understanding, and mobile-first access to provide intelligent insights on plans, scopes, and specs.

---

## 📦 Modules

### 1. **Authentication**
- Uses [Clerk.dev](https://clerk.dev) for secure, scalable authentication.
- Enables role-based access for field users, foremen, PMs, and management.

### 2. **Mobile App (React Native)**
- Built using React Native to support both Android and iOS.
- Features:
  - AskBoGar Chatbot: AI QnA assistant
  - Conversation history (local + persisted)
  - Auth integration and offline support
  - Native document viewer (PDF, image, DWG previews)

### 3. **Backend Orchestrator**
- Built in Node.js / Express (or applicable framework)
- Manages data flow between the mobile app, vector DB, and AI engine
- Components:
  - MongoDB (data persistence)
  - Task automation triggers
  - Sync engine for real-time & daily updates

### 4. **AI Engine**
- RAG-based pipeline combining:
  - File parser (PDFs, images, CAD, and structured docs)
  - Vector DB (Qdrant or Pinecone)
  - Multimodal LLM/VLM (e.g., InternVL or custom fine-tuned models)
- Handles queries via text/image + document context

---
