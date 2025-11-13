# 📰 Vietnamese-News-Topic-Modeling
![Stars](https://img.shields.io/github/stars/maithanhphuc2004/Vietnamese-News-TopicModeling?style=flat-square)
![Forks](https://img.shields.io/github/forks/maithanhphuc2004/Vietnamese-News-TopicModeling?style=flat-square)
![Issues](https://img.shields.io/github/issues/maithanhphuc2004/Vietnamese-News-TopicModeling?style=flat-square)
![Last Commit](https://img.shields.io/github/last-commit/maithanhphuc2004/Vietnamese-News-TopicModeling?color=green&style=flat-square)

![Python](https://img.shields.io/badge/Python-3.10+-blue?style=flat-square&logo=python)
![TF-IDF](https://img.shields.io/badge/TFIDF-Feature%20Engineering-orange?style=flat-square)
![PhoBERT](https://img.shields.io/badge/PhoBERT-Embeddings-red?style=flat-square)
![BERTopic](https://img.shields.io/badge/BERTopic-Topic%20Modeling-purple?style=flat-square)
![License](https://img.shields.io/badge/License-MIT-yellow?style=flat-square)

---

## 📌 Overview *(Tổng quan)*

This project applies **multiple Topic Modeling approaches**—including **LDA, NMF, LSA, and BERTopic**—to identify and analyze latent topics from **7,052 preprocessed Vietnamese online news articles**.  
*(Dự án áp dụng nhiều phương pháp Topic Modeling—LDA, NMF, LSA, BERTopic—để trích xuất & phân tích chủ đề tiềm ẩn từ 7.052 bài báo điện tử Việt Nam đã tiền xử lý.)*

It includes:  
- Full web scraping pipeline (Selenium + BeautifulSoup)  
- Text cleaning, normalization, tokenization  
- TF-IDF, BoW, and PhoBERT embeddings  
- Training & evaluation across 4 topic models  
- Coherence, Perplexity, Reconstruction Error, ARI, NMI evaluation  
- Final comparison & conclusions  

📄 *Full content extracted from:* :contentReference[oaicite:1]{index=1}

---

## 📚 Data Pipeline *(Quy trình dữ liệu)*

### **1. Data Collection (Thu thập dữ liệu)**  
- Automatic crawling using **Selenium** & **BeautifulSoup**  
- Extracted fields: `title`, `category`, `content`, `pub_date`, `author`, `link`  
- 7,580 articles collected → 7,052 final cleaned samples  
- Saved as CSV for reproducibility  

### **2. Preprocessing (Tiền xử lý)**  
Includes:  
- Lowercasing  
- Removing URLs, emojis, digits, and special characters  
- Vietnamese word segmentation using **Underthesea**  
- Removing duplicates using **MinHash + LSH**  
- Removing short documents (<100 tokens)  
- Merging rare categories  
- Exporting cleaned dataset for modeling  

### **3. Feature Engineering (Biểu diễn đặc trưng)**  
- **TF-IDF** → used for NMF & LSA  
- **Bag-of-Words** → used for LDA  
- **PhoBERT / Vietnamese-SBERT embeddings** (768-dim) → used for BERTopic  

---

## 🔥 Models Used *(Các mô hình sử dụng)*

| Category | Models |
|---------|--------|
| **Classical Topic Models** | LDA, NMF, LSA |
| **Embedding-based Models** | PhoBERT + BERTopic |
| **Clustering Algorithms** | HDBSCAN, KMeans |
| **Evaluations** | Coherence, Perplexity, Reconstruction Error, ARI, NMI |

---

# 📊 Algorithm Comparison Table  
*(Bảng so sánh mô hình – đẹp & chuyên nghiệp)*

### **Table 1 — Summary of Optimal Results**  
*(Tóm tắt kết quả tốt nhất của từng mô hình)*

| Model | Optimal K | Coherence (c_v) | Other Metrics | Notes (Ghi chú) |
|-------|-----------|------------------|----------------|------------------|
| **NMF (TF-IDF)** | 13 | **0.8405** | Rec. Error ↓ 80.24 | Best coherence; balanced topics; easy interpretation |
| **BERTopic (SBERT)** | 11 | 0.7324 | Outliers: 600 docs | Strong semantic grouping; modern embeddings |
| **LDA (BoW)** | 13 | 0.6642 | — | Clean topics; probabilistic; stable |
| **LSA + KMeans** | 12 | 0.4040 | Var. Explained 0.0681 | Weak separation; overlapping topics |

---

## 🧠 Detailed Model Insights *(Phân tích chi tiết từng mô hình)*

### **1️⃣ LDA – Latent Dirichlet Allocation**  
- Works on Bag-of-Words  
- Best at **K = 13**  
- Coherence = **0.6642**  
- Produces clean, interpretable topics  
- Topics include: education, health, economy, law, lifestyle, sports...

### **2️⃣ NMF – Non-negative Matrix Factorization**  
- Works on TF-IDF  
- Best at **K = 13**  
- Highest coherence: **0.8405**  
- Most stable and interpretable result  
- Topics: ESG, family, auto, sports, health, Ukraine–Russia, entertainment...

### **3️⃣ LSA + KMeans**  
- Works on TF-IDF + SVD  
- Best at K = 12  
- Coherence = **0.4040** (low)  
- Topics overlap heavily → not ideal for Vietnamese text  

### **4️⃣ BERTopic (PhoBERT + UMAP + HDBSCAN)**  
- Embedding-based, no need to choose K  
- Extracted 11 topics  
- Coherence = **0.7324**  
- Strong semantic clustering  
- Some outliers (~600 docs)

---

## 🧪 Evaluation Metrics *(Các chỉ số đánh giá)*

### **Intrinsic (Nội tại)**  
- **Coherence (c_v)**: Topic interpretability  
- **Perplexity** (LDA)  
- **Reconstruction Error** (NMF)  
- **Explained Variance** (LSA)

### **Extrinsic (Ngoại tại)**  
| Model | ARI | NMI |
|--------|------|------|
| **NMF** | **0.4295** | **0.5417** |
| LDA | 0.3989 | 0.5234 |
| LSA | 0.3373 | 0.5300 |

➡️ *NMF provides the best match to real categories.*

---

## 🚀 Applications *(Ứng dụng thực tế)*

- News trend analysis *(Phân tích xu hướng báo chí)*  
- Media monitoring *(Giám sát truyền thông)*  
- Policy insights *(Hỗ trợ hoạch định chính sách)*  
- Contextual advertising *(Quảng cáo theo ngữ cảnh)*  
- Research & social science *(Nghiên cứu học thuật)*  
- Building recommender systems *(Hệ thống gợi ý bài viết)*  

---

## ⚠️ Limitations *(Hạn chế)*

- Single data source → limited generalization  
- LSA coherence low  
- BERTopic requires GPU & produces outlier cluster  
- Classical models require manual K tuning  

---

## 🔮 Future Work *(Hướng phát triển)*

- Expand dataset to multiple news sources  
- Use advanced neural topic models: **ProdLDA, ETM**  
- Improve Vietnamese embeddings (vBERT, PhoBERT-large)  
- Deploy real-time topic explorer dashboard  
- Incorporate human evaluation (expert labeling)  

---

## 👨‍💻 Authors *(Tác giả)*

- **Mai Thanh Phúc**  
- **Hoàng Thị Yến Nhi**  
- **Trần Trọng Thành**
- **GVHD: Lê Nhật Tùng**

---

