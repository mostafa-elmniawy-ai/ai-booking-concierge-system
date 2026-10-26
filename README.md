<div align="center">

# 🤖 AI Booking Concierge
### Enterprise-Grade Agentic AI System

[![n8n](https://img.shields.io/badge/n8n-Workflow-orange?style=for-the-badge&logo=n8n)](https://n8n.io)
[![OpenAI](https://img.shields.io/badge/OpenAI-GPT--4o--mini-blue?style=for-the-badge&logo=openai)](https://openai.com)
[![Supabase](https://img.shields.io/badge/Supabase-PostgreSQL-green?style=for-the-badge&logo=supabase)](https://supabase.com)
[![Paymob](https://img.shields.io/badge/Paymob-Payment-red?style=for-the-badge)](https://paymob.com)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](https://opensource.org/licenses/MIT)

*An advanced, production-ready AI Booking System that autonomously manages appointments, enforces strict business rules, handles real payments, and recovers from errors gracefully.*

</div>

---

## 📖 Overview
This is not a simple chatbot. It is a fully autonomous Agentic AI System built on a micro-workflow architecture. It acts as a 24/7 virtual receptionist that communicates naturally, verifies identities, manages a real-time calendar, processes deposits via Paymob, and autonomously follows up with customers.

## 🏗️ System Architecture
The system is designed using a Micro-Workflow Architecture to ensure stability and separation of concerns. The AI Agent acts as the brain, orchestrating 7 distinct workflows:

1. User Interface: Telegram Bot API.
2. Core Brain: n8n AI Agent (OpenAI GPT-4o-mini).
3. Memory & State: Supabase & Window Buffer Memory.
4. Tools: Database querying, Paymob Link Generation, Escalation.
5. Payment Gateway: Paymob (Webhooks & Checkout).
6. Schedulers: Cron jobs for Reminders & Follow-ups.

## 📂 Workflows Directory
The repository contains 7 interconnected n8n workflows designed to work together:

| File | Description |
|------|-------------|
| 01_Main_Agentic_Bot.json | The core brain. Handles conversations, decides actions, and enforces business rules. |
| 02_Demo_Bot_Instant_Booking.json | A lightweight version for basic demos (no payment required). |
| 03_Basic_Bot_No_Deposit.json | Standard booking bot without the payment gateway dependency. |
| 04_Paymob_Payment_Webhook.json | Listens for real payment confirmations from Paymob, updates DB, notifies user. |
| 05_Paymob_Link_Generator.json | Triggered by the AI to generate secure Paymob checkout links. |
| 06_Booking_Reminders.json | Automated Cron job that sends reminders 24 hours before appointment. |
| 07_Followup_Scheduler.json | Autonomous follow-up engine for users who abandoned the booking process. |

---

## ✨ Key Features & Capabilities

### 🧠 1. Agentic AI & Natural Language
- Multilingual: Communicates in Egyptian Arabic, English, or Franco-Arabic naturally.
- Memory Retention: Retains the last 12 messages per session for contextual conversations.
- Strict Validation: Rejects invalid inputs, media files, and enforces strict phone number formatting (11 digits, valid prefixes).
- Identity Verification: Cross-checks names/phones against existing bookings using fuzzy matching (handles typos and Arabic variations).
- Graceful Escalation: Automatically escalates complaints or angry customers to a human via escalate_to_human.

### 📅 2. Smart Scheduling & Availability
- Live Availability Check: Calculates open slots dynamically for the next 14 days (10 AM - 6 PM) using Supabase.
- Double-Booking Prevention: Locks the time slot for 65 minutes while the user is in the payment process.
- No Duplicate Bookings: Prevents the same user from booking multiple times on the same day.

### 💳 3. Payment-First Architecture (Paymob)
- Zero-Trust AI: The AI is physically incapable of booking an appointment without a successful payment.
