# biz-speak-skill

An AI agent skill that rewrites technical output into business language.
把 AI 的技术输出改写成业务语言。

[English](#english) · [中文](#中文)

---

## English

When an AI agent finishes a task, it reports in file names, function names, and implementation details. This skill rewrites that output into business language a non-technical reader can act on. Unshipped plans work too.

**Install** — copy the whole `biz-speak` folder into your platform's skills directory:

| Platform | Path |
|---|---|
| Cursor | `.cursor/skills/biz-speak/` |
| Claude | `.claude/skills/biz-speak/` |
| Qoder | your project's skills directory |
| Other | adapt to your platform's skill format |

**Usage**

```
/biz-speak
```

**Docs**

- [`SKILL.md`](SKILL.md) — the rules: output structure, task-type variations, transformation rules, anti-patterns
- [`examples/`](examples/) — bug fix, new feature, refactor, plan

---

## 中文

AI 完成任务后，产出的总结通常充满技术细节：文件名、函数名、实现方式。这个技能把那段输出改写成业务方能直接使用的业务语言。尚未执行的实施计划也适用。

**安装** —— 复制整个 `biz-speak` 目录到对应平台的技能目录：

| 平台 | 路径 |
|---|---|
| Cursor | `.cursor/skills/biz-speak/` |
| Claude | `.claude/skills/biz-speak/` |
| Qoder | 项目的技能目录 |
| 其他 | 按该平台的技能格式改造 |

**用法**

```
/biz-speak
```

**说明文档**

- [`SKILL.md`](SKILL.md) —— 规则本体：输出结构、任务类型变体、改写规则、反面例子
- [`examples/`](examples/) —— 修 bug、新功能、重构、计划

---

## License · 许可

MIT
