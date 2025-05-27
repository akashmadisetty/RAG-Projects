# RAG Projects with Milvus and Groq

This repository contains two implementations of Retrieval-Augmented Generation (RAG) projects, both built from scratch without the use of orchestration libraries like LangChain or LlamaIndex. Both projects utilize Milvus as the vector database and Groq for the Large Language Model (LLM).

## Project Overview

The goal of these projects is to demonstrate different approaches to implementing RAG for question answering or document retrieval tasks.

### Project 1: RAG without HYDE

This project implements a standard RAG pipeline, found in the `RAG` file. It involves:

1.  **Document Loading and Chunking:** Processing raw document into smaller chunks.
2.  **Embedding:** Generating vector embeddings for the document chunks.
3.  **Indexing:** Storing the embeddings in a Milvus vector database.
4.  **Retrieval:** Given a user query, performing a similarity search in Milvus to retrieve relevant document chunks.
5.  **Generation:** Passing the retrieved chunks and the user query to the Groq LLM to generate a response.

### Project 2: RAG with HYDE (Hypothetical Document Embedding)

This project incorporates the HYDE technique, found in the `HYDE` file, to potentially improve retrieval accuracy. The process is similar to Project 1, with an additional step during retrieval:

1.  **Hypothetical Document Generation:** Before performing the vector search, the user query is first passed to the Groq LLM to generate a hypothetical answer or document.
2.  **Embedding the Hypothetical Document:** An embedding is generated for this hypothetical document.
3.  **Retrieval using Hypothetical Embedding:** The embedding of the hypothetical document is then used to perform the similarity search in Milvus to retrieve actual relevant document chunks.
4.  **Generation:** The retrieved chunks and the original user query are passed to the Groq LLM to generate the final response.

## Technologies Used

*   **Milvus:** Used as the vector database for storing and searching document embeddings.
*   **Groq:** Utilized as the Large Language Model for generating responses.
*   **No Orchestration Libraries:** Both implementations are built using core libraries for embedding (e.g., sentence-transformers, OpenAI's embedding models if applicable) and interaction with Milvus and Groq APIs directly, without relying on higher-level RAG frameworks.

## Setup and Usage

1. Create your Groq LLM API Key here https://console.groq.com/keys
