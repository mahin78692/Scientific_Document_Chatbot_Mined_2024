# Scientific_Document_Chatbot_Mined_2024
Introducing the Scientific Document Chatbot: your AI-powered research assistant. Upload PDFs, DOCX, or PPTs and ask intelligent questions. Our advanced LLMs understand complex scientific content, delivering precise answers instantly. Save time, gain deeper insights effortlessly. Embrace the future of research assistance today!
# Scientific Document Chatbot (Mined 2024)

Welcome to the Scientific Document Chatbot, an innovative web-based tool designed to interactively 'chat' with your scientific documents. Powered by the Mistral 7B Language Model through the RAG (Retrieval-Augmented Generation) Chain, this chatbot leverages advanced AI to provide insightful answers and facilitate document exploration.

## Dependencies

To set up the project, execute the following commands in the first cell of `final.ipynb` to install all necessary dependencies:

```bash
!pip install -q -U torch datasets transformers tensorflow langchain playwright html2text sentence_transformers faiss-cpu
!pip install -q accelerate==0.21.0 peft==0.4.0 bitsandbytes==0.40.2 trl==0.4.7
!pip install pypdf2
!pip install transformers
!pip install torch
!playwright install
!playwright install-deps
!pip install python-docx
!pip install python-pptx
!pip install gradio
```

# Flow of the Project

## 1. Uploading File

Files can be uploaded in three types: `.pptx`, `.pdf`, and `.docx`. We provide a user-friendly interface using Gradio for seamless file uploads.

## 2. Document-type Detector

We have implemented a document type detector to automatically detect the file extension upon upload.

## 3. Parsing

Once the document type is identified, a specific parser is invoked to process the document content accordingly.

## 4. Chunking

The parsed document is segmented into manageable chunks using the `Langchain.split_text()` function.

## 5. Creating Embeddings and Storing in Vector Stores

Chunks of the document are converted into embeddings using `HuggingFaceEmbeddings` and stored in vector stores for efficient retrieval:

```python
db = FAISS.from_texts(chunked_documents, HuggingFaceEmbeddings(model_name='sentence-transformers/all-mpnet-base-v2'))
retriever = db.as_retriever()
```
An user interface is created by us using Gradio for asking queries which will give answers based on the research document.<br>
## [Demo Video](https://drive.google.com/drive/folders/1IL8-HZMIkE31kj0MQwjccHHEDCDVAxxL?usp=drive_link)
