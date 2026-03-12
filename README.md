# 🏥 Serenity Mental Health Therapy Center — Management System

<p align="center">
  <img src="https://img.shields.io/badge/Java-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white"/>
  <img src="https://img.shields.io/badge/JavaFX-007396?style=for-the-badge&logo=java&logoColor=white"/>
  <img src="https://img.shields.io/badge/Hibernate-59666C?style=for-the-badge&logo=hibernate&logoColor=white"/>
  <img src="https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white"/>
  <img src="https://img.shields.io/badge/BCrypt-FF6B6B?style=for-the-badge&logo=letsencrypt&logoColor=white"/>
</p>

<p align="center">
  A fully-featured desktop application built to digitize and streamline patient management for a mental health therapy center — developed as part of the <strong>ITS1155 - ORM Concepts</strong> module in the <strong>Graduate Diploma in Software Engineering (GDSE)</strong> at <strong>IJSE</strong>.
</p>

---

## 📌 Table of Contents

- [About the Project](#about-the-project)
- [Features](#features)
- [Tech Stack](#tech-stack)
- [Architecture](#architecture)
- [Database Relationships](#database-relationships)
- [Getting Started](#getting-started)
- [Screenshots](#screenshots)
- [What I Learned](#what-i-learned)

---

## 📖 About the Project

The **Serenity Mental Health Therapy Center** serves over **3,000 patients annually** across Sri Lanka. Previously relying on manual paper-based records, the center needed a digital system to manage patients, therapists, therapy programs, sessions, and payments efficiently.

This system replaces that manual workflow with a secure, role-based desktop application built on **JavaFX** and **Hibernate ORM**.

---

## ✨ Features

### 👤 User Role Management
- **Admin** — Manages therapists and therapy programs
- **Receptionist** — Manages patients, schedules sessions, and processes payments
- Secure login with **BCrypt** password hashing
- Role-based access control (RBAC)

### 🧑‍⚕️ Therapist Management *(Admin Only)*
- Add, update, delete, and view therapist profiles
- Assign therapists to therapy programs
- Track therapist schedules and availability

### 📋 Therapy Program Management *(Admin Only)*
- Create, modify, and remove therapy programs
- Define name, duration, cost, and description
- Link programs to assigned therapists

### 🙋 Patient Management
- Full CRUD for patient profiles
- Store medical history and therapy records
- Search and filter patients by therapy sessions
- Support for multi-program enrollment per patient

### 📅 Therapy Session Scheduling
- Book, reschedule, and cancel therapy appointments
- Assign available therapists based on schedule
- Conflict detection for overlapping sessions

### 💳 Payment & Invoice Management
- Process upfront payments per therapy program
- Generate and print invoices
- Track pending and completed transactions

### 📊 Reporting & Analytics
- Admin: Therapist performance & session statistics
- Receptionist: Financial reports & payment tracking
- Both roles: Read-only patient therapy history

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| UI | JavaFX |
| ORM | Hibernate 6.x |
| Query Language | HQL / JPQL |
| Database | MySQL |
| Password Security | BCrypt (jBCrypt) |
| Build Tool | Maven |
| Config | `hibernate.properties` |
| Design Patterns | Façade, Factory |

---

## 🏗️ Architecture

This project follows a **Layered Architecture**:

```
├── presentation/        # JavaFX Controllers & FXML Views
├── business/            # Service / Façade Layer
├── dao/                 # Data Access Objects (Hibernate)
├── entity/              # Hibernate Entity Classes
├── util/                # SessionFactory, Validators, Helpers
└── exception/           # Custom Exception Classes
```

---

## 🔗 Database Relationships

```
Therapist     ──< TherapySession      (One-to-Many)
TherapyProgram──< TherapySession      (One-to-Many)
Patient       ──< TherapySession      (One-to-Many)
Patient       >──< TherapyProgram     (Many-to-Many via Enrollment)
TherapySession──< Payment             (One-to-Many)
User          ──  Role                (Many-to-One)
```

---

## 🚀 Getting Started

### Prerequisites
- Java 17+
- MySQL 8.x
- Maven 3.x

### Setup

1. **Clone the repository**
   ```bash
   git clone https://github.com/your-username/serenity-therapy-system.git
   cd serenity-therapy-system
   ```

2. **Configure the database**

   Edit `src/main/resources/hibernate.properties`:
   ```properties
   hibernate.connection.url=jdbc:mysql://localhost:3306/serenity_db
   hibernate.connection.username=your_username
   hibernate.connection.password=your_password
   hibernate.hbm2ddl.auto=update
   hibernate.show_sql=true
   ```

3. **Build & Run**
   ```bash
   mvn clean install
   mvn javafx:run
   ```

### Default Credentials *(change after first login)*
| Role | Username | Password |
|---|---|---|
| Admin | `admin` | `Admin@1234` |
| Receptionist | `receptionist` | `Recep@1234` |

---

## 📸 Screenshots

> *(Add your screenshots here)*

---

## 🎓 What I Learned

Building this project gave me hands-on experience with concepts that go far beyond textbook definitions:

- **Entity Lifecycle States** — Understanding Transient → Persistent → Detached was a turning point in debugging Hibernate sessions
- **Lazy vs Eager Fetching** — Hit N+1 query issues early and learned why fetch strategy decisions matter at the relationship level
- **Cascade Types** — Choosing between `PERSIST`, `MERGE`, `REMOVE`, and `ALL` taught me how tightly coupled entity operations can be
- **BCrypt** — Learned that hashing ≠ encryption, and why one-way hashing is the correct approach for passwords
- **Design Patterns in Practice** — Retrofitting the Façade pattern mid-project was painful; now I design architecture before writing code

---

## 📄 License

This project was developed for academic purposes as part of the GDSE programme at IJSE.

---

<p align="center">Made with ☕ and a lot of Hibernate debugging — <strong>GDSE Batch 71/72 · IJSE</strong></p>