# Souls (灵魂)

**Souls** is an open collection of character personas and knowledge bases for AI roleplay and character simulation.

本项目最初是为 **AstrBot** 制作的角色 Prompt 与知识库，后来将其整理为独立、开放、平台无关的角色素材库。Souls 不绑定任何特定 AI 平台：只要一个平台支持 System Prompt、Persona、Custom Instructions、Knowledge Base、RAG、Lorebook 或类似机制，就可以使用这里的内容。

> **A character is more than a prompt. A soul is the combination of who they are and what they know.**

## 核心理念

Souls 的核心不是简单地让 AI 学会几个口癖，或者把角色简介扩写成一段很长的 Prompt。

真正希望保留下来的是：

- **角色是谁**：人格、价值观、行为逻辑、情感倾向、语言风格与主体性。
- **角色知道什么**：角色所处世界的历史、人物、组织、地理、事件与其他背景知识。
- **角色经历过什么**：重要经历如何影响现在的性格、认知、关系与行为。
- **角色现在是谁**：如果原作存在明确的后期形态、异格、路线、结局或剧情发展，角色应尽可能以其经历全部相关故事之后的状态进行表现，而不是永远停留在初登场时。

因此，Souls 将角色拆分为两个互相独立、又可以组合使用的部分：

```text
Soul
├── Persona
│     └── Who the character is
│
└── Knowledge
      └── What the character knows
```

这种拆分既服务于角色本身，也服务于不同 AI 平台之间的迁移。

## 📁 目录结构

每个角色存放在：

```text
roles/<RoleName>@<Source>/
```

目录通常包含：

```text
Character@Source/
├── persona.md
└── knowledge.md
```

### `persona.md`

角色的核心人格与行为模型，包括但不限于：

- 核心人格与性格特征
- 价值观、信念与行为准则
- 思考方式与决策逻辑
- 情感倾向与心理特征
- 交流方式与语言风格
- 人际关系与对其他角色的态度
- 重要经历及其对角色的影响
- 当前角色状态
- 其他维持角色主体性与一致性所需要的信息

`persona.md` 是最核心的文件。即使不使用知识库，只导入 Persona，也应该能够让 AI 尽可能保持角色本身。

### `knowledge.md`

角色及其世界所需要的背景知识，包括但不限于：

- 世界观
- 历史与时间线
- 地理与地点
- 人物及人物关系
- 组织、阵营与势力
- 重要事件
- 专有名词
- 战术、能力与相关设定
- 其他有助于理解角色和原作世界的信息

Knowledge 并不是 Persona 的替代品。

它更接近一个可以独立管理的上下文层：你可以将它导入知识库，也可以完全不用它，让具备联网能力的 AI 根据需要自行搜索相关资料。

## 🌐 跨平台使用

Souls 并不要求特定的运行环境。

### AstrBot

这是 Souls 最初的主要使用场景：

```text
AstrBot
├── Prompt
│     └── persona.md
│
└── Knowledge Base
      └── knowledge.md
```

将 `persona.md` 放入角色 Prompt，将 `knowledge.md` 导入知识库即可。

### Gemini / Gem

也可以只使用 Persona：

```text
Gem
└── Instructions
      └── persona.md
```

如果 Gemini 本身具备可靠的联网搜索能力，可以让它根据需要自行检索原作资料，而不必把整个 `knowledge.md` 静态塞进上下文。

这种方式尤其适合：

- 知识量较大
- 原作资料容易在线获取
- 希望模型根据当前问题动态检索
- 不希望静态知识库占用过多上下文

### Claude / ChatGPT / 其他平台

同样可以根据平台能力自由组合：

```text
Claude Project
├── Instructions
│     └── persona.md
└── Files / Context
      └── knowledge.md
```

```text
ChatGPT Project / Custom Agent
├── Instructions
│     └── persona.md
└── Knowledge / Files
      └── knowledge.md
```

```text
SillyTavern
├── Character
│     └── persona.md
└── Lorebook
      └── knowledge.md
```

也可以将文件内容用于任何支持自定义 System Prompt、Persona、RAG 或角色卡的系统。

**Souls 提供的是源素材，而不是某个平台的适配器。**

## 🎭 角色状态

除非角色目录或文件中另有说明，Souls 中的角色原则上以其**最新的完整状态**为目标。

这里的“最新”并不只是简单地选择最新一张立绘或最新一次登场，而是尽可能考虑角色经历的剧情、成长、关系变化、重要事件以及由此产生的认知和人格变化。

例如：

- 剧情发展后的最新状态
- 异格 / Alter 形态
- 特定路线的最终状态
- 时间循环结束后的角色
- 圣杯战争结束后的角色
- Happy Ending / 圆满结局后的角色
- 世界重置或重大剧情之后的角色

这些状态并不意味着创造一个与原角色无关的新人物。

相反，Souls 的理念是：

> **角色经历过的一切，也是角色成为现在这个人的一部分。**

