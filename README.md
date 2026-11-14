# WebQR Scanner Mandiri untuk MikroTik Hotspot

WebQR ini dibuat khusus agar berjalan di **GitHub Pages (HTTPS)** milik akun Anda sendiri (`jacob157-rgb`), sehingga:
1. **Izin Kamera HP Aktif 100%:** Karena berjalan di HTTPS, seluruh peramban smartphone (Google Chrome Android, iOS Safari, browser Captive Portal bawaan HP) mengizinkan akses kamera live streaming tanpa kendala.
2. **Mandiri & Terpercaya:** Tidak menumpang / bergantung pada GitHub orang lain (`laksa19`). Anda memiliki kendali penuh atas kode dan tampilannya.
3. **Terintegrasi MikroTik:** Setelah QR voucher terpindai, scanner langsung me-redirect kembali ke `http://agungwifi.net/login?username=...&password=...` dan login otomatis.

---

## Cara Pasang ke GitHub Anda (Hanya 2 Menit):

### Cara 1: Lewat Web GitHub (Paling Mudah)
1. Buka browser dan login ke akun GitHub Anda: **https://github.com/new**
2. Isi form:
   - **Repository name:** `myqr`
   - **Visibility:** Pilih **Public** (wajib Public agar fitur GitHub Pages gratis aktif).
   - Klik tombol hijau **Create repository**.
3. Di halaman repository baru Anda, klik tombol **Upload an existing file** (atau **creating a new file**).
4. Upload file `index.html` yang ada di folder ini (`C:\Users\Jacob\Project\LNet-Access\webqr\index.html`).
5. Klik **Commit changes**.
6. Aktifkan GitHub Pages:
   - Masuk ke tab **Settings** di repo tersebut.
   - Di menu sebelah kiri, klik **Pages**.
   - Pada bagian **Build and deployment** -> **Branch**, pilih branch `main` (atau `master`) dan folder `/ (root)`.
   - Klik tombol **Save**.
7. Tunggu sekitar 1-2 menit. Web scanner Anda sekarang sudah live di:
   👉 **`https://jacob157-rgb.github.io/myqr/`**

---

### Cara 2: Lewat Terminal Git
```bash
cd C:\Users\Jacob\Project\LNet-Access\webqr
git init
git add index.html
git commit -m "Init WebQR Scanner"
git branch -M main
git remote add origin https://github.com/jacob157-rgb/myqr.git
git push -u origin main
```
Lalu aktifkan GitHub Pages di tab **Settings** -> **Pages**.

---

## Pengaturan Walled Garden MikroTik (Sudah Dikonfigurasi)

MikroTik Anda sudah disiapkan dengan rule berikut:
```text
/ip hotspot walled-garden ip add action=accept comment="Jacob-WebQR" dst-host="jacob157-rgb.github.io"
```
Dengan rule ini, pengguna hotspot yang belum login tetap dapat membuka `https://jacob157-rgb.github.io/myqr/` untuk memindai voucher.
