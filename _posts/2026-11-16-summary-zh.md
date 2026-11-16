---
layout: default
title: "Horizon Summary: 2026-11-16 (ZH)"
date: 2026-11-16
lang: zh
---

> 从 36 条内容中筛选出 10 条重要资讯。

---

**科技新闻**
1. [Meta FAIR 与 NYU：视觉编码器预训练非必需，视觉专用参数仍关键](#item-tech-news-1) ⭐️ 8.0/10
2. [美团开源 LongCat-2.5，称全程用华为升腾训练](#item-tech-news-2) ⭐️ 8.0/10
3. [Protomaps：自托管地图瓦片更便宜、更简单](#item-tech-news-3) ⭐️ 7.0/10
4. [现代 LLM 位置嵌入的实现解析与理论讨论](#item-tech-news-4) ⭐️ 7.0/10
5. [MacBook Pro 的 OLED PWM 频闪问题](#item-tech-news-5) ⭐️ 7.0/10
6. [开源工具 cmt 宣称在 B300 上将可页迁移 cudaMemcpy 提速约 5 倍](#item-tech-news-6) ⭐️ 7.0/10
7. [华为云 MaaS 上线开源盘古 openPangu-2.1-Pro](#item-tech-news-7) ⭐️ 7.0/10

**财经新闻**
1. [CNBC：Cantor Fitzgerald 减持英伟达持股，卢特尼克面临利益冲突质疑](#item-finance-news-1) ⭐️ 7.0/10
2. [美法官驳回美光、三星、SK 海力士 DRAM 价格操纵案撤诉动议](#item-finance-news-2) ⭐️ 7.0/10
3. [中美俄领导人将在深圳 APEC 场边举行首次三方会晤](#item-finance-news-3) ⭐️ 7.0/10

---

## 科技新闻

<a id="item-tech-news-1"></a>
### [Meta FAIR 与 NYU：视觉编码器预训练非必需，视觉专用参数仍关键](https://www.reddit.com/r/MachineLearning/comments/1xx1k2o/meta_fair_nyu_unbundling_multimodal_vision/) ⭐️ 8.0/10

Meta FAIR 与 NYU 的作者团队在 Reddit 公布一项受控消融研究，称多模态 LLM 的视觉编码器单独预训练是可选的，但仅由视觉 token 使用的专用参数仍然必需。研究从零训练 200 多个模型（包括 LLM），在相同数据和统一计算预算下比较；主实验采用 Qwen3-1.7B 和 4B 骨干、配置 0.4B 视觉容量，规模阶梯覆盖 0.6B 到 6.4B。作者报告，四种预训练目标的编码器在匹配计算下最多只能追平与 LLM 一起从零训练的编码器，把 MetaCLIP 预训练延长 6.5 倍虽将 ImageNet 线性探针从 80.4% 提至 84.4%，却未提升 VQA；无编码器模型在各规模均落后，约需 3 倍计算才能追上，而将视觉专用权重以“in-fusion”注入 LLM 前 8 层，在 1.7B 到 6.4B 与编码器表现相当，并降低约 13% 的首 token 时间。评测覆盖 Cambrian 的 16 个 448px VQA 基准和 12 个语言基准；这些是作者在 Reddit 帖子中自述并附论文链接的结果，尚需独立复现。

reddit · r/MachineLearning · /u/trungh98 · 11月15日 17:38

**「背景：视觉编码器不只是单一组件」** 多模态大模型通常把视觉编码器视为一个完整组件，但它实际上同时包含三项彼此独立的选择：是否单独预训练、是否为视觉 token 保留专用参数，以及是否将编码器置于 LLM 之前。已发布模型在训练数据和算力上差异很大，且很少单独计算编码器预训练的成本，因此仅通过横向比较难以判断哪项选择真正影响 VQA 表现。

**「对 MLLM 架构选型的影响」** 对正在选型的多模态团队来说，这项研究给出的可操作结论是：若直接去掉视觉编码器，在同等算力口径下需要约 3 倍训练算力才能追平；更省算力的替代方案是保留视觉专用参数，例如在 LLM 前 8 层加入零初始化的视觉分支，该方法在 1.7B 至 6.4B 规模上与编码器方案持平，并将首 token 时间降低约 13%。需要注意，这些数字来自 Qwen3-1.7B/4B 主干、448 像素输入和 16 个 VQA 基准的受控实验，迁移到其他分辨率、数据分布或更大模型前仍需自行验证。

**标签**: `#multimodal learning`, `#vision encoders`, `#MLLM architecture`, `#pretraining`, `#model scaling`

---

<a id="item-tech-news-2"></a>
### [美团开源 LongCat-2.5，称全程用华为升腾训练](https://the-decoder.com/meituan-releases-a-1-6-trillion-parameter-agent-model-that-never-touched-an-nvidia-gpu/) ⭐️ 8.0/10

美团 LongCat 团队在模型发布一周后公开了 LongCat-2.5 的权重。该模型面向可自主完成长流程、多步骤任务的智能体，尤其侧重编程，官方称每个 token 激活约 480 亿参数，支持文本、图像和视频输入，并以 MIT 许可证发布、允许商用。官方还称其训练全程使用华为升腾加速卡、未使用英伟达 GPU，并在 Terminal Bench v2.1 上报告 88.4 分，略低于 Claude Opus 5 的 89.1 分；这些训练与基准说法尚待独立验证。

telegram · zaihuapd · 11月15日 11:08

**「背景」** LongCat-2.5 属于稀疏混合专家（MoE）模型：Hugging Face 上的模型卡显示，其总参数为 1.6 万亿，但每个 token 仅激活约 480 亿参数，因此推理开销远低于同等总参数量的稠密模型，这也是该模型能以 MIT 许可开放权重的原因之一。据 promptyze 的报道，上一代 LongCat-2.0 同样是 1.6 万亿参数规模，并宣称端到端在国产芯片上完成训练；因此本次关于训练硬件的说法更像是该系列既定路线的延续，而非首次尝试。需要注意的是，这些关于训练硬件的说法目前来自厂商及其二手报道，尚未获得独立验证。

**「影响」** 对需要商用编码智能体的团队，MIT 许可证允许直接用于商业产品，文本、图像和视频输入也覆盖多模态任务；不过 88.4 的 Terminal Bench v2.1 成绩仅比 Claude Opus 5 低 0.7 分，且缺少独立复现，实际选型仍应自行验证。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://huggingface.co/meituan-longcat/LongCat-2.5">meituan - longcat / LongCat - 2 . 5 · Hugging Face</a></li>
<li><a href="https://promptyze.com/meituans-longcat-2-0-breaks-nvidia/">Meituan ’s LongCat - 2 .0 Breaks the Nvidia Barrier — 1 . 6 T Parameters ...</a></li>

</ul>
</details>

**标签**: `#open-source LLMs`, `#AI agents`, `#Huawei Ascend`, `#AI hardware`, `#coding models`

---

<a id="item-tech-news-3"></a>
### [Protomaps：自托管地图瓦片更便宜、更简单](https://bruceroettgers.eu/blog/protomaps/) ⭐️ 7.0/10

一篇实践文章称，借助 Protomaps 自托管地图瓦片已经变得便宜且容易，面向希望自己掌控地图基础设施、减少对商业底图服务依赖的开发者。所给材料没有提供可核验的成本或性能基准，因此“便宜、简单”目前主要来自作者和社区的使用经验。评论中提到的相关做法包括 OpenFreeMap 以免费公共实例提供地图、有团队把瓦片放在 Cloudflare R2 上以兼顾隐私和访问控制，以及独立开发者用 Protomaps 为步行游戏实时渲染街道地图。

hackernews · bcye · 11月15日 19:26 · [社区讨论](https://news.ycombinator.com/item?id=50509837)

**「背景」** 要理解这类方案，先要区分传统地图瓦片服务与 PMTiles：后者把瓦片打包成单个云原生归档文件，客户端通过 HTTP 范围请求直接读取，不必运行数据库或瓦片服务器。Protomaps 正是围绕这一格式提供自托管地图工具，因此可以只把文件放到对象存储或静态主机上提供瓦片。

**「影响」** 对个人项目和小团队来说，最直接的后果是底图可以作为静态文件放在对象存储或普通 Web 服务器上，避免按地图请求量向商业服务付费；但高分辨率卫星影像的存储成本会随缩放级别快速上升，有评论者称为离线访问做到 z17 就已受存储预期限制。

**「社区讨论」** 评论者把自托管底图与隐私、访问控制和降低公共基础设施负载联系起来，并分享了 OpenFreeMap、Cloudflare R2 等不同部署方式。也有实践者提醒，普通底图瓦片体积可控，但高分辨率卫星影像在高缩放级别会迅速膨胀到数百 TB，未必适合“放对象存储再用 Worker 提供”的模式。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://protomaps.com/">Protomaps - The open source map in a file</a></li>
<li><a href="https://awesome-repositories.com/repository/protomaps-pmtiles">PMTiles - serve map tiles from cloud storage | Awesome Repos</a></li>

</ul>
</details>

**标签**: `#protomaps`, `#self-hosting`, `#map-tiles`, `#open-source`, `#pmtiles`

---

<a id="item-tech-news-4"></a>
### [现代 LLM 位置嵌入的实现解析与理论讨论](https://magazine.sebastianraschka.com/p/understanding-positional-embeddings) ⭐️ 7.0/10

一篇技术解析文章面向希望理解现代大语言模型中位置嵌入实现方式的读者，梳理了该机制在 Transformer 架构中的实现细节。随附的 Hacker News 讨论把话题从实现延伸到群论基础，认为位置嵌入可以被理解为群表示。由于原始文章内容未提供，具体模型、版本和实验数据无法在此核实。

hackernews · vismit2000 · 11月15日 12:14 · [社区讨论](https://news.ycombinator.com/item?id=50506376)

**「背景」** Transformer 的自注意力机制本身不包含词序信息，模型必须通过位置编码显式注入顺序。据相关技术资料，早期机器翻译等模型常用绝对正弦位置编码，而目前多数开源大模型转向相对方案：RoPE 通过对 query 和 key 施加旋转矩阵来表达相对位置，且不引入与位置相关的可学习参数；ALiBi 则直接在注意力分数上叠加线性偏置。了解“绝对与相对”“可学习与无参数”这两组区分，是理解本文所讲实现细节的前提。

**「影响」** 对正在实现或调参位置嵌入的开发者来说，这篇文章可作为实现层面的参考；但如果目标是自行设计或参数化位置嵌入，评论指出还需要补充群表示论等理论知识。

**「社区讨论」** 评论者 programjames 认为文章只覆盖了位置嵌入的实现，真正理解它需要群表示论，并举例说旋转位置嵌入是平移群的表示。这一观点把讨论引向如何用群表示来发现和参数化可学习的位置嵌入。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://blackseedusa.com/rope-vs-alibi-how-modern-positional-encodings-power-long-context-llms">RoPE vs ALiBi : How Modern Positional Encodings Power...</a></li>
<li><a href="https://arxiv.org/html/2408.11382v1">On the Interchangeability of Positional Embeddings in Multilingual...</a></li>
<li><a href="https://arxiv.org/pdf/2512.07805v1">Group Representational Position Encoding - arXiv.org</a></li>
<li><a href="https://apxml.com/courses/how-to-build-a-large-language-model/chapter-13-positional-encoding-variations/rotary-position-embedding-rope">Rotary Position Embedding (RoPE) Explained - apxml.com</a></li>

</ul>
</details>

**标签**: `#positional embeddings`, `#large language models`, `#transformer architecture`, `#deep learning`, `#technical explainer`

---

<a id="item-tech-news-5"></a>
### [MacBook Pro 的 OLED PWM 频闪问题](https://macanorak.com/the-macbook-pros-oled-pwm-problem-when-a-better-display-becomes-worse-to-use/) ⭐️ 7.0/10

一篇分析文章聚焦 MacBook Pro 的 OLED 屏幕 PWM 调光，认为这项让显示规格更好的技术，可能反而让对闪烁敏感的用户更难使用。文章讨论的核心是亮度调节与频闪之间的取舍，而不是分辨率或色彩等传统指标。评论区对文章中 240 Hz 的测量结论提出异议：有读者推测，串联 OLED 的两层以 480 Hz、180 度反相工作，实际可形成 960 Hz 的有效频率；这些说法属于读者推断，尚未获得独立确认。

hackernews · MacAnorak · 11月15日 13:15 · [社区讨论](https://news.ycombinator.com/item?id=50506719)

**「背景」** PWM 调光通过快速开关像素来调节亮度，频率越低，部分对闪烁敏感的人越容易感到不适。MacBook Pro 自 2021 年起使用 Mini-LED，这一代转向被 Apple 称为“PROLED XDR”的串联 OLED；Notebookcheck 的评测指出其 PWM 频率为 240 Hz，即便有 DC 调光，敏感用户仍可能受影响。

**「对敏感用户的影响」** 对 PWM 敏感的用户来说，这块屏幕可能在长时间工作时引发头痛、疲劳或不适，即使它的显示规格更好。研究显示 PWM 敏感性个体差异很大，且多数人在常见商用频率下察觉不到闪烁，因此受影响者很难仅凭参数判断，实际选购时应以较长时间的实机试用为准。

**「社区讨论」** 有评论者希望把闪烁敏感性的讨论扩展到 PWM 之外，指出白光 LED 的显色指数和 LCD 的运动模糊也会影响部分用户；另一位有脑震荡经历的读者则表示，自己的不适并不限于高亮 OLED 屏幕，而是所有屏幕都可能触发。这些属于个人经验和主观观察，不能视为普遍的医学结论。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://macanorak.com/the-macbook-pros-oled-pwm-problem-when-a-better-display-becomes-worse-to-use/">The MacBook Pro ’s OLED PWM Problem: When a ‘Better’ Display...</a></li>
<li><a href="https://www.notebookcheck.net/Amazing-OLED-panel-Apple-MacBook-Pro-14-PROLED-XDR-Review.1438048.0.html">Amazing OLED panel - Apple MacBook Pro ... - Notebookcheck Review</a></li>
<li><a href="https://ieeexplore.ieee.org/document/10600511">Study of the Presence of Pulse Width Modulated Flicker of the ...</a></li>
<li><a href="https://screenlab.nl/blog/pwm-sensitivity-test/">PWM Sensitivity: Why Some People Get Headaches from Monitors</a></li>

</ul>
</details>

**标签**: `#OLED displays`, `#PWM flicker`, `#MacBook Pro`, `#hardware usability`, `#display health`

---

<a id="item-tech-news-6"></a>
### [开源工具 cmt 宣称在 B300 上将可页迁移 cudaMemcpy 提速约 5 倍](https://www.reddit.com/r/MachineLearning/comments/1xx2n25/making_cudamemcpy_5x_faster_on_a_b300_p/) ⭐️ 7.0/10

开发者 makneeee 发布了开源工具 cudamemcpy-tuner（命令行 \`cmt\`），用于加速 CUDA 中 pageable（非锁页）内存的 cudaMemcpy 传输。在其自测中，用 PyTorch 在 B300 上把 1 GiB uint8 张量从 CPU 拷到 GPU、循环 5 次计时，直接运行得到 10.2 GB/s，而在前面加上 \`cmt tune --\` 运行同一脚本则得到 51.5 GB/s。该结果由作者自行报告，仅覆盖单一硬件、单一大小的 CPU→GPU 方向（尽管帖子标题提到“拷入并拷回”），尚未经过独立复现或跨设备验证。代码与博客均已公开。

reddit · r/MachineLearning · /u/makneeee · 11月15日 18:20

**「背景」** CUDA 的 cudaMemcpy 在主机内存为可分页（pageable）时，通常要经驱动管理的页锁定暂存区中转，GPU 不能像访问页锁定（pinned）内存那样直接对其做异步 DMA；因此 pageable 的 CPU 与 GPU 间拷贝往往明显慢于 pinned 路径。这个工具针对的正是这条常被忽略的慢路径。

**「实际影响」** 如果这一加速在更多环境下成立，那么依赖 pageable 内存做大块主机到设备拷贝的推理、数据加载和预处理流程，可以减少与 pinned memory 之间的带宽差距，而且只需在启动命令前加 \`cmt tune --\`，不必改代码。不过，在采用之前，应先在自己的 GPU、传输尺寸和方向上复测；该工具目前只有 B300 单点数据，GPU→CPU 方向、小尺寸传输及其他架构均无公开结果。

**标签**: `#CUDA`, `#GPU memory transfers`, `#performance optimization`, `#machine learning systems`, `#open source tools`

---

<a id="item-tech-news-7"></a>
### [华为云 MaaS 上线开源盘古 openPangu-2.1-Pro](https://mp.weixin.qq.com/s/8JfFmscBTDl_mPQMycD8Nw) ⭐️ 7.0/10

11 月 15 日，华为云在其 MaaS 模型即服务平台上线开源盘古模型 openPangu-2.1-Pro，围绕 Agent 开发、AI 编码和推理优化升级能力。该模型基于 10 万余条专项数据优化 Skills 触发与工具调用，适配鸿蒙 ArkTS 开发和升腾算子生成，并接入智果 AgentArts、码道 CodeArts、果办 OfficeAce。定价为输入 0.8 元/百万 tokens、输出 3.2 元/百万 tokens、缓存命中输入 0.016 元/百万 tokens；来源未披露模型规模、许可证和基准结果。

telegram · zaihuapd · 11月15日 16:03

**「背景」** 华为云此前于 11 月 1 日公告，MaaS 模型即服务平台将在 11 月 6 日停止销售 openPangu-2.0-Flash 和 openPangu-2.0-Pro 两款模型服务，并称 openPangu 系列新版本已在规划中，将逐步上线。据媒体报道，openPangu-2.1-Pro 在本次 MaaS 上线前已率先接入华为小艺 Work，主打“鸿蒙任务增强”，当时官方尚未公开参数量、激活量、上下文与训练数据等规格。作为参照，前代 openPangu-2.0-Flash 是基于升腾 NPU 训练的大规模混合专家（MoE）语言模型，参数规模约 92B，每 token 激活参数约 6B，支持 512k 上下文长度，训练数据总量约 34T。

**「影响」** 使用华为云 MaaS 的开发者现已可按 token 计费调用该模型，缓存命中输入的单价为普通输入的 1/50，适合有重复上下文或工具调用场景的 Agent 应用；但计划自托管或进行选型对比的团队，仍需等待许可证、模型规模和基准数据公布。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.163.com/dy/article/LAUGH8N10511B8LM.html">华 为 小艺Work率先上线 openPangu - 2 . 1 - Pro 模 型 ，主打“鸿蒙任务增强”</a></li>
<li><a href="https://huggingface.co/lovedheart/openPangu-2.0-Flash-FP8">lovedheart/ openPangu - 2 .0-Flash-FP8 · Hugging Face</a></li>
<li><a href="https://www.d1ev.com/newsflash/315764">华 为 openPangu 两款 模 型 将停售 2 . 1 - Pro 已抢先上线小艺Work...</a></li>

</ul>
</details>

**标签**: `#Huawei Pangu`, `#open-source LLM`, `#AI agents`, `#AI coding`, `#Huawei Cloud MaaS`

---

## 财经新闻

<a id="item-finance-news-1"></a>
### [CNBC：Cantor Fitzgerald 减持英伟达持股，卢特尼克面临利益冲突质疑](https://www.cnbc.com/2026/11/13/howard-lutnick-nvidia-jensen-huang-china-cantor-fitzgerald.html) ⭐️ 7.0/10

CNBC 报道称，在英伟达 CEO 黄仁勋周四辞职、美国商务部长霍华德·卢特尼克因疑似英伟达芯片走私至中国的审查承压之际，卢特尼克之子执掌的 Cantor Fitzgerald 在 2025 年 9 月至 2026 年 3 月间将其申报的英伟达持股数量削减近 50%。报道援引证券申报文件称，这批申报持仓的市值同期从 6.52 亿美元降至 3.10 亿美元，并称相关关系引发利益冲突质疑；Cantor 表示其英伟达自营头寸“微不足道”，申报持仓与客户互换交易有关。

rss · CNBC Finance · 11月15日 19:58

**「背景」** 美国商务部长霍华德·卢特尼克即将就商务部对人工智能芯片出口管制的处理接受参议院质询；此案核心是新加坡公司 Megaspeed 涉嫌违反美国出口管制、将英伟达先进芯片转往中国，而英伟达已被禁止向中国出售此类芯片。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://nypost.com/2026/11/13/business/howard-lutnick-to-testify-before-senate-on-nvidia-megaspeed-fiasco/">Howard Lutnick to testify before Senate on Nvidia , Megaspeed fiasco</a></li>
<li><a href="https://www.cnbc.com/2026/11/15/bessent-nvidia-ceo-lutnick-megaspeed.html">Bessent calls for ‘dramatic shakeup’ at Nvidia , urges outside CEO</a></li>
<li><a href="https://www.bbc.com/news/articles/cmdx1vpprk9vo">Suspected China spy linked to Nvidia &#x27;s ex-boss left in 2025...</a></li>

</ul>
</details>

**标签**: `#Nvidia`, `#export controls`, `#conflict of interest`, `#Commerce Department`, `#China`

---

<a id="item-finance-news-2"></a>
### [美法官驳回美光、三星、SK 海力士 DRAM 价格操纵案撤诉动议](https://www.tomshardware.com/tech-industry/big-tech/judge-denies-motion-to-dismiss-dram-price-fixing-lawsuit-against-micron-samsung-and-sk-hynix-says-chipmakers-acted-like-hawks-flying-in-formation-finds-evidence-of-dram-collusion-plausible-after-500-percent-price-surge) ⭐️ 7.0/10

美国联邦法官 Noël Wise 驳回美光、三星、SK 海力士要求撤销 DRAM 价格操纵集体诉讼的动议，认定 17 名个人及小企业原告提交的证据足以让三家厂商同步限制供应、价格最高上涨 500% 的合谋指控成立为「合理」，因此案件继续审理。三家公司须在 12 月 7 日前回应，案件管理会议定于 2027 年 1 月。

telegram · zaihuapd · 11月15日 16:39

**「背景」** 撤诉动议是被告在开庭审理前请求法院直接驳回诉讼的程序性步骤。此次裁定只说明法院认为原告的共谋指控足够可信、案件可以继续，并不等于已认定三家公司违法。

**「影响」** 案件继续推进意味着三家厂商须在 12 月 7 日前应诉、随后进入取证和审理，而这一高度集中的市场格局——2026 年第二季度三星占 DRAM 市场 39%、SK 海力士 26%、美光 25%——意味着其供应与定价行为直接关系到采购内存的电脑、手机等设备制造商。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.techpowerup.com/354863/samsung-sk-hynix-and-micron-fail-to-get-dram-antitrust-suit-dismissed">Samsung , SK hynix , and Micron Fail to Get DRAM Antitrust Suit ...</a></li>
<li><a href="https://litnews.ai/articles/garciaguirre-samsung-sk-hynix-micron-dram-conspiracy-suit-survives-dismissal">Judge Refuses to Dismiss DRAM Supply Conspiracy Suit Against...</a></li>
<li><a href="https://english.hani.co.kr/arti/english_edition/e_business/1271541.html">Samsung defends No. 1 spot in DRAM market as Micron narrows...</a></li>

</ul>
</details>

**标签**: `#antitrust litigation`, `#DRAM`, `#semiconductor supply`, `#price fixing`, `#memory chips`

---

<a id="item-finance-news-3"></a>
### [中美俄领导人将在深圳 APEC 场边举行首次三方会晤](https://apnews.com/article/trump-xi-putin-summit-china-5fe92253ef38100bae913834a9b74d72) ⭐️ 7.0/10

中国外交部发言人宣布，中美俄三国领导人计划于 11 月 19 日在深圳 APEC 峰会期间举行三方会晤，会晤在 APEC 场边举行，不属于 APEC 正式议程。媒体称这将是三国领导人首次专门举行三方会晤。

telegram · zaihuapd · 11月16日 01:38

**「背景」** 2026 年 APEC 领导人会议定于 11 月 18 日至 19 日在深圳举行，这是中国第三次主办、也是时隔 12 年再次主办，因此这场三方会晤被安排在 APEC 正式议程之外。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://english.www.gov.cn/news/202609/10/content_WS6aa2b5d7c6d00ca5f9a0d1fa.html">APEC CEO Summit 2026 to be held in Shenzhen from Nov. 17 to 18</a></li>

</ul>
</details>

**标签**: `#geopolitics`, `#US-China-Russia`, `#APEC`, `#diplomacy`, `#market-risk`

---