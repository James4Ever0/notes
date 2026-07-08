---
created: 2026-07-08T08:21:20+08:00
modified: 2026-07-08T08:21:43+08:00
---

# Export deepseek chat history

DeepSeek 网页版目前没有官方的“一键导出”按钮，但可以通过开源工具、用户脚本等方式实现。我整理了以下几种主流方案，你可以按需选择：

💻 浏览器扩展 (Extensions)
在浏览器中直接使用，图形化操作，比较方便。

· DeepSeek Exporter (sharkymew)：Chrome扩展。支持多选和批量导出为ZIP（内含JSON和MD）。纯本地处理，注重隐私。需在chrome://extensions开启开发者模式后安装。
· DeepSeek Exporter (agoramachina)：支持Chrome和Firefox。特点是功能全面，支持搜索、排序、批量导出ZIP，通过API获取数据更稳定。
· AI Exporter / AI Chat Export：支持多平台的通用扩展。可导出为PDF、MD、TXT、JSON、Word等多种格式。

📜 用户脚本 (Userscripts)
需配合 Tampermonkey 或 Violentmonkey 等脚本管理器使用。

· DeepSeek-Chat-Exporter：在聊天页面右上角增加导出按钮，支持导出MD、PDF、PNG图片。
· DeepseekWeb-enhance：功能强大的增强脚本，支持导出JSON/MD，还提供搜索、批量删除、重命名等对话管理功能。
· DeepSeek 对话导出器 (Exporter Plus)：专门适配DeepSeek V4版，支持导出思考链、工具调用、引用链接等。
· 一键导出脚本 (CSDN)：零依赖，可将全部对话历史导出为JSON/MD/ZIP，适合做完整备份。

🐍 编程方式 (Python)
适合喜欢命令行的技术用户。

· deepseek-chat-exporter：基于Selenium的Python脚本，可将历史记录导出为JSON文件。安装依赖后运行即可。

---

💎 总结与建议

· 追求方便：选浏览器扩展（如 DeepSeek Exporter），图形界面操作简单。
· 追求轻量和功能：选用户脚本（如 DeepseekWeb-enhance 或 DeepSeek-Chat-Exporter），功能强大且无需安装额外应用。
· 需要完整备份：选能批量导出的工具（如 agoramachina 的扩展或CSDN的脚本）。
· 技术爱好者：用 Python脚本，可实现自动化。

⚠️ 关于官方API：目前DeepSeek并未公开用于导出历史对话的官方API。现有工具大多通过模拟浏览器操作或调用内部接口实现。

选择时请注意查看工具是否适配当前网站版本，以防失效。
