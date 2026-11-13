---
layout: default
title: "Horizon Summary: 2026-11-13 (EN)"
date: 2026-11-13
lang: en
---

> From 53 items, 14 important content pieces were selected

---

**Technology News**
1. [Rust 1.100 stabilizes never type, custom allocators, and Cargo cooldowns](#item-tech-news-1) ⭐️ 9.0/10
2. [Chips and Cheese Interviews AMD&\#x27;s Mike Clark on Zen 6](#item-tech-news-2) ⭐️ 8.0/10
3. [PostgreSQL Type-Confusion Primitive Turned Into RCE in CVE-2026-6460](#item-tech-news-3) ⭐️ 8.0/10
4. [Anthropic IPO discussion centers on valuation, revenue, and compute commitments](#item-tech-news-4) ⭐️ 8.0/10
5. [SemiAnalysis Claims Jensen Huang Has Left Nvidia](#item-tech-news-5) ⭐️ 8.0/10
6. [US Commerce Department Reportedly Finalizing Rule on Remote AI Chip Access](#item-tech-news-6) ⭐️ 8.0/10
7. [Microsoft 365 email outage stretches hours for large organizations](#item-tech-news-7) ⭐️ 7.0/10
8. [Google&\#x27;s Gemini 4 Hydrogen launch draws questions on naming and pricing](#item-tech-news-8) ⭐️ 7.0/10
9. [Open-source project claims 16B LLM inference on sub-1GB devices](#item-tech-news-9) ⭐️ 7.0/10
10. [UMAP 0.6 Adds New Initialization and Optimizers](#item-tech-news-10) ⭐️ 7.0/10
11. [Audit finds Meta&\#x27;s TRIBE v2 lacks retinotopic and tonotopic maps](#item-tech-news-11) ⭐️ 7.0/10
12. [Apple details Secure Exclaves audio/video isolation and hardware-verified privacy indicator](#item-tech-news-12) ⭐️ 7.0/10
13. [Unverified warning claims Telegram Widgets RCE flaw](#item-tech-news-13) ⭐️ 7.0/10

**Financial News**
1. [China approves Eli Lilly&\#x27;s oral weight-loss pill, a first for the country](#item-finance-news-1) ⭐️ 8.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [Rust 1.100 stabilizes never type, custom allocators, and Cargo cooldowns](https://blog.rust-lang.org/2026/11/12/Rust-1.100.0/) ⭐️ 9.0/10

Rust 1.100, released on November 12, 2026, stabilizes the never type and custom allocators and adds several Cargo changes. Cargo can now enforce a minimum publish age, also called dependency cooldowns under RFC 3923: when configured, the resolver ignores versions published more recently unless they are already in Cargo.lock. \`cargo install\` now uses the lockfile inside the \`.crate\` tarball by default, making \`--locked\` a no-op, and Cargo reports unused dependencies with \`cargo::unused\_dependencies\` set to \`warn\` by default. Commenters also noted stabilized APIs absent from the blog post, including \`bool::toggle\(\)\`, \`Box::map\(\)\`, and \`str::trim\_prefix\(\)\`/\`trim\_suffix\(\)\`.

hackernews · mbStavola · Nov 12, 18:39 · [Discussion](https://news.ycombinator.com/item?id=50472038)

**「Background」** The never type and the allocator API had been tracked as unstable Rust features for years before landing in stable form here. Cargo&\#x27;s new dependency cooldown implements RFC 3923, which adds a \`min-publish-age\` configuration option, and the behavior is opt-in rather than a default resolver policy.

**「Impact」** For projects that enable a minimum publish age, routine dependency resolution will deliberately lag newly published crates until the configured window passes, unless the version is already pinned in \`Cargo.lock\`.

**「Community Discussion」** Commenters welcomed the release as unusually large, with one pointing to stabilized APIs the blog post did not mention, such as \`bool::toggle\(\)\` and \`Box::map\(\)\`. Another questioned whether compiler performance had improved and reported long compile times and needing to run \`cargo clean\` regularly to remove about 90 GB of temporary files.

<details><summary>References</summary>
<ul>
<li><a href="https://byteiota.com/rust-1100-cargo-cooldowns/">Rust 1 . 100 : Cargo Dependency Cooldowns Are Here... | byteiota</a></li>
<li><a href="https://rust-lang.github.io/rfcs/3923-cargo-min-publish-age.html">3923 - cargo -min-publish-age - The Rust RFC Book</a></li>

</ul>
</details>

**Tags**: `#Rust`, `#Cargo`, `#programming languages`, `#compilers`, `#open source`

---

<a id="item-tech-news-2"></a>
### [Chips and Cheese Interviews AMD&\#x27;s Mike Clark on Zen 6](https://chipsandcheese.com/p/talking-zen-6-with-mike-clark-at) ⭐️ 8.0/10

Chips and Cheese published an in-depth interview with AMD&\#x27;s Mike Clark focused on Zen 6, the next generation of AMD&\#x27;s CPU core architecture. The item supplied here contains no architectural specifics — no core counts, cache sizes, process node, release timing, or performance figures — so the concrete technical claims made in the discussion cannot be summarized or verified from this material. The piece drew notable attention from hardware-focused readers on Hacker News.

hackernews · dverlaeckt80 · Nov 12, 14:12 · [Discussion](https://news.ycombinator.com/item?id=50467460)

**「Zen&\#x27;s unified origins」** AMD introduced Zen as a single scalable microarchitecture meant to span high-power and low-power segments, replacing its earlier split between separate CPU designs; Tom&\#x27;s Hardware reported at the time that Mike Clark described the transition away from that segmented playbook as a challenge. Clark, the AMD designer interviewed in this discussion, was already involved in explaining that unified approach during Zen&\#x27;s original rollout. Zen 6 is the next generation in that same architecture line.

**「Community Discussion」** One commenter described the article as interesting and noted that it is very rare to see CPU designers discuss their work at this level of depth. That is a reader&\#x27;s impression of the interview&\#x27;s depth rather than an assessment of any specific claim in it.

<details><summary>References</summary>
<ul>
<li><a href="https://www.tomshardware.com/news/amd-zen-cpu-microarchitecture,32540.html">Everything Zen : AMD Presents New... | Tom&#x27;s Hardware</a></li>

</ul>
</details>

**Tags**: `#computer architecture`, `#AMD`, `#Zen 6`, `#CPUs`, `#hardware`

---

<a id="item-tech-news-3"></a>
### [PostgreSQL Type-Confusion Primitive Turned Into RCE in CVE-2026-6460](https://mehmetince.net/part-3-6-how-i-ended-up-turning-a-22-year-old-postgresql-type-confusion-primitive-into-rce-cve-2026-6460/) ⭐️ 8.0/10

A researcher&\#x27;s write-up describes turning a 22-year-old PostgreSQL type-confusion primitive into remote code execution, tracked as CVE-2026-6460. The post walks through PostgreSQL internals and the path to a zero-day, according to the item&\#x27;s analysis summary. Commenters dispute whether the result is best described as RCE or privilege escalation, arguing the exploit path requires an authenticated SQL session.

hackernews · ozirus · Nov 12, 18:22 · [Discussion](https://news.ycombinator.com/item?id=50471761)

**「Background」** PostgreSQL&\#x27;s advisory for CVE-2026-6460 describes a type-confusion flaw that lets an object creator execute arbitrary code as the operating-system user running the database, primarily through \`ALTER ... SET DATA TYPE\`; it also lists alternative DDL routes such as \`ALTER TABLE ... ADD COLUMN; ROLLBACK; ALTER TABLE ... ADD COLUMN\`. The write-up builds on that vulnerability record, tracing a long-standing PostgreSQL type-confusion primitive into a working code-execution chain.

**「Impact」** Operators of multi-tenant PostgreSQL systems where untrusted users can run SQL should treat the issue as a potential database-account-to-server compromise and scrutinize role privileges; commenters argue the chain requires authenticated SQL access rather than unauthenticated network reach.

**「Community discussion」** Commenters disputed the RCE label, with jmuguy calling it more of a privilege escalation and logophobia arguing the exploits require authenticated remote access and matter mainly for multi-tenant databases. Others praised the write-up for exposing PostgreSQL internals and showing the path to a zero-day.

<details><summary>References</summary>
<ul>
<li><a href="https://www.postgresql.org/support/security/CVE-2026-6460/">PostgreSQL: CVE-2026-6460: PostgreSQL type confusion after ...</a></li>

</ul>
</details>

**Tags**: `#PostgreSQL`, `#security research`, `#type confusion`, `#exploit chain`, `#CVE`

---

<a id="item-tech-news-4"></a>
### [Anthropic IPO discussion centers on valuation, revenue, and compute commitments](https://ipo.anthropic.com/us/) ⭐️ 8.0/10

Anthropic&\#x27;s IPO page is being discussed on Hacker News, but the supplied material contains no filing text, so the listing terms are not independently confirmed. A commenter citing linked documents lists a $70–78 price range, an $85.3B gross deal size including a $26B private placement, a roughly $968B implied market cap at $74 on 13.09B shares, Q3 2026 revenue of $17.0B \(+1,127% year over year\), a ~$81B run rate as of October 2026, $900.9B of compute commitments through 2045, and the ticker ANT on Nasdaq. Those figures come from community discussion and should be treated as unverified until the filing itself is available.

hackernews · josephljohnston · Nov 12, 11:46 · [Discussion](https://news.ycombinator.com/item?id=50465829)

**「Background」** Anthropic is an AI model developer whose earlier funding came through private venture rounds; commenters cite Series E, F, and G valuations as the backdrop for the listing. An IPO would shift the company’s valuation and financial obligations—such as revenue and compute commitments—from private fundraising into public-market disclosure and pricing.

**「Public reporting changes vendor risk for Claude customers」** For organizations running Claude in production or negotiating enterprise agreements, the IPO converts Anthropic from a private vendor into a reporting issuer: the 825 million Class A shares at $70–$78 give buyers a public reference price and put the company&\#x27;s revenue and spending on a quarterly disclosure schedule rather than occasional private-round announcements. Procurement and platform teams evaluating multi-year API commitments can now anchor counterparty-risk reviews to filed financials, though what is actually disclosed — including any compute or capacity obligations — depends on the offering documents, not the share price.

**「Community Discussion」** Commenters are split on whether the IPO timing undercuts Anthropic&\#x27;s frontier-AI narrative: maerF0x0 argues investors would have delayed a truly dominant model rather than accept dilution, while brainless and maupin contend that easy model switching and increasingly capable local models limit pricing power. irthomasthomas questions whether later private rounds could already be underwater at the low end of the cited range.

<details><summary>References</summary>
<ul>
<li><a href="https://techcrunch.com/2026/11/10/anthropic-sets-ipo-price-range-of-70-to-78-per-share-to-reach-an-implied-valuation-of-1-404-trillion/">Anthropic sets IPO price range of $70 to $78 per share to ...</a></li>
<li><a href="https://finance.yahoo.com/markets/stocks/articles/anthropic-sets-ipo-price-range-140602411.html?fr=sycsrp_catchall">Anthropic Sets IPO Price Range at $70 to $78, Valuing Company ...</a></li>
<li><a href="https://www.cnbc.com/2026/11/10/anthropic-sets-price-range-of-70-to-78-in-upcoming-ipo.html">Anthropic sets price range of $70 to $78 in upcoming IPO - CNBC</a></li>

</ul>
</details>

**Tags**: `#Anthropic`, `#IPO`, `#AI industry`, `#AI economics`, `#compute infrastructure`

---

<a id="item-tech-news-5"></a>
### [SemiAnalysis Claims Jensen Huang Has Left Nvidia](https://newsletter.semianalysis.com/p/nvidia-and-the-world-without-jensen) ⭐️ 8.0/10

SemiAnalysis reports that Jensen Huang is no longer Nvidia&\#x27;s CEO and that Colette Kress has been named interim CEO while the company searches for a permanent successor. The newsletter links the change to a board investigation of Huang&\#x27;s conduct and to its claim that more than 1.5GW of restricted Nvidia chips ultimately reached China, but the supplied excerpt provides no documents or independent confirmation for those allegations. It also argues that Nvidia&\#x27;s unusual structure—about 60 direct reports and no deep bench of successors—makes the transition riskier for the company and its AI-supply-chain partners. The claims should be treated as unverified until Nvidia or another source confirms them.

rss · Semianalysis · Nov 12, 18:06

**「Background」** Nvidia’s own announcement on November 12, 2026 confirmed that Jensen Huang resigned as president, CEO, and board member effective immediately. Deadline reported the move followed a meeting of Nvidia’s board, so the leadership change was already public when SemiAnalysis published its analysis.

**「Impact」** For cloud providers and the Chinese labs renting GPU capacity remotely, the concrete legislative risk is RASA \(H.R. 2683\), which passed the House 369-22 on 12 January 2026 and would extend the Export Control Reform Act so that remote access to export-controlled AI chips counts as an export event. SemiAnalysis argues that with Huang — portrayed as the restrictions&\#x27; most prominent internal defender — out of the way, such measures will advance faster, so anyone relying on offshore or cloud-brokered access to restricted Nvidia parts should plan for licensing requirements instead of the current legal grey zone. The piece does not substantiate that the CEO transition has actually happened, so the policy timing should be read as the author&\#x27;s prediction rather than an established result.

<details><summary>References</summary>
<ul>
<li><a href="https://nvidianews.nvidia.com/news/nvidia-announces-ceo-transition">NVIDIA Announces CEO Transition | NVIDIA Newsroom</a></li>
<li><a href="https://deadline.com/2026/11/jensen-huang-is-out-as-nvidia-ceo-1237221531/">Jensen Huang Fired As Nvidia CEO By Board</a></li>
<li><a href="https://newsletter.semianalysis.com/p/nvidia-and-the-world-without-jensen">Nvidia and the World Without Jensen</a></li>
<li><a href="https://www.softwareseni.com/the-ai-overwatch-act-and-remote-access-security-act-how-new-laws-are-reshaping-cloud-gpu-access/">The AI Overwatch Act and Remote Access Security... - SoftwareSeni</a></li>
<li><a href="https://worldreporter.com/chinese-ai-firms-access-restricted-nvidia-chips-through-southeast-asian-cloud-servers-exposing-a-structural-gap-in-u-s-export-controls/">Chinese AI Firms Access Restricted Nvidia Chips ... - World Reporter</a></li>

</ul>
</details>

**Tags**: `#Nvidia`, `#AI hardware`, `#GPU export controls`, `#semiconductor industry`, `#corporate leadership`

---

<a id="item-tech-news-6"></a>
### [US Commerce Department Reportedly Finalizing Rule on Remote AI Chip Access](https://www.theinformation.com/articles/commerce-department-finalizing-long-awaited-ai-remote-access-rule) ⭐️ 8.0/10

The Information reported that the US Commerce Department is finalizing a rule to block Chinese AI companies from remotely using advanced AI chips via overseas data centers, with an announcement possible as early as this month. The rule would extend existing semiconductor export restrictions to seven countries, including Singapore, Malaysia, and Thailand, to close remote-access and chip-smuggling gaps; the other four countries were not identified. The department is consulting other government agencies before finalizing the measure. The White House previously asked Congress to legislate to require the rule, and Nvidia has lobbied against closing the remote-access gap, arguing that US AI infrastructure needs to win globally.

telegram · zaihuapd · Nov 12, 03:42

**「Background」** The reported rule builds on existing US semiconductor export restrictions, which the source says would be extended to Malaysia, Singapore, Thailand and four other countries to cover remote access and chip smuggling. According to the source, the White House had already asked Congress to legislate the measure, while Nvidia lobbied against closing the remote-access gap, arguing that US AI infrastructure needs to compete globally.

**「Compliance burden for cross-border GPU rental」** If finalized as described, cloud and data-center operators in Singapore, Malaysia, Thailand and four other listed countries would need licenses and end-user reporting before serving Chinese AI customers, according to reporting on the seven-nation license list. Chinese AI firms that rent overseas GPU capacity — and the providers hosting them — would then have to document end users or relocate workloads, a restriction Nvidia has lobbied against.

<details><summary>References</summary>
<ul>
<li><a href="https://www.theinformation.com/articles/commerce-department-finalizing-long-awaited-ai-remote-access-rule">Commerce Department Finalizing Long-Awaited AI Remote Access Rule</a></li>
<li><a href="https://biz.chosun.com/en/en-international/2026/11/12/M2ICNVHJPVCFLJDLAGG5IP4VDE/">US to widen AI chip export controls to seven nations, curb ...</a></li>

</ul>
</details>

**Tags**: `#AI chips`, `#export controls`, `#US Commerce Department`, `#Southeast Asia`, `#AI infrastructure`

---

<a id="item-tech-news-7"></a>
### [Microsoft 365 email outage stretches hours for large organizations](https://status.cloud.microsoft/) ⭐️ 7.0/10

Microsoft 365 is experiencing a major service degradation, with email unavailable for hours at some large organizations while other Microsoft 365 services such as Teams chat and meetings continued to work. Microsoft said it validated an alternative health check on a subset of affected infrastructure, returned those servers to service, and was applying the change more broadly while preparing an automated recovery process to restart unresponsive servers. According to one sysadmin commenter, Azure infrastructure remained fine while Microsoft 365 email was affected.

hackernews · dkpk · Nov 12, 18:20 · [Discussion](https://news.ycombinator.com/item?id=50471731)

**「Background」** Microsoft 365 bundles email, Teams, and other cloud productivity services, so an email-specific failure can leave chat and meetings usable while core communications are down. During this incident, the status page was reported to be unreliable, and a commenter relied on its RSS feed for updates.

**「Impact」** Organizations relying on Microsoft 365 email had to manage multi-hour gaps in inbound mail while Teams remained available; one commenter reported email down for more than 15,000 employees at hour eight. The unreliable status page also meant some administrators had to use the RSS feed to track recovery.

**「Community discussion」** Commenters reported that email was still down at hour eight for an organization of 15,000-plus employees, while Teams chat and meetings worked and Azure infrastructure appeared unaffected. One commenter attributed the outage to reduced investment amid AI-focused cuts, an opinion that the incident reports do not establish.

**Tags**: `#Microsoft 365`, `#cloud outage`, `#service reliability`, `#sysadmin`, `#enterprise IT`

---

<a id="item-tech-news-8"></a>
### [Google&\#x27;s Gemini 4 Hydrogen launch draws questions on naming and pricing](https://blog.google/innovation-and-ai/models-and-research/gemini-models/introducing-gemini-4-hydrogen/) ⭐️ 7.0/10

Google has announced Gemini 4 Hydrogen, a new Gemini model that at least one user reports has already replaced 3.8 Flash in the Gemini app interface. The supplied announcement contains no benchmarks, context-window, architecture, or official pricing details, so its capabilities and tier position cannot be verified from the source. Community reaction centers on the element-based name, which readers say makes models harder to compare, and on whether Hydrogen is priced like non-discounted 3.8 Flash rather than the cheaper Flash and Flash Lite tiers.

hackernews · dvaplima · Nov 12, 18:01 · [Discussion](https://news.ycombinator.com/item?id=50471431)

**「Predecessor pricing and the new naming」** Gemini 4 Hydrogen is positioned as the recommended upgrade from Gemini 3.8 Flash, the fast tier it has already begun replacing in the Gemini app, according to reader reports in the thread. Third-party pricing trackers list 3.8 Flash at an introductory $0.75/$3.75 per million input/output tokens through December 31, 2026, against $1.50/$7.50 for Hydrogen — the gap behind commenters&\#x27; question about whether Google is dropping its cheap tier. Those same external write-ups describe Hydrogen as a faster model adapted from a larger sibling, Gemini 4 Carbon, which is where the element-based naming now applied across the Gemini 4 family originates.

**「Impact」** Developers and users who relied on Gemini&\#x27;s Flash tier now need to check actual model routing and pricing before assuming Hydrogen is a like-for-like low-cost replacement, because the supplied item offers no official price or capability figures.

**「Community discussion」** Commenters criticized the element-based naming as unhelpful for products meant to be compared, with one noting that &quot;Hydrogen&quot; intuitively sounds more powerful than &quot;Argon.&quot; Another argued that Hydrogen appears to be an entry-level replacement for 3.5 Flash Lite but is priced at the same rate as non-discounted 3.8 Flash, and asked whether Google is abandoning its fast-and-cheap tier; these are reader interpretations, not confirmed specifications.

<details><summary>References</summary>
<ul>
<li><a href="https://benchlm.ai/google/api-pricing">Gemini API Pricing (November 2026): Rates &amp; Price Increases</a></li>
<li><a href="https://felloai.com/gemini-4-hydrogen/">Gemini 4 Hydrogen: Price, Benchmarks and Who Gets It</a></li>

</ul>
</details>

**Tags**: `#Gemini`, `#Google`, `#LLM releases`, `#model pricing`, `#AI industry`

---

<a id="item-tech-news-9"></a>
### [Open-source project claims 16B LLM inference on sub-1GB devices](https://github.com/hyperionaidev/smolmaxxing/) ⭐️ 7.0/10

A project author on Hacker News reports that an open-source effort, smolmaxxing, has run 16B-parameter language models on a first-generation iPad Air and a Xiaomi TV box, both described by the author as having less than 1GB of usable memory. The author says the work includes custom kernels, developed results, and modified models published on Hugging Face for others to reproduce. These are self-reported claims; the supplied material provides no independent benchmarks or precise throughput figures. The discussion frames the effort as experimental edge inference on old, scarce hardware rather than a generally available product.

hackernews · mrashad74 · Nov 12, 15:23 · [Discussion](https://news.ycombinator.com/item?id=50468888)

**「Background」** The project&\#x27;s approach relies on mixture-of-experts models: its README says both devices run 8B and 16B MoE models on about 1 GB of RAM by keeping only part of each model in memory and reading the rest from flash as needed. That memory strategy is the prerequisite for attempting larger parameter counts on hardware with less than 1 GB of usable memory.

**「Impact」** Developers interested in edge inference can inspect the published kernels and modified models and test the claims on their own constrained hardware. Because the results are self-reported and lack precise throughput or compatibility details, teams should treat them as experimental rather than production-ready.

**「Community Discussion」** One commenter argues that modern coding agents can already one-shot much of an inference engine, since inference is largely multiplication, making access to old hardware the harder part. Other commenters describe experiments with small models on older GPUs and welcome the trend of squeezing more capability out of constrained hardware.

<details><summary>References</summary>
<ul>
<li><a href="https://github.com/hyperionaidev/smolmaxxing/">GitHub - hyperionaidev / smolmaxxing : maxxing the ability to run...</a></li>

</ul>
</details>

**Tags**: `#LLM inference`, `#edge AI`, `#old hardware`, `#quantization`, `#open source`

---

<a id="item-tech-news-10"></a>
### [UMAP 0.6 Adds New Initialization and Optimizers](https://www.reddit.com/r/MachineLearning/comments/1xudaah/umap_06_new_initialization_new_optimizers_and/) ⭐️ 7.0/10

UMAP 0.6 is released with a new recursive initialization scheme and new optimizers, plus nearest-neighbor search that the author says is about 4× faster through better use of PyNNDescent. With the new optimizers, a fixed-seed run is reproducible while using every core; the author reports 3 million arXiv papers finishing in under five minutes, versus 52 minutes for a seeded 0.5 run that was single-threaded. The author also claims better million-scale embedding quality, including finer cluster detail and better kNN recall, and says the new initialization and optimizer are opt-in via compatibility\_layout=False because they change the output.

reddit · r/MachineLearning · /u/lmcinnes · Nov 12, 13:51

**「Earlier UMAP behavior」** The 0.6 release notes describe this version as a transition release: it keeps the established 0.5.x behavior by default and makes the new nearest-neighbor, recursive-initialization, and optimizer pipeline available for evaluation, with a future release planned to make that pipeline the default. Historically, UMAP provided a single layout optimizer; 0.6 adds Adam- and momentum-based alternatives while retaining the original for compatibility.

**「Impact」** Users who want the new faster, reproducible multithreaded behavior must explicitly set compatibility\_layout=False, since the new initialization and optimizers change the output and remain opt-in. The author says future versions will make them the default, so testing now helps identify changed embeddings before that switch.

<details><summary>References</summary>
<ul>
<li><a href="https://umap-learn.readthedocs.io/en/latest/release_notes.html">Release Notes — umap 0.6.0 documentation - Read the Docs</a></li>
<li><a href="https://umap-learn.readthedocs.io/en/latest/optimizers.html">Choosing a UMAP Layout Optimizer — umap 0.6.0 documentation</a></li>

</ul>
</details>

**Tags**: `#UMAP`, `#dimensionality-reduction`, `#open-source`, `#machine-learning`, `#performance`

---

<a id="item-tech-news-11"></a>
### [Audit finds Meta&\#x27;s TRIBE v2 lacks retinotopic and tonotopic maps](https://www.reddit.com/r/MachineLearning/comments/1xuillf/does_metas_brainresponse_model_tribe_v2_actually/) ⭐️ 7.0/10

A self-reported, control-tested audit of Meta&\#x27;s TRIBE v2 fMRI-prediction model reports that classic mapping stimuli produce no retinotopic map \(d=0.05, not significant\) and no tonotopic map \(ρ=-0.07, not significant\), even with loudness controlled, after validation against a synthetic ground-truth control. The same tests found strong motion selectivity correctly localized to MT+ \(d=4.31, 52× enrichment over chance\). The author also reports that an eccentricity effect appeared significant and correct only under three stimulus-geometry controls, which they interpret as an image-statistics confound rather than a genuine positional code. The findings are provisional: this is an anonymous solo project, not peer reviewed, and not independently replicated.

reddit · r/MachineLearning · /u/Own\_Tank1283 · Nov 12, 17:16

**「Background」** TRIBE v2 is Meta FAIR&\#x27;s foundation model that predicts whole-brain fMRI responses to images, video, audio, and text; secondary coverage describes it as trained on 720 volunteers with reported 2–3x gains over prior methods. Retinotopy, tonotopy, and motion selectivity are classic topographic maps — orderly representations of visual-field position, sound frequency, and motion in cortex — that serve as standard validation targets for brain-encoding models. The audit&\#x27;s premise is that TRIBE v2&\#x27;s own paper never tested these maps, and its methods section states that video features are spatially averaged before prediction, which the poster argues should degrade position information.

**「Impact」** For researchers using TRIBE v2 as a brain-encoding benchmark, the audit argues that its video pathway should not be assumed to carry retinotopic or tonotopic position information—especially because the model spatially averages video features before prediction—so position-related decoding claims need separate validation rather than being inferred from overall prediction accuracy.

<details><summary>References</summary>
<ul>
<li><a href="https://awesomeagents.ai/news/meta-tribe-v2-brain-prediction-ai/">Meta TRIBE v 2 Predicts Brain Activity From Any... | Awesome Agents</a></li>

</ul>
</details>

**Tags**: `#neuroimaging`, `#model-evaluation`, `#replication-critique`, `#fMRI`, `#representation-learning`

---

<a id="item-tech-news-12"></a>
### [Apple details Secure Exclaves audio/video isolation and hardware-verified privacy indicator](https://security.apple.com/blog/secure-exclaves/) ⭐️ 7.0/10

Apple published a Nov. 12 post detailing Secure Exclaves, an architecture that processes audio and video in an isolated secure environment so the main system and apps in environment-aware mode receive only the recognition results they need, not raw sensor data. The company says the technology is used in HomeView face and sound recognition and in the iPhone 18 Pro privacy indicator. On the iPhone 18 Pro, Apple says dedicated hardware verifies the microphone indicator dot’s color, brightness, and visibility before audio can enter the main system, and it requires the dot to remain displayed throughout relevant Siri audio sessions for at least three seconds total to prevent masking or spoofing.

telegram · zaihuapd · Nov 12, 09:13

**「Background」** Secure Exclaves are protected, compartmentalized runtimes that process camera and microphone data separately from the rest of the system. Apple says isolation features across many core silicon components keep each exclave segregated, so data analyzed inside cannot be accessed by the main system or apps.

**「Impact」** For users, Apple’s claimed benefit is that the microphone indicator must pass a hardware check before audio is released rather than relying only on software display. For apps using environment-aware processing, the exposed interface is limited to required recognition results instead of raw audio or video.

<details><summary>References</summary>
<ul>
<li><a href="https://security.apple.com/blog/secure-exclaves">Secure Exclaves and Ambient Sensing - Apple Security Research</a></li>

</ul>
</details>

**Tags**: `#Apple Secure Exclaves`, `#privacy architecture`, `#hardware security`, `#audio/video privacy`, `#iPhone 18 Pro`

---

<a id="item-tech-news-13"></a>
### [Unverified warning claims Telegram Widgets RCE flaw](https://x.com/telegram/status/2120502876728680765?a=qTsR6dLMSgt3RHbYYO0&amp;amp;s=46) ⭐️ 7.0/10

A community warning circulating on Telegram claims that Telegram Widgets — a feature introduced in the Bot API 10.4 release dated November 9, 2026, which lets bots embed HTML, CSS and JavaScript inside chat messages — contains a sandbox escape that permits remote code execution. The post says Telegram has stated the issue is fixed, but that testers in its group found the exploit still usable on some devices running the latest version, and it advises users not to click bots of unknown origin and to hold off upgrading to Widgets-capable clients for now. The claim is unverified: no CVE identifier, affected version list, technical write-up, or link to a primary Telegram advisory is provided, and the warning itself is the only account of both the flaw and the disputed fix. Treat the specifics — including which client versions remain exploitable — as unconfirmed until Telegram or an independent researcher publishes details.

telegram · zaihuapd · Nov 13, 01:02

**「How Telegram Widgets work」** Telegram Widgets were introduced with Bot API 10.4 on November 9, 2026, letting bots place HTML, CSS, and JavaScript interfaces directly inside chat messages. Unlike Telegram Mini Apps, which open a separate WebView and load a remote page, the new widgets execute inline in the message, making the client-side sandbox the key security boundary.

**「Practical exposure」** Because the warning says the flaw remains exploitable on some fully updated devices, Telegram users cannot treat an installed fix as proof of safety and are advised to avoid interacting with unfamiliar bots in the meantime. The report gives no affected client versions, CVE identifier, or technical detail, so organizations running bots that embed Widgets — the JavaScript-capable feature introduced in the November 9, 2026 Bot API 10.4 — have no way to verify whether their own deployments or user populations are exposed.

<details><summary>References</summary>
<ul>
<li><a href="https://thecybersecguru.com/exploits/telegram-widget-rce-zero-click/">Telegram Widget RCE: Zero-Click Exploit Chains Explained ...</a></li>

</ul>
</details>

**Tags**: `#Telegram`, `#security vulnerability`, `#remote code execution`, `#messaging`, `#unverified report`

---

## Financial News

<a id="item-finance-news-1"></a>
### [China approves Eli Lilly&\#x27;s oral weight-loss pill, a first for the country](https://www.reuters.com/business/healthcare-pharmaceuticals/china-approves-eli-lillys-weight-loss-pill-orforglipron-2026-11-12/) ⭐️ 8.0/10

China&\#x27;s drug regulator approved Eli Lilly&\#x27;s oral GLP-1 weight-loss drug orforglipron, sold as Muyouda, on Nov. 12 as a Class 1 new drug for adults who are obese or overweight with at least one weight-related condition — the first oral GLP-1 weight-loss treatment cleared in the country. The pill is taken once daily without food or water restrictions; a separate approval for type 2 diabetes is still under review, and Lilly has not disclosed pricing or a launch date.

telegram · zaihuapd · Nov 12, 10:09

**「Background」** Orforglipron is an oral small-molecule GLP-1 receptor agonist — a drug class that mimics the gut hormone GLP-1 — and Lilly studied it in Phase 3 ATTAIN trials in adults with obesity or overweight before approval; the competing GLP-1 weight-loss drugs in China are weekly injections.

**「Impact」** For Chinese adults who are obese or overweight with at least one weight-related condition, the approval adds a once-daily pill alongside the weekly injections already sold by Novo Nordisk, Eli Lilly, Pfizer and Innovent — but with price and launch timing undisclosed, how widely it is actually used remains undetermined.

<details><summary>References</summary>
<ul>
<li><a href="https://investor.lilly.com/news-releases/news-release-details/lillys-oral-glp-1-orforglipron-delivers-weight-loss-average-273">Lilly&#x27;s oral GLP-1, orforglipron, delivers weight loss of up ...</a></li>
<li><a href="https://www.nejm.org/doi/full/10.1056/NEJMoa2511774">Orforglipron, an Oral Small-Molecule GLP-1 Receptor Agonist ...</a></li>
<li><a href="https://mezha.net/eng/bukvy/d46e467b_drugmakers_intensify_competition/">Drugmakers Intensify Competition for China ’s Weight Loss Market</a></li>

</ul>
</details>

**Tags**: `#医药监管`, `#GLP-1`, `#礼来`, `#减重药`, `#中国市场`

---