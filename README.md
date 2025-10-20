# Praktikum 5: JavaScript

**Nama   :** Maulana Malik Ibrahim

**NIM    :** 312410185

**Kelas  :** TI.24.A2

**Matkul :** Pemrograman Web 1

**Dosen Pengampu :** Agung Nugroho, S.Kom., M.Kom

# Langkah 1: Struktur Dasar HTML
```html
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Validasi Form dengan JavaScript</title>
</head>
<body>
    <h1>Form Pendaftaran</h1>
    <form id="registrationForm">
        <!-- Form fields akan ditambahkan di sini -->
    </form>
</body>
</html>
```
**Penjelasan:**

 - Struktur dasar HTML5 dengan tag essential.
 - Form dengan ID `registrationForm` yang akan kita validasi.
 - Belum ada field input (akan ditambahkan bertahap).

# Langkah 2: Menambahkan Field Input Dasar
```html
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Validasi Form dengan JavaScript</title>
</head>
<body>
    <h1>Form Pendaftaran</h1>
    <form id="registrationForm">
        <div>
            <label for="nama">Nama Lengkap</label>
            <input type="text" id="nama" name="nama">
            <div id="namaError" style="color: red; display: none;">
                Nama harus diisi dan minimal 3 karakter
            </div>
        </div>
        
        <div>
            <label for="email">Email</label>
            <input type="email" id="email" name="email">
            <div id="emailError" style="color: red; display: none;">
                Format email tidak valid
            </div>
        </div>
        
        <button type="submit">Daftar</button>
    </form>

    <script>
        // Validasi dasar akan ditambahkan di sini
    </script>
</body>
</html>
```
**Penjelasan:**

 - Menambahkan field nama dan email.
 - Setiap field memiliki div error yang awalnya tersembunyi (display: none).
 - Menggunakan inline style untuk sementara (akan dipindahkan ke CSS)

# Langkah 3: Menambahkan JavaScript Validasi Dasar
```html
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Validasi Form dengan JavaScript</title>
</head>
<body>
    <h1>Form Pendaftaran</h1>
    <form id="registrationForm">
        <div>
            <label for="nama">Nama Lengkap</label>
            <input type="text" id="nama" name="nama">
            <div id="namaError" style="color: red; display: none;">
                Nama harus diisi dan minimal 3 karakter
            </div>
        </div>
        
        <div>
            <label for="email">Email</label>
            <input type="email" id="email" name="email">
            <div id="emailError" style="color: red; display: none;">
                Format email tidak valid
            </div>
        </div>
        
        <button type="submit">Daftar</button>
    </form>

    <script>
        function validasiForm() {
            let isValid = true;
            
            // Validasi Nama
            const nama = document.getElementById('nama').value.trim();
            if (nama === '' || nama.length < 3) {
                document.getElementById('namaError').style.display = 'block';
                isValid = false;
            } else {
                document.getElementById('namaError').style.display = 'none';
            }
            
            // Validasi Email
            const email = document.getElementById('email').value.trim();
            const emailPattern = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
            if (!emailPattern.test(email)) {
                document.getElementById('emailError').style.display = 'block';
                isValid = false;
            } else {
                document.getElementById('emailError').style.display = 'none';
            }
            
            return isValid;
        }
        
        document.getElementById('registrationForm').addEventListener('submit', function(event) {
            if (!validasiForm()) {
                event.preventDefault();
            }
        });
    </script>
</body>
</html>
```
**Penjelasan:**

 - Fungsi `validasiForm()` memeriksa field nama dan email.
 - Menggunakan regex untuk validasi format email.
 - `event.preventDefault()` mencegah form submit jika validasi gagal.
 - Menampilkan/sembunyikan pesan error berdasarkan hasil validasi.

