# 📝 Go Gin Todo API

REST API sederhana untuk manajemen todo list yang dibangun dengan **Gin**, **PostgreSQL**, dan **Go**.

[![Go Version](https://img.shields.io/badge/Go-1.27-blue.svg)](https://golang.org/)
[![Gin Framework](https://img.shields.io/badge/Gin-v1.12.0-green.svg)](https://gin-gonic.com/)
[![PostgreSQL](https://img.shields.io/badge/Database-PostgreSQL-blue.svg)](https://www.postgresql.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

---

## 🚀 Fitur

- ✅ **CRUD Todo** — Buat, baca, perbarui, dan hapus todo
- ✅ **Filter** — Filter todo berdasarkan status selesai (`?done=true/false`)
- ✅ **Validasi Input** — Title wajib diisi minimal 3 karakter
- ✅ **Database Connection Pool** — Konfigurasi koneksi PostgreSQL yang optimal
- ✅ **Graceful Shutdown** — Server matang saat menerima sinyal interrupt
- ✅ **Error Handling** — Format respons error yang seragam
- ✅ **Environment Config** — Konfigurasi melalui file `.env`

---

## 📂 Struktur Proyek

```
go_gin/
├── main.go                 # Entry point aplikasi
├── go.mod                  # Dependensi Go
├── .env                    # Variabel lingkungan (DATABASE_URL)
├── .gitignore              # File yang diabaikan Git
├── README.md               # Dokumentasi ini
├── database/
│   └── database.go         # Koneksi dan migrasi database
├── router/
│   └── router.go           # Pengaturan route Gin
└── todo/
    ├── handler.go          # Logika handler (CRUD)
    ├── model.go            # Struct model dan request
    └── routes.go           # Definisi endpoint todo
```

---

## 🛠️ Instalasi & Menjalankan

### 1. Clone repositori

```bash
git clone https://github.com/username/go_gin.git
cd go_gin
```

### 2. Siapkan database PostgreSQL

Pastikan PostgreSQL sudah berjalan, lalu buat database:

```sql
CREATE DATABASE neondb;
```

### 3. Konfigurasi environment

Salin contoh file environment dan sesuaikan:

```bash
cp .env.example .env   # atau buat .env secara manual
```

Isi `.env`:

```env
DATABASE_URL="postgresql://user:password@localhost:5432/neondb?sslmode=require"
```

### 4. Install dependensi

```bash
go mod tidy
```

### 5. Jalankan aplikasi

```bash
go run main.go
```

Server akan berjalan di `http://localhost:8080`.

---

## 📡 API Endpoint

| Method | Endpoint | Deskripsi |
|--------|----------|-----------|
| `GET` | `/api/v1/todos` | Daftar semua todo |
| `GET` | `/api/v1/todos?done=true` | Filter todo selesai/belum |
| `GET` | `/api/v1/todos/:id` | Detail satu todo |
| `POST` | `/api/v1/todos` | Buat todo baru |
| `PUT` | `/api/v1/todos/:id` | Perbarui todo |
| `DELETE` | `/api/v1/todos/:id` | Hapus todo |

### Contoh Request & Response

#### GET /api/v1/todos
```json
[
  {
    "id": 1,
    "title": "Belajar Go Gin",
    "is_done": false
  }
]
```

#### POST /api/v1/todos
**Request:**
```json
{
  "title": "Belajar Go Gin",
  "is_done": false
}
```

**Response (201 Created):**
```json
{
  "id": 1,
  "title": "Belajar Go Gin",
  "is_done": false
}
```

#### Error Response (400 Bad Request)
```json
{
  "error": "Title wajib diisi"
}
```

---

## 🧪 Testing

Jalankan semua test:

```bash
go test ./...
```

Jalankan test dengan coverage:

```bash
go test -cover ./...
```

---

## 🤝 Kontribusi

Kontribusi sangat diterima! Silakan:

1. Fork repositori ini
2. Buat branch fitur (`git checkout -b fitur/awesome`)
3. Commit perubahan (`git commit -m 'Tambah fitur awesome'`)
4. Push ke branch (`git push origin fitur/awesome`)
5. Buka Pull Request

---

## 📄 Lisensi

Proyek ini dilisensikan di bawah [MIT License](LICENSE).

---

## 👨‍💻 Author

Dibuat dengan ❤️ menggunakan Go dan Gin Framework.

---

⭐ **Jika proyek ini bermanfaat, jangan lupa beri bintang!**