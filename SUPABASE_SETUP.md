# 🔗 Integrasi Supabase

Panduan menghubungkan **Mutqin Super App** dengan **Supabase** (Database + Auth + Storage).

## ✅ Langkah 1: Ambil Credential dari Supabase

1. Buka [Supabase Dashboard](https://supabase.com/dashboard)
2. Pilih project kamu
3. Pergi ke **Settings** → **Database**
   - Copy **Connection string** (pilih **URI**)
4. Pergi ke **Settings** → **API**
   - Copy **Project URL**
   - Copy **anon public** key
   - Copy **service_role** key (simpan rahasia!)

## ✅ Langkah 2: Update File `.env`

Buka file `.env` di project Laravel kamu, lalu ganti bagian database dengan credential Supabase:

```env
# ============================================
# SUPABASE CONFIGURATION
# ============================================
SUPABASE_URL=https://xxxxx.supabase.co
SUPABASE_ANON_KEY=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...
SUPABASE_SERVICE_ROLE_KEY=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...   # JANGAN commit ke git!

# ============================================
# DATABASE (Supabase Postgres)
# ============================================
DB_CONNECTION=pgsql
DB_HOST=db.xxxxx.supabase.co
DB_PORT=5432
DB_DATABASE=postgres
DB_USERNAME=postgres
DB_PASSWORD=your-supabase-db-password

# Atau pakai DB_URL (lebih simpel):
# DB_URL=postgresql://postgres:[PASSWORD]@db.xxxxx.supabase.co:5432/postgres
```

> **Catatan**: Ganti `xxxxx` sesuai project ID Supabase kamu.

## ✅ Langkah 3: Install Package Pendukung (Opsional)

Jika kamu ingin pakai Supabase Auth, Storage, atau Realtime dari Laravel:

```bash
composer require supabase/supabase-php
```

Atau untuk integrasi lebih lengkap (Auth + Storage):

```bash
composer require supabase/supabase-php
composer require laravel/socialite   # jika butuh social login
```

## ✅ Langkah 4: Jalankan Migration ke Supabase

```bash
php artisan migrate
```

> Pastikan password Supabase sudah benar dan koneksi internet stabil.

## ✅ Langkah 5: Test Koneksi

Buat file test sementara di `routes/web.php`:

```php
use Illuminate\Support\Facades\DB;

Route::get('/test-db', function () {
    try {
        DB::connection()->getPdo();
        return 'Koneksi ke Supabase berhasil! 🎉';
    } catch (\Exception $e) {
        return 'Gagal koneksi: ' . $e->getMessage();
    }
});
```

Kemudian buka `http://localhost:8000/test-db`

## 🚨 Keamanan Penting

- **JANGAN** pernah commit file `.env` ke GitHub
- `service_role` key hanya boleh dipakai di backend (server)
- `anon` key boleh dipakai di frontend
- Gunakan **Row Level Security (RLS)** di Supabase untuk keamanan data

## 📁 Struktur Rekomendasi

```
.env                  ← JANGAN di-push
.env.example          ← Update dengan contoh Supabase
SUPABASE_SETUP.md     ← File ini
config/supabase.php   ← (opsional) buat config sendiri
```

## 🚀 Next Step

Setelah berhasil konek, kamu bisa:
- Pindah dari Filament auth ke Supabase Auth
- Gunakan Supabase Storage untuk upload file
- Manfaatkan Realtime subscription
- Buat Edge Functions

---

Butuh bantuan lebih lanjut? Ketik saja mau bagian mana yang ingin disetup dulu:
1. Database saja (paling umum)
2. Supabase Auth + Filament
3. Supabase Storage
4. Realtime
