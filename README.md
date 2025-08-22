# n8n-document-rag-pipeline
An automated RAG pipeline in n8n to chat with documents from Google Drive using Gemini, and Pinecone.

# Drive-to-Chat RAG Pipeline

This project is an automated Retrieval-Augmented Generation (RAG) pipeline built in n8n. It ingests documents from Google Drive, indexes them in a Pinecone vector database, and allows a user to ask questions about them through a conversational AI agent powered by Google Gemini.

---

## 🎥 Video Demo



https://github.com/user-attachments/assets/f6cd9bdb-9d71-40b3-8a69-48905b7db752



---

## ⚙️ Project Architecture

This project consists of two core n8n workflows that work in tandem:

### 1. `aws cloud rag` (Data Ingestion Pipeline)
This workflow is the automated backend that processes and learns new information.

* **Trigger:** Activates when a new file is uploaded to a specific Google Drive folder.
* **Process:** It downloads the document, splits it into chunks, generates vector embeddings via Google Gemini, and indexes them in our Pinecone knowledge base.

![Data Ingestion Workflow]<img width="1440" height="900" alt="Data injestion aws cloud rag" src="https://github.com/user-attachments/assets/08fe3bff-2295-4a43-8c97-73633b0bef07" />


### 2. `aws-n8n-rag-operate` (Conversational AI Agent)
This workflow powers the user-facing chat interface and handles the query process.

* **Trigger:** Executes when a user sends a message.
* **Process:** The AI agent retrieves relevant context from Pinecone, combines it with the user's question, and uses Google Gemini to generate an intelligent, source-grounded answer.

![AI Agent Workflow]<img width="1440" height="900" alt="AI agent aws n8n rag operate" src="https://github.com/user-attachments/assets/90fa73c5-c280-4d46-ae5c-15e9b233f381" />


---

## 🛠️ Technology Stack

* **Automation:** n8n (self-hosted via Docker)
* **Vector Database:** Pinecone
* **AI Models:** Google Gemini (for both embeddings and chat generation)
* **Data Source:** Google Drive
* **Core Concept:** Retrieval-Augmented Generation (RAG)
