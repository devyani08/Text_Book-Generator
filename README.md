# Textbook Question Answering System

This system uses advanced natural language processing and machine learning techniques to answer questions based on textbook content. It employs a RAPTOR (Recursive Application of Patterns To Organize Representation) indexing structure for efficient retrieval and a state-of-the-art language model for generating accurate answers.

## Table of Contents
1. [System Overview](#system-overview)
2. [Setup Instructions](#setup-instructions)
3. [Usage Guide](#usage-guide)
4. [Textbooks Used](#textbooks-used)
5. [System Components](#system-components)
6. [Dependencies](#dependencies)
7. [Known Limitations](#known-limitations)
8. [Output](Output)
9. [Contributing](#contributing)
10. [Individual Task](#Individualtask)

## System Overview

The system processes PDF textbooks, chunks the content, builds a RAPTOR index, and stores embeddings in a Milvus vector database. It uses a hybrid retrieval approach combining SBERT and DPR embeddings, re-ranks results, and generates answers using Google's Gemini Pro model.

## Setup Instructions

1. Clone this repository:
git clone https://github.com/Aryamantiwari17/Text_Book-Generator?tab=readme-ov-file
cd textbook-qa-system

3. Install dependencies:
pip install -r requirements.txt
Copy
4. Set up Milvus:
- Follow the [official Milvus installation guide](https://milvus.io/docs/install_standalone-docker.md)
-  curl -sfL https://raw.githubusercontent.com/milvus-io/milvus/master/scripts/standalone_embed.sh -o
-  standalone_embed.sh
- Start the Milvus server

4. Configure API keys:
- Create a `.env` file in the project root
- Add your Google API key: `GOOGLE_API_KEY=your_api_key_here`

5. Prepare textbooks:
- Place PDF textbooks in the `textbooks/` directory

## Usage Guide

1. Process textbooks and build the RAPTOR index:
python build_index.py
Copy
2. Start the question-answering interface:
python main.py
Copy
3. Enter your questions when prompted. Type 'quit' to exit.

## Textbooks Used

- FESC101 (Above Given)
- FESC105 (Above Given)
- FESC106 (Above Given)

## System Components

1. **Content Extraction**: Uses PyPDF2 to extract text from PDF textbooks.
2. **Data Chunking**: Splits text into manageable chunks using NLTK.
3. **RAPTOR Indexing**: 
- Generates embeddings using SentenceTransformer
- Clusters embeddings with GaussianMixture
- Builds a hierarchical RAPTOR tree structure
4. **Retrieval**:
- Implements hybrid retrieval using SBERT and DPR embeddings
- Performs query expansion with NLTK and WordNet
5. **Re-ranking**: Uses cosine similarity with SBERT embeddings
6. **Question Answering**: Utilizes Google's Gemini Pro model for answer generation

## Dependencies

- nltk
- PyPDF2
- sentence-transformers
- scikit-learn
- torch
- transformers
- google-generativeai
- pymilvus

For exact versions, see `requirements.txt`.

## Known Limitations

1. Input and Processing Constraints:
   - System performance is heavily dependent on the quality and relevance of input textbooks
   - Very long textbooks require significant processing time during indexing
   - The system may struggle with highly specialized or technical questions outside the scope of the textbooks

2. Token and Usage Limitations:
   - Free versions of language models (like Gemini) restrict the number of tokens, limiting the amount of text that can be processed
   - Daily usage limits for free services can be quickly exceeded, potentially interrupting system functionality

3. Deployment and Integration Challenges:
   - Issues arise when deploying the system through Streamlit
   - Integration with Milvus database encounters problems, causing the system to stop after deployment in Streamlit

## Output
![Screenshot from 2024-07-24 01-53-19](https://github.com/user-attachments/assets/20ed46f3-72d9-4d9f-9dd2-431272cb6fdf)
![Screenshot from 2024-07-24 01-56-28](https://github.com/user-attachments/assets/5d5d6fa9-aec7-4bc2-9a9a-7256ba0255de)
![Screenshot from 2024-07-24 01-56-42](https://github.com/user-attachments/assets/fb32e72a-378d-4a42-9198-d51208afad79)
![Screenshot from 2024-07-24 01-56-55](https://github.com/user-attachments/assets/604c01c9-3ed4-4d4f-82b6-9bdd3671dcef)



## Contribution

Contributions are welcome! Please read our [Contributing Guidelines](CONTRIBUTING.md) for details on how to submit pull requests, report issues, or request features.

## Individual Task
Download The Zip File and Find all the tasks individually as mentioned.
