# Suricata Platform

[![License](https://img.shields.io/github/license/jalalsadeghi/suricata-platform)](LICENSE)

This repository demonstrates an integrated cybersecurity platform featuring a containerized **Suricata Intrusion Detection System (IDS)**, a backend built in **NestJS**, a **PostgreSQL** database, real-time log monitoring using the **ELK Stack** (Elasticsearch, Logstash, Kibana), and an advanced identity and access management system using **Keycloak**.

---

## 🚀 Features

- **Backend API** built with NestJS
- **Containerized IDS** using Suricata
- **Database integration** with PostgreSQL
- **Real-time Log Monitoring and Visualization** using ELK Stack (Elasticsearch, Logstash, Kibana)
- **Identity and Access Management (IAM)** using Keycloak
- **Docker Compose** for quick and easy setup

---

## 🛠️ Tech Stack

- **Backend:** NestJS, TypeScript
- **Database:** PostgreSQL
- **IDS/IPS:** Suricata
- **Log Management:** ELK Stack (Elasticsearch, Logstash, Kibana)
- **Authentication & IAM:** Keycloak
- **Containerization:** Docker, Docker Compose

---

## 📦 Prerequisites

- Docker & Docker Compose
- Git

Make sure you have Docker installed and running on your system. Instructions to install Docker on Ubuntu can be found [here](https://docs.docker.com/engine/install/ubuntu/).

---

## 🔧 Installation & Setup

1\. **Clone the repository:**

```bash
git clone https://github.com/jalalsadeghi/suricata-platform.git
cd suricata-platform
```

2\. **Create directories with proper permissions:**

```bash
mkdir suricata-logs
chmod 777 suricata-logs
```

3\. **Start all services:**

```bash
docker-compose up --build
```

4\. **Verify services:**

- **Backend API:** [http://localhost:3000](http://localhost:3000)
- **PostgreSQL Database:** `localhost:5432`
- **Elasticsearch:** [http://localhost:9200](http://localhost:9200)
- **Kibana Dashboard:** [http://localhost:5601](http://localhost:5601)
- **Keycloak Dashboard:** [http://localhost:8080](http://localhost:8080) (default username/password: `admin`/`admin`)
- **Suricata Logs:** stored locally in `./suricata-logs`

To verify Suricata functionality:

```bash
ping 8.8.8.8

docker exec -it suricata tail -f /var/log/suricata/eve.json
```

You should see alerts related to ICMP traffic.

---

## 🔑 Keycloak Setup

- **Login to Keycloak** at [http://localhost:8080](http://localhost:8080) using `admin`/`admin`.
- Create a new Realm named `suricata-platform`.
- Create a new Client within your realm for backend or frontend integration.
- Configure authentication, users, roles, and permissions through the Keycloak dashboard.

---

## 📊 Viewing Logs in Kibana

1. Access Kibana Dashboard at [http://localhost:5601](http://localhost:5601).
2. Go to **Management → Data Views** and create a new Data View with the index pattern:

```
suricata-*
```

3. Select `@timestamp` as the time field.
4. Navigate to **Discover** to view and analyze Suricata logs in real-time.

---

## 📂 Project Structure

```
suricata-platform/
├── backend/             # NestJS Backend
├── elk/                 # ELK configuration and setup
├── suricata-config/     # Suricata configuration
├── suricata-logs/       # Suricata logs storage
├── Dockerfile           # Dockerfile for NestJS Backend
└── docker-compose.yml   # Compose file for managing all containers
```

---

## 🤝 Contributing

Contributions are always welcome!

1. Fork the project.
2. Create your feature branch (`git checkout -b feature/AmazingFeature`).
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`).
4. Push to your branch (`git push origin feature/AmazingFeature`).
5. Open a Pull Request.

---

## 📄 License

Distributed under the MIT License. See [`LICENSE`](LICENSE) for more information.