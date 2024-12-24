
# **MediQuery AI**

MediQuery AI is a chatbot designed to answer medical queries with precision and speed. Leveraging **Sentence Transformers** for semantic search, **Pinecone** for efficient vector storage and retrieval, and **Streamlit** for an intuitive user interface, this project provides accurate and contextually relevant answers to healthcare-related questions.

---

## **Project Features**

1. **Semantic Search**:
   - Uses state-of-the-art embeddings to find answers based on the meaning of user queries.
2. **Dynamic Query Refinement**:
   - Refines ambiguous or incomplete queries using OpenAI's GPT-3.5 model.
3. **Real-time Chat Interface**:
   - An interactive chatbot built with Streamlit and Streamlit Chat.
4. **Scalability**:
   - Pinecone ensures fast and efficient similarity searches even with large datasets.

---

## **Technologies Used**

- **Python**: Backend processing and integration.
- **Streamlit**: Frontend for user interaction.
- **Sentence Transformers**: For semantic embeddings.
- **Pinecone**: A vector database for storing and searching embeddings.
- **OpenAI GPT-3.5**: For query refinement and enhanced context understanding.
- **NLTK**: Text preprocessing (optional, if enabled).

---

## **Project Goals**

1. Provide a scalable and accurate chatbot for answering medical queries.
2. Integrate advanced semantic search for relevant responses.
3. Enable a user-friendly web-based interface for interaction.
4. Ensure the project can handle large datasets with minimal latency.

---

## **File Structure**
```
mediquery-ai/
├── backend.py           # Backend logic for dataset processing and Pinecone integration
├── main.py              # Streamlit application for chatbot UI
├── utils.py             # Utility functions for query refinement and embeddings
├── requirements.txt     # Required Python dependencies
├── README.md            # Project documentation
└── icliniq_medical_qa_2.csv  # Medical Q&A dataset (or use a provided link)
```

---

## **Setup Instructions**

### **Step 1: Clone the Repository**
First, clone the repository to your local machine:
```bash
git clone https://github.com/<your-username>/mediquery-ai.git
cd mediquery-ai
```

---

### **Step 2: Create a Virtual Environment**
To ensure a clean environment, create and activate a Python virtual environment:

#### For Windows:
```bash
python -m venv env
env\Scripts\activate
```

#### For macOS/Linux:
```bash
python3 -m venv env
source env/bin/activate
```

---

### **Step 3: Install Dependencies**
Install the required libraries using `requirements.txt`:
```bash
pip install -r requirements.txt
```

If `requirements.txt` is not available, install dependencies manually:
```bash
pip install streamlit sentence-transformers langchain langchain-community pinecone-client tqdm pandas openai nltk
```

---

### **Step 4: Configure Pinecone**
#### **Step 4.1: Create a Pinecone Account**
1. Sign up at [Pinecone.io](https://www.pinecone.io/).
2. Create an API key and note down your **API key** and **region**.

#### **Step 4.2: Update Pinecone Configuration**
Update the `backend.py` and `utils.py` files with your API key and region:
```python
PINECONE_API_KEY = "your-pinecone-api-key"
PINECONE_REGION = "your-region"  # e.g., us-east-1
```

#### **Step 4.3: Populate Pinecone Index**
Run `backend.py` to process the dataset and populate the Pinecone index:
```bash
python backend.py
```

This script:
1. Processes the dataset and generates embeddings.
2. Uploads the embeddings to Pinecone along with metadata.

---

### **Step 5: Configure OpenAI**
#### **Step 5.1: Create an OpenAI Account**
1. Sign up at [OpenAI](https://platform.openai.com/).
2. Generate an API key from the dashboard.

#### **Step 5.2: Update OpenAI Configuration**
Add your API key to `utils.py`:
```python
openai.api_key = "your-openai-api-key"
```

---

### **Step 6: Run the Chatbot**
Start the chatbot application using Streamlit:
```bash
streamlit run main.py
```

Open the URL provided in the terminal (e.g., `http://localhost:8501`) to interact with the chatbot.

---

## **Usage Instructions**

1. **Ask a Question**:
   - Enter your medical query into the chatbot, such as:
     ```
     What are the symptoms of pneumonia?
     ```

2. **View Responses**:
   - The chatbot retrieves the most relevant answer(s) and displays them along with their similarity scores (if enabled).

3. **Refined Queries**:
   - If a query is ambiguous, the chatbot refines it using OpenAI GPT-3.5.

---

## **Example Outputs**

### **Input Query**
```plaintext
How can I lose weight?
```

### **Expected Output**
```json
[
    {
        "metadata": {
            "question": "How can I lose weight?",
            "answer": "To reduce weight, you should maintain a calorie deficit and exercise regularly."
        },
        "score": 0.89
    },
    {
        "metadata": {
            "question": "What are some weight loss tips?",
            "answer": "Avoid sugary foods, eat more protein, and stay hydrated."
        },
        "score": 0.85
    }
]
```

---

## **Troubleshooting**

### **1. Pinecone Errors**
- Ensure the Pinecone index is populated:
  ```python
  index.describe_index_stats()
  ```
- Verify the **API key** and **region** configuration.

### **2. Missing Modules**
If a module is missing, ensure all dependencies are installed:
```bash
pip install -r requirements.txt
```

### **3. OpenAI Quota Issues**
If you receive an error about exceeding your OpenAI quota:
1. Check your usage on the OpenAI dashboard.
2. Upgrade to a paid plan if necessary.

---

## **Future Enhancements**

1. **Multilingual Support**:
   - Add multilingual embeddings for broader accessibility.
2. **Dynamic Dataset Updates**:
   - Allow users to upload and index new datasets.
3. **Cloud Deployment**:
   - Deploy the chatbot on platforms like AWS, Azure, or GCP for wider access.
4. **GPT Integration for Answers**:
   - Use GPT to generate or refine answers dynamically.

---

## **Acknowledgments**
- **Hugging Face** for pre-trained Sentence Transformer models.
- **Pinecone** for vector storage and retrieval.
- **Streamlit** for frontend development.
- **OpenAI** for GPT query refinement.

---

## **License**
This project is licensed under the MIT License.

---

### **Installation Codes (For README)**

**Ensure `requirements.txt` includes:**
```
streamlit
sentence-transformers
langchain
langchain-community
pinecone-client
openai
tqdm
pandas
nltk
```

---

Let me know if you need any further refinements!
