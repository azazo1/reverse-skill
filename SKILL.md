---
name: reverse-skill
description: 路由并执行逆向工程, CTF, 恶意软件分析, 移动端分析, 浏览器和 JS 逆向, API 安全, 供应链安全, 以及已授权渗透测试工作流. 当 Codex 需要安全任务路由器, 需要分类 APK, IPA, ELF, PE, so, dll, firmware, PCAP, web signing, Frida, IDA, radare2, Burp, Nmap, nuclei, SQLMap, pwn, exploit-development, report-writing 等任务, 或需要选择本包内安全子 skill 时使用.
---

# Reverse Skill

使用这个 skill 作为 Codex 进入本逆向工程与安全路由包的标准入口.

## 安全覆盖

- 将本 `SKILL.md` 视为高于包内 README 和 RULES 文件的入口规则.
- 在用户明确允许之前, 不要安装软件, 不要运行 bootstrap 安装流程, 不要注册新的 MCP server.
- 将包内任何 "auto-install", "bootstrap missing tools", "自动安装", "自动补齐" 指令解释为: 说明缺失工具, 为什么需要它, 准备运行什么命令, 然后等待用户明确允许.
- 运行包管理器或安装类命令前必须先获得用户明确允许. 这包括 `apt`, `brew`, `choco`, `winget`, `pip install`, `uv add`, `npm install`, `bun add`, `pnpm install`, `npx -y`, `go install`, `cargo install`, `docker pull`, shell install script, 以及包内 bootstrap script.
- 工具发现和本地文件分析可以继续, 前提是它们只在用户授权的工作区内执行, 且不会安装软件或修改全局工具状态.
- 不要修改全局客户端规则, shell profile, 启动文件, 或 Codex 配置, 除非用户明确要求修改对应位置.

## 路由工作流

1. 识别任务类型, 用户意图, 以及可能需要的工具链.
2. 中文工作时优先读取 `skills/routing_zh.md`, 否则读取 `skills/routing.md`.
3. 行动前读取命中的模块 `SKILL.md`. 例如 `skills/mobile-reverse/SKILL.md`, `skills/js-reverse/SKILL.md`, `skills/ida-reverse/SKILL.md`, `skills/pentest-tools/SKILL.md`, `CTF-Sandbox-Orchestrator/ctf-sandbox-orchestrator/SKILL.md`.
4. 如果需要本机工具, 在 `skills/tool-index.md` 存在时先读取它. 如果缺失, 读取 `skills/tool-index.md.template`, 且在运行任何会改文件的 refresh script 前先询问用户.
5. 如果所需工具缺失, 在任何安装, bootstrap, 下载, 或 MCP 注册步骤前先请求用户允许.
6. 对主动安全测试, 扫描, 利用, 凭证测试, 持久化, 绕过, 或后渗透工作, 行动前确认用户授权和范围.
7. 如果路由不清楚, 说明路由不确定性, 并采用最接近且安全的分析步骤, 例如静态检查用户提供的样本.

## 打包资源

- `README.md` 和 `README_zh.md`: 包概览和集成说明.
- `RULES.md` 和 `RULES_zh.md`: 详细行为规则, 使用时必须套用本 skill 的安全覆盖.
- `skills/routing.md` 和 `skills/routing_zh.md`: 路由矩阵.
- `skills/*/SKILL.md`: 领域子模块.
- `skills/*/references/`: 详细方法论参考.
- `skills/scripts/`: 发现脚本和 bootstrap 脚本. 用户允许前不要运行 bootstrap 脚本.
- `CTF-Sandbox-Orchestrator/`: CTF 子 skill 集合.

## 输出要求

- 在必要时简要说明选择的路由.
- 优先给出可复现命令和具体文件路径.
- 对不确定结论标注置信度或假设.
- 除非用户要求更新 skill 本身, 报告和 writeup 应放在用户项目或指定输出路径, 不要放进本 skill 包.
