# 🏦 CoreLedger

<div align="center">

### **Ledger-Driven Banking Backend System**

> A production-grade banking backend focused on transaction consistency, ledger accounting, fraud detection, and secure API architecture.

[![Node.js](https://img.shields.io/badge/Node.js-18.x-green)](https://nodejs.org)
[![Express.js](https://img.shields.io/badge/Express.js-Backend-black)](https://expressjs.com)
[![MongoDB](https://img.shields.io/badge/MongoDB-Atlas-brightgreen)](https://mongodb.com)
[![Swagger](https://img.shields.io/badge/API_Docs-Swagger-orange)](http://localhost:3000/api-docs)

</div>

---

# 📌 Overview

CoreLedger is a production-style banking backend built to simulate how modern financial systems process and secure transactions.

The project focuses on backend engineering concepts commonly used in fintech infrastructure, including:

* Ledger-based accounting
* Atomic money transfers
* Fraud detection systems
* Idempotent APIs
* Transaction reversals
* Rate limiting and abuse prevention
* Secure authentication
* Audit logging

Instead of storing balances directly in the database, CoreLedger derives balances from immutable ledger entries, ensuring traceability and transactional consistency.

---

# 🚀 Core Features

## 🏦 Banking Infrastructure

### ✅ Double-Entry Ledger System

Every transaction creates:

* One DEBIT entry
* One CREDIT entry

Balance calculation:

```text
Balance = Total Credits - Total Debits
```

This approach provides:

* Financial consistency
* Complete auditability
* Safer transaction tracking

---

### ✅ Atomic Transactions

MongoDB sessions ensure:

* Debit and credit occur together
* Failed operations rollback automatically
* No partial transaction states

---

### ✅ Transaction Reversal

Supports secure reversal handling with:

* Duplicate reversal prevention
* Ledger consistency
* Reversal tracking

---

# 🛡️ Security & Abuse Prevention

## ✅ JWT Authentication

* Token-based authentication
* Protected routes
* Middleware-driven authorization

---

## ✅ Rate Limiting

Protection against:

* Brute-force attacks
* API abuse
* Transaction spam

Implemented limits:

| Type         | Limit               |
| ------------ | ------------------- |
| Login        | 5 attempts / 15 min |
| Transactions | 10 req / min        |
| Global       | 100 req / min       |

---

## ✅ Daily Transaction Limit

Implemented banking-style transaction caps:

* ₹50,000/day transfer limit
* Aggregation-based monitoring
* Suspicious activity prevention

---

## ✅ Idempotency Protection

Duplicate payments are prevented using unique `idempotencyKey` values.

This ensures:

* Safe retries
* No accidental duplicate charges
* Better reliability during network failures

---

# 🚨 Fraud Detection Engine

CoreLedger includes a rule-based fraud detection system.

### Risk Signals

The system evaluates:

* High-value transactions
* Rapid transaction frequency
* Suspicious transfer patterns

---

### Automated Actions

| Risk Level | Action         |
| ---------- | -------------- |
| Low        | ALLOW          |
| Medium     | VERIFY         |
| High       | BLOCK          |
| Critical   | FREEZE ACCOUNT |

---

### Fraud Logs

Every suspicious activity is stored with:

* User reference
* Account reference
* Risk score
* Trigger reason
* Action taken
* Timestamp

---

# 🔒 Account Management

Implemented features:

* Account creation
* Freeze / unfreeze functionality
* Status-based transaction validation
* Audit logging

---

# 📄 API Documentation

Interactive API documentation is available using Swagger UI.

### Features

* Live endpoint testing
* Request/response examples
* Organized endpoint documentation

### Access

```text
http://localhost:3000/api-docs
```

---

# 🏗️ System Architecture

```text
Client Request
      │
      ▼
Rate Limiter
      │
      ▼
JWT Authentication Middleware
      │
      ▼
Controller Layer
      │
   ┌──┴──┐
   │     │
   ▼     ▼
Models  Services
(MongoDB) (Fraud Engine)
   │
   ▼
Ledger System
(Balance = Credits - Debits)
```

---

# 🛠️ Tech Stack

| Layer                  | Technology         |
| ---------------------- | ------------------ |
| Runtime                | Node.js            |
| Framework              | Express.js         |
| Database               | MongoDB + Mongoose |
| Authentication         | JWT                |
| Documentation          | Swagger            |
| Security               | express-rate-limit |
| Password Hashing       | bcryptjs           |
| Environment Management | dotenv             |

---

# 📂 Project Structure

```text
src/
├── controllers/
├── middleware/
├── models/
├── routes/
├── services/
├── app.js
└── server.js
```

---

# ⚙️ Installation & Setup

## 1️⃣ Clone Repository

```bash
git clone https://github.com/VanshAgrawal01/coreledger
cd coreledger
```

---

## 2️⃣ Install Dependencies

```bash
npm install
```

---

## 3️⃣ Configure Environment Variables

Create a `.env` file:

```env
PORT=3000
MONGO_URL=your_mongodb_uri
JWT_SECRET=your_secret_key
```

---

## 4️⃣ Start Development Server

```bash
npm run dev
```

---

# 🔗 API Reference

## Authentication APIs

| Method | Endpoint             | Description   |
| ------ | -------------------- | ------------- |
| POST   | `/api/auth/register` | Register user |
| POST   | `/api/auth/login`    | Login user    |
| POST   | `/api/auth/logout`   | Logout user   |

---

## Account APIs

| Method | Endpoint                     | Description         |
| ------ | ---------------------------- | ------------------- |
| POST   | `/api/accounts`              | Create account      |
| GET    | `/api/accounts`              | Get user accounts   |
| GET    | `/api/accounts/balance/:id`  | Get account balance |
| POST   | `/api/accounts/freeze/:id`   | Freeze account      |
| POST   | `/api/accounts/unfreeze/:id` | Unfreeze account    |

---

## Transaction APIs

| Method | Endpoint                                | Description         |
| ------ | --------------------------------------- | ------------------- |
| POST   | `/api/transactions`                     | Create transaction  |
| GET    | `/api/transactions`                     | Transaction history |
| GET    | `/api/transactions/accounts/:id/ledger` | Ledger entries      |
| POST   | `/api/transactions/:id/reverse`         | Reverse transaction |

---

# 🧠 Engineering Concepts Demonstrated

* Ledger-based accounting
* Atomic database transactions
* Idempotent APIs
* Fraud risk scoring
* Secure backend architecture
* Abuse prevention systems
* Financial transaction consistency

---

# 🎯 Why This Project Matters

CoreLedger demonstrates backend engineering concepts beyond traditional CRUD applications.

This project reflects understanding of:

* Financial system design
* Transaction consistency
* Security engineering
* Backend architecture
* Production-style API development

---

# 👨‍💻 Author

## Vansh Agrawal

* GitHub: [https://github.com/VanshAgrawal01/coreledger](https://github.com/VanshAgrawal01/coreledger)
* LinkedIn: [https://www.linkedin.com/in/vansh-agrawal-275b57375/](https://www.linkedin.com/in/vansh-agrawal-275b57375/)

---

# ⭐ Final Note

> CoreLedger was built to simulate real backend engineering decisions used in modern financial systems, focusing on reliability, consistency, and security.