# Langkah 4: Menambahkan Field Password dan Konfirmasi
```html
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Validasi Form dengan JavaScript</title>
</head>
<body>
    <h1>Form Pendaftaran</h1>
    <form id="registrationForm">
        <div>
            <label for="nama">Nama Lengkap</label>
            <input type="text" id="nama" name="nama">
            <div id="namaError" style="color: red; display: none;">
                Nama harus diisi dan minimal 3 karakter
            </div>
        </div>
        
        <div>
            <label for="email">Email</label>
            <input type="email" id="email" name="email">
            <div id="emailError" style="color: red; display: none;">
                Format email tidak valid
            </div>
        </div>
        
        <div>
            <label for="password">Password</label>
            <input type="password" id="password" name="password">
            <div id="passwordError" style="color: red; display: none;">
                Password harus minimal 8 karakter
            </div>
        </div>
        
        <div>
            <label for="konfirmasiPassword">Konfirmasi Password</label>
            <input type="password" id="konfirmasiPassword" name="konfirmasiPassword">
            <div id="konfirmasiPasswordError" style="color: red; display: none;">
                Konfirmasi password tidak sesuai
            </div>
        </div>
        
        <button type="submit">Daftar</button>
    </form>

    <script>
        function validasiForm() {
            let isValid = true;
            
            // Validasi Nama
            const nama = document.getElementById('nama').value.trim();
            if (nama === '' || nama.length < 3) {
                document.getElementById('namaError').style.display = 'block';
                isValid = false;
            } else {
                document.getElementById('namaError').style.display = 'none';
            }
            
            // Validasi Email
            const email = document.getElementById('email').value.trim();
            const emailPattern = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
            if (!emailPattern.test(email)) {
                document.getElementById('emailError').style.display = 'block';
                isValid = false;
            } else {
                document.getElementById('emailError').style.display = 'none';
            }
            
            // Validasi Password
            const password = document.getElementById('password').value;
            if (password.length < 8) {
                document.getElementById('passwordError').style.display = 'block';
                isValid = false;
            } else {
                document.getElementById('passwordError').style.display = 'none';
            }
            
            // Validasi Konfirmasi Password
            const konfirmasiPassword = document.getElementById('konfirmasiPassword').value;
            if (password !== konfirmasiPassword) {
                document.getElementById('konfirmasiPasswordError').style.display = 'block';
                isValid = false;
            } else {
                document.getElementById('konfirmasiPasswordError').style.display = 'none';
            }
            
            return isValid;
        }
        
        document.getElementById('registrationForm').addEventListener('submit', function(event) {
            if (!validasiForm()) {
                event.preventDefault();
            }
        });
    </script>
</body>
</html>
```
**Penjelasan:**

 - Menambahkan field password dan konfirmasi password.
 - Validasi panjang password minimal 8 karakter.
 - Memastikan password dan konfirmasi password sama.

