# Deteksi-status-customer-perusahaan-telekomunikasi

# Disclaimer
Pembuatan model machine learning ini saya lakukan dalam tahap proses pembelajaran saya di bootcamp Fresh graduate academy yang di adakan oleh
Kementerian Komunikasi dan Informatika bekerja sama dengan binar academy.

# Model machine learning
Model machine learning yang saya buat adalah Xgboost dan logistic regression, nantinya kedua model ini akan dibandingkan model mana yang lebih baik
dengan melihat akurasi, presisi, F1-call dan recall

dalam pembuatan model machine learning ini, hal yang saya lakukan adalah :
1. Melakukan Exploratory Data Analysis
Pada tahapan ini saya lakukan untuk mengetahui kolom dan baris dari dataframe yang digunakan. lalu mengecek apakah pada dataframe memiliki 
kolom bernilai null dan duplikat, hasilnya dataframe tidak memiliki data null dan duplikat.
lalu saya mengecek jumlah data pelanggan yang churn dan tidak churn,
hasilnya untuk data pelanggan churn memiliki data sebanyak 3652 data dan data pelanggan tidak churn sebanyak 598, cukup berbeda jauh sehingga berisiko model akan overfitting
sehingga saya memutuskan untuk melakukan sampling sebelum melatih model machine learning.

2. Visualisasi Data
proses pembuatan visualisasi data yang saya lakukan, saya mulai dari membuat pertanyaan terlebih dahulu, yaitu :
daerah mana yang paling banyak memiliki pelanggan churn dan apakah jumlah panggilan pelanggan ke customer service mempengaruhi pelanggan akan churn?
hasilnya :
![image](https://user-images.githubusercontent.com/94748637/196013624-396b18b5-d639-4fae-9de2-4e64e3b84948.png)
Dapat dilihat bahwa pelanggan kita paling banyak berada di area 415 namun di daerah tersebut memiliki jumlah pelanggan churn terbanyak

![image](https://user-images.githubusercontent.com/94748637/196013648-8b68b75b-42fe-4fc5-a8a6-ac5e6c2c2e73.png)
Dari grafik diatas didapatkan informasi bahwa jumlah customer menghubungi customer service call tidak mempengaruhi apakah customer tersebut akan churn atau tidak.

3. Data preprocessing
Yang pertama saya lakukan adalah mengubah kolom yang bertipe kategorikal yang memiliki 2 nilai menjadi numeric agar bisa mengetahui korelasi antara kolom kategorik dengan kolom churn

lalu saya melihat korelasi antar kolom dengan kolom churn (karena kolom churn adalah kolom yang ingin di deteksi) dan didapatkan hasil seperti berikut :

![image](https://user-images.githubusercontent.com/94748637/196013682-f3f1ff5d-e0f9-4d7b-bd0e-f867c72afefd.png)

Dapat dilihat bahwa korelasi antar kolom dengan kolom churn itu cukup rendah, paling tinggi berada di nilai 0,25. sehingga saya memutuskan untuk mengambil kolom dengan korelasi diatas 0.1

langkah selanjutnya adalah melakukan standarisasi pada kolom numeric dan one-hot encoding untuk kolom kategorik untuk meningkatkan kualitas dari model machine learning

4. Sampling
saya melakukan 2 macam sampling, yaitu oversampling menggunakan SMOTE dan undersampling menggunakan random under sampler. hal ini dilakukan untuk mengetahui apakah ada perbedaan untuk hasil model
machine learning yang dilatih menggunakan oversampling dan undersampling

5. Membuat model machine learning
Model yang saya buat adalah logistic regression dan XGboost dengan data latih data yang di oversampling dan di undersampling, sehingga total saya membuat 4 model machine learning

6. Evaluasi model machine learning
untuk evaluasi yang saya lakukan adalah melihat akurasi, presisi, recall dan F1-score dimana didapatkan model Xgboost dengan data train di oversampling memiliki nilai terbaik. dimana 4 parameter tersebut
memiliki nilai diatas 90% sehingga saya putuskan model xgboost dengan data train oversampling yang saya gunakan untuk mendeteksi data test
