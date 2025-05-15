# Proyek Akhir: Menyelesaikan Permasalahan Perusahaan Edutech

## Business Understanding  
Perusahaan Edutech “Jaya Jaya Learning” menyediakan platform pembelajaran daring untuk mahasiswa program sarjana di berbagai jurusan. Misi mereka adalah menurunkan angka dropout dan meningkatkan tingkat kelulusan dengan intervensi tepat waktu. Saat ini belum ada sistem pemantauan risiko dan sistem pemantauan yang dapat membantu tim akademik mengenali mahasiswa berisiko tinggi sehingga intervensi sering terlambat.

### Permasalahan Bisnis  
1. **Tingginya angka dropout**: Institusi pendidikan masih kesulitan dalam mengidentifikasi apa saja faktor faktor yang menyebabkan siswa dropout
2. **Kurangnya Pemantauan**: tidak adanya sistem pemantauan yang bersifat real time untuk mendeteksi potensi siswa dropout
3. **Intervensi terlambat**: tim akademik hanya tahu mahasiswa bermasalah setelah nilai semester turun drastis    

### Cakupan Proyek  
- Data preprocessing dan EDA pada dataset “Students’ Performance”  
- Pengembangan model klasifikasi (Logistic Regression, RandomForest) untuk memprediksi risiko dropout  
- Pembuatan dashboard analitik di Metabase untuk business monitoring  
- Pembuatan prototype Streamlit untuk prediksi real‑time 
- Export data ke Supabase PostgreSQL sebagai data source terpusat  

## Persiapan  

**Sumber data**:  
- `students_performance.csv` (4424 baris, 37 kolom) berisi demografi, prestasi akademik sem‑1 & sem‑2, dan status akhir (Dropout/Graduate/Enrolled).  
- Link Dataset : https://github.com/dicodingacademy/dicoding_dataset/blob/main/students_performance/data.csv

**Setup environment**:  

1. Buat virtual environment
```
conda create -name submission_student python=3.12.9
conda activate submission_student
```

2. Install dependencies
```
pip install requirements.txt
```

3. (Optional) untuk Metabase: tidak perlu install, cukup koneksi ke Supabase
- **Credential Supabase (untuk Metabase)**:
  - Host: `aws-0-us-east-2.pooler.supabase.com`
  - Port: `5432`
  - Database: `postgres`
  - User: `postgres.uamrqobimfgxwfswnprl`
  - Password: `<YOUR-PASSWORD>`
  - Pool mode: `session`

- **Email dan password Metabase**:
  - Email: baskoroaji2@gmail.com
  - Password: root@123

## Business Dashboard
Kami membangun dashboard Student Risk Insights di Metabase, terhubung ke Supabase Postgres.


Dashboard menampilkan 7 question utama:

1. Student count filter by status

2. Average of Admission grade filter by status

3. Average of Curricular units 1st semester grade filter by status

4. Average of Curricular units 1st semester grade filter by status

5. Student Scholarship holder filter by status

6. Student Gender filter by status

7. Student marital status filter by status

Tim bisnis dapat memfilter per status seperti dropout, enrolled, dan graduate

## Menjalankan Sistem Machine Learning
Prototype prediksi risiko mahasiswa disajikan via Streamlit app..

1. Jalankan server Streamlit:
```
    streamlit run app.py
```

2. Entry Data yang ingin digunakan

3. Lihat prediksi status (Dropout/Graduate) dengan warna label.

Link prototype:

https://studentperformance-eqensdkgjrsgndmse4bwao.streamlit.app/

## Conclusion
- Dengan model ML kami dapat memprediksi mahasiswa berisiko dropout dengan akurasi di 77 %.

- Pembuatan sistem pemantauan/dashboard secara real-time dengan metabase memudahkan tim akademik dalam mengidentifikasi tingginya angka dropout 

- Dengan adanya dashboard metabase tim akademik akan lebih mudah tau dan langsung bertindak jika ada beberapa mahasiswa yang memiliki potensi potensi dropout seperti dari nilai, umur, attendances, marital status, dan gender

- Dari analisa dashboard dan EDA faktor faktor yang menyebabkan mahasiswa/i yang dropout adalah:
  - rata rata nilai di semester 1 dan 2 yang kecil dari rata rata nilai yang kecil itu bisa dilihat performa siswa yang sedikit, 
  - umur dari mahasiswa yang dropout diatas 25tahun dimana otomatis banyak mahasiswa yang menambah semester, 
  - pengambilan kelas pagi/siang oleh mahasiswa kelas pagi/siang adalah kelas yang paling banyak dropout dimana bisa 85% dari seluruh siswa menandakan bahwa kelas pagi/siang memiliki resiko lebih besar untuk dropout, 
  - dan yang terakhir adalah marital status dari analisa dashboard bisa dilihat mahasiswa yang paling dropout adalah single, diikuti married ini menandakan bahwa sebagian besar mahasiswa yang dropout adalah single dan belum berkeluarga ini juga menjadi indikasi apakah mahasiswa itu memiliki masalah pribadi atau mungkin sedang bekerja tetapi tidak sempat menyelesaikan kuliahnya

## Rekomendasi Action Items

**1. Student Dengan grade < 10 di semester 1 & 2**
Rekomendasi: Dengan kecilnya performa mahasiswa pada semester 1 dan 2 tim akademik harus menintervensi langsung mahasiswa melewati dosen pembimbing akademik untuk mengetahui alasan kenapa kecilnya performa siswa

**2. Konsultasi Mahasiswa/Siswa/Mahasiswi/Siswi**
Rekomendasi: Karena banyaknya dropout dari mahasiswa perempuan walaupun hanya sedikit lebih banyak dari laki laki harus ada penelusuran lebih lanjut apakah perempuan itu memiliki masalah dihidupnya atau apakah dia sudah menikah, Langkah paling bijak adalah memberikan konsultasi agar bisa menyelesaikan studinya

**3. Course yang paling banyak dropout**
Rekomendasi: Mempaketkan Kelas/SKS guna membantu percepatan kelulusan di semester awal perkuliahan, diadakannya kelas tambahan untuk para mahasiswa yang belum mengerti materi

**4. Umur dari mahasiswa**
Rekomendasi: dari dashboard umur mahasiswa yang dropout rata rata di angka 26, ini sudah pasti mereka yang memiliki semester sampai 10 keatas. Solusi paling bijak adalah pembimbing akademik merangkul mahasiswa yang sudah berada di semester diatas 10 agar lebih cepat lulus

**5. Marital Status**
Rekomendasi: dari dashboard dapat dilihat bahwa mahasiswa yang dropout kebanyakan adalah single, diikuti married, dan divorced. Solusi paling bijak memberikan konsultasi dan merangkul mahasiswa untuk menyelesaikan studinya, apalagi dalam status menikah dan cerai dosen pembimbing akademik harus berusaha lebih ekstra untuk menyemangati mereka untuk menyelesaikan studi

**6. Survey mahasiswa yang sedang bekerja sampingan**
Rekomendasi: dari banyaknya faktor penyebab mahasiswa dropout, salah satunya umur dan marital status perlu adanya survey apakah mahasiswa juga sedang bekerja sampingan atau tidak, karena terkadang mahasiswa yang sudah nyaman dengan pekerjaan bisa lupa untuk menyelesaikan kuliah
