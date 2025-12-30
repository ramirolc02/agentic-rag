# Agentic RAG for Estimation of Distribution Algorithms

[Master Thesis](https://oa.upm.es/90999/1/TFM_RAMIRO_LOPEZ_CENTO.pdf)

<div align="center">
  <img src="https://github.com/user-attachments/assets/8cec3a14-0eb1-4fe5-b531-678ba9bdafac" />
</div>

An agentic Retrieval-Augmented Generation (RAG) system following the ReAct paradigm, where an LLM iteratively reasons, retrieves evidence, and invokes tools over OCR-processed scientific documents, enabling contextual, grounded question answering for algorithmic research domains.

# Architecture 
<div align="center">
  <img width="639" height="289" alt="image" src="https://github.com/user-attachments/assets/8b096165-dfb0-4b53-88ba-77135bc4be14" />
</div>

# 🏗️ Repository Structure

```
agentic-rag/
├── chainlit/              # Agentic RAG execution and user interface
├── mistral-ocr/          # Raw data extraction and processing scripts
├── data/                 # PDF knowledge database
└── README.md
```

### 📁 Directory Overview

#### `/chainlit/`
Contains the core Agentic RAG system with interactive user interface:
- **Purpose**: Main application for document querying and AI-powered responses
- **Features**: Interactive chat interface, document retrieval, and intelligent answer generation
- **Technology**: Built with Chainlit for seamless UI/UX

#### `/mistral-ocr/`
Houses data processing and extraction scripts:
- **Purpose**: Convert raw PDF documents into structured, searchable format
- **Features**: OCR processing, image extraction, markdown conversion
- **Technology**: Powered by Mistral AI's OCR capabilities
- **Output**: Processed documents ready for RAG ingestion

#### `/data/`
Centralized repository for source documents:
- **Purpose**: Storage for all PDF files used in the knowledge database
- **Content**: Research papers, documents, and reference materials
- **Format**: PDF files that get processed by the OCR pipeline
---

# Evals 

### Embedding Models 

<div align="center">
   <img width="612" height="340" alt="image" src="https://github.com/user-attachments/assets/3780b986-c05a-48cd-9dd5-780243dc30a2" />
</div>
  
### Chunking Strategies
<div align="center">
   <img width="612" height="379" alt="image" src="https://github.com/user-attachments/assets/c3b785c3-b1c8-4f59-bb6e-22c63cba2ec6" />
</div>

### LLM-as-a-judge

<div align="center">
   <img width="631" height="311" alt="image" src="https://github.com/user-attachments/assets/18a3f610-4d13-4e3c-9f56-dd9511217572" />
</div>


