# Implementasi Pipeline Big Data untuk Prediksi Recovery Score Menggunakan Apache Spark

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![Spark](https://img.shields.io/badge/Apache%20Spark-PySpark-orange)
![Machine Learning](https://img.shields.io/badge/Machine%20Learning-Random%20Forest-green)

> **Proyek Ujian Akhir Semester (UAS)**
> **Mata Kuliah:** Big Data & Predictive Analytics Lanjut
> **Topik:** Health Data Analytics

## 📋 Tentang Proyek
Proyek ini bertujuan untuk membangun *pipeline* Big Data *end-to-end* guna memprediksi skor pemulihan tubuh (*Recovery Score*) berdasarkan data sensor kebugaran. Menggunakan **Apache Spark**, proyek ini mensimulasikan pemrosesan data skala besar (100k+ baris) mulai dari penyimpanan, pembersihan, analisis data eksploratif, hingga pemodelan Machine Learning.

### Fitur Utama:
* **Big Data Storage:** Simulasi penyimpanan terdistribusi menggunakan format **Parquet** (HDFS Simulation).
* **Advanced Data Processing:** Implementasi **RDD MapReduce** manual dan **Spark SQL** dengan CTE (*Common Table Expressions*).
* **Machine Learning Pipeline:** Komparasi algoritma **Linear Regression** vs **Random Forest Regressor**.
* **Model Optimization:** Hyperparameter tuning menggunakan **Cross-Validator**.

## 📊 Dataset
Dataset yang digunakan adalah data sintetis dari perangkat Whoop Fitness.
* **Sumber:** [Kaggle - Whoop Fitness Dataset](https://www.kaggle.com/datasets/likithagedipudi/whoop-fitness-dataset)
* **Volume:** 100,000+ Baris.
* **Fitur Utama:** `recovery_score` (Target), `day_strain`, `sleep_hours`, `hrv`, `resting_heart_rate`.

## 🛠️ Teknologi yang Digunakan
* **Core Engine:** Apache Spark (PySpark)
* **Bahasa:** Python
* **Library Pendukung:** Pandas, Matplotlib, Seaborn (untuk visualisasi)
* **Environment:** Google Colab / Jupyter Notebook

## ⚙️ Alur Kerja (Pipeline)
1.  **Ingestion:** Membaca data CSV dan menyimpannya ke format Parquet untuk efisiensi I/O.
2.  **Preprocessing:** Handling missing values, casting tipe data, dan encoding variabel kategorikal (`StringIndexer`).
3.  **Analisis:**
    * Menggunakan **Spark SQL (CTE)** untuk membandingkan performa user terhadap rata-rata komunitas olahraga.
    * Menggunakan **RDD MapReduce** untuk menghitung rata-rata beban latihan (*strain*) per olahraga.
4.  **Modeling:** Melatih model prediksi menggunakan `VectorAssembler` dan `StandardScaler`.
5.  **Evaluasi:** Mengukur akurasi menggunakan metrik RMSE (*Root Mean Square Error*).

## 📈 Hasil Analisis & Evaluasi
Berdasarkan eksperimen, berikut adalah perbandingan performa model:

| Model | RMSE (Root Mean Square Error) | Keterangan |
| :--- | :--- | :--- |
| **Linear Regression** | 16.89 | Baseline Model |
| **Random Forest** | **16.81** | **Best Model** |
| *Random Forest (Tuned)* | 16.86 | Setelah Hyperparameter Tuning |

**Kesimpulan:**
Model **Random Forest** terbukti lebih akurat dalam menangkap pola non-linear pada data kesehatan. Analisis *Feature Importance* menunjukkan bahwa **HRV (Heart Rate Variability)** dan **Durasi Tidur** adalah dua faktor paling dominan yang mempengaruhi pemulihan tubuh.

## 🚀 Cara Menjalankan Project
1.  **Clone Repository**
    ```bash
    git clone [https://github.com/username-anda/nama-repo-anda.git](https://github.com/username-anda/nama-repo-anda.git)
    ```
2.  **Install Dependencies**
    Pastikan Java (JDK 8/11) dan Python sudah terinstall.
    ```bash
    pip install pyspark pandas matplotlib seaborn numpy
    ```
3.  **Jalankan Notebook**
    Buka file `FP_BDAL.ipynb` menggunakan Jupyter Notebook atau Google Colab.
    Pastikan file dataset `whoop_fitness_dataset_100k.csv` berada di direktori yang sama.

---
**Author:** Izzuddin Akmal Daffani Ramadhan
**Universitas Amikom Yogyakarta**
