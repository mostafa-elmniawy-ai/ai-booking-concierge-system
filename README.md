- Dynamic Deposit: Calculates 5% of the service price on the server side.
- Webhook Confirmation: The booking is ONLY marked as confirmed and paid when Paymob sends a success webhook.
- Smart Rescheduling: Calculates deposit differences if a user upgrades or downgrades a service.

### 📈 4. Growth & Retention
- Smart Upselling: Automatically suggests a 20% discount on complementary services (e.g., Checkup + Cleaning) if a slot is available.
- Abandoned Cart Recovery: If a user ignores the payment link, the system waits 2 hours and sends an automated reminder.
- Automated Reminders: Proactively reminds users 24 hours before their appointment to reduce no-shows.

### 🛡️ 5. Enterprise Reliability
- Owner Notifications: Instantly alerts the clinic owner via Telegram on cancellations, reschedules, or escalations.
- Full Logging: Every conversation and action is logged in Supabase (bot_logs) for auditing.
- Error Handling: Built-in fallback workflows that apologize to the user and retry automatically if a node fails.
- Dynamic Config: All clinic settings (Name, Hours, Policy, WhatsApp number) are managed in a single Business Config node.

---

## 🛠️ Tech Stack
- Orchestration: n8n
- AI Engine: OpenAI GPT-4o-mini (Function Calling / Tools)
- Database: Supabase (PostgreSQL)
- Messaging: Telegram Bot API
- Payments: Paymob API

## 🚀 Setup & Deployment
To deploy this system for a new client:
1. Import the workflows into n8n.
2. Run the schema.sql in Supabase to create the required tables.
3. Update the Business Config node with the new client's details.
4. Set the environment variables for PAYMOB_API_KEY and TELEGRAM_BOT_TOKEN.
5. Activate the workflows.

---
<div align="center">
<i>Built with a focus on reliability, security, and autonomous decision-making.</i>
</div>
