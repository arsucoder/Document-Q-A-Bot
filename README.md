# 📄 Document Q&A Chatbot

A **Retrieval-Augmented Generation (RAG)** based chatbot that allows users to upload a PDF document and ask questions about its content.

The application extracts text from the uploaded PDF, splits it into smaller chunks, generates embeddings, stores them in an in-memory vector database, retrieves the most relevant sections for each question, and uses a Large Language Model to generate an answer based on the retrieved context.

## 🚀 Features

- 📄 Upload PDF documents
- 🔍 Semantic document search using vector embeddings
- 🤖 AI-powered question answering
- 💬 Interactive Streamlit chat interface
- 🧠 Retrieval-Augmented Generation (RAG)
- 📚 Context-aware answers based on the uploaded document
- 🔐 API keys managed through environment variables
- ⚡ Fast in-memory vector search

## 🏗️ Architecture

```text
                ┌─────────────────┐
                │   Upload PDF    │
                └────────┬────────┘
                         │
                         ▼
                ┌─────────────────┐
                │   PyPDFLoader   │
                └────────┬────────┘
                         │
                         ▼
             ┌───────────────────────┐
             │ Text Chunking         │
             │ RecursiveTextSplitter │
             └──────────┬────────────┘
                        │
                        ▼
             ┌────────────────────────┐
             │ Generate Embeddings    │
             │ Gemini Embeddings      │
             └───────────┬────────────┘
                         │
                         ▼
             ┌────────────────────────┐
             │ InMemoryVectorStore     │
             └───────────┬────────────┘
                         │
                         │ User Question
                         ▼
             ┌────────────────────────┐
             │ Similarity Search       │
             │ Retrieve relevant chunks│
             └───────────┬────────────┘
                         │
                         ▼
             ┌────────────────────────┐
             │ Google Gemini LLM        │
             │ Answer Generation       │
             └───────────┬────────────┘
                         │
                         ▼
                ┌─────────────────┐
                │ Chatbot Response│
                └─────────────────┘
```

## 🛠️ Technologies Used

- **Python**
- **Streamlit** – Web interface
- **LangChain** – LLM and RAG framework
- **Google Gemini** – LLM inference
- **Google Gemini Embeddings** – Text embeddings
- **PyPDFLoader** – PDF document loading
- **InMemoryVectorStore** – Vector storage and similarity search
- **python-dotenv** – Environment variable management

## 💬 How to Use

1. Start the application.
2. Upload a PDF document.
3. Wait for the document to be processed.
4. Ask a question in the chat box.
5. The application searches the document for relevant information.
6. The retrieved context is sent to the Hugging Face LLM.
7. The chatbot generates an answer based on the document.

### Example

Upload a medical document and ask:

```text
What is the name of the patient?
```

The system retrieves the relevant section of the document and generates an answer using the retrieved context.

## 🧠 How RAG Works

This project follows a basic **Retrieval-Augmented Generation** pipeline.

### 1. Document Loading

The uploaded PDF is loaded using `PyPDFLoader`.

### 2. Text Splitting

The extracted text is divided into smaller chunks using:

```python
RecursiveCharacterTextSplitter(
    chunk_size=1000,
    chunk_overlap=200
)
```

Chunking makes it easier to retrieve relevant sections of a large document.

### 3. Embedding Generation

Each document chunk is converted into a numerical vector using Gemini embeddings.

### 4. Vector Storage

The embeddings are stored in an `InMemoryVectorStore`.

### 5. Retrieval

When the user asks a question, the application performs similarity search:

```python
documents = vector_db.similarity_search(
    query,
    k=2
)
```

The two most relevant document chunks are retrieved.

### 6. Generation

The retrieved context and user question are provided to the Hugging Face LLM.

The model generates an answer using the supplied context.

## 📌 Learning Objectives

This project demonstrates how to build a basic RAG application using:

- Document loaders
- Text splitters
- Embeddings
- Vector stores
- Similarity search
- Prompt construction
- Large Language Models
- Streamlit
- LangChain

It is a useful starting point for learning how modern document-based AI assistants work.

## 📜 License

This project is available for educational and personal use.

---

⭐ If you found this project useful, consider giving the repository a star!
```

This version is ready to paste into your repository as `README.md`.
