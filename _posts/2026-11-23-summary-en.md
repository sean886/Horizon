---
layout: default
title: "Horizon Summary: 2026-11-23 (EN)"
date: 2026-11-23
lang: en
---

> From 28 items, 7 important content pieces were selected

---

**Technology News**
1. [OpenAI article links perplexity to model intelligence, prompting benchmark debate](#item-tech-news-1) ⭐️ 7.0/10
2. [FT Report Alleges Prince Group Figure Helped Smuggle Nvidia Chips to China](#item-tech-news-2) ⭐️ 7.0/10
3. [Google Reportedly Tests Chrome AI Agent in Simulated Web](#item-tech-news-3) ⭐️ 7.0/10

**Technology Blog**
1. [When in Doubt, Flail: Experimenting Through Engineering Uncertainty](#item-tech-blog-1) ⭐️ 5.0/10

**Financial News**
1. [US tech selloff: Nasdaq falls 5.28% as Asian markets roll out stabilization measures](#item-finance-news-1) ⭐️ 9.0/10
2. [China Urges US to Withdraw Phone Number Access Limits](#item-finance-news-2) ⭐️ 7.0/10
3. [蚂蚁集团领投Simplexity Robotics 1亿美元融资，估值16亿美元](#item-finance-news-3) ⭐️ 7.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [OpenAI article links perplexity to model intelligence, prompting benchmark debate](https://openai.com/index/perplexity-and-intelligence/) ⭐️ 7.0/10

OpenAI has published an article on the relationship between perplexity and intelligence in language models, framing perplexity—the exponentiated cross-entropy of next-token prediction—as a measure connected to model capability for researchers and engineers comparing models. The full article text was not available with the item, so its specific claims, charts, and any benchmark results could not be independently checked. The piece drew substantial Hacker News discussion focused on whether cross-entropy loss still tracks progress as models rely more on reinforcement learning and reasoning-oriented training.

hackernews · acossta · Nov 22, 17:06 · [Discussion](https://news.ycombinator.com/item?id=50601525)

**「Background」** OpenAI&\#x27;s essay is by chief scientist Jakub Pachocki, who argues for perplexity—equivalently, cross-entropy loss—as a metric for comparing model developers and informing shared safety standards. Perplexity measures how much probability a language model assigns to the tokens that actually occur in a sequence; lower cross-entropy means the model is less surprised by held-out text.

**「Shared Perplexity Evals」** If a single held-out perplexity set is adopted across labs, teams choosing base models would get one comparable pre-training number rather than the growing stack of task-specific benchmark suites. The adoption signal so far is vendor-reported: a Hacker News commenter cited a Mustafa Suleyman post in which Microsoft published MAI-2 Base at 0.819 log-perplexity on OpenAI&\#x27;s evaluation set, a self-reported figure rather than an independent measurement.

**「Community discussion」** Commenters debated the metric&\#x27;s meaning and usefulness: one supplied a plain definition of perplexity as next-token surprise bounded by vocabulary size at worst and 1 at best, while another said it was surprising that cross-entropy trends remained clear despite the shift to RL and welcomed a simpler benchmark. A further commenter argued that prediction or compression rate on raw data is intrinsically the right measure of intelligence, and one relayed a reported Microsoft claim that its MAI-2 Base model had a log-perplexity of 0.819 on OpenAI&\#x27;s evaluation set.

<details><summary>References</summary>
<ul>
<li><a href="https://openai.com/index/perplexity-and-intelligence/">Perplexity and Intelligence | OpenAI</a></li>
<li><a href="https://openai.com/index/perplexity-and-intelligence/">Perplexity and Intelligence | OpenAI</a></li>

</ul>
</details>

**Tags**: `#perplexity`, `#AI evaluation`, `#language models`, `#cross-entropy`, `#OpenAI`

---

<a id="item-tech-news-2"></a>
### [FT Report Alleges Prince Group Figure Helped Smuggle Nvidia Chips to China](https://www.ft.com/content/f3ad8a81-3890-4a8a-8853-ff0a94b08ba9?syn-25a6b1a6=1) ⭐️ 7.0/10

The Financial Times, citing people familiar with the matter, reported that Hu Xiaowei — described by the U.S. Treasury as a “number two” figure in Cambodia’s Prince Group — allegedly helped move Nvidia chips into China through a network that included shell companies, underground financing, and private aircraft. Trade data cited by the FT put the declared value of goods imported by Megaspeed’s Malaysian subsidiary at about $4.6 billion from December 2024 to December 2025, with some chips allegedly reaching China’s black market. Prince Group denied that Hu worked for it and said the allegations about an illegal network and private-aircraft smuggling lacked factual basis. The report rests on unnamed sources and trade data rather than an independently confirmed court finding.

telegram · zaihuapd · Nov 22, 04:34

**「Context」** The report concerns a product category at the center of U.S. export controls: advanced Nvidia AI accelerators whose sale to China is restricted. Those controls make the physical route and financing behind China-bound shipments a key enforcement question, which is the focus of the FT account.

**「Compliance impact」** For compliance and procurement teams handling high-end Nvidia hardware, the operative consequence is that declared import destinations and intermediary paperwork are not sufficient: the FT report alleges that a Malaysian subsidiary declared about $4.6 billion in imports while some chips reached China&\#x27;s black market through shell companies, underground financing, and private aircraft. A separate search result reports that Nvidia put Megaspeed on a &quot;no sell&quot; list in June 2025 and that its team later ran Novagate Cloud, which took in at least $300 million of hardware with Nvidia chips in Malaysia in the first five months of the year, suggesting that blocking one named intermediary may not stop diversion if personnel and operations move.

<details><summary>References</summary>
<ul>
<li><a href="https://actualidad-rt.com/actualidad/639191-hombre-detras-espia-china-nvidia">Quién es el hombre detrás de la &#x27;espía china &#x27; de Nvidia ? - RT</a></li>

</ul>
</details>

**Tags**: `#Nvidia`, `#chip smuggling`, `#export controls`, `#AI hardware`, `#semiconductor supply chain`

---

<a id="item-tech-news-3"></a>
### [Google Reportedly Tests Chrome AI Agent in Simulated Web](https://www.landian.news/archives/128701.html) ⭐️ 7.0/10

A brief Landian News report says Google built an isolated simulated internet environment, called “Mirror Dimension,” to test Chrome’s AI agent as it opens websites, searches, logs in, adds items to carts, and completes tasks. The environment reportedly contains thousands of simulated websites, gives each engineer a separate isolated test setup, and runs more than 1,000 test cases per day, with emphasis on defending against prompt-injection attacks from malicious webpages. The report provides limited technical detail and no primary-source confirmation from Google.

telegram · zaihuapd · Nov 23, 01:30

**「Background」** Browser agents such as Chrome’s must navigate real sites, click through pages, and handle hostile content, so testing them without exposing live accounts or data requires a controlled environment. Google’s Chrome security team describes Mirror Dimension as a synthetic, fully controlled version of the web built for that purpose; Wired reported that Google detailed it publicly for the first time in a blog post, including hidden prompt-injection tests.

<details><summary>References</summary>
<ul>
<li><a href="https://blog.google/security/mirror-dimension-for-agents/">Mirror Dimension for Agents : Evaluating Browser-Use Agents ...</a></li>
<li><a href="https://www.wired.com/story/google-built-a-giant-mirror-dimension-internet-to-test-its-chrome-ai-agents/">Google Built a Giant ‘ Mirror Dimension ’ Internet to Test Its Chrome ...</a></li>

</ul>
</details>

**Tags**: `#Chrome AI agent`, `#prompt injection`, `#AI safety`, `#browser automation`, `#Google`

---

## Technology Blog

<a id="item-tech-blog-1"></a>
### [When in Doubt, Flail: Experimenting Through Engineering Uncertainty](https://seangoedecke.com/when-in-doubt-flail-about/) ⭐️ 5.0/10

rss · Sean Goedecke · Nov 23, 00:00

**「Background」** Engineers facing an unclear situation — no guidance, no obvious starting point — usually assume the responsible move is to wait until they understand things better before acting. Sean Goedecke argues the opposite: in most such cases, cautious delay is the wrong instinct, and deliberately &quot;flailing about&quot; is the fastest route to the understanding you lack.

**「Solution」** Flailing well means doing three things together: try many different things, pay close attention to feedback, and ruthlessly drop whatever isn&\#x27;t getting positive feedback. Trying many things matters because most plans formed under ignorance will be bad, so the odds of finding a good one rise with volume, and because a portfolio of ten plans prevents the over-investment that makes engineers defend a single failing idea. Feedback comes both from more experienced colleagues and from reality itself — whether a change actually lowers latency or moves user metrics. Goedecke applies this to product work \(at GitHub Models, most features and integrations went nowhere, but letting AI inference run from a GitHub Actions token proved sticky and seeded &quot;Continuous AI&quot;\), to engineering \(rather than reading through a huge, fast-changing system, make speculative changes and keep only what shows improvement, with AI agents useful for generating several refactor candidates\), and to organizational problems, where automating manual work or volunteering for tasks mostly won&\#x27;t help but demonstrates effort — and where misreading feedback is most dangerous, since pressing on with a failing plan redirects people&\#x27;s frustration onto you. He concedes the advice is risky: flailing badly damages reputations, and from the inside it feels like repeated failure, a psychological barrier to push through rather than a sign of trouble.

**「Takeaway」** Goedecke&\#x27;s thesis is that effective action under uncertainty looks like undisciplined flailing from the outside but is really a tight loop of cheap experiments and fast abandonment. The discomfort of feeling like you&\#x27;re failing is the expected cost of finding what actually works.

**Tags**: `#engineering practice`, `#uncertainty`, `#experimentation`, `#product development`, `#organizational dynamics`

---

## Financial News

<a id="item-finance-news-1"></a>
### [US tech selloff: Nasdaq falls 5.28% as Asian markets roll out stabilization measures](https://news.bjd.com.cn/2026/11/22/12039852.shtml) ⭐️ 9.0/10

US tech and semiconductor shares sold off sharply on Friday, with the Nasdaq down 5.28% and the Philadelphia Semiconductor Index down nearly 11%, according to an aggregated market report. In response, mainland China lowered its minimum margin-financing ratio to 80%, South Korea is loosening daily share-buyback order limits from Nov 24 for three months, and Taiwan barred short-selling below the previous close from Nov 23 while raising its short-sale margin requirement to 150% from 130%.

telegram · zaihuapd · Nov 22, 13:24

**「Background」** Chip stocks had already slid earlier in November on doubts about the sustainability of the AI investment boom, according to market commentary. China&\#x27;s minimum margin requirement for buying shares with borrowed money had been 100% before the cut to 80%, and lowering it lets investors borrow more, while short-selling curbs restrict bets that a stock will fall.

**「Market impact」** The measures directly change trading conditions for investors and listed companies in these markets: mainland China’s lower margin requirement reduces collateral needed for leveraged purchases, Taiwan’s higher short-selling margin and below-close ban make bearish bets costlier, and South Korea’s relaxed buyback limits let companies buy back more stock.

<details><summary>References</summary>
<ul>
<li><a href="https://www.gate.com/crypto-wiki/article/semiconductor-index-crash-largest-sox-declines">Semiconductor Index Selloffs : Largest SOX Declines | Gate Wiki</a></li>
<li><a href="https://www.zerohedge.com/markets/south-korea-readies-first-market-rescue-fund-deployment-2008">Asian Market Panic Continues As Korea Readies To... | ZeroHedge</a></li>
<li><a href="https://finance.biggo.com/news/41704fd7-7d88-4cb6-8773-17f6b6f5c964">South Korea Restarts Stock Market Stabilization Fund Preparations...</a></li>
<li><a href="https://www.zerohedge.com/markets/south-korea-readies-first-market-rescue-fund-deployment-2008">Asian Market Panic Continues As Korea Readies To... | ZeroHedge</a></li>

</ul>
</details>

**Tags**: `#US tech selloff`, `#semiconductor stocks`, `#Asian market stabilization`, `#margin rules`, `#short-selling restrictions`

---

<a id="item-finance-news-2"></a>
### [China Urges US to Withdraw Phone Number Access Limits](https://www.bloomberg.com/news/articles/2026-11-22/china-objects-to-us-curbs-on-telecoms-access-to-phone-numbers) ⭐️ 7.0/10

China&\#x27;s Commerce Ministry said on Nov. 22 that it wants the US to withdraw restrictions that bar China Mobile, China Telecom and China Unicom from directly accessing US phone numbers. The ministry said the measure violates non-discrimination and fair-competition principles, and that the Federal Communications Commission cited national-security risk without factual basis; the FCC voted on Nov. 19 to add national-security certification for voice-over-internet providers seeking direct access to US numbers, aimed at keeping entities on its Covered List off US networks.

telegram · zaihuapd · Nov 22, 06:44

**「Background」** The FCC voted on Nov. 19 to bar China Mobile, China Telecom and China Unicom from directly accessing U.S. phone numbers on national-security grounds, part of an escalating U.S. crackdown on Chinese telecoms.

<details><summary>References</summary>
<ul>
<li>FCC bans Chinese firms from direct access to US phone numbers in bid to curb robocalls</li>
<li>FCC votes to ban Chinese telecoms from direct access to US phone numbers | Reuters</li>

</ul>
</details>

**Tags**: `#US-China relations`, `#telecom regulation`, `#FCC`, `#Chinese telecom carriers`, `#market decoupling`

---

<a id="item-finance-news-3"></a>
### [蚂蚁集团领投Simplexity Robotics 1亿美元融资，估值16亿美元](https://www.bloomberg.com/news/articles/2026-11-22/ant-group-bets-on-simplexity-to-thrive-in-china-s-humanoid-race) ⭐️ 7.0/10

彭博报道，中国具身智能公司Simplexity Robotics完成1亿美元pre-A轮融资，由蚂蚁集团领投，投后估值16亿美元。公司董事长兼联合创始人Wang Kai向彭博确认，老股东阿里巴巴、腾讯、HongShan和蓝驰创投跟投。

telegram · zaihuapd · Nov 23, 02:02

**「Background」** Simplexity was founded in Hangzhou in July 2025 with a core team drawn from Li Auto. In March it disclosed five funding rounds worth a combined 2 billion yuan within its first six months, at a post-money valuation already above $1 billion, so this round roughly lifts its reported valuation from that level to $1.6 billion.

**「Impact」** The new capital is intended to help Simplexity contest market share with better-established Chinese makers such as Unitree and UBTech, adding competitive pressure in a humanoid-robot market that Morgan Stanley projects will grow from roughly $1–2 billion to $15 billion by 2030.

<details><summary>References</summary>
<ul>
<li><a href="https://www.linkedin.com/posts/melvin-mathew-2a234312a_chinas-humanoid-robot-market-is-projected-activity-7496314077376356352-vSng">China ’s humanoid robot market is projected to grow 15x in five years...</a></li>

</ul>
</details>

**Tags**: `#humanoid robotics`, `#venture funding`, `#Ant Group`, `#China tech`, `#startup valuation`

---