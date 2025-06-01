# 🚀 vProfile Microservices - Dockerized Web App Stack

A fully containerized microservices architecture for the **vProfile** application using **Docker** and **Docker Compose**.

This project simulates a real-world production environment with backend, database, caching, messaging, and a reverse-proxy frontend — perfect for learning DevOps, containerization, and system design.

---

## 🧱 Architecture Overview

```

Client ↔ 🌐 NGINX (vproweb) ↔ 🐱‍🏍 Tomcat App (vproapp) ↔ 🐬 MySQL DB (vprodb)
↕
💾 Memcached (vprocache01)
📬 RabbitMQ (vpromq01)

```

---

## 📦 Services Breakdown

| 🔧 Service       | ⚙️ Image/Build                | 🌐 Port | 📋 Description                         |
|------------------|-------------------------------|--------|----------------------------------------|
| `vprodb`         | MySQL 8 + SQL dump            | 3306   | Preloaded database for user data       |
| `vprocache01`    | Memcached (official)          | 11211  | High-speed in-memory cache             |
| `vpromq01`       | RabbitMQ (official)           | 5672   | Message queue for backend events       |
| `vproapp`        | WAR built via Maven, runs on Tomcat | 8080   | Java-based backend service             |
| `vproweb`        | NGINX reverse proxy           | 80     | Frontend load balancer/proxy           |

---

## 📁 Project Structure

```

vprofile-project/
├── Docker-files/
│   ├── app/        # Builds WAR, runs on Tomcat
│   ├── db/         # MySQL + SQL data seed
│   └── web/        # NGINX reverse proxy config
├── compose.yaml    # Docker Compose stack file
└── README.md       # You're here!

````

---

## 🛠️ Prerequisites

✅ [Docker](https://www.docker.com/products/docker-desktop)  
✅ [Docker Compose](https://docs.docker.com/compose/)

---

## 📸 Screenshots

<p align="center">
  <img src="https://github.com/user-attachments/assets/22de7e57-507d-494f-be88-9d7e1318715f" width="600"/>
  <br/>
  <img src="https://github.com/user-attachments/assets/5a115977-ec54-40a0-913c-e167b81a1556" width="600"/>
  <img src="https://github.com/user-attachments/assets/e758f940-156a-4eaa-9a65-e42451b44be9" width="600"/>
</p>

## 🚀 Getting Started

1. **Clone this repository:**
   ```bash
   git clone https://github.com/Flack74/vprofile-microservices.git
   cd vprofile-microservices


2. **Build and launch the app stack:**

   ```bash
   docker compose up --build
   ```

3. **Visit in your browser:**

   ```
   http://localhost
   ```

---

## 🔐 Sample Login Credentials

| 👤 Username | 🔑 Password |
| ----------- | ----------- |
| `admin_vp`  | `admin_vp`  |

> 🧠 Passwords are securely hashed inside the MySQL container.

---

## ⚙️ Developer Notes

* 🧱 **Multi-stage Docker build**: Maven compiles source → WAR deployed to Tomcat.
* 🐬 **MySQL Initialization**: Uses SQL dump to preload DB.
* 🌐 **NGINX Reverse Proxy**: Handles frontend routing to backend container.
* 🔐 **Environment Variables**: Used for DB credentials and config.

---

## 🧹 Cleanup

To stop all services and delete associated volumes:

```bash
docker compose down -v
```

---

## 🙌 Acknowledgements

Based on the original [vprofile-project](https://github.com/hkhcoder/vprofile-project) by **@hkhcoder**.
Containerization and Docker Compose setup by **[@Flack74](https://github.com/Flack74)** for DevOps practice and learning.

---

## 📄 License

This project is licensed under the [MIT License](LICENSE).