# Langkah 5: Menambahkan Field Lain dan Styling CSS
```html
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Validasi Form dengan JavaScript</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            max-width: 600px;
            margin: 0 auto;
            padding: 20px;
        }
        
        .form-group {
            margin-bottom: 15px;
        }
        
        label {
            display: block;
            margin-bottom: 5px;
        }
        
        input, select, textarea {
            width: 100%;
            padding: 8px;
            border: 1px solid #ddd;
            border-radius: 4px;
        }
        
        .error {
            color: red;
            font-size: 14px;
            margin-top: 5px;
            display: none;
        }
        
        button {
            background-color: #007bff;
            color: white;
            padding: 10px 20px;
            border: none;
            border-radius: 4px;
            cursor: pointer;
        }
    </style>
</head>
<body>
    <h1>Form Pendaftaran</h1>
    <form id="registrationForm">
        <div class="form-group">
            <label for="nama">Nama Lengkap</label>
            <input type="text" id="nama" name="nama">
            <div class="error" id="namaError">Nama harus diisi dan minimal 3 karakter</div>
        </div>
        
        <div class="form-group">
            <label for="email">Email</label>
            <input type="email" id="email" name="email">
            <div class="error" id="emailError">Format email tidak valid</div>
        </div>
        
        <div class="form-group">
            <label for="password">Password</label>
            <input type="password" id="password" name="password">
            <div class="error" id="passwordError">Password harus minimal 8 karakter</div>
        </div>
        
        <div class="form-group">
            <label for="konfirmasiPassword">Konfirmasi Password</label>
            <input type="password" id="konfirmasiPassword" name="konfirmasiPassword">
            <div class="error" id="konfirmasiPasswordError">Konfirmasi password tidak sesuai</div>
        </div>
        
        <div class="form-group">
            <label for="tanggalLahir">Tanggal Lahir</label>
            <input type="text" id="tanggalLahir" name="tanggalLahir" placeholder="DD/MM/YYYY">
            <div class="error" id="tanggalLahirError">Format tanggal tidak valid (DD/MM/YYYY)</div>
        </div>
        
        <div class="form-group">
            <label for="jenisKelamin">Jenis Kelamin</label>
            <select id="jenisKelamin" name="jenisKelamin">
                <option value="">Pilih Jenis Kelamin</option>
                <option value="L">Laki-laki</option>
                <option value="P">Perempuan</option>
            </select>
            <div class="error" id="jenisKelaminError">Pilih jenis kelamin</div>
        </div>
        
        <button type="submit">Daftar</button>
    </form>

    <script>
        function validasiForm() {
            let isValid = true;
            
            // Reset semua error
            document.querySelectorAll('.error').forEach(error => {
                error.style.display = 'none';
            });
            
            // Validasi Nama
            const nama = document.getElementById('nama').value.trim();
            if (nama === '' || nama.length < 3) {
                document.getElementById('namaError').style.display = 'block';
                isValid = false;
            }
            
            // Validasi Email
            const email = document.getElementById('email').value.trim();
            const emailPattern = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
            if (!emailPattern.test(email)) {
                document.getElementById('emailError').style.display = 'block';
                isValid = false;
            }
            
            // Validasi Password
            const password = document.getElementById('password').value;
            if (password.length < 8) {
                document.getElementById('passwordError').style.display = 'block';
                isValid = false;
            }
            
            // Validasi Konfirmasi Password
            const konfirmasiPassword = document.getElementById('konfirmasiPassword').value;
            if (password !== konfirmasiPassword) {
                document.getElementById('konfirmasiPasswordError').style.display = 'block';
                isValid = false;
            }
            
            // Validasi Tanggal Lahir
            const tanggalLahir = document.getElementById('tanggalLahir').value.trim();
            const tanggalPattern = /^(0[1-9]|[12][0-9]|3[01])\/(0[1-9]|1[0-2])\/\d{4}$/;
            if (!tanggalPattern.test(tanggalLahir)) {
                document.getElementById('tanggalLahirError').style.display = 'block';
                isValid = false;
            }
            
            // Validasi Jenis Kelamin
            const jenisKelamin = document.getElementById('jenisKelamin').value;
            if (jenisKelamin === '') {
                document.getElementById('jenisKelaminError').style.display = 'block';
                isValid = false;
            }
            
            return isValid;
        }
        
        document.getElementById('registrationForm').addEventListener('submit', function(event) {
            if (!validasiForm()) {
                event.preventDefault();
            }
        });
    </script>
</body>
</html>
```
**Penjelasan:**

 - Menambahkan CSS untuk styling yang lebih baik.
 - Menambahkan field tanggal lahir dengan validasi regex.
 - Menambahkan field jenis kelamin (select dropdown).
 - Menggunakan class `form-group` dan `error` untuk styling konsisten.
 - Reset semua error di awal validasi.

