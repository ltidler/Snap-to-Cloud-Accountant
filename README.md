# Snap-to-Cloud-Accountant 🧾🤖

基于 n8n 和 Google Gemini 2.5 Flash-lite 的智能记账流。只需向 Telegram 发送一张收据照片或 PDF，系统即可自动识别、分类、存档并登记。

## 🌟 核心功能
- **双模态识别**：支持图片 (JPG/PNG) 和 PDF 文档。
- **AI 深度分析**：利用 `gemini-2.5-flash-lite` 提取金额、商户、日期及备注。
- **自动存档**：原始文件自动重命名并保存至 Google Drive。
- **多维度归类**：内置严格的分类字典（F&B, Transport, Lifestyle 等）。
- **实时反馈**：记账完成后通过 Telegram 自动回复确认详情。

## 🛠️ 技术栈
- **n8n**: 工作流自动化引擎。
- **Google Gemini**: 负责 OCR 与逻辑分析。
- **Telegram Bot**: 作为输入与输出终端。
- **Google Workspace**: 存储文件 (Drive) 与汇总数据 (Sheets)。

## 🚀 部署指南
1. **准备环境**：在 Hugging Face 或 VPS 上部署 n8n。
2. **导入工作流**：下载本仓库的 `workflow.json` 并导入 n8n。
3. **配置凭据**：在 n8n 中设置 Telegram API、Google Gemini API 和 Google OAuth2。
4. **设置变量**：修改 Google Sheets 节点中的 `documentId` 为你自己的表格 ID。

## 📝 环境变量参考
请参考 `.env.example` 设置你的运行环境。