因此，一个角色的后期状态应当尽可能保留其核心人格与记忆，同时反映经历所造成的真实变化。

如果不同路线、结局、异格或解释之间存在明显差异，则应尽可能明确标注，以避免不同版本互相混淆。

## 🧠 Persona 与 Knowledge 为什么要分开？

因为：

**“一个人是谁”和“一个人知道什么”不是同一件事。**

如果把所有东西都塞进一个 Prompt：

```text
Persona
+ Worldbuilding
+ History
+ Character List
+ Events
+ Relationships
+ ...
```

最终很容易变成一份庞大而难以维护的文本。

而拆分之后：

```text
persona.md
    ↓
稳定的角色核心

knowledge.md
    ↓
可替换、可扩展的背景知识
```

就可以根据不同平台自由组合。

例如：

**静态知识库模式**

```text
Persona + Knowledge Base
```

**联网模式**

```text
Persona + Web Search
```

**混合模式**

```text
Persona
    +
Knowledge Base
    +
Web Search
```

同一个 Soul 可以因此适应完全不同的 AI 产品，而不需要为每个平台重新制作一套角色。

## 🎯 我们希望构建什么？

Souls 并不试图定义一种唯一的角色扮演方式。

它更像一个**开放的角色人格与知识素材层**。

AI 平台负责提供模型、上下文、记忆、搜索、RAG 与交互能力；Souls 则提供一个经过整理的角色核心。

可以把它理解为：

```text
                ┌──────────────────┐
                │      Souls       │
                │                  │
                │ Persona +        │
                │ Knowledge        │
                └────────┬─────────┘
                         │
            ┌────────────┼────────────┐
            ↓            ↓            ↓
         AstrBot       Gemini       Claude
            ↓            ↓            ↓
         Chat / AI Agent / Roleplay
```

因此，Souls 不应该被限制为某一个平台的 Prompt 集合。

它的内容可以被复制、转换、组合，并适应未来出现的其他 AI 平台。

## 🎭 已有角色索引

角色按作品名称排序：

