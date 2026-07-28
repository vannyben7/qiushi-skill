# Qiushi Skill — Codex 优化封装版

这是 [HughYau/qiushi-skill](https://github.com/HughYau/qiushi-skill) 的衍生优化版本，面向 OpenAI Codex 的个人 Skill 安装与调用方式进行了重新封装。

## 原作者与上游项目

- 原始项目：[`HughYau/qiushi-skill`](https://github.com/HughYau/qiushi-skill)
- 原作者：**HughYau**
- 上游许可证：MIT License

求是方法库、方法论内容及相应参考资料来自 HughYau 的原始项目。感谢原作者建立并开放这一方法体系。

本仓库不是上游项目的官方发行版。这里的封装、目录调整和 Codex 适配由 **vannyben7** 完成。

## 本版本的优化

相对于上游将不同方法作为多个独立 Skill 暴露的方式，本版本主要进行了以下调整：

1. 提供单一公开入口 `qiushi-skill`，避免 Codex 的 Skill 菜单出现大量内部方法。
2. 将十个方法收纳到 `references/`，作为同一工作流内部的方法库。
3. 增加工作流内部解析规则，使方法之间通过相对路径传递和读取，不再尝试调用独立的顶层 Skill。
4. 增加适用于 Codex 的 `agents/openai.yaml` 元数据、中文简介和默认提示。
5. 保留 `/qiushi-skill`、`qiushi-skill`、`求是工作流` 等自然触发方式。
6. 可作为 `edict-agent` 的求是预检来源。

## 安装

```bash
git clone https://github.com/vannyben7/qiushi-skill.git
mkdir -p "${CODEX_HOME:-$HOME/.codex}/skills"
cp -R qiushi-skill "${CODEX_HOME:-$HOME/.codex}/skills/qiushi-skill"
```

安装后开启新的 Codex 会话，让 Skill 被重新发现。

## 使用

```text
/qiushi-skill 帮我从零规划并推进这个任务
```

也可以直接说：

```text
用 qiushi-skill 的求是工作流分析这个项目
```

公开入口会先读取 `references/workflows/METHOD.md` 选择工作流，再按需加载相应的内部方法。

## 目录结构

```text
qiushi-skill/
├── SKILL.md
├── agents/
│   └── openai.yaml
└── references/
    ├── workflows/
    ├── investigation-first/
    ├── contradiction-analysis/
    ├── concentrate-forces/
    ├── practice-cognition/
    ├── criticism-self-criticism/
    ├── overall-planning/
    ├── mass-line/
    ├── protracted-strategy/
    └── spark-prairie-fire/
```

## 许可证与归属

本仓库沿用上游项目的 MIT License。原作者、上游地址和本版本修改说明同时记录在 [`NOTICE.md`](NOTICE.md) 中。