# Langkah 6: Versi Final dengan Semua Fitur
```html
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Validasi Form dengan JavaScript</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            max-width: 600px;
            margin: 0 auto;
            padding: 20px;
            background-color: #f5f5f5;
        }
        
        .container {
            background-color: white;
            padding: 30px;
            border-radius: 8px;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
        }
        
        h1 {
            color: #333;
            text-align: center;
            margin-bottom: 30px;
        }
        
        .form-group {
            margin-bottom: 20px;
        }
        
        label {
            display: block;
            margin-bottom: 8px;
            font-weight: bold;
            color: #555;
        }
        
        input[type="text"],
        input[type="email"],
        input[type="password"],
        select,
        textarea {
            width: 100%;
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 4px;
            box-sizing: border-box;
            font-size: 16px;
        }
        
        textarea {
            height: 100px;
            resize: vertical;
        }
        
        .error {
            color: #e74c3c;
            font-size: 14px;
            margin-top: 5px;
            display: none;
        }
        
        .success {
            color: #2ecc71;
            font-size: 14px;
            margin-top: 5px;
            display: none;
        }
        
        button {
            background-color: #3498db;
            color: white;
            border: none;
            padding: 12px 20px;
            border-radius: 4px;
            cursor: pointer;
            font-size: 16px;
            width: 100%;
            transition: background-color 0.3s;
        }
        
        button:hover {
            background-color: #2980b9;
        }
        
        .form-footer {
            margin-top: 20px;
            text-align: center;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Form Pendaftaran</h1>
        <form id="registrationForm" action="#" method="post">
            <div class="form-group">
                <label for="nama">Nama Lengkap</label>
                <input type="text" id="nama" name="nama" placeholder="Masukkan nama lengkap">
                <div class="error" id="namaError">Nama harus diisi dan minimal 3 karakter</div>
            </div>
            
            <div class="form-group">
                <label for="email">Email</label>
                <input type="email" id="email" name="email" placeholder="Masukkan alamat email">
                <div class="error" id="emailError">Format email tidak valid</div>
            </div>
            
            <div class="form-group">
                <label for="password">Password</label>
                <input type="password" id="password" name="password" placeholder="Masukkan password">
                <div class="error" id="passwordError">Password harus minimal 8 karakter</div>
            </div>
            
            <div class="form-group">
                <label for="konfirmasiPassword">Konfirmasi Password</label>
                <input type="password" id="konfirmasiPassword" name="konfirmasiPassword" placeholder="Konfirmasi password">
                <div class="error" id="konfirmasiPasswordError">Konfirmasi password tidak sesuai</div>
            </div>
            
            <div class="form-group">
                <label for="tanggalLahir">Tanggal Lahir</label>
                <input type="text" id="tanggalLahir" name="tanggalLahir" placeholder="DD/MM/YYYY">
                <div class="error" id="tanggalLahirError">Format tanggal tidak valid (DD/MM/YYYY)</div>
            </div>
            
            <div class="form-group">
                <label for="jenisKelamin">Jenis Kelamin</label>
                <select id="jenisKelamin" name="jenisKelamin">
                    <option value="">Pilih Jenis Kelamin</option>
                    <option value="L">Laki-laki</option>
                    <option value="P">Perempuan</option>
                </select>
                <div class="error" id="jenisKelaminError">Pilih jenis kelamin</div>
            </div>
            
            <div class="form-group">
                <label for="alamat">Alamat</label>
                <textarea id="alamat" name="alamat" placeholder="Masukkan alamat lengkap"></textarea>
                <div class="error" id="alamatError">Alamat harus diisi</div>
            </div>
            
            <div class="form-group">
                <label>
                    <input type="checkbox" id="syaratKetentuan" name="syaratKetentuan">
                    Saya menyetujui syarat dan ketentuan
                </label>
                <div class="error" id="syaratKetentuanError">Anda harus menyetujui syarat dan ketentuan</div>
            </div>
            
            <button type="submit">Daftar</button>
            
            <div class="form-footer">
                <div class="success" id="successMessage">Form berhasil divalidasi dan siap dikirim!</div>
            </div>
        </form>
    </div>

    <script>
        // Fungsi untuk validasi form
        function validasiForm() {
            let isValid = true;
            
            // Reset pesan error
            document.querySelectorAll('.error').forEach(el => {
                el.style.display = 'none';
            });
            document.getElementById('successMessage').style.display = 'none';
            
            // Validasi Nama
            const nama = document.getElementById('nama').value.trim();
            if (nama === '' || nama.length < 3) {
                document.getElementById('namaError').style.display = 'block';
                isValid = false;
            }
            
            // Validasi Email
            const email = document.getElementById('email').value.trim();
            const emailPattern = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
            if (!emailPattern.test(email)) {
                document.getElementById('emailError').style.display = 'block';
                isValid = false;
            }
            
            // Validasi Password
            const password = document.getElementById('password').value;
            if (password.length < 8) {
                document.getElementById('passwordError').style.display = 'block';
                isValid = false;
            }
            
            // Validasi Konfirmasi Password
            const konfirmasiPassword = document.getElementById('konfirmasiPassword').value;
            if (password !== konfirmasiPassword) {
                document.getElementById('konfirmasiPasswordError').style.display = 'block';
                isValid = false;
            }
            
            // Validasi Tanggal Lahir
            const tanggalLahir = document.getElementById('tanggalLahir').value.trim();
            const tanggalPattern = /^(0[1-9]|[12][0-9]|3[01])\/(0[1-9]|1[0-2])\/\d{4}$/;
            if (!tanggalPattern.test(tanggalLahir)) {
                document.getElementById('tanggalLahirError').style.display = 'block';
                isValid = false;
            }
            
            // Validasi Jenis Kelamin
            const jenisKelamin = document.getElementById('jenisKelamin').value;
            if (jenisKelamin === '') {
                document.getElementById('jenisKelaminError').style.display = 'block';
                isValid = false;
            }
            
            // Validasi Alamat
            const alamat = document.getElementById('alamat').value.trim();
            if (alamat === '') {
                document.getElementById('alamatError').style.display = 'block';
                isValid = false;
            }
            
            // Validasi Syarat dan Ketentuan
            const syaratKetentuan = document.getElementById('syaratKetentuan').checked;
            if (!syaratKetentuan) {
                document.getElementById('syaratKetentuanError').style.display = 'block';
                isValid = false;
            }
            
            // Jika semua validasi berhasil
            if (isValid) {
                document.getElementById('successMessage').style.display = 'block';
                // Di sini biasanya form akan dikirim ke server
                // Untuk contoh ini, kita hanya menampilkan pesan sukses
            }
            
            return isValid;
        }
        
        // Event listener untuk form submission
        document.getElementById('registrationForm').addEventListener('submit', function(event) {
            event.preventDefault(); // Mencegah form dikirim secara default
            validasiForm();
        });
        
        // Validasi real-time untuk beberapa field
        document.getElementById('password').addEventListener('input', function() {
            const konfirmasiPassword = document.getElementById('konfirmasiPassword').value;
            if (konfirmasiPassword !== '') {
                if (this.value !== konfirmasiPassword) {
                    document.getElementById('konfirmasiPasswordError').style.display = 'block';
                } else {
                    document.getElementById('konfirmasiPasswordError').style.display = 'none';
                }
            }
        });
        
        document.getElementById('konfirmasiPassword').addEventListener('input', function() {
            const password = document.getElementById('password').value;
            if (this.value !== password) {
                document.getElementById('konfirmasiPasswordError').style.display = 'block';
            } else {
                document.getElementById('konfirmasiPasswordError').style.display = 'none';
            }
        });
    </script>
</body>
</html>
```
**Penjelasan Final:**

 - Form lengkap dengan semua field yang diperlukan.
 - Styling CSS yang modern dan responsive.
 - Validasi real-time untuk password.
 - Pesan sukses ketika semua validasi berhasil.
 - Penggunaan class CSS yang terorganisir.
 - Event listeners untuk interaktivitas yang lebih baik.

# Contoh hasil Input dan hasil output

<img width="1920" height="1200" alt="Cuplikan layar 2025-10-20 225923" src="https://github.com/user-attachments/assets/9b4d7f5b-1b4a-46e9-83af-5a3b4254a1c3" />

