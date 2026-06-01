<div align="center">

# 👨‍💼 staffHub — Servlet-Based Employee Management Web App

**Classic Java EE stack: Servlets + Hibernate + JSP + MySQL — with one-click Excel export.**

[![Java](https://img.shields.io/badge/Java-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white)](https://www.oracle.com/java/)
[![Hibernate](https://img.shields.io/badge/Hibernate-59666C?style=for-the-badge&logo=hibernate&logoColor=white)](https://hibernate.org)
[![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white)](https://www.mysql.com)
[![Maven](https://img.shields.io/badge/Maven-C71A36?style=for-the-badge&logo=apachemaven&logoColor=white)](https://maven.apache.org)

</div>

---

## 🎯 Overview

`staffHub` is a lean **employee management** web app written the old-school enterprise way — pure Servlets + Hibernate + JSP — perfect as a teaching reference or as a starting point for migrating to Spring Boot.

> _Want a screenshot here? Save `docs/screenshot.png` and link `![](docs/screenshot.png)`._

---

## ✨ Features

- ➕ Create, view, and manage employee records
- 📊 **Export to Excel** via `ExcelExportServlet` (Apache POI)
- 🗂️ Hibernate ORM via `HibernateUtil` (SessionFactory singleton)
- 🌐 **REST resource** alongside JSP (Jakarta REST: `JakartaEE8Resource`)
- 🧪 Clear DAO separation — `EmployeeDao` is unit-test friendly

---

## 🧰 Tech Stack

| Concern        | Tech                                   |
| -------------- | -------------------------------------- |
| **Language**   | Java 17                                |
| **Web**        | Jakarta Servlets, JSP, JSTL            |
| **ORM**        | Hibernate 6                            |
| **REST**       | Jakarta RESTful Web Services           |
| **DB**         | MySQL 8                                |
| **Excel**      | Apache POI                             |
| **Build**      | Maven                                  |
| **Runtime**    | Tomcat 10 / Payara / any Jakarta EE 10 |

---

## 🏁 Quick Start

### Prerequisites
- JDK 17+, Maven 3.9+, MySQL 8, Tomcat 10

### 1 · Clone
```bash
git clone https://github.com/Shashu1007/staffHub.git
cd staffHub
```

### 2 · Database
```sql
CREATE DATABASE staffhub;
CREATE USER 'staffhub'@'localhost' IDENTIFIED BY 'staffhub';
GRANT ALL PRIVILEGES ON staffhub.* TO 'staffhub'@'localhost';
```
Update credentials in `ConnectionFactory.java` (or, ideally, externalize to `application.properties`).

### 3 · Build & deploy
```bash
mvn clean package
cp target/*.war $TOMCAT_HOME/webapps/staffhub.war
$TOMCAT_HOME/bin/catalina.sh run
```
Open **http://localhost:8080/staffhub/** 🎉

---

## 📁 Project Structure

```
staffHub/
├── ConnectionFactory.java          # JDBC DataSource bootstrap
├── Employee.java                   # JPA entity
├── EmployeeDao.java                # CRUD operations
├── EmployeeServlet.java            # Controller (form POST handler)
├── ExcelExportServlet.java         # /export → .xlsx download
├── HibernateUtil.java              # SessionFactory singleton
├── JakartaEE8Resource.java         # Sample REST resource
├── JakartaRestConfiguration.java   # JAX-RS app config
├── employee-list.jsp               # View
└── pom.xml
```

---

## 🔌 Endpoints

| Method | URL                | Purpose                |
| ------ | ------------------ | ---------------------- |
| GET    | `/employee-list`   | Render JSP list view   |
| POST   | `/EmployeeServlet` | Add employee           |
| GET    | `/export`          | Download Excel (.xlsx) |
| GET    | `/api/employees`   | JSON list (REST)       |

---

## 🗺️ Roadmap

- [ ] Migrate to Spring Boot 3 + Thymeleaf
- [ ] Add CRUD UI (edit/delete) — currently create-only
- [ ] Externalize all credentials to env vars
- [ ] Containerize (Dockerfile + docker-compose with MySQL)
- [ ] Add JUnit tests for `EmployeeDao`

---

## 🤝 Contributing

PRs welcome. Run a quick `mvn verify` before submitting.

---

<div align="center">

**Built by [Shashank R](https://github.com/Shashu1007)**
🐙 [GitHub](https://github.com/Shashu1007) · 💼 [LinkedIn](https://linkedin.com/in/shashank1007) · 📧 sshashu777@gmail.com

⭐ _Helpful? A star goes a long way._

</div>
