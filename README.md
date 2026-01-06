AIBILL RADIUS - Billing System for RTRW.NET

Modern, full-stack billing system for RTRW.NET ISP with proper Nairobi (EAT, UTC+3) timezone handling and integrated M-Pesa, WhatsApp, and SMS notifications.

🎯 Key Features

✅ Proper Nairobi Timezone Handling - All dates stored in UTC, displayed in EAT

🎨 Premium UI - Mobile-first responsive design with dark mode

⚡ Modern Stack - Next.js 15, TypeScript, Tailwind CSS, Prisma

🔐 Secure - Built-in authentication structure

📱 SPA Experience - Fast, smooth navigation without page reloads

💳 M-Pesa Integration - STK Push and payment callbacks

📩 Notifications - WhatsApp and SMS alerts for invoices and events

🚀 Tech Stack

Framework: Next.js 15 (App Router)

Language: TypeScript

Styling: Tailwind CSS

Database: MySQL with Prisma ORM

Icons: Lucide React

Date Handling: date-fns with timezone support

Messaging: WhatsApp & SMS APIs

Payments: M-Pesa API

📋 Features Overview
Admin Panel Modules

Dashboard - Overview with stats and real-time data

PPPoE Management - Users and profiles

Hotspot Management - Vouchers, profiles, and templates

Agent Management - Reseller accounts

Invoices - Billing and payment tracking

Payment Gateway - M-Pesa, Midtrans, Xendit

Keuangan - Financial reporting

Sessions - Active connections monitoring

WhatsApp & SMS Integration - Automated notifications for invoices, alerts, and payments

Network Management - Router/NAS configuration

Network Map - Visual network topology

Settings - Company profile, cron jobs, GenieACS

🕐 Timezone Handling (Nairobi/EAT)

This project solves the UTC vs Nairobi timezone issue that can affect billing accuracy.

How It Works:

Database Storage (UTC)

All dates stored in MySQL as UTC

Prisma handles UTC storage automatically

Display (EAT)

Frontend converts UTC to Nairobi/EAT using date-fns-tz

Functions in src/lib/timezone.ts:

toEAT() - Convert UTC to EAT for display

toUTC() - Convert EAT to UTC for storage

formatEAT() - Format dates in EAT

isExpired() - Check expiry in EAT context

Environment Configuration

TZ="Africa/Nairobi"
NEXT_PUBLIC_TIMEZONE="Africa/Nairobi"

Example Usage:
import { formatEAT, isExpired, toUTC } from '@/lib/timezone';

// Display date in Nairobi time
const displayDate = formatEAT(user.createdAt, 'dd/MM/yyyy HH:mm');

// Check if expired
const expired = isExpired(user.expiredAt);

// Convert user input to UTC before saving
const utcDate = toUTC(userInputDate);
await prisma.user.create({ data: { expiredAt: utcDate } });

💳 Payment & Notifications

M-Pesa Integration:

STK Push payments

Webhook callbacks to update invoices automatically

Notifications:

WhatsApp notifications via templates

SMS alerts via configured SMS gateway

🛠️ Setup Instructions
1. Database Setup
mysql -u root -p
CREATE DATABASE aibill_radius;
exit;

2. Environment Configuration

Update .env with your credentials:

DATABASE_URL="mysql://root:YOUR_PASSWORD@localhost:3306/aibill_radius?connection_limit=10&pool_timeout=20"
TZ="Africa/Nairobi"
NEXT_PUBLIC_TIMEZONE="Africa/Nairobi"

# M-Pesa API
MPESA_CONSUMER_KEY="your_key"
MPESA_CONSUMER_SECRET="your_secret"
MPESA_SHORTCODE="123456"

# WhatsApp/SMS API
WHATSAPP_API_KEY="your_whatsapp_key"
SMS_API_KEY="your_sms_key"

3. Install Dependencies & Setup Database
npm install
npx prisma generate
npx prisma db push

4. FreeRADIUS Integration Setup
bash scripts/setup-sudoers.sh
sudo systemctl restart freeradius

5. Run Development Server
npm run dev


Open http://localhost:3000
 → redirects to /admin.

6. Production Deployment with PM2
npm run build
pm2 start npm --name "aibill-radius" -- start
# or
pm2 start ecosystem.config.js

📁 Project Structure
src/
├── app/
│   ├── admin/              # Admin panel routes
│   └── page.tsx            # Root redirect to /admin
├── lib/
│   ├── timezone.ts         # Nairobi timezone utilities
│   └── utils.ts            # General utilities
└── prisma/
    └── schema.prisma       # Database schema

🔒 Security

Environment variables for sensitive data

Password hashing with bcryptjs

SQL injection prevention via Prisma

XSS protection via Next.js

📊 Database Models

Users (Admin, Agent, User)

PPPoE Users & Profiles

Hotspot Vouchers & Profiles

Sessions (RADIUS accounting)

Invoices & Payments

Payment Gateways

Routers/NAS

WhatsApp Providers & Templates

Company Settings

🚧 TODO

 Add multi-language support

 Add analytics and charts

 Export reports (PDF, Excel)

 Finalize GenieACS integration

 Enhance RADIUS server automation

📝 License

Private - Proprietary software for AIBILL RADIUS

👨‍💻 Development

Built with ❤️ for Kenyan ISPs with proper Nairobi timezone handling and integrated M-Pesa, WhatsApp, and SMS services.

Critical Note: Always use formatEAT() and toEAT() functions when displaying dates. Never display raw UTC dates from the database.
