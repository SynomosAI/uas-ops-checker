# AGENTS.md — 给 AI Agent 的工作指引

本文件面向自动化 AI Agent（编码助手、配置校验器、知识库机器人）。人类读者请看 [README.md](README.md)。

## 这个仓库是什么

`uas-ops-checker` 是一个**行业接入域配置包**，不是可运行的 SDK。核心资产是四个 JSON 文件：`domain.manifest.json`（域声明）、`gate-map.json`（阻断规则）、`privacy.json`（隐私声明）、`checker.io.json`（MCP 核验器契约）。域 ID `uas`，当前状态 RESERVED。

## 可用的工作命令

```bash
# 查看本域声明（属性 / 签发方 / 红线）
cat domain.manifest.json

# 查看阻断规则
cat gate-map.json

# 查看 MCP 核验器输入输出契约
cat checker.io.json
```

前置依赖：本机已安装 git。本仓无可执行代码，无需 Python / Node 运行时。

## 约定（Do）

- 修改属性取值或红线时，**必须同步** `domain.manifest.json` 与 `gate-map.json`（每条红线都要有对应阻断规则）。
- 认领后在 `domain.manifest.json` 的 `operator` 与 `checker_endpoint` 中填注真实信息。
- 保持 `profile_version` 字段与平台骨架版本一致。

## 禁止（Don't）

- 不要改动 `LICENSE` 的版权主体（© 2026 SynomosAI）。
- 不要在核验器输出中生成「合格 / 可飞 / 已合规」等专业判定结论——核验器只出示与核验出处链。
- 不要删除 `privacy.json` 或其必填字段——缺失即符合性校验失败。
- 不要在仓库内提交任何密钥、令牌或真实运营方数据。

## 边界

本仓专注**低空 · 无人驾驶航空器运营**域；不覆盖其他空域类别、不覆盖有人驾驶航空器、不下适航审定结论。
