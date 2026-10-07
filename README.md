# Dai Arrisalah

Aplikasi laporan kegiatan dai. Halaman web statis (GitHub Pages) + database Supabase.

## A. Siapkan Supabase (sekali saja)
1. Daftar di supabase.com, klik **New project**, simpan kata sandi database.
2. Buka **Authentication > Providers > Email**, matikan **Confirm email**, lalu simpan.
3. Buka **SQL Editor > New query**, tempel seluruh isi `supabase/schema.sql`, klik **Run**.
4. Buat akun koordinator: **Authentication > Users > Add user > Create new user**.
   Email: `admin@dai-arrisalah.app` (boleh ganti bagian sebelum @), isi sandi, centang Auto Confirm User.
5. Kembali ke SQL Editor, jalankan (ganti `admin` bila Anda memakai nama lain di email):
```sql
insert into profiles(id,username,name,role)
select id,'admin','Koordinator','koordinator' from auth.users where email='admin@dai-arrisalah.app';
```
6. Buka **Project Settings > API**, salin **Project URL** dan **anon public key**, lalu isikan ke `config.js`.
   Jangan pernah memakai `service_role` key.

## B. Unggah ke GitHub
1. Buat repository baru `dai-arrisalah` (Public).
2. Klik **Add file > Upload files**, seret semua isi folder ini (index.html, config.js, manifest.json, logo.png, icon-192.png, icon-512.png, folder supabase, README.md), lalu **Commit changes**.
3. Buka **Settings > Pages**, pilih **Deploy from a branch**, branch `main`, folder `/ (root)`, Save.
4. Setelah 1-2 menit aplikasi terbuka di `https://NAMA-GITHUB.github.io/dai-arrisalah/`.

## C. Pemakaian
- Koordinator masuk dengan username `admin` (atau yang Anda buat), lalu membuat akun dai di tab **Dai**.
- Dai masuk dengan username dan sandi dari koordinator. Di HP: menu browser > **Tambahkan ke layar utama**.

## Catatan
- Pembuatan banyak akun sekaligus bisa kena batas Supabase (Authentication > Rate Limits). Jika muncul pesan gagal, tunggu sebentar atau naikkan batasnya.
- Sandi dai yang lupa belum bisa direset dari aplikasi. Reset lewat Supabase: Authentication > Users.
- Menghapus dai di aplikasi menghapus akses masuknya, riwayat laporannya tetap tersimpan.
