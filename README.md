## EXPLORATORY DATA ANAYSIS<br>
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
Diketahui setelah melakukan cross validation, 
