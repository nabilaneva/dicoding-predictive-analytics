# 📊 Laporan Proyek Machine Learning - Nabila Neva Rahmawati

## 🌟 Domain Proyek

Pertumbuhan pesat industri startup menghadirkan tantangan baru dalam pengambilan keputusan berbasis data. Salah satu tantangan utamanya adalah memprediksi keuntungan perusahaan berdasarkan faktor-faktor operasional seperti pengeluaran untuk riset dan pengembangan (R&D), administrasi, pemasaran, serta lokasi geografis perusahaan. Dalam proyek ini, digunakan dataset yang memuat informasi dari 1000 perusahaan startup yang diperoleh dari Kaggle. Dataset ini digunakan untuk membangun model prediktif berbasis regresi dengan tujuan memperoleh prediksi keuntungan yang lebih akurat dan dapat digunakan sebagai dasar pengambilan keputusan bisnis yang lebih strategis. 🚀

---

## 🧐 Business Understanding

### ❓ Problem Statements

Masalah pada proyek ini antara lain:

1. Bagaimana cara memprediksi kinerja finansial perusahaan berdasarkan pengeluaran di berbagai departemen (R&D, Administrasi, dan Marketing)?
2. Bagaimana cara memilih model prediksi yang paling akurat untuk memprediksi kinerja finansial perusahaan dari beberapa model yang ada (seperti KNN, Random Forest, dan Boosting)?

### 🎯 Goals

Tujuan dari proyek ini antara lain:

1. Mengembangkan model prediksi yang dapat secara akurat memprediksi kinerja finansial perusahaan berdasarkan pengeluaran di departemen R&D, Administrasi, dan Marketing untuk membantu pengambilan keputusan bisnis yang lebih tepat.
2. Menganalisis dan membandingkan berbagai model prediksi untuk menentukan model terbaik yang memberikan hasil paling akurat dalam memprediksi kinerja finansial berdasarkan data pengeluaran perusahaan.

### 🔧 Solution statements

1. Menggunakan algoritma **KNeighborsRegressor**, **RandomForestRegressor**, dan **AdaBoostRegressor** untuk membandingkan kinerja setiap model dalam memprediksi kinerja finansial perusahaan berdasarkan pengeluaran di departemen R&D, Administrasi, dan Marketing.
2. Melakukan evaluasi model menggunakan **Mean Squared Error (MSE)** untuk membandingkan keakuratan prediksi setiap model, dan memilih model yang memberikan MSE terkecil sebagai model terbaik untuk memprediksi kinerja finansial perusahaan.

---

## 📂 Data Understanding

