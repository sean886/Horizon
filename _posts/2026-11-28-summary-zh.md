---
layout: default
title: "Horizon Summary: 2026-11-28 (ZH)"
date: 2026-11-28
lang: zh
---

> 从 31 条内容中筛选出 11 条重要资讯。

---

**科技新闻**
1. [OpenSec 披露 CVE-2026-99362：nfsd 预认证漏洞可获 root](#item-tech-news-1) ⭐️ 8.0/10
2. [购物网站出现利用 WebRTC 的信用卡盗刷脚本](#item-tech-news-2) ⭐️ 7.0/10
3. [证明检查器漏洞如何产生假证明](#item-tech-news-3) ⭐️ 7.0/10
4. [多州总检察长起诉 SpaceX，寻求阻止 Grok 生成儿童性虐待和非自愿私密影像](#item-tech-news-4) ⭐️ 7.0/10
5. [Google Research 提出 DeepCrossAttention，声称最高提速 3 倍](#item-tech-news-5) ⭐️ 7.0/10
6. [SemiAnalysis 深挖 AWS Trainium3 推理与微架构](#item-tech-news-6) ⭐️ 7.0/10
7. [《我的世界》基岩版资源包漏洞影响 26.52 至 26.63，26.65 已修复](#item-tech-news-7) ⭐️ 7.0/10
8. [微软拟用 Windows 内置驱动替代部分第三方驱动](#item-tech-news-8) ⭐️ 7.0/10

**财经新闻**
1. [国常会部署优化中央汇金类“平准基金”功能](#item-finance-news-1) ⭐️ 8.0/10
2. [传 DeepSeek 完成千亿元级二轮融资，蜜雪冰城认缴 5 亿元](#item-finance-news-2) ⭐️ 7.0/10
3. [央行发布大额存单新规：个人起购门槛降至 10 万元](#item-finance-news-3) ⭐️ 7.0/10

---

## 科技新闻

<a id="item-tech-news-1"></a>
### [OpenSec 披露 CVE-2026-99362：nfsd 预认证漏洞可获 root](https://opensec.in/blog/nfs2root-cve-2026-99362) ⭐️ 8.0/10

OpenSec 披露 Linux 内核 NFS 服务器 nfsd 的预认证堆溢出漏洞 CVE-2026-99362，CVSS 评分 9.8；攻击者无需登录，只需向 tcp/2049 发起连接即可越界写入内核堆并获取 root shell。该漏洞自 Linux 3.16 起存在，影响启用 NFSv4.1 或 4.2 的文件服务器、NAS 和集群存储节点。修复版本为 6.12.117、6.18.61、7.3.2 和 7.4-rc1，升级后需重启；CVE 于 2026 年 11 月 20 日公开。

telegram · zaihuapd · 11月27日 12:57

**「背景：nfsd 的内核态暴露面与 NFSv4 复合请求」** NFS 服务端守护进程 nfsd 运行在 Linux 内核中并直接监听 tcp/2049，因此其内存破坏类缺陷在认证之前就能被网络对端触发，危害等同于内核本身被攻破。NFSv4.1/4.2 引入复合请求（compound requests）机制，客户端可在单次连接中连续下发多个操作，其中 SEQUENCE 用于会话与槽位管理。据 Red Hat 的漏洞条目描述，该缺陷正是服务端在协商出极小的缓存回复尺寸后，处理携带 SEQUENCE 操作的构造复合请求时发生越界写。

**「影响与处置」** 无法立即升级的系统应限制 tcp/2049 访问；管理员需核对内核版本并升级到对应修复版本后重启，否则仍暴露的 NFS 服务可能被单条未认证连接利用。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://access.redhat.com/security/cve/cve-2026-99362">CVE-2026-99362 - Red Hat Customer Portal</a></li>
<li><a href="https://app.opencve.io/cve/CVE-2026-99362">CVE-2026-99362 - Vulnerability Details - OpenCVE</a></li>

</ul>
</details>

**标签**: `#Linux kernel`, `#NFS`, `#security vulnerability`, `#CVE-2026-99362`, `#remote root`

---

<a id="item-tech-news-2"></a>
### [购物网站出现利用 WebRTC 的信用卡盗刷脚本](https://www.infohawk.com/news/2026-11-27-black-friday-webrtc-skimmer) ⭐️ 7.0/10

据 Infohawk 报道，一些热门购物网站被发现存在使用 WebRTC 的信用卡盗刷脚本，风险指向电商页面加载的第三方 JavaScript。报道未列出受影响网站、脚本样本或受影响交易数量，因此目前无法确认事件范围，也无法确认是否已发生实际支付数据泄露。由于发布时间接近黑色星期五，这一报告提醒商户检查支付页面的第三方脚本，也提醒购物者在促销季留意支付安全。

hackernews · scanr · 11月27日 15:40 · [社区讨论](https://news.ycombinator.com/item?id=50668145)

**「背景：Magecart 与第三方脚本风险」** Magecart 式网页盗刷（web skimming）指攻击者把恶意代码注入电商结账页所依赖的第三方脚本——分析标签、标签管理器、客服组件或支付 iframe——在付款环节窃取银行卡数据；The Hacker News 的汇总称，Sansec 已统计超过 10 万个站点遭遇此类网页盗刷和供应链攻击。就这次 WebRTC 变种而言，相关报道称涉事脚本已于 11 月 24 日或 25 日从五个站点被移除；connect-src 规则可阻断该脚本在建立 WebRTC 通道前所需的两条 Web 请求。

**「对电商与支付页面的直接影响」** 对在结账页嵌入第三方 JavaScript 的电商站点来说，这意味着仅靠 CSP 一类浏览器端策略可能挡不住数据外传：3 月的分析已记录过利用 WebRTC 数据通道接收载荷并窃取支付数据、从而绕过安全控制的 skim 脚本（tool-3-3）。据报道，Lascana、Samsonite、American Tourister、Revolve 和 FWRD 是在收到研究者通报后才采取处置，说明站点自身并未先行发现植入（tool-3-1）；运维方应审计结账流程中的第三方脚本，并对页面发起的 WebRTC 连接进行监控。

**「社区讨论」** 评论区中，afavour 认为问题不在 WebRTC 的技术能力，而在于它较少受到恶意行为监控，并称嵌入第三方脚本的网站始终存在风险；jszymborski 则把此类攻击视为不应对广告拦截感到内疚的理由。另有评论者建议浏览器应沙箱化广告或不执行广告中的 JavaScript，但这些属于观点和建议，报道并未说明已有此类防护被采用。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://daily.dev/posts/credit-card-skimming-scripts-using-webrtc-found-on-popular-shopping-sites-mr8zgdbaf">Credit card skimming scripts using WebRTC found on...</a></li>
<li><a href="https://thehackernews.com/search/label/Magecart">Magecart — Latest News, Reports &amp; Analysis | The Hacker News</a></li>
<li><a href="https://www.infohawk.com/news/2026-11-27-black-friday-webrtc-skimmer">Credit card skimming scripts using WebRTC found on popular ...</a></li>
<li><a href="https://thehackernews.com/2026/03/webrtc-skimmer-bypasses-csp-to-steal.html">WebRTC Skimmer Bypasses CSP to Steal Payment Data from E ...</a></li>

</ul>
</details>

**标签**: `#web security`, `#credit card skimming`, `#WebRTC`, `#third-party scripts`, `#e-commerce`

---

<a id="item-tech-news-3"></a>
### [证明检查器漏洞如何产生假证明](https://cr.yp.to/proofs/falseccp.html) ⭐️ 7.0/10

cr.yp.to 的文章《False computer-checked proofs》分析证明检查器中的健全性漏洞如何让错误证明通过机器检查。文章强调，计算机检查过的证明并非自动可信，检查器实现本身的缺陷足以破坏结论；这是一篇风险分析，而不是新工具或新版本的发布。对形式验证和证明助理的使用者来说，核心问题是：当证明依赖检查器时，如何评估单一实现出错带来的可信度缺口。

hackernews · \_tk\_ · 11月27日 15:26 · [社区讨论](https://news.ycombinator.com/item?id=50667989)

**「背景」** 这里的“可靠性缺陷”（soundness bug）指检查器错误地接受了实际不成立的证明步骤。相关先例是 Lean 内核 \#14576：一份 AI 辅助的 Collatz 猜想“反证”暴露出内核缺陷，随后出现了修复与复盘；复盘还涉及独立 Rust 检查器 nanoda 为何漏检，以及修复后它能否拒绝这些伪证明。

**「影响」** 对使用 Lean、Metamath 等证明助理的团队而言，实际后果是不能把“通过检查”当作唯一的信任根；采用多个独立实现的检查器并保留人工审查，可以降低单一实现漏洞让错误证明被接受的风险。评论中提到的 Metamath 主数据库要求 5 个独立验证器，就是这种做法的具体例子。

**「社区讨论」** 评论区的核心分歧在于风险应如何表述。twotwotwo 和 dwheeler 认为多检查器架构大幅缩小了实际风险：前者举出 DeepMind 研究员分别利用 Lean 与当时刚发布一周的 nanoda 的不同漏洞构造出通过验证的“证明”，后者指出 Metamath 主数据库要求 5 个不同语言实现的独立验证器；gr\_norm 则强调这些检查器存在多年，其健全性漏洞少到几乎能用一条推文列完，对绝大多数软件已足够，但仍需在验证目标层面保持警惕。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://aitoolly.com/ai-news/article/2026-08-02-lean-kernel-soundness-bug-14576-postmortem-of-the-ai-assisted-collatz-conjecture-disproof-and-fix">Lean Kernel Bug #14576: Postmortem and Technical Analysis | AIToolly</a></li>
<li><a href="https://leodemoura.github.io/blog/2026-8-24-postmortem-for-the-kernel-soundness-bug-hunt/">Postmortem for the Kernel Soundness Bug Hunt — Leonardo de Moura</a></li>

</ul>
</details>

**标签**: `#formal verification`, `#proof assistants`, `#soundness bugs`, `#Lean`, `#Metamath`

---

<a id="item-tech-news-4"></a>
### [多州总检察长起诉 SpaceX，寻求阻止 Grok 生成儿童性虐待和非自愿私密影像](https://www.oag.state.va.us/media-center/news-releases/jay-jones/3162-attorneys-general-jones-and-rayfield-file-suit-against-spacex-parent-company-of-x-xai-and-grok-over-creation-and-promotion-of-child-exploitation-and-non-consensual-images-on-platform) ⭐️ 7.0/10

美国多州总检察长对 SpaceX 提起诉讼，并在案件中将其描述为 X、xAI 和 Grok 的母公司。起诉指控 Grok 被用于生成儿童性虐待材料和非自愿私密影像，并要求法院阻止该产品继续生成此类内容。这些目前只是诉讼主张，尚未经法院认定；现有材料也没有给出参与州的具体数量、完整诉状或 SpaceX 的回应。

hackernews · DeepLogin · 11月27日 19:42 · [社区讨论](https://news.ycombinator.com/item?id=50670855)

**「背景」** Grok 是部署在 X 上的生成式聊天机器人，围绕其图像生成能力的争议在本次诉讼前已经发酵：2026 年 9 月，一名儿童性虐待幸存者起诉 xAI，指其未采用行业通行的防护措施，导致 AI 生成的儿童性虐待材料出现在 X 上并传播；多州总检察长此前也联名致函 xAI，要求立即停止生成未经同意的私密图像和此类材料。此次诉讼正是在这些先前指控和各州监管施压的基础上展开。

**「实际影响」** 对 xAI 与 X 而言，这起诉讼说明即使没有专门针对生成式 AI 的新立法，各州总检察长也可以援引现有的消费者保护、儿童安全和刑事执法权限，追究图像生成功能造成的后果；但法律分析同时指出，第一修正案与 Section 230 会限制可获得的救济以及可起诉的对象，因此诉讼能否成立仍不确定。对开发者的直接压力在于，Grok 的图像生成需要具备阻止生成真实人物未经同意的私密图像和儿童性化内容的防护，而不能只靠事后删除来应对州级执法。

**「社区讨论」** 评论中，有人怀疑 Grok 此前是否已被各平台广泛禁止，以及用户是否需要刻意绕过限制；也有人追问制作和传播这些图像的人应承担什么责任。另有评论者声称，美国最高法院已裁定个人用 AI 制作儿童性虐待材料属于受保护言论，但这是评论者说法，未经来源证实，也不等同于法院已对本案指控作出判断。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.theguardian.com/technology/2026/sep/03/elon-musk-ai-grok-child-porn-lawsuit">Child sexual abuse survivor alleges Elon Musk’s AI... | The Guardian</a></li>
<li><a href="https://www.tapinto.net/towns/phillipsburg/sections/around-new-jersey/articles/acting-ag-davenport-demands-immediate-action-from-xai-to-stop-production-of-nonconsensual-intimate-images-and-child-sexual-abuse-material">Acting AG Davenport Demands Immediate Action from xAI to... | TAPinto</a></li>
<li><a href="https://www.lexology.com/library/detail.aspx?g=8ac74728-f1b0-423a-be4e-f714c3a6d402">Abusive Images Are Posted on an Online Platform —Now... - Lexology</a></li>
<li><a href="https://factually.co/fact-checks/justice/state-attorneys-general-online-nonconsensual-sexual-imagery-remedies-08ecba">How have U.S. state attorneys general historically han...</a></li>

</ul>
</details>

**标签**: `#AI governance`, `#generative AI`, `#content safety`, `#platform liability`, `#xAI/Grok`

---

<a id="item-tech-news-5"></a>
### [Google Research 提出 DeepCrossAttention，声称最高提速 3 倍](https://research.google/blog/supercharging-transformer-residual-connections/) ⭐️ 7.0/10

Google Research 在博客中提出 DeepCrossAttention，声称在模型质量相当的情况下最高快 3 倍。该技术被定位为对 Transformer 残差连接的改进，但现有摘要未说明这是训练还是推理场景，也没有给出方法细节、基准设置或可复现实验。因此，3 倍加速目前仍是待验证的厂商说法，无法据此判断其技术深度或适用范围。

hackernews · ComputedCamp995 · 11月27日 23:06 · [社区讨论](https://news.ycombinator.com/item?id=50672565)

**「背景」** Transformer 的标准残差连接把各层输出按固定方式相加，在深层网络中可能造成早期层信息被稀释。DeepCrossAttention（DCA）改用可学习、依赖输入的权重，并通过跨层注意力动态组合此前各层的输出，让模型逐 token 选择相关信息；该方法的 arXiv 论文于 2025 年 2 月公开，Google Research 此次博客则集中介绍这一架构。

**「影响」** 在缺少方法细节和基准结果的情况下，开发者无法判断 DeepCrossAttention 是否适用于自己的训练或推理负载；在论文、代码或可复现实验公布前，宜将其视为待验证的效率主张。

**「社区讨论」** 评论中有人指出，性能对比不应使用折线图而应使用柱状图，因为各方法之间没有时间关系；其他评论多为订阅价格跑题、标题更正或简短提问，未形成实质性的技术辩论。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://research.google/blog/supercharging-transformer-residual-connections/">Supercharging transformer residual connections - Google Research</a></li>
<li><a href="https://arxiv.org/abs/2502.06785">[2502.06785] DeepCrossAttention: Supercharging Transformer ...</a></li>
<li><a href="https://explainx.ai/blog/google-deepcrossattention-transformer-residual-connections-2026">DeepCrossAttention (DCA): Google Fix for Deep Transformers ...</a></li>

</ul>
</details>

**标签**: `#transformer architectures`, `#attention mechanisms`, `#model efficiency`, `#Google Research`, `#LLM training`

---

<a id="item-tech-news-6"></a>
### [SemiAnalysis 深挖 AWS Trainium3 推理与微架构](https://newsletter.semianalysis.com/p/trainium3-inferencex) ⭐️ 7.0/10

SemiAnalysis 发布了对 AWS Trainium3 推理路线与微架构的深度分析，称 Trainium3 与 TPU 已上线其 InferenceX 基准平台，在生成 token 的总拥有成本（TCO）上与 Nvidia GB300「互有胜负、甚至胜出」。作者给出的技术依据是：Trainium 的 Descriptor Generation Engine（DGE，对位 Nvidia TMA 与 AMD MI455X TDM）在其微基准中让小消息尺寸即可打满 HBM 带宽利用率（MBU），作者称这在 Nvidia GPU 上做不到；同时 Trainium 微架构把 tile 当作一等原语，而不是在大量线程之上外挂张量计算与数据搬运单元，作者称这曾让软件生态极为困难，但「现在不再是问题」。文章还称 Trainium3 配合 PDS 与 vLLM，在整条 TCO 对 p90 交互性曲线上，每美元性能优于除 Vera Rubin 之外的所有加速器。需要说明的是，这些结果出自 SemiAnalysis 自建的 UBenchX 微基准与 AgentX 智能体会话回放，AWS Annapurna Labs 团队参与了架构讲解与实验验证，因此属于厂商协助校准的第三方分析；所给摘录未包含具体数值，不构成可独立复现的结论。

rss · Semianalysis · 11月27日 15:54

**「背景」** Trainium 是 AWS 自研的机器学习加速器产品线，Trainium3 的前代是 Trn2 UltraServers；AWS 声称，基于 Trainium3 的 Trn3 UltraServers 最高可带来 4.4 倍性能、3.9 倍内存带宽和 4 倍每瓦性能提升\[tool-2-3\]。SemiAnalysis 这次把 Trainium3 纳入其 InferenceX 推理基准，并用 UBenchX 做微基准，重点分析 DGE 等面向 tile 的硬件设计；这与 Nvidia 数据中心 GPU 从图形渲染管线出发、逐代加装 Tensor Core、TMA 和 Tensor Memory 的路线形成对照。

**「成本与带宽取舍」** 对于以单位 token 成本为主要指标的推理团队，SemiAnalysis 的 AgentX 回放基准显示，Trainium3 在 agentic 负载下每美元性能最高可达 Nvidia GB300 NVL72 的 2.28 倍，芯片小时价约为 1.05 美元对 2.31 美元；在已适配 vLLM 的模型上，迁移可能带来明显的单位推理成本下降。但 Trainium3 每芯片 HBM 带宽为 4.9 TB/s，约为 GB300 8.0 TB/s 的 61%，因此在解码等内存受限、低延迟场景中，成本优势仍需按实际 batch 和交互性目标核算。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://aws.amazon.com/ec2/instance-types/trn3/">Gen AI Compute Instance - Amazon EC2 Trn3 UltraServers - AWS</a></li>
<li><a href="https://newsletter.semianalysis.com/p/trainium3-inferencex">AWS Challenger: Trainium3 Inference and Microarchitecture ...</a></li>
<li><a href="https://cryptobriefing.com/trainium3-nvidia-gb300-inference-benchmark/">Trainium3 competes with Nvidia GB300 in inference performance ...</a></li>
<li><a href="https://www.kucoin.com/news/flash/amazon-trainium3-outperforms-nvidia-gb300-in-cost-efficiency-for-ai-inference">Amazon Trainium3 Outperforms Nvidia GB300 in Cost ... - KuCoin</a></li>

</ul>
</details>

**标签**: `#AWS Trainium`, `#AI hardware`, `#inference`, `#microarchitecture`, `#custom silicon`

---

<a id="item-tech-news-7"></a>
### [《我的世界》基岩版资源包漏洞影响 26.52 至 26.63，26.65 已修复](https://www.zaikei.co.jp/article/20261119/878386.html) ⭐️ 7.0/10

《我的世界》基岩版存在资源包漏洞：带有 content.zipe 文件的资源包能修改 Ore UI 界面框架的文件并运行隐藏脚本，已确认影响 26.52 至 26.63 版本，更早版本也可能受影响，涉及 PC、手机和主机，Java 版不受影响。玩家加入服务器或 Realm 并开启资源包自动下载时，可能在未手动安装的情况下收到问题文件；8Crafter 列举的利用方式包括删除全部存档、获取玩家 IP，以及在 Windows 上特定条件下无提示打开任意 URI、启动资源包内的批处理文件下载恶意软件。Mojang 已在 26.65 版修复。AxmBro 发布的 Windows 只读检测工具可以查找 content.zipe，但不能判定资源包是否恶意。

telegram · zaihuapd · 11月27日 18:04

**「背景」** 《我的世界》基岩版允许玩家在加入服务器或 Realm 时按设置自动下载并启用资源包，而资源包可包含 content.zipe 等打包内容；Ore UI 则是基岩版用于构建游戏界面的框架。正因资源包能够触及界面层，问题资源包才可能影响 Ore UI 文件并执行隐藏脚本，而不只是替换材质。

**「升级与防护」** 仍停留在 26.52–26.63 的基岩版玩家，在加入开启资源包自动下载的服务器或 Realm 时可能被动收到恶意资源包，从而面临存档被删除、IP 暴露等风险；应优先升级到 26.65，无法升级时关闭自动下载。Windows 用户可用 AxmBro 的只读检测工具查找 content.zipe，但该工具只能发现可疑文件，不能判断资源包是否恶意。

<details><summary>参考链接</summary>
<ul>
<li>Minecraft Bedrock 26.65: the resource pack security fix - KAIMUX Network</li>
<li>Minecraft Bedrock Malware Flaw: Update, Scan, Back Up</li>

</ul>
</details>

**标签**: `#Minecraft Bedrock`, `#security vulnerability`, `#resource packs`, `#malware`, `#game security`

---

<a id="item-tech-news-8"></a>
### [微软拟用 Windows 内置驱动替代部分第三方驱动](https://www.techspot.com/news/114721-microsoft-wants-replace-most-third-party-device-drivers.html) ⭐️ 7.0/10

微软在 Ignite 2026 上确认，正为整类硬件开发新的 Windows 内置驱动，以减少进入系统内核的第三方代码；打印机是首批重点，近期推出的 Windows Ready Print 模式将取代旧式第三方打印驱动。Windows 产品经理 Mehmet Kucukgoz 表示，SoundWire、SDCA 等音频驱动将很快成为 Windows 内置组件，I3C 总线、USB 以太网和 MIPI 摄像头驱动仍在开发中。微软还推出驱动质量倡议（DQI），以提高驱动可靠性、质量和安全标准，并鼓励第三方开发者及 OEM 尽量采用内置驱动。上述音频、总线和摄像头驱动目前属于开发或计划阶段，微软未给出完成时间。

telegram · zaihuapd · 11月28日 02:09

**「背景」** Windows 的设备驱动需要与内核及系统组件配合工作，第三方驱动因此成为系统稳定性和安全性的重要环节。微软此次把打印机列为首批重点，以 Windows Ready Print 取代旧式第三方打印驱动，并表示音频、I3C 总线、USB 以太网和 MIPI 摄像头等整类驱动也在转为内置；配套的驱动质量倡议（DQI）则要求第三方和 OEM 定制驱动遵循更高的可靠性与安全标准。

**「影响」** 对打印机、音频、USB 以太网和摄像头设备厂商及企业 IT 而言，部分第三方驱动包可能被系统内置功能替代，部署时需重点验证依赖厂商自定义功能的设备；微软目前只说明了驱动类别和 DQI 方向，未公布各类内置驱动的完成时间或兼容性清单。

**标签**: `#Windows`, `#device drivers`, `#kernel security`, `#Microsoft`, `#hardware ecosystem`

---

## 财经新闻

<a id="item-finance-news-1"></a>
### [国常会部署优化中央汇金类“平准基金”功能](https://www.tmtpost.com/nictation/8220182.html) ⭐️ 8.0/10

国务院总理李强 11 月 27 日主持召开国务院常务会议，提出加力发挥“国家队”稳市作用、进一步优化中央汇金公司的类“平准基金”功能并提供充足流动性保障，同时完善保险、企业年金、社保基金等中长期资金入市支持引导政策。会议还要求推动上市公司加大分红回购力度，并依法查处财务造假、违规减持等行为。

telegram · zaihuapd · 11月27日 05:35

**「背景」** 中央汇金公司被市场视为资本市场“国家队”的主要成员，其类“平准基金”作用是指在市场波动时入市提供流动性、稳定预期。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://36kr.com/p/3242170090487424">A股 史 上最强“ 稳 市 组合拳”，脉络清晰了-36氪</a></li>

</ul>
</details>

**标签**: `#资本市场`, `#国常会`, `#中央汇金`, `#平准基金`, `#中长期资金`

---

<a id="item-finance-news-2"></a>
### [传 DeepSeek 完成千亿元级二轮融资，蜜雪冰城认缴 5 亿元](https://m.sohu.com/a/1107027659_115479) ⭐️ 7.0/10

据搜狐网报道，DeepSeek 已完成第二轮融资，规模在 1000 亿至 1055 亿元人民币之间，投后估值约 6155 亿元人民币；该报道未获公司确认。报道称新增 31 家出资人中包括腾讯、宁德时代、中国移动和 vivo，蜜雪冰城股份有限公司认缴 5 亿元，并通过天津砺思星深基金投入。

telegram · zaihuapd · 11月27日 06:33

**「背景」** 今年 5 月，DeepSeek 启动首次融资，计划募资约 73 亿美元，对应估值 500 亿美元以上；6 月有报道称首轮实际募资超过 74 亿美元、估值超过 500 亿美元，公司并计划将员工规模翻倍，本轮是继此之后的第二轮融资。

<details><summary>参考链接</summary>
<ul>
<li>DeepSeek seeks ~$7.3B in first-ever funding round at $50B+ valuation | Dealroom News</li>
<li>DeepSeek Looks to Double Workforce as Fresh Funding Fuels Growth - WSJ</li>

</ul>
</details>

**标签**: `#DeepSeek`, `#AI financing`, `#Mixue Bingcheng`, `#China venture capital`, `#Tech investment`

---

<a id="item-finance-news-3"></a>
### [央行发布大额存单新规：个人起购门槛降至 10 万元](https://www.news.cn/fortune/20261127/70789d77822242cc82216f51a416f872/c.html) ⭐️ 7.0/10

中国人民银行 11 月 27 日公布《大额存单管理办法》，将个人投资人认购起点从不低于 20 万元下调至不低于 10 万元，机构门槛从 1000 万元降至 500 万元，自 2027 年 3 月 21 日起施行。

telegram · zaihuapd · 11月27日 11:36

**「背景」** 大额存单是银行面向个人和机构发行的大额存款凭证，原有 20 万元和 1000 万元的门槛由 2015 年《大额存单管理暂行办法》规定，此次两个门槛都减半，新办法同时废止该暂行办法和 2016 年第 13 号公告。

**「影响」** 门槛下调后，存款在 10 万元至 20 万元之间的个人储户也可认购大额存单；同日发布、同样自 2027 年 3 月 21 日起施行的《人民币存贷款利率管理规定》要求金融机构自主确定存贷款利率、不得通过高息揽储等不正当手段吸收存款，这将约束银行以抬高利率争抢存款的空间。

**标签**: `#央行新规`, `#大额存单`, `#存款利率`, `#银行业监管`

---