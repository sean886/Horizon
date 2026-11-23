---
layout: default
title: "Horizon Summary: 2026-11-23 (ZH)"
date: 2026-11-23
lang: zh
---

> 从 28 条内容中筛选出 7 条重要资讯。

---

**科技新闻**
1. [OpenAI 发文讨论困惑度与模型智能的关系](#item-tech-news-1) ⭐️ 7.0/10
2. [英媒指太子集团关联人士涉对华走私英伟达芯片](#item-tech-news-2) ⭐️ 7.0/10
3. [谷歌用 Mirror Dimension 模拟互联网测试 Chrome AI 代理](#item-tech-news-3) ⭐️ 7.0/10

**科技博客**
1. [不确定时，主动试错优于谨慎等待](#item-tech-blog-1) ⭐️ 5.0/10

**财经新闻**
1. [美股科技股遭抛售，亚洲多地出台稳市措施](#item-finance-news-1) ⭐️ 9.0/10
2. [中国要求美国撤销电话号段接入限制](#item-finance-news-2) ⭐️ 7.0/10
3. [蚂蚁集团领投 Simplexity Robotics 1 亿美元 pre-A 轮，投后估值 16 亿美元](#item-finance-news-3) ⭐️ 7.0/10

---

## 科技新闻

<a id="item-tech-news-1"></a>
### [OpenAI 发文讨论困惑度与模型智能的关系](https://openai.com/index/perplexity-and-intelligence/) ⭐️ 7.0/10

OpenAI 发布了一篇题为《Perplexity and Intelligence》的分析文章，讨论困惑度（perplexity）与语言模型能力之间的关系，目标读者是关注模型评估的研究者和开发者。由于没有提供文章正文，无法确认文中是否给出了新的定量结果、基准或可复现实验；目前可核实的只是文章主题及其在 Hacker News 上引发的技术讨论。评论者围绕交叉熵损失在强化学习时代是否仍重要、基准是否过于复杂，以及 GPT-4.5、o1 等推理模型的时间线展开争论。

hackernews · acossta · 11月22日 17:06 · [社区讨论](https://news.ycombinator.com/item?id=50601525)

**「背景」** 困惑度（perplexity）是语言模型预训练中衡量下一词预测不确定性的指标，数值越低表示模型对文本的预测越有把握；它与交叉熵损失直接对应，交叉熵取指数即得到困惑度。OpenAI 首席科学家 Jakub Pachocki 在 11 月 22 日的文章中主张，把这一语言模型指标提升为不同模型开发者之间可比较、并可服务于共同安全标准的公开尺度。

**「对评测与比较的影响」** 若困惑度成为跨厂商的可比指标，开发者会得到一个比现有基准更简单、更廉价的基础模型能力信号：评论区提到，微软已在 OpenAI 的共同留出评测集上报告 MAI-2 Base 的对数困惑度为 0.819，并称其与 GPT-5.6 Sol 基础模型同档——但这一说法来自社区转述的推文，不能当作已确认的行业标准。实际使用者需要注意，困惑度只有在评测集、分词器和上下文长度一致时才可直接比较，否则跨模型的数字没有可比性。

**「社区讨论」** 评论者 hazrmard 补充了困惑度的定义（最差等于词表大小、最好为 1），jrflo 则对交叉熵在强化学习普及后仍呈现清晰趋势感到意外，并认为简单基准比日益复杂的评测更有价值；d\_burfoot 主张预测/压缩率正好刻画了从原始数据中提取世界模型的进展。另有评论者 reasonableklout 转述 Mustafa Suleyman 的推文，称微软 MAI-2 Base 在 OpenAI 的评测集上 log-perplexity 为 0.819，这属于厂商说法而非独立验证。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://openai.com/index/perplexity-and-intelligence/">Perplexity and Intelligence | OpenAI</a></li>
<li><a href="https://pikabu.ru/story/glavnyiy_uchenyiy_openai_raskryil_sekretnyiy_grafik_rosta_ii_i_poprosil_konkurentov_dogovoritsya_o_stoplimitakh_14554049">Главный ученый OpenAI раскрыл секретный график роста... | Пикабу</a></li>
<li><a href="https://openai.com/index/perplexity-and-intelligence/">Perplexity and Intelligence | OpenAI</a></li>

</ul>
</details>

**标签**: `#perplexity`, `#AI evaluation`, `#language models`, `#cross-entropy`, `#OpenAI`

---

<a id="item-tech-news-2"></a>
### [英媒指太子集团关联人士涉对华走私英伟达芯片](https://www.ft.com/content/f3ad8a81-3890-4a8a-8853-ff0a94b08ba9?syn-25a6b1a6=1) ⭐️ 7.0/10

英国《金融时报》援引知情人士称，被美国财政部指为柬埔寨太子集团“二号人物”的胡小伟涉嫌参与将英伟达芯片运入中国，相关网络被指使用空壳公司、地下融资渠道和私人飞机。报道援引贸易数据称，2024 年 12 月至 2025 年 12 月，Megaspeed 马来西亚子公司进口货物申报价值约 46 亿美元，部分芯片据称流入中国黑市。太子集团否认胡小伟曾为其工作，并称有关非法网络和私人飞机走私的指控缺乏事实依据；上述说法来自报道及其引述，尚非独立确认。

telegram · zaihuapd · 11月22日 04:34

**「背景」** 美国对英伟达高端 AI 芯片实施对华出口管制，相关产品进入中国市场通常需要许可证或满足特定条件，第三国转口的最终流向因而成为合规审查重点。这一管制背景解释了为何有关走私网络的指控会涉及空壳公司、地下融资和私人飞机等规避安排。

**「对采购渠道的直接影响」** 对通过马来西亚等东南亚中间商采购英伟达加速器的企业而言，这一指控意味着需要更严格的最终用户核查与货物流向凭证：报道称 Megaspeed 马来西亚子公司在 2024 年 12 月至 2025 年 12 月间申报进口约 46 亿美元货物，部分芯片据称流入中国黑市。渠道方被切断供货已有先例——据称英伟达于 2025 年 6 月将 Megaspeed 列入禁售名单，其团队随后转往新公司 Novagate Cloud，这说明经手此类中转贸易的经销商可能面临供应商直接停供的合规风险。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://actualidad-rt.com/actualidad/639191-hombre-detras-espia-china-nvidia">Quién es el hombre detrás de la &#x27;espía china &#x27; de Nvidia ? - RT</a></li>

</ul>
</details>

**标签**: `#Nvidia`, `#chip smuggling`, `#export controls`, `#AI hardware`, `#semiconductor supply chain`

---

<a id="item-tech-news-3"></a>
### [谷歌用 Mirror Dimension 模拟互联网测试 Chrome AI 代理](https://www.landian.news/archives/128701.html) ⭐️ 7.0/10

蓝点网报道，谷歌为 Chrome 的 AI 代理搭建了一个名为 Mirror Dimension 的模拟互联网，用于在隔离环境中测试该代理打开网站、搜索浏览、登录、加购和完成任务等操作。该环境包含数千个模拟网站，每名工程师使用各自隔离的测试环境，每天运行超过 1000 个测试案例。报道称，测试重点是防御恶意网页发起的提示词注入等攻击；目前这些信息来自一篇简要的二手报道，尚未见到谷歌的主源确认，也缺少更多技术细节。

telegram · zaihuapd · 11月23日 01:30

**「背景：隔离测试环境」** 浏览器 AI 代理需要打开网页、搜索、登录和完成操作，直接放到真实网络上测试会带来安全风险；提示词注入则是把恶意指令藏进网页内容，诱导代理偏离任务的攻击方式。Google Chrome 团队在公开博客中把 Mirror Dimension 描述为一个由团队完全控制、与真实网络隔离的合成网络环境，用于在接近真实的在线场景中安全测试代理。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://blog.google/security/mirror-dimension-for-agents/">Mirror Dimension for Agents : Evaluating Browser-Use Agents ...</a></li>
<li><a href="https://www.wired.com/story/google-built-a-giant-mirror-dimension-internet-to-test-its-chrome-ai-agents/">Google Built a Giant ‘ Mirror Dimension ’ Internet to Test Its Chrome ...</a></li>

</ul>
</details>

**标签**: `#Chrome AI agent`, `#prompt injection`, `#AI safety`, `#browser automation`, `#Google`

---

## 科技博客

<a id="item-tech-blog-1"></a>
### [不确定时，主动试错优于谨慎等待](https://seangoedecke.com/when-in-doubt-flail-about/) ⭐️ 5.0/10

rss · Sean Goedecke · 11月23日 00:00

**「背景」** 当工程或组织问题缺乏清晰指引、甚至不知道从哪里入手时，作者认为谨慎等待通常不是最佳选择；真正的挑战是在信息不足时尽快获得理解并变得有用。

**「方案」** 他主张“乱撞”（flail）：大量尝试不同做法，密切观察来自同事与现实的反馈，并果断放弃没有正面反馈的方案。多试之所以关键，一是能直接接触更多现实，二是因为多数计划本来就会失败，三是不至于对单一计划过度投入。作者把这种方法用于三类场景：产品尚未找到市场契合时，在边缘快速试错——他在 GitHub Models 上做的多项功能大多不成功，但用 GitHub Actions token 运行 AI 推理意外受欢迎，后来成为“Continuous AI”的种子；面对过于复杂的大型系统时，先做一批推测性改动看效果，也可让 AI 代理生成多个重构方案；组织问题中则尝试自动化手工工作、主动承担任务或提出长期方案，且更要敏感于反馈，及时撤掉无效举措以建立信任。作者也提醒，这种做法有风险：乱撞得不好会损害声誉；从内部看它像是在反复失败，但主管可能只看到主动实验，只要对反馈敏感并愿意立即放弃，这种不适感可以当作正向信号，而不是麻烦的征兆。

**「启示」** 作者的核心结论是：在高度不确定的工程和组织情境中，有纪律的“乱撞”——广撒网、读反馈、快放弃——往往比等待完整理解更快带来突破；但若忽视反馈、持续推行坏主意，也会损害声誉。

**标签**: `#engineering practice`, `#uncertainty`, `#experimentation`, `#product development`, `#organizational dynamics`

---

## 财经新闻

<a id="item-finance-news-1"></a>
### [美股科技股遭抛售，亚洲多地出台稳市措施](https://news.bjd.com.cn/2026/11/22/12039852.shtml) ⭐️ 9.0/10

美国 AI 科技股周五遭遇大规模抛售，纳斯达克指数单日下跌 5.28%，费城半导体指数重挫近 11%；随后中国内地、韩国和中国台湾地区分别推出下调融资保证金最低比例、放宽上市公司回购订单限制和禁止平盘以下卖空等市场稳定措施。

telegram · zaihuapd · 11月22日 13:24

**「背景」** 中国内地的融资保证金最低比例此前为 100%，此次下调至 80%，意味着投资者借钱买股票时需自备的资金比例降低，可撬动的杠杆相应放大。这并非本轮首次下跌：11 月初市场已因对 AI 投资热潮能否持续、半导体企业业绩不佳的疑虑出现过一轮抛售。

**「直接影响」** 这些措施直接改变中国内地、韩国和台湾市场融资交易者与卖空者的可操作空间和成本，并通过放宽回购限制让韩国上市公司更容易在跌市中买回股票。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.gate.com/crypto-wiki/article/semiconductor-index-crash-largest-sox-declines">Semiconductor Index Selloffs : Largest SOX Declines | Gate Wiki</a></li>
<li><a href="https://www.zerohedge.com/markets/south-korea-readies-first-market-rescue-fund-deployment-2008">Asian Market Panic Continues As Korea Readies To... | ZeroHedge</a></li>

</ul>
</details>

**标签**: `#US tech selloff`, `#semiconductor stocks`, `#Asian market stabilization`, `#margin rules`, `#short-selling restrictions`

---

<a id="item-finance-news-2"></a>
### [中国要求美国撤销电话号段接入限制](https://www.bloomberg.com/news/articles/2026-11-22/china-objects-to-us-curbs-on-telecoms-access-to-phone-numbers) ⭐️ 7.0/10

中国商务部 11 月 22 日敦促美国撤销一项禁止中国移动、中国电信、中国联通直接接入美国电话号码的措施，称其违反非歧视与公平竞争原则，并指美方在没有事实依据的情况下援引国家安全风险。美国联邦通信委员会（FCC）于 11 月 19 日投票收紧对申请直接接入美国号码的互联网语音服务商的安全要求，新增国家安全认证，以阻止其“涵盖清单”上的实体、设备和服务接入美国网络。

telegram · zaihuapd · 11月22日 06:44

**「背景」** 此次争议源于美国联邦通信委员会（FCC）11 月 19 日的投票：该机构以国家安全为由，收紧对申请直接接入美国电话号码的互联网语音服务商的安全认证，并阻止其“覆盖清单”上的实体、设备和服务接入美国网络。

<details><summary>参考链接</summary>
<ul>
<li>FCC votes to ban Chinese telecoms from direct access to US phone numbers | Reuters</li>

</ul>
</details>

**标签**: `#US-China relations`, `#telecom regulation`, `#FCC`, `#Chinese telecom carriers`, `#market decoupling`

---

<a id="item-finance-news-3"></a>
### [蚂蚁集团领投 Simplexity Robotics 1 亿美元 pre-A 轮，投后估值 16 亿美元](https://www.bloomberg.com/news/articles/2026-11-22/ant-group-bets-on-simplexity-to-thrive-in-china-s-humanoid-race) ⭐️ 7.0/10

彭博报道，中国具身智能公司 Simplexity Robotics 完成 1 亿美元 pre-A 轮融资，由蚂蚁集团领投，投后估值 16 亿美元。公司董事长兼联合创始人 Wang Kai 向彭博确认了该消息，老股东阿里巴巴、腾讯、HongShan 和蓝驰创投跟投。

telegram · zaihuapd · 11月23日 02:02

**「背景」** Simplexity Robotics 于 2025 年 7 月在杭州成立，核心团队来自理想汽车；据彭博报道，该公司今年 3 月披露成立半年内已完成五轮融资、累计融资 20 亿元人民币，当时投后估值已超过 10 亿美元。中国人形机器人厂商约占全球出货量的 97%，因此它需要与宇树、优必选等更成熟的厂商争夺市场。

**「市场影响」** 这笔融资将用于与宇树、优必选等更成熟的厂商争夺市场，意味着这些厂商将在市场份额上面临一个资金更充足的新对手。

**标签**: `#humanoid robotics`, `#venture funding`, `#Ant Group`, `#China tech`, `#startup valuation`

---