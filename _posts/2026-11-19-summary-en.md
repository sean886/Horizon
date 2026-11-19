---
layout: default
title: "Horizon Summary: 2026-11-19 (EN)"
date: 2026-11-19
lang: en
---

> From 44 items, 13 important content pieces were selected

---

**Technology News**
1. [Google launches Gemini 4 Neon with 1M context and $3 input pricing](#item-tech-news-1) ⭐️ 9.0/10
2. [Wiz reports unauthenticated RCE in Nginx HTTP/2](#item-tech-news-2) ⭐️ 8.0/10
3. [Google DeepMind Releases Genie 4, With Access Details Still Unclear](#item-tech-news-3) ⭐️ 8.0/10
4. [Xint discloses five-nginx-vulnerability chain reaching host root](#item-tech-news-4) ⭐️ 8.0/10
5. [Quad9&\#x27;s France exit and the case against DNS piracy blocking](#item-tech-news-5) ⭐️ 7.0/10
6. [Show HN: Voyager 1 teardown reaches a single memory bit](#item-tech-news-6) ⭐️ 7.0/10
7. [A Walk Through Early x86, From the 4004 to the 486](#item-tech-news-7) ⭐️ 7.0/10
8. [Microsoft announces seven AI models at Ignite 2026](#item-tech-news-8) ⭐️ 7.0/10
9. [US Weighs Requiring Firms to Disclose Chinese AI Use](#item-tech-news-9) ⭐️ 7.0/10

**Financial News**
1. [Fed minutes show further rate hikes expected, AI risks flagged](#item-finance-news-1) ⭐️ 8.0/10
2. [Fed&\#x27;s Waller Floats Half-Point December Rate Hike to &\#x27;Shock&\#x27; Inflation](#item-finance-news-2) ⭐️ 8.0/10
3. [Tencent Q3 2026: capex far above estimates, free cash flow negative](#item-finance-news-3) ⭐️ 8.0/10
4. [China, South Korea say services and investment FTA talks substantively concluded](#item-finance-news-4) ⭐️ 7.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [Google launches Gemini 4 Neon with 1M context and $3 input pricing](https://blog.google/innovation-and-ai/models-and-research/gemini-models/introducing-gemini-4-neon/) ⭐️ 9.0/10

Google released Gemini 4 Neon, a model positioned for complex software engineering, knowledge work, and research workflows, and made it available to developers, enterprises, and Google AI Pro/Ultra subscribers. It is priced at $3 per million input tokens \($0.15 cached\) and $15 per million output tokens, with a 1M-token context window. The release claims first place on Artificial Analysis&\#x27;s coding-agent index at 58.6, third overall on its intelligence index at 61 in the xhigh setting, and 65.2% on Terminal-Bench 4.1; the default high setting is claimed to cut cost per task 32% versus Carbon. These details come from a Telegram post and have not been independently verified.

telegram · zaihuapd · Nov 19, 02:00

**「Neon&\#x27;s place in the Gemini 4 line」** Gemini 4 Neon arrives inside an existing Gemini 4 family rather than as a standalone flagship: the source measures Neon&\#x27;s default high setting against the earlier Gemini 4 Carbon model, reporting a 32% lower cost per task. One commenter reads Google&\#x27;s positioning as complementary rather than a straight replacement, noting that Carbon is still described as the &quot;long horizon&quot; model while Neon posts the higher overall Artificial Analysis score but lower results on research-style evaluations such as CritPt.

**「Token use complicates the low-price pitch」** Teams evaluating Gemini 4 Neon should measure cost per completed task, not just the quoted per-token price: Artificial Analysis reports that the model generated 283M tokens during its Intelligence Index run, versus a 65.1M median. Its explicit reasoning mode can also add latency and token use, so representative workload testing is warranted before migration.

**「Community discussion」** Hacker News commenters complained that overlapping Gemini model names make it hard to map models to use cases, and one argued Neon still felt less capable in general use than Anthropic&\#x27;s Opus 5.5 despite benchmark results. Another commenter noted Carbon remains positioned as the long-horizon model with stronger research-scale reasoning evals, while a user reported Neon serving much faster than Carbon on OpenRouter.

<details><summary>References</summary>
<ul>
<li><a href="https://artificialanalysis.ai/models/gemini-4-neon">Gemini 4 Neon Models - Intelligence... | Artificial Analysis</a></li>
<li><a href="https://benchlm.ai/models/gemini-4-neon">Gemini 4 Neon Pricing , Specs &amp; Sources (November 2026)</a></li>

</ul>
</details>

**Tags**: `#Google`, `#Gemini`, `#LLM release`, `#software engineering`, `#benchmarks`

---

<a id="item-tech-news-2"></a>
### [Wiz reports unauthenticated RCE in Nginx HTTP/2](https://www.wiz.io/blog/nginx-http2-rce-vulnerabilities) ⭐️ 8.0/10

Wiz reports unauthenticated remote code execution vulnerabilities in Nginx&\#x27;s HTTP/2 handling, tracked as CVE-2026-123633 and CVE-2026-123007. The supplied material does not give affected-version ranges, fixed releases, or a patch date; discussion notes that HTTP/2 is not enabled by default, limiting exposure to servers configured to use it.

hackernews · speedping · Nov 18, 15:19 · [Discussion](https://news.ycombinator.com/item?id=50547374)

**「Background」** These flaws are in NGINX&\#x27;s own HTTP/2 handling rather than in application code, so a site can be exposed even when its application is secure. Xint.io&\#x27;s write-up lists affected official nginx releases from 1.9.5 through 1.31.8, and Wiz rates both CVEs Critical with a CVSS 4.0 score of 9.2. The vulnerable code was also present in nginx master as of November 10, 2026, according to Xint.io.

**「Who is exposed and what to do」** Exposure is limited to nginx deployments that have enabled HTTP/2, which is not on by default; a commenter citing W3Techs puts HTTP/2 adoption at roughly 12% of servers, still a large number at internet scale. For those operators, the mitigation raised in the discussion is to disable HTTP/2 until the patched build is deployed — commenter black3r notes the workaround is &quot;as simple as disabling http2&quot; — so sites that never turned the protocol on have no emergency action beyond normal upgrade hygiene.

**「Community discussion」** Commenters focused on exposure and exploitability: one cited W3Techs&\#x27; estimate that about 12% of servers run HTTP/2 and noted it is not enabled by default, while another argued the bug is a non-issue because exploitation requires 128 Gb of HTTP/2 traffic and specific CPU instructions. A separate criticism concerned disclosure timing, with a commenter saying the fix was visible in the open-source repository a week before the advisory and that a public warning to disable HTTP/2 would have been warranted.

<details><summary>References</summary>
<ul>
<li><a href="https://xint.io/blog/nginx2root-remote-code-execution">NGINX 2 Root: New Remote Code Execution Vulnerabilities in nginx ...</a></li>
<li><a href="https://www.wiz.io/blog/nginx-http2-rce-vulnerabilities">Unauthenticated Remote Code Execution in NGINX ... | Wiz Blog</a></li>

</ul>
</details>

**Tags**: `#nginx`, `#http/2`, `#remote code execution`, `#vulnerability disclosure`, `#web server security`

---

<a id="item-tech-news-3"></a>
### [Google DeepMind Releases Genie 4, With Access Details Still Unclear](https://blog.google/innovation-and-ai/models-and-research/google-deepmind/genie-4-now-available-project-genie/) ⭐️ 8.0/10

Google DeepMind published a blog post announcing that Genie 4, the next version of its Genie generative world-model line, is now available. The post itself was not included in the material reviewed, and the only access condition visible in the discussion is the phrase &quot;Eligible Google AI Ultra subscribers.&quot; Commenters trying to use it report that their own Google AI Ultra accounts still advertise Genie 3 rather than Genie 4, leaving open whether the gap reflects a regional rollout, an account-type restriction, or a page that has not been updated. Beyond the availability question, no technical specifications, benchmarks, or regional terms could be confirmed from the supplied material.

hackernews · leumon · Nov 18, 18:49 · [Discussion](https://news.ycombinator.com/item?id=50550415)

**「Background」** Genie is DeepMind&\#x27;s line of generative &quot;world models,&quot; systems that synthesize interactive environments rather than static images or text. One commenter recalls that a previous Genie version was offered in the US only, which is the basis for speculation that the current confusion over who can reach Genie 4 is geographic.

**「Impact」** For prospective users, the practical obstacle is eligibility rather than capability: a commenter reports that their Google Workspace account cannot hold an AI Ultra subscription at all, so they must check access from a personal Gmail account, where the Ultra offering still lists Genie 3. Anyone planning to build on Genie 4 should confirm both their account type and their region before assuming access, since the announcement text does not resolve either condition.

**「Community Discussion」** The most concrete thread is about paying for access: one commenter asks Google to state plainly whether and how they can subscribe, and cannot tell whether their missing Genie 4 is a UK restriction or a stale product page. Others diverge on framing — one long-time reader says the forum focuses on pricing and capability while ignoring potential negative consequences and concludes &quot;I don&\#x27;t want any of this,&quot; while another praises DeepMind&\#x27;s work as craft-driven and questions how it could ever be profitable. A separate comment speculates that world models could eventually serve as game engines, subject to Google&\#x27;s willingness to allow recreations of commercial games.

**Tags**: `#Google DeepMind`, `#generative AI`, `#world models`, `#AI product availability`, `#Hacker News`

---

<a id="item-tech-news-4"></a>
### [Xint discloses five-nginx-vulnerability chain reaching host root](https://nginx2root.com/) ⭐️ 8.0/10

Xint has disclosed NGINX2Root, which it says chains five nginx vulnerabilities and a Linux kernel flaw to take an unauthenticated nginx visitor to host root. The post identifies CVE-2026-123007 as an HTTP/2 flow-control memory-corruption flaw that allows command execution in a worker without authentication. It says nginx 1.30.7 and 1.31.9 fix 10 CVEs, Rapid7 has published a proof-of-concept, and no in-the-wild exploitation is known; the supplied Telegram post has not been independently verified. Teams unable to upgrade should disable externally exposed HTTP/2, according to the disclosure.

telegram · zaihuapd · Nov 18, 16:21

**「Background」** The central HTTP/2 flaw in the chain, CVE-2026-123007, has existed in nginx&\#x27;s open-source code since version 1.9.5, released on September 22, 2015, according to The Hacker News. F5&\#x27;s November 18, 2026 fixes in nginx 1.30.7 and 1.31.9 address the five nginx vulnerabilities that researchers collectively call NGINX2Root, according to Ox Security.

**「Mitigation scope」** For teams that cannot move to nginx 1.30.7 or 1.31.9 immediately, disabling external HTTP/2 is only a partial mitigation: per Ox Security&\#x27;s analysis, it blocks CVE-2026-123007 and CVE-2026-123633 but not the other three flaws in the chain. Those require also disabling HTTP/3, avoiding dynamic upstream address resolution during the request phase, and removing public exposure of the mail proxy or restricting access to it; Rapid7 has published PoC scripts for CVE-2026-123007, so exposed HTTP/2 endpoints should be treated as testable.

<details><summary>References</summary>
<ul>
<li><a href="https://thehackernews.com/2026/11/10-year-old-nginx-http2-flaw-lets.html">10-Year-Old NGINX HTTP / 2 Flaw Lets Unauthenticated Attackers...</a></li>
<li><a href="https://www.ox.security/blog/nginx2root-five-critical-nginx-flaws-expose-web-servers-to-remote-code-execution/">NGINX 2 Root : 5 Critical NGINX RCE Vulnerabilities &amp; CVE Fixes</a></li>
<li><a href="https://www.ox.security/blog/nginx2root-five-critical-nginx-flaws-expose-web-servers-to-remote-code-execution/">NGINX 2 Root : 5 Critical NGINX RCE Vulnerabilities &amp; CVE Fixes</a></li>
<li><a href="https://github.com/sfewer-r7/CVE-2026-123007">GitHub - sfewer-r7/ CVE - 2026 - 123007 : Proof-of-concept ( PoC ) scripts...</a></li>

</ul>
</details>

**Tags**: `#nginx`, `#vulnerability disclosure`, `#HTTP/2`, `#remote code execution`, `#security patching`

---

<a id="item-tech-news-5"></a>
### [Quad9&\#x27;s France exit and the case against DNS piracy blocking](https://techstackups.com/articles/quad9-leaves-france-dns-blocking/) ⭐️ 7.0/10

An analysis argues that DNS resolvers are the wrong enforcement point for fighting piracy, using Quad9&\#x27;s withdrawal from France as its case study. The article frames DNS-level copyright orders as a censorship risk for neutral infrastructure and treats the French episode as evidence that resolver-level blocking is the wrong tool; it is an argument piece rather than a report of new independent measurements.

hackernews · ritzaco · Nov 18, 13:18 · [Discussion](https://news.ycombinator.com/item?id=50545958)

**「Earlier French blocking order」** Quad9 is a public DNS resolver, the lookup layer that turns domain names into IP addresses before a browser can connect. In October 2026 a Paris court ordered it to block 58 domains in a beIN Sports copyright case and, after Quad9 blocked none of them, imposed a €1,000-per-day penalty, according to reports. Quad9 said it could not reliably identify French users in order to apply France-only blocks and announced it would stop serving users in France on November 24.

**「Impact」** French users of Quad9 lose the 9.9.9.9 service on November 24, 2026, when the non-profit stops serving France rather than implement a beIN Sports domain-blocking order, so anyone relying on it must reconfigure to another resolver or fall back to their ISP&\#x27;s DNS. Cloudflare, which documented the withdrawal, argues that forcing public resolvers to block domains is ineffective against infringement, leaving other operators to decide whether to comply with similar orders or exit the market.

**「Community discussion」** Commenters debated whether such blocking is mainly a speech-suppression backdoor or a defensible application of a bad law, with one asking whether anger should target judges or lawmakers. Others argued that piracy is better countered by making legal access cheaper and easier—for example, DRM-free movie downloads at $2–5—than by DNS enforcement.

<details><summary>References</summary>
<ul>
<li>Quad9 Leaves France: Public DNS Resolvers vs Piracy Blocking Orders</li>
<li>Quad9 to stop serving users in France on November 24th - LinkedIn</li>
<li>Quad9 is leaving France, and the hard bit is that both sides have a point</li>
<li><a href="https://techstackups.com/articles/quad9-leaves-france-dns-blocking/">Quad 9 Is Leaving France : Why DNS Resolvers Are... | Tech Stackups</a></li>
<li><a href="https://blog.cloudflare.com/quad9-withdrawal-from-france/">Quad 9 ’s withdrawal from France : A canary in the coal... | Cloudflare Blog</a></li>

</ul>
</details>

**Tags**: `#DNS`, `#internet censorship`, `#copyright enforcement`, `#internet infrastructure`, `#Quad9`

---

<a id="item-tech-news-6"></a>
### [Show HN: Voyager 1 teardown reaches a single memory bit](https://rshekhar.com/voyager/) ⭐️ 7.0/10

A new interactive site posted to Show HN lets visitors take Voyager 1 apart from the spacecraft level down to a single memory chip and even one bit of the command computer&\#x27;s memory. It also maps both Voyagers&\#x27; current positions and the Earth dishes listening to them, opens the nuclear battery to its 24 plutonium spheres, explains how the Golden Record cover teaches playback, and walks through how Voyager 1 was fixed by radio. The creator says Voyager 1 reached one light-day from Earth today and has also posted a four-minute film plus direct links to the RTG, memory chips, Golden Record cover, and repair story.

hackernews · raj-shekhar · Nov 18, 16:18 · [Discussion](https://news.ycombinator.com/item?id=50548161)

**「Background」** A light-day is the distance light travels in 24 hours — about 25.9 billion kilometers, or 16.1 billion miles. NASA puts Voyager 1 at that threshold as of 10:16 UTC on Nov. 18, 2026, the milestone the interactive tour is built around.

**「Community discussion」** Commenters praised the visualization and shared related Golden Record projects, while one asked for a gate-and-trace-level explanation of the memory failure and another questioned whether the site was largely AI-generated and checked against authoritative sources. The creator responded with direct links to the RTG, data-computer memory chips, a single command-computer bit, the Golden Record cover, and the radio-repair story.

<details><summary>References</summary>
<ul>
<li>Voyager 1: What Is a Light-Day - NASA Science</li>
<li>Voyager 1 Passed One Light-Day: Live Distance - Orbital Radar</li>

</ul>
</details>

**Tags**: `#Voyager 1`, `#interactive visualization`, `#spacecraft hardware`, `#computer memory`, `#engineering education`

---

<a id="item-tech-news-7"></a>
### [A Walk Through Early x86, From the 4004 to the 486](https://pikuma.com/blog/history-of-x86-4004-to-486) ⭐️ 7.0/10

pikuma.com has published a detailed historical walkthrough of Intel&\#x27;s early CPU lineage, tracing the 4004 through the 486 with an emphasis on architectural detail. The piece is a historical explainer for systems and hardware readers, not an announcement of new hardware. Hacker News readers supplemented it with corrections and context, including challenges to its account of little-endianness and the relationship between the 4004 and 8008.

hackernews · ibobev · Nov 18, 14:47 · [Discussion](https://news.ycombinator.com/item?id=50546967)

**「What came before the 486」** Intel&\#x27;s 4004, introduced in 1971, is generally described as the first commercial microprocessor, followed by the 8-bit 8008 and 8080 and then the 16-bit 8086/8088 that gave the x86 family its name and instruction set. Later chips in the article&\#x27;s range extended that same instruction set rather than replacing it, so the 386&\#x27;s 32-bit linear memory model and the 486 are presented as stages in one continuous lineage rather than as clean breaks.

**「Community Discussion」** Commenters offered several technical nitpicks: chimpontherun argued that little-endianness originally came from data access speed on the 2200 rather than arithmetic, and that the 8008 and 8080 also had multiplexed address/data buses, not just the 8085. petercooper said Intel engineers including Stan Mazor did modify the 8008 instruction set, while kens stressed that the 4004 and 8008 are unrelated except for shared personnel. skissane separately questioned why modern CPUs still start in a mode compatible with a 1978 chip rather than beginning in long mode or 32-bit protected mode.

<details><summary>References</summary>
<ul>
<li>Evolution of Intel Processor Families | PDF | Intel | Microprocessor - Scribd</li>

</ul>
</details>

**Tags**: `#x86`, `#CPU architecture`, `#computer history`, `#Intel`, `#retrocomputing`

---

<a id="item-tech-news-8"></a>
### [Microsoft announces seven AI models at Ignite 2026](https://microsoft.ai/news/microsoft-ignite-2026/) ⭐️ 7.0/10

Microsoft announced seven new AI models at Ignite 2026, pitching the lineup to developers and enterprises around scalable price-performance. The available announcement material does not specify version numbers, pricing, availability dates, or benchmark results, so the concrete capabilities and shipping status of the lineup remain largely unverified.

hackernews · gmays · Nov 18, 16:08 · [Discussion](https://news.ycombinator.com/item?id=50548021)

**「Background」** Price-performance in AI model releases refers to the trade-off between capability and the cost of running the model, especially at deployment scale. Microsoft&\#x27;s positioning of the seven new models around &quot;scalable price-performance&quot; therefore points to cost and throughput as the main selling point, but the supplied item gives no model names, prices, parameter counts, or availability details to verify that claim.

**「Cost-per-task becomes the comparison」** Teams choosing a coding model now have a cost-based comparison to set against peak benchmark scores: Microsoft claims MAI Code 2 reaches 98% of GPT-6.1 Sol&\#x27;s coding quality at about 40% of the price, and 96% of Opus 5.5&\#x27;s performance at 5% of the price. Those are vendor figures rather than independent measurements, so organizations should validate them on their own workloads before moving spend, and because the lineup splits coding, vulnerability discovery, and image generation into separate specialized models, adoption may mean routing tasks across several models instead of standardizing on one.

**「Community reaction」** A commenter who said they had tested MAI Code 2 called it &quot;quite good&quot; for their usual work and did not strongly dispute comparisons to Opus or Sol. Another argued Microsoft should release some models as open source or open weight to secure market share, warning of a &quot;Windows Phone OS&quot; outcome, while others criticized the keynote and Microsoft&\#x27;s competitiveness.

<details><summary>References</summary>
<ul>
<li><a href="https://microsoft.ai/news/microsoft-ignite-2026/">Seven new world class models at scalable... | Microsoft AI</a></li>
<li><a href="https://forklog.com/en/microsoft-unveils-ai-models-for-coding-and-cybersecurity/">Microsoft unveils AI models for coding and cybersecurity | ForkLog</a></li>
<li><a href="https://finance.yahoo.com/markets/article/microsoft-ignite-focuses-on-ai-models-for-specific-tasks-lowering-costs-for-enterprise-203433266.html">Microsoft &#x27;s AI pitch at Ignite : Cheaper models as business &#x27;token...</a></li>

</ul>
</details>

**Tags**: `#Microsoft`, `#LLMs`, `#AI model releases`, `#price-performance`, `#Hacker News`

---

<a id="item-tech-news-9"></a>
### [US Weighs Requiring Firms to Disclose Chinese AI Use](https://www.reuters.com/world/china/trump-administration-weighs-forcing-us-firms-disclose-chinese-ai-use-2026-11-18/) ⭐️ 7.0/10

The Trump administration is reportedly considering requiring US companies to publicly disclose their use of Chinese AI models, with the Treasury Department and the White House Office of Science and Technology Policy having discussed the proposal, according to Reuters. The reported aim is to discourage reliance on inexpensive Chinese open-weight models through public naming rather than by imposing new restrictions. Under the reported plan, affected companies would have to publish the disclosure on their websites; Reuters cited Airbnb&\#x27;s use of Alibaba&\#x27;s Qwen for customer service as an example. It remains unclear whether the proposal has internal administration support or will proceed to formal legislation.

telegram · zaihuapd · Nov 19, 02:30

**「Background」** Open-weight models are AI systems whose trained parameters are released for others to download and run, often making them cheaper to deploy than closed models accessed only through vendor APIs. The Reuters report cites Airbnb&\#x27;s use of Alibaba&\#x27;s Qwen for customer service as an example of the corporate reliance on Chinese open-weight models that the disclosure proposal would target.

**「Disclosure burden」** If adopted, firms such as Airbnb—which reportedly relies heavily on Alibaba&\#x27;s Qwen for its AI customer-service agent—would have to publicly identify that use on their websites, turning model provenance into a disclosure and procurement-review item even though the reported plan would not ban the models.

<details><summary>References</summary>
<ul>
<li>Airbnb picks Alibaba&#x27;s Qwen over ChatGPT in a win for Chinese open ...</li>
<li>Airbnb CEO Brian Chesky Called Chinese AI Fast And Cheap. Now ...</li>

</ul>
</details>

**Tags**: `#AI regulation`, `#China AI`, `#open-weight models`, `#US tech policy`, `#AI procurement`

---

## Financial News

<a id="item-finance-news-1"></a>
### [Fed minutes show further rate hikes expected, AI risks flagged](https://www.cnbc.com/2026/11/18/fed-minutes-october-2026.html) ⭐️ 8.0/10

Minutes from the Federal Reserve’s October meeting released Wednesday showed that almost all officials judged further rate increases would likely be appropriate to return inflation to 2%, after the committee voted 10-2 to hold its benchmark rate at 3.75%-4%, with both dissents favoring a quarter-point increase. The minutes also flagged artificial-intelligence demand as a material inflation risk and rapid, opaque AI-related borrowing as a financial-stability concern.

rss · CNBC Finance · Nov 18, 19:41

**「Background」** The Fed targets 2% inflation, and the report said inflation remained well above that goal; October CPI rose 0.4% for all items and 0.3% for core prices, each 0.1 percentage point above expectations.

**Tags**: `#Federal Reserve`, `#monetary policy`, `#interest rates`, `#inflation`, `#AI financial risk`

---

<a id="item-finance-news-2"></a>
### [Fed&\#x27;s Waller Floats Half-Point December Rate Hike to &\#x27;Shock&\#x27; Inflation](https://www.cnbc.com/2026/11/18/federal-reserve-governor-christopher-waller.html) ⭐️ 8.0/10

Federal Reserve Governor Christopher Waller said Wednesday the central bank may need to &quot;shock people&quot; with a half-percentage-point rate increase at the Dec. 8-9 policy meeting, arguing it should first reverse the three quarter-point cuts made in 2025. His call is a proposal rather than a decision: futures markets fully price only a quarter-point December move, and other officials, including New York Fed President John Williams, have backed more gradual tightening.

rss · CNBC Finance · Nov 18, 15:13

**「Background」** The Fed had cut rates three times in 2025, then raised its benchmark rate in September 2026 for the first time in more than three years and left it unchanged in October. Inflation has remained above 3%—above the Fed’s 2% target—after energy prices spiked following U.S. and Israeli strikes on Iran in late February and tariff effects persisted.

**「Impact」** If a half-point increase were approved instead of the quarter-point move markets fully price, short-term borrowing costs would rise faster for households and businesses with variable-rate credit cards, auto loans and credit lines.

<details><summary>References</summary>
<ul>
<li>Waller says on CNBC the Fed needs to get more aggressive in inflation ...</li>

</ul>
</details>

**Tags**: `#Federal Reserve`, `#interest rates`, `#inflation`, `#monetary policy`, `#Christopher Waller`

---

<a id="item-finance-news-3"></a>
### [Tencent Q3 2026: capex far above estimates, free cash flow negative](https://api3.cls.cn/share/article/2537922?os=android&amp;amp;sv=8.8.5&amp;amp;app=cailianpress&amp;amp;selected=) ⭐️ 8.0/10

Tencent’s 2026 third-quarter revenue rose 8% year on year to 207.3 billion yuan, below market expectations, while net profit attributable to shareholders edged up 0.8% to 63.6 billion yuan. Capital expenditure reached 81.433 billion yuan, far above the 55.4 billion yuan estimate, leaving free cash flow—cash left after capital spending—at negative 69.1 billion yuan.

telegram · zaihuapd · Nov 18, 09:20

**「Background」** Tencent’s 8% year-on-year revenue growth in Q3 2026 was a slowdown from 11% in the previous quarter.

<details><summary>References</summary>
<ul>
<li><a href="https://www.freemalaysiatoday.com/category/business/2026/11/18/china-tech-giant-tencent-s-quarterly-revenue-growth-slows">China tech giant Tencent ’s quarterly revenue growth slows | FMT</a></li>

</ul>
</details>

**Tags**: `#Tencent`, `#earnings`, `#AI capex`, `#free cash flow`, `#China tech`

---

<a id="item-finance-news-4"></a>
### [China, South Korea say services and investment FTA talks substantively concluded](https://x.com/Jaemyung_Lee/status/2122988472994791476) ⭐️ 7.0/10

China and South Korea said on Nov. 18 that they had substantively concluded follow-up negotiations to their free trade agreement covering services and investment, with China pledging most-favored-nation treatment for Korean films and games and wider openings in tourism, legal, construction and finance.

telegram · zaihuapd · Nov 18, 10:02

**「Background」** The follow-up talks, launched in March 2018 and running 8 years and 8 months, build on the existing China–South Korea free trade agreement; &quot;most-favored-nation&quot; treatment means Korean films and games would face no tougher conditions in China than suppliers from any other country, though some technical items are still left to working-level talks.

**「Who is affected」** Korean film, game and broadcast producers stand to gain, since most-favoured-nation treatment means China would apply to them the same terms it gives other foreign suppliers, while the wider co-production scope covers TV dramas, animation, variety shows and documentaries as well as films.

**Tags**: `#China-South Korea FTA`, `#services and investment`, `#trade liberalization`, `#film and games`, `#audiovisual co-production`

---