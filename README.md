# 🚀 Mutqin Super App

Aplikasi super lengkap yang dibangun dengan **Laravel 11** + **Filament 3**.

## ✨ Fitur Utama

- Admin Panel modern menggunakan Filament
- Multi-user & role management
- API-ready
- Responsive & modern UI
- Siap untuk production

## 👨‍💻 Tech Stack

- Laravel 11
- Filament 3
- PHP 8.2+
- SQLite (default) / MySQL / PostgreSQL

## 🚀 Quick Start

### 1. Clone Repository

```bash
git clone https://github.com/syuhadahanif13/mutqin-super-app.git
cd mutqin-super-app
```

### 2. Install Dependencies

```bash
composer install
cp .env.example .env
php artisan key:generate
```

### 3. Setup Database

```bash
# Untuk development pakai SQLite (sudah default)
touch database/database.sqlite

# Atau gunakan MySQL/PostgreSQL, edit .env
php artisan migrate
```

### 4. Install Filament

```bash
php artisan filament:install --panels
```

### 5. Jalankan Aplikasi

```bash
php artisan serve
```

Buka browser: **http://localhost:8000/admin**

## 🔧 Development

```bash
# Run dev server + Vite
composer dev

# Format code
./vendor/bin/pint

# Run tests
php artisan test
```

## 📁 Struktur Folder

```
mutqin-super-app/
├── app/
├── bootstrap/
├── config/
├── database/
├── public/
├── resources/
├── routes/
├── storage/
├── tests/
├── artisan
├── composer.json
├── .env
├── README.md
```

## 🚢 Deployment

Siap di-deploy ke:
- Laravel Forge
- Ploi
- VPS biasa
- Railway / Render / Fly.io

## 👋 Kontribusi

Pull request sangat welcome!

## ⚖️ License

MIT License

---

Dibuat dengan ❤️ oleh **Mutqin** | 2026
