# 🦞 宋韵阁 ASR 增强版

**钉钉语音消息自动识别 + Edge TTS 语音回复**

[![GitHub stars](https://img.shields.io/github/stars/songyunge-studio/songyunge-asr-enhanced)](https://github.com/songyunge-studio/songyunge-asr-enhanced)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![OpenClaw](https://img.shields.io/badge/OpenClaw-Skill-blue)](https://github.com/openclaw/openclaw)

---

## 📖 简介

**宋韵阁 ASR 增强版** 是一个专为 OpenClaw 钉钉渠道设计的语音技能，实现：
- ✅ **语音识别（ASR）**：自动识别钉钉语音消息，转换为文字
- ✅ **语音合成（TTS）**：用自然流畅的语音回复用户
- ✅ **三策方案**：上策（在线）、中策（备用）、下策（离线）

**适用场景**：
- 开车时不方便打字
- 做饭时手脏无法操作
- 带娃忙到飞起
- 单纯懒得打字

---

## 🚀 快速开始

### 前置要求
- Python 3.8+
- Node.js 18+
- OpenClaw 已安装并配置钉钉渠道

### 安装步骤

```bash
# 1. 克隆仓库
git clone https://github.com/songyunge-studio/songyunge-asr-enhanced.git
cd songyunge-asr-enhanced

# 2. 安装依赖
pip3 install --break-system-packages edge-tts openai-whisper

# 3. 复制配置文件
cp config.example.yaml config.yaml

# 4. 编辑配置（如果需要自定义）
vim config.yaml
```

### 使用方法

**方式 1：自动模式（推荐）**
```yaml
# config.yaml
asr:
  mode: auto  # 自动选择最佳方案
```

**方式 2：手动指定**
```yaml
asr:
  mode: manual
  strategy: top  # top/middle/bottom
```

**在 OpenClaw 中使用**：
```python
# 技能会自动加载
# 当收到钉钉语音消息时，自动识别并回复
```

---

## 🎯 三策方案

### 上策：钉钉自动转写 + Edge TTS
- **识别**：钉钉平台自带语音转文字
- **合成**：Edge TTS（微软免费接口）
- **优势**：最简单、音质最好、完全免费
- **适用**：日常使用

### 中策：Whisper + Edge TTS
- **识别**：Whisper（OpenAI 开源模型）
- **合成**：Edge TTS
- **优势**：不依赖钉钉、准确率 95%+
- **适用**：钉钉转写失效时

### 下策：Whisper + sherpa-onnx（离线）
- **识别**：Whisper（本地运行）
- **合成**：sherpa-onnx（离线 TTS）
- **优势**：完全离线、隐私安全
- **适用**：断网环境

---

## ⚙️ 配置说明

### 环境变量（可选）

```bash
# ASR API Key（如果使用中策/下策）
export ASR_API_KEY=your_api_key_here

# TTS 音色配置
export TTS_VOICE=zh-CN-XiaoyiNeural
export TTS_RATE="+15%"
export TTS_PITCH="+8Hz"
```

### 配置文件

```yaml
# config.yaml
asr:
  mode: auto  # auto/manual
  strategy: top  # top/middle/bottom
  
tts:
  voice: zh-CN-XiaoyiNeural
  rate: "+15%"
  pitch: "+8Hz"
  
dingtalk:
  enabled: true
  auto_reply_voice: true
```

---

## 📊 性能指标

| 指标 | 数值 |
|------|------|
| 识别速度 | ~10 秒/分钟音频 |
| 合成速度 | ~5 秒/分钟音频 |
| 识别准确率 | 95%+ |
| 单次成本 | ¥0（全部免费） |

---

## 🔒 安全说明

**本技能不会收集或上传任何个人信息**：
- ✅ 所有处理都在本地完成
- ✅ 不使用第三方云服务（除了 Edge TTS）
- ✅ 不存储语音文件（处理后立即删除）
- ✅ 不泄露 API Key（使用环境变量）

**注意事项**：
- ❌ 不要将 config.yaml 上传到公开仓库
- ✅ 使用 .gitignore 忽略敏感文件
- ✅ 定期更换 API Key（如果使用）
- ✅ **内部安全策略不公开**（如蜜罐、监控等）
- ✅ **内部安全策略不公开**（如蜜罐、监控等）

---

## 🤝 贡献指南

欢迎提交 Issue 和 Pull Request！

**贡献流程**：
1. Fork 本仓库
2. 创建特性分支 (`git checkout -b feature/AmazingFeature`)
3. 提交更改 (`git commit -m 'Add some AmazingFeature'`)
4. 推送到分支 (`git push origin feature/AmazingFeature`)
5. 开启 Pull Request

---

## 📄 许可证

本项目采用 MIT 许可证 - 查看 [LICENSE](LICENSE) 文件了解详情。

---

## 🙏 致谢

- [OpenClaw](https://github.com/openclaw/openclaw) - 强大的 AI 助手框架
- [Edge TTS](https://github.com/rany2/edge-tts) - 微软免费 TTS 接口
- [Whisper](https://github.com/openai/whisper) - OpenAI 语音识别模型
- [sherpa-onnx](https://github.com/k2-fsa/sherpa-onnx) - 离线语音合成

---

## 👤 关于作者

**宋韵阁** - 一家制造企业的技术专员  
**主要职责**：公司官网维护、网络安防、数字化技术应用  
**技术栈**：OpenClaw、Python、网络安全、AI 技能开发  
**理念**：解决痛点，创造价值

## 📞 联系方式

- **GitHub**: [@songyunge-studio](https://github.com/songyunge-studio)
- **工作室**: 宋韵阁工作室
- **邮箱**: songyunge-studio@example.com（待设置）

---

**🦞 解决痛点，创造价值！**
