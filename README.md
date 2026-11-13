# 📚 Multiple PDF Chat Application

An AI-powered PDF question-answering application built using **Streamlit, Google Gemini, LangChain, and FAISS**. Upload multiple PDF documents and interact with their content through natural language queries.

The application uses Retrieval-Augmented Generation (RAG) to retrieve relevant information from uploaded documents and generate context-aware responses using Google Gemini.

## ✨ Features

- **Multiple PDF Upload:** Upload and process multiple PDF documents simultaneously.
- **PDF Text Extraction:** Extract text from PDF documents using PyPDF2.
- **Text Chunking:** Split extracted text into smaller chunks using Recursive Character Text Splitter.
- **Vector Embeddings:** Generate embeddings using Google's Gemini embedding model.
- **Semantic Search:** Retrieve relevant document chunks using FAISS vector similarity search.
- **AI-Powered Responses:** Generate context-aware answers using Google Gemini.
- **Source Tracking:** Display the source PDF filename and page number for retrieved content.
- **Session-Based Storage:** Maintain separate FAISS vector stores for individual Streamlit sessions.
- **Clear Documents:** Clear the current session's processed documents and vector store.

## 🛠️ Tech Stack

| Technology | Purpose |
|---|---|
| Python | Core programming language |
| Streamlit | Interactive web application |
| Google Gemini API | LLM-powered answer generation |
| Gemini Embeddings | Text embedding generation |
| LangChain | RAG pipeline and LLM integration |
| FAISS | Vector storage and similarity search |
| PyPDF2 | PDF text extraction |
| RecursiveCharacterTextSplitter | Document chunking |

## 🏗️ Application Workflow

1. **PDF Upload:** Users upload multiple PDF documents through the Streamlit interface.
2. **Text Extraction:** PyPDF2 extracts text from each PDF while retaining filename and page information.
3. **Text Chunking:** Extracted text is divided into smaller chunks with overlapping content.
4. **Embedding Generation:** Google Gemini generates vector embeddings for the text chunks.
5. **Vector Storage:** FAISS creates a vector store containing document embeddings and metadata.
6. **Question Processing:** Users submit natural language questions about their uploaded documents.
7. **Similarity Search:** FAISS retrieves the four most relevant document chunks.
8. **Answer Generation:** Google Gemini generates an answer using the retrieved context.
9. **Source Display:** The application displays the filenames and page numbers of retrieved chunks.

## 🔄 RAG Architecture

```text
        Multiple PDF Upload
                |
                v
        PDF Text Extraction
             (PyPDF2)
                |
                v
          Text Chunking
    (RecursiveCharacterTextSplitter)
                |
                v
       Gemini Embeddings
                |
                v
         FAISS Vector Store
                |
                v
          User Question
                |
                v
        Similarity Search
          (Top 4 Chunks)
                |
                v
       Retrieved Document Context
                |
                v
         Google Gemini LLM
                |
                v
         Context-Aware Answer
                |
                v
          Streamlit UI
```

## 📂 Project Structure

```text
MultiplePDFChat/
│
├── app.py
├── requirements.txt
├── .env
├── .gitignore
└── README.md
```

## ⚙️ Installation & Setup

### 1. Clone the Repository

```bash
git clone YOUR_GITHUB_REPOSITORY_URL
```

### 2. Navigate to the Project Directory

```bash
cd MultiplePdfChat
```

### 3. Create a Virtual Environment

```bash
python -m venv venv
```

Activate the environment:

**Windows:**
```bash
venv\Scripts\activate
```

**Linux / macOS:**
```bash
source venv/bin/activate
```

### 4. Install Dependencies

```bash
pip install -r requirements.txt
```

### 5. Configure Google Gemini API Key

Obtain an API key from [Google AI Studio](https://aistudio.google.com/).

Create a `.env` file in the project root:

```env
GOOGLE_API_KEY=your_google_api_key
```

Never commit your `.env` file or expose your API key publicly.

### 6. Run the Application

```bash
streamlit run app.py
```

The application will be available locally at:

```text
http://localhost:8501
```

## 🔐 Environment Variables

| Variable | Description |
|---|---|
| GOOGLE_API_KEY | Google Gemini API authentication key |

For cloud deployment, configure this variable through your hosting provider's secrets or environment settings.

## 🧠 Key Implementation Details

### Document Chunking

Uses `RecursiveCharacterTextSplitter` with:

- Chunk Size: 10,000 characters
- Chunk Overlap: 1,000 characters

### Embedding Model

Uses Google's `gemini-embedding-2` model to convert document chunks into vector representations.

### Vector Database

FAISS performs similarity-based retrieval to identify relevant document chunks for a given question.

### Language Model

Google Gemini (`gemini-3.6-flash`) generates answers using the retrieved document context.

### Session-Based Vector Storage

The FAISS vector store is maintained in Streamlit's `st.session_state`, keeping each visitor's processed documents separate during their active session.

The vector store is maintained in memory and is not permanently persisted. Users may need to upload their PDFs again after a session is lost or the application restarts.

## 🚀 Future Improvements

- Docker containerization for consistent deployment.
- Automated CI/CD pipeline using GitHub Actions.
- Persistent vector storage for saved document collections.
- Support for scanned PDFs using OCR.
- Chat history and conversational memory.
- Improved document retrieval and reranking.
- Authentication and user-specific document management.
- Source-based citations in generated answers.

## ⚠️ Limitations

- Currently supports text-extractable PDF documents.
- Scanned PDFs may require OCR processing.
- FAISS indexes are session-based and are not permanently stored.
- Gemini API usage is subject to applicable API quotas and pricing.
- Very large PDF files may require additional memory and processing resources.

## 👨‍💻 Author

**Nishant Singh**

- GitHub: [Niishants](https://github.com/Niishants)

---

⭐ If you find this project useful, consider giving the repository a star!
