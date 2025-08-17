# 📰 News Bias Analyzer with IBM Granite

## 📌 Project Overview
Proyek ini dibuat untuk menganalisis **bias politik dalam berita online** yang diambil secara real-time melalui **News API**.  
Latar belakangnya adalah semakin banyaknya informasi di media digital yang dapat dipengaruhi oleh framing tertentu. Hal ini menimbulkan kebutuhan akan **alat bantu analisis bias** agar pembaca berita dapat memahami sudut pandang media dengan lebih kritis.  

Permasalahan yang diangkat adalah:  
- Bagaimana mengidentifikasi kecenderungan bias politik dalam berita secara **otomatis**?  
- Bagaimana menyajikan hasil analisis dalam bentuk yang mudah dipahami (ringkasan, label bias, dan skor probabilitas)?  

Pendekatan yang digunakan adalah dengan memanfaatkan **Large Language Model (LLM)** untuk membaca dan menganalisis teks berita, kemudian menyimpan hasilnya dalam bentuk tabel dan file CSV agar bisa ditindaklanjuti untuk penelitian lebih lanjut.  

---

## 🔍 Analysis Process
Langkah-langkah analisis dilakukan secara sistematis:  

1. **Data Collection**  
   - Menggunakan [News API](https://newsapi.org/) untuk mengambil artikel real-time berdasarkan kategori tertentu (`business`, `health`, `technology`, dll).  

2. **Preprocessing**  
   - Mengambil atribut penting dari artikel: *judul, deskripsi, sumber, dan URL*.  
   - Menyusun prompt khusus untuk model Granite agar menghasilkan output terstruktur dalam format JSON.  

3. **Bias Analysis**  
   - LLM (Granite) diminta melakukan:  
     - **Summarization** → membuat ringkasan singkat artikel.  
     - **Classification** → menentukan kecenderungan bias politik: *Left, Center, Right*.  
     - **Probability Scoring** → memberikan bobot probabilistik pada setiap kategori (jumlah total = 1.0).  

4. **Result Storage**  
   - Hasil analisis dimasukkan ke **Pandas DataFrame**.  
   - Data disimpan dalam file CSV agar bisa dipakai untuk riset lebih lanjut.  

---

## 📊 Insight & Findings
Dari hasil pengujian awal pada berbagai kategori berita:  
- Model mampu mengidentifikasi kecenderungan bias dengan tingkat granularitas yang cukup baik.  
- Artikel dari sumber tertentu cenderung konsisten pada satu spektrum politik (misalnya *Left* atau *Right*), sementara artikel dari media mainstream sering berada di kategori *Center*.  
- **Pendekatan probabilistik** lebih informatif dibanding label tunggal, karena menggambarkan spektrum bias yang lebih realistis.  

Insight utama:  
1. Media yang berbeda dapat menyajikan berita serupa dengan sudut pandang berbeda.  
2. Analisis otomatis seperti ini dapat mendukung penelitian komunikasi, literasi media, dan deteksi bias dalam konteks politik.  
3. Data hasil analisis bisa dijadikan dasar untuk membangun **dashboard monitoring bias media**.  

---

## 🤖 AI Support Explanation
- **IBM Granite 3.3-8B Instruct** (via Replicate API) digunakan sebagai **Large Language Model** untuk:  
  - **Summarization** → menyarikan artikel menjadi ringkas (maks. 3 kalimat).  
  - **Classification** → mengklasifikasikan bias politik ke dalam *Left, Center, Right*.  
  - **Scoring** → memberikan probabilitas numerik pada setiap kategori bias.  

- **LangChain Community** memudahkan integrasi LLM agar output bisa diproses dalam format JSON terstruktur.  
- **Pandas** digunakan untuk menyimpan dan mengolah hasil analisis ke dalam tabel.  
- **News API** menjadi sumber utama data real-time.
  
Dengan kombinasi ini, AI digunakan secara **relevan dan terarah** untuk menjawab permasalahan penelitian: **deteksi bias politik dalam berita online**.  
