# RAG-Based Q&A Chatbot Web Page Integrated with Langchain and Hugging Face 

This project is a Q&A Chatbot Web Page built using the Streamlit library, integrated with Langchain and Hugging Face to enable natural language querying of documents. Users can interact with the chatbot by uploading their documents and asking questions, with the chatbot providing context-aware answers based on the content.

## Key Features

1. LLM Integration with Multiple Providers:
   Users can select from multiple Large Language Model (LLM) providers such as OpenAI, Google Generative AI, or Hugging Face by inputting their respective API keys.

2. Configurable LLM Parameters:
   Users can set parameters such as temperature and top_p to fine-tune the LLM's response behavior.

3. Multiple Retriever Options:
   The project provides three types of retrievers:
   - Vector Store-Backed Retriever
   - Contextual Compression Retriever
   - Cohere Reranker

4. Document Upload & Processing:
   Users can upload files in various formats, including CSV, PDF, TXT, and DOCX. After uploading, the documents are processed and stored in a Chroma Vector Store (a vector database library). The vector store can be saved locally for efficient retrieval and reuse.

## Running The App Locally
1. Install Dependencies
   Run the command:

   	    pip install -r requirements.txt

2. Start the Application
   Run the command below in the terminal:

       streamlit run RAG_app.py

3. Configure the LLM Provider:
   Select your desired LLM provider in the sidebar, adjust its parameters, and insert the appropriate API keys.

4. Create or Load a Chroma Vector Store:
   Upload your documents and configure the vector store for efficient document querying.

5. Chat with Your Documents:
   Ask questions, and the chatbot will provide context-based answers using the integrated retriever and LLM.

## Project Architecture:

This Q&A system follows a Retrieval-Augmented Generation (RAG) architecture, which consists of two main blocks:

1. Document Processing Block:
   - Document Loader: Upload external files (CSV, PDF, TXT, DOCX).
   - Text Splitter: Split long documents into smaller chunks for better processing.
   - Vector Store: Create embeddings for document chunks and store them in the Chroma Vector Store.
   - Retriever: Retrieve similar documents based on the query.
  
2. Response Generation Block:
   - Language Model (LLM): Communicates with the retriever to answer queries using the retrieved documents.
   - Memory & Prompt Templates: Maintain conversation history and construct prompts for more context-aware responses.
  
## RAG Workflow:
1. Standalone Question Generation:
   - The input question is reformulated based on chat history and context using the LLM.

2. Document Retrieval:
   - The reformulated query is matched against the vector store to retrieve relevant document chunks.

3. Prompt Augmentation:
   - The retrieved documents are combined with the standalone query and chat history to create a comprehensive LLM prompt.

4. Response Generation:
   - The LLM generates a context-aware answer using the augmented prompt.

5. Memory Update:
   - The chat history is updated with the user's question and the AI's response, maintaining context for follow-up queries.

## Example Workflow
Imagine the chatbot is interacting with a dataset of user reviews for a music application, like Spotify. The user might ask:

    "What features do users like most about Spotify app?"

The chatbot retrieves relevant documents from the vector store, summarizes them, and respond with:

    "Users appreciate several features and aspects of the Spotify application, including:

    1. Custom-Made Playlists: Spotify offers personalized playlists based on users' listening history and preferences, making music discovery a delightful experience.
    2. Radio Stations from ANYTHING: Users can create radio stations from any song, artist, or genre, allowing for endless music exploration.
    3. User Experience and Design: Spotify's intuitive and user-friendly interface, along with its seamless navigation, provides an exceptional user experience.
    
    These features, along with Spotify's continuous innovation, make it a top choice for music enthusiasts."

If the follow-up question is:

    "Which music streaming service is our app most often compared to?"

The LLM reformulates this question and replaces the "our app" phrases with "Spotify", and retrieves relevant documents to provide an informed answer like:

    "Users frequently compare Spotify with Apple Music due to its extensive music library and similar features."

## Web Interface Preview

This project provides an interactive, context-aware Q&A system that allows users to extract insights from their documents using a combination of retrieval and language models. With customizable parameters and a user-friendly interface, it offers an intuitive way to query documents and get meaningful answers.

![UI Screenshot](https://github.com/wiryanatasunardi/QnA-Chatbot/blob/main/data/docs/screenshots/WEB_UI.png)

![Prompt Example](https://github.com/wiryanatasunardi/QnA-Chatbot/blob/main/data/docs/screenshots/Prompt_Response.png)
