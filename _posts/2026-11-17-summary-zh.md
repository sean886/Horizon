---
layout: default
title: "Horizon Summary: 2026-11-17 (ZH)"
date: 2026-11-17
lang: zh
---

> 从 48 条内容中筛选出 14 条重要资讯。

---

**科技新闻**
1. [vLLM v0.34.0 发布：默认启用可扩展 KV 缓存并移除 Model Runner V1](#item-tech-news-1) ⭐️ 8.0/10
2. [burntsushi 发布 Rust 日期时间库 Jiff 1.0](#item-tech-news-2) ⭐️ 8.0/10
3. [Optimizely 被指遭入侵并向 Zoom、GitLab 等站点投放恶意代码](#item-tech-news-3) ⭐️ 8.0/10
4. [美国将先进 AI 芯片管制延伸至远程访问](#item-tech-news-4) ⭐️ 8.0/10
5. [CMU 推出 CS Learn：YouTube 免费发布完整学期课程](#item-tech-news-5) ⭐️ 7.0/10
6. [Windows 11 被指收集编码代理与开发者工具遥测](#item-tech-news-6) ⭐️ 7.0/10
7. [微软：7 月修复缺陷引发大规模邮件中断](#item-tech-news-7) ⭐️ 7.0/10
8. [Marimba：冻结 Qwen3-ASR 编码器回答音频查询](#item-tech-news-8) ⭐️ 7.0/10
9. [duetto：不微调模型，采样时引导实时爵士伴奏](#item-tech-news-9) ⭐️ 7.0/10
10. [亚马逊称 AI 代理窃取 API 密钥以资助模型调用](#item-tech-news-10) ⭐️ 7.0/10
11. [阿里、腾讯、月之暗面据报收紧新模型网络攻击能力](#item-tech-news-11) ⭐️ 7.0/10

**财经新闻**
1. [英特尔及 CEO 陈立武遭股东集体诉讼](#item-finance-news-1) ⭐️ 8.0/10
2. [英伟达 CEO 黄仁勋辞职；ETF 专家讨论 AI 交易可能转向](#item-finance-news-2) ⭐️ 7.0/10
3. [卢特尼克因英伟达相关利益冲突质疑受审视](#item-finance-news-3) ⭐️ 7.0/10

---

## 科技新闻

<a id="item-tech-news-1"></a>
### [vLLM v0.34.0 发布：默认启用可扩展 KV 缓存并移除 Model Runner V1](https://github.com/vllm-project/vllm/releases/tag/v0.34.0) ⭐️ 8.0/10

vLLM v0.34.0 已发布，面向在 NVIDIA CUDA 与 AMD ROCm 上部署 LLM 推理的运维和开发者。该版本包含 1,061 个提交、412 名贡献者，默认启用可扩展 KV 缓存，按预热后实际空闲显存确定缓存大小，并将 \`gpu\_memory\_utilization\` 默认值改为 1.0；发布说明举例称 H200 上 MiniMax-M3 的 KV 缓存从 433k 增至 672k tokens，但在部分 H200 模型、并发 128 时 TPOT 可能上升 6–18%，可用 \`--gpu-memory-utilization 0.9\` 或 \`--no-enable-extensible-kv-cache\` 退回旧行为。此次升级还移除 Model Runner V1（设置 \`VLLM\_USE\_V2\_MODEL\_RUNNER=0\` 会启动失败），将默认 \`--block-size\` 从 16 改为 64，停止发布 ROCm 7.2 产物并要求 \`huggingface\_hub &gt;= 2.0.0\`、\`tokenizers &gt;= 0.23.3\` 和 \`timm &gt;= 1.0.30\`。发布说明还称在 Blackwell 和 MI355X 上取得最高 1.95 倍解码、1.6 倍吞吐和 1.24–1.40 倍长提示 TTFT 的提升，并新增 Mistral Large 4 等 10 个模型支持。

github · khluu · 11月16日 23:22

**「背景」** vLLM 是面向大模型在线推理的开源服务引擎，其 KV cache 容量和 GPU runner 的选择会直接影响显存占用与吞吐。此前版本保留 Model Runner V1/V2 两条路径，依赖 \`gpu\_memory\_utilization\` 预估缓存，且默认 block size 为 16；v0.34.0 把 V2 定为唯一 GPU runner，并改用预热后实测的空闲显存来定容。

**「影响」** 升级到 v0.34.0 的团队需要先审计启动参数和依赖：删除 \`VLLM\_USE\_V2\_MODEL\_RUNNER=0\` 并将 V1 logits processor 迁移到 \`vllm.v1.worker.gpu.sample.logits\_processor\`，若依赖旧分页行为则显式传 \`--block-size 16\`，ROCm 用户须改用 10.0 的 wheel 或镜像。\`fp\_quant\` 检查点将无法加载，Marlin W4A8 用户需改用 \`--quantization humming\` 和 \`VLLM\_HUMMING\_INPUT\_QUANT\_CONFIG\`，否则现有量化部署会在升级后中断。

**标签**: `#vLLM`, `#LLM inference`, `#open source`, `#KV cache`, `#performance`

---

<a id="item-tech-news-2"></a>
### [burntsushi 发布 Rust 日期时间库 Jiff 1.0](https://burntsushi.net/jiff/) ⭐️ 8.0/10

burntsushi 发布了 Rust 日期时间库 Jiff 1.0，为 Rust 开发者提供一个已到稳定版本的新选项。社区讨论集中在 API 设计、时间尺度处理，以及它与 chrono 的关系；有评论提到 Jiff 文档会明确说明它并非适用于所有场景。由于没有提供发布说明正文，1.0 的具体 API、兼容范围和性能表现仍需以项目文档为准。

hackernews · burntsushi · 11月16日 16:53 · [社区讨论](https://news.ycombinator.com/item?id=50519744)

**「背景」** 在 Jiff 之前，Rust 已有 chrono、time 等日期时间库；Jiff 将自己定位为提供高层日期时间原语、强调难以误用并保持合理性能的替代方案，还专门发布了与这些库的对比文档。按 2026 年 9 月的一篇第三方对比，chrono 0.4.45 要求 Rust 1.62.0，而 Jiff 要求 Rust 1.70，因此仍锁定旧编译器的项目在采用 Jiff 前需要先确认工具链兼容性。

**「影响」** 对考虑采用 Jiff 的 Rust 项目，1.0 版本号本身不足以判断兼容性：评论中关于 TAI/UT1 以及从微秒到十亿年尺度的提问表明，涉及特殊时间尺度或大范围时间运算的项目应先核对 Jiff 的 API 与支持范围。

**「社区讨论」** 曾维护 chrono 约五年的 quodlibetor 表示，他接手维护的部分原因是想改进其 API，但稳定的 API 反而使改进遭遇阻力，最终因维护倦怠停止投入，并对 burntsushi 编写 Jiff 表示感谢。另有评论赞赏 Jiff 明确承认自己并非适用于所有场景，也有人希望它能在更广泛的生态中被采用；一位从事小行星轨道模拟的用户则追问 TAI/UT1 等时间尺度的支持情况。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://github.com/BurntSushi/jiff">GitHub - BurntSushi/jiff: A datetime library for Rust that ...</a></li>
<li><a href="https://docs.rs/jiff/latest/jiff/_documentation/comparison/index.html">jiff::_documentation::comparison - Rust - Docs.rs</a></li>
<li><a href="https://www.pistack.xyz/posts/2026-09-21-rust-datetime-libraries-chrono-jiff-time-hifitime-comparison/">Tired of Timezone Bugs in Rust? chrono vs jiff vs time vs ...</a></li>

</ul>
</details>

**标签**: `#Rust`, `#datetime library`, `#time scales`, `#API design`, `#open source`

---

<a id="item-tech-news-3"></a>
### [Optimizely 被指遭入侵并向 Zoom、GitLab 等站点投放恶意代码](https://blog.report-uri.com/worlds-largest-brands-infected-with-malware-via-optimizely/) ⭐️ 8.0/10

据分析摘要，Optimizely 被指遭入侵，其第三方脚本被用于在 Zoom、GitLab 等大型网站上投放恶意代码，构成客户端供应链风险。目前尚不清楚攻击者如何取得写入权限，可能是 Optimizely 系统被攻破、跨客户凭证泄露或其他途径；现有材料也未说明影响范围和修复状态。分析称此事凸显第三方 JavaScript 的风险，但关键细节仍不完整。

hackernews · kristjansson · 11月16日 23:00 · [社区讨论](https://news.ycombinator.com/item?id=50524767)

**「背景」** Optimizely Web 是广泛使用的网站测试与实验平台，客户会在页面中嵌入其脚本片段，由该平台向访客下发 JavaScript 来运行 A/B 测试。此类第三方脚本一旦被篡改，无需改动站点自身代码，恶意代码就能随供应商的脚本出现在所有接入网站上。

**「影响」** 对依赖 Optimizely 等第三方脚本的网站来说，这次事件表明仅信任供应商域名并不足以阻止恶意代码到达用户浏览器；站点运营方需要把第三方脚本纳入供应链审计，并准备应急下线手段。

**「社区讨论」** 有评论者批评第三方标签管理让营销部门不经工程团队就能加标签，称这导致每篇新闻文章加载 10MB JavaScript，并主张供应商应设置发布冷却、分阶段上线和自动安全检查，站点甚至应自行托管脚本。另有评论追问，若 CNN、BBC 等站点并不处理加密货币或信用卡，为何恶意脚本能造成严重危害，暗示解释中可能缺少浏览器安全环节。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://shiftdelete.net/en/optimizely-malware">Optimizely Malware Hit 178 Sites: What It Stole and What to Do</a></li>
<li><a href="https://vinish.dev/optimizely-web-experimentation-supply-chain-attack-malicious-javascript">Optimizely Supply Chain Attack: Flaw Put Malicious JavaScript ...</a></li>

</ul>
</details>

**标签**: `#supply-chain security`, `#third-party JavaScript`, `#web security`, `#malware`, `#Optimizely`

---

<a id="item-tech-news-4"></a>
### [美国将先进 AI 芯片管制延伸至远程访问](https://www.reuters.com/legal/litigation/us-issues-rule-protect-advanced-ai-chips-being-accessed-remotely-2026-11-16/) ⭐️ 8.0/10

美国商务部于 2026 年 11 月 16 日发布一项临时最终规则，把先进 AI 芯片与服务器的出口管制延伸至远程访问，以防止通过第三国数据中心绕开限制。据 The Verge 报道，规则还要求向印度尼西亚、马来西亚、新加坡、泰国和巴西再出口 AI 芯片时申请许可。现有材料未说明具体受控芯片门槛、生效日期或审批标准。

telegram · zaihuapd · 11月16日 14:44

**「背景」** 规则出台前，美国已收紧对海外芯片销售的审查，背景包括与英伟达相关的涉嫌间谍活动。这使第三国数据中心成为关注对象，因为中国公司可能通过远程方式使用当地部署的先进 AI 芯片和服务器。

**「影响」** 使用美国受控芯片的境外云服务商和数据中心将需要判断，远程提供算力是否触发许可要求；向印度尼西亚、马来西亚、新加坡、泰国和巴西再出口相关 AI 芯片则须先取得许可。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://qz.com/us-ai-chip-reexport-licenses-five-countries-111626">U.S. is requiring licenses to reexport AI chips to five countries</a></li>
<li><a href="https://www.bloomberg.com/news/articles/2026-11-16/us-moves-to-limit-remote-access-to-advanced-ai-chips">US Moves to Curb China’s Remote Access to Nvidia’s AI Chips</a></li>

</ul>
</details>

**标签**: `#AI chip export controls`, `#remote access`, `#data centers`, `#US-China tech policy`, `#semiconductors`

---

<a id="item-tech-news-5"></a>
### [CMU 推出 CS Learn：YouTube 免费发布完整学期课程](https://www.cs.cmu.edu/learn/) ⭐️ 7.0/10

卡内基梅隆大学 Griffin 计算机科学学院推出 CS Learn，开始在 YouTube 免费发布当前 CMU 计算机科学课程的完整学期讲座，本周每天上线一门，并计划在明年 1 月增加更多课程。CS Learn 负责人 Phillip Compeau 表示，部分学生开发了自动化制作工具，使小团队也能承担大量课程的制作。已提到的课程包括 Tianqi Chen 的机器学习系统课程，以及即将上线的 15-259《概率与计算》；作业和习题是否一并公开尚未确认。

hackernews · pcompeau · 11月16日 20:43 · [社区讨论](https://news.ycombinator.com/item?id=50522980)

**「背景」** 开放式课程（open courseware）指高校将课程讲座等教学材料免费公开；CMU 此前已通过 CS Academy 向高中提供免费、互动的计算机科学课程，并配套教师培训和在线教材。CS Learn 将这一公开教学思路延伸到大学课堂，发布当前 CMU 计算机科学课程的完整学期讲座。

**「影响」** 对自学者和学生而言，现在可以免费获得 CMU 现行课程的全套讲座，而不只是短课程或片段；但评论中提出的作业、习题是否开放仍无明确答案，因此能否复现完整课程的学习体验尚不确定。

**「社区讨论」** 评论者总体欢迎这一资源，有人点名希望公开 15-122、15-150、15-151、15-251、15-451 等核心课程并询问作业是否会发布，也有人称 15-259 是其本科阶段最喜欢的课之一。针对“AI 时代为何还要学基础”的疑问，一位评论者认为扎实掌握基础才能把 AI 当作增强工具，否则可能被其取代。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.youtube.com/watch?v=hztO5vaBTRs">Demonstration of Carnegie Mellon CS Academy - YouTube</a></li>

</ul>
</details>

**标签**: `#computer science education`, `#open courseware`, `#online learning`, `#CMU`, `#YouTube`

---

<a id="item-tech-news-6"></a>
### [Windows 11 被指收集编码代理与开发者工具遥测](https://xusheng.dev/posts/windows-coding-agent-telemetry/) ⭐️ 7.0/10

一篇技术分析声称，Windows 11 会收集用户使用哪些编码代理和开发者工具的遥测数据，涉及使用 AI 辅助开发流程的开发者。由于未提供原始分析内容，目前无法核实具体采集字段、触发条件或适用版本；该报告将问题指向隐私与平台信任，而非已确认的漏洞或数据泄露。

hackernews · cwaffles · 11月16日 22:58 · [社区讨论](https://news.ycombinator.com/item?id=50524736)

**「背景」** 这项发现来自对 Windows 11 的 MissionControlAggregator 组件的逆向分析：相关代码在随系统启动的 DiagTrack 遥测服务下由 AggregatorHost.exe 运行，并通过可选的诊断 ETW 报告生成一个紧凑的使用位图，而非记录编码会话内容。报道中的测试环境为 Windows 11 build 26200.9974、DLL 版本 10.0.26100.9818。

**「影响」** 开发团队应把 Windows 诊断与遥测设置纳入开发环境合规检查，尤其是在受监管或保密项目中；在具体采集范围得到核实前，不能假定相关数据一定只以匿名或聚合形式处理。

**「社区讨论」** 评论者没有直接验证遥测内容，讨论主要转向迁移 Linux 的可行性：有人称单人游戏在 Linux 上基本可玩、多人游戏仍有问题，也有人认为若日常工作以 Web 服务为主，从 Windows 切换约需一周适应。另有评论认为 Windows 对 AI 代理的沙箱支持滞后，并称 MXC 于 10 月 7 日发布、Claude Code 尚不支持，因此希望有非侵入式遥测帮助确定功能优先级。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://xusheng.dev/posts/windows-coding-agent-telemetry/">Windows 11 Is Collecting Data on Which Coding Agents and ...</a></li>
<li><a href="https://windowsforum.com/news/windows-11-optional-telemetry-can-report-coding-agent-usage-research-finds.452631/">Windows 11 Optional Telemetry Can Report Coding Agent Usage ...</a></li>
<li><a href="https://www.startuphub.ai/ai-news/technology/2026/windows-11-logs-which-coding-agent-you-ran">Windows 11 logs which coding agent you ran | StartupHub.ai</a></li>

</ul>
</details>

**标签**: `#windows-telemetry`, `#privacy`, `#developer-tools`, `#ai-coding-agents`, `#linux`

---

<a id="item-tech-news-7"></a>
### [微软：7 月修复缺陷引发大规模邮件中断](https://www.theregister.com/saas/2026/11/16/microsoft-blames-monster-email-outage-on-software-defect-introduced-in-july-fix/5310026) ⭐️ 7.0/10

微软将一起大规模邮件服务中断归因于一项 7 月修复引入的软件缺陷。该故障影响 Microsoft 365/Exchange Online 的邮件服务，但现有信息未披露受影响用户数量、中断持续时长或修复完成时间。上述原因是微软的复盘结论，尚无法从独立来源核实。

hackernews · Bender · 11月16日 13:18 · [社区讨论](https://news.ycombinator.com/item?id=50517321)

**「背景」** 据 Cybersecurity News 报道，引发此次故障的缺陷来自一项专门针对 Microsoft 365 网络网关服务器准备的修复，该变更于 7 月开始部署，并在全球范围内运行了三个多月而没有出现可见问题——这也是缺陷长期潜伏、直到特定条件才暴露的原因。NPR 的报道则显示，11 月 12 日前后 Outlook 与 Microsoft 邮件服务已出现大范围中断，微软当时表示正在全力修复。

**「影响」** 对依赖 Microsoft 365/Exchange Online 的组织而言，直接后果是邮件服务在中断期间不可用；更具体的运维提醒是，7 月已部署的修复仍可能在数月后触发故障，评估供应商变更时应把回归风险纳入业务连续性计划。

**「社区讨论」** 评论者把故障恢复类比为电网的“黑启动”，并质疑微软为何不通过限流或按 IP 段分批放量来降低负载。另有评论指出，低端测试环境通过了 7 月代码、却未暴露生产环境中的并发缺陷，认为这是值得质疑的取舍；也有人对关键网络基础设施中使用 Windows 表示意外。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://cybersecuritynews.com/microsoft-outage-incident-report/">Microsoft Reveals How a Hidden Windows Bug Took Down Microsoft ...</a></li>
<li><a href="https://www.npr.org/2026/11/12/nx-s1-6039343/outlook-down-widespread-outage-microsoft-email">A negative Outlook: Microsoft scrambles to fix email outage : NPR</a></li>

</ul>
</details>

**标签**: `#Microsoft 365`, `#outage post-mortem`, `#site reliability`, `#software regression`, `#Exchange Online`

---

<a id="item-tech-news-8"></a>
### [Marimba：冻结 Qwen3-ASR 编码器回答音频查询](https://www.reddit.com/r/MachineLearning/comments/1xxsqro/marimba_a_system_one_model_for_speech_r/) ⭐️ 7.0/10

Marimba 提出一种紧凑的语音“System One”模型：用户可对 8 秒音频窗口提出是/否、选项或评分问题，模型会返回校准后的概率；每段窗口只运行一次冻结的 Qwen3-ASR-0.6B 编码器，就能处理所有问题。作者在论文中报告，在相同的 1,000 个公开问题上，它在 9 项测试中的 6 项匹配或超过 Qwen3-Omni（30B-A3B），但在 Speech Commands 上仍落后；语言识别在 300 个 FLEURS 片段上准确率为 100%，说话人变化 AUROC 为 0.966–0.980，说话人计数优于 pyannote 3.1。其局限同样明确：turn-end 读数是用 Smart Turn 数据训练的，因此在 Smart Turn 自身测试集上 AUROC 为 0.930，低于 Smart Turn v3.2 的 0.982；在 ICSI 会议上，它与 Smart Turn v3.2 基本持平（0.716 对 0.712）；在未见过的 CochlScene 场景分类上，所有头都处于随机水平。代码、Apache-2.0 权重和 pip 包已发布。

reddit · r/MachineLearning · /u/solanotodesch · 11月16日 15:47

**「背景：为什么复用冻结 ASR 编码器」** “System one”在认知科学中指的是快速、直觉式的感知处理，与需要多步推理的“system two”相对；Marimba 借用这一区分，把语音理解任务设计成对单个音频窗口做一次快速前向计算，并不进行多轮推理。具体做法是复用冻结的 Qwen3-ASR-0.6B 编码器，只在中间层特征上加小型读出层或校准打分，从而不必为每个任务单独训练一个大模型。作者表示本次发布是上周 Reddit 帖子的后续，新增了论文、Apache-2.0 权重、GitHub 代码与 Hugging Face 演示。

**「影响」** 对开发者而言，这套设计让多种音频查询共用一次冻结编码器前向，并提供 Apache-2.0 权重与 \`pip install marimba-audio\`，因此可在已有 Qwen3-ASR 部署上增加校准查询头；但作者展示的未见任务下随机水平表现和 turn-end 相对专用模型的劣势意味着，不能直接假设它能替代专用的关键词识别或 turn-end 系统，部署前仍需按目标域验证。

**标签**: `#speech recognition`, `#calibration`, `#model efficiency`, `#Qwen3-ASR`, `#audio understanding`

---

<a id="item-tech-news-9"></a>
### [duetto：不微调模型，采样时引导实时爵士伴奏](https://www.reddit.com/r/MachineLearning/comments/1xxkyh3/steering_a_pretrained_music_transformer_at/) ⭐️ 7.0/10

开发者发布了 duetto，一个面向 MIDI 键盘的实时爵士伴奏伙伴：它能与演奏者一起演奏标准曲，在独奏、伴奏和行走贝斯之间切换，并在演奏者停下时进入独奏。它不微调模型，而是直接使用预训练的 Anticipatory Music Transformer，把演奏者和模型的音符放进同一事件序列；每次采样前，规则层会对 logit 做掩码和偏置，屏蔽必须等待的手、超出音域的音、非拍点上的贝斯音等，并提高当前和弦音、强拍导向音和待引用乐句下一音的权重。乐句取自 Weimar Jazz Database 中转录的独奏，按独奏者实际换气的位置分段，移调到曲目和弦后在一个 chorus 内发展。开发者称，160 bpm 的《Autumn Leaves》演示中约 61% 的独奏音符来自引用乐句或主题；在 3080 Ti 上约为每音 12 ms（medium）和 18 ms（large），large 模型在 Jetson Orin Nano 上约每音 90 ms。代码可免费用于非商业用途，但目前没有定量评估或对比，开发者自述仍会出现偏离演奏者、响应难以预测，以及规则与模型想法之间平衡脆弱的问题。

reddit · r/MachineLearning · /u/GGAllin43 · 11月16日 09:19

**「背景：Anticipatory Music Transformer」** duetto 所依赖的 Anticipatory Music Transformer 是 Thickstun 等人在 2023 年提出的模型（arXiv 2306.08620，2024 年修订至 v2）。它把“事件”序列与“控制”序列交错建模，以时间点过程的方式逐事件生成，因此在给定另一声部作为控制信号的条件下可以生成伴奏，并在音乐控制任务上达到与自回归模型相当的效果。正因这种“跟随式”生成能力是模型训练目标的一部分，duetto 才能在完全不微调权重的情况下，仅靠采样阶段的约束把它当作实时搭档使用。

**「影响」** 对希望构建交互式符号音乐生成的开发者而言，这个项目给出了一条不训练模型、只在推理时施加约束的可行路径，且代码允许非商业使用；但规则层、乐句库和实时重采样逻辑需要按曲目与设备调整，当前的速度和音乐效果都来自作者演示，尚无独立或定量评估。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://arxiv.org/abs/2306.08620">[2306.08620] Anticipatory Music Transformer</a></li>
<li><a href="https://paperswithcode.co/paper/2306.08620">Anticipatory Music Transformer (arXiv...) | Papers with Code</a></li>

</ul>
</details>

**标签**: `#music generation`, `#inference-time control`, `#transformers`, `#constrained decoding`, `#open source`

---

<a id="item-tech-news-10"></a>
### [亚马逊称 AI 代理窃取 API 密钥以资助模型调用](https://cybernews.com/security/amazon-autonomous-cybercrime-artex-framework/) ⭐️ 7.0/10

亚马逊表示，其诱饵网络 MadPot 于 11 月 5 日阻断了一场自 10 月 3 日开始的攻击活动；攻击者用开源渗透测试框架 Artex 驱动 AI 代理，窃取 LiteLLM、Dify 等公网暴露 AI 应用的 API 密钥，验证后汇入共享池，用于支付更多大模型调用。亚马逊以中等信心将行动归因于中国相关威胁组织，并称并非所有被列目标都已失陷，已通知可能受影响的 AWS 客户。上述结论来自亚马逊的单方面通报，技术细节和归因仍有限，需谨慎看待。

telegram · zaihuapd · 11月16日 13:00

**「背景：AI 网关与密钥集中风险」** LiteLLM 这类 AI 网关用一个接口聚合 100 多家模型提供商，并集中管理 API 密钥和预算；一旦实例暴露在公网，其中保存的厂商密钥就会成为可直接盗取的高价值凭据。相关报道也指出，攻击代理正是把 LiteLLM、One API、Dify 等公网暴露的 AI 应用作为搜寻密钥的目标。

**「对暴露 AI 网关的组织」** 对自建 LiteLLM、One API、Dify 等 AI 网关的组织而言，直接后果是实例中存放的上游模型密钥一旦被读取，就可能被他人拿去支付模型调用费用；这类服务应检查是否暴露在公网、限制访问并轮换可能泄露的密钥。亚马逊已通知可能受影响的 AWS 客户，但其对攻击来源的归因仅为中等信心，且该公司表示并非所有被列出的目标都已失陷。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://thehackernews.com/2026/11/amazon-uncovers-ai-agent-campaign.html">Amazon Uncovers AI Agent Campaign Targeting LiteLLM , Dify , and...</a></li>
<li><a href="https://docs.litellm.ai/">LiteLLM documentation | liteLLM</a></li>
<li><a href="https://thehackernews.com/2026/11/amazon-uncovers-ai-agent-campaign.html">Amazon Uncovers AI Agent Campaign Targeting LiteLLM , Dify , and...</a></li>
<li><a href="https://cybelangel.com/blog/the-litellm-supply-chain-attack/">The LiteLLM Breach: 153 GB of AI and Cloud Credentials Exposed</a></li>

</ul>
</details>

**标签**: `#AI agents`, `#cybersecurity`, `#API key theft`, `#cloud security`, `#threat intelligence`

---

<a id="item-tech-news-11"></a>
### [阿里、腾讯、月之暗面据报收紧新模型网络攻击能力](https://www.bloomberg.com/news/articles/2026-11-16/china-s-top-ai-firms-limit-cyber-capabilities-in-latest-models) ⭐️ 7.0/10

据 Bloomberg 报道，阿里巴巴、腾讯和月之暗面在新一代模型中削弱了进攻性网络能力，同时提升了防御表现。阿里最新旗舰 Qwen 未开放完整权重，用户无法下载并自定义完整版本。报道还称，这与商务部上月公布的出口管制草案有关，该草案拟禁止可攻击关键基础设施、政府网络的 AI 工具出口；腾讯在发布 Hy4 前已削减相关网络功能。

telegram · zaihuapd · 11月17日 02:20

**「背景」** 这一调整已有直接先例：2026 年 11 月初腾讯发布 Hy4 时表示，训练中过滤了漏洞利用开发、逆向工程和渗透测试等网络安全内容，以降低模型被用于网络攻击的风险。当前报道称腾讯在发布 Hy4 前已削减相关网络功能，属于同一产品发布脉络下的进一步说明。

**「影响」** 对依赖完整开放权重进行本地部署或微调的开发者来说，阿里最新旗舰 Qwen 未提供可下载的完整版本，限制了自行修改和适配的空间；报道未说明是否有其他获取渠道或限制的具体范围。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.analyticsinsight.net/news/tencent-launches-hy4-ai-model-with-restricted-cybersecurity-training-data">Tencent Launches Hy4 AI Model with Restricted Cybersecurity ...</a></li>
<li><a href="https://www.reuters.com/legal/litigation/tencent-rolls-out-ai-model-trained-with-limited-cybersecurity-data-amid-hacking-2026-11-04/">Tencent rolls out AI model trained with limited cybersecurity ...</a></li>

</ul>
</details>

**标签**: `#AI governance`, `#cybersecurity`, `#export controls`, `#open-weight models`, `#Chinese AI industry`

---

## 财经新闻

<a id="item-finance-news-1"></a>
### [英特尔及 CEO 陈立武遭股东集体诉讼](https://www.investing.com/news/stock-market-news/intel-sued-by-shareholders-following-29-stock-plunge-5028171) ⭐️ 8.0/10

英特尔及 CEO 陈立武、CFO 津斯纳遭股东集体诉讼，股东指控公司隐瞒 PC 需求疲软和库存积压的影响。诉讼寻求代表 2026 年 7 月 23 日至 10 月 29 日买入股票的投资者；此前公司 10 月 29 日发布的第四季度营收和利润预测不及预期，次日股价暴跌 28.6%，市值蒸发约 1400 亿美元。

telegram · zaihuapd · 11月16日 11:10

**「背景」** 美国这类股东集体诉讼通常由在指定“集体期”内买入股票的投资者发起，指控公司及高管在信息披露中误导市场；本案集体期为 2026 年 7 月 23 日至 10 月 29 日，由一家密歇根州养老基金牵头。据 wccftech 报道，DRAM 价格上涨推高了 PC 零售成本，抑制了消费者购买。

**「影响」** 这起诉讼使在 2026 年 7 月 23 日至 10 月 29 日买入英特尔股票的投资者成为潜在索赔群体，英特尔则需应对相关法律程序。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://wccftech.com/intel-ceo-lip-bu-tan-named-defendant-class-action-lawsuit-pc-sales-slowdown/">Intel CEO Lip - Bu Tan Named As Defendant In New Class-Action...</a></li>

</ul>
</details>

**标签**: `#英特尔`, `#股东集体诉讼`, `#股价暴跌`, `#业绩指引`, `#半导体`

---

<a id="item-finance-news-2"></a>
### [英伟达 CEO 黄仁勋辞职；ETF 专家讨论 AI 交易可能转向](https://www.cnbc.com/2026/11/14/nvidia-ai-trade-data-centers-congress.html) ⭐️ 7.0/10

据 CNBC 报道，英伟达创始人兼 CEO 黄仁勋已辞职，公司股价随后录得自 2012 年以来最长周连跌。临时 CEO 兼 CFO 科莱特·克雷斯将在下周二第三季度财报中首次面对市场，而 ETF 专家推测，大型科技股和其他 AI 芯片商可能从英伟达动荡及民主党控制国会对数据中心的潜在阻力中受益。

rss · CNBC Finance · 11月16日 12:13

**「背景」** 英伟达联合创始人黄仁勋因涉及婚外情及疑似中国间谍关联的丑闻，于 11 月 12 日辞去首席执行官职务，由首席财务官科莱特·克雷斯暂代，公司定于下周二公布第三季度业绩。此前在 11 月 3 日中期选举中，民主党赢得国会控制权，多位当选议员主张限制人工智能开发、放慢数据中心建设。

**「影响」** Yorkville Ives 估计，若民主党控制的国会推动放缓数据中心建设，低端 10%、高端 15%至 20%的规划项目可能无法落地，而需求仍为供应的四倍，这可能影响依赖 AI 算力的云厂商和芯片投资者，但该数字是预测。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://finance.yahoo.com/markets/stocks/articles/nvidia-ceo-jensen-huang-resigns-140651041.html?fr=sycsrp_catchall">Nvidia CEO Jensen Huang resigns in wake of affair, spy scandal Nvidia CEO Jensen Huang resigns amid spy scandal : NPR Jensen Huang resigns as Nvidia CEO after alleged affairs Timeline of a scandal: How Jensen Huang&#x27;s abrupt resignation ... Silicon Valley and Trump rally behind Nvidia CEO after his ... Jensen Huang Scandal: Timeline That Led To His Resignation ...</a></li>
<li><a href="https://www.npr.org/2026/11/12/nx-s1-6037833/jensen-huang-nvidia-stepped-down">Nvidia CEO Jensen Huang resigns amid spy scandal : NPR</a></li>
<li><a href="https://foreignpolicy.com/2026/11/05/midterm-results-ai-data-centers-texas-georgia-ohio/">Midterm Results Reflect AI , Data Center Concerns</a></li>
<li><a href="https://fxmacrowire.com/wire/top-democrats-call-to-rein-in-ai-buildout-after-midterms-sweep">Top Democrats call to rein in AI buildout after... | FXMacro Wire</a></li>

</ul>
</details>

**标签**: `#Nvidia`, `#AI trade`, `#ETFs`, `#data centers`, `#US Congress`

---

<a id="item-finance-news-3"></a>
### [卢特尼克因英伟达相关利益冲突质疑受审视](https://www.cnbc.com/2026/11/13/howard-lutnick-nvidia-jensen-huang-china-cantor-fitzgerald.html) ⭐️ 7.0/10

CNBC 报道，美国商务部长霍华德·卢特尼克因英伟达相关事务面临利益冲突质疑：其子执掌的坎托·菲茨杰拉德在 2025 年 9 月至 2026 年 3 月间申报的英伟达持股数量减少近 50%，而据 Axios 报道，卢特尼克多次抵制对涉嫌向中国走私英伟达芯片公司的打击，英伟达 CEO 黄仁勋随后辞职。报道称，没有证据表明卢特尼克泄露非公开信息、其子提前知情或持股变动与情报警告有关；坎托表示其英伟达自营头寸一直无关紧要，13F 申报中的头寸是客户互换交易相关的正常业务。

rss · CNBC Finance · 11月16日 12:14

**「背景」** 康托菲茨杰拉德（Cantor Fitzgerald）是卢特尼克在 2025 年出任美国商务部长前长期执掌的华尔街投行，目前由他的两个儿子布兰登和凯尔经营；而商务部正是负责出口管制、包括将企业列入限制贸易的“实体清单”的部门。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://en.wikipedia.org/wiki/Howard_Lutnick">Howard Lutnick - Wikipedia</a></li>

</ul>
</details>

**标签**: `#Nvidia`, `#U.S. export controls`, `#China tech policy`, `#conflict of interest`, `#Commerce Department`

---