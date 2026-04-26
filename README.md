# Snap-to-Cloud-Accountant 🧾🤖

一个基于 **n8n** + **Gemini 2.5 Flash-lite** 的全自动智能记账工作流。
只需向 Telegram 发送收据照片或 PDF，AI 会自动识别并同步到 Google Sheets 和云端存档。

## 🌟 核心特性
- **AI 智能识别**：利用 `gemini-2.5-flash-lite` 提取金额、商户及分类。
- **双模态支持**：支持直接发送照片 (Image) 或 PDF 文档。
- **持久化存储**：集成 **Supabase (PostgreSQL)** 作为后端数据库，防止重启丢数据。
- **云端同步**：自动重命名并保存原始收据至 Google Drive，并登记至 Google Sheets。

## 🛠️ 部署指南

### 1. 准备工作
- **n8n**: 部署在 Hugging Face Spaces (使用本项目提供的 Dockerfile)。
- **Database**: 申请一个免费的 [Supabase](https://supabase.com/) 项目。
- **AI API**: 在 [Google AI Studio](https://aistudio.google.com/) 获取 Gemini API Key。
- **Bot**: 通过 BotFather 创建一个 Telegram Bot。

### 2. 环境变量配置 (Secrets)
在你的部署环境（如 HF Spaces 的 Settings > Secrets）中添加以下变量：

| 变量名 | 说明 |
| :--- | :--- |
| `N8N_ENCRYPTION_KEY` | 随机长字符串，用于加密凭据 |
| `DB_TYPE` | 固定填写 `postgresdb` |
| `DB_POSTGRESDB_HOST` | Supabase 提供的 Host 地址 |
| `DB_POSTGRESDB_PORT` | `5432` |
| `DB_POSTGRESDB_DATABASE` | `postgres` |
| `DB_POSTGRESDB_USER` | `postgres` |
| `DB_POSTGRESDB_PASSWORD` | 你的数据库密码 |
| `DB_POSTGRESDB_SSL_REJECT_UNAUTHORIZED` | `false` |

### 3. 导入工作流
1. 启动 n8n 后，点击 **Import from File**。
2. 选择本仓库中的 `workflow.json`。
3. 在 n8n 中配置你的 Telegram、Google Drive 和 Gemini 凭据。

## 📁 分类字典
本项目内置了严格的审计分类逻辑：
- **F&B**: Meals, Groceries, Drinks, Dessert
- **Transport**: Fuel, Toll, Parking, Maintenance
- **Fixed expenses**: Utilities, Rental, Housing Loan...
*(完整字典请查阅 workflow.json 内部节点说明)*

## 📄 License
MIT License
