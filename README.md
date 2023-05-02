<p align="center"><img src="https://github.com/iqbalmudzakky/final_project/blob/main/bootcamp_notes/Bank-header.png" width=50% height=50%></p>
<h2> EXPLORATORY DATA ANAYSIS</h2><br>
by: Data Magician Team<br>
Dataset : data train from [[source]](https://www.kaggle.com/datasets/reverie5/av-janata-hack-payment-default-prediction)

### Introduction :
Bank Taiwan nasional/national Taiwan bank (NTB) merupakan bank terkemuka di Asia. Bank ini menyediakan kemudahan dalam bertransaksi berupa debit card dan credit . Namun bank ini mempunyai sebuah masalah resiko credit yang perlu kami atasi. <br>
Default rate Taiwan National Bank pada bulan Oktober 2005 sebesar 22%.<br>
Jika tidak diminimalisir kemungkinan dapat mengarahkan ke masalah finansial karena turunnya pemasukan bank, mengganggu kestabilan keuangan bank, dan dapat menurunkan reputasi bank di mata nasabah maupun investor hingga mengarah ke penurunan harga saham bank.
<br>
* <b>Our Role :</b><br>
Risk Analyst Team <br>
* <b>Business Metrics :</b><br>
Default Rate<br>
* <b>Goal :</b><br>
Menurunkan angka default rate sehingga meminimalisir kerugian bank<br>
* <b>Solution :</b><br>
Model Machine Learning yang dapat digunakan untuk memprediksi customer dengan tendensi melakukan payment default pada bulan depan.<br>

### Data Overview 
Satu baris data berisi informasi dari seorang customer, yaitu :
* Profil pribadi seperti gender, usia, limit kredit, marital status, dan pendidikan
* Riwayat kredit customer seperti status pembayaran, total tagihan, dan total pembayaran tiap bulannya pada periode April - September 2005
* Label default payment bulan depan yang menjadi terget prediksi.
### EXPLORATORY DATA ANALYSIS CONCLUSION :<br>
Dari EDA yang telah dilakukan, dapat ditarik beberapa insight yaitu:
1. Default rate dari bank ini masih berada di angka 22%, dimana angka ini masih tergolong tinggi (Default rate ideal bagi suatu bank adalah di bawah 5%). Masalah ini tentu perlu segera ditangani agar bank tidak mengalami kerugian yang besar, baik kerugian finansial maupun turunnya reputasi bank di mata nasabah lain maupun investor.
2. User terbanyak yang tidak bisa membayar tagihan sesuai dengan jumlahnya pada bulan tertentu merupakan user yang masih single dengan pendidikan tingkat terakhir university. Karena hal ini, perlu ada nya tinjauan khusus kedepannya untuk terkait masalah ini
3. Nasabah paling banyak berada pada segmen usia Dewasa (25-40 tahun), dan segment usia adult ini juga memiliki nasabah yang gagal bayar pada bulan Oktober paling banyak dibandingkan dengan segmen usia lainnya.

### Data Pre-processing
* Dilakukan data splitting menjadi data train dan data test dengan rasio 7:3
* Dilakukan Outlier Handling dengan kaidah IQR
* Dilakukan Feature Transform dengan standarisasi & label encoding 
* Karena label target memiliki rasio yang tidak seimbang, dilakukan Imbalance Class Handling dengan undersampling, oversampling, dan SMOTE kemudian melihat mana yang memiliki performa paling baik

### Data Modeling
Dilakukan data modeling dengan Logistic Regression, Random Forest, XGBoost, dan Decision Tree. <br>
Diketahui setelah melakukan cross validation, diperoleh nilai yang sudah cukup baik pada data dengan undersampling, oversampling, dan smote pada tiap algoritma model, sehingga tetap akan dilakukan testing pada tiap dataset. Dan untuk mengurangi overfit pada model, kamu juga melakukan hyperparameter tuning pada tiap algoritma model.
Hasil di bawah merupakan hasil model dengan data train dengan performa terbaik pada tiap model.

| Model  | Recall Score | Accuracy Score | Precission Score | F-1  Score | ROC AUC Score |
| ------------- | ------------- | ------------- | ------------- | ------------- | ------------- |
| Logistic Regression  | 62%  | 70%  | 40%  | 48%  | 72%  |
| Random Forest  | 63%  | 74%  | 45%  | 52%  | 77%  |
| XGBoost  | 43%  | 80%  | 56%  | 49%  | 76%  |
| Decision Tree  | 61%  | 74%  | 44%  | 51%  | 75%  |

Pada project ini, kami memfokuskan pada metrik skor Recall karena kami ingin mengurangi adanya False Negative, atau customer yang diprediksi tidak akan default payment padahal kenyataannya mengalami default payment. Dari hasil skor yang diperoleh, diketahui Algoritma model <b>Random Forest</b> memiliki performa terbaik dibanding dengan model lainnya. 
<br>
Dari confusion matrix yang diperoleh dengan model random forest, diketahui terdapat 893 dari 2100 customer yang tepat diprediksi akan melakukan default payment. 
Jika diasumsikan akan diberikan treatment khusus pada customer yang diprediksi akan gagal bayar sehingga customer tersebut berhasil bayar pada bulan depannya, maka dapat diperoleh penurunan Default Payment Rate dari 22% menjadi 17%.<br>
![](https://github.com/iqbalmudzakky/final_project/blob/main/bootcamp_notes/Screenshot%202023-05-02%20081611.png)
<br>

### Insight
* Customer dengan range usia 25-39 tahun dengan background pendidikan sarjana dan berstatus single cenderung melakukan default payment
* Limit kredit, status pembayaran, dan total tagihan bulan September memiliki pengaruh pada status payment default customer pada bulan selanjutnya

## Business Recommendation
* Bank dapat menggunakan karakteristik customer terutama limit kredit, dan status pembayaran dan total tagihan bulan September / bulan terakhir ini sebagai pertimbangan utama dalam menentukan prioritas customer yang akan diberikan treatment khusus untuk menghindari default payment.
* Memberikan treatment khusus kepada customer yang diprediksi akan melakukan default payment tentu akan membutuhkan cost yang tidak sedikit, sehingga bank perlu untuk memberikan batasan dan menentukan customer mana yang diprioritaskan untuk mendapatkan treatment. Hal ini dapat diatasi dengan membuat model baru untuk melakukan sistem scoring kepada customer sehingga lebih mudah untuk menentukan customer prioritas.
* Untuk membuat model yang lebih robust dan dapat digunakan dalam jangka panjang, sebaiknya perlu dilakukan kembali pemilihan feature yang lebih general dan dapat merepresentasikan customer lebih baik, seperti income, total aset, dsb.
