# 编程红绿灯 · Vibe Light

> 用 Cursor 写代码时，不用切窗口，余光就知道 AI 是在等你点确认、正在跑，还是已经空闲。

[![macOS](https://img.shields.io/badge/macOS-12%2B-lightgrey)](https://github.com/artistannabelle/vibe-light/releases)
[![Windows](https://img.shields.io/badge/Windows-10%2F11-lightgrey)](https://github.com/artistannabelle/vibe-light/releases)
[![Cursor](https://img.shields.io/badge/Cursor-支持-blue)](https://cursor.com/)
[![License](https://img.shields.io/badge/License-闭源-red)]()

Mac 屏幕角落悬浮 **🔴🟡🟢 红绿灯**。红灯时可一键 **通过 / 拒绝**，代你在 Cursor 里确认授权。

📖 **产品介绍页**：[artistannabelle.github.io/vibe-light](https://artistannabelle.github.io/vibe-light/)  
🪟 **Windows 界面预览**：[artistannabelle.github.io/vibe-light/windows-preview.html](https://artistannabelle.github.io/vibe-light/windows-preview.html)

> **本仓库为闭源发布渠道**：仅提供安装包与使用说明，**不含源代码**。

---

## 一、产品介绍

### 它解决什么问题？

用 Cursor 让 AI 写代码时，窗口常被飞书、浏览器挡住——你不知道 AI 是在跑、在等你授权，还是已经停了。

**Vibe Light** 读取 Cursor **本机数据**，用一盏红绿灯告诉你当前状态，显示在屏幕角落预览条上，不用切回 Cursor。

### 红绿灯含义

| 灯 | 含义 | 你可以做什么 |
|----|------|--------------|
| 🔴 红 | **待授权** — AI 等你点「运行 / 允许」 | 预览条一键 **通过 / 拒绝** |
| 🟡 黄 | **执行中** — AI 正在写代码或跑命令 | 安心做别的事，余光扫一眼即可 |
| 🟢 绿 | **空闲** — 当前没有任务在执行 | 可以休息或发下一条指令 |

### 核心特点

- **本地运行** — 只读 Cursor 本机文件，数据不上传云端
- **角落常驻** — 预览条可拖拽，开会写文档时余光可见
- **一键授权** — 红灯时不用切回 Cursor 点确认
- **轻量安装** — 下载 zip，双击安装脚本即可（无需 Xcode）

---

## 二、快速使用

### 下载

前往 **[Releases](https://github.com/artistannabelle/vibe-light/releases/latest)** 下载 **v1.3.0**：

| 平台 | 安装包 |
|------|--------|
| **macOS** | `Vibe-Light-1.3.0-macOS.zip` |
| **Windows** | `Vibe-Light-1.3.0-Windows.zip` |

### macOS 安装（4 步）

**系统要求：** macOS 12+ · [Cursor](https://cursor.com/) · Python 3（macOS 通常自带）

1. **解压** zip 到任意文件夹
2. **双击** `安装 Vibe Light.command`（若提示无法打开，见下方注意事项）
3. 打开 **系统设置 → 隐私与安全性 → 辅助功能**，勾选 **Vibe Light**
4. **重启 Cursor**（安装脚本会一并配置 Hook）

安装完成后，App 位于 `/Applications/Vibe Light.app`，屏幕角落会出现预览条。

### Windows 安装（4 步）

**系统要求：** Windows 10/11 · [Cursor](https://cursor.com/) · [Python 3](https://www.python.org/downloads/)（安装时勾选 Add to PATH）

安装前可先查看 **[界面预览](https://artistannabelle.github.io/vibe-light/windows-preview.html)**（浏览器模拟，非真实程序）。

1. **解压** `Vibe-Light-1.3.0-Windows.zip`
2. **双击** `安装 Vibe Light.bat`
3. 从开始菜单或桌面打开 **Vibe Light**
4. **重启 Cursor**

预览条会出现在屏幕底部；托盘区有 Vibe Light 图标。

### 日常使用

1. 先打开 **Cursor**，再打开 **Vibe Light**（或设为登录时自动打开）
2. 看角落红绿灯判断 AI 状态
3. 🔴 红灯时，在预览条点 **通过** 或 **拒绝**
4. 预览条可拖拽到顺手的位置；点月亮/太阳图标切换深/浅色

---

## 三、注意事项

### 权限与安全

| 项目 | 说明 |
|------|------|
| **辅助功能** | 一键「通过 / 拒绝」需要此权限；未开启时只能看灯，不能代点 |
| **本机数据** | 仅读取 Cursor 本地对话与状态，**不上传**任何内容 |
| **闭源软件** | 本仓库不提供源码；仅供个人学习使用，未经授权请勿商用 |

### 常见问题

**Q：双击安装脚本提示「无法打开」或「来自未知开发者」？**

在访达中 **右键 → 打开**，或在 **系统设置 → 隐私与安全性** 里点「仍要打开」。安装脚本不会上传你的数据。

**Q：灯一直不亮 / 显示未连接？**

1. 确认 Cursor 已打开且有对话在进行  
2. 重启 Vibe Light  
3. 确认已重启 Cursor（Hook 安装后需要）

**Q：点了「通过」但灯还是红的？**

检查辅助功能是否已勾选 **Vibe Light**（路径选 `/Applications/Vibe Light.app`）。

**Q：换电脑怎么迁移？**

重新下载 zip，在新电脑上执行安装脚本即可。配置文件在 `~/Library/Application Support/Vibe Light/`。

### 卸载

```bash
rm -rf "/Applications/Vibe Light.app"
rm -rf "$HOME/Library/Application Support/Vibe Light"
```

---

## 四、反馈与支持

- 🐛 问题反馈 → [Issues](https://github.com/artistannabelle/vibe-light/issues)
- ⭐ 觉得有用 → 点 **Star**，帮助我们了解有多少人在用
- 💡 功能建议 → 欢迎在 Issues 留言

---

## 许可证

Copyright © 2026. All rights reserved.

本软件为**闭源**产品。您可下载并使用发布包供个人非商业用途；禁止反编译、再分发或商业使用（除非获得书面授权）。
