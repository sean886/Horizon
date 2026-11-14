---
layout: default
title: "Horizon Summary: 2026-11-14 (EN)"
date: 2026-11-14
lang: en
---

> From 41 items, 9 important content pieces were selected

---

**Technology News**
1. [Report: TorchTitan trains 1T MoE at 1,300 tokens/s per GH200](#item-tech-news-1) ⭐️ 8.0/10
2. [Orcas Airband streams live airband with dual-GPU SDR](#item-tech-news-2) ⭐️ 7.0/10
3. [ICML 2027 CFP Adds Two-Stage Review and Reviewer-Author Caps](#item-tech-news-3) ⭐️ 7.0/10
4. [Microsoft Outlook, Teams Outage Lasts More Than 12 Hours](#item-tech-news-4) ⭐️ 7.0/10
5. [DeepSeek opens app-level APIs for search, files, OCR and voice](#item-tech-news-5) ⭐️ 7.0/10
6. [OpenAI launches ChatGPT Wallet for agent-initiated purchases](#item-tech-news-6) ⭐️ 7.0/10

**Financial News**
1. [Lutnick faces Nvidia scrutiny as his sons&\#x27; firm cut reported stake nearly 50%](#item-finance-news-1) ⭐️ 8.0/10
2. [Chicago Fed&\#x27;s Goolsbee Says Central Bank &\#x27;Has Definitely Got Work to Do&\#x27; on Inflation](#item-finance-news-2) ⭐️ 8.0/10
3. [Jensen Huang resigns from Nvidia amid China spy scrutiny](#item-finance-news-3) ⭐️ 8.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [Report: TorchTitan trains 1T MoE at 1,300 tokens/s per GH200](https://www.reddit.com/r/MachineLearning/comments/1xvce5h/scaling_to_1t_moe_on_torchtitan_p/) ⭐️ 8.0/10

A Reddit experience report from a team working with TorchTitan and PyTorch maintainers says it reached about 1,300 tokens/s per GPU while training a ~1T-parameter mixture-of-experts model on 384 GH200 GPUs, a 14x improvement over its initial setup. The configuration used 384-way FSDP plus 4-way expert parallelism kept inside each node, and deliberately skipped pipeline parallelism to avoid long steps and slow failure discovery. Reported gains came from full activation checkpointing and Grace offload, Muon, FlexShard expert sharding, attention-cost load balancing, bf16 gradient transfer with fp32 local accumulation, FP8 expert all-gather, and an allocator fix; the figures are the authors&\#x27; experience-report results, not independently verified benchmarks.

reddit · r/MachineLearning · /u/f14-bertolotti · Nov 13, 16:28

**「Background」** TorchTitan is a PyTorch-native library for distributed training of large models; PyTorch&\#x27;s write-up describes this run as using 384 GH200 GPUs across 96 nodes. A ~1T-parameter mixture-of-experts model cannot fit on one GPU, so the work depends on sharding both dense parameters and experts across ranks—making the interconnect hierarchy, including the much slower inter-node InfiniBand link compared with the Grace–Hopper C2C connection, the central constraint.

**「Impact」** Teams attempting similar MoE training on GH200 clusters should plan around inter-node bandwidth: the report measured about 25 GB/s per GPU over InfiniBand and kept 4-way expert parallelism node-local so the token all-to-all did not dominate. That makes node-local NVLink/C2C placement and communication-specific collectives, rather than model code alone, a prerequisite for reproducing the reported throughput.

<details><summary>References</summary>
<ul>
<li><a href="https://pytorch.org/blog/training-a-1t-parameter-moe-on-eu-public-infrastructure-with-pytorch-and-torchtitan/">Training a 1T-Parameter MoE on EU public ... - PyTorch</a></li>

</ul>
</details>

**Tags**: `#TorchTitan`, `#Mixture-of-Experts`, `#distributed training`, `#PyTorch`, `#GH200`

---

<a id="item-tech-news-2"></a>
### [Orcas Airband streams live airband with dual-GPU SDR](https://orcasairband.com/) ⭐️ 7.0/10

Orcas Airband is running a live software-defined radio feed from KORS that the operator says monitors the entire airband using an Ettus B210 and a dual RTX 4090 machine, with CUDA-based polyphase channelization, demodulation, transmission detection, and raw transcripts. According to the operator, data transmissions are discarded and the published transcripts are unedited; no independent coverage or accuracy measurements were provided. Commenters used the feed during a Vancouver-area ground stop, quoting a 14:03 exchange confirming a ground stop into Vancouver and a Victoria Ground transmission saying traffic had been stopped.

hackernews · mmaunder · Nov 13, 22:04 · [Discussion](https://news.ycombinator.com/item?id=50490593)

**「Background」** Airband voice traffic occupies VHF frequencies around 118–137 MHz, and conventional scanners generally demodulate one tuned channel at a time. A wideband software-defined radio such as the ETTUS B210 can capture much of that span at once; GPU-based polyphase channelization then splits the capture into many narrow channels so each can be demodulated and transcribed in parallel.

**「What the transcripts were good for」** During the FAA&\#x27;s nationwide ground stop on Nov. 13, 2026 — which delayed hundreds of flights at YVR before being lifted — the site gave listeners public, near-real-time access to the relevant controller frequencies: the operator posted time-stamped raw transcripts from Victoria Ground on 126.400 and Vancouver Centre on 134.800, and a commenter cited a 14:03 exchange confirming the Vancouver ground stop. The practical caveat is reliability: the transcripts are unedited machine output from a single hobbyist B210/dual-4090 receiver, and one commenter said roughly half the transmissions were hard to understand, so they work as situational awareness rather than an authoritative record of what controllers said.

**「Community discussion」** Commenters found the feed useful for following the ground stop, while another said many transmissions were hard to understand and asked whether airband remains analog for security or interoperability reasons. A separate commenter compared it to a hobby project that decodes ships&\#x27; DSC signals from public KiwiSDR receivers.

<details><summary>References</summary>
<ul>
<li><a href="https://www.vancouverisawesome.com/travel/us-flights-grounded-yvr-cancellations-delays-nov-2026-13016578">All US flights grounded: Dozens of YVR flights cancelled ...</a></li>
<li><a href="https://news.yvr.ca/us-bound-flight-disruption/">U.S. ground stop lifted - news.yvr.ca</a></li>

</ul>
</details>

**Tags**: `#software-defined radio`, `#GPU signal processing`, `#CUDA`, `#aviation communications`, `#real-time monitoring`

---

<a id="item-tech-news-3"></a>
### [ICML 2027 CFP Adds Two-Stage Review and Reviewer-Author Caps](https://www.reddit.com/r/MachineLearning/comments/1xvkxbj/icml_2027_changes_d/) ⭐️ 7.0/10

According to a Reddit summary of the ICML 2027 call for papers, the conference will use a two-stage review in which an area chair decides whether a paper advances to full review, with any proposed first-stage rejection confirmed by a senior area chair and a short justification sent to authors by February 23. The policy also reportedly caps any individual at 20 submissions, requires every paper to name a reciprocal reviewer from its author list \(at most six papers per reviewer\), and requires anyone with three or more submissions to serve on the program committee, with non-compliant papers subject to desk rejection. The poster singles out the limit of one paper per author that has no eligible reciprocal reviewer among its authors as the biggest change. These details are a community reading of the CFP rather than an official announcement, and the poster links the document at icml.cc.

reddit · r/MachineLearning · /u/Gravitist · Nov 13, 21:53

**「Prior reciprocal reviewing requirement」** ICML already operated a reciprocal reviewing arrangement under which authors are expected to review for the conference; the 2027 rules describe that requirement as being strengthened rather than introduced from scratch. ICML&\#x27;s own explanation for the change is that submissions have been growing faster than the pool of qualified reviewers, which it says threatens a fair and informative review process.

**「Impact」** Authors who routinely list undergraduates, interns, or collaborators outside the field as coauthors can now put their name on only one paper per cycle that lacks an eligible reviewer from within the author list, so groups should confirm reviewer eligibility before submitting. Anyone reaching three or more submissions must also plan for program-committee service, and papers missing a required reciprocal reviewer risk desk rejection.

<details><summary>References</summary>
<ul>
<li><a href="https://icml.cc/Conferences/2027/ReciprocalReviewingAndSubmissionQuotas">2027 Reciprocal Reviewing And Submission Quotas - icml.cc</a></li>

</ul>
</details>

**Tags**: `#ICML`, `#peer review`, `#machine learning research`, `#conference policy`, `#reviewer load`

---

<a id="item-tech-news-4"></a>
### [Microsoft Outlook, Teams Outage Lasts More Than 12 Hours](https://www.reuters.com/technology/microsoft-365-outlook-down-thousands-us-users-downdetector-shows-2026-11-12/) ⭐️ 7.0/10

Microsoft Outlook, Teams and Copilot experienced a global outage lasting more than 12 hours on November 13, disrupting enterprise and government communications. Microsoft attributed the disruption to a server issue, said it found no malicious activity, and reported that it had expanded remediation and was seeing signs of stabilization. The report described it as Microsoft 365&\#x27;s second service disruption this year but did not provide a complete root cause or a full recovery time.

telegram · zaihuapd · Nov 13, 12:21

**「Context」** Outlook, Teams and Copilot are part of Microsoft 365, Microsoft&\#x27;s cloud productivity suite, and rely on the company&\#x27;s cloud infrastructure, so a server-side fault can disrupt several services at once. The source notes that this was the second Microsoft 365 service interruption this year, but it does not identify the earlier incident or say whether the two shared a cause.

**「Impact」** The disruption forced affected organizations onto fallback channels: Euronext&\#x27;s email was blocked, and some Taiwanese financial institutions used fax to confirm transactions, while government agencies in Australia, Japan and the U.S. were also affected.

**Tags**: `#Microsoft 365`, `#Outlook`, `#Teams`, `#service outage`, `#cloud reliability`

---

<a id="item-tech-news-5"></a>
### [DeepSeek opens app-level APIs for search, files, OCR and voice](https://mp.weixin.qq.com/s/78KBHc4-4N5b2vfL9SkutQ) ⭐️ 7.0/10

DeepSeek announced it has opened app-level conversational APIs that let developers enable deep-thinking search, file input, link reading and voice capabilities through parameters in its existing API, with the server handling tool calls and context assembly. The company says its V4.1-Flash model is supported on three interfaces, while Search, Fetch, OCR, ASR and TTS can also be called separately. It additionally open-sourced a chat frontend demo that can import conversation history and be deployed locally.

telegram · zaihuapd · Nov 13, 14:27

**「Existing API entry point」** DeepSeek&\#x27;s existing chat API remains the entry point: developers obtain an API key, select a model such as \`deepseek-flash\` or \`deepseek-v4-pro\`, and enable the new application-level parameters. DeepSeek&\#x27;s official API documentation corroborates that the release covers web search, file input, link reading, model safety, ASR and TTS, and links to a usage guide.

**「Impact」** Developers using DeepSeek&\#x27;s existing API can add these capabilities by turning on parameters instead of wiring separate search, OCR or speech services themselves, and can start from the open-source demo if they need a deployable chat frontend with imported history.

<details><summary>References</summary>
<ul>
<li><a href="https://api-docs.deepseek.com/zh-cn/">首次调 用 API | DeepSeek API Docs</a></li>

</ul>
</details>

**Tags**: `#DeepSeek`, `#API`, `#AI agents`, `#open source`, `#multimodal`

---

<a id="item-tech-news-6"></a>
### [OpenAI launches ChatGPT Wallet for agent-initiated purchases](https://openai.com/index/introducing-chatgpt-wallet/) ⭐️ 7.0/10

According to a short Telegram summary, OpenAI launched ChatGPT Wallet with American Express, Mastercard and Visa, allowing agents to pay without receiving users&\#x27; real card numbers. The payment networks issue tokens that replace the actual card number. The item says the wallet is available starting today in the U.S. to ChatGPT Pro subscribers aged 18 and older with U.S.-issued cards, through a service it calls &quot;dots.&quot; Each purchase requires the user to review the item and amount and confirm with Face ID or a fingerprint; the summary offers limited technical detail and no independent confirmation.

telegram · zaihuapd · Nov 13, 15:43

**「Background」** Payment-network tokenization replaces a real card number with a network-issued surrogate that can be restricted or revoked, which is the mechanism ChatGPT Wallet uses for agent purchases. OpenAI&\#x27;s announcement names American Express, Mastercard, and Visa as partners and limits the initial rollout to U.S. ChatGPT Pro subscribers through dots; CNBC reports those cardholders keep their existing credit-card rewards.

**「Impact」** For affected U.S. Pro users, agent-initiated purchases remain gated by item-and-amount review and biometric confirmation, so the wallet is designed for supervised checkout rather than unattended spending. Users also need an eligible Pro subscription and a U.S.-issued card to take part.

<details><summary>References</summary>
<ul>
<li><a href="https://openai.com/index/introducing-chatgpt-wallet/">Introducing ChatGPT Wallet | OpenAI</a></li>
<li><a href="https://www.cnbc.com/2026/11/13/openai-chatgpt-wallet-dot-purchases.html">OpenAI &#x27;s ChatGPT Wallet allows &#x27; dots &#x27; AI agents to make purchases</a></li>

</ul>
</details>

**Tags**: `#OpenAI`, `#agentic payments`, `#ChatGPT Wallet`, `#tokenization`, `#AI agents`

---

## Financial News

<a id="item-finance-news-1"></a>
### [Lutnick faces Nvidia scrutiny as his sons&\#x27; firm cut reported stake nearly 50%](https://www.cnbc.com/2026/11/13/howard-lutnick-nvidia-jensen-huang-china-cantor-fitzgerald.html) ⭐️ 8.0/10

CNBC reported that Cantor Fitzgerald — the Wall Street firm formerly led by Commerce Secretary Howard Lutnick and now run by his sons Brandon and Kyle — cut its reported Nvidia share count by 49% between September 2025 and March 2026, from 3.5 million shares worth $652 million to 1.78 million worth $310 million, while continuing to arrange billions of dollars in financing for the chipmaker&\#x27;s business partners. The scrutiny follows Axios reporting, citing unnamed sources, that Lutnick resisted a crackdown on companies suspected of smuggling Nvidia AI chips to China, and Thursday&\#x27;s resignation of Nvidia CEO Jensen Huang; CNBC said there is no evidence of wrongdoing or that Cantor&\#x27;s holdings changes were tied to intelligence warnings about Huang.

rss · CNBC Finance · Nov 13, 23:42

**「Background」** The scrutiny follows Nvidia CEO Jensen Huang’s resignation after a scandal involving an alleged spy \(tool-2-2\); reports said he had an affair with a former Megaspeed executive whom U.S. intelligence suspected China’s Ministry of State Security had recruited \(tool-2-1\). Megaspeed, a Singapore-based buyer of Nvidia’s AI chips, has faced questions over whether it is a front for Beijing \(tool-1-2\).

**「Who would be affected」** If Commerce acts on the entity-list push, Megaspeed and similar firms suspected of diverting Nvidia chips would need US licences to buy them, closing off a supply route Chinese AI developers have used.

<details><summary>References</summary>
<ul>
<li><a href="https://www.cbsnews.com/news/megaspeed-nvidia-china-ties/">Megaspeed&#x27;s vacant offices raise questions about ties to ...</a></li>
<li><a href="https://en.wikipedia.org/wiki/Jensen_Huang_spying_scandal">Jensen Huang spying scandal - Wikipedia</a></li>
<li><a href="https://www.cbsnews.com/news/nvidia-ceo-jensen-huang-resigns/">Nvidia CEO Jensen Huang resigns in wake of affair with woman ...</a></li>
<li><a href="https://www.cnbc.com/2026/11/12/nvidia-megaspeed-alice-huang-jensen-.html">What we know so far about Nvidia partner Megaspeed’s Asia ...</a></li>
<li><a href="https://www.nbcnews.com/tech/tech-news/nvidia-chips-loophole-export-ruleschinese-companies-access-megaspeed-rcna608601">How Chinese companies access Nvidia chips through a loophole ...</a></li>

</ul>
</details>

**Tags**: `#Nvidia`, `#US-China export controls`, `#semiconductors`, `#Commerce Department ethics`, `#corporate governance`

---

<a id="item-finance-news-2"></a>
### [Chicago Fed&\#x27;s Goolsbee Says Central Bank &\#x27;Has Definitely Got Work to Do&\#x27; on Inflation](https://www.cnbc.com/2026/11/13/chicago-feds-goolsbee-says-central-bank-has-definitely-got-work-to-do-on-inflation.html) ⭐️ 8.0/10

Chicago Fed President Austan Goolsbee said the Federal Reserve &quot;has definitely got work to do&quot; to reestablish its inflation-fighting credibility, after the Labor Department reported October producer prices rose 6.5% from a year earlier — the fastest annual pace since November 2022 — and futures markets fully priced a quarter-point rate increase at the Dec. 8-9 policy meeting.

rss · CNBC Finance · Nov 13, 14:22

**「Background」** The Fed targets 2% annual inflation, but Goolsbee said inflation has remained above that level for almost six years; October wholesale prices rose 6.5% from a year earlier, the highest since November 2022.

**「Impact」** If the Fed raises rates as those markets expect, borrowing costs would climb for households and businesses carrying variable-rate debt such as credit cards and adjustable-rate mortgages, though the move is currently a market expectation rather than a decision.

<details><summary>References</summary>
<ul>
<li><a href="https://www.cnbc.com/2026/11/13/ppi-inflation-report-october-2026.html">PPI inflation report October 2026 - CNBC</a></li>

</ul>
</details>

**Tags**: `#Federal Reserve`, `#inflation`, `#producer price index`, `#monetary policy`, `#interest rate expectations`

---

<a id="item-finance-news-3"></a>
### [Jensen Huang resigns from Nvidia amid China spy scrutiny](https://www.cnbc.com/2026/11/13/jensen-huang-nvidia-us-china-relations.html) ⭐️ 8.0/10

Jensen Huang resigned from Nvidia on Thursday and agreed to testify before Congress by Nov. 26 amid scrutiny of an alleged affair with a woman reported to be a Chinese spy. The espionage allegation is unconfirmed, and it is unclear whether any sensitive information was shared.

rss · CNBC Finance · Nov 13, 02:56

**「Background」** Washington has restricted Nvidia&\#x27;s advanced chip sales to China since 2022, though the Trump administration eased many Biden-era limits in 2025, and Huang had argued U.S. technology needed to be used in China to stay globally relevant.

**「Impact」** Analysts cited by CNBC expect Congress may tighten chip export rules before year-end, which could limit U.S. chipmakers&\#x27; China sales and prompt Beijing to restrict rare-earth or chipmaking-material supplies.

**Tags**: `#Nvidia`, `#U.S.-China relations`, `#semiconductor export controls`, `#corporate governance`, `#espionage allegation`

---