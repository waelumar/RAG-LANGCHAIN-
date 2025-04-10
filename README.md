# RAG-LANGCHAIN-
a few projectrs built on rag and langchain



# 🤖 PDF Q&A Chatbot using LangChain + Groq + HuggingFace + FAISS

This project allows you to **ask questions about any PDF** document using a powerful **Retrieval-Augmented Generation (RAG)** pipeline built with **LangChain**, **Groq’s LLaMA3 model**, **FAISS**, and **HuggingFace embeddings**.



## 🚀 Features

- 📄 Extracts and splits text from any PDF.
- 🔍 Converts document into semantic vector chunks using HuggingFace embeddings.
- 🧠 Uses FAISS for fast vector similarity search.
- 🗨️ Answers your questions using LLaMA3-8B from Groq API via LangChain's custom LLM integration.



## 🛠️ Tech Stack

| Component        | Tool/Library                            |
|------------------|------------------------------------------|
| Language Model   | [Groq's LLaMA3](https://console.groq.com/) |
| LLM Framework    | [LangChain](https://github.com/langchain-ai/langchain) |
| Embeddings       | [HuggingFace Transformers](https://huggingface.co/sentence-transformers/all-MiniLM-L6-v2) |
| Vector Store     | [FAISS](https://github.com/facebookresearch/faiss) |
| PDF Reader       | [PyPDF2](https://pypi.org/project/PyPDF2/) |


## ⚙️ How It Works

### 1. **PDF/Excel/Text Upload**
- User inputs the path to a PDF file.
- The file is read using `PyPDF2.PdfReader`.

### 2. **Text Splitting**
- The document text is split into manageable chunks using `CharacterTextSplitter`.
- Each chunk is 100 characters long with a 10-character overlap.

### 3. **Embedding & Vectorization**
- Chunks are converted into embeddings using `sentence-transformers/all-MiniLM-L6-v2` via HuggingFace.
- Embeddings are stored in a FAISS vector store.

### 4. **Custom Groq LLM Integration**
- A custom LangChain `LLM` wrapper is created to call Groq's `llama3-8b-8192` model.
- Prompting is handled with a system role and user question.

### 5. **Retrieval-Augmented QA Chain**
- A `RetrievalQA` chain is created using the Groq LLM and FAISS retriever.
- On each user question, relevant text chunks are retrieved and passed to the LLM to generate an answer.



## 🧰 Requirements

Install the following Python libraries:

groq
pydantic
PyPDF2
faiss-cpu
sentence-transformers

## 🔑 Setup API Key

Replace your Groq API key here in the code:

```python
Groq(api_key="your_groq_api_key")
```

