---
layout: default
title: "Horizon Summary: 2026-11-14 (ZH)"
date: 2026-11-14
lang: zh
---

> 从 41 条内容中筛选出 9 条重要资讯。

---

**科技新闻**
1. [TorchTitan 称在 384 块 GH200 上训练约 1T 参数 MoE](#item-tech-news-1) ⭐️ 8.0/10
2. [Orcasairband 实时监听 KORS 全部航空波段](#item-tech-news-2) ⭐️ 7.0/10
3. [ICML 2027 投稿新规：双阶段审稿与互惠审稿人](#item-tech-news-3) ⭐️ 7.0/10
4. [微软 Outlook、Teams 与 Copilot 全球宕机逾 12 小时](#item-tech-news-4) ⭐️ 7.0/10
5. [DeepSeek 开放搜索、文件与语音应用 API](#item-tech-news-5) ⭐️ 7.0/10
6. [OpenAI 推出 ChatGPT Wallet 智能体支付钱包](#item-tech-news-6) ⭐️ 7.0/10

**财经新闻**
1. [卢特尼克因英伟达“间谍”风波受质询，其子执掌的公司与英伟达关系深厚](#item-finance-news-1) ⭐️ 8.0/10
2. [古尔斯比：美联储在通胀问题上“肯定还有工作要做”](#item-finance-news-2) ⭐️ 8.0/10
3. [黄仁勋辞职，美中芯片出口管制前景添变数](#item-finance-news-3) ⭐️ 8.0/10

---

## 科技新闻

<a id="item-tech-news-1"></a>
### [TorchTitan 称在 384 块 GH200 上训练约 1T 参数 MoE](https://www.reddit.com/r/MachineLearning/comments/1xvce5h/scaling_to_1t_moe_on_torchtitan_p/) ⭐️ 8.0/10

Reddit 上的一份经验报告称，作者与 TorchTitan/PyTorch 维护者合作，在 384 块 GH200 上采用 384 路 FSDP 加 4 路节点内专家并行（EP）、跳过流水线并行，把约 1T 参数 MoE 的训练吞吐做到每 GPU 约 1,300 tokens/s，较最初设置提升 14 倍。报告把主要收益归因于全量激活重计算、将检查点卸载到 Grace、用 Muon 替代 Adam 以支撑 64k token 序列，以及 FlexShard 按完整专家分片，让专家矩阵的 Newton-Schulz 本地执行而无需跨卡通信。其他报告数据包括：Newton-Schulz 移到 GPU 后优化器步从 42 秒降到约 2 秒、吞吐提升 35%；按注意力成本分桶把最慢卡从平均的 7.9 倍降到 1.15 倍、提升 13%；FP8 专家 all-gather 提升 18%；修复分配器流问题后吞吐提升 21%。这些均为作者自述结果；分组受限路由虽带来 7% 提升，但早期运行显示可能损害训练，且分配器修复依赖 FSDP2 的私有 \`unshard\_async\_op\` 标志，文章称其正在转为公开 API。

reddit · r/MachineLearning · /u/f14-bertolotti · 11月13日 16:28

**「背景」** TorchTitan 是 PyTorch 官方的大规模分布式训练库，支持 FSDP、专家并行（EP）与流水线并行（PP）等 4D 并行组合。此次试验运行在 JUPITER 上，这是一台由 EuroHPC 共同出资、面向欧洲研究者开放申请的 GH200 超算；本次共使用 96 个节点、384 块 GPU。据 PyTorch 博客，优化前的起点吞吐约为 90 tokens/s/GPU，本文报告的约 1,300 tokens/s/GPU 就是以该基线为参照。

**「影响」** 对想复现这套配方的分布式训练团队，最直接的兼容性问题是：把 FP8/bf16 通信临时分配移回计算流、从而带来 21% 吞吐提升的修复，依赖 FSDP2 的私有 \`unshard\_async\_op\` 标志，文章称其正在转为公开 API；在公开版本落地前，需要确认所用 TorchTitan/PyTorch 版本是否包含该开关，否则不能假定能复现同一内存与吞吐结果。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://pytorch.org/blog/training-a-1t-parameter-moe-on-eu-public-infrastructure-with-pytorch-and-torchtitan/">Training a 1T-Parameter MoE on EU public ... - PyTorch</a></li>
<li><a href="https://www.linkedin.com/posts/domynai_thanks-for-featuring-our-work-pytorch-activity-7526975992490332160-9kaa">Thanks for featuring our work, PyTorch! Getting a trillion ...</a></li>
<li><a href="https://explore.n1n.ai/blog/training-1t-parameter-moe-pytorch-torchtitan-2026-11-13">Training a 1T-Parameter MoE on EU Public Infrastructure with ...</a></li>

</ul>
</details>

**标签**: `#TorchTitan`, `#Mixture-of-Experts`, `#distributed training`, `#PyTorch`, `#GH200`

---

<a id="item-tech-news-2"></a>
### [Orcasairband 实时监听 KORS 全部航空波段](https://orcasairband.com/) ⭐️ 7.0/10

Orcasairband.com 提供来自 KORS 的整段航空波段实时监听和解调文本。项目作者 mmaunder 称，系统由 ETTUS B210 接收机连接双 RTX 4090 主机，通过 CUDA 实现的 polyphase channelizer 将整个 airband 分信道、解调并检测发射，再生成文本。该服务在当天的温哥华地区 ground stop 中被用来查看空域通话，评论者引用了 126.400 Victoria Ground 和 134.800 Vancouver Centre 的原始记录。作者强调这些文本未经编辑，且该服务属于业余项目。

hackernews · mmaunder · 11月13日 22:04 · [社区讨论](https://news.ycombinator.com/item?id=50490593)

**「技术背景」** 软件定义无线电（SDR）会尽早把射频信号数字化，后续的滤波、信道化和解调都交给软件完成；多相信道化能把一段宽带同时拆成许多窄带频道，因此一台宽带接收机配合 GPU 就能并行监听整个航空频段。民航地空语音通信仍大量使用模拟调幅，接收条件不佳时语音会断续、含混，所以这类系统还需要检测通话并把音频转写成文字。

**「对自建宽频监听者的实际含义」** 对想自建全频段监听的技术爱好者而言，这套方案证明一块 ETTUS B210 加双 RTX 4090、用 CUDA 实现多相信道化，就能实时切分并解调整个航空频段，还能顺带生成文字记录；在 11 月 13 日美国联邦航空管理局因通信问题发布全国地面停飞、导致温哥华机场大量航班延误期间，网站转录到了 126.400（Victoria Ground）与 134.800（Vancouver Centre）上关于停飞的对话。但可用性有明确边界：弱信号频道的转录存在大量无法辨识的片段，作者也说明这些是未经编辑的原始文本，因此不能当作可靠的事故或运行记录，只适合作为辅助了解空域动态的参考。

**「社区讨论」** 评论者 molsongolden 回溯到 14:03 的通话，称其中确认了飞往温哥华的地面停飞，且当时没有航班从温哥华起降。plipt 则指出许多通话听感模糊，并询问航空通信是否仍因安全或互操作原因使用模拟制式。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://vancouversun.com/news/us-flights-grounded-yvr-vancouver-airport-updates">Hundreds of flights delayed at YVR after FAA grounds planes ...</a></li>

</ul>
</details>

**标签**: `#software-defined radio`, `#GPU signal processing`, `#CUDA`, `#aviation communications`, `#real-time monitoring`

---

<a id="item-tech-news-3"></a>
### [ICML 2027 投稿新规：双阶段审稿与互惠审稿人](https://www.reddit.com/r/MachineLearning/comments/1xvkxbj/icml_2027_changes_d/) ⭐️ 7.0/10

一篇 Reddit 帖文概括了 ICML 2027 CFP 的多项审稿改革：采用两阶段评审，由领域主席决定论文是否进入完整评审，任何拟议的一阶段拒稿须经资深领域主席确认，作者可在 2 月 23 日前收到简短理由。帖文还称，每人在投稿中最多出现 20 次，每篇论文须从作者名单中指定一名互惠审稿人（每名审稿人最多承担 6 篇），有 3 篇及以上投稿的人必须加入程序委员会，不合规论文可能被直接拒稿。最严格的限制是每名作者最多只能有一篇论文没有任何合格互惠审稿人；这些内容来自 Reddit 对 CFP 的转述，所给材料未提供官方页面核验。

reddit · r/MachineLearning · /u/Gravitist · 11月13日 21:53

**「背景」** ICML 的投稿量增长快于合格审稿人的供给，会议方称这正是 2027 年引入投稿配额并强化“互惠审稿”要求的背景（tool-2-1）。所谓互惠审稿，是把审稿义务与作者身份绑定：论文须从作者名单中指定审稿人，且单个审稿人可承担的论文数有限（tool-2-3）。

**「影响」** 对作者而言，互惠审稿承诺会直接影响署名策略：与本科生、实习生或领域外合作者共同署名时，可用于“无合格审稿人”论文的额度只有一篇，因此多投稿团队需提前安排审稿人力并检查合规，否则可能面临直接拒稿。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://icml.cc/Conferences/2027/ReciprocalReviewingAndSubmissionQuotas">2027 Reciprocal Reviewing And Submission Quotas - icml.cc</a></li>
<li><a href="https://agihunt.info/en/p/1a1d6ef21b4678bbe1d81712b77">ICML 2027 Caps Submissions at 20, Ties… · AGI Hunt</a></li>

</ul>
</details>

**标签**: `#ICML`, `#peer review`, `#machine learning research`, `#conference policy`, `#reviewer load`

---

<a id="item-tech-news-4"></a>
### [微软 Outlook、Teams 与 Copilot 全球宕机逾 12 小时](https://www.reuters.com/technology/microsoft-365-outlook-down-thousands-us-users-downdetector-shows-2026-11-12/) ⭐️ 7.0/10

微软 Outlook、Teams 和 Copilot 在 11 月 13 日仍处于宕机状态，故障已持续超过 12 小时，影响全球企业与政府通信。微软将原因归为服务器问题，称未发现恶意活动，并表示已扩大修复范围、出现回稳迹象。澳大利亚、日本和美国部分政府机构受到影响，Euronext 邮件受阻，台湾有金融机构改用传真确认交易；这是微软 365 服务今年第二次中断。

telegram · zaihuapd · 11月13日 12:21

**「背景」** Microsoft 365 是将 Outlook 邮件、Teams 会议与 Copilot 等云服务打包提供的订阅服务，企业通信高度依赖其云端基础设施。来源同时指出，这是微软 365 服务今年第二次中断。

**「直接影响」** 对把 Outlook、Teams 作为主要通信渠道的机构而言，故障期间需要启用备用通道；台湾金融机构改用传真确认交易就是具体表现，说明关键业务连续性不能只依赖单一云服务。

**标签**: `#Microsoft 365`, `#Outlook`, `#Teams`, `#service outage`, `#cloud reliability`

---

<a id="item-tech-news-5"></a>
### [DeepSeek 开放搜索、文件与语音应用 API](https://mp.weixin.qq.com/s/78KBHc4-4N5b2vfL9SkutQ) ⭐️ 7.0/10

DeepSeek 宣布开放一套应用级对话 API：开发者在原有 API 中开启相应参数，即可使用深度思考搜索、文件输入、链接阅读和语音等能力，工具调用与上下文拼接由服务端完成。V4.1-Flash 模型已在三个接口中支持这些能力，Search、Fetch、OCR、ASR、TTS 也可单独调用。官方同时开源了可导入历史对话的前端 Demo，并称可基于 API 在本地部署 DeepSeek 网页端。

telegram · zaihuapd · 11月13日 14:27

**「背景」** 这里的“应用级 API”指在原有模型调用接口上增加参数，由服务端自动完成搜索、文件读取、OCR、语音等工具调用与上下文拼接，开发者不必自行串联这些步骤。DeepSeek 官方 API 文档已列出联网搜索、文件输入、阅读链接、ASR、TTS 的使用入口和 API key 申请方式。

**「影响」** 对开发者而言，可直接按需调用单项能力，或通过对话接口交给服务端编排，从而减少分别集成搜索、OCR、语音等组件的工程量；但现有信息未披露计费、配额和具体接口参数，接入前需核对 V4.1-Flash 的适用范围与兼容性。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://api-docs.deepseek.com/zh-cn/">首次调 用 API | DeepSeek API Docs</a></li>

</ul>
</details>

**标签**: `#DeepSeek`, `#API`, `#AI agents`, `#open source`, `#multimodal`

---

<a id="item-tech-news-6"></a>
### [OpenAI 推出 ChatGPT Wallet 智能体支付钱包](https://openai.com/index/introducing-chatgpt-wallet/) ⭐️ 7.0/10

OpenAI 宣布推出 ChatGPT Wallet，并与美国运通、万事达和 Visa 合作，让 AI 智能体在不接触用户真实卡号的情况下发起付款。每笔购买都需用户核对商品和金额，并通过 Face ID 或指纹确认；支付网络会下发替代真实卡号的支付令牌。公告称，该服务自今日起在美国通过 dots 面向 18 岁以上的 ChatGPT Pro 订阅用户开放，且必须使用美国发行的银行卡；这些细节来自简短公告，尚无独立验证。

telegram · zaihuapd · 11月13日 15:43

**「背景」** 网络令牌化（network tokenization）是移动支付中已有的做法：支付网络向设备下发一个替代真实卡号的支付令牌，商户或代理程序只能看到令牌，真实卡号不会直接暴露。ChatGPT Wallet 把这一机制用于 AI 智能体代付，首发通过 OpenAI 的 dots 智能体提供，仅面向美国 ChatGPT Pro 订阅用户，并要求使用美国发行的银行卡。

**「影响」** 符合条件的用户不能把付款确认完全交给智能体：每笔交易仍需人工核对商品和金额并完成生物识别。非美国发行卡、非 ChatGPT Pro 订阅用户或未满 18 岁者不在首批开放范围内。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://openai.com/index/introducing-chatgpt-wallet/">Introducing ChatGPT Wallet | OpenAI</a></li>
<li><a href="https://www.cnbc.com/2026/11/13/openai-chatgpt-wallet-dot-purchases.html">OpenAI &#x27;s ChatGPT Wallet allows &#x27; dots &#x27; AI agents to make purchases</a></li>

</ul>
</details>

**标签**: `#OpenAI`, `#agentic payments`, `#ChatGPT Wallet`, `#tokenization`, `#AI agents`

---

## 财经新闻

<a id="item-finance-news-1"></a>
### [卢特尼克因英伟达“间谍”风波受质询，其子执掌的公司与英伟达关系深厚](https://www.cnbc.com/2026/11/13/howard-lutnick-nvidia-jensen-huang-china-cantor-fitzgerald.html) ⭐️ 8.0/10

据 CNBC 报道，曾由美国商务部长霍华德·卢特尼克执掌、现由其子布兰登和凯尔经营的坎托·菲茨杰拉德公司，在 2025 年 9 月至 2026 年 3 月期间将其申报持有的英伟达股票数量削减近 50%，从约 350 万股（价值 6.52 亿美元）降至 178 万股（价值 3.10 亿美元），同时仍继续为英伟达的合作伙伴安排融资。此事发生之际，卢特尼克正因处理一起疑似英伟达芯片走私中国的事件而受到审查，英伟达 CEO 黄仁勋也已辞职；CNBC 指出，目前没有证据表明坎托的持股变化与相关情报警告有关，也没有证据表明卢特尼克泄露了非公开信息。

rss · CNBC Finance · 11月13日 23:42

**「背景」** 黄仁勋此前因与新加坡公司 Megaspeed 前高管 Alice Huang 的私人关系曝光而辞去英伟达首席执行官职务；据报，美方情报界怀疑 Alice Huang 被中国国家安全部招募，相关说法仍属指控。美国商务部负责执行芯片出口管制并维护限制对华出口的实体清单，卢特尼克因此对涉英伟达芯片转运的调查拥有决策权。

**「受影响方」** 商务部是否将 Megaspeed 列入实体清单（即限制美国企业向其出口的名单），直接关系到受管制的英伟达 AI 芯片能否继续经这类中介流入中国，因而影响依赖该渠道的中国 AI 企业和英伟达的海外云合作伙伴。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://en.wikipedia.org/wiki/Jensen_Huang_spying_scandal">Jensen Huang spying scandal - Wikipedia</a></li>
<li><a href="https://www.cbsnews.com/news/nvidia-ceo-jensen-huang-resigns/">Nvidia CEO Jensen Huang resigns in wake of affair with woman ...</a></li>
<li><a href="https://www.cnbc.com/2026/11/12/nvidia-megaspeed-alice-huang-jensen-.html">What we know so far about Nvidia partner Megaspeed’s Asia ...</a></li>
<li><a href="https://www.nbcnews.com/tech/tech-news/nvidia-chips-loophole-export-ruleschinese-companies-access-megaspeed-rcna608601">How Chinese companies access Nvidia chips through a loophole ...</a></li>

</ul>
</details>

**标签**: `#Nvidia`, `#US-China export controls`, `#semiconductors`, `#Commerce Department ethics`, `#corporate governance`

---

<a id="item-finance-news-2"></a>
### [古尔斯比：美联储在通胀问题上“肯定还有工作要做”](https://www.cnbc.com/2026/11/13/chicago-feds-goolsbee-says-central-bank-has-definitely-got-work-to-do-on-inflation.html) ⭐️ 8.0/10

芝加哥联储主席古尔斯比 11 月 13 日表示，美联储在重建通胀公信力方面“肯定还有工作要做”；此前公布的 10 月生产者价格指数（PPI，批发价格指标）同比上涨 6.5%，为 2022 年 11 月以来最高。市场目前完全计入美联储在 12 月 8-9 日会议上加息 25 个基点的预期；古尔斯比目前不是联邦公开市场委员会（FOMC）投票委员，2027 年才有投票权。

rss · CNBC Finance · 11月13日 14:22

**「背景」** 美联储的长期通胀目标是 2%，但古尔斯比称通胀已近六年高于该水平；本周稍早公布的消费者价格指数（CPI）环比上涨 0.4%、高于预期，进一步加大了政策压力。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.cnbc.com/2026/11/11/goolsbee-october-inflation-fed-rates-disturbing-distressing.html">Austan Goolsbee calls inflation report &#x27;borderline disturbing ...</a></li>

</ul>
</details>

**标签**: `#Federal Reserve`, `#inflation`, `#producer price index`, `#monetary policy`, `#interest rate expectations`

---

<a id="item-finance-news-3"></a>
### [黄仁勋辞职，美中芯片出口管制前景添变数](https://www.cnbc.com/2026/11/13/jensen-huang-nvidia-us-china-relations.html) ⭐️ 8.0/10

英伟达首席执行官黄仁勋周四辞职，此前美国国会审查他与一名被指为中国间谍的女性有婚外情，他同意在 11 月 26 日前向国会作证。分析人士预计，这起间谍指控尚未证实的风波可能促使国会在年底前收紧对华芯片出口限制。

rss · CNBC Finance · 11月13日 02:56

**「背景」** 美国自 2022 年起限制英伟达向中国出售先进芯片，特朗普政府 2025 年又放宽了多项拜登时期限制，两国目前维持着脆弱的贸易休战。

**「影响」** 若国会如分析人士所料收紧规则，英伟达等美国芯片企业的对华销售将面临更大约束，北京也可能以限制稀土或芯片制造材料供应作为反制。

**标签**: `#Nvidia`, `#U.S.-China relations`, `#semiconductor export controls`, `#corporate governance`, `#espionage allegation`

---