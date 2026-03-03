# 🚀 StudentApp – Dockerized Deployment on AWS (EC2 + RDS)

## 📌 Project Overview

This project demonstrates the end-to-end Dockerization and deployment of a Java-based Student Management Web Application on AWS infrastructure.

The application is deployed inside a Docker container running on an Ubuntu EC2 instance and connected to an Amazon RDS MySQL database.

---

## 🏗️ Architecture

* AWS EC2 (Ubuntu) – Application Server
* AWS RDS (MySQL) – Database
* Docker – Containerization
* GitHub – Source Code Repository

---

# 🔥 Deployment Steps Performed

## 1️⃣ Create RDS (MySQL)

* Created an Amazon RDS instance with MySQL engine
* Configured DB name, username, and password
* Enabled public access 
* Allowed port 3306 in Security Group

---

## 2️⃣ Create Ubuntu EC2 Instance

* Launched Ubuntu EC2 instance
* Allowed inbound rules:

  * Port 22 (SSH)
  * Port 8080 (Application Access)
  * port 3306 (MYsql)

---

## 3️⃣ Configure Application Files

* Created `Dockerfile`
* Updated `context.xml`
* Created `docker-compose.yml` (optional future enhancement)

### Updated `context.xml`:

* Replaced:

  * RDS endpoint
  * Database name
  * Username
  * Password

---

## 4️⃣ Connect to EC2 Instance

```bash
ssh -i key.pem ubuntu@public-ip
```

---

## 5️⃣ Update Packages

```bash
sudo apt update
```

---

## 6️⃣ Install MySQL Client

```bash
sudo apt install mysql-client -y
```

---

## 7️⃣ Connect to RDS from EC2

```bash
mysql -h <RDS-endpoint> -u <username> -p
```

---

## 8️⃣ Create Database

```sql
CREATE DATABASE studentapp;
USE studentapp;
```

* Imported SQL query file from repository to create tables

```sql
CREATE TABLE IF NOT EXISTS students(
    student_id INT NOT NULL AUTO_INCREMENT,
    student_name VARCHAR(100) NOT NULL,
    student_addr VARCHAR(100) NOT NULL,
    student_age VARCHAR(3) NOT NULL,
    student_qual VARCHAR(20) NOT NULL,
    student_percent VARCHAR(10) NOT NULL,
    student_year_passed VARCHAR(10) NOT NULL,
    PRIMARY KEY (student_id)
);
exit;
```

---

## 9️⃣ Install Docker

Installed Docker using official documentation or package manager.

Verified installation:

```bash
docker --version
```

---

## 🔟 Clone Repository

```bash
git clone <repository-url>
cd studentapp-ui
```

---

## 1️⃣1️⃣ Navigate to Docker Folder

```bash
cd docker
```

---

## 1️⃣2️⃣ Build Docker Image

```bash
docker build .
```

---

## 1️⃣3️⃣ Verify Image

```bash
docker images -a
```

---

## 1️⃣4️⃣ Tag Docker Image

```bash
docker tag <image_id> studentapp-ui:latest
```

---

## 1️⃣5️⃣ Run Docker Container

```bash
docker run -d -p 8080:8080 studentapp-ui:latest
```

---

## 1️⃣6️⃣ Verify Running Container

```bash
docker ps
```

---

## 🌍 Access Application

Open in browser:

```
http://<EC2-Public-IP>:8080/student
```

Application frontend loads successfully and connects to RDS database.

---

# ✅ Final Outcome

✔ Successfully Dockerized Java WAR application
✔ Deployed on AWS EC2
✔ Integrated with Amazon RDS MySQL
✔ Verified frontend and database connectivity
✔ Implemented secure port configuration

---

# 📈 Future Improvements

* Push Docker image to Docker Hub
* Implement Docker Compose for multi-service management
* Add Nginx Reverse Proxy
* Implement CI/CD Pipeline
* Deploy using ECS or Kubernetes

---

# 👩‍💻 Author

Shweta Bhore
Aspiring DevOps Engineer
