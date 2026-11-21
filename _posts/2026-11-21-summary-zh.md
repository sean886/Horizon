---
layout: default
title: "Horizon Summary: 2026-11-21 (ZH)"
date: 2026-11-21
lang: zh
---

> 从 39 条内容中筛选出 9 条重要资讯。

---

**科技新闻**
1. [Inkling 2 Mini 发布：采用循环 Transformer 的开放权重小模型](#item-tech-news-1) ⭐️ 8.0/10
2. [GitHub 稿件声称给出 Navier–Stokes 有限时间爆破](#item-tech-news-2) ⭐️ 8.0/10
3. [CVE-2026-99312：KVM 漏洞致 AMD 虚拟机读取宿主内存](#item-tech-news-3) ⭐️ 8.0/10
4. [台积电暂停中国公司 16nm 及以下订单](#item-tech-news-4) ⭐️ 8.0/10
5. [美 SEC 据报调查英伟达潜在会计问题](#item-tech-news-5) ⭐️ 7.0/10
6. [Signal 称正限制移动端 AI 代理获取用户数据](#item-tech-news-6) ⭐️ 7.0/10
7. [阿伦森博客借“随机鹦鹉证明黎曼猜想”讨论 AI 数学理解](#item-tech-news-7) ⭐️ 7.0/10

**科技博客**
1. [为什么缓存 LLM 输出省不了钱](#item-tech-blog-1) ⭐️ 6.0/10

**财经新闻**
1. [特朗普称拟对海外建设 AI 数据中心的美国公司征收“巨额税款”](#item-finance-news-1) ⭐️ 7.0/10

---

## 科技新闻

<a id="item-tech-news-1"></a>
### [Inkling 2 Mini 发布：采用循环 Transformer 的开放权重小模型](https://thinkingmachines.ai/news/inkling-2-mini/) ⭐️ 8.0/10

thinkingmachines.ai 发布了 Inkling 2 Mini，这是一个采用循环 Transformer（looped transformer）架构的开放权重小模型；由于条目未附带原文内容，参数规模与官方基准仍需以社区转述为准。据评论者引述团队在 Reddit 的说法，训练全程使用 nvfp4，模型尺寸主要参照本地用户的常见需求确定，并被拿来与 Qwen3.8-27B 相提并论；这一基准对比尚未得到独立验证。可运行性方面，社区报告已在 llama.cpp 上跑通，其中一例为 Ryzen 395 搭配 Vulkan 后端、解码约 27 tokens/s，另一例为 32GB M1 Pro 上的 q4 量化、约 10 tokens/s。unsloth 已放出可用于 Ollama/llama.cpp 的 GGUF 版本。

hackernews · jasondavies · 11月20日 20:12 · [社区讨论](https://news.ycombinator.com/item?id=50581260)

**「背景：循环 Transformer」** 循环 Transformer 的关键设计是让中间若干层被重复执行，从而用更多“每 token 计算”提升推理能力，而不必按比例增加参数量。Hugging Face 的介绍称，Inkling 2 Mini 是约 260 亿总参数、每 token 激活约 30 亿参数的多模态 MoE 模型，部分层会循环三次，并支持 100 万 token 上下文以及图像和文本输入。

**「对本地部署的影响」** 目前 llama.cpp 对该模型的支持尚不完整：评论者列出至少四个尚未合并的相关 PR（32694、32657、32429、32704），并给出一段位于 src/llama-graph.cpp 的补丁，称可带来约 30% 的提速。对希望在本地部署的用户而言，这意味着要获得较理想的速度，需要自行应用这些补丁，或者等待它们被合并。

**「社区实测与讨论」** 实测反馈并不一致：一位用户在 M1 Pro 上让模型写 CSV 排序脚本，结果正确，只是解释偏啰嗦；同一用户让其识别硬币类型与年份时，模型输出了约 12,000 tokens 仍未收敛。另有评论者认为，开放权重模型在此之后可能普遍转向循环架构，并对这一普及程度下的安全性与可解释性提出疑问；这属于个人推测，并非已证实的事实。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://thinkingmachines.ai/news/inkling-2-mini/">Introducing Inkling 2 Mini - Thinking Machines Lab</a></li>
<li><a href="https://huggingface.co/blog/inkling2mini">Welcome Inkling 2 Mini, Cutting-edge Performance for your ...</a></li>

</ul>
</details>

**标签**: `#open-weights`, `#looped-transformers`, `#local-llm-inference`, `#llama.cpp`, `#model-release`

---

<a id="item-tech-news-2"></a>
### [GitHub 稿件声称给出 Navier–Stokes 有限时间爆破](https://github.com/tristanbuckmaster/navier-stokes/) ⭐️ 8.0/10

一份托管在 GitHub 上的稿件声称对 Navier–Stokes 方程给出有限时间爆破结果，并在 Hacker News 上引起大量讨论。所给材料只呈现了这一公开声明，没有论文全文、同行评审、复现或正式发表信息，因此无法判断其证明是否成立。若该声明得到确认，受影响的主要是研究该方程解的数学家与流体力学研究者，而不是一般软件开发者。

hackernews · trotro · 11月20日 15:34 · [社区讨论](https://news.ycombinator.com/item?id=50576232)

**「背景」** 纳维–斯托克斯存在性与光滑性问题是千禧年大奖难题之一：它问三维空间中光滑初值是否总会在所有时间保持光滑。此前，2026 年 9 月 8 日 OpenAI 曾提出一个带光滑外力项的解法，而据维基百科条目，Tristan Buckmaster 在 OpenAI 公布前约 12 小时代表自己并部分代表 Levent Alpöge 发表了声明（tool-1-1）。与此相对，本次 GitHub 仓库所附论文声称处理无外力情形，对 R^3 上紧支撑、T^3 上周期的光滑初值给出有限时间爆破，并包含 79 页论文和 Lean 4 形式化（tool-1-2、tool-1-3）。

**「距离千禧年奖仍有门槛」** 对关心这一结果的人而言，关键的不确定处不在于“是否发生爆破”，而在于它能否对应 Clay 数学研究所千禧年难题所要求的四条命题之一：检索到的资料指出，无外力情形下的有限时间爆破本身并不构成对该问题的解答，奖项路径涉及带光滑外力的 C/D 类命题。加之当前证据只是 GitHub 上发布的声明，尚无独立验证或同行评审，研究者在引用或据此推进时应把它当作待核实的预印本主张，而非已确立的结论。

**「社区讨论」** 评论者把这份声明与需要精心设计外力项的版本作对比，认为无外力情形若成立更接近“真实”场景；也有人希望看到能实时展示爆破的数值模拟，以建立直观理解。还有评论提到同一天出现的其他重大数学声明，但这些比较和期待都属于个人观点，未在提供材料中得到验证。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://en.wikipedia.org/wiki/Navier%E2%80%93Stokes_priority_controversy">Navier–Stokes priority controversy - Wikipedia</a></li>
<li><a href="https://hotrepo.ai/tristanbuckmaster/navier-stokes">tristanbuckmaster/navier-stokes: Lean 4 formalization of a ...</a></li>
<li><a href="https://aixiv.online/abs/2611.02204">[2611.02204] Finite-time blow-up for the Navier–Stokes ...</a></li>
<li><a href="https://en.wikipedia.org/wiki/Navier%E2%80%93Stokes_existence_and_smoothness">Navier – Stokes existence and smoothness - Wikipedia</a></li>
<li><a href="https://vibemathed.com/problem/navier-stokes-millennium-prize-problem-finite-time-breakdown-with-smooth-forcing">Navier – Stokes Millennium Prize problem: finite - time breakdown with...</a></li>

</ul>
</details>

**标签**: `#Navier–Stokes equations`, `#mathematics research`, `#fluid dynamics`, `#research preprint`, `#Hacker News`

---

<a id="item-tech-news-3"></a>
### [CVE-2026-99312：KVM 漏洞致 AMD 虚拟机读取宿主内存](https://thehackernews.com/2026/11/new-linux-kvm-flaw-cve-2026-99312-lets.html) ⭐️ 8.0/10

Linux 内核 KVM 中的 CVE-2026-99312 漏洞允许启用了嵌套虚拟化的 AMD 主机上的虚拟机读取宿主内存；研究者在 DigitalOcean 环境中从虚拟机内读取到约 127 GB 宿主内存。上游修复已于 11 月 18 日随稳定内核 7.3.5 等版本发布，但 Debian、Ubuntu 等发行版内核尚未修复。受影响的 AMD 主机在补丁到位前可关闭嵌套虚拟化以规避风险。

telegram · zaihuapd · 11月20日 14:23

**「背景」** KVM 是 Linux 内核中的虚拟化层，负责在宿主机与客户机之间隔离 CPU 和内存访问。嵌套虚拟化允许客户机内部再运行一层虚拟机监控程序，因而引入更复杂的权限与内存管理路径，CVE-2026-99312 正位于这一配置面。

**「影响与处置」** 运行启用嵌套虚拟化的 AMD 主机的云服务商和运维者，需要在发行版内核补丁可用前关闭嵌套虚拟化，或改用已包含上游修复的内核；否则虚拟机可读取宿主内存。Debian、Ubuntu 等发行版内核当前仍未修复。

**标签**: `#KVM`, `#AMD`, `#virtualization security`, `#Linux kernel`, `#CVE-2026-99312`

---

<a id="item-tech-news-4"></a>
### [台积电暂停中国公司 16nm 及以下订单](https://appleinsider.com/articles/26/11/20/apple-supplier-tsmc-cuts-off-china-chip-orders-amid-tighter-export-controls) ⭐️ 8.0/10

据 AppleInsider 报道，台积电已通知客户，暂停接受中国公司的 16nm 及以下先进制程订单。按照收紧后的美国半导体出口新规，除非事先取得美国出口许可或豁免，台积电不得向这些中国公司供货；这些中国公司因此只能使用 28nm、40nm 等旧制程，也无法使用 AI 数据中心所需的高带宽内存。此前台积电可自行评估客户设计是否符合豁免条件，现在则须由客户提前申请；美国获批名单包括苹果、AMD 和英伟达，尚无中国公司。台积电表示将遵守新规。

telegram · zaihuapd · 11月21日 02:01

**「背景」** 美国对先进半导体的对华出口实行许可或豁免制度，受控订单在供货前须获得授权。此前台积电可自行评估客户设计是否满足豁免条件；收紧后的规则要求客户提前申请，且现有获批名单尚未列入中国公司。

**「影响」** 中国芯片设计公司若要继续在台积电投 16nm 及以下订单，须先取得美国出口许可；未获许可时只能退回 28nm、40nm 等旧制程，这将迫使其重新设计或另寻产能，并限制其面向 AI 数据中心的芯片方案。美国获批名单目前没有中国公司，短期内许可不确定性会直接卡住相关流片排期。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://theoutpost.ai/news-story/tsmc-cuts-chinese-chip-designers-off-from-the-tech-their-ai-chips-need-33882/">TSMC tightens chip curbs on Chinese designers</a></li>

</ul>
</details>

**标签**: `#semiconductors`, `#TSMC`, `#export controls`, `#AI hardware`, `#China tech`

---

<a id="item-tech-news-5"></a>
### [美 SEC 据报调查英伟达潜在会计问题](https://www.marketscreener.com/news/us-sec-s-nvidia-probe-is-examining-potential-accounting-issues-sources-say-ce785ed3dd8ff627) ⭐️ 7.0/10

据 Marketscreener 援引消息人士报道，美国证券交易委员会（SEC）正在审查英伟达可能存在的会计问题。目前公开信息仅支持这一标题级说法，未提供调查范围、时间表、具体指控或英伟达回应的细节，相关指称尚未得到证实。该报道将这家 AI 硬件核心供应商置于监管审查之下，但不应把尚未确认的会计问题当作既定事实。

hackernews · ftchd · 11月20日 20:22 · [社区讨论](https://news.ycombinator.com/item?id=50581438)

**「背景」** 美国证券交易委员会（SEC）负责监督上市公司的财务报告；本次报道中的调查聚焦英伟达可能存在的会计问题。路透社称，英伟达临时 CEO、长期担任 CFO 的 Colette Kress 在周二的财报电话会上表示，公司为支持 AI 产业感到自豪，但今后会“更具选择性”；相关报道还称，Kress 自 2013 年起担任 CFO，并负责签署和认证公司财报。

**「社区讨论」** 评论者中，有人把此事与所谓“循环融资”以及与 neocloud 重新谈判使用协议联系起来，并担心会加剧市场回调；也有人质疑，若董事会认为存在会计问题，为何让首席财务官出任临时 CEO，并认为财务部门应对相关收入入账负责。这些说法均来自评论，未在所给材料中得到证实。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.reuters.com/world/us-secs-nvidia-probe-is-examining-potential-accounting-issues-sources-say-2026-11-20/">EXCLUSIVE: Nvidia&#x27;s accounting is a focus of US SEC ...</a></li>
<li><a href="https://www.kucoin.com/news/flash/us-sec-investigates-nvidia-over-potential-accounting-issues">The U.S. SEC Investigates NVIDIA Over Potential Accounting ...</a></li>

</ul>
</details>

**标签**: `#Nvidia`, `#SEC investigation`, `#accounting`, `#AI hardware`, `#tech industry`

---

<a id="item-tech-news-6"></a>
### [Signal 称正限制移动端 AI 代理获取用户数据](https://signal.org/blog/protecting-your-privacy/) ⭐️ 7.0/10

Signal 发布博客称，它正在设法限制移动操作系统上的 AI 代理捕获用户数据，并表示在这一方向上取得了进展；但公开信息没有给出具体技术机制、适用版本或上线时间。因此目前无法确认这已经是交付给用户的防护能力，还是仍在推进中的计划。这项工作的直接影响对象是 Signal 用户，以及移动平台上能够访问其他应用数据的 AI 代理。

hackernews · dotcoma · 11月20日 09:42 · [社区讨论](https://news.ycombinator.com/item?id=50572348)

**「背景」** Signal 长期将隐私保护作为核心产品定位，其博客把这项措施描述为限制移动操作系统内置的最新 AI 代理读取或存储 Signal 数据。相关风险在于权限层级：一旦代理在操作系统层获得屏幕读取或跨应用内容访问能力，单个应用自身的防护就可能被绕过。

**「实际影响」** 在 Signal 公布具体机制前，用户和开发者只能将其视为方向性说明，无法判断现有聊天是否已受保护，也无法据此做兼容性或部署决策。

**「社区讨论」** 部分评论者肯定 Signal 着手处理这一问题，但讨论很快转向可验证性和可用性：有人提到 Meredith Whittaker 的访谈称，即使用户自己不安装 AI 应用，联系人安装后仍可能泄露聊天内容；也有人要求 Signal 公开其取证调查结果，供资源较少的开发者复用。另有用户报告 Signal 的垃圾信息防护会让 VPN 用户反复遭遇验证码，认为这反而迫使需要保护的人改用其他应用。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://signal.org/blog/protecting-your-privacy/">Signal &gt;&gt; Blog &gt;&gt; Signal is Serious About Protecting Your Privacy</a></li>

</ul>
</details>

**标签**: `#privacy`, `#AI agents`, `#mobile security`, `#Signal`, `#data access`

---

<a id="item-tech-news-7"></a>
### [阿伦森博客借“随机鹦鹉证明黎曼猜想”讨论 AI 数学理解](https://scottaaronson.blog/?p=10344) ⭐️ 7.0/10

Scott Aaronson 的博客文章以“随机鹦鹉显然证明了黎曼猜想”为题，引发 Hacker News 讨论；现有材料没有提供任何数学证明或论文，文章与讨论实际围绕大模型能否产出可被人类理解、可验证的数学结果展开。讨论者用国际象棋引擎作类比：Stockfish 能给出评估和计算链条，但底层 NNUE 仍是难以直观解释的“随机鹦鹉”式组件。因而这更像关于 AI 能力、可解释性与科学理解边界的评论，而非黎曼猜想的突破。

hackernews · stratos123 · 11月20日 20:03 · [社区讨论](https://news.ycombinator.com/item?id=50581084)

**「背景」** “随机鹦鹉”（stochastic parrots）是 2021 年出现的一个批评性说法，用来贬低大型语言模型只会复述统计模式。Aaronson 的这篇博文正是在回应社交媒体上“这些所谓的随机鹦鹉已经证明了黎曼猜想”一类说法，并对这种论调表示不以为然。

**「社区讨论」** 有评论者用国际象棋引擎类比，认为 Stockfish 的评估虽有解释，但底层 NNUE 仍是难以直观理解的“随机鹦鹉”式组件；另一人则担忧人类会在科学和工程中越来越无法理解，也无法作出实质贡献。也有评论设想，如果数学家拥有近乎无限的算力，是否能取得类似突破。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://scottaaronson.blog/?p=10344">Shtetl-Optimized » Blog Archive » The stochastic parrots have ...</a></li>

</ul>
</details>

**标签**: `#AI and mathematics`, `#LLM capabilities`, `#interpretability`, `#scientific understanding`, `#Hacker News discussion`

---

## 科技博客

<a id="item-tech-blog-1"></a>
### [为什么缓存 LLM 输出省不了钱](https://seangoedecke.com/why-output-caching-doesnt-work/) ⭐️ 6.0/10

rss · Sean Goedecke · 11月21日 00:00

**「背景」** LLM 推理经济的核心做法之一是缓存输入（KV cache），以免每条新消息都重算整段对话历史。作者据此追问：既然输出端也存在大量重复，为什么不把模型输出也缓存起来？

**「方案」** 输出重复确实存在：让 agent 写 PR 时要它复述相关代码、长任务调查要它引用自己产出的证据文档，而输出 token 单价比输入 token 贵得多，理论上更值得优化。作者设想的办法是微调或提示模型只输出“src/script.py:12-15”这类引用，由 harness 展开给用户。但他认为这行不通，因为重复只发生在用户可见的输出里，模型在内部思维链中并不需要重述已经掌握的信息。按他自己的 agent 历史估算，可见输出只占约 6% 的输出 token，推理占 50%、工具调用占 44%；即使乐观地砍掉可见输出三分之二的 token，总输出也只省约 4%，这正是 Amdahl 定律的作用。真正要省输出 token，得压缩那 94% 的不可见部分，而这主要取决于模型智能：模型越强，需要的推理与工具调用越少，于是会出现单 token 贵 5 倍、总 token 少 6 倍、整体反而更便宜的现象。作者也坦言对思维链不重复的判断只有中等把握，并好奇工具调用内部是否也存在重复。

**「启示」** 输出缓存只能触及可见输出的微小一角，输出成本的真正杠杆是模型智能带来的 token 效率，而非表面的重复消除。

**标签**: `#LLM inference economics`, `#output caching`, `#agentic coding`, `#Amdahl&\#x27;s law`, `#token costs`

---

## 财经新闻

<a id="item-finance-news-1"></a>
### [特朗普称拟对海外建设 AI 数据中心的美国公司征收“巨额税款”](https://apnews.com/article/trump-artificial-intelligence-data-centers-f1ac03b73d13445400eeed8631d9d879) ⭐️ 7.0/10

特朗普于当地时间 11 月 20 日在白宫记者会上表示，计划对在海外建设 AI 数据中心的美国科技公司征收“巨额税款”，但未说明税率、立法安排或实施时间。他称此举旨在把数据中心留在美国、保持对中国的 AI 竞争优势，并表示尚未向政府内部官员透露这项计划。

telegram · zaihuapd · 11月21日 03:26

**「背景」** 美国多地社区正因数据中心的用电需求和噪音反对新建项目；特朗普同日敦促各地接纳数据中心，并建议社区与开发商谈判、争取由开发商向社区付款。

**「影响」** 这项拟议征税若实施，将直接提高美国科技公司在海外建设 AI 数据中心的成本；特朗普同时建议美国本土社区与开发商谈判，争取由开发商向社区付款，以换取接纳数据中心项目。

**标签**: `#US policy`, `#AI infrastructure`, `#data centers`, `#tax policy`, `#US-China tech competition`

---