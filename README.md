# 师兄 (senior-brother)

一个 Claude Code skill，将 Claude 从"答案输出者"转变为"认知过程的共同参与者"。

## 这是什么

**师兄**不是一个角色扮演，而是一套**认知方法论**。它让 Claude 不再直接给你答案，而是展示自己是怎么从"不懂"走到"懂"的——包括走错的路、卡住的点、排除过的假设、以及选择A放弃B的考量。

核心信条：**认知示范 > 答案输出。**

## 安装

将仓库克隆到本地，然后在 Claude Code 中注册 skill：

```bash
git clone <repo-url> ~/Code/skills/senior-brother
```

在 `~/.claude/settings.json` 中添加 skill 配置（具体配置方式取决于 Claude Code 版本）。

或通过 Claude Code 插件系统安装（如果发布到插件市场）。

## 适用场景

师兄在设计上是**广泛激活**的——任何技术对话都适用。尤其擅长：

- **Debug**：不是建议你改哪里，而是带着你从现象一步一步收束到根因
- **源码分析**：带着你从 Makefile 一路追到最底层，建立系统拓扑感
- **架构决策**：追问"为什么选A不选B？B的代价你考虑过吗？"
- **学习新技术**：不是讲知识点，而是展示"我是怎么学的"

不适用：
- 需要快速回答的简单语法问题（师兄会显得啰嗦）
- 非技术领域的对话

## 行为特征

与师兄对话，你会感受到这些特征：

- 回答问题前先建立全局场（"不急，我们先看看整个通路"）
- 涉及3个以上组件时自动画 Mermaid 架构图
- 用 `>` 引用块标注警告和易错点
- 每句话标记认知状态：`[事实]` `[推断]` `[假设]` `[猜测]`
- 默认只输出伪代码和分析，不直接修改你的项目
- 每次收束后做回看总结，沉淀经验

## 文件说明

```
senior-brother/
  SKILL.md                    # 主 skill 文件——身份 + 标志性动作 + 触发规则 + 工具索引
  METHODOLOGY.md              # 完整哲学方法论参考（十点方法论 + 六步流程，独立阅读用）
  README.md                   # 本文件
  examples/
    ext4-debug.md             # EXT4 缺页排查——Debug 场景完整对话示例
    arceos-startup.md         # ArceOS 启动分析——学习/分析场景完整对话示例
  extensions/
    methodology/              # 14 个方法论工具模块（可独立插拔、扩展）
      first-principles.md     # 第一性原理
      abduction.md            # 溯因推理
      phenomenology.md        # 现象学观察
      reductionism.md         # 还原论拆解
      holism.md               # 整体论/整体观
      analogy.md              # 类比锚定
      invariants.md           # 不变量思维
      temporal.md             # 时间性推理
      practice.md             # 实践论
      dialectics.md           # 辩证法反思
      occam.md                # 奥卡姆剃刀
      structuralism.md        # 结构主义
      history.md              # 历史方法
      negation.md             # 否定之否定
    domains/                  # 领域经验模块（可插拔，v1 为空）
```

## 扩展

师兄设计为三层可扩展架构：

- **方法论层** (`extensions/methodology/`)：每个工具一个独立文件，按统一模板编写（触发条件 → 关键问句 → 示例 → 常见误用）。加新工具只需新增文件，不影响主 SKILL.md。
- **领域层** (`extensions/domains/`)：OS 内核、编译器、嵌入式等领域经验，按需加载。
- **例库层** (`examples/`)：完整的对话示例，展示方法论在实际场景中的落地。

详见 `docs/2026-05-23-senior-brother-design.md`。

## 许可

MIT
