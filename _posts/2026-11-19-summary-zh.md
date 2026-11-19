---
layout: default
title: "Horizon Summary: 2026-11-19 (ZH)"
date: 2026-11-19
lang: zh
---

> 从 44 条内容中筛选出 13 条重要资讯。

---

**科技新闻**
1. [谷歌发布 Gemini 4 Neon，主打软件工程与科研](#item-tech-news-1) ⭐️ 9.0/10
2. [Nginx HTTP/2 曝两项未认证远程代码执行漏洞](#item-tech-news-2) ⭐️ 8.0/10
3. [Google DeepMind 发布 Genie 4，订阅资格不明](#item-tech-news-3) ⭐️ 8.0/10
4. [Xint 公开 NGINX2Root：五漏洞可提权至主机 root](#item-tech-news-4) ⭐️ 8.0/10
5. [DNS 不是打击盗版的合适执法点](#item-tech-news-5) ⭐️ 7.0/10
6. [Show HN：旅行者 1 号交互拆解至单颗内存芯片](#item-tech-news-6) ⭐️ 7.0/10
7. [从 4004 到 486：x86 早期架构史](#item-tech-news-7) ⭐️ 7.0/10
8. [微软 Ignite 2026 发布七款新 AI 模型，主打可扩展性价比](#item-tech-news-8) ⭐️ 7.0/10
9. [美政府据悉考虑要求企业公开披露使用中国 AI 模型](#item-tech-news-9) ⭐️ 7.0/10

**财经新闻**
1. [美联储纪要：官员预计进一步加息，并警惕 AI 推升通胀与金融风险](#item-finance-news-1) ⭐️ 8.0/10
2. [美联储理事沃勒称 12 月可能需加息 0.5 个百分点](#item-finance-news-2) ⭐️ 8.0/10
3. [腾讯三季度营收增长 8%低于预期，AI 资本开支升至 814 亿元](#item-finance-news-3) ⭐️ 8.0/10
4. [中韩宣布自贸协定服务与投资后续谈判实质性结束](#item-finance-news-4) ⭐️ 7.0/10

---

## 科技新闻

<a id="item-tech-news-1"></a>
### [谷歌发布 Gemini 4 Neon，主打软件工程与科研](https://blog.google/innovation-and-ai/models-and-research/gemini-models/introducing-gemini-4-neon/) ⭐️ 9.0/10

据 Telegram 帖文，谷歌发布 Gemini 4 Neon，面向复杂软件工程、知识工作与科研工作流，并已向开发者、企业以及 Google AI Pro/Ultra 订阅用户开放。该模型支持 100 万 token 上下文，定价为每百万输入 token 3 美元（缓存输入 0.15 美元）、输出 15 美元。帖文称，Gemini 4 Neon 在 Artificial Analysis 编程智能体指数以 58.6 分排名第一，在智能指数 xhigh 档以 61 分位列总榜第三；Terminal-Bench 4.1 得分 65.2%，在默认 high 档下单任务成本比 Carbon 低 32%。上述性能与成本数据来自该帖文，尚待独立验证。

telegram · zaihuapd · 11月19日 02:00

**「背景」** Gemini 模型通常按能力和用途分成不同型号，并通过开发者 API、企业平台及 Google AI 订阅计划提供；型号名称本身并不直接说明参数规模或代际关系。此次帖子把 Neon 与 Carbon 并列，但未交代 Carbon 的发布时间和具体规格，因此两者的先后关系无法从现有材料确认。

**「按总 token 核算成本」** 对计划迁移的开发者来说，Neon 的单价优势不一定会带来更低的账单：Artificial Analysis 的智能指数评测记录到，Neon 生成了 2.83 亿 token，而中位数约为 6500 万；同时该模型采用显式推理模式，会增加延迟和 token 消耗。因此，上线前应按真实任务测量输入、输出和推理 token 总量及延迟，再与现有模型比较，不能只比较每百万 token 的价格。

**「社区讨论」** 评论中有人抱怨 Google、Anthropic、OpenAI 的模型命名难以对应到具体用途，希望厂商固定一套命名方案；也有用户称，Neon 虽在基准上领先，但实际综合体验仍不如 Opus 5.5。另有评论指出，Neon 在综合智能指数上高于 Carbon，但 Carbon 仍被定位为长周期任务模型；还有人在 OpenRouter 上测得 Neon 约 127 token/秒，远快于 Carbon 的 46 token/秒，并对这一速度与产品定位的关系感到困惑。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://artificialanalysis.ai/models/gemini-4-neon">Gemini 4 Neon Models - Intelligence... | Artificial Analysis</a></li>
<li><a href="https://benchlm.ai/models/gemini-4-neon">Gemini 4 Neon Pricing , Specs &amp; Sources (November 2026)</a></li>

</ul>
</details>

**标签**: `#Google`, `#Gemini`, `#LLM release`, `#software engineering`, `#benchmarks`

---

<a id="item-tech-news-2"></a>
### [Nginx HTTP/2 曝两项未认证远程代码执行漏洞](https://www.wiz.io/blog/nginx-http2-rce-vulnerabilities) ⭐️ 8.0/10

Wiz 报告披露 Nginx HTTP/2 处理中的两项未认证远程代码执行漏洞，编号为 CVE-2026-123633 和 CVE-2026-123007。给定材料未列出具体受影响版本、修复版本或完整的利用条件；暴露面取决于服务器是否显式启用 HTTP/2，而该协议并非 Nginx 默认开启。

hackernews · speedping · 11月18日 15:19 · [社区讨论](https://news.ycombinator.com/item?id=50547374)

**「背景」** NGINX 的 HTTP/2 支持按 server 块配置，关闭时需移除 listen 指令中的 http2 或设置 http2 off，因此漏洞影响面取决于是否启用了该协议。Xint.io 的分析称，CVE-2026-123007 影响从 nginx 1.9.5 到 1.31.8 的所有官方发布版本，且截至 2026 年 11 月 10 日 master 分支仍含易受攻击代码。Wiz 将 CVE-2026-123633 与 CVE-2026-123007 均评为 Critical（CVSS 4.0 9.2）。

**「影响与处置」** 影响集中在启用了 HTTP/2 的 Nginx 实例：评论指出 HTTP/2 并非默认开启，约有 12% 的服务器启用，因此未开启该模块的部署不在这条攻击路径上，运维方在补丁可用前可直接在配置中关闭 http2 来消除暴露面。有评论者称实际利用需要约 128GB 的 HTTP/2 流量和特定 CPU 指令、因而近乎“非问题”，但这属于社区对可利用性的判断，各站点仍应按自身 Nginx 版本与是否启用 HTTP/2 评估风险。

**「社区讨论」** 评论者对实际可利用性存在分歧：有人称利用需要约 128GB 的 HTTP/2 流量和特定 CPU 指令，因此认为风险有限；也有评论者强调 HTTP/2 在互联网规模上仍有约 12% 的服务器使用，并批评修复提交提前一周进入开源仓库却未及时发布禁用 HTTP/2 的临时指引。上述数字和判断均来自评论者，而非独立验证。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://xint.io/blog/nginx2root-remote-code-execution">NGINX 2 Root: New Remote Code Execution Vulnerabilities in nginx ...</a></li>
<li><a href="https://www.wiz.io/blog/nginx-http2-rce-vulnerabilities">Unauthenticated Remote Code Execution in NGINX ... | Wiz Blog</a></li>
<li><a href="https://thehackernews.com/2026/11/10-year-old-nginx-http2-flaw-lets.html">10-Year-Old NGINX HTTP / 2 Flaw Lets Unauthenticated Attackers...</a></li>

</ul>
</details>

**标签**: `#nginx`, `#http/2`, `#remote code execution`, `#vulnerability disclosure`, `#web server security`

---

<a id="item-tech-news-3"></a>
### [Google DeepMind 发布 Genie 4，订阅资格不明](https://blog.google/innovation-and-ai/models-and-research/google-deepmind/genie-4-now-available-project-genie/) ⭐️ 8.0/10

Google DeepMind 宣布 Genie 4 现已可用。一位评论者引述页面称，该产品面向“符合条件的 Google AI Ultra 订阅用户”；该评论者还报告其 Workspace 账户无法开通 Ultra，而非 Workspace 的 Gmail 账户页面显示 Ultra 提供的是 Genie 3，并不确定这与英国地区限制还是页面未更新有关。现有材料没有给出 Genie 4 的能力、价格、版本差异或完整地区支持范围，因此具体可用性仍不清楚。

hackernews · leumon · 11月18日 18:49 · [社区讨论](https://news.ycombinator.com/item?id=50550415)

**「背景」** Genie 是 Google DeepMind 的交互式世界模型项目；评论者提到前代 Genie 3 已通过 Google AI Ultra 订阅层提供，更早的 Genie 版本曾仅限美国。此次发布因此需要先厘清订阅层级、账户类型和地区限制，才能判断谁能实际使用 Genie 4。

**「社区讨论」** 一位评论者报告订阅资格混乱：Workspace 账户无法获得 Ultra，且其英国个人账户页面仍显示 Genie 3，并猜测可能是地区限制或页面未更新。另一位评论者则认为讨论过度聚焦定价与能力，忽视了这类技术的潜在负面后果，同时也有评论者对 DeepMind 的研究动机表示赞赏。

**标签**: `#Google DeepMind`, `#generative AI`, `#world models`, `#AI product availability`, `#Hacker News`

---

<a id="item-tech-news-4"></a>
### [Xint 公开 NGINX2Root：五漏洞可提权至主机 root](https://nginx2root.com/) ⭐️ 8.0/10

据一则 Telegram 帖子，Xint 公开了 NGINX2Root：5 个 nginx 漏洞与 1 个 Linux 内核缺陷可串联，使 nginx 访客获得主机 root。帖子称其中 CVE-2026-123007 是 HTTP/2 流控内存破坏，未认证即可在 worker 中执行命令；nginx 1.30.7 与 1.31.9 已于 11 月 18 日修复 10 个 CVE。帖子还称 Rapid7 已发布 PoC、目前没有已知在野利用，并建议无法升级者关闭对外 HTTP/2；这些说法尚未获得独立验证。

telegram · zaihuapd · 11月18日 16:21

**「背景」** 这次被串联利用的核心缺陷并非近期才引入：据 The Hacker News 报道，CVE-2026-123007 自 nginx 1.9.5（2015 年 9 月 22 日发布）起就存在于开源代码中，直到 1.30.7 和 1.31.9 才修复。F5 在 2026 年 11 月 18 日发布的修复覆盖了研究人员称为 “nginx 2 root” 的五个 nginx 漏洞，管理员被建议升级到 1.31.9。

**「影响与处置」** 无法立即升级到 nginx 1.30.7 或 1.31.9 的运维者，不能只靠关闭对外 HTTP/2 来规避全部风险：该措施只阻断 CVE-2026-123007 和 CVE-2026-123633；其余三个漏洞还需禁用 HTTP/3、避免在请求阶段动态解析上游地址，并停止公网暴露 mail proxy 或对其限制访问。Rapid7 已公开 CVE-2026-123007 的 PoC，暴露在公网的 HTTP/2 服务应优先迁移到修复版本。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://thehackernews.com/2026/11/10-year-old-nginx-http2-flaw-lets.html">10-Year-Old NGINX HTTP / 2 Flaw Lets Unauthenticated Attackers...</a></li>
<li><a href="https://www.ox.security/blog/nginx2root-five-critical-nginx-flaws-expose-web-servers-to-remote-code-execution/">NGINX 2 Root : 5 Critical NGINX RCE Vulnerabilities &amp; CVE Fixes</a></li>
<li><a href="https://www.ox.security/blog/nginx2root-five-critical-nginx-flaws-expose-web-servers-to-remote-code-execution/">NGINX 2 Root : 5 Critical NGINX RCE Vulnerabilities &amp; CVE Fixes</a></li>
<li><a href="https://github.com/sfewer-r7/CVE-2026-123007">GitHub - sfewer-r7/ CVE - 2026 - 123007 : Proof-of-concept ( PoC ) scripts...</a></li>

</ul>
</details>

**标签**: `#nginx`, `#vulnerability disclosure`, `#HTTP/2`, `#remote code execution`, `#security patching`

---

<a id="item-tech-news-5"></a>
### [DNS 不是打击盗版的合适执法点](https://techstackups.com/articles/quad9-leaves-france-dns-blocking/) ⭐️ 7.0/10

一篇分析文章以 Quad9 退出法国为案例，主张 DNS 解析器不应成为打击盗版的执法点。文章的核心论点是，把版权执法推到 DNS 层会让公共解析器承担内容审查职责，却不能替代针对侵权服务的执法。这是一篇政策与基础设施评论，而非新发布的技术能力或独立测量结果。

hackernews · ritzaco · 11月18日 13:18 · [社区讨论](https://news.ycombinator.com/item?id=50545958)

**「背景」** 这起争议的直接前情是法国法院在 beIN Sports 版权案中要求 Quad9 屏蔽 58 个域名；Quad9 未执行，巴黎法院遂于 2026 年 10 月 21 日按每日 1,000 欧元处以罚款，相关命令执行至 11 月 14 日。Quad9 表示无法可靠识别法国用户以仅对法国实施域名屏蔽，并称将于 11 月 24 日停止为法国用户提供服务。

**「对法国用户与解析器生态的影响」** 对法国境内依赖 Quad9（9.9.9.9）进行解析的用户与网络管理员而言，这一决定意味着在 2026 年 11 月 24 日之前必须改用其他解析器，并同时失去 Quad9 提供的隐私保护与恶意域名过滤能力。Cloudflare 将该事件称为「煤矿里的金丝雀」，指出若公共解析器被普遍要求执行域名封锁，其他在法国运营的公共 DNS 服务可能面临同样的封锁令或退出选择，进而加剧解析结果的分裂与不可信。

**「社区讨论」** 评论区中，trentnix 认为不以起诉盗版者为核心的“打击盗版”措施只是压制言论的后门；bemtevi 则主张用无 DRM、按片付费等更好的正版体验来竞争，并称合法观看流程仍然麻烦。skrebbel 追问，问题应归咎于法院的错误裁决，还是法院只是在忠实执行一项不合理的法律。

<details><summary>参考链接</summary>
<ul>
<li>Quad9 Leaves France: Public DNS Resolvers vs Piracy Blocking Orders</li>
<li>Quad9 to stop serving users in France on November 24th - LinkedIn</li>
<li>Quad9 is leaving France, and the hard bit is that both sides have a point</li>
<li><a href="https://techstackups.com/articles/quad9-leaves-france-dns-blocking/">Quad 9 Is Leaving France : Why DNS Resolvers Are... | Tech Stackups</a></li>
<li><a href="https://blog.cloudflare.com/quad9-withdrawal-from-france/">Quad 9 ’s withdrawal from France : A canary in the coal... | Cloudflare Blog</a></li>

</ul>
</details>

**标签**: `#DNS`, `#internet censorship`, `#copyright enforcement`, `#internet infrastructure`, `#Quad9`

---

<a id="item-tech-news-6"></a>
### [Show HN：旅行者 1 号交互拆解至单颗内存芯片](https://rshekhar.com/voyager/) ⭐️ 7.0/10

开发者 raj-shekhar 在 Hacker News 上线了一个交互式网站，可逐层查看旅行者 1 号：从两艘探测器的当前所在位置、核电池的 24 个钚球，到数据计算机内部的单颗内存芯片，以及金唱片封套的播放说明和正在接收信号的地面天线。网站还包含一段 4 分钟影片，并设有“旅行者 1 号如何通过无线电被修复”等专题页面。作者在发布帖中称旅行者 1 号当天距地球一光日；这些内容是对既有任务和硬件的可视化解释，不是新的探测结果。

hackernews · raj-shekhar · 11月18日 16:18 · [社区讨论](https://news.ycombinator.com/item?id=50548161)

**「背景：一光日的距离」** 一光日是光（或无线电波）在真空中行进一天的距离，约合 259 亿公里。NASA 的数据显示，旅行者 1 号于 2026 年 11 月 18 日到达距地球约 160.94 亿英里（259.02 亿公里）处，成为首个达到一光日距离的航天器；这也意味着地面与其通信的单程无线电延迟约为 24 小时。

**「社区讨论」** 评论者称赞这种拆解视角，有人分享金唱片致敬项目及将原始音频解码为图像的脚本；也有评论者追问 CMOS 存储器为何会持续读错，以及网站是否主要由 AI 生成、是否对照过权威资料。作者在评论中补充了核电池、存储器芯片和金唱片封套等直达链接。

<details><summary>参考链接</summary>
<ul>
<li>Voyager 1: What Is a Light-Day - NASA Science</li>
<li>Voyager 1 reaches 1 light-day from earth on november 18 2026</li>
<li>Voyager 1 Passed One Light-Day: Live Distance - Orbital Radar</li>

</ul>
</details>

**标签**: `#Voyager 1`, `#interactive visualization`, `#spacecraft hardware`, `#computer memory`, `#engineering education`

---

<a id="item-tech-news-7"></a>
### [从 4004 到 486：x86 早期架构史](https://pikuma.com/blog/history-of-x86-4004-to-486) ⭐️ 7.0/10

这篇文章按时间线回顾 Intel 从 4004 到 486 的早期 x86 处理器，面向系统与硬件读者梳理具体架构细节，本身不是新品发布或性能测试。Hacker News 讨论对文中若干史实提出修正，涉及小端序的最初动机、8085 的地址/数据复用总线，以及 8008 指令集的设计归属和 4004 与 8008 的关系。由于原始正文不可用，上述范围来自文章摘要与评论，具体技术论断仍应以原文为准。

hackernews · ibobev · 11月18日 14:47 · [社区讨论](https://news.ycombinator.com/item?id=50546967)

**「背景」** x86 指的是源自 Intel 8086、并保持对早期指令向后兼容的指令集家族，这种兼容性使后续处理器能继续运行为旧芯片编写的软件。文章却从 1971 年的 Intel 4004 讲起——它通常被视为第一款微处理器，但并不属于 x86；评论区中 kens 也强调，4004 与后来的 8008 除共享部分设计人员外并无直接设计关系。因此这篇编年史梳理的是从 4004 经 8008、8080 到 8086 乃至 486 的连续演进脉络，而非单一指令集内部的变化。

**「社区讨论」** 评论者主要纠正文中若干历史细节：有人指出小端序最初源于 2200 的数据访问速度考虑，而非算术运算；8085 的地址/数据复用总线也并非独有；还有人强调 8008 指令集曾由 Intel 工程师修改增强，且 4004 与 8008 除参与人员重叠外并无直接继承关系。另有评论质疑现代 x86 为何仍以 1978 年的实模式启动，认为若改为直接进入长模式或 32 位保护模式，主要受影响的只会是 BIOS 编写者。

<details><summary>参考链接</summary>
<ul>
<li>Intel Microprocessor | PPTX - Slideshare</li>
<li>Evolution of Intel Processor Families | PDF | Intel | Microprocessor - Scribd</li>

</ul>
</details>

**标签**: `#x86`, `#CPU architecture`, `#computer history`, `#Intel`, `#retrocomputing`

---

<a id="item-tech-news-8"></a>
### [微软 Ignite 2026 发布七款新 AI 模型，主打可扩展性价比](https://microsoft.ai/news/microsoft-ignite-2026/) ⭐️ 7.0/10

微软在 Ignite 2026 上发布了七款新 AI 模型，官方将这批模型定位为可扩展的性价比选择。提供的材料没有给出各模型的参数规模、具体价格、是否开放权重或上线时间，因此目前只能确认发布数量与定位，无法核实其性能对比或成本优势。

hackernews · gmays · 11月18日 16:08 · [社区讨论](https://news.ycombinator.com/item?id=50548021)

**「背景」** 背景是微软在 Ignite 上集中发布企业 AI 产品，并以自研 MAI 系列参与前沿模型竞争，其中代码模型 MAI Code 2 已在社区讨论中被试用。此次七款模型把卖点放在规模化部署下的价格性能比，而非只强调单项能力；现有材料未披露参数、上下文长度、定价或开放权重，产品分层仍不清楚。

**「对开发者的影响」** 对开发者和企业而言，MAI Code 2 成为一个可纳入选型评测的低成本编码模型选项：微软称其编码质量达到 GPT-6.1 Sol 的 98%、价格约为后者的 40%，相对 Opus 5.5 则达到 96% 的性能而价格仅约 5%。这些是厂商公布的数据，且性能仍非完全持平，团队在替换现有模型前应先在自身代码库与工作负载上验证正确率、延迟和总成本，而不能只比较标价。

**「社区讨论」** 有评论者称自己实际测试了 MAI Code 2，认为其表现不错，并认可微软从零开始做出这样的模型；另一位评论者则主张微软应开放部分模型的源码或权重，否则可能重演 Windows Phone 的市场失败。也有评论从 Anthropic IPO 定价和竞争压力角度讨论此次发布，并对 Ignite 主题演讲的创新性提出尖锐批评，这些都属于个人体验和判断。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://microsoft.ai/news/microsoft-ignite-2026/">Seven new world class models at scalable... | Microsoft AI</a></li>

</ul>
</details>

**标签**: `#Microsoft`, `#LLMs`, `#AI model releases`, `#price-performance`, `#Hacker News`

---

<a id="item-tech-news-9"></a>
### [美政府据悉考虑要求企业公开披露使用中国 AI 模型](https://www.reuters.com/world/china/trump-administration-weighs-forcing-us-firms-disclose-chinese-ai-use-2026-11-18/) ⭐️ 7.0/10

路透社报道，特朗普政府正在考虑要求美国企业公开披露其使用中国 AI 模型的情况；美国财政部与白宫科技政策办公室已讨论该方案。按报道所述，若方案落地，使用阿里 Qwen 支撑客服等业务的企业需在官网公示相关使用情况。此举意在通过“公开点名”减少企业对低价中国开放权重模型的依赖，而非出台新的限制；但该方案是否获得政府内部支持、是否会进入正式立法程序尚不明朗。

telegram · zaihuapd · 11月19日 02:30

**「背景」** 开放权重模型指权重可下载、企业可自行部署的模型；与按调用量付费的闭源 API 相比，这类模型往往能显著压低推理成本。路透社的报道以 Airbnb 使用阿里 Qwen 支撑客服为例，说明披露要求可能覆盖已在实际业务中部署中国模型的企业。

**「实际影响」** 对已把中国模型放进生产环境的企业来说，最直接的变化是模型来源从内部工程细节变成可能需要公开披露的合规信息。路透社提到 Airbnb 用阿里 Qwen 支撑客服；彭博社此前报道称 Airbnb 共使用 13 个 AI 模型但“重度依赖”Qwen，其 CEO Chesky 称其“很好”“快”且便宜，若方案落地，这类企业须在官网公示使用情况，采购与法务团队需要先盘点所用模型的来源与托管方式。该方案目前仍处于讨论阶段，是否获得政府内部支持、能否进入正式立法程序均未确定。

<details><summary>参考链接</summary>
<ul>
<li>Airbnb picks Alibaba&#x27;s Qwen over ChatGPT in a win for Chinese open ...</li>
<li>Airbnb CEO Brian Chesky Called Chinese AI Fast And Cheap. Now ...</li>

</ul>
</details>

**标签**: `#AI regulation`, `#China AI`, `#open-weight models`, `#US tech policy`, `#AI procurement`

---

## 财经新闻

<a id="item-finance-news-1"></a>
### [美联储纪要：官员预计进一步加息，并警惕 AI 推升通胀与金融风险](https://www.cnbc.com/2026/11/18/fed-minutes-october-2026.html) ⭐️ 8.0/10

美联储 10 月会议纪要显示，官员们预计仍需进一步加息以遏制通胀，但当时以 10 票赞成、2 票反对将联邦基金利率目标区间维持在 3.75%-4%，两位反对者支持加息 25 个基点。纪要还称，几乎所有与会者认为进一步加息可能合适，并将 AI 相关需求列为“通胀风险的重要来源”。

rss · CNBC Finance · 11月18日 19:41

**「背景」** 10 月会议后公布的通胀数据显示价格压力仍远高于美联储 2%的目标：10 月消费者价格指数（CPI）环比上涨 0.4%，剔除食品和能源的核心 CPI 环比上涨 0.3%，均比预期高 0.1 个百分点。

**「影响」** 据 CME FedWatch，市场已完全计入 12 月 8 日至 9 日会议加息 25 个基点；若实施，信用卡、汽车贷款等与政策利率挂钩的借贷成本将上升。

**标签**: `#Federal Reserve`, `#monetary policy`, `#interest rates`, `#inflation`, `#AI financial risk`

---

<a id="item-finance-news-2"></a>
### [美联储理事沃勒称 12 月可能需加息 0.5 个百分点](https://www.cnbc.com/2026/11/18/federal-reserve-governor-christopher-waller.html) ⭐️ 8.0/10

美联储理事克里斯托弗·沃勒 11 月 18 日表示，央行可能需要在 12 月 8 日至 9 日的联邦公开市场委员会会议上加息 0.5 个百分点，以“震撼”市场来遏制通胀，并称可能需要逆转去年（2025 年）的三次 25 个基点降息。这一主张并非政策决定，其他美联储官员倾向更渐进的紧缩。

rss · CNBC Finance · 11月18日 15:13

**「背景」** 美联储在 2025 年曾三次降息，但今年通胀在能源价格和关税影响下重新升破 3%，央行已在 9 月进行三年多来的首次加息、10 月按兵不动，12 月会议将决定是否进一步收紧。

**标签**: `#Federal Reserve`, `#interest rates`, `#inflation`, `#monetary policy`, `#Christopher Waller`

---

<a id="item-finance-news-3"></a>
### [腾讯三季度营收增长 8%低于预期，AI 资本开支升至 814 亿元](https://api3.cls.cn/share/article/2537922?os=android&amp;amp;sv=8.8.5&amp;amp;app=cailianpress&amp;amp;selected=) ⭐️ 8.0/10

腾讯公布 2026 年第三季度财报，营收 2073 亿元、同比增长 8%，低于市场预期；归母净利润 636 亿元，同比增长 0.8%。当季资本开支 814.33 亿元，远超市场预估的 554 亿元，单季自由现金流为负 691 亿元；腾讯同时披露，WorkBuddy 日均 Token（模型处理文本的基本单位）用量超过 100 万亿，为国内大语言模型产品第一。

telegram · zaihuapd · 11月18日 09:20

**「背景」** 腾讯营收同比增速已从上一季度的 11%放缓至本季度的 8%，本次三季报的 8%增速延续了这一放缓趋势。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.freemalaysiatoday.com/category/business/2026/11/18/china-tech-giant-tencent-s-quarterly-revenue-growth-slows">China tech giant Tencent ’s quarterly revenue growth slows | FMT</a></li>

</ul>
</details>

**标签**: `#Tencent`, `#earnings`, `#AI capex`, `#free cash flow`, `#China tech`

---

<a id="item-finance-news-4"></a>
### [中韩宣布自贸协定服务与投资后续谈判实质性结束](https://x.com/Jaemyung_Lee/status/2122988472994791476) ⭐️ 7.0/10

中韩双方 11 月 18 日宣布，中韩自贸协定服务与投资后续谈判实质性结束，中国承诺在电影、游戏等领域给予韩国最惠国待遇，即给予韩国不低于任何第三方享有的准入条件，并扩大旅游、法律、建筑、金融等领域开放。据转述，此轮谈判自 2018 年 3 月启动，历时 8 年 8 个月，部分技术事项仍留待工作层面协商。

telegram · zaihuapd · 11月18日 10:02

**「背景」** 中韩自贸协定的服务与投资后续谈判于 2018 年 3 月启动，历时约 8 年 8 个月才实现“实质性结束”，即主要分歧已解决，但部分技术事项仍需在工作层面继续协商敲定。

**标签**: `#China-South Korea FTA`, `#services and investment`, `#trade liberalization`, `#film and games`, `#audiovisual co-production`

---