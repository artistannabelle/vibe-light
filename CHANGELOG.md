# Changelog

## 1.2.0 — 2026-06-07（当前稳定 · GitHub 公开发布）

> 自本版起，本地修订号从 **1.2.x** 累加；下次整包发 GitHub 时为 **1.3.0**。详见 [VERSIONING.md](VERSIONING.md)。

### 本包相对 1.1.0 的主要升级
- **点发送即时黄灯**：`beforeSubmitPrompt` Hook + 直写 `status.json`
- **执行中不闪绿**：对话文件热更新期间保持黄灯
- **结束后可靠变绿**：pending 结束判定与 1.2s 冷静期，用户验收通过
- 完整修订记录见下方 1.1.1～1.1.6

## 1.1.6 — 2026-06-07

### 修复结束后不变绿
- 结束判定不再要求 analyze 先判绿；assistant 纯文字收尾 + 用户消息之后有回复 + 文件冷静 → 主动清 pending 并写绿灯
- 用「本次用户消息之后是否已有 assistant」区分「刚发送」与「真的结束」
- 冷静期 2.5s → 1.2s，结束后更快变绿

## 1.1.5 — 2026-06-07

### 执行过程中不再闪绿
- pending 存在时：须 analyze 已绿 + 本次用户消息已落盘 + assistant 纯文字收尾 + 对话文件 **冷静 2.5s** 才清 pending
- 对话文件仍在热更新时（2.5s 内有写入），即使出现 assistant 中间文字行也保持黄灯
- `is_agent_still_executing` 改用最后一条**有效**消息判断，忽略空行干扰

## 1.1.4 — 2026-06-07

### 修复点发送后「闪绿」缝隙
- pending 存在时，不再因上一轮 assistant 收尾或 analyze 判绿就误清 pending
- 仅当 transcript 已出现**本次发送**的用户消息且 assistant 纯文字收尾时，才清 pending 变绿

## 1.1.3 — 2026-06-07

### 点发送即时黄灯（加强）
- `beforeSubmitPrompt` Hook 在写入 pending 的**同时**直接刷新 `status.json` 为黄灯，预览条通过文件监听即时更新
- 采集器主循环固定 ~0.15s 轮询，不再空闲等待最长 2s 才发现 pending
- 预览条轮询间隔 0.8s → 0.35s（备用刷新）

## 1.1.2 — 2026-06-07

### 结束变绿优化（P0）
- `agent_pending.json` 被删除（如 `stop` Hook）时，采集器立即刷新状态，不再最多等 2 秒
- 对话文件出现 assistant 纯文字收尾时主动清除 pending，不依赖 `stop` Hook
- 修正 pending 存在时 analyze 已判绿仍被强行改黄的问题

## 1.1.1 — 2026-06-06

### 即时黄灯
- 新增 Cursor `beforeSubmitPrompt` Hook：用户点发送后立即写入 `agent_pending.json`
- 采集器读取 pending 状态，在对话文件更新前即显示 🟡「Agent 回复中」
- `stop` Hook 在 Agent 任务结束时清除 pending
- pending 期间采集器加速刷新（~0.15s）

## 1.1.0 — 2026-06-06

> **版本规则**：小修复只加修订号（`1.1.1`、`1.1.2`…）；整包发 GitHub 时次版本 +1（`1.2.0`、`1.3.0`）。详见 [VERSIONING.md](VERSIONING.md)。

### 与 1.1 草案相同的内容

### 正式版
- 移除演示模式（`demo_mode.json`、`--demo`、网页模拟红灯）
- 安装时自动清理残留演示文件

### 响应速度
- 用户发送消息后尽快显示 🟡「Agent 回复中」
- 对话文件变更约 0.4s 内触发采集刷新
- 预览条监听 status.json，写入后即时更新 UI

### 授权体验
- 点「通过」后立即变 🟡 执行中（不等 Cursor 对话档案更新）
- Shell 命令授权后正确区分「待确认」与「执行中」
- 不再每次点通过都弹出系统辅助功能授权框
- 辅助功能未开启时显示明确提示文案

### 安装
- 支持 Release 打包并安装到「应用程序」
- 采集器与配置安装到 `~/Library/Application Support/Vibe Light/`
- 新增 `install_app.command` 一键安装

### 未纳入本版的试验（已回滚）

- 「会话选择 A + 执行中判断 B」曾本地调试，导致黄灯难回绿灯 → **已回滚至 1.1.0 基线**，后续在 `1.1.x` 分步验证后再发

## 1.0.0 — 初始版本

- 角落红绿灯预览条
- Touch Bar / 主窗口「通过 / 拒绝」
- Cursor 本地数据采集与网页控制台
