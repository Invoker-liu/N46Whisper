# 项目上下文

## 目的
N46Whisper 是基于 Google Colab 的视频字幕生成应用。开发初衷旨在提高乃木坂46（以及坂道系）字幕组日语视频的制作效率，但亦适于所有外语视频的字幕制作。目标是搭建并提供一个简单且自动化的使用平台，以节省生产成品字幕的时间和精力。

## 技术栈
- **运行环境**：Google Colab (Jupyter Notebook)
- **语音识别**：faster-whisper (基于 CTranslate2 的 Whisper 优化实现)
- **字幕处理**：pysubs2 (字幕文件读写库)
- **AI 翻译**：OpenAI GPT API、Google Gemini API
- **文件处理**：Google Drive 集成、本地文件上传
- **编程语言**：Python 3

## 项目约定

### 代码风格
- 中英双语注释，面向中文用户为主
- 使用 Colab 表单参数 (`@param`) 提供用户交互界面
- 函数和变量使用 snake_case 命名

### 架构模式
- 单一 Jupyter Notebook 作为主应用入口
- 模块化辅助脚本 (如 `srt2ass.py`)
- 按执行顺序组织的单元格流程：文件选择 → 模型加载 → 转录 → 翻译 → 导出

### 测试策略
- 手动测试为主，在 Colab 环境中验证
- 关注不同模型大小、语言、文件格式的兼容性

### Git工作流
- main 分支为稳定版本
- dev 分支用于开发和测试新功能

## 领域上下文
- **Whisper 模型**：OpenAI 开发的自动语音识别模型，支持多语言转录和翻译
- **faster-whisper**：使用 CTranslate2 重新实现的 Whisper，速度更快、内存占用更低
- **VAD (Voice Activity Detection)**：语音活动检测，用于提高转录精度
- **字幕格式**：SRT (简单文本) 和 ASS (高级样式) 是主要输出格式
- **坂道系**：日本偶像团体系列，包括乃木坂46、樱坂46、日向坂46等

## 重要约束
- 依赖 Google Colab 免费/付费 GPU 资源
- OpenAI API 有速率限制和费用
- Whisper 模型对长音频和嘈杂环境有精度限制
- 项目已宣布不再维护更新

## 外部依赖
- **Google Colab**：运行环境和 GPU 资源
- **Google Drive**：文件存储和访问
- **OpenAI API**：GPT-3.5-turbo 翻译服务
- **Google Gemini API**：替代翻译服务
- **Hugging Face**：faster-whisper 模型下载
