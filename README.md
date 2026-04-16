# ⚔️ MIMS | Military Inventory Management System

[![Next.js](https://img.shields.io/badge/Next.js-15-black?style=for-the-badge&logo=next.js)](https://nextjs.org/)
[![Prisma](https://img.shields.io/badge/Prisma-ORM-2D3748?style=for-the-badge&logo=prisma)](https://www.prisma.io/)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-3.4-38B2AC?style=for-the-badge&logo=tailwind-css)](https://tailwindcss.com/)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-16-336791?style=for-the-badge&logo=postgresql)](https://www.postgresql.org/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5-3178C6?style=for-the-badge&logo=typescript)](https://www.typescriptlang.org/)

> **MIMS** is a comprehensive, enterprise-grade supply chain and orchestration platform designed for multi-tier military logistics. From Central Command to frontline local bases, MIMS ensures resource availability, transparency, and accountability.

---

## 🚀 Key Modules

| Module | Description | Icon |
| :--- | :--- | :---: |
| **Strategic Command** | High-level overview and regional distribution management. | 🏛️ |
| **Logistics Engine** | Automated request, approval, and dispatch workflows. | 🚛 |
| **Arsenal Control** | Precision tracking of weapons, medical supplies, and rations. | 🔫 |
| **Audit & Compliance** | Full-spectrum audit logs and transaction history tracking. | 📜 |
| **Alert System** | Proactive notifications for low stock, expiry, and maintenance. | ⚠️ |

---

## 🏗️ Technical Architecture

```mermaid
graph TD
    User((User)) --> NextJS[Next.js 15 Frontend/API]
    NextJS --> NextAuth[NextAuth.js]
    NextJS --> Prisma[Prisma ORM]
    Prisma --> DB[(PostgreSQL)]
    NextJS --> Resend[Resend Email Service]
    NextJS --> UploadThing[UploadThing Assets]
```

---

## 📊 Database Schema (ERD)

```mermaid
erDiagram
    USER ||--o{ REQUEST : creates
    USER ||--o{ AUDIT_LOG : generates
    UNIT ||--o{ USER : contains
    UNIT ||--o{ STOCK_ITEM : holds
    UNIT ||--o{ REQUEST : "origin/target"
    ITEM ||--o{ STOCK_ITEM : defines
    BATCH ||--o{ TRANSACTION : logs
    REQUEST ||--|{ REQUEST_ITEM : includes
    TRANSFER ||--o{ TRANSACTION : triggers
```

---

## 🛠️ Tech Stack

- **Framework**: [Next.js 15](https://nextjs.org/) (App Router)
- **Database**: [PostgreSQL](https://www.postgresql.org/)
- **ORM**: [Prisma](https://www.prisma.io/)
- **Auth**: [NextAuth.js](https://next-auth.js.org/)
- **Styling**: [Tailwind CSS](https://tailwindcss.com/)
- **UI Components**: [Lucide React](https://lucide.dev/)
- **Security**: Argon2/Bcrypt Password Hashing, Multi-level RBAC (Role-Based Access Control)
- **Validation**: [Zod](https://zod.dev/)

---

## 📦 Project Structure

```text
mims/
├── prisma/               # Database Schema & Seed scripts
├── src/
│   ├── app/              # Next.js Pages & API Routes
│   ├── features/         # Core business logic & slices
│   ├── shared/           # Reusable components & utilities
│   │   ├── components/   # UI Library (Topbar, Sidebar, etc.)
│   │   ├── lib/          # API Clients (Prisma, Auth, Resend)
│   │   └── types/        # Global TypeScript definitions
```

---

## 🏁 Getting Started

### 1. Clone the repository
```bash
git clone https://github.com/Vishaldubey2210/DBMS_Project.git
cd mims
```

### 2. Install dependencies
```bash
npm install
```

### 3. Setup Environment Variables
Create a `.env` file in the root directory:
```env
DATABASE_URL="postgresql://user:password@localhost:5432/mims"
NEXTAUTH_SECRET="your-secret"
RESEND_API_KEY="re_..."
```

### 4. Database Setup
```bash
npx prisma generate
npx prisma db push
npm run seed
```

### 5. Run Development Server
```bash
npm run dev
```

---

## 🛡️ Security & Roles
MIMS implements a strict **Command Hierarchy**:
- **SUPER_ADMIN**: Full system orchestration.
- **REGIONAL_ADMIN**: Manages Regional Depots and distributions.
- **BASE_OFFICER**: Handles local unit inventory and requests.
- **AUDITOR**: Read-only oversight with full log access.

---

Built with ❤️ for **DBMS Final Project**.
