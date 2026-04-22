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

# Praktikum 3 - View Layout & View Cell (CodeIgniter 4)

## Langkah-Langkah Pengerjaan

### 1. Membuat Template Layout

Pada tahap ini dibuat file:

* `header.php`
* `footer.php`

Fungsi:

* `header.php` digunakan untuk bagian atas (judul, navbar, CSS)
* `footer.php` digunakan untuk bagian bawah (footer dan sidebar)

Kemudian dipanggil pada setiap halaman menggunakan:

```php
<?= $this->include('template/header'); ?>
<?= $this->include('template/footer'); ?>
```

---

### 2. Membuat Struktur Layout

Struktur halaman dibagi menjadi:

* Header
* Navigasi
* Konten utama (`main`)
* Sidebar (`aside`)
* Footer

Sehingga tampilan menjadi lebih rapi dan konsisten di setiap halaman.

---

### 3. Membuat View Cell

View Cell digunakan untuk membuat komponen dinamis.

File yang dibuat:

* `app/Cells/ArtikelTerkini.php`

Berfungsi untuk mengambil data artikel terbaru dari database:

```php
$artikel = $model->orderBy('id', 'DESC')->limit(5)->findAll();
```

---

### 4. Membuat View untuk View Cell

File:

* `app/Views/artikel/terkini.php`

Digunakan untuk menampilkan daftar artikel terbaru dalam bentuk list.

---

### 5. Menampilkan View Cell

View Cell dipanggil pada bagian sidebar:

```php
<?= view_cell('App\\Cells\\ArtikelTerkini::render') ?>
```

Sehingga sidebar akan menampilkan artikel terbaru secara otomatis.

---

### 6. Integrasi dengan Halaman Artikel

Pada file `index.php`, halaman utama artikel tetap menggunakan template:

```php
<?= $this->include('template/header'); ?>
```

dan

```php
<?= $this->include('template/footer'); ?>
```

Sedangkan sidebar diambil dari View Cell.

---

## Hasil Tampilan

<img width="1120" height="646" alt="image" src="https://github.com/user-attachments/assets/08a70846-3674-4e9e-8b0f-2322098266f9" />

Hasil dari praktikum ini adalah:

* Tampilan website menjadi lebih rapi
* Layout terbagi menjadi dua kolom (konten dan sidebar)
* Sidebar menampilkan artikel terbaru secara dinamis
* Tampilan sesuai dengan desain pada modul praktikum

---
# Praktikum 4 - Pagination & Pencarian Artikel (CodeIgniter 4)


## Langkah-Langkah Pengerjaan

### 1. Mengubah Controller

File yang diubah:

* `app/Controllers/Artikel.php`

Pada function `index()`, ditambahkan fitur pencarian dan pagination:

```php
public function index()
{
    $model = new \App\Models\ArtikelModel();

    $q = $this->request->getGet('q');

    if ($q) {
        $artikel = $model->like('judul', $q)
                         ->paginate(5);
    } else {
        $artikel = $model->paginate(5);
    }

    return view('artikel/index', [
        'title'   => 'Daftar Artikel',
        'artikel' => $artikel,
        'pager'   => $model->pager,
        'q'       => $q
    ]);
}
```

---

### 2. Menambahkan Form Pencarian

File yang diubah:

* `app/Views/artikel/index.php`

Ditambahkan form untuk mencari artikel:

```php
<form method="get">
    <input type="text" name="q" value="<?= $q; ?>" placeholder="Cari artikel...">
    <button type="submit">Cari</button>
</form>
```

---

### 3. Menampilkan Hasil Pencarian

Masih di file yang sama, ditambahkan informasi keyword:

```php
<?php if ($q): ?>
    <p>Hasil pencarian untuk: <b><?= $q; ?></b></p>
<?php endif; ?>
```

---

### 4. Menambahkan Pagination

Pagination ditampilkan di bagian bawah daftar artikel:

```php
<?= $pager->links(); ?>
```

---

### 5. Menambahkan Styling Pagination

File yang diubah:

* `public/style.css`

Ditambahkan CSS agar pagination tampil lebih rapi:

```css
.pagination {
    display: flex;
    list-style: none;
    padding: 0;
    margin-top: 20px;
}

.pagination li {
    margin-right: 5px;
}

.pagination li a,
.pagination li span {
    display: block;
    padding: 6px 12px;
    background: #2f5fa5;
    color: #fff;
    text-decoration: none;
    border-radius: 3px;
}

.pagination li.active span {
    background: #1d3c73;
}
```

---

## Hasil Tampilan

<img width="948" height="581" alt="image" src="https://github.com/user-attachments/assets/3b27efd2-8483-4495-bf77-74f455a814cb" />

Hasil dari praktikum ini:

* Artikel ditampilkan per halaman (pagination)
* Terdapat tombol navigasi halaman (1, 2, 3, dst)
* Pengguna dapat mencari artikel berdasarkan judul
* Tampilan lebih rapi dan interaktif

---


