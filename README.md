# 🚀 FastAPI + Render + MariaDB + JWT Authentication (Alembic Ready)

Last updated

- 31-05-2026

# Version

At Render I use the PYTHON_VERSION environment variable to tell Render to use Python version 3.11. Locally I am using Python 3.12

A production-ready backend built with FastAPI, MariaDB (HelioHost), JWT authentication, bcrypt password hashing, and Alembic migrations hosted at Render.

---

## 🧱 Tech Stack

- FastAPI
- Hosted at Render
- MariaDB (HelioHost)
- SQLAlchemy ORM
- Alembic (migrations)
- JWT Authentication (python-jose)
- bcrypt
- Uvicorn
- PyMySQL driver

---

## ✨ Features

- User registration (DEV mode only)
- Secure password hashing (bcrypt)
- JWT login system
- Protected routes
- MariaDB cloud database (HelioHost)
- Alembic migrations
- Swagger UI testing

---

## 📦 Setup & Installation

### Clone repository
git clone https://github.com/your-username/your-repo.git
cd your-repo

### Create virtual environment
python -m venv .venv

### Activate virtual environment

Windows:
.venv\Scripts\activate

Mac/Linux:
source .venv/bin/activate

### Install dependencies
pip install -r requirements.txt

---

## ⚙️ Environment Variables

Create a `.env` file:

DATABASE_URL=mysql+pymysql://USER:PASSWORD@HOST:3306/DATABASE  
SECRET_KEY=your-secret-key  
ALGORITHM=HS256  
ACCESS_TOKEN_EXPIRE_MINUTES=30  
DEV_MODE=true  

---

## 🗄️ Database (Alembic)

Initialize Alembic:
alembic init alembic

Create migration:
alembic revision --autogenerate -m "create users table"

Apply migration:
alembic upgrade head

---

## 🚀 Run the server

uvicorn app:app --reload

---

## 🌐 API Endpoints

Register user (DEV ONLY):
POST /register

{
  "email": "user@example.com",
  "password": "12345678"
}

---

Login:
POST /token

- username = email
- password = password

---

Protected route:
GET /protected

Authorization:
Bearer YOUR_TOKEN

---

## 📚 Swagger UI

http://127.0.0.1:8000/docs

---

## 🧠 Architecture

FastAPI → SQLAlchemy → MariaDB (HelioHost)
→ Alembic migrations
→ bcrypt + JWT authentication

---

## 🔐 Security

- bcrypt password hashing
- JWT authentication
- Environment variables
- No hardcoded secrets
- DEV_MODE protection for user creation

---

## ☁️ Deployment Notes

Render Start Command:

gunicorn app:app -k uvicorn.workers.UvicornWorker --bind 0.0.0.0:$PORT

Before deploying:
- Run migrations locally:
  alembic upgrade head

- Set environment variables in Render

---

## 📌 Important

- Do NOT use create_all()
- Always use Alembic migrations
- Ensure MariaDB connection uses PyMySQL:
  mysql+pymysql://USER:PASSWORD@HOST:3306/DB

---

## 📜 License

MIT