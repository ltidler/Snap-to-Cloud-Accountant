# Snap-to-Cloud-Accountant 🧾🤖

[![Hugging Face Spaces](https://img.shields.io/badge/%F0%9F%A4%97%20Hugging%20Face-Spaces-blue)](https://huggingface.co/spaces/ltidler/n8n-smart-accountant)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

**Snap-to-Cloud-Accountant** 是一款基于 **n8n** + **Gemini 2.5 Flash-lite** 的个人财务自动化工具。通过简单的照片拍摄或 PDF 转换，AI 会自动审计收据、提取结构化数据并同步至 Google Sheets，同时利用 Supabase 实现数据的永久存储。

---

## 🌟 核心功能
- **智能审计**：使用 `gemini-2.5-flash-lite` 模型，精准识别商户、日期、金额、货币及消费分类。
- **多格式支持**：兼容 Telegram 发送的图片（Image）与 PDF 文件。
- **数据持久化**：后端接入 **Supabase (PostgreSQL)**，解决 Hugging Face 重启导致的工作流丢失问题。
- **云端归档**：原始凭证自动重命名并保存至 Google Drive，方便日后查账。

## 🛠️ 部署指南 (Hugging Face)

本项目提供专用的 `Dockerfile`，支持在 Hugging Face Spaces 一键部署。

### 1. 环境变量配置 (Secrets)
在部署环境（Settings > Secrets）中配置以下变量，确保连接到你的数据库：

| 变量名 | 必填 | 说明 |
| :--- | :--- | :--- |
| `N8N_ENCRYPTION_KEY` | 是 | 随机长字符串，用于保护你的凭据安全 |
| `DB_TYPE` | 是 | 固定值为 `postgresdb` |
| `DB_POSTGRESDB_HOST` | 是 | Supabase 数据库 Host 地址 |
| `DB_POSTGRESDB_PASSWORD` | 是 | Supabase 数据库密码 |
| `DB_POSTGRESDB_PORT` | 是 | `5432` |
| `DB_POSTGRESDB_USER` | 是 | `postgres` |
| `DB_POSTGRESDB_SSL_REJECT_UNAUTHORIZED` | 是 | `false` |

### 2. 导入工作流
1. 运行 n8n 后，进入界面选择 **Import from File**。
2. 上传本仓库中的 `workflow.json`。
3. 在节点中配置你的 **Telegram Bot Token**、**Gemini API Key** 及 **Google Service Account**。

## 📂 支出分类字典 (SOP)
为了保证记账的一致性，系统内置了以下分类逻辑：
- **F&B (餐饮)**: Meals, Groceries, Drinks, Dessert
- **Transport (出行)**: Fuel, Toll, Parking, Maintenance, Road tax
- **Fixed Expenses (固定开支)**: Utilities, Rental, Housing Loan, Subscriptions
- **Daily Needs (生活百货)**: Toiletries, Personal care, Pharmacy
- **Lifestyle (生活方式)**: Skincare, Clothing, Entertainment, Gym

## 🏗️ 技术架构
- **Logic Engine**: n8n (Self-hosted on HF)
- **AI Model**: Google Gemini 2.5 Flash-lite
- **Database**: Supabase (PostgreSQL)
- **Storage**: Google Drive & Google Sheets

## 📄 开源协议
本项目采用 [MIT License](LICENSE) 开源。

---
**Author**: [ltidler](https://github.com/ltidler)  
*注：本项目仅供个人财务管理使用，请妥善保管你的 API Keys 与加密密钥。*
