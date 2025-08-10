# 🛠️ User Service - Go (Golang) Microservice

User Service ini adalah bagian dari arsitektur **MICRO-SAYUR**, dibangun menggunakan **Golang** dengan **Clean Architecture** & **Repository Pattern**.  
Service ini mengelola **User Account**, **Customer Management**, dan fitur-fitur terkait seperti verifikasi, update data, dan otentikasi.

---

## 🚀 Tech Stack

- **Golang** 1.22+
- **GORM** ORM untuk akses database
- **PostgreSQL** / MySQL (tergantung konfigurasi)
- **JWT** untuk otentikasi
- **Viper** untuk manajemen konfigurasi
- **Labstack Echo** sebagai HTTP framework
- **Docker** untuk containerization
- **Go Modules** untuk dependency management

---

## 📂 Project Structure

```
user-service/
│
├── cmd/                    # Entry point aplikasi
├── config/                 # File konfigurasi (Viper)
├── internal/
│   ├── core/
│   │   ├── domain/         # Entity & model domain
│   │   ├── ports/          # Interface untuk usecase/repository
│   ├── repository/         # Implementasi repository (GORM)
│   ├── service/            # Business logic & usecase
│   ├── handler/            # HTTP handler (controller)
│
├── go.mod                  # Go module definition
├── go.sum                  # Dependency checksum
└── README.md               # Dokumentasi proyek
```

---

## ⚙️ Installation & Setup

### 1. Clone Repository

```bash
git clone https://github.com/username/micro-sayur-user-service.git
cd micro-sayur-user-service
```

### 2. Setup Environment

Buat file `.env`:

```env
APP_PORT=8080
APP_ENV=development
DB_DRIVER=postgres
DB_HOST=localhost
DB_PORT=5432
DB_USER=your_db_user
DB_PASSWORD=your_db_password
DB_NAME=your_db_name
JWT_SECRET=your_secret_key
```

### 3. Install Dependencies

```bash
go mod tidy
```

### 4. Run Database Migration (Jika ada)

```bash
go run cmd/migrate/main.go
```

### 5. Run Service

```bash
go run cmd/main.go
```

---

## 📡 API Endpoints

### **User**

| Method | Endpoint              | Description         |
| ------ | --------------------- | ------------------- |
| POST   | `/users`              | Create new user     |
| GET    | `/users/:id`          | Get user by ID      |
| GET    | `/users/email/:email` | Get user by email   |
| PUT    | `/users/:id/password` | Update password     |
| PUT    | `/users/:id/verify`   | Verify user account |

### **Customer (Admin)**

| Method | Endpoint         | Description                                  |
| ------ | ---------------- | -------------------------------------------- |
| GET    | `/customers`     | Get all customers (with filter & pagination) |
| GET    | `/customers/:id` | Get customer by ID                           |
| POST   | `/customers`     | Create customer                              |
| PUT    | `/customers/:id` | Update customer                              |
| DELETE | `/customers/:id` | Delete customer                              |

---

## 🧩 Repository Pattern

Repository ini mengimplementasikan interface `UserRepositoryInterface` yang memisahkan **akses data** dari **business logic**, sehingga:

- Lebih mudah di-_mock_ saat unit testing.
- ORM (GORM) bisa diganti tanpa ubah business logic.
- Codebase lebih clean & maintainable.

---

## 🧪 Running Tests

```bash
go test ./...
```

---

## 🐳 Docker Support

Build dan jalankan dengan Docker:

```bash
docker build -t user-service .
docker run -p 8080:8080 --env-file .env user-service
```

---

## 📜 License

MIT License © 2025 - Jansen

---

## ✨ Author

**Jansen Stanlie**  
_Supply Chain Project & Digitalization Specialist | Backend Developer (Golang, Node.js)_
