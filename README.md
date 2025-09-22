# Ranked Retrieval Model 🔍
🌐 **Try the live demo**: https://ranked-retrieval-model.streamlit.app/

A comprehensive information retrieval system built with Python that implements advanced text processing, indexing, and ranking algorithms for efficient document search and retrieval.

## 🌟 Features

### Core Functionality
- **Text Preprocessing Pipeline**: Complete tokenization, stopword removal, and Porter stemming
- **Inverted Index Construction**: Efficient document indexing with term frequency storage
- **Vector Space Model (VSM)**: TF-IDF based document ranking and similarity scoring
- **Spell Correction**: Intelligent query correction using Levenshtein distance and phonetic matching
- **Multi-format Persistence**: Support for both JSON and Pickle serialization
- **Normalized Cosine Similarity**: Implements proper document vector normalization for accurate similarity scoring

### Novel Features & Innovations
- **Hybrid Spell Correction**: Combines PySpellChecker with custom vocabulary-based correction using Levenshtein distance fallback
- **Interactive Query Interface**: Real-time query processing with spell correction feedback using Streamlit
- **Interactive Document Links**: Results display clickable links directly to source documents for immediate access


## 🏗️ System Architecture

```
┌─────────────────┐    ┌──────────────────┐    ┌─────────────────┐
│   Raw Corpus    │───▶│  Text Processing │───▶│ Inverted Index  │
└─────────────────┘    └──────────────────┘    └─────────────────┘
                              │
                              ▼
┌─────────────────┐    ┌──────────────────┐    ┌─────────────────┐
│  Search Results │◀───│  VSM Ranking     │◀───│ Query Processing│
└─────────────────┘    └──────────────────┘    └─────────────────┘
```

## 📋 Requirements

### Dependencies
```
nltk==3.9.1
jellyfish==1.2.0
pyspellchecker==0.8.3
```

### Python Version
- Python 3.7 or higher

## 🚀 Installation & Setup

1. **Clone the repository**:
   ```bash
   git clone <repository-url>
   cd ranked-retrieval-model
   ```

2. **Install dependencies**:
   ```bash
   pip install nltk jellyfish pyspellchecker
   ```

3. **Download NLTK data**:
   ```python
   import nltk
   nltk.download('punkt')
   nltk.download('punkt_tab')
   nltk.download('stopwords')
   ```

4. **Prepare your corpus**:
   - Create a `Corpus` folder in the project directory
   - Add your `.txt` files to the corpus folder

## 📁 Project Structure

```
ranked-retrieval-model/
│
├── pipeline.ipynb              # Main implementation notebook
├── doc_lengths.json           # Precomputed document vector lengths
├── inverted_index.json        # Serialized inverted index
├── inverted_index.pkl         # Binary index (more efficient)
├── Corpus/                    # Document collection
│   ├── Adobe.txt
│   ├── Amazon.txt
│   ├── apple.txt
│   └── ... (other documents)
└── README.md                  # This file
```

## 🎯 How to Run

### Option 1: Web Interface (Recommended)
🌐 **Try the live demo**:(https://ranked-retrieval-model.streamlit.app/)

### Option 2: Jupyter Notebook
1. Launch Jupyter Notebook:
   ```bash
   jupyter notebook
   ```
2. Open `pipeline.ipynb`
3. Run all cells sequentially
4. Use the interactive search interface in the last cell

### Option 3: Python Script
Extract the code from the notebook and run:
```bash
python search_engine.py
```

### Running the Search System
1. **Build the index** (first time only):
   - The system will process all `.txt` files in the `Corpus` folder
   - Creates `inverted_index.json` and `doc_lengths.json`

2. **Search for documents**:
   - Enter your query when prompted
   - The system will show spell-corrected query
   - View ranked results with similarity scores

## 💡 Usage Examples

### Basic Search
```
Enter your search query: enviroment protecion
user query: enviroment protecion
Corrected query: environment protection
```

### Results Display
```
🔍 Top 10 Results
[google.txt](corpus/google.txt) — Score: 0.0729
[Adobe.txt](corpus/Adobe.txt) — Score: 0.0494
[Discord.txt](corpus/Discord.txt) — Score: 0.0379
```

## 🔧 Technical Details

### Text Processing Pipeline
1. **Tokenization**: NLTK word tokenization
2. **Normalization**: Lowercase conversion
3. **Filtering**: Remove non-alphanumeric tokens and stopwords
4. **Stemming**: Porter Stemmer for word reduction
5. **Phonetic Encoding**: Soundex codes for pronunciation matching

### Ranking Algorithm
- **TF-IDF Weighting**: `(1 + log₁₀(tf)) × log₁₀(N/df)`
- **Cosine Similarity**: Normalized dot product between query and document vectors
- **Length Normalization**: Prevents bias toward longer documents

### Spell Correction Strategy
1. Check against corpus vocabulary
2. PySpellChecker for common corrections
3. Levenshtein distance fallback for domain-specific terms

## 📊 Performance Metrics

- **Index Size**: ~840KB (JSON), ~160KB (Pickle)
- **Corpus Size**: 41 documents processed
- **Search Latency**: Sub-second query processing
- **Memory Efficiency**: Optimized data structures for large corpora

## 🔍 Advanced Features

### Customization Options
- **Modify stemming**: Replace PorterStemmer with other algorithms
- **Adjust similarity metrics**: Implement BM25 or other ranking functions
- **Extend spell correction**: Add domain-specific dictionaries
- **Filter results**: Add document type or date filtering



### Contributors
1. Charvi 
2. Navya Jain 
3. Vanshika Srivastava 
