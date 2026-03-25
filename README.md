# 🧠 Multimodal AI Assistant: The All-in-One Intelligence Hub

A state-of-the-art Multimodal AI application developed in **Google Colab** and deployed via **Gradio**. This project combines Retrieval-Augmented Generation (RAG) with generative media capabilities, allowing users to interact with AI through text, images, and voice.

## 🚀 Key Features
- **Document Intelligence (RAG):** Upload PDFs or images (OCR) to create a private knowledge base. Chat with your documents using **LangChain** and **Cohere Embeddings**.
- **Generative Art:** Built-in **Stable Diffusion v1.4** pipeline for high-quality Text-to-Image generation.
- **Vision Capabilities:** Image-to-Text captioning using **ViT-GPT2** to describe visual content.
- **Voice Interface:** - **Speech-to-Text (STT):** Powered by Google Speech Recognition.
  - **Text-to-Speech (TTS):** Powered by `gTTS` for natural voice responses.
- **Dual Chat Modes:** Switch between a "Normal Chat" (General Knowledge) and "RAG Chat" (Document-specific knowledge).

## 🛠️ The Tech Stack
- **Frameworks:** LangChain, Gradio, PyTorch
- **LLMs & APIs:** Cohere (Command-R), Google Gemini (via LangChain)
- **Computer Vision:** OpenCV, PIL, Tesseract OCR, HuggingFace Transformers
- **Audio:** Pydub, SpeechRecognition, gTTS
- **Vector Database:** ChromaDB (for persistent document storage)
- **Deployment:** Google Colab with GPU (CUDA) acceleration

## 📂 System Architecture


1. **Ingestion:** PDF/Image data is extracted and chunked using `RecursiveCharacterTextSplitter`.
2. **Vectorization:** Chunks are converted into 1024-dimensional embeddings using Cohere's `embed-english-v3.0`.
3. **Storage:** Embeddings are stored in a **ChromaDB** vector store for fast semantic search.
4. **Retrieval:** When a user asks a question, the system retrieves the most relevant document chunks.
5. **Generation:** The Cohere `command-r` model synthesizes a final answer based strictly on the retrieved context.

## ⚙️ Setup & Installation
Since this project relies on GPU-heavy models like Stable Diffusion, it is optimized for **Google Colab**.

1. **Open the Notebook:** Import the `.ipynb` file into Google Colab.
2. **Hardware Accelerator:** Go to `Edit > Notebook Settings` and select **T4 GPU**.
3. **Install Dependencies:**
   ```bash
   !pip install -U gradio langchain chromadb cohere diffusers transformers accelerate gtts
   !sudo apt-get install tesseract-ocr
