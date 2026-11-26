---
layout: default
title: "Horizon Summary: 2026-11-26 (ZH)"
date: 2026-11-26
lang: zh
---

> 从 35 条内容中筛选出 10 条重要资讯。

---

**科技新闻**
1. [1Password 确认安全事件，部分客户账户信息遭窃](#item-tech-news-1) ⭐️ 8.0/10
2. [Minecraft Java 版曝高危 RCE 漏洞，1.20.5 起受影响](#item-tech-news-2) ⭐️ 8.0/10
3. [Scott Aaronson 博客指向 9/4 矩阵乘法指数，引发 AI 数学能力激辩](#item-tech-news-3) ⭐️ 7.0/10
4. [Anthropic GRH 形式化出现更短、更易读的 Lean 版本](#item-tech-news-4) ⭐️ 7.0/10
5. [Ubuntu 安全响应迟缓引发 oss-security 与社区讨论](#item-tech-news-5) ⭐️ 7.0/10
6. [SemiAnalysis 发布 GDPx 基准：首日最高分仅 12%](#item-tech-news-6) ⭐️ 7.0/10
7. [腾讯开源 Hy4 flash GGUF 量化权重，最小版可跑在 64 GB Mac mini](#item-tech-news-7) ⭐️ 7.0/10
8. [三星与 SK 海力士据报交叉许可采用长江存储 Xtacking 技术](#item-tech-news-8) ⭐️ 7.0/10

**财经新闻**
1. [法庭文件：美商务部施压英特尔交出 10%股份，政府未付对价](#item-finance-news-1) ⭐️ 9.0/10
2. [美国拟对 14 个贸易伙伴加征第 301 条关税](#item-finance-news-2) ⭐️ 7.0/10

---

## 科技新闻

<a id="item-tech-news-1"></a>
### [1Password 确认安全事件，部分客户账户信息遭窃](https://1password.com/blog/update-on-nov-2026-security-incident) ⭐️ 8.0/10

1Password 确认发生安全事件：攻击者通过被入侵的员工企业 GitHub 账户访问源代码，并向后台服务推送恶意代码，导致部分客户账户信息被下载，包括姓名、邮箱地址、账户标识以及账户创建和最近登录时间。公司表示客户保险库及其内容未受影响，但未披露受影响用户数量。调查始于 11 月 19 日；1Password 已停用涉事账户、轮换或撤销可能暴露的内部凭证，并加强邀请和恢复邮件的验证码。现有用户无需更改账户，但应警惕利用事件信息发起的钓鱼邮件。

hackernews · lxhrstn · 11月25日 17:18 · [社区讨论](https://news.ycombinator.com/item?id=50644817)

**「背景」** 1Password 是托管式密码管理器：客户保险库内容以加密形式保存，而姓名、邮箱、账户标识和登录时间等账户管理数据由后台服务处理。1Password 官方博客称，相关调查始于 2026 年 11 月 19 日，攻击者先控制一名员工的企业 GitHub 账户，再利用该账户访问源代码并向后台服务推送恶意代码。此次事件的关键环节因此是后台管理数据和代码部署链路，而不是客户保险库的加密内容。

**「影响与应对」** 受影响客户面临的主要后果是定向钓鱼风险上升：泄露的数据包含姓名、邮箱、账户标识以及账户创建和最近登录时间，足以让冒充 1Password 的邮件看起来更可信。1Password 表示客户保险库及其内容未受影响，用户无需更改账户，但应警惕伪装成共享保险库链接或账户通知的邮件；社区中已有用户报告收到此类高质量钓鱼邮件，不过尚不能确认其直接源于本次事件。

**「社区讨论」** 评论者认为，员工终端被攻陷后向代码仓库推送并部署恶意代码，是 SaaS 公司最关键的入侵路径之一；有人追问 1Password 是否缺少分支保护、为何能向主分支推送，并希望公司明确说明加密保险库未被下载。另有用户报告收到包含部分个人细节、非官方域名的高质量钓鱼邮件，还有人表示因担忧此类事件而坚持使用仅本地保险库和旧版应用。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://1password.com/blog/update-on-nov-2026-security-incident">Update on a security incident involving 1Password’s backend ...</a></li>
<li><a href="https://1password.com/blog/update-on-nov-2026-security-incident">Update on a security incident involving 1Password’s backend ...</a></li>
<li><a href="https://techcrunch.com/2026/11/25/1password-said-hackers-broke-into-its-internal-systems-but-customer-passwords-are-safe/">1Password said hackers broke into its internal systems, but ...</a></li>

</ul>
</details>

**标签**: `#security-incident`, `#password-managers`, `#saas-security`, `#software-supply-chain`, `#phishing`

---

<a id="item-tech-news-2"></a>
### [Minecraft Java 版曝高危 RCE 漏洞，1.20.5 起受影响](https://github.com/bikini/minecraft2shell) ⭐️ 8.0/10

11 月 22 日公开的 minecraft2shell 利用代码显示，Minecraft Java 版服务器资源包中的特制 TrueType 字体可触发 FreeType 2.14.3 及更早版本的原生越界写，并在 26.3 Windows 客户端上实现任意代码执行。受影响范围为 Java 版 1.20.5 至 1.21.10 以及 26.1 至 26.4 快照，1.20.4 及更早版本和基岩版不受影响。Mojang 仍使用 lwjgl-freetype 3.4.3，暂无官方补丁；社区于 11 月 24 日发布 m2sfix 1.0.0，通过 Java agent 或 mod 关闭 hinting 作为临时缓解。在修复前，用户应避免添加资源包，将多人游戏服务器资源包权限设为“禁用”，或安装该社区临时修复 mod。

telegram · zaihuapd · 11月25日 12:46

**「字体渲染与 hinting」** Minecraft Java 版使用开源字体引擎 FreeType 绘制 TrueType 字体。资源包可提供携带 hinting 指令的字体，这些指令本是用于调整字形以适配像素网格的小程序；当客户端请求绘制字形时，恶意指令会触发 FreeType 的原生内存越界写。

**「处置建议」** 受影响版本的玩家和服务器管理员应在官方补丁发布前避免加载不可信资源包，并在多人游戏设置中将服务器资源包权限设为“禁用”，或部署 11 月 24 日发布的 m2sfix 1.0.0（Java agent 或 mod）关闭字体 hinting；这些只是临时缓解，不能替代 Mojang 修复。公开复现已在 Mojang 签名的 Minecraft 26.3 Windows 客户端上触发本机代码执行，因此连接不受控服务器的客户端面临现实风险。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.cyberkendra.com/2026/11/minecraft2shell-minecraft-java-rce-resource-pack.html">Minecraft2Shell RCE in Minecraft Java Still Unpatched</a></li>
<li><a href="https://wurst.wiki/minecraft2shell">Minecraft2Shell Vulnerability - wurst.wiki</a></li>
<li><a href="https://github.com/bikini/minecraft2shell">GitHub - bikini/ minecraft 2shell: Minecraft to native RCE · GitHub</a></li>

</ul>
</details>

**标签**: `#Minecraft`, `#RCE`, `#FreeType`, `#security vulnerability`, `#community patch`

---

<a id="item-tech-news-3"></a>
### [Scott Aaronson 博客指向 9/4 矩阵乘法指数，引发 AI 数学能力激辩](https://scottaaronson.blog/?p=10379) ⭐️ 7.0/10

计算机科学家 Scott Aaronson 于 2026 年 11 月 25 日发表了一篇标题情绪强烈的博客文章，文中以“另见”形式指向一篇宣称矩阵乘法指数为 9/4 的论文。该文在 Hacker News 上获得 1129 分、953 条评论，讨论很快转向 AI 在数学与科学发现中的能力边界。由于提供的材料只有这条链接和评论摘录，没有博客正文或论文的方法与证明细节，9/4 这一结果在此无法核实，AI 在其中究竟起了什么作用也不清楚。

hackernews · Kotlopou · 11月25日 19:11 · [社区讨论](https://news.ycombinator.com/item?id=50646108)

**「背景：矩阵乘法指数与 AI 数学进展之争」** 这条帖子本身几乎只是一个“see also”指针：Aaronson 链接到一份 PDF，其中主张矩阵乘法指数已达四分之九（ω = 9/4，即 2.25）。ω 是矩阵乘法时间复杂度 O\(n^ω\) 中的指数，长期以来是复杂度理论中渐进改进的目标。据 AI/TLDR 对原文的摘要，Aaronson 称自己此前的文章低估了 AI 目前在硬数学上的进展，并把 ω = 9/4、一份傅里叶变换预印本以及一项 AI 辅助的 QIP\(2\) = PSPACE 证明并列为例子；不过这些内容在本条目提供的源文本里没有技术细节，只能作为转述看待。

**「对矩阵乘法研究的影响」** 对研究快速矩阵乘法的学者来说，OpenAI 的预印本把方阵矩阵乘法的指数 ω 声称推进到 9/4，并声称给出匹配下界；在同行复核前，这应被视为待验证的证明，而不是可直接依赖的复杂度结论。复核时应重点检查下界论证，以及 Lean 形式化实际覆盖了哪些步骤。

**「社区讨论」** 评论者 jsLavaGoat 认为，AI 擅长公理化数学这类分析性先验领域，但这不能推出它同样能“解决”其他学科或带来生存风险；Nevermark 则主张，人类在生物学上无法对如此量级的变化作出相称的反应。sunir 借 Latour 的“计算中心”概念与第谷·布拉赫的例子，把当前进展类比成为下一次科学综合整理数据；utopiah 追问，若只有 Lean、MathLib 和算力而没有 LLM，进展会有多少，并怀疑当下的时机与大型公司为营销而补贴算力有关。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://ai-tldr.dev/releases/scott-aaronson-holy-shit-magnitude-nov25/">Scott Aaronson — &#x27;Holy shit&#x27;: AI math results… | AI/TLDR</a></li>
<li><a href="https://raw.githubusercontent.com/openai/math/main/preprints/The-matrix-multiplication-exponent-is-nine-fourths-November-24-2026/paper.pdf">The matrix multiplication exponent is nine fourths</a></li>
<li><a href="https://kingy.ai/blog/openai-matrix-multiplication-exponent-nine-fourths/">OpenAI Claims Matrix Multiplication Exponent Is Exactly 9/4</a></li>

</ul>
</details>

**标签**: `#AI and mathematics`, `#AI capabilities`, `#scientific discovery`, `#Hacker News discussion`, `#community debate`

---

<a id="item-tech-news-4"></a>
### [Anthropic GRH 形式化出现更短、更易读的 Lean 版本](https://github.com/lsernau/grh-lean) ⭐️ 7.0/10

社区开发者发布了 Anthropic GRH 形式化验证的一个更短 Lean 版本，面向希望审阅这份机器可检查证明的研究者和开发者。Hacker News 讨论中有人称代码量从约 1700 万行降到约 7.6 万行，并保留了“已知数学”与“新数学”的分区及可读文档；该版本旨在让原证明更容易浏览和理解，而非提出新的数学结论。上述行数缩减来自评论者说法，现有材料未独立验证其与 Anthropic 原证明的完整对应关系。

hackernews · nb-t · 11月25日 21:48 · [社区讨论](https://news.ycombinator.com/item?id=50648050)

**「背景」** 广义黎曼猜想（GRH）是黎曼猜想在狄利克雷 L 函数上的推广；Anthropic 此前公布的证明以 Lean 4 完成形式化，维基百科条目记载，发布次日 Lean FRO 与 Mathlib Initiative 宣布独立验证通过。此次的 grh-lean 仓库是在该形式化基础上重写的短版本，作者称其与 Anthropic 同事及 Claude 合作完成，并分为可读版与精简版两个版本。

**「影响」** 对需要审阅或复用这份形式化的研究者和开发者，更短的代码与分区文档能降低导航和人工检查成本；但即使 Lean 代码通过内核检查，也不等于给出了人类可读的数学论证，理解核心思路仍可能需要原论文或专家讲解。

**「社区讨论」** 有评论者称赞新版把“已知数学”和“新数学”分开，并配有便于阅读的文档，认为这有助于消化原证明；另一位评论者则追问，这是否回应了 Tao 一个月前关于“巨大但缺乏洞见的证明是个问题”的观点，以及更聪明的 LLM 是否已能精简并解释证明。还有人希望由真正理解核心论证的数学家写出正式论文并在会议上讲解。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://en.wikipedia.org/wiki/Alp%C3%B6ge&#x27;s_proof_of_the_Riemann_hypothesis">Alpöge&#x27;s proof of the Riemann hypothesis - Wikipedia</a></li>
<li><a href="https://github.com/lsernau/grh-lean">GitHub - lsernau/ grh - lean : A short Lean 4 proof of the Generalized...</a></li>

</ul>
</details>

**标签**: `#Lean`, `#formal verification`, `#mathematics`, `#AI-assisted proof`, `#open source`

---

<a id="item-tech-news-5"></a>
### [Ubuntu 安全响应迟缓引发 oss-security 与社区讨论](https://www.openwall.com/lists/oss-security/2026/11/25/9) ⭐️ 7.0/10

2026 年 11 月 25 日，oss-security 邮件列表出现一篇题为“Slow Ubuntu security response times”的帖子，把 Ubuntu 安全补丁响应速度的问题摆到公开邮件列表上，随后在 Hacker News 引发讨论。素材中没有提供该帖正文，因此具体涉及哪些 CVE、影响哪些 Ubuntu 版本、延迟了多久都无法确认。讨论中的具体说法来自评论者：有人称已因此把服务器镜像迁到 Debian，也有人称一周前为搭建通用 Linux 虚拟机首次放弃 Ubuntu。

hackernews · gslin · 11月25日 20:38 · [社区讨论](https://news.ycombinator.com/item?id=50647181)

**「背景」** 这轮讨论涉及 Ubuntu 如何处理 LTS 内核：oss-security 帖子指出，近期一台 Ubuntu LTS 机器的内核版本为 7.0.0-44，表明 Ubuntu 并未直接采用 kernel.org 的 longterm 内核，而是把补丁回移到较旧的内核版本上。该帖由 Hanno Böck 于 11 月 25 日发到 oss-security 邮件列表，成为讨论 Ubuntu 安全响应速度的起点。

**「对运维的实际影响」** 多名评论者报告了具体的迁移动作：把服务器镜像或通用 Linux 虚拟机从 Ubuntu 换成 Debian。仍留在 Ubuntu 的用户则面临一个配置取舍，评论者 alanfranz 称观察到安全修复常先进入 -updates 仓库、数小时后才进入 security 仓库，因此他不再只对 security 源做无人值守升级，而是安装全部更新并接受“更新弄坏系统”的风险；这是个人经验描述，不是 Canonical 确认的发布流程。

**「社区讨论」** 争论集中在安全响应速度与回归测试之间的取舍：有评论者以 Debian 的一个回归 bug 为例，提醒快速推送补丁本身会带来稳定性风险；另一人引述稳定内核维护者 2025 年的说法，认为必须跟进完整的 stable/LTS 补丁集，挑拣单个补丁反而会留下已知和未知问题。也有评论者质疑，Ubuntu 在这件事上长期迟缓令人费解，并询问是否有自己不了解的原因。以上均为参与者观点，素材中没有 Ubuntu 方面的回应。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.openwall.com/lists/oss-security/2026/11/25/9">oss-security - Slow Ubuntu security response times - openwall.com</a></li>
<li><a href="https://seclists.org/oss-sec/2026/q4/890">oss-sec: Slow Ubuntu security response times</a></li>

</ul>
</details>

**标签**: `#Ubuntu`, `#Linux distributions`, `#security updates`, `#CVE response`, `#Debian`

---

<a id="item-tech-news-6"></a>
### [SemiAnalysis 发布 GDPx 基准：首日最高分仅 12%](https://newsletter.semianalysis.com/p/evaluating-recent-model-releases) ⭐️ 7.0/10

SemiAnalysis 于 11 月 1 日发布 GDPx 基准，用 206 个任务覆盖芯片设计、网络安全、生物、金融、法律、量化交易、递归自我改进、硬件设计、材料科学、对齐和软件工程 11 个领域，并与 14 家专业数据合作伙伴共同制作。该基准刻意不按 GDP 占比或 O\*NET 职业分类选领域，而是聚焦其认为前沿模型影响最大的方向。发布当天最高分的 Opus 5.5 仅得 12%，而许多新基准首发最高分常超过 50%，SemiAnalysis 以此说明 GDPx 仍有区分未来模型的空间。自发布以来 Anthropic、OpenAI、Google、Alibaba 和 Moonshot 均有新模型发布，SemiAnalysis 更新了排行榜；它同时指出 Fable 5.2 和 GPT-6.2 Astra 的安全分类器会拉低总分，并给出排除网络安全、生物、对齐并调整法律和金融评分的替代榜单。

rss · Semianalysis · 11月26日 00:05

**「背景：为何另建一个前沿模型基准」** GDPx 由 SemiAnalysis 于 11 月 1 日发布，其设计出发点是现有综合性智能体基准挑选领域的方式：GDPVal 按占 GDP 比例选行业，Agent&\#x27;s Last Exam 依据 O\*NET 职业分类，而 SemiAnalysis 认为 AI 的经济影响并不均匀分布，应以模型最能发挥作用的领域为衡量对象。这也是 GDPx 舍弃政府、房地产等行业，只覆盖芯片设计、网络安全、生物、金融、法律、量化交易、递归自我改进、硬件设计、材料科学、对齐与软件工程等领域的理由，其 206 道任务由 14 家专业数据合作方制作。文章同时指出 Terminal Bench 4.0 等基准已被头部模型接近打满，难以继续区分新模型的能力差异。

**「影响」** 对需要用基准比较前沿模型的团队来说，GDPx 的低分分布提供了更大的区分空间，但评分口径会直接影响结论：安全分类器可能使模型在网络安全、生物和对齐领域失分，而法律和金融默认二值评分也会损失部分信号。SemiAnalysis 因此同时展示剔除这些领域并采用部分评分的替代排行榜，引用其排名时应说明采用哪一版评分。

**标签**: `#AI benchmarks`, `#model evaluation`, `#frontier models`, `#agentic AI`, `#GDPx`

---

<a id="item-tech-news-7"></a>
### [腾讯开源 Hy4 flash GGUF 量化权重，最小版可跑在 64 GB Mac mini](https://mp.weixin.qq.com/s/o0xxShVQX6g2UllrrEv1WQ) ⭐️ 7.0/10

腾讯混元通过大模型压缩加速工具箱 AngelSlim 开源了 224B 参数模型 Hy4 flash 的 GGUF 量化权重，面向需要在本地运行该模型的开发者。原权重约 410.27GiB，最小的 IQ2-AH 版本为 125.73GiB，约为原版的 30%；腾讯称借助 Strata offload 框架，64 GB Mac mini 也能运行该最小版本。腾讯公布的数据显示，48 GB 显存设备在 10K 上下文下每秒生成 89 个 token，M5 Max 128 GB 上 Q3\_K 版本在 32K 上下文下每秒生成 47 个 token。DeepSWE v1.1 等评测中，Q3\_K 与原模型的得分差距不超过 0.4 分，但这些数字来自发布方，尚缺独立验证。

telegram · zaihuapd · 11月25日 09:29

**「背景」** 据 Hugging Face 模型卡，Hy4 flash 总参数为 220B（含 64B Engram 参数），每个 token 仅激活 12B，原生支持文本与图像输入，上下文窗口最长 1M token；这样的规模使原始权重难以直接加载到个人设备。AngelSlim 是腾讯的模型压缩工具包，提供 FP8 等量化流程，本次 GGUF 权重即通过该工具链发布；IT 之家 的相关报道提到，其原始权重约 410.27 GiB，并给出了 4-bit 量化版本在 16K 上下文下的本地推理速度。

**「本地部署的实际门槛」** 对本地部署者来说，关键限制在于最小 IQ2-AH 权重约 125.73 GiB，远大于 64 GB Mac mini 的统一内存，必须借助 Strata offload 才能运行；而腾讯给出的 89 token/s（48 GB 显存、10K 上下文）和 47 token/s（M5 Max 128 GB、Q3\_K、32K 上下文）都不是该 64 GB 配置的实测数据，选用前需自行验证实际吞吐。若更看重精度，可注意 Q3\_K 在 DeepSWE v1.1 等评测中与原模型差距不超过 0.4 分，但素材未给出该版本体积，按量化位宽推算应明显大于最小版，内存与 offload 压力也会更高。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://huggingface.co/tencent/Hy4-flash">tencent/ Hy 4 - flash · Hugging Face</a></li>
<li><a href="https://www.ithome.com/1/032/131.htm">让大模型跑在个人设备上， 腾 讯 混 元 开源 Hy 4 flash GGUF ...</a></li>
<li><a href="https://github.com/Tencent/AngelSlim">GitHub - Tencent/ AngelSlim : Model compression toolkit engineered for...</a></li>

</ul>
</details>

**标签**: `#腾讯混元`, `#模型量化`, `#GGUF`, `#本地推理`, `#开源模型`

---

<a id="item-tech-news-8"></a>
### [三星与 SK 海力士据报交叉许可采用长江存储 Xtacking 技术](https://tech.ifeng.com/c/8yLRPKxQy4L) ⭐️ 7.0/10

据凤凰网报道，三星电子与 SK 海力士已通过交叉许可协议，同意在 3D NAND 闪存中采用长江存储 Xtacking 堆叠技术的部分内容；三星、SK 海力士和长江存储三方均拒绝置评，因此该协议的范围与是否已实际落地仍未经官方确认。Xtacking 的做法是把存储单元阵列与控制电路（CMOS）分别制作在两片晶圆上，再通过键合工艺合二为一，使两部分可以各自独立生产和优化。Omdia 高级分析师表示，这使厂商能够自行生产存储阵列、把逻辑电路交给晶圆代工厂，从而用上更先进的制程。报道未披露许可的具体技术范围、财务条款或量产时间表。

telegram · zaihuapd · 11月25日 14:33

**「技术背景」** 3D NAND 通过垂直堆叠存储单元来提高密度，而负责读写控制的 CMOS 外围电路通常与存储阵列制造在同一晶圆上。Xtacking 的做法是把存储阵列和逻辑电路分别放在两片晶圆上，再通过键合合为一体，使两部分可以各自选择制程并独立优化；这类晶圆键合被认为是高层数 NAND 提升密度和能效的一条技术路径。

**「影响」** 若该交叉许可最终执行，三星和 SK 海力士可在数百层 3D NAND 中将存储阵列与 CMOS 逻辑分开制造，从而缓解单晶圆工艺的限制，并可能把逻辑部分交给更先进制程的代工厂生产。由于三家公司均拒绝置评、许可范围未披露，客户和供应链目前无法确认哪些产品会采用该技术，也不能把它当作已量产的确定方案。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.trendforce.com/news/2026/11/25/news-sk-hynix-reportedly-joins-samsung-in-licensing-ymtcs-xtacking-technology-as-nand-race-heats-up/">[News] SK hynix Reportedly Joins Samsung in Licensing YMTC’s ...</a></li>
<li><a href="https://www.techpowerup.com/355199/samsung-and-sk-hynix-to-license-ymtcs-xtacking-technology">Samsung and SK hynix to License YMTC&#x27;s Xtacking Technology</a></li>

</ul>
</details>

**标签**: `#3D NAND`, `#Xtacking`, `#semiconductor manufacturing`, `#memory chips`, `#cross-licensing`

---

## 财经新闻

<a id="item-finance-news-1"></a>
### [法庭文件：美商务部施压英特尔交出 10%股份，政府未付对价](https://www.wired.com/story/inside-trumps-demands-to-another-chips-ceo/) ⭐️ 9.0/10

据 WIRED 报道，2025 年 8 月美国商务部律师在电话中告诉英特尔首席财务官，不要“误以为这是一场谈判”，并称董事会可以拒绝，但要承担“无法预测的后果”；数日后，英特尔董事会交出了美方要求的股份。特朗普随后称美国政府“完全拥有并控制”英特尔 10%的股份，且未为此付款，按报道所述该批股份现值约 110 亿美元。

telegram · zaihuapd · 11月25日 13:25

**「背景」** 英特尔在 2025 年 8 月 22 日宣布，美国政府将以每股 20.47 美元认购约 4.333 亿股新发行股票、合计 89 亿美元，对应约 9.9%的股份。上述电话内容出自一起英特尔股东诉讼中被解封的法庭文件。

<details><summary>参考链接</summary>
<ul>
<li>Court records show Commerce told Intel that rejecting a US stake would have consequences | MLQ.ai</li>
<li>Wired: Commerce Lawyer Warned Intel CFO Rejecting US 10% Stake Would Carry &#x27;Unpredictable Consequences&#x27; | AI Weekly</li>

</ul>
</details>

**标签**: `#英特尔`, `#美国政府入股`, `#半导体政策`, `#公司治理`, `#产业政策`

---

<a id="item-finance-news-2"></a>
### [美国拟对 14 个贸易伙伴加征第 301 条关税](https://www.cnbc.com/2026/11/25/us-tariffs-trump-section-301.html) ⭐️ 7.0/10

美国政府拟依据 1974 年《贸易法》第 301 条，对中国、欧盟、日本、印度等 14 个贸易伙伴加征按国别设定的新关税，理由是制造业结构性产能过剩；该计划目前仍是报道中未经立法的拟议措施，尚未公布生效日期。中国将在 2018 年已加征的 25%关税基础上再加 20%，若未遵守 2025 年 10 月在韩国釜山达成的贸易休战协议，对华税率可能升至 40%。

telegram · zaihuapd · 11月25日 13:59

**「背景」** 此次拟议关税依据 1974 年《贸易法》第 301 条，该条款允许美国贸易代表办公室对认定存在不公平贸易行为的贸易伙伴加征关税，本轮调查聚焦靠补贴形成的制造业产能过剩。2025 年 10 月美中在韩国会晤达成贸易休战，美方下调了部分对华关税，该协议正是报道中所提对华关税可能进一步上调的触发条件。

<details><summary>参考链接</summary>
<ul>
<li>USTR Proposes Tariffs Following 14 Section 301 Manufacturing Excess Capacity Investigations | Insights | Holland &amp; Knight</li>
<li><a href="https://www.cfr.org/articles/united-states-and-china-agree-trade-truce">United States and China Agree to Trade Truce | Council on ...</a></li>
<li><a href="https://www.supplychaindive.com/news/us-china-trade-truce-donald-trump-xi-jinping-apec/804233/">US to lower China tariffs as part of trade war truce</a></li>

</ul>
</details>

**标签**: `#US tariffs`, `#Section 301`, `#China-US trade`, `#EU trade`, `#manufacturing overcapacity`

---