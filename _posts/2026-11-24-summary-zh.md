---
layout: default
title: "Horizon Summary: 2026-11-24 (ZH)"
date: 2026-11-24
lang: zh
---

> 从 38 条内容中筛选出 12 条重要资讯。

---

**科技新闻**
1. [Ladybird 首个 alpha 发布，macOS/Linux 可直接安装](#item-tech-news-1) ⭐️ 8.0/10
2. [GLM-5.4 发布：Z.ai 首个循环 Transformer 编程模型](#item-tech-news-2) ⭐️ 8.0/10
3. [Anthropic 称 Claude 发现 VP≠VNP 并公布 Lean 4 证明](#item-tech-news-3) ⭐️ 8.0/10
4. [NariQ 发布 Qwen3.8-27B 低比特 GGUF 量化](#item-tech-news-4) ⭐️ 7.0/10
5. [Codex2api 疑遭供应链投毒，v3.1.11 被指移除鉴权](#item-tech-news-5) ⭐️ 7.0/10
6. [Meta AI 负责人称超级智能将至，警告控制风险](#item-tech-news-6) ⭐️ 7.0/10
7. [黎曼猜想 AI 证明被指空转，作者承认代码满是垃圾](#item-tech-news-7) ⭐️ 7.0/10
8. [4.5 万家企业组织联名致信欧盟，要求对苹果 iPhone 浏览器限制立案](#item-tech-news-8) ⭐️ 7.0/10
9. [黄循财：新加坡不会成规避芯片管制通道](#item-tech-news-9) ⭐️ 7.0/10

**科技博客**
1. [vLLM 插件实现 ERNIE 5.5 Flash 首日支持](#item-tech-blog-1) ⭐️ 7.0/10

**财经新闻**
1. [纽约联储主席威廉姆斯：通胀仍过高，进一步加息可随时间推进](#item-finance-news-1) ⭐️ 7.0/10
2. [上海地铁 12 月 1 日起调整票价，为 21 年来首次](#item-finance-news-2) ⭐️ 7.0/10

---

## 科技新闻

<a id="item-tech-news-1"></a>
### [Ladybird 首个 alpha 发布，macOS/Linux 可直接安装](https://ladybird.org/posts/alpha/) ⭐️ 8.0/10

Ladybird 发布了首个 alpha 版本，macOS 和 Linux 用户现在可以直接下载安装，不必自行编译。这个从零实现的浏览器包含自己的 HTML 解析、CSS 引擎、布局、JavaScript 和 WebAssembly 实现，仅外部依赖 HarfBuzz、Skia、ffmpeg 和 SQLite 等少数组件，并按标签页分进程运行。实际测试中，多数网站、ffmpeg/WASM 视频压缩工具和 Pyodide REPL 可正常工作，但 Datasette Lite 因缺少 navigator.serviceWorker.startMessages 而报错；官方同时警告 alpha 仍会崩溃和遇到不兼容网站，并邀请用户从浏览器内报告问题。据项目 10 月通讯，Ladybird 当月新增 75,650 项 web-platform-tests 子测试通过，约 218 万项，超过 Safari 但仍低于 Firefox；这些改进大量由 AI 编程代理完成。

hackernews · janvdberg · 11月23日 16:13 · [社区讨论](https://news.ycombinator.com/item?id=50614249)

**「背景」** Ladybird 的浏览器引擎大部分自行实现，包括 HTML 解析、CSS、布局、JavaScript 和 WebAssembly，仅复用 HarfBuzz、Skia、ffmpeg、SQLite 等外部组件，部分代码则继承自更早的 SerenityOS 项目。2026 年 2 月，项目将 LibJS 的部分实现从 C++ 移植为约 2.5 万行 Rust；到 10 月，团队借助 AI 编程代理集中补齐 Web 平台功能，单月新增 75,650 项 web-platform-tests 通过项。

**「影响」** 对准备试用的用户，这个 alpha 更适合兼容性测试而不是日常主力：依赖 service worker 等未实现 API 的网页应用会直接失败，崩溃报告也要由用户自行决定是否发送。遇到坏站时，用户可以从浏览器内提交报告，把具体兼容性问题反馈给项目。

**「社区讨论」** 多位评论者报告自己常去的网站以及 Proxmox/NoVNC 等复杂页面能正确渲染，有人称 NoVNC 在 Ladybird 中比 Firefox 更流畅，但也有人指出页面滚动略显卡顿。评论还提到 Ladybird 采用 SQLite、Skia 等生产级依赖，有人怀念 SerenityOS 时期自研库的黑客精神，也有人希望项目后续认真处理浏览器指纹问题。

**标签**: `#browsers`, `#open source`, `#Ladybird`, `#browser engine`, `#alpha release`

---

<a id="item-tech-news-2"></a>
### [GLM-5.4 发布：Z.ai 首个循环 Transformer 编程模型](https://z.ai/blog/glm-5.4) ⭐️ 8.0/10

Z.ai 发布 GLM-5.4，称这是其首个采用循环 Transformer 架构的模型：一组共享权重的层在一次前向传播中多次运行，反复细化隐藏状态，从而在不增加参数量的情况下加深网络。GLM-5.4 目前尚未提供开放权重，也不能通过常规 API 套餐调用，只能通过 Z.ai 的 Coding Plan 订阅访问；该订阅的 API key 可用于其 OpenAI 兼容的 Responses API（https://api.z.ai/api/v1）。Simon Willison 的初步测试显示，GLM-5.4 在低、高、最高三档生成的 pelican SVG 与 GLM-5.3 质量相近，且风格更接近 OpenAI 和 Anthropic 模型，而非 5.1/5.2 的独特画风。

hackernews · foohis · 11月23日 10:06 · [社区讨论](https://news.ycombinator.com/item?id=50609685)

**「背景」** 循环 Transformer 让一组共享权重的层在一次前向传播中重复运行多次，从而在不增加参数量的情况下加深有效网络；GLM-5.4 是 Z.ai 首个采用这一架构的模型。就在几天前，Thinking Machines Lab 发布了同样采用循环架构的 Inkling 2 Mini，其模型对每个 token 将中间层运行三次，官方称这能用更少 token 完成推理，尤其在依赖推理质量的智能体编程任务上。

**「影响」** 对开发者而言，现阶段接入需要先订阅 Coding Plan，并确认工具链支持新模型：现有 llm-zai 插件尚未支持 GLM-5.4，Willison 因此临时发布了 llm-glm，并计划在 llm-zai 跟上后停用自己的插件。

**「社区讨论」** 评论者一方面赞赏智谱公开架构细节，并解释循环 Transformer 通过复用层权重减少 HBM 与芯片之间的权重搬运，从而缓解推理的内存带宽瓶颈；另一方面，有人抱怨部分中国模型在简单任务上也会长时间“马拉松式思考”，显著拉长完成时间，并认为 GLM-5.4 的输出与 GLM-5.3 颇为相似。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://thinkingmachines.ai/news/inkling-2-mini/">Introducing Inkling 2 Mini - Thinking Machines Lab</a></li>
<li><a href="https://openrouter.ai/thinkingmachines/inkling-2-mini">Inkling 2 Mini - API Pricing &amp; Benchmarks | OpenRouter</a></li>

</ul>
</details>

**标签**: `#LLMs`, `#GLM-5.4`, `#looped transformers`, `#coding assistants`, `#model release`

---

<a id="item-tech-news-3"></a>
### [Anthropic 称 Claude 发现 VP≠VNP 并公布 Lean 4 证明](https://github.com/anthropics/formal-math/blob/main/vp-vnp/README.md) ⭐️ 8.0/10

该 Telegram 帖文称，Anthropic 于 11 月 24 日公开论文《VP ≠ VNP over every field》及 Lean 4 形式化证明；仓库称结果由内部研究用 Claude 模型发现，论文和代码均由 AI 撰写。论文声称给出哈密顿圈多项式的超多项式算术电路下界，据此推出 VP 是 VNP 的真子类；若成立，这将解决 Valiant 1979 年的代数复杂度猜想，但并不涉及 P 与 NP。该工作已经过三条标准公理审计和独立内核 nanoda 复核，除预留文件外没有 sorry，但尚无人类数学家通读。Lean 无法确认形式化陈述与所称命题一致，附录 Q 列出出入，结果仍在等待独立审阅。

telegram · zaihuapd · 11月24日 06:02

**「背景」** VP 与 VNP 是 Valiant 于 1979 年提出的代数复杂度类，用来刻画多项式能否由规模受限的算术电路计算；VP≠VNP 是 P≠NP 在算术电路模型下的类比，但并非同一个命题。此次公开的 Lean 4 形式化正是围绕这一长期未决的猜想展开。

**「影响」** 对 AI for math 和复杂度理论研究者来说，眼下可核查的具体事项是附录 Q 所列的形式化陈述与论文命题之间的出入，以及 nanoda 复核的范围；在独立人类审阅确认前，不应把该结果作为已解决的 Valiant 猜想引用。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://explainx.ai/blog/anthropic-claude-vp-vnp-valiant-lean-proof-claimed-vs-verified-2026">VP ≠ VNP Lean Proof: Claimed vs Verified (2026) - explainx.ai</a></li>
<li><a href="https://interestingengineering.com/ai-robotics/claude-proves-vp-not-vnp-valiant-conjecture">Claude claims to prove VP ≠ VNP in Valiant&#x27;s 47-year-old ...</a></li>

</ul>
</details>

**标签**: `#complexity theory`, `#Lean 4`, `#AI for math`, `#formal verification`, `#Anthropic`

---

<a id="item-tech-news-4"></a>
### [NariQ 发布 Qwen3.8-27B 低比特 GGUF 量化](https://huggingface.co/nari-labs/Qwen3.8-27B-NariQ-GGUF) ⭐️ 7.0/10

面向本地和自托管推理，NariQ 发布了 Qwen3.8-27B 的 3 比特及以下 GGUF 量化，称一个 10 GB 文件能在代理任务、数学、多语言推理和图像理解上保留接近 BF16 的质量，并自称据其所知是首个在长程代理任务上达到 BF16 水平的 3 比特以下量化。厂商给出的 BF16/3-bit/2.5-bit/2-bit 得分为 DeepSWE 39.8/41.0/41.9/28.6、Terminal-Bench 2.1 62.6/63.8/60.2/52.4，显示 3-bit 和 2.5-bit 接近 BF16，而 2-bit 在代理任务上明显下降。运行这些量化目前需要 NariQ 的 llama.cpp fork，而不是上游 llama.cpp；解码速度仅称在 RTX PRO 6000 上与其他量化相当。

hackernews · toebee · 11月23日 13:42 · [社区讨论](https://news.ycombinator.com/item?id=50611402)

**「背景」** Qwen3.8-27B 是一个开放权重的稠密视觉语言模型。GGUF 是 llama.cpp 生态常用的模型格式，量化通过降低权重位宽来压缩模型体积和内存占用；位宽越低，长程智能体（agentic）任务上的精度损失通常越明显，因此 3-bit 以下量化能否保留 BF16 表现，是本地推理用户判断此类发布的关键。

**「影响」** 对本地部署者而言，最直接的约束是兼容性：这些 GGUF 目前只能在 nari-llama.cpp 分支上运行，现有基于上游 llama.cpp 的加载器、服务框架和部署脚本需要另行适配或从源码构建。若用于长程代理任务，厂商数据也显示 2-bit 的 DeepSWE 28.6 和 Terminal-Bench 52.4 远低于 BF16，因此选型应优先验证 3-bit/2.5-bit，而不能只看文件更小。

**「社区讨论」** 评论中，rao-v 肯定该项目覆盖多类长程任务并提及 held-out 检查，但 WithinReason 认为从图表看大部分提升来自评测框架差异而非模型本身，Retro\_Dev 则追问降比特到底丢失了哪些信息。jedbrooke 报告在 M3 Pro（18 GB）上 3.0bpw 约为 3.8 tok/s、2.0bpw 约为 4.9 tok/s，并询问能否装进 16 GB Mac。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://openrouter.ai/qwen/qwen3.8-27b">Qwen 3 . 8 27 B - API Pricing &amp; Benchmarks | OpenRouter</a></li>

</ul>
</details>

**标签**: `#quantization`, `#LLM inference`, `#local AI`, `#GGUF`, `#benchmark evaluation`

---

<a id="item-tech-news-5"></a>
### [Codex2api 疑遭供应链投毒，v3.1.11 被指移除鉴权](https://github.com/WormW/codex2api-incident-2026-11) ⭐️ 7.0/10

据 Telegram 转述的事件复盘，开源项目 codex2api 的作者账号被黑，攻击者绕过 main 分支推送 tag，使 Release 构建出带后门的版本。报告称 v3.1.11 移除了鉴权，导致无需密码即可远程执行命令；同时有一个 workflow 将仓库的 16 个 GitHub Actions secrets 外传，波及同一账号下至少 21 个仓库。该报告将这些行为描述为“疑似”，且尚未独立核实；已安装或更新到 3.1.10–3.1.12 的用户应停止使用这些版本，回退到 3.1.9，并轮换 GitHub token、SSH key、数据库及 DeepSeek 等相关密钥。

telegram · zaihuapd · 11月23日 11:21

**「背景」** GitHub Actions 的发布流程可以配置为由 tag 推送触发，而 tag 能指向不在 main 分支上的提交；若工作流未限制触发来源和令牌权限，构建过程就可能执行非主线代码并读取仓库 secrets。2025 年 3 月，常用的 tj-actions/changed-files 曾被入侵并导致使用该 Action 的仓库泄露 CI/CD 密钥，是同类供应链风险的先例。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://thehackernews.com/2025/03/github-action-compromise-puts-cicd.html">GitHub Action Compromise Puts CI/CD Secrets at Risk in Over ...</a></li>
<li><a href="https://unit42.paloaltonetworks.com/github-actions-supply-chain-attack/">GitHub Actions Supply Chain Attack: A Targeted Attack on ...</a></li>

</ul>
</details>

**标签**: `#supply-chain-security`, `#security-incident`, `#github-actions`, `#secrets-management`, `#open-source-security`

---

<a id="item-tech-news-6"></a>
### [Meta AI 负责人称超级智能将至，警告控制风险](https://thenextweb.com/news/metas-ai-chief-says-superintelligence-is-arriving-and-control-is-at-risk) ⭐️ 7.0/10

Meta 首席 AI 官、超级智能实验室负责人 Alexandr Wang 在 X 发长文称，超级智能已不再是“未来某天”的议题，并警告人类很难继续掌控可无限自我改进或比自己聪明 1000 倍的系统，呼吁紧急投入安全、对齐与防护研究。他以数学家 Levent Alpöge 借助 Anthropic 的 Claude 完成、据称经 Lean 与 Mathlib 社区机器校验的黎曼猜想证明为例，认为 AI 与顶尖人类的差距只剩具体知识、工程整合与实验三块。该证明目前尚无人类可读版本，也未见独立确认。

telegram · zaihuapd · 11月23日 12:49

**「背景」** 据 Al Jazeera 报道，Anthropic 员工 Levent Alpöge 于 2026 年 11 月 20 日宣布用 Claude 找到了这道有 167 年历史的黎曼猜想证明；Meta 首席 AI 官 Alexandr Wang 随后在周日以此为例警告超级智能临近。该证明经 Lean 与 Mathlib 机器校验，但尚无人类可读版本——形式化校验能确认代码符合给定陈述，却不能替代数学界对证明思路和结论的同行评审。

**「影响」** 对研究者和政策制定者而言，最直接的动作是先把该数学声明与超级智能风险判断分开处理：在人类可读证明和独立复核出现前，无法核验 Lean/Mathlib 的机器校验结果，也不宜据此制定安全或治理决策。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.aljazeera.com/economy/2026/11/23/ai-superintelligence-arriving-warns-top-meta-executive">Artificial superintelligence ‘arriving’, warns top Meta ... | Al Jazeera</a></li>
<li><a href="https://www.clarin.com/us-news/who-is-levent-alpoge-the-anthropic-mathematician-who-claims-solved-the-riemann-hypothesis-with-claude_0_2WdGvYKBVM.html">Who is Levent Alpöge ? The Anthropic mathematician who claims he...</a></li>

</ul>
</details>

**标签**: `#AI safety`, `#superintelligence`, `#Riemann hypothesis`, `#Lean theorem proving`, `#Meta AI`

---

<a id="item-tech-news-7"></a>
### [黎曼猜想 AI 证明被指空转，作者承认代码满是垃圾](https://x.com/i/web/status/2124987173439209561) ⭐️ 7.0/10

一则聚合消息称，Alpöge 与 Claude 此前宣称用 Lean 形式化证明了黎曼猜想及其广义版本，但公开成果约 1700 万行、17.5 万个文件，没有人类可读的证明。Lean 与 Mathlib 社区次日曾表示，对该代码证明此命题“有充分信心”，随后有研究者指出关键定义被写成恒真、几何条件形同虚设，证明可能只是空转。23 日 Alpöge 承认“25 万页是玩笑”，称代码“满是垃圾但能编译”，并认为批评完全合理；这些细节来自聚合摘要，尚待独立核实。

telegram · zaihuapd · 11月24日 01:29

**「背景」** Lean 是交互式定理证明器，Mathlib 是其数学库；形式化证明依赖内核逐行检查，但“能编译”只保证代码通过类型检查，不保证形式化定义忠实于原本要证的命题。外部报道显示，Lean 社区曾在 11 月 21 日表示已核验约 1700 万行代码并认定证明正确，随后才有研究者指出关键定义被写成恒真、证明可能空转。

**「影响」** 对依赖 Lean 形式化结果的数学家和评审者来说，直接影响是审查重点不能停在“代码能否编译”，还要确认关键定义并非恒真、定理陈述仍对应黎曼猜想；此次争议正因定义被指空转，使可编译性不足以支撑结论。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.zerohedge.com/science/did-claude-just-solve-maths-most-famous-problem-even-anthropics-mathematician-admits-timing">Mathematicians Confirm Claude Solved Math&#x27;s Most... | ZeroHedge</a></li>

</ul>
</details>

**标签**: `#AI for mathematics`, `#Lean theorem proving`, `#formal verification`, `#research integrity`, `#Claude`

---

<a id="item-tech-news-8"></a>
### [4.5 万家企业组织联名致信欧盟，要求对苹果 iPhone 浏览器限制立案](https://appleinsider.com/articles/26/11/23/eu-urges-to-challenge-apples-grip-on-iphone-browsers?utm_source=rss) ⭐️ 7.0/10

包括 Mozilla 和 Shopify 在内的企业及民间组织联名致信欧盟委员会，要求对苹果在 iPhone 上的浏览器限制正式立案。联名方称，署名方合计代表约 4.5 万至 5.5 万家欧盟企业组织，联署将持续征集至 2026 年 12 月 3 日。信中主张，苹果虽已按《数字市场法》在欧盟允许竞品浏览器使用自有引擎，但现有技术与法律要求使厂商无法把已有欧盟用户迁出 WebKit，企业也更依赖通过 App Store 触达用户。联名方自行测算，若半数原生 iOS 应用转为 Web 形式，欧盟企业每年可节省 110 亿欧元开发成本和 13 亿欧元 App Store 费用。需要说明的是，这目前只是企业联盟向监管机构施压的诉求，并非欧盟委员会已确认的立案或处罚决定。

telegram · zaihuapd · 11月24日 03:02

**「背景」** 欧盟《数字市场法》将浏览器和应用商店等列为大型平台必须开放竞争的核心服务。苹果虽已按该法在欧盟允许竞品浏览器使用自有引擎，但现有用户难以随浏览器更新迁出 WebKit，企业也仍主要依赖 App Store 触达用户，这构成联名方要求欧盟委员会立案审查的技术与市场背景。

**「实际影响」** 对欧盟开发者和浏览器厂商来说，现行 DMA 规则虽允许替代引擎，但联名方称两年来没有一次成功的 WebKit 迁移，这意味着企业短期内仍须为 iOS 用户维护原生应用并通过 App Store 分发，不能把“转向 Web 应用可省成本”的测算视为已实现收益。联名行动能否推动欧盟委员会立案尚不确定，相关企业可关注 12 月 3 日联署截止后委员会是否启动程序。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.yahoo.com/news/politics/articles/eu-coalition-presses-eu-commission-191706516.html?fr=sycsrp_catchall">EU Coalition Presses EU Commission to Act on Apple Browser ...</a></li>

</ul>
</details>

**标签**: `#Apple`, `#EU DMA`, `#browser competition`, `#WebKit`, `#tech policy`

---

<a id="item-tech-news-9"></a>
### [黄循财：新加坡不会成规避芯片管制通道](https://www.bloomberg.com/news/articles/2026-11-24/singapore-won-t-be-conduit-to-skirt-us-chip-curbs-wong-says) ⭐️ 7.0/10

新加坡总理黄循财表示，新加坡不会成为企业规避美国芯片出口管制的通道，当局正在调查 Megaspeed 采购英伟达芯片的交易。就在此前一天，美国商务部将 Megaspeed 及另外 6 家东南亚企业列入贸易黑名单，涉及它们在马来西亚和泰国的关联实体；《联邦公报》称这些企业存在向未获授权用户转移先进计算产品的“重大风险”。路透社报道，阿里巴巴新加坡子公司 Apex Enterprise Solutions 也在名单中，阿里巴巴表示从未转移受管制的先进计算芯片。

telegram · zaihuapd · 11月24日 05:03

**「背景」** 美国商务部在前一天将 Megaspeed 及另外 6 家东南亚企业列入贸易黑名单，理由是这些实体存在向未获授权用户转移先进计算产品的“重大风险”，名单还包括其在马来西亚和泰国的关联实体。新加坡对 Megaspeed 采购英伟达芯片交易的调查，正是在这一黑名单措施之后展开。

**「对相关企业的直接影响」** 美国商务部工业与安全局已于 11 月 23 日将 Megaspeed 及其在东南亚的关联实体等共七家列入实体清单，这意味着美国供应商向这些实体出口先进计算产品需申请许可，实际业务往来将受阻。被列入清单的还包括阿里巴巴新加坡子公司 Apex Enterprise Solutions，阿里巴巴否认曾转移受管制芯片，说明相关企业需就自身跨境采购与转售链条准备合规说明。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.reuters.com/business/us-blacklist-megaspeed-chip-firm-linked-nvidia-scandal-source-says-2026-11-23/">US blacklists Alibaba subsidiary and Megaspeed linked to ...</a></li>
<li><a href="https://casrai.org/news/bis-adds-megaspeed-seven-entities-entity-list-final-rule-2026">BIS Adds Seven Megaspeed Entities to Entity List — CASRAI</a></li>
<li><a href="https://www.ibtimes.com/us-blacklists-megaspeed-southeast-asian-firms-nvidia-chips-3810114">US Blacklists Nvidia-Linked Firm Over China Chip Fears. Six ...</a></li>

</ul>
</details>

**标签**: `#chip export controls`, `#AI hardware`, `#Singapore`, `#Nvidia`, `#US tech policy`

---

## 科技博客

<a id="item-tech-blog-1"></a>
### [vLLM 插件实现 ERNIE 5.5 Flash 首日支持](https://vllm.ai/blog/2026-11-24-ernie-5-5-flash-preview) ⭐️ 7.0/10

rss · vLLM Blog · 11月24日 00:00

**「背景」** ERNIE 5.5 Flash Preview 是 280B 总参数、每 token 激活 14B 的稀疏 MoE 模型，支持 1M token 上下文和长程 Agent 任务；其新注意力、MoE 与低精度设计让高效推理和框架适配成为双重挑战。厂商希望发布当天就能在官方 vLLM 上运行，而不必维护分叉或等待专用镜像。

**「方案」** 作者的核心思路是模型侧按推理成本重设结构并做算子融合，框架侧用独立插件承载 ERNIE 代码与定制内核。模型共 43 层，37 层用 HCA、6 层用 MLA-DSA，并引入 VHA、Multi-Router Latent MoE、mHC 和 MultiMax 输出头；团队把可预计算参数折叠进权重，并将 FP8 量化、路由链和分段激活等合并进单内核，报告相对逐算子实现有 1.55×–6.53× 的每内核加速。FlashIndexer 用小型头路由器按 token 动态选择稀疏索引头，并以阈值预过滤缩小 top-k 候选，作者称在 1M 上下文约有 1.4×（约 40%）加速；它只需约 1B token 微调路由器，且不改下游注意力接口。量化上，路由专家采用 MXFP4 W4A8 QAT，训练伪量化与推理的粒度、缩放和舍入一致，KV 缓存用 FP8、DSA 索引器用 FP4。DSpark 用随权重发布的 3 层 MoE 草稿模型，每步最多提议 7 个 token，在编码和 Agent 负载上平均接受长度超过 4.0。集成层面，vLLM-ERNIE 通过 vllm.general\_plugins 入口注册架构，并按需延迟导入，因此能与官方 vllm==0.32.0 共存而不影响其他模型，并复用前缀缓存、分块预填、CUDA 图和 PD 分离等能力。

**「启示」** 作者据此认为，推理优化应从模型架构阶段就与 serving 框架协同设计，而插件化让新模型无需分叉即可接入成熟生态；不过这些加速与性能数字来自厂商自报，且未附完整基准方法，宜作方向性证据。

**标签**: `#vLLM`, `#ERNIE`, `#MoE inference`, `#kernel fusion`, `#speculative decoding`

---

## 财经新闻

<a id="item-finance-news-1"></a>
### [纽约联储主席威廉姆斯：通胀仍过高，进一步加息可随时间推进](https://www.cnbc.com/2026/11/23/john-williams-fed-inflation-rate-hikes.html) ⭐️ 7.0/10

纽约联储主席威廉姆斯表示，要把通胀拉回美联储 2%的目标“仍有工作要做”，并暗示进一步加息可以“随着时间”推进。市场已完全计入 12 月 8 日至 9 日 FOMC 会议加息 25 个基点，当前联邦基金利率目标区间为 3.75%-4%。

rss · CNBC Finance · 11月23日 21:02

**「背景」** 美联储官员对加息速度存在分歧，威廉姆斯主张审慎行事；他预计通胀将在 2027 年更接近 2%、并在 2028 年达到该目标，即便经济增长保持稳健。

**标签**: `#Federal Reserve`, `#monetary policy`, `#interest rates`, `#inflation`, `#John Williams`

---

<a id="item-finance-news-2"></a>
### [上海地铁 12 月 1 日起调整票价，为 21 年来首次](https://weibo.com/1699432410/5368461393397183) ⭐️ 7.0/10

上海轨道交通将于 12 月 1 日实施 21 年来首次票价调整，起步价 3 元、覆盖 0 至 4 公里，之后按 4、4、4、7、7、10、10 公里分段加 1 元，50 公里以上每 15 公里加 1 元。

telegram · zaihuapd · 11月23日 10:45

**「背景」** 上海地铁现行票价自上次调整后已沿用 21 年，此次是这一期间首次调价；同步推出的计次票和“当月同一支付渠道累计满 90 元享 9 折”，意在减轻高频通勤者受到的涨价影响。

**「影响」** 对高频通勤者，同步推出的四档计次票和同一支付渠道当月累计满 90 元享 9 折可减轻部分支出，但节省幅度取决于出行距离和次数。

**标签**: `#Shanghai Metro`, `#public transit fares`, `#fare adjustment`, `#commuter costs`, `#urban transport policy`

---