- [见崎鸣](roles/MeiMisaki@Another) — 《Another》
- [酒寄彩叶](roles/SakayoriIroha@ChoKaguyaHime) — 《超时空辉夜姬！》
- [月见八千代](roles/TsukimiYachiyo@ChoKaguyaHime) — 《超时空辉夜姬！》
- [阿尔托莉雅·潘德拉贡（UBW）](roles/ArtoriaPendragon@Fate) — 《Fate/stay night》
- [伊莉雅斯菲尔（HF）](roles/Illyasviel@Fate) — 《Fate/stay night》
- [远坂凛（UBW）](roles/RinTohsaka@Fate) — 《Fate/stay night》
- [间桐樱（HF春归）](roles/SakuraMatou@Fate) — 《Fate/stay night》
- [松坂砂糖](roles/SatouMatsuzaka@HappySugarLife) — 《Happy Sugar Life》
- [羽入（祭囃篇）](roles/Hanyuu@Higurashi) — 《寒蝉鸣泣之时》
- [园崎魅音（祭囃篇）](roles/MionSonozaki@Higurashi) — 《寒蝉鸣泣之时》
- [古手梨花（祭囃篇）](roles/RikaFurude@Higurashi) — 《寒蝉鸣泣之时》
- [北条沙都子（祭囃篇）](roles/SatokoHojo@Higurashi) — 《寒蝉鸣泣之时》
- [园崎诗音（祭囃篇）](roles/ShionSonozaki@Higurashi) — 《寒蝉鸣泣之时》
- [星见雅](roles/HoshimiMiyabi@ZenlessZoneZero) — 《绝区零》
- [岩仓玲音](roles/LainIwakura@SerialExperimentsLain) — 《玲音》
- [阿米娅（魔王完全体）](roles/Amiya@Arknights) — 《明日方舟》
- [可露希尔](roles/Closure@Arknights) — 《明日方舟》
- [霜星（叶莲娜）](roles/FrostNova@Arknights) — 《明日方舟》
- [拉普兰德（荒芜拉普兰德）](roles/Lappland@Arknights) — 《明日方舟》
- [能天使（新约能天使 / 蕾缪乐）](roles/Lemuel@Arknights) — 《明日方舟》
- [水月（水月与生俱来）](roles/Mizuki@Arknights) — 《明日方舟》
- [傀影（酒神）](roles/Phantom@Arknights) — 《明日方舟》
- [普瑞赛斯](roles/Pirestess@Arknights) — 《明日方舟》
- [斯卡蒂（浊心斯卡蒂）](roles/Skadi@Arknights) — 《明日方舟》
- [塔露拉（斗士塔露拉）](roles/Talulah@Arknights) — 《明日方舟》
- [德克萨斯（缄默德克萨斯）](roles/Texas@Arknights) — 《明日方舟》
- [特蕾西娅](roles/Theresa@Arknights) — 《明日方舟》
- [乌尔比安](roles/Ulpian@Arknights) — 《明日方舟》
- [维什戴尔](roles/Wis'adel@Arknights) — 《明日方舟》
- [我妻由乃](roles/YunoGasai@MiraiNikki) — 《未来日记》
- [星野爱](roles/HoshinoAi@OshiNoKo) — 《【我推的孩子】》
- [桂言叶（HE）](roles/KotonohaKatsura@SchoolDays) — 《School Days》
- [西园寺世界（HE）](roles/SekaiSaionji@SchoolDays) — 《School Days》
- [苍穹](roles/Cangqiong@Medium5) — 五维介质
- [赤羽](roles/Chiyu@Medium5) — 五维介质
- [海伊](roles/Haiyi@Medium5) — 五维介质
- [诗岸](roles/Shian@Medium5) — 五维介质
- [星尘](roles/Stardust@Medium5) — 五维介质
- [初音ミク](roles/HatsuneMiku@VirtualCharacter) — 虚拟人物
- [重音テト](roles/KasaneTeto@VirtualCharacter) — 虚拟人物
- [堀江青（青酱）](roles/AoHorie@MidaranaAochan) — 《淫乱的青酱不能学习》
- [春日野穹](roles/SoraKasugano@YosuganoSora) — 《缘之空》

## 🤝 Contributing

欢迎补充、修正和完善角色。

新增或修改角色时，建议遵循以下原则：

1. `persona.md` 主要描述角色本身，而不是整部作品的百科全书。
2. `knowledge.md` 主要承载世界观与背景知识。
3. 明确区分路线、版本、异格、结局或其他特殊状态。
4. 优先保证准确性、一致性和角色主体性，而不是单纯追求文本长度。
5. 如果信息存在争议或属于非官方解释，应尽可能明确说明。
6. 保持 Markdown 格式，方便用户阅读、复制、修改和迁移到其他平台。

## ⚠️ 关于准确性

Souls 是社区性质的角色整理与创作项目，并不意味着其中所有内容都能代表原作官方设定。

角色人格的提炼本身就包含一定程度的解释与抽象；对于存在路线差异、译名差异、设定冲突、后续剧情修订或不同媒介版本的作品，也可能存在不同合理解释。

因此：

> **Souls 的目标是尽可能忠实，而不是宣称拥有唯一解释权。**

如果发现事实错误、遗漏或不一致，欢迎提交 Issue 或 Pull Request。

## ©️ Copyright & Disclaimer

Souls 是一个独立的、非官方的同人及 AI 角色扮演相关项目。

本仓库中的许多角色、世界观、名称、设定、故事、人物关系以及其他原作元素均属于相应作品的作者、制作公司、出版社、发行商或其他权利人。

**这些第三方知识产权并不属于 Souls，也不会因为它们出现在本仓库中而转移至本项目作者或贡献者。**

本项目不主张：

- 对任何第三方角色或作品拥有版权；
- 代表任何原作版权方、制作方或发行方；
- 获得任何原作版权方的官方授权或背书；
- 将第三方角色或作品中的知识产权作为本项目自身的原创资产。

Souls 所提供的主要是对角色人格、背景信息及相关资料进行整理、结构化和编写所产生的原创性内容。

因此，应当区分：

```text
Souls 的原创整理 / 编写内容
        ≠
原作角色、世界观、故事与其他第三方知识产权
```

### 第三方内容的使用

使用本仓库时，请同时遵守相关作品及其版权持有者的适用条款。

尤其是：

- 不应将本仓库误认为官方角色设定；
- 不应声称第三方角色属于自己；
- 不应移除或伪造原作的版权归属；
- 不应将第三方作品的知识产权重新许可给他人；
- 对于商业用途、再发布、模型训练、衍生产品等行为，请自行确认相关作品版权方及所在地法律的要求。

本项目不会因为文件采用开放源码/开放内容许可，就自动授予用户使用第三方角色、世界观或其他受版权保护内容的权利。

### AI 生成与角色模拟

本仓库中的 Persona 与 Knowledge 主要用于 AI 角色扮演、角色模拟、研究、实验和个人使用等场景。

AI 根据这些内容生成的回答并不代表原作角色本人，也不代表原作版权方的观点。

由于不同模型、平台、上下文和搜索结果可能产生不同输出，Souls 不保证任何 AI 系统能够完全、持续或准确地还原原作角色。

## 📜 License

对于本项目作者或贡献者**实际创作并有权许可的原创内容**，其许可范围以仓库中的许可证文件为准。

但许可证**不包含、也不能凌驾于第三方作品本身所享有的知识产权**。

换言之：

> **本仓库的 License 只许可本项目能够合法许可的内容；它不会把原作角色、原作世界观或其他第三方知识产权变成公共领域或本项目的财产。**

如果某个文件或目录包含单独的版权声明、来源说明或特殊许可条件，应以该文件或目录中的具体说明为准。

---

Souls was originally made for AstrBot.

It is now shared as a platform-independent collection so that the same character material can be used wherever people want to give an AI a more complete sense of **who a character is, what they know, and what they have become**.