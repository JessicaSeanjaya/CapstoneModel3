# **Capstone Project 3 - E-Commerce Customer Churn**
Created by : Jessica Seanjaya

## **1. Business Problem Understanding**
**Context**  
Sebuah divisi data science dan big data dalam suatu perusahaan e-commerce diminta untuk mengidentifikasi customer yang memiliki kecenderungan untuk berhenti berlangganan, dikenal juga dengan istilah **customer churn**. Perusahaan ingin melakukan pencegahan customer churn dengan memberikan promo-promo menarik untuk meningkatkan loyalitas customer dan mengurangi jumlah customer churn menjadi tidak churn.

**Goals**  
Perusahaan ingin menganalisa kemampuan customer yang dapat churn di waktu mendatang, tentunya hal ini sangat dihindari oleh perusahaan karena berpengaruh terhadap pendapatan perusahaan. Adapun berdasarkan referensi, Customer Acquisition Cost (CAC) pada  e-commerce berkisar antara 45-50 USD, sehingga apabila e-commerce tidak dapat mempertahankan customer maka e-commerce akan kehilangan biaya yang sebelumnya pernah dikeluarkan dan harus mengeluarkan biaya untuk mendapatkan 1 customer kembali. Dengan menggunakan machine learning, kita dapat menganalisa faktor dan variable apa saja yang berpengaruh terdapat customer churn dan dapat membuat strategi bisnis/promosi untuk meningkatkan loyalitas customer yang akan digunakan oleh tim promosi/marketing.

Referensi:
1. https://scalecrush.io/blog/average-customer-acquisition-cost-ecommerce#:~:text=The%20average%20CAC%20on%20the,to%20acquire%20a%20single%20customer diakses pada 19 Februari 2023 pukul 21.00 WIB.

**Analytic Approach**  
Setelah perusahaan memprediksi customer yang churn, selanjutnya kita dapat membuat program dan strategi untuk dapat mempertahankan customer yang akan churn.

**Metric Evaluation**    

Confusion Matrix
|       | **N-Prediction**| **P-Prediction** |
| --- | --- | --- |
| **N-Actual**     | TN | FP |
| **P-Actual**      | FN | TP |

Target:   
0 : Customer tidak *churn*  
1 : Customer *churn*

Condition:  
1. True Positive -> Customer churn  
2. False Positive (Type 1 error) -> Customer tidak churn tapi terprediksi Churn  
Konsekuensi: Biaya promosi yang dikeluarkan oleh perusahaan tidak tepat atau untuk customer yang sebenarnya tidak churn.  
3. True Negative -> Customer tidak churn  
4. False Negative (Type 2 error) -> Customer churn tapi terprediksi tidak churn.
Konsekuensi: Customer churn dan tidak lagi menggunakan layanan perusahaan.    

Model yang diinginkan adalah model yang dapat mengoptimalkan biaya promosi hanya ditujukan ke customer yang memiliki kecenderungan untuk churn dan memutuskan untuk tidak churn. Sehingga, metrics yang cocok digunakan pada model ini adalah **ROC_AUC**.     

Menurut Park Seong Ho, Receiver Operating Characteristic (ROC) merupakan kurva antara sensitivitas uji atau positif sesungguhnya (TPR) (koordinat y) dengan 1-spesifisitas atau positif palsu (FPR) (koordinat x) dan merupakan metode yang efektif untuk mengevaluasi kinerja tes diagnostik. Adapun metode pengukuran yang paling dikenal adalah pengukuran area di bawah kurva/Area Under Curve (AUC) yang menginterpretasikan nilai rata-rata sensitivitas untuk semua kemungkinan nilai speisfisitas.

Sehingga, strategi yang digunakan pada model ini adalah :
1. Memaksimalkan nilai **Recall/True Positive Rate**
2. Meminimalkan **False Positive Rate**

Referensi:  
1. Park, Seong Ho dan Goo, Jin Mo dan Jo. Chan-Hee. 2004. Receiver Operating Characteristic (ROC) Curve : Practical Review for Radiologist. Korean J Radiol 5(1): 11-18. doi:  10.3348/kjr.2004.5.1.11

# **2. Data Understanding**
Sumber Dataset : https://drive.google.com/drive/folders/1PITb78NtK9Ra6wOkQdXCIgItZkj29Ves?usp=share_link  

Note:  
1. Sebagian besar fitur bersifat kategorik (Nominal, Ordinal, Binary)
2. Setiap baris data merepresentasikan satu informasi customer yang pernah berbelanja di e-commerce

### **Attribute Information**
| Attribute | Data Type | Description |
| --- | --- | --- |
| Tenure | Float | Masa tenor customer |
| WarehouseToHome | Float | Jarak antara gudang dengan rumah customer |
| NumberOfDeviceRegistered | Integer | Jumlah perangkat yang terdaftar  |
| PreferedOrderCat | Text | Kategori pesanan customer bulan sebelumnya |
| SatisfactionScore | Integer | Skor kepuasan customer |
| MaritalStatus | Text | Status pernikahan customer |
| NumberOfAddress | Integer | Jumlah alamat yang terdaftar |
| Complain | Integer | 0 - Tidak ada complain, 1 - ada complain |
| DaySinceLastOrder | Float | Hari sejak pesanan terakhir |
| CashbackAmount | Float |  Rata-rata Cashback bulan lalu |
| Churn | Integer | 0 - Tidak churn, 1 - Churn |

# **3. Data Cleaning**
1. Melihat profil dataset
2. Drop data duplikat
3. Handling missing values
4. Handling outlier

# **4. Modeling**
1. Data Splitting
2. Model Benchmarking : K-Fold
3. Model Benchmarking : Data Testing
4. Oversampling Test (SMOTE)
5. Hyperparameter Tuning (with Grid Search CV)

# **5. Conclusion and Recommendation**
