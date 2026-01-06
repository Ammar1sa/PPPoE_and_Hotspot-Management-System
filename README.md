# AIBILL RADIUS – Billing System for RTRW.NET

Modern, full-stack billing system for RTRW.NET ISP with proper Nairobi (EAT, UTC+3) timezone handling and integrated M-Pesa, WhatsApp, and SMS notifications.

---

## 🎯 Key Features

- Proper Nairobi Timezone Handling (EAT / UTC+3)
- Mobile-first premium UI with dark mode
- Single Page Application (SPA) experience
- Secure authentication-ready architecture
- Fast, scalable, and production-ready
- Integrated M-Pesa STK Push & callbacks
- WhatsApp & SMS automated notifications

---

## 🚀 Tech Stack

- Framework: Next.js 15 (App Router)
- Language: TypeScript
- Styling: Tailwind CSS
- Database: MySQL
- ORM: Prisma
- Icons: Lucide React
- Date Handling: date-fns & date-fns-tz
- Messaging: WhatsApp & SMS APIs
- Payments: M-Pesa API

---

## 📋 Admin Panel Modules

- Dashboard – Real-time stats & analytics
- PPPoE Management – Users & profiles
- Hotspot Management – Vouchers & templates
- Agent Management – Resellers
- Invoices – Billing & payment tracking
- Payment Gateway – M-Pesa, Midtrans, Xendit
- Keuangan – Financial reports
- Sessions – Active connections monitoring
- Notifications – WhatsApp & SMS automation
- Network Management – Router & NAS configs
- Network Map – Visual topology
- Settings – Company profile, cron jobs, GenieACS

---

## 🕐 Timezone Handling (Africa/Nairobi)

- Database: All timestamps stored in UTC
- Frontend: Converted and displayed in EAT
- Utilities:
  - `toEAT()`
  - `toUTC()`
  - `formatEAT()`
  - `isExpired()`

---

## 🌍 Environment Variables

```bash
TZ="Africa/Nairobi"
NEXT_PUBLIC_TIMEZONE="Africa/Nairobi"


---

**Made with ❤️ by Mwaki Denis**

