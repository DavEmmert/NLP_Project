# NLP_Contract_Checker

The NLP_Contract_Checker is a modular Python tool designed to automatically analyze, classify, and assess sections of contracts using natural language processing and large language models (LLMs). It supports web scraping, paragraph and section extraction, topic classification, and evaluation against user-defined compliance criteria.

---

## Repository Structure

```
├── classes/                 # Modular class definitions
│   ├── class_cosine_mapper.py
│   ├── class_section_topic_preditcor.py
│   └── Class_TextLabelDataset.py
│
├── functions/              # Reusable functional components
│   ├── function_read_in.py
│   ├── functions_embeddings.py
│   ├── functions_criteria_fullfillment.py
│   └── functions_preprocessing.py
│
├── data/
│   ├── input_files/        # Raw contract inputs
│   ├── temporary_files/    # Intermediary processed files
│   └── final_output/       # Output with mapped sections and fulfillment ratings
│
├── contractchecker.ipynb   # Main executable notebook with explanations
├── requirements.in         # Editable dependency list
├── requirements.txt        # Compiled and frozen dependency list (gitignore)
└── key.py                  # Contains your OpenAI key (excluded from version control) (gitignore)
```

---

## Setup Instructions

### 1. Create and activate a virtual environment

```bash
# Create environment with Python 3.11
uv venv .venv --python=python3.11

# Activate it
# Windows
.venv\Scripts\Activate.ps1

# macOS/Linux
source .venv/bin/activate
```

### 2. Install dependencies

```bash
# Add the package name to requirements.in
# Then run:
uv pip compile requirements.in > requirements.txt
uv pip sync requirements.txt
```

### 3. Configure your OpenAI key

Create a file named `key.py` with your OpenAiKey in the root directory:

```bash
echo OpenAiKey = "'YOUR OPEN AI KEY HERE'" > key.py
```

---

## Main Notebook

The notebook `contractchecker.ipynb` provides a step-by-step interactive pipeline including:

- Contract loading (from files or scraped URLs)
- Preprocessing and section extraction
- Topic classification using cosine similarity
- Fulfillment checks using GPT (OpenAI API)
- Summary of fulfillment percentages

---

## Core Functionality

### Defined Functions (in `functions/`)

- **Scraping Contracts**: Flexible functions to extract contracts from CommonPaper, Fakturia, Mitratech, or arbitrary HTML.
- **Preprocessing**: Extracts paragraphs and sections, cleans text, and handles title extraction.
- **Embeddings**: Generates text embeddings using a SentenceTransformer model.
- **Fulfillment Check**: Uses GPT to evaluate contract sections against defined criteria (returns JSON with scores).

### Defined Classes (in `classes/`)

- **CosineMapper**: A custom transformer-based module for semantic classification using cosine similarity.
- **SectionTopicPredictor**: Predicts topics for contract sections based on semantic similarity to labeled topics.
- **TextLabelDataset**: A simple PyTorch dataset for fine-tuning or evaluation of text-classification models.

---

## Output

The final output consists of:

- Contracts split into paragraphs and sections
- Each section labeled with a predicted topic
- Fulfillment score per section and overall (as percent)
- All outputs saved under `/data/final_output/`

---

## Contact

- [Nils Taglieber](mailto:nils.taglieber01@gmail.com)  
- [David Emmert](mailto:David.Emmert@online.de)  
- [Nick Stein](mailto:steinnick18@gmail.com)  
- [Paul Scrima](mailto:paulscrima@gmail.com)

---

## License

This project is intended for academic or internal prototyping purposes. No warranties implied.