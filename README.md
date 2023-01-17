Praktikum 11
Nama   : riski probo sadewo
NIM    : 312210191
Kelas  : TI.22.A2

# Laporan Praktikum 11
Instruksi Praktikum

 1 Persiapkan text editor misalnya VSCode.
 2 Buat folder baru dengan nama lab11_php_ci pada docroot webserver (htdocs)
 3 Ikuti langkah-langkah praktikum yang akan dijelaskan berikutnya.
# Langkah-langkah Praktikum
### Persiapan
Sebelum memulai menggunakan Framework Codeigniter, perlu dilakukan konfigurasi pada webserserver. Beberapa ekstensi PHP perlu diaktifkan untuk kebutuhan pengembangan Codeigniter 4.

Berikut beberapa ekstensi yang perlu diaktifkan: • php-json ekstension untuk bekerja dengan JSON; • php-mysqlnd native driver untuk MySQL; • php-xml ekstension untuk bekerja dengan XML; • php-intl ekstensi untuk membuat aplikasi multibahasa; • libcurl (opsional), jika ingin pakai Curl.

Untuk mengaktifkan ekstentsi tersebut, melalui XAMPP Control Panel, pada bagian Apache klik Config -> PHP.ini

![image](https://user-images.githubusercontent.com/115862112/212901979-aea53443-fc7d-401f-be2f-70a1a5ce05e1.png)


Pada bagian extention, hilangkan tanda ; (titik koma) pada ekstensi yang akan diaktifkan. Kemudian simpan kembali filenya dan restart Apache web server.

![image](https://user-images.githubusercontent.com/115862112/212902314-e8d70923-f55e-406c-b6e5-effd6e20659d.png)

# Instalasi Codeigniter 4
Untuk melakukan instalasi Codeigniter 4 dapat dilakukan dengan dua cara, yaitu cara manual dan menggunakan composer. Pada praktikum ini kita menggunakan cara manual.

- Unduh Codeigniter dari website https://codeigniter.com/download
- Extrak file zip Codeigniter ke direktori htdocs/lab11_ci.
- Ubah nama direktory framework-4.x.xx menjadi ci4.
- Buka browser dengan alamat http://localhost/lab11_php_ci/ci4/public/

![image](https://user-images.githubusercontent.com/115862112/212902502-41a041e5-a7a0-43c2-ab6d-210c32613410.png)


## Menjalankan CLI (Command Line Interface)
Codeigniter 4 menyediakan CLI untuk mempermudah proses development. Untuk mengakses CLI buka terminal/command prompt.

![image](https://user-images.githubusercontent.com/115862112/212902599-19962cbc-5021-46de-95e0-489e429cb990.png)

Arahkan lokasi direktori sesuai dengan direktori kerja project dibuat (xampp/htdocs/lab11_ci/ci4/)

Perintah yang dapat dijalankan untuk memanggil CLI Codeigniter adalah:
```
php spark
```
![image](https://user-images.githubusercontent.com/115862112/212902698-5073d6a2-7ddd-4542-93a8-7d0a44da1b76.png)

# Mengaktifkan Mode Debugging
Codeigniter 4 menyediakan fitur debugging untuk memudahkan developer untuk mengetahui pesan error apabila terjadi kesalahan dalam membuat kode program. Secara default fitur ini belum aktif.

Ketika terjadi error pada aplikasi akan ditampilkan pesan kesalahan seperti berikut.

![image](https://user-images.githubusercontent.com/115862112/212902863-c221b52d-501c-4dbf-88a8-f55943390cda.png)

Semua jenis error akan ditampilkan sama. Untuk memudahkan mengetahui jenis errornya, maka perlu diaktifkan mode debugging dengan mengubah nilai konfigurasi pada environment variable CI_ENVIRINMENT menjadi development.

![image](https://user-images.githubusercontent.com/115862112/212902972-ae99dc0e-9c37-4a56-ab6e-5c03adfb8bbc.png)

Ubah nama file env menjadi .env kemudian buka file tersebut dan ubah nilai variable CI_ENVIRINMENT menjadi development.

Kemudian ubah file production.php dalam folder app\Config\Boot, ganti value "0" menjadi "1", untuk memunculkan error pada halaman

![image](https://user-images.githubusercontent.com/115862112/212903079-a3038423-dbb3-4f44-870c-63a36bc64156.png)

Sebagai contoh ubah file app/Controller/Home.php dengan menghilangkan titik koma (;) pada akhir kode.

![image](https://user-images.githubusercontent.com/115862112/212903143-4f47a9fc-3243-467e-86c0-2bad101d06e3.png)

Selanjutnya load ulang halaman untuk melihat hasil error yang muncul :

![image](https://user-images.githubusercontent.com/115862112/212903288-d4675720-3859-4e36-8b67-3ab50fd10c74.png)

## Struktur Direktori
Untuk lebih memahami Framework Codeigniter 4 perlu mengetahui struktur direktori dan file yang ada. Buka pada Windows Explorer atau dari Visual Studio Code -> Open Folder.

Terdapat beberapa direktori dan file yang perlu dipahami fungsi dan kegunaannya.

- .github folder ini kita butuhkan untuk konfigurasi repo github, seperti konfigurasi untuk build dengan github action;
- app folder ini akan berisi kode dari aplikasi yang kita kembangkan;
- public folder ini berisi file yang bisa diakses oleh publik, seperti file index.php, robots.txt, favicon.ico, ads.txt, dll;
- tests folder ini berisi kode untuk melakukan testing dengna PHPunit;
- vendor folder ini berisi library yang dibutuhkan oleh aplikasi, isinya juga termasuk kode core dari system CI.
- writable folder ini berisi file yang ditulis oleh aplikasi. Nantinya, kita bisa pakai untuk menyimpan file yang di-upload, logs, session, dll. Sedangkan file-file yang berada pada root direktori CI sebagai berikut.
- .env adalah file yang berisi variabel environment yang dibutuhkan oleh aplikasi.
- .gitignore adalah file yang berisi daftar nama file dan folder yang akan diabaikan oleh Git.
- build adalah script untuk mengubah versi codeigniter yang digunakan. Ada versi release (stabil) dan development (labil).
- composer.json adalah file JSON yang berisi informasi tentang proyek dan daftar library yang dibutuhkannya. File ini digunakan oleh Composer sebagai acuan.
- composer.lock adalah file yang berisi informasi versi dari libraray yang digunakan aplikasi.
- license.txt adalah file yang berisi penjelasan tentang lisensi Codeigniter;
- phpunit.xml.dist adalah file XML yang berisi konfigurasi untuk PHPunit.
- README.md adalah file keterangan tentang codebase CI. Ini biasanya akan dibutuhkan pada repo github atau gitlab.
- spark adalah program atau script yang berfungsi untuk menjalankan server, generate kode, dll.

![image](https://user-images.githubusercontent.com/115862112/212903899-ae97ac16-9df6-4f02-89b2-015c1dc0930e.png)

Fokus kita pada folder app, dimana folder tersebut adalah area kerja kita untuk membuat aplikasi. Dan folder public untuk menyimpan aset web seperti css, gambar, javascript, dll.

## Memahami Konsep MVC
Codeigniter menggunakan konsep MVC. MVC meripakan singkatan dari Model-View-Controller. MVC merupakan konsep arsitektur yang umum digunakan dalam pengembangan aplikasi. Konsep MVC adalah memisahkan kode program berdasarkan logic proses, data, dan tampilan. Untuk logic proses diletakkan pada direktori Contoller, Objek data diletakkan pada direktori Model, dan desain tampilan diletakkan pada direktori View.

Codeigniter menggunakan konsep pemrograman berorientasi objek dalam mengimplementasikan konsep MVC.

Model merupakan kode program yang berisi pemodelan data. Data dapat berupa database ataupun sumber lainnya.

View merupakan kode program yang berisi bagian yang menangani terkait tampilan user interface sebuah aplikasi. didalam aplikasi web biasanya pasti akan berhubungan dengan html dan css.

Controller merupakaan kode program yang berkaitan dengan logic proses yang menghubungkan antara view dan model. Controller berfungsi untuk menerima request dan data dari user kemudian diproses dengan menghubungkan bagian model dan view.

Routing dan Controller Routing merupakan proses yang mengatur arah atau rute dari request untuk menentukan fungsi/bagian mana yang akan memproses request tersebut. Pada framework CI4, routing bertujuan untuk menentukan Controller mana yang harus merespon sebuah request. Controller adalah class atau script yang bertanggung jawab merespon sebuah request.

Pada Codeigniter, request yang diterima oleh file index.php akan diarahkan ke Router untuk meudian oleh router tesebut diarahkan ke Controller.

Router terletak pada file app/config/Routes.php

![image](https://user-images.githubusercontent.com/115862112/212904115-52f8b95d-d643-4929-9019-bdf21b3ae4bb.png)

Pada file tersebut kita dapat mendefinisikan route untuk aplikasi yang kita buat.
```
$routes->get('/', 'Home::index');
```
Kode tersebut akan mengarahkan rute untuk halaman home.

## Membuat Route Baru
Tambahkan kode berikut di dalam Routes.php
```
$routes->get('/about', 'Page::about');
$routes->get('/contact', 'Page::contact');
$routes->get('/faqs', 'Page::faqs');
```
Untuk mengetahui route yang ditambahkan sudah benar, buka CLI dan jalankan perintah berikut.
```
php spark routes
```
![image](https://user-images.githubusercontent.com/115862112/212904492-3e119d27-0286-4eb5-8773-e27110972019.png)

Selanjutnya coba akses route yang telah dibuat dengan mengakses alamat url http://localhost:8080/about

![image](https://user-images.githubusercontent.com/115862112/212904553-80cff2cf-7f7a-4ca3-a994-5c5c8ea0a8f3.png)

Ketika diakses akan mucul tampilan error 404 file not found, itu artinya file/page tersebut tidak ada. Untuk dapat mengakses halaman tersebut, harus dibuat terlebih dahulu Contoller yang sesuai dengan routing yang dibuat yaitu Contoller Page.

Membuat Controller
Selanjutnya adalah membuat Controller Page. Buat file baru dengan nama page.php pada direktori Controller kemudian isi kodenya seperti berikut.
```
<?php
namespace App\Controllers;
class Page extends BaseController
{
 public function about()
 {
 echo "Ini halaman About";
 }
 public function contact()
 {
 echo "Ini halaman Contact";
 }
 public function faqs()
 {
 echo "Ini halaman FAQ";
 }
}
```
Selanjutnya refresh Kembali browser, maka akan ditampilkan hasilnya yaitu halaman sudah dapat diakses.

![image](https://user-images.githubusercontent.com/115862112/212905068-40de89c9-01b9-4845-a2d4-b78cf44971e8.png)

## Auto Routing
Secara default fitur autoroute pada Codeiginiter sudah aktif. Untuk mengubah status autoroute dapat mengubah nilai variabelnya. Untuk menonaktifkan ubah nilai true menjadi false.
```
$routes->setAutoRoute(true);
```
Tambahkan method baru pada Controller Page seperti berikut
```
public function tos()
{
 echo "ini halaman Term of Services";
}
```
Method ini belum ada pada routing, sehingga cara mengaksesnya dengan menggunakan alamat: http://localhost:8080/page/tos

![image](https://user-images.githubusercontent.com/115862112/212905322-82ecd84f-ae02-4cc8-a075-186163251307.png)

## Membuat View
Selanjutnya adalam membuat view untuk tampilan web agar lebih menarik. Buat file baru dengan nama about.php pada direktori view (app/view/about.php) kemudian isi kodenya seperti berikut.
```
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title><?= $title; ?></title>
</head>
<body>
	<h1><?= $title; ?></h1>
	<hr>
	<p><?= $content; ?></p>
</body>
</html>
```
Ubah method about pada class Controller Page menjadi seperti berikut:
```
public function about()
{
	return view('about', [
		'title' => 'Halaman Abot',
		'content' => 'Ini adalah halaman abaut yang menjelaskan tentang isi halaman ini.'
	]);
}
```
Kemudian lakukan refresh pada halaman tersebut.

![image](https://user-images.githubusercontent.com/115862112/212905649-4fb07218-ccc0-45ce-907c-027db2d1d7b4.png)

Membuat Layout Web dengan CSS
Pada dasarnya layout web dengan css dapat diimplamentasikan dengan mudah pada codeigniter. Yang perlu diketahui adalah, pada Codeigniter 4 file yang menyimpan asset css dan javascript terletak pada direktori public.

Buat file css pada direktori public dengan nama style.css (copy file dari praktikum lab4_layout. Kita akan gunakan layout yang pernah dibuat pada praktikum 4.

![image](https://user-images.githubusercontent.com/115862112/212905814-37a64c02-15aa-48f0-b3f2-58a57e3e1421.png)


Kemudian buat folder template pada direktori view kemudian buat file header.php dan footer.php

File app/view/template/header.php
```
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title><?= $title; ?></title>
	<link rel="stylesheet" href="<?= base_url('/style.css');?>">
</head>
<body>
	<div id="container">
	<header>
		<h1>Layout Sederhana</h1>
	</header>
	<nav>
		<a href="<?= base_url('/');?>" class="active">Home</a>
		<a href="<?= base_url('/artikel');?>">Artikel</a>
		<a href="<?= base_url('/about');?>">About</a>
		<a href="<?= base_url('/contact');?>">Kontak</a>
	</nav>
	<section id="wrapper">
		<section id="main">
```

File app/view/template/footer.php

```
	</section>
	<aside id="sidebar">
			<div class="widget-box">
				<h3 class="title">Widget Header</h3>
				<ul>
					<li><a href="#">Widget Link</a></li>
					<li><a href="#">Widget Link</a></li>
				</ul>
			</div>
			div class="widget-box">
				<h3 class="title">Widget Text</h3>
				<p>Vestibulum lorem elit, iaculis in nisl volutpat, malesuada tincidunt arcu. Proin in leo fringilla, vestibulum mi porta, faucibus felis. Integer pharetra est nunc, nec pretium nunc pretium ac.</p>
			</div>
		</aside>
	</section>
	<footer>
		<p>&copy; 2021 - Universitas Pelita Bangsa</p>
	</footer>
	</div>
</body>
</html>
```

Kemudian ubah file app/view/about.php seperti berikut.

```
<?= $this->include('template/header'); ?>

<h1><?= $title; ?></h1>
<hr>
<p><?= $content; ?></p>

<?= $this->include('template/footer'); ?>
```
Selanjutnya refresh tampilan pada alamat http://localhost:8080/about

![image](https://user-images.githubusercontent.com/115862112/212906317-6ab3c44e-9a56-41d0-821d-9407c5d01d80.png)

## Pertanyaan dan Tugas
Lengkapi kode program untuk menu lainnya yang ada pada Controller Page, sehingga semua link pada navigasi header dapat menampilkan tampilan dengan layout yang sama.

# Laporan Praktikum
1 Buatlah repository baru dengan nama Lab11Web.
2 Kerjakan semua latihan yang diberikan sesuai urutannya.
3 Screenshot setiap perubahannya.
4 Buatlah file README.md dan tuliskan penjelasan dari setiap langkah praktikum beserta screenshotnya.
5 Commit hasilnya pada repository masing-masing.
6 Kirim URL repository pada e-learning ecampus
Jawaban :

Pertama, lakukan perubahan atau tambahkan pada file app/config/routes.php
File routes.php :

![image](https://user-images.githubusercontent.com/115862112/212906716-4d9d19da-87d1-4c18-bc51-817917210770.png)


Kedua, lakukan pengeditan atau tambahkan pada file app/controllers/page.php
File page.php :

![image](https://user-images.githubusercontent.com/115862112/212906771-abc3c6f7-7a7e-4cbd-8fd7-0c39bd0aeeb2.png)


Ketiga, buat file baru atau tambahkan file pada direktori view app/views
File home.php :

![image](https://user-images.githubusercontent.com/115862112/212906876-2a702d44-dd1f-43be-9991-4faf683ec939.png)


File article.php :

![image](https://user-images.githubusercontent.com/115862112/212907098-f49c1201-ea8b-4bf6-85ec-cc58405ba191.png)


File contact.php :

![image](https://user-images.githubusercontent.com/115862112/212907133-b172998d-d646-429c-9fa0-02851220ebf2.png)


File faqs.php :

![image](https://user-images.githubusercontent.com/115862112/212907207-d9d96705-0567-41dc-bf89-a7d0b585e991.png)


File tos.php :

![image](https://user-images.githubusercontent.com/115862112/212907234-6b6aa970-31bf-4901-9c13-8ebb5b5439cd.png)


Keempat, tambahkan template baru (di app/views/template) yang di perlukan pada direktori app/view
File kontak.php :

![image](https://user-images.githubusercontent.com/115862112/212907301-518b8f77-ef13-4cac-b18b-14329a1c5ec5.png)


File visimis.php :

![image](https://user-images.githubusercontent.com/115862112/212907396-8b6e3521-3d95-42e3-8632-a69d9810e48f.png)


Kelima cek hasil semua tampilan semua layout
Tampilan layout Home :

![image](https://user-images.githubusercontent.com/115862112/212907446-388ab29f-fdc6-4ddf-974d-053c07928f70.png)


Tampilan layout Artikel :

![image](https://user-images.githubusercontent.com/115862112/212907570-5f2fc8c6-2e0e-4371-bc90-3135ea793cf4.png)


Tampilan layout About :

![image](https://user-images.githubusercontent.com/115862112/212907729-6d170363-7d2b-4b44-94c7-9040ce362355.png)


Tampilan layout Kontak :

![image](https://user-images.githubusercontent.com/115862112/212907757-fc88d4f3-fda8-4f13-9fa1-4529e914837b.png)

Tampilan layout Pertanyaan dan Jawaban :

![image](https://user-images.githubusercontent.com/115862112/212907816-d96e6c56-cafc-46d1-a13c-e2e25f56ec91.png)

Tampilan layout Terms Of Services :

![image](https://user-images.githubusercontent.com/115862112/212907860-528c1e48-f36f-4f02-9f17-79588cda9cfb.png)

# Praktikum 12 | Framework Lanjutan (CRUD)
### 1. Database
- Jalankan Apache, MySql pada Xampp, Buat database dengan nama lab_ci4 di http://localhost/phpmyadmin.
- Buat tabel dengan nama artikel.
```
CREATE TABLE artikel (
    id INT(11) auto_increment,
    judul VARCHAR(200) NOT NULL,
    isi TEXT,
    gambar VARCHAR(200),
    status TINYINT(1) DEFAULT 0,
    slug VARCHAR(200),
    PRIMARY KEY(id)
);
```

![image](https://user-images.githubusercontent.com/115862112/212908109-64771440-9d48-4e01-a937-d00c95e191a3.png)

2. Konfigurasi Koneksi Database
- Terletak di folder ci4, file .env, Hapus tanda #. img27

![image](https://user-images.githubusercontent.com/115862112/212908135-f7922f7f-b0a9-418e-8525-24fb8571bef9.png)

3. Membuat Model
-  Terletak di folder app/Models, buat file ArtikelModel.php. img27

![image](https://user-images.githubusercontent.com/115862112/212908246-91053232-bde9-4097-bea8-9ae9882bd623.png)

4. Membuat Controller
- Terletak di folder app/Controllers, buat file Artikel.php. img27

![image](https://user-images.githubusercontent.com/115862112/212908282-07e387f8-9d07-4d22-9e19-3dd02657ea8c.png)

5. Membuat View pada artikel
- Terletak di folder app/Views/artikel, buat file index.php. img27

![image](https://user-images.githubusercontent.com/115862112/212908315-95f36dc5-8758-438a-ad81-acdb81ff4cfd.png)

Buka browser, ketik http://localhost:8080/artikel

![image](https://user-images.githubusercontent.com/115862112/212908447-810bee71-b549-401c-8947-5c622ddb43ca.png)

- Masukkan data ke tabel artikel,
```
INSERT INTO artikel (judul, isi, slug) VALUE
('Artikel pertama', 'Lorem Ipsum adalah contoh teks atau dummy dalam industri 
percetakan dan penataan huruf atau typesetting. Lorem Ipsum telah menjadi 
standar contoh teks sejak tahun 1500an, saat seorang tukang cetak yang tidak 
dikenal mengambil sebuah kumpulan teks dan mengacaknya untuk menjadi sebuah 
buku contoh huruf.', 'artikel-pertama'), 
('Artikel kedua', 'Tidak seperti anggapan banyak orang, Lorem Ipsum bukanlah 
teks-teks yang diacak. Ia berakar dari sebuah naskah sastra latin klasik dari 
era 45 sebelum masehi, hingga bisa dipastikan usianya telah mencapai lebih 
dari 2000 tahun.', 'artikel-kedua');
Refresh kembali browser. img34
```

6. Membuat Tampilan detail Artikel
- Terletak di folder app/Controllers, edit file Artikel.php. Tambah method view().

![image](https://user-images.githubusercontent.com/115862112/212908650-a1f0b026-4b2a-4d58-a18b-8674b570cee8.png)

7. Membuat View pada Detail
- Terletak di folder app/Views/artikel, buat file detail.php. img36

![image](https://user-images.githubusercontent.com/115862112/212908716-03bd840c-7d80-4639-b175-42157b151fdc.png)

8. Membuat Routing untuk artikel detail
- Terletak di folder app/Config, edit file Routes.php. 

![image](https://user-images.githubusercontent.com/115862112/212908812-a7886f40-585b-4a5c-a5c4-3230ded55dbe.png)

- Klik Artikel Kedua pada http://localhost:8080/artikel, untuk pindah ke detailnya. 

![image](https://user-images.githubusercontent.com/115862112/212908897-42276953-3f81-4659-af6b-a0506b304ce3.png)

9. Membuat Menu admin
- Terletak di folder app/Controller, edit file Artikel.php. Tambah method admin_index(). 

![image](https://user-images.githubusercontent.com/115862112/212909027-ec98713f-5d8d-4225-94bc-b8e1cf54b283.png)

- Selanjutnya, akses kembali folder app/Views/artikel, buat file admin_index.php.

![image](https://user-images.githubusercontent.com/115862112/212909071-ae7495ab-49ef-461e-b1d4-4ae881b03ffc.png)

- Buka folder yang ada di app/Views/template, kemudian buat:
admin_header.php,

![image](https://user-images.githubusercontent.com/115862112/212909285-f4df4be6-ff96-4712-baf1-1d2ed9b793c4.png)

- admin_footer.php 

![image](https://user-images.githubusercontent.com/115862112/212909644-35cd4683-6102-40c8-9e47-393dd2e393b1.png)


10. Membuat Routing untuk menu admin
- Terletak di folder app/Config, edit file Routes.php. 

![image](https://user-images.githubusercontent.com/115862112/212909735-569ebff6-3f59-4f0d-ab42-326eabffe872.png)

- Akses browser dengan http://localhost:8080/admin/artikel. 

![image](https://user-images.githubusercontent.com/115862112/212909864-815d5912-4522-4a42-b799-bb03e071e41f.png)


11. Menambah data untuk Artikel
- Terletak di folder app/Controller, edit file Artikel.php. Tambah method add(). 

![image](https://user-images.githubusercontent.com/115862112/212910193-a0178a61-b1f4-4266-a5ca-af0f15401776.png)

- Akses kembali folder app/Views/artikel, buat file form_add.php. 

![image](https://user-images.githubusercontent.com/115862112/212910261-4ff7b230-4160-4487-8d21-8f5ba4feaebd.png)


- Akses browser dengan http://localhost:8080/admin/artikel/add. img43

![image](https://user-images.githubusercontent.com/115862112/212910333-7bfb1cdc-48c9-46a1-9035-1216f8d97a52.png)

12. Mengubah data pada Artikel
Terletak di folder app/Controller, edit file Artikel.php. Tambah method edit().

![image](https://user-images.githubusercontent.com/115862112/212910397-19848bbd-ac25-4b20-9344-015225e7b7db.png)


- Akses kembali folder app/Views/artikel, buat file form_edit.php. img45

![image](https://user-images.githubusercontent.com/115862112/212910483-d53bdb33-214c-4cc2-9cd8-510cba0b042e.png)

- Akses browser dengan http://localhost:8080/admin/artikel/edit/3 untuk Mengubah artikel pertama. 

![image](https://user-images.githubusercontent.com/115862112/212910578-84dcfc7a-9c01-47d8-806d-e66928d3b96e.png)


13. Menghapus data pada Artikel
- Terletak di folder app/Controller, edit file Artikel.php. Tambah method delete(). 

![image](https://user-images.githubusercontent.com/115862112/212910641-c1b0fbc6-1762-4e81-a54a-98f0a4877ecd.png)


- Akses browser dengan http://localhost:8080/admin/artikel/add untuk membuat artikel ketiga, lalu kirim. img48

![image](https://user-images.githubusercontent.com/115862112/212910697-27a4c44e-09c0-4d98-8f3c-54779e0fe139.png)

- Untuk mengeceknya ketik di url, http://localhost:8080/artikel kemudian enter. 

![image](https://user-images.githubusercontent.com/115862112/212910771-a8308089-0e90-45f4-b902-d93c0ac4e41e.png)

- Pergi ke menu admin untuk menghapusnya, http://localhost:8080/admin/artikel, kemudian pilih hapus.

![image](https://user-images.githubusercontent.com/115862112/212910839-8913b9b5-24c4-4f2f-a2d4-97286890585f.png)

- Artikel berhasil dihapus.

![image](https://user-images.githubusercontent.com/115862112/212910913-259ad0db-0e69-4824-8f60-bd2fb4fc7099.png)

### Praktikum 13 | Framework Lanjutan (Modul Login)
1. Membuat Table User
- Jalankan Apache, MySql pada Xampp, Akses browser http://localhost/phpmyadmin.
- Buat tabel dengan nama artikel.
```   
   CREATE TABLE user (
    id INT(11) auto_increment,
    username VARCHAR(200) NOT NULL,
    useremail VARCHAR(200),
    userpassword VARCHAR(200),
    PRIMARY KEY(id)
    );
```

![image](https://user-images.githubusercontent.com/115862112/212911187-daec037b-5d06-41b7-b9c5-5c49f2c6dfb5.png)

2. Membuat Model User
- Terletak di folder app/Models, buat file UserModel.php. img53

![image](https://user-images.githubusercontent.com/115862112/212911250-1f5ecf80-c91c-4185-a995-cd348bd31e54.png)

3. Membuat Controller User
- Terletak di folder app/Controllers, buat file User.php.

![image](https://user-images.githubusercontent.com/115862112/212911346-7802e86c-e7a1-471d-895f-5c41e6e1d9b0.png)

4. Membuat View Login
- Terletak di folder app/Views, buat folder baru dengan nama user, buat file login.php di dalamnya. 

![image](https://user-images.githubusercontent.com/115862112/212911464-1cbcda83-42ff-427b-a59c-d1fe01f11ad5.png)

5. Membuat Database Seeder
- Untuk keperluan uji coba.
- Masuk ke direktori ci4, kemudian ketikkan kode: php spark make:seeder UserSeeder 

![image](https://user-images.githubusercontent.com/115862112/212911586-36e3c16a-d054-4eea-9557-11f5491ecc3f.png)


- Terletak di folder app/Database/Seeds, buka file UserSeeder.php, kemudian edit menjadi berikut: 

![image](https://user-images.githubusercontent.com/115862112/212911691-583bde6e-2fa2-4d45-a9aa-3b18dc95bdf3.png)

- Buka kembali CLI, kemudian ketik perintah berikut: php spark db:seed UserSeeder 

![image](https://user-images.githubusercontent.com/115862112/212911769-c292ec50-d883-42a9-a967-20407e181f7c.png)

- Berikut data yang sudah ditambah pada tabel user. Dengan mengakses http://localhost/phpmyadmin. 

![image](https://user-images.githubusercontent.com/115862112/212911874-2d9dd13d-dbc4-4643-ba52-d45af5c58a49.png)


- Buka file .env, kemudian hapus # pada app.sessionX 

![image](https://user-images.githubusercontent.com/115862112/212911983-1e2da145-32a7-4471-b3e2-e41efee64031.png)

- Akses kembali url http://localhost:8080/user/login 

![image](https://user-images.githubusercontent.com/115862112/212912080-42be8961-0372-48fc-ade1-bf6affe3622b.png)


## 6. Menambah Auth Filter
- Terletak di folder app/Filters, buat file Auth.php 

![image](https://user-images.githubusercontent.com/115862112/212901048-9bd5e7fb-deb2-4960-a656-f6565b4acea3.png)


- Kemudian pada folder app/Config, edit isi file Filters.php menjadi berikut: 

![image](https://user-images.githubusercontent.com/115862112/212899266-1d984924-6513-420e-b559-27d78e464532.png)


- Untuk mencobanya, akses http://localhost:8080/index.php/user/login, lalu tekan Enter. 

![image](https://user-images.githubusercontent.com/115862112/212899036-ab240f5a-9d76-4697-a137-87e40b00fcc6.png)


- Dan anda akan di alihkan pada tampilan halaman login.

- Masuk dengan alamat login email admin@email.com, dan password admin123, selanjutnya tekan login.

![image](https://user-images.githubusercontent.com/115862112/212898687-43f2b6d0-6195-4761-8e61-2ccf34200fec.png)

- Berhasil masuk sebagai admin, dan semua menu dapat diakses.Untuk mencobanya klik menu Artikel. 

![image](https://user-images.githubusercontent.com/115862112/212898579-5e0d279b-704c-4cde-9990-2e2521c1802c.png)

- Kemudian klik menu Login Admin, untuk diarahkan ke http://localhost:8080/admin/artikel.

![image](https://user-images.githubusercontent.com/115862112/212898411-64afe3ff-8278-4251-9a09-84b97bd4e5dc.png)

- Maka akan masuk ke menu admin sebelumnya, tidak login ulang. 

![image](https://user-images.githubusercontent.com/115862112/212898265-1527bcf6-f2f8-4375-beb2-86613c3522a5.png)

# 7. Membuat Fungsi Logout
- Menambah method logout().
- Terletak di folder app/Controllers, buka file User.php, kemudian edit menjadi berikut: 

![image](https://user-images.githubusercontent.com/115862112/212898087-2a4b5525-d563-4054-b853-19ae15a50f84.png)

- Untuk mencobanya, klik menu Logout. 

![image](https://user-images.githubusercontent.com/115862112/212897953-29ad9f3e-3edf-4882-a219-00220b665977.png)


- Maka akan langsung diarahkan untuk login ulang, sebelum bisa mengakses menu admin. 

![image](https://user-images.githubusercontent.com/115862112/212897859-ac518f69-dd61-4cee-9368-e657b2b59d76.png)



- Namun, untuk http://localhost:8080/artikel masih dapat diakses. 

![image](https://user-images.githubusercontent.com/115862112/212897681-4e711f4b-2443-4da7-a9ce-b2e7e0223e37.png)

# Praktikum 14 | Pagination dan Pencarian
## 1. Membuat Pagination
- Terletak di folder app/Controllers, buka file Artikel.php. Ubah menjadi berikut : 

![image](https://user-images.githubusercontent.com/115862112/212897442-c3f4fbbf-9683-4b09-9914-6126f2550126.png)

- Terletak di folder app/Views/artikel, buka file admin_index.php, tambah kode berikut : <?= $pager->links(); ?> 

![image](https://user-images.githubusercontent.com/115862112/212897150-6dd149e6-750d-45be-9331-dbce47c00a1d.png)

- Buka kembali teks editor (VScode), ubah isi file .env menjadi berikut :

![image](https://user-images.githubusercontent.com/115862112/212897016-e3256a3c-3193-490d-92e5-64ed5cbe89af.png)

- Akses kembali http://localhost:8080/admin/artikel. Menampilkan artikel maksimal 4 per halaman.

- Halaman 1 

![image](https://user-images.githubusercontent.com/115862112/212896805-ef2d8ce9-361b-4bf8-86ed-c41afa7c8ad5.png)

- Halaman 2

![image](https://user-images.githubusercontent.com/115862112/212896670-0513167b-84f7-407a-9e9a-46373864e847.png)

## 2. Membuat Pencarian
Terletak di folder app/Controllers, buka file Artikel.php. Ubah menjadi berikut : 

![image](https://user-images.githubusercontent.com/115862112/212896483-074c7409-c352-4a5f-97a2-bee29a798b08.png)

- Terletak di folder app/Views/artikel, buka file admin_index.php. Ubah menjadi berikut : 

![image](https://user-images.githubusercontent.com/115862112/212896397-dd669a2c-a65b-4638-8780-14bdce13aed0.png)

- Juga berikut : 

![image](https://user-images.githubusercontent.com/115862112/212896238-f44aedd1-19df-42e9-a9a4-b171fa156c36.png)

- Akses kembali http://localhost:8080/admin/artikel. Kemudian ketik artikel yang akan di cari, selanjutnya tekan cari.

- Proses mencari artikel Tambah Artikel 3

- Artikel ditemukan.

![image](https://user-images.githubusercontent.com/115862112/212895994-d90405d5-d85a-4713-9c3e-dd253a73eadd.png)


## 3. Upload Gambar
- Terletak di folder app/Controllers, buka file Artikel.php. Ubah menjadi berikut :

![image](https://user-images.githubusercontent.com/115862112/212895755-bdddafc3-bc07-4e76-9565-41e43c4c3d76.png)

- Terletak di folder app/Views/artikel, buka file form_add.php. Ubah menjadi berikut :

![image](https://user-images.githubusercontent.com/115862112/212895630-a56f4112-f7e6-4584-a94b-cb745805a31a.png)

- Akses kembali http://localhost:8080/admin/artikel. Kemudian pilih menu Tambah Artikel
- Lalu isi Artikel dan pilih Gambar

![image](https://user-images.githubusercontent.com/115862112/212895289-f7e955b1-0f2f-4296-8419-48d3e7af6b11.png)
![image](https://user-images.githubusercontent.com/115862112/212895182-467a6f9a-84c9-4113-8db7-44ba9c6f6e66.png)

- Otomatis diarahkan kembali ke menu admin. Pilih halaman ke-3 (terakhir ditambah). Untuk melihat tampilannya, tekan menu artikel.
- Berikut tampilannya.

![image](https://user-images.githubusercontent.com/115862112/212895019-bfe20049-ab0e-4498-b377-aff54a0f0430.png)
![image](https://user-images.githubusercontent.com/115862112/212894577-af338452-3ff3-407e-9bf0-443eed233d00.png)

# Lab11Web