- **Sumber data**: [Kaggle - 1000 Companies Profit Dataset](https://www.kaggle.com/datasets/rupakroy/1000-companies-profit)
- **Jumlah data**: 1000 baris, 5 kolom (fitur asli), yaitu R&D Spend, Administration, Marketing Spend, Profit, dan State.
- **Kondisi data**:
  - Tidak ada missing value ✅
  - Terdapat 1 data duplikat ❌
  - Terdeteksi outlier pada kolom **Administration** dan **Profit** 🧐

### 🔍 Variabel pada 1000 Companies Profit Dataset adalah sebagai berikut:

- **R&D Spend**: Pengeluaran untuk penelitian dan pengembangan.
- **Administration**: Pengeluaran untuk administrasi perusahaan.
- **Marketing Spend**: Pengeluaran untuk pemasaran dan promosi.
- **Profit**: Keuntungan perusahaan yang menjadi target prediksi.
- **State**: Lokasi geografis perusahaan (nama negara bagian di AS).

### 🔎 Exploratory Data Analysis (EDA):

#### 1. Univariate Analysis:

- **Fitur Kategorikal**:
  - Distribusi sampel pada fitur kategorikal menunjukkan pembagian yang hampir merata antara California (34,3%), New York (33,2%), dan Florida (32,5%).
  - California sedikit lebih dominan dibandingkan dengan New York dan Florida. 🌍
    ![univariate categorical](</gambar/univariate categorical.png>)
- **Fitur Numerik**:
  - **R&D Spend** dan **Profit** memiliki sebaran yang cukup luas.
  - **Administration** lebih terkonsentrasi di rentang sempit.
  - **Marketing Spend** menunjukkan variasi terbesar di antara fitur numerik lainnya. 💡
    ![univariate numerical](</gambar/univariate numerical.png>)

#### 2. Multivariate Analysis:

- **Fitur Kategorikal**:
  - Berdasarkan analisis fitur kategorikal, rata-rata **Profit** di New York, Florida, dan California relatif mirip.
  - Florida sedikit lebih unggul, namun perbedaannya tidak terlalu signifikan. 🔄
    ![multivariate categorical](</gambar/multivariate categorical.png>)
- **Numerical Features**:
  - **R&D Spend** dan **Marketing Spend** memiliki hubungan sangat kuat dengan **Profit**.
  - **Administration** juga berpengaruh positif terhadap **Profit**, namun tidak sekuat keduanya. 📈
    ![multivariate numerical 1](</gambar/multivariate numerical 1.png>)
    ![multivariate numerical 2](</gambar/multivariate numerical 2.png>)

---

## 🛠️ Data Preparation

- Data duplikat dihapus.
- Outlier ditangani menggunakan metode **IQR (Interquartile Range)**.
- Fitur kategorikal **State** diubah menjadi variabel numerik melalui **one-hot encoding**.
- Data dibagi menjadi data latih (train) dan data uji (test) menggunakan **train_test_split** dengan proporsi 80% untuk data latih dan 20% untuk data uji.
- Fitur numerik dinormalisasi dengan **StandardScaler**.

---

## 📈 Modeling

### 🔶 K-Nearest Neighbors Regressor (KNN)

- Model pertama adalah **KNeighborsRegressor** dengan parameter **n_neighbors=10**. KNN memprediksi nilai target berdasarkan rata-rata dari 10 tetangga terdekat dalam ruang fitur. Model ini cocok digunakan pada dataset kecil hingga sedang, dan bersifat **non-parametrik** sehingga fleksibel terhadap bentuk data.

### 🔷 Random Forest Regressor

- Model kedua adalah **RandomForestRegressor**, yang merupakan metode ensemble berbasis pohon keputusan. Model ini dilatih dengan parameter **n_estimators=50** (jumlah pohon), **max_depth=16** (kedalaman maksimum pohon), **random_state=55** untuk hasil yang reprodusibel, dan **n_jobs=-1** untuk mempercepat pelatihan menggunakan seluruh core CPU.

### 🔶 AdaBoost Regressor

- Model ketiga adalah **AdaBoostRegressor**, yaitu model boosting yang bekerja dengan membangun sejumlah estimator lemah secara bertahap. Model ini menggunakan parameter **learning_rate=0.05** dan **random_state=55**.

---

## 📊 Evaluation

### 📉 Metrik Evaluasi

Pada proyek ini, **Mean Squared Error (MSE)** digunakan sebagai metrik evaluasi untuk mengukur seberapa akurat model dalam memprediksi kinerja finansial perusahaan berdasarkan pengeluaran di departemen R&D, Administrasi, dan Marketing.

Penjelasan MSE:  
MSE adalah salah satu metrik yang umum digunakan untuk evaluasi model regresi. Metrik ini mengukur rata-rata kuadrat selisih antara nilai prediksi dan nilai aktual (ground truth). Semakin kecil nilai MSE, semakin akurat model dalam memprediksi. 🔍

### 🏆 Hasil Evaluasi Berdasarkan MSE:

- **Random Forest (RF)**:

  - **MSE**: 4000–5000
  - Model ini memiliki MSE terkecil, menunjukkan akurasi terbaik. ✅

- **K-Nearest Neighbor (KNN)**:

  - **MSE**: ~22000
  - Model ini memiliki performa terburuk dengan MSE tinggi. ❌

- **Boosting**:
  - **MSE**: 16000–17000
  - Meskipun lebih baik dari KNN, masih kurang akurat dibandingkan RF. ⚠️

### 📊 Hasil Evaluasi Berdasarkan Data Aktual:

- **KNN**: 51671,8
- **RF**: 52206,2
- **Boosting**: 57879,2

**Random Forest** memberikan prediksi yang paling mendekati nilai aktual. 🏆

---

Secara keseluruhan, **Random Forest** terbukti sebagai model terbaik untuk memprediksi kinerja finansial perusahaan. 🔥
