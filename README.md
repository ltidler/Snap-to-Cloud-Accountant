# Snap-to-Cloud-Accountant 🧾🤖

[![Hugging Face Spaces](https://img.shields.io/badge/%F0%9F%A4%97%20Hugging%20Face-Spaces-blue)](https://huggingface.co/spaces/ltidler/n8n-smart-accountant)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

**Snap-to-Cloud-Accountant** is an AI-powered personal finance automation tool. Simply snap a photo of your receipt and send it to a Telegram bot—AI will audit the expense, categorize it, save it to Google Sheets, and back up the original image to Google Drive.

---

## 🚀 Quick Start Guide (Step-by-Step)

### 1. Preparation (The "Keys")
Before deployment, prepare these free API keys:
* **Telegram Bot Token**: Create via [@BotFather](https://t.me/botfather).
* **Google AI (Gemini) Key**: Get it at [Google AI Studio](https://aistudio.google.com/).
* **Supabase Database**: Register at [Supabase](https://supabase.com/) and create a project. This ensures your n8n credentials and workflows are persistent.
* **Google Cloud Credentials**: Create a Service Account JSON to access Google Sheets and Drive.

### 2. Deployment (Hugging Face)
1.  Log in to [Hugging Face](https://huggingface.co/) and click **New Space**.
2.  Select **Docker** as the SDK and choose the **Blank** template.
3.  Go to `Files and versions` -> `Add file` -> `Create a new file`.
4.  Name it `Dockerfile` and paste the content from the `Dockerfile` in this repository.

### 3. Configuration (Secrets)
In your Hugging Face Space, go to **Settings** -> **Variables and Secrets**. Add the following **Secrets**:

| Key | Value / Source |
| :--- | :--- |
| `N8N_ENCRYPTION_KEY` | A random long string (e.g., `accountant_secure_123`) |
| `DB_TYPE` | `postgresdb` |
| `DB_POSTGRESDB_HOST` | From Supabase Project Settings -> Database -> Host |
| `DB_POSTGRESDB_PASSWORD` | Your Supabase Database Password |
| `DB_POSTGRESDB_PORT` | `5432` |
| `DB_POSTGRESDB_USER` | `postgres` |
| `N8N_USER_MANAGEMENT_DISABLED` | `false` (Recommended for security) |

### 4. The "Brain" (Import Workflow)
1.  Open your running n8n instance from the Hugging Face App view.
2.  Follow the setup instructions to create your owner account.
3.  Inside n8n, click the **three dots `...`** (top right) -> **Import from File**.
4.  Select the **`workflow.json`** from this repository.
5.  Open the nodes (Telegram, Gemini, Google Sheets) to link your credentials.
6.  Click **Save** and toggle the **Active** switch to **ON**.

---

## 📂 Expense Categorization (SOP)
The AI utilizes built-in logic to ensure consistent auditing:
* **F&B**: Meals, Groceries, Drinks, Dessert.
* **Transport**: Fuel, Tolls, Parking, Vehicle Maintenance, Road Tax.
* **Fixed Expenses**: Utilities, Rental, Mortgage, Subscriptions.
* **Daily Needs**: Toiletries, Personal care, Pharmacy, Cleaning supplies.
* **Lifestyle**: Apparel, Skincare, Movies, Gym, Gaming.

---

## 🏗️ Tech Stack
* **Automation Engine**: n8n (Self-hosted on HF)
* **AI Model**: Google Gemini 2.5 Flash-lite
* **Database**: Supabase (PostgreSQL)
* **Storage**: Google Drive & Google Sheets

## 📄 License
This project is licensed under the [MIT License](LICENSE).

---
**Author**: [ltidler](https://github.com/ltidler)  
*If you find this project useful, please consider giving it a ⭐ on GitHub!*
