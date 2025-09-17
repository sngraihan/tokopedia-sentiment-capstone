# Capstone Project — Analisis Sentimen Ulasan Produk Tokopedia dengan IBM Granite

## 📌 Deskripsi
Proyek ini bertujuan untuk menganalisis ulasan produk dari platform e-commerce **Tokopedia** menggunakan pendekatan machine learning tradisional (baseline) dan **Large Language Model IBM Granite** (melalui Replicate API).  
Tujuan akhirnya adalah:
- Mengklasifikasikan ulasan menjadi **positif, netral, atau negatif**.
- Mengevaluasi performa model baseline vs Granite.
- Menghasilkan **insight & rekomendasi** yang bermanfaat untuk seller maupun platform.

## 📂 Dataset
Dataset yang digunakan:
- **Tokopedia Product Reviews (2019)** dari Kaggle  
  [Link dataset](https://www.kaggle.com/datasets/farhan999/tokopedia-product-reviews)  
- Jumlah data: **40.607 ulasan**  
- Kolom utama: `text`, `rating`, `category`, `product_name`, dll. 

Label sentimen dibuat otomatis berdasarkan rating:
- `≤ 2` → **negatif**
- `= 3` → **netral**
- `≥ 4` → **positif**

## 🛠️ Metodologi
1. **EDA (Exploratory Data Analysis)**
   - Distribusi rating → mayoritas review bintang 5.
   - Panjang teks rata-rata ~55 karakter.
   - Kategori dominan: elektronik, fashion, olahraga.

2. **Baseline Model**
   - Preprocessing: TF-IDF (unigram + bigram).
   - Model: Logistic Regression (`class_weight=balanced`).
   - Evaluasi: F1-score makro, confusion matrix.

3. **IBM Granite (Replicate API)**
   - Model: `ibm-granite/granite-3.3-8b-instruct`.
   - Prompt engineering → few-shot untuk klasifikasi `neg/neu/pos`.
   - Evaluasi: F1-score makro di subset 1000 review.

4. **Summarization (Insight)**
   - Granite digunakan untuk merangkum kumpulan ulasan per kategori.
   - Output berupa: *Top 3 keluhan, Top 3 hal positif, dan 1 rekomendasi*.
  


