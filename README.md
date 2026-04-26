# Snap-to-Cloud-Accountant 🚀

一个基于 n8n + Gemini AI 的全自动智能记账系统。

### ✨ 功能特性
- **多模态识别**：支持 Telegram 发送图片 (Receipt) 或文档 (PDF/Doc)。
- **AI 智能分析**：调用 Gemini 1.5 Pro 自动提取金额、类别、日期。
- **云端存档**：自动将原始文件上传至 Google Drive 指定文件夹。
- **自动汇总**：将分析结果实时写入 Google Sheets。

### 🛠️ 部署步骤
1. **克隆仓库**：`git clone ...`
2. **导入 n8n**：将 `workflow.json` 导入你的 n8n 实例。
3. **配置环境变量**：
   - `TELEGRAM_BOT_TOKEN`
   - `GEMINI_API_KEY`
   - `GOOGLE_CREDENTIALS` (JSON 格式)
