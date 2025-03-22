# 🧠 Paragraph2Category: Intelligent Social Event Categorization

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

## 💼 Business Use Cases

This tool can serve a wide range of industries and business needs:

### 📚 Education & Academia
- Automatically categorize abstracts, papers, and seminar topics
- Classify academic journal content based on thematic alignment
- Assist journal editors and reviewers in matching submissions with subject categories
- Support academic conference planning and content organization

### 🏢 Enterprise & HR
- Classify training material, employee workshops, and onboarding content
- Improve internal knowledge management systems

### 🏥 Healthcare & Medical Institutions
- Organize awareness campaigns, medical conference summaries, and educational outreach materials

### 📣 Marketing & Event Management
- Automate social event categorization for calendar listings and public portals
- Enhance content tagging and discoverability in CMS or blog systems

### 📰 Media & Publishing
- Tag articles, editorials, and news summaries for internal or public distribution

### 🛡 Government & Nonprofits
- Structure documentation for social programs, civic engagement, and community outreach
- Enable rapid sorting of initiatives and proposals by department or goal

---

## 📁 Folder Structure

```
├── Social_Event.xlsx                # Excel file with a list of category names
├── Catogory_selection.ipynb        # Jupyter Notebook with the implementation
├── README.md                        # This file
```

---

## 📦 Requirements

- Python 3.7+
- pandas
- scikit-learn
- keybert
- sentence-transformers
- openpyxl (for reading Excel files)

Install required packages:
```bash
pip install keybert -q
pip install -U sentence-transformers -q
pip install pandas scikit-learn openpyxl
```

---

## 📌 How It Works

1. Loads your category list from an Excel file (e.g., `Social_Event.xlsx`)
2. Accepts a paragraph of text (e.g., "An oncology seminar focusing on colon cancer awareness")
3. Extracts top keywords from the paragraph using KeyBERT
4. Compares the extracted keywords against category names using TF-IDF + cosine similarity
5. Outputs the best match and top 5 closest matches

---

## 🧪 Example Usage

```python
# ✅ Paragraph to test
paragraph = """
The Oncology Department is pleased to host a seminar focused on raising awareness about colon cancer, its early detection, and advancements in treatment.
This event aims to educate the public and healthcare professionals on the importance of timely screening, preventive measures, and supportive care.
Featuring expert talks by leading oncologists and real-life experiences from survivors, the seminar will serve as a platform for knowledge sharing
and community engagement. Attendees will have the opportunity to ask questions, access resources, and contribute to spreading awareness that could help save lives.
"""

keywords = kw_model.extract_keywords(paragraph, keyphrase_ngram_range=(1, 3), stop_words='english', top_n=10)
keyword_list = [kw[0] for kw in keywords]
keyword_text = " ".join(keyword_list)

# ✅ Match keywords with category names using TF-IDF similarity
texts = category_names + [keyword_text]
vectorizer = TfidfVectorizer().fit_transform(texts)
cosine_sim = cosine_similarity(vectorizer[-1], vectorizer[:-1])

# ✅ Get best and top 5 matching categories
best_index = cosine_sim.argmax()
top5_indices = cosine_sim[0].argsort()[-5:][::-1]
top5_matches = [category_names[i] for i in top5_indices]

# ✅ Print results
print("🔍 Extracted Keywords:", keyword_list)
print("✅ Best Matching Category:", category_names[best_index])
print("✅ Top 5 Matching Categories:", top5_matches)
```

---

## 📈 Potential Applications

- Auto-tagging and classification of event listings  
- Recommendation engines for CMS/blog systems  
- Data cleaning and semantic matching for large event datasets  
- Categorizing research abstracts or educational programs  
- Automating workflows in secure text-processing pipelines

---

## 📎 File Notes

- `Social_Event.xlsx` must have a column named **"Category Name"**
- Avoid including "ID" or headers as part of the category values

---

## 🤝 Contributing

Pull requests and suggestions are welcome! Feel free to fork this repo and adapt it for your own use case.

---

## 📝 License

This project is licensed under the MIT License.

---

## 🙌 Acknowledgements

- [KeyBERT](https://github.com/MaartenGr/KeyBERT)
- [Sentence Transformers](https://www.sbert.net/)
- scikit-learn for similarity scoring

