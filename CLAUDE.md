# small sunshine prompt-injection-guard

## 官方上游与版本溯源
- 官方仓库（Upstream Repository）：https://github.com/MCYXG233/prompt_injection_guard_new
- 官方作者（Author / Maintainer）：MCYXG233
- 功能定位：提示词防注入与恶意越狱指令拦截插件
- 本地演进定位：基于官方上游最新版本，融入本地生产环境兼容性定制与稳定性加固。
- 本地专属定制：本地将非法模型名 tool_use 纠正为 utils，并修复 1.2.5 签名兼容性。


## 插件基本信息

- 插件 ID：`small_sunshine.prompt-injection-guard`
- 频率：low（高频 = 群聊主路径 / 中频 = 辅助工具 / 低频 = 偶尔触发）
- 描述：prompt injection 防御

## 主要功能 / 配置要点

- injection detection

## 接入依赖

- 走 MaiBot SDK 2.x（`MaiBotPlugin` 基类 + `Action`/`Command`/`HookHandler` 装饰器）
- 容器内一律用服务名（如 `napcat`、`core`），禁止 `127.0.0.1`
- 配置通过 `PluginConfigBase`（Pydantic v2）声明 schema

## 关键日志（启动标志）

插件加载时输出：`xxx 已加载`。
如未加载，参考 MaiBot 启动日志 `已加载=N 失败=M 未激活=K`。

## 用法

由 MaiBot LLM 自主调用（Action/Tool）或通过命令（Command）触发。
详细用法参考 plugin 的 README（如有）或上游文档。

## 历史脚注

- 2026-08-15：自动生成（深度 plan B10）
- 本仓库是主人本地副本，与服务器 `/MaiMBot/plugins/` 同步使用。
- 修改走 CLAUDE.md 工作流（本机改 → 本机 commit → 部署服务器 → 验证加载）。

## 已应用的本机修复（深度 plan 进度）

- T1（hardcoded localhost）：— 无生产代码命中
- T3（except: pass）：— 见 plan 进度
- T5（deprecated asyncio）：— 无生产代码命中
- T6（单元测试）：见功能列表
