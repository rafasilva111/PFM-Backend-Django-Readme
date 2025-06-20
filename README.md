# 🍽️ GoodBites Backend

Welcome to the backend of **GoodBites**, a modern food-focused platform designed for real-time interaction and efficient task processing.  
This backend is built with Django, PostgreSQL, Celery, Redis, and Channels, and is fully containerized using Docker for ease of development and deployment.

---

## 🔧 Tech Stack

| Technology     | Description                                                                 |
|----------------|-----------------------------------------------------------------------------|
| **Django**     | High-level Python web framework for rapid development and clean architecture |
| **PostgreSQL** | Reliable and powerful open-source relational database                        |
| **Celery**     | Asynchronous task queue for background processing and scheduling             |
| **Redis**      | In-memory data store used as Celery broker and for caching                  |
| **Channels**   | Adds WebSocket and async support to Django for real-time features            |
| **Docker**     | Ensures consistent environments for development, testing, and deployment     |
| **WSL**        | Linux environment on Windows for native-like Docker and development support  |
| **VS Code**    | Optional IDE integration for streamlined development                         |

---

## ✨ General Features

- 🔐 **User Authentication & Permissions**
- 🔄 **Real-time Updates via WebSockets**
- 🧠 **Asynchronous Tasks with Celery + Redis**
- 🗓️ **Scheduled Jobs with Celery Beat**
- 🛠️ **Powerful Django Admin Dashboard**
- 📦 **Containerized for Easy Setup and Deployment**
- 🔍 **API-ready Architecture (REST)**
- 🧪 **Integrated Testing Tools (Pytest, unittest)**
- 📚 **Well-Structured Developer Documentation with Sphinx**
- 🌐 **DNS Configuration and HTTPS Support for Secure Production Deployment (NameCheap)**
- 📧 **Email Integration for Notifications, Verification & Password Reset (MailTrap)**
- 🔐 **Bot Protection via CAPTCHA Integration (reCAPTCHA)**

## ✨ App Features



---

## 🧰 Prerequisites

- Python 3.10+
- PostgreSQL (via Docker or local)
- Redis (via Docker or local)
- RabbitMQ (via Docker or local)
- Docker + Docker Compose
- [WSL](https://learn.microsoft.com/en-us/windows/wsl/) for Windows users
- [VS Code](https://code.visualstudio.com/) (optional but recommended)

---

## ⚙️ Local Development Setup

### 1. Setup WSL + System Dependencies

```bash
wsl
sudo apt update
sudo apt install -y python3.10 python3.10-venv libpq-dev gcc postgresql redis
```

### 2. Clone the Repository

```bash
git clone https://github.com/rafasilva111/PFM-Backend-Django.git
cd PFM-Backend-Django
```

### 3. Create and Activate Virtual Environment

```bash
python3.10 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

### 4. Setup Environment Variables

Copy and modify `.env.dev.full_local` to `.env.dev`:

```bash
cp .env.dev.full_local .env.dev
```

Update values as needed.

### 5. Run Database Setup

```bash
sudo service postgresql start
python create_databases.py
```

### 6. Start Redis

```bash
sudo service redis-server start
```

### 7. Run the Development Server

```bash
python manage.py migrate
python manage.py runserver
```

---

## 🧪 Testing

To run tests:

```bash
python manage.py test
```

Or use pytest if configured:

```bash
pytest
```

---

## 🐳 Docker Setup

To run the entire stack with Docker:

```bash
docker-compose up --build
```

Access Django at: [http://localhost:8000](http://localhost:8000)

---

## 📁 VS Code Integration (Optional)

Use `.vscode/launch.json` for debugging and development directly from VS Code. Enable `devcontainers` if using Remote - WSL or Docker.

---

## 💡 Useful Commands

```bash
# Start RabbitMQ (if used)
docker run -d -p 5672:5672 rabbitmq

# Celery workers and beat scheduler
celery -A config.celery worker --loglevel=info
celery -A config.celery beat --loglevel=info --scheduler django_celery_beat.schedulers:DatabaseScheduler

# Access PostgreSQL
psql -U postgres -h localhost -d goodbites

# Access Django shell
docker exec -it django python manage.py shell
```

---

## 📦 Deployment

- Use Gunicorn + UvicornWorker for ASGI compatibility.
- Nginx or Caddy recommended as reverse proxy.
- Environment variables and secrets should be managed using `.env` files or a secret manager.

---

## 🤝 Contributing

Feel free to fork the repo and open a pull request. Contributions are welcome and encouraged!

---

## 📜 License

MIT License © [Your Name or Company]