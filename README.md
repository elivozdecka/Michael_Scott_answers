# Michael_Scott_answers
A Haystack-based RAG system that adapts its output style to imitate Michael Scott, combining factual QA with persona-driven generation.

It retrieves relevant information from an external document and answers questions about it as Michael Scott.
Installation:
Set up: install packages and libraries
!pip install haystack-ai
!pip install "datasets>=2.6.1"
!pip install "sentence-transformers>=4.1.0"
!pip install google-genai-haystack
 
There is a need for a Google Generative AI API key for the generator.
 
 # Implementation:
  The project is implemented as a Retrieval-Augmented Generation (RAG) pipeline using Haystack with the following components:
 
 1. Document Store
     - I use InMemoryDocumentStore to store the knowledge base (documents that Michael Scott can “learn” from).
     - Documents are loaded using TextFileToDocument and wrapped as Document objects.
3. Embeddings
     - SentenceTransformersDocumentEmbedder generates embeddings for documents.
     - SentenceTransformersTextEmbedder generates embeddings for user queries.
3. Retriever
     - InMemoryEmbeddingRetriever retrieves the most relevant documents from the store based on query similarity.
3. Prompt Building
     - ChatPromptBuilder and ChatMessage are used to construct a custom prompt that tells the model to respond in the style of Michael Scott from The Office.
5. Generator
     - I use GoogleGenAIChatGenerator to generate the final response.
     - The generator combines the retrieved context with the Michael Scott–styled prompt to produce the answer.
5. Pipeline
     - All components are connected in a Pipeline.
