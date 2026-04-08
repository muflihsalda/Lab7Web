# Lab7Web 
# Laporan Praktikum Pemrograman Web2 (1-4)

**Nama:** Muflih Salda Maulana  
**NIM:** 312410527 
**Kelas:** I241E 


## Praktikum 1: Dasar Framework CodeIgniter 4

### Menjalankan CLI (Command Line Interface)
Codeigniter 4 menyediakan CLI untuk mempermudah proses development.

<img width="614" height="140" alt="image" src="https://github.com/user-attachments/assets/305d0efd-6d62-4d15-a3e0-8cbf2811e190" />

<img width="657" height="625" alt="image" src="https://github.com/user-attachments/assets/73baec29-5563-492f-9b61-ca765d0f679f" />



### Membuat Layout Web dengan CSS

<img width="1111" height="643" alt="dashbord web2" src="https://github.com/user-attachments/assets/cd3450c4-ae16-45cc-a0a4-e72bb94dd05c" />


## Praktikum 2: Framework Lanjutan (CRUD)

### 1. Konfigurasi Database
Membuat database `lab_ci4` dan tabel `artikel`. Koneksi diatur pada file `.env` untuk menghubungkan aplikasi dengan MySQL.

<img width="1245" height="85" alt="image" src="https://github.com/user-attachments/assets/15f37c0f-8b07-4698-bd3c-b5e86eaf1de4" />

<img width="515" height="168" alt="image" src="https://github.com/user-attachments/assets/66c45817-f41a-4842-af03-71080548e083" />


### 2. Pembuatan Model
Membuat `ArtikelModel.php` yang mewarisi class `Model` dari CodeIgniter untuk berinteraksi dengan tabel artikel di database.

<img width="564" height="292" alt="image" src="https://github.com/user-attachments/assets/73858713-c2b5-4eb5-bfe1-b824849055ff" />


### 3. Fitur Daftar Artikel 
Mengambil data dari database menggunakan fungsi `findAll()` pada Controller dan menampilkannya kepada pengguna

<img width="1146" height="631" alt="image" src="https://github.com/user-attachments/assets/4cbd8f41-568e-4e39-9f01-d2cdedef7ede" />

### 4. Detail Artikel
Menambahkan fungsi `view($slug)` untuk menampilkan konten lengkap artikel berdasarkan *slug* yang dipilih.
<img width="1249" height="676" alt="image" src="https://github.com/user-attachments/assets/0c1bce58-8441-4b92-8c08-4a2b3670ad9f" />


### 5. Manajemen Data (Admin CRUD)
Membuat fitur administrasi untuk memanipulasi data artikel:

<img width="1365" height="536" alt="dashbord_admin" src="https://github.com/user-attachments/assets/e7e9aeac-202a-4b5b-9278-f216c304ab2a" />

**Tambah (Create)**: Menggunakan form untuk menginput artikel baru ke database.
<img width="1042" height="608" alt="from_tambah" src="https://github.com/user-attachments/assets/a0d1cd99-d37e-4b7e-bde9-f53992128b5c" />

**Ubah (Update)**: Memperbarui data artikel yang sudah ada berdasarkan ID.
<img width="1033" height="605" alt="from_ubah" src="https://github.com/user-attachments/assets/661b083f-c492-41fc-9c41-1d05b1672fe4" />

**Hapus (Delete)**: Menghapus data artikel dari sistem.
<img width="1362" height="534" alt="hapus_artikel" src="https://github.com/user-attachments/assets/40c99cbf-7d42-4e65-a395-2ca66fd0c896" />
