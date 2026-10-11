# MaiBot 提示词防注入与越狱指令拦截插件 (prompt_injection_guard_new)

专为 MaiBot 打造的企业级提示词安全网关（Prompt Injection Firewall）。能够实时检测并拦截针对大模型的恶意越狱攻击、系统指令覆盖、身份劫持、提示词窥探及有害引导。

## 多层防御架构

1. 规则过滤层（第一道防线）：基于高性能正则字典库，实时检测常见的越狱关键词、角色扮演欺骗（如 DAN 模式）、系统指令重置前缀等。
2. 语义复核层（第二道防线）：对于疑似攻击的高危消息，调用专用安全判别任务（已适配 MaiBot 1.2.5 `task_name="utils"` 契约）进行语义意图二次分类。
3. 动态反制策略：对确认的攻击请求执行静默阻断、人设警告或自动禁言。

## 配置项详解

| 配置项 | 类型 | 默认值 | 说明 |
| :--- | :--- | :--- | :--- |
| `[plugin].enabled` | bool | `true` | 是否开启防注入安全守护 |
| `[guard].min_rule_hits` | int | `2` | 触发二次安全复核的最小规则命中数 |
| `[guard].enable_llm_check` | bool | `true` | 是否启用大模型语义深度判别 |
| `[guard].action` | string | `"block"` | 拦截动作：`"block"`（静默丢弃）、`"warn"`（回复警告） |
| `[guard].main_task_name` | string | `"utils"` | 判别模型任务名（已适配 1.2.5 规范） |

## 开源协议

本项目采用 MIT 许可证开源，详情请参阅 [LICENSE](LICENSE)。
