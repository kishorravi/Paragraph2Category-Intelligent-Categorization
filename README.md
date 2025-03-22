# 🧠 Paragraph2Category: Intelligent Categorization

This project automatically matches a paragraph of text (e.g., a description of a social event) to the most relevant category from a predefined list. It uses **KeyBERT** for semantic keyword extraction and **TF-IDF cosine similarity** to rank and return the most suitable category.

---

## 🚀 Features

- ✅ Reads an Excel sheet of predefined social event categories
- ✅ Uses KeyBERT to extract meaningful keywords from a paragraph
- ✅ Applies TF-IDF + cosine similarity to find the best-matching category
- ✅ Returns top 5 similar category suggestions
- ✅ Lightweight and easy to integrate into classification pipelines
- ✅ Safe and secure: no external API calls or internet processing

---

## 🛡 Cybersecurity & Privacy Emphasis

This tool is designed with **data privacy** and **cybersecurity** in mind.

- 🔒 **No external data transfer**: All processing is done **locally** within your environment (Google Colab or desktop). No content is sent to external servers.
- 🔐 **Safe for sensitive content**: You can confidently use this tool for private or proprietary text such as internal reports, health records, policy notes, or institutional descriptions.
- ✅ **No model training required**: The system uses pre-trained transformer embeddings (from `sentence-transformers`) and never modifies or stores user data.
- 🧠 **Read-only processing**: The input data is only used in memory for keyword extraction and similarity comparison. It is never stored, uploaded, or cached.

This makes it suitable for use in:
- Secure enterprise environments
- Government and policy systems
- Healthcare & education records
- Any domain with sensitive text information

---

## ⚙️ System Performance & Load

This solution is optimized for **low-to-medium scale data processing**:

- 🚀 **Lightweight Transformer model**: Uses `all-MiniLM-L6-v2`, which is compact and fast while still maintaining high semantic understanding.
- 🧠 **Efficient TF-IDF vectorization**: The cosine similarity step is based on sparse matrix operations and is optimized for short inputs (such as event categories and paragraphs).
- 🖥 Can run on CPU in Google Colab, Jupyter, or any local machine (no GPU required)
- 🧩 Suitable for batch processing with minor optimization

If you're working on very large-scale text matching (millions of records), consider indexing strategies or approximate nearest neighbor techniques like FAISS.

---

## 📁 Folder Structure

