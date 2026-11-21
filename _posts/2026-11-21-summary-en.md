---
layout: default
title: "Horizon Summary: 2026-11-21 (EN)"
date: 2026-11-21
lang: en
---

> From 39 items, 9 important content pieces were selected

---

**Technology News**
1. [Thinking Machines&\#x27; Inkling 2 Mini brings a looped transformer to open weights](#item-tech-news-1) ⭐️ 8.0/10
2. [Finite-time blow-up claim for Navier–Stokes posted on GitHub](#item-tech-news-2) ⭐️ 8.0/10
3. [KVM CVE-2026-99312 lets VMs read AMD host memory](#item-tech-news-3) ⭐️ 8.0/10
4. [TSMC Halts 16nm-and-Below Orders From Chinese Firms Under US Rules](#item-tech-news-4) ⭐️ 8.0/10
5. [Report: SEC probe examines potential accounting issues at Nvidia](#item-tech-news-5) ⭐️ 7.0/10
6. [Signal moves to limit AI agents capturing data on mobile platforms](#item-tech-news-6) ⭐️ 7.0/10
7. [Aaronson&\#x27;s &\#x27;Stochastic Parrots&\#x27; Post Frames Debate on AI Math and Understanding](#item-tech-news-7) ⭐️ 7.0/10

**Technology Blog**
1. [Why Output Caching Saves Little in LLM Agents](#item-tech-blog-1) ⭐️ 6.0/10

**Financial News**
1. [Trump says US firms building AI data centers abroad would face &\#x27;huge taxes&\#x27;](#item-finance-news-1) ⭐️ 7.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [Thinking Machines&\#x27; Inkling 2 Mini brings a looped transformer to open weights](https://thinkingmachines.ai/news/inkling-2-mini/) ⭐️ 8.0/10

Thinking Machines released Inkling 2 Mini, a small model that is reported to be open-weights and built on a looped transformer architecture; the supplied item contains no article text, so architectural and benchmark details rest on the release page as described in the discussion and remain unverified. A note attributed to the team in the thread says training was done end-to-end in nvfp4 and that the sizing was chosen around what local-inference users ask for. A GGUF build for llama.cpp and Ollama is linked from the thread as unsloth/Inkling on Hugging Face. Early users report running it locally, but several llama.cpp pull requests \(32694, 32657, 32429, 32704\) are still unmerged, and one commenter posts a small patch claimed to give roughly a 30% speed boost.

hackernews · jasondavies · Nov 20, 20:12 · [Discussion](https://news.ycombinator.com/item?id=50581260)

**「What a looped transformer is」** A looped transformer reuses one set of layer weights across repeated passes instead of stacking separate layers, trading extra computation per token for more effective depth without a proportional increase in parameter count. Inkling 2 Mini applies that idea inside a multimodal mixture-of-experts model with roughly 26B total and 3B active parameters per token and a 1M-token context, according to its published model card.

**「Impact for local users」** Local-inference users are the immediate audience, and getting usable throughput currently means building against unmerged llama.cpp changes or applying community patches rather than running a stock release. Reported results span roughly 27 tokens/s decode on a Ryzen 395 via llama.cpp Vulkan and about 10 tokens/s on a 32GB M1 Pro at q4 while other applications were open, though these are individual, unbenchmarked measurements rather than verified figures.

**「Community discussion」** Commenters treat the reported results as promising but conditional: one calls the model &quot;bonkers good if these benchmarks hold up,&quot; specifically framing parity with Qwen3.8-27B as an open question rather than an established result. Experience is mixed on real tasks — one user reports a clean Python coding answer on an M1 Pro but a failure on a harder identification task after about 12,000 tokens of output — and another commenter raises an open question about what widely available looped architectures mean for safety and interpretability.

<details><summary>References</summary>
<ul>
<li><a href="https://huggingface.co/blog/inkling2mini">Welcome Inkling 2 Mini, Cutting-edge Performance for your ...</a></li>

</ul>
</details>

**Tags**: `#open-weights`, `#looped-transformers`, `#local-llm-inference`, `#llama.cpp`, `#model-release`

---

<a id="item-tech-news-2"></a>
### [Finite-time blow-up claim for Navier–Stokes posted on GitHub](https://github.com/tristanbuckmaster/navier-stokes/) ⭐️ 8.0/10

The GitHub repository tristanbuckmaster/navier-stokes claims a finite-time blow-up result for the Navier–Stokes equations, but the supplied item contains no paper text, proof details, or independent verification. It is drawing substantial Hacker News discussion, where commenters treat it as a potentially major mathematical claim rather than a confirmed result. Commenters describe the claim as the “unforced” version of the problem, contrasting it with a separate OpenAI example said to rely on carefully designed external forcing.

hackernews · trotro · Nov 20, 15:34 · [Discussion](https://news.ycombinator.com/item?id=50576232)

**「The Millennium Prize backdrop」** The Navier–Stokes existence and smoothness problem asks whether every smooth three-dimensional initial condition yields a smooth solution for all time; a finite-time blow-up would resolve the Millennium Prize question negatively. The backdrop is a priority dispute: Wikipedia records that on 8 September 2026 OpenAI proposed a solution using a smooth external force, while Tristan Buckmaster had made a statement about 12 hours earlier, and the current repository accompanies an Alpöge–Buckmaster paper that claims the unforced case and includes a Lean 4 formalization.

**「Verification burden」** Because the argument is circulating as a GitHub write-up rather than a peer-reviewed paper, mathematicians assessing it must first establish which of the Clay Mathematics Institute&\#x27;s four Navier–Stokes statements the proof claims to resolve. Commenters describe this as the unforced case, which they treat as the more consequential version because it would not rely on the engineered external forcing used in the earlier OpenAI example.

**「Community discussion」** Commenters distinguish the unforced claim from an OpenAI example said to use designed external forcing, with one calling the unforced version more “realistic.” Others ask whether a simulation could show the blow-up in real time and whether a physical demonstration is possible.

<details><summary>References</summary>
<ul>
<li><a href="https://en.wikipedia.org/wiki/Navier%E2%80%93Stokes_priority_controversy">Navier–Stokes priority controversy - Wikipedia</a></li>
<li><a href="https://hotrepo.ai/tristanbuckmaster/navier-stokes">tristanbuckmaster/navier-stokes: Lean 4 formalization of a ...</a></li>
<li><a href="https://en.wikipedia.org/wiki/Navier%E2%80%93Stokes_existence_and_smoothness">Navier – Stokes existence and smoothness - Wikipedia</a></li>

</ul>
</details>

**Tags**: `#Navier–Stokes equations`, `#mathematics research`, `#fluid dynamics`, `#research preprint`, `#Hacker News`

---

<a id="item-tech-news-3"></a>
### [KVM CVE-2026-99312 lets VMs read AMD host memory](https://thehackernews.com/2026/11/new-linux-kvm-flaw-cve-2026-99312-lets.html) ⭐️ 8.0/10

Linux KVM has a new guest-to-host memory-disclosure vulnerability, CVE-2026-99312, that affects only AMD hosts with nested virtualization enabled. Researchers demonstrated reading about 127 GB of host memory from inside a virtual machine on DigitalOcean. Upstream fixes shipped on November 18 in stable kernel 7.3.5 and related stable releases, but Debian and Ubuntu distribution kernels remain unpatched.

telegram · zaihuapd · Nov 20, 14:23

**「Background」** KVM is the Linux kernel&\#x27;s hypervisor component that allows the kernel to host virtual machines. This flaw becomes reachable when nested virtualization is enabled, meaning a guest VM is itself permitted to run a hypervisor and expose hardware virtualization features to its own guests; in that AMD configuration, a malicious guest can read host memory.

**「Impact」** Operators of affected AMD hosts should disable nested virtualization until their kernel includes the fix, or move to a fixed upstream kernel such as 7.3.5. Debian and Ubuntu users in particular cannot rely on current distribution kernels and need to verify whether their installed kernel has the patch.

**Tags**: `#KVM`, `#AMD`, `#virtualization security`, `#Linux kernel`, `#CVE-2026-99312`

---

<a id="item-tech-news-4"></a>
### [TSMC Halts 16nm-and-Below Orders From Chinese Firms Under US Rules](https://appleinsider.com/articles/26/11/20/apple-supplier-tsmc-cuts-off-china-chip-orders-amid-tighter-export-controls) ⭐️ 8.0/10

TSMC has told customers it is suspending orders from Chinese companies for 16nm-and-below processes, according to a report relayed by a Telegram aggregator and citing AppleInsider. Under the tightened US semiconductor export rules described in the item, TSMC may not supply those nodes without a prior US export license or exemption. Chinese firms are therefore left with older 28nm and 40nm processes and cannot obtain the high-bandwidth memory needed for AI data-center hardware, the report says. TSMC previously assessed for itself whether a customer&\#x27;s design qualified for an exemption; customers must now apply in advance, and the US approved list cited includes Apple, AMD and Nvidia but no Chinese company, while TSMC says it will comply.

telegram · zaihuapd · Nov 21, 02:01

**「Background」** Under the tightened US semiconductor export rules, foundries need a US export license or exemption before shipping advanced-node chips to Chinese customers. The source reports that TSMC previously could assess on its own whether a customer&\#x27;s chip design qualified for an exemption; that self-assessment route is what has now been replaced by a requirement that customers apply in advance.

**「Impact」** Chinese chip designers needing TSMC&\#x27;s 16nm-and-below capacity now must secure a US export license or exemption before orders can proceed; without one, they are confined to 28nm/40nm processes, which the report links to losing access to the high-bandwidth memory required for AI data-center hardware. The reported US-approved customer list includes Apple, AMD, and Nvidia but no Chinese companies, adding a licensing gate before advanced-node work can start.

<details><summary>References</summary>
<ul>
<li><a href="https://www.trendforce.com/news/2026/11/20/news-tsmc-samsung-reportedly-pause-china-consumer-chip-shipments-under-new-u-s-rules-16nm-orders-affected/">[News] TSMC , Samsung Reportedly Pause China Consumer Chip...</a></li>
<li><a href="https://theoutpost.ai/news-story/tsmc-cuts-chinese-chip-designers-off-from-the-tech-their-ai-chips-need-33882/">TSMC tightens chip curbs on Chinese designers</a></li>

</ul>
</details>

**Tags**: `#semiconductors`, `#TSMC`, `#export controls`, `#AI hardware`, `#China tech`

---

<a id="item-tech-news-5"></a>
### [Report: SEC probe examines potential accounting issues at Nvidia](https://www.marketscreener.com/news/us-sec-s-nvidia-probe-is-examining-potential-accounting-issues-sources-say-ce785ed3dd8ff627) ⭐️ 7.0/10

MarketScreener, citing unnamed sources, reported that the US Securities and Exchange Commission&\#x27;s probe into Nvidia is examining potential accounting issues. The material supplied here consists only of that headline and reader comments, with no detail on which practices, reporting periods, or financial statements are under review. Neither the SEC nor Nvidia is quoted confirming the scope of the examination, so the accounting allegations remain unconfirmed. The report does not say whether the matter is a formal investigation, what stage it has reached, or whether Nvidia has responded.

hackernews · ftchd · Nov 20, 20:22 · [Discussion](https://news.ycombinator.com/item?id=50581438)

**「Context: Nvidia&\#x27;s CFO now interim CEO」** Nvidia&\#x27;s Colette Kress, chief financial officer since 2013 and the executive who signed and certified the company&\#x27;s annual and quarterly financial reports, is now serving as interim CEO, according to Reuters and ChainCatcher. On Nvidia&\#x27;s most recent earnings call, Kress said the company was proud of its role in supporting the AI industry but would be &quot;far more selective&quot; in how it does so going forward, per Reuters. Those two developments — the CFO-turned-acting-CEO arrangement and the stated shift toward selectivity in AI deals — form the immediate backdrop to the reported SEC examination of the company&\#x27;s accounting.

**「Community discussion」** Commenters skeptical of Nvidia&\#x27;s reporting tied the reported probe to what one described as years of &quot;circular financing&quot; and argued that renegotiated usage deals with neoclouds would damage the company, while another asked why a board worried about accounting would install the CFO as interim CEO. Others speculated about stock-for-discounted-chip arrangements and large volumes of unaccounted GPUs; these are commenter assertions rather than verified findings.

<details><summary>References</summary>
<ul>
<li><a href="https://www.reuters.com/world/us-secs-nvidia-probe-is-examining-potential-accounting-issues-sources-say-2026-11-20/">EXCLUSIVE: Nvidia&#x27;s accounting is a focus of US SEC ...</a></li>
<li><a href="https://www.kucoin.com/news/flash/us-sec-investigates-nvidia-over-potential-accounting-issues">The U.S. SEC Investigates NVIDIA Over Potential Accounting ...</a></li>

</ul>
</details>

**Tags**: `#Nvidia`, `#SEC investigation`, `#accounting`, `#AI hardware`, `#tech industry`

---

<a id="item-tech-news-6"></a>
### [Signal moves to limit AI agents capturing data on mobile platforms](https://signal.org/blog/protecting-your-privacy/) ⭐️ 7.0/10

Signal published a blog post describing its efforts to stop AI agents on mobile operating systems from capturing user data, including data in Signal chats. The post presents the work as incremental progress rather than a finished fix, and the available material does not specify the technical mechanisms, platform versions, or a release timeline. Signal&\#x27;s framing, as characterized in the supplied analysis, is that it is cautiously optimistic about some of the protections being put in place.

hackernews · dotcoma · Nov 20, 09:42 · [Discussion](https://news.ycombinator.com/item?id=50572348)

**「Background」** Mobile operating-system AI agents can access information shown in or available to other apps, so an end-to-end encrypted messenger’s privacy also depends on whether those agents can capture messages once they are displayed. Signal’s post frames its move as part of its existing privacy mission, saying it is restricting the latest built-in AI agents from potentially capturing and storing Signal data.

**「Impact」** Because Signal describes only partial, ongoing progress, users should not assume the new protections guarantee that an AI agent on a device cannot reach their conversations; the post does not document coverage across specific platforms or app versions.

**「Community discussion」** Commenters welcomed the direction while pressing for more: one cited a Meredith Whittaker interview arguing that AI apps have excessive device access and that a contact&\#x27;s installed AI app can still expose a Signal chat even if the user has none. Another asked Signal to publish its forensics findings in a shared document or repository so smaller app developers could benefit, while others argued users should be told when systems contain spyware and should be pointed to alternatives such as GrapheneOS.

<details><summary>References</summary>
<ul>
<li><a href="https://signal.org/blog/protecting-your-privacy/">Signal &gt;&gt; Blog &gt;&gt; Signal is Serious About Protecting Your Privacy</a></li>

</ul>
</details>

**Tags**: `#privacy`, `#AI agents`, `#mobile security`, `#Signal`, `#data access`

---

<a id="item-tech-news-7"></a>
### [Aaronson&\#x27;s &\#x27;Stochastic Parrots&\#x27; Post Frames Debate on AI Math and Understanding](https://scottaaronson.blog/?p=10344) ⭐️ 7.0/10

A Scott Aaronson blog post titled &quot;The stochastic parrots have apparently proved the Riemann Hypothesis&quot; uses that provocative premise to examine what it would mean for an LLM to produce a correct mathematical result, and a Hacker News thread debates AI capability, interpretability, and human understanding. The supplied material contains no post text, and nothing in it substantiates an actual proof of the Riemann Hypothesis; the item is commentary, not a verified mathematical announcement. The discussion focuses on whether people could understand or verify a machine-derived result rather than on any specific claimed theorem.

hackernews · stratos123 · Nov 20, 20:03 · [Discussion](https://news.ycombinator.com/item?id=50581084)

**「Background」** “Stochastic parrots” is a 2021 term of criticism for large language models that became shorthand for systems generating plausible text by pattern-matching rather than understanding. Scott Aaronson’s post invokes the phrase against social-media claims that LLMs had “proved” the Riemann Hypothesis, framing the title as a provocation about machine mathematical reasoning rather than a verified proof.

**「Community Discussion」** Commenter janalsncm compared the problem to chess engines, arguing that a Stockfish evaluation counts as an &quot;explanation&quot; only as an aggregate of calculations stacked on a neural evaluator, which leaves &quot;why&quot; questions unsatisfying. jstummbillig asked whether humans could tolerate becoming steadily worse at understanding scientific and engineering results, and elorant wondered how many mathematicians could reach similar breakthroughs given near-infinite compute.

<details><summary>References</summary>
<ul>
<li><a href="https://scottaaronson.blog/?p=10344">Shtetl-Optimized » Blog Archive » The stochastic parrots have ...</a></li>

</ul>
</details>

**Tags**: `#AI and mathematics`, `#LLM capabilities`, `#interpretability`, `#scientific understanding`, `#Hacker News discussion`

---

## Technology Blog

<a id="item-tech-blog-1"></a>
### [Why Output Caching Saves Little in LLM Agents](https://seangoedecke.com/why-output-caching-doesnt-work/) ⭐️ 6.0/10

rss · Sean Goedecke · Nov 21, 00:00

**「Background」** LLM inference economics already depends on input caching to avoid recomputing conversation history, and repeated output may look like the next obvious waste to eliminate. Because attention lets input tokens be processed in parallel while output tokens must be generated one at a time, output tokens are substantially more expensive, making repeated output especially tempting to optimize.

**「Solution」** The author considers prompting or fine-tuning models to emit references such as “src/script.py:12-15” or pointers into conversation history, which the harness could expand transparently. But this would optimize only visible output. In his own agent histories, roughly 6% of output tokens are visible, 50% are reasoning tokens, and 44% are tool calls. By Amdahl’s law, even eliminating two-thirds of visible output tokens would save only about 4% of total output tokens. He is only moderately confident that frontier models rarely repeat themselves in chain of thought, and notes that tool calls may also contain repetition. The larger lever is the invisible 94%, which depends largely on model intelligence: a model that costs 5x more per token can be cheaper overall if it needs 6x fewer tokens.

**「Takeaway」** Output caching targets a small visible fraction of agent token spend, so it offers limited savings; reducing hidden reasoning and tool-call output through smarter models is the more consequential path to lower inference costs.

**Tags**: `#LLM inference economics`, `#output caching`, `#agentic coding`, `#Amdahl&\#x27;s law`, `#token costs`

---

## Financial News

<a id="item-finance-news-1"></a>
### [Trump says US firms building AI data centers abroad would face &\#x27;huge taxes&\#x27;](https://apnews.com/article/trump-artificial-intelligence-data-centers-f1ac03b73d13445400eeed8631d9d879) ⭐️ 7.0/10

Speaking at a White House press conference on Nov. 20, President Trump said he plans to impose &quot;huge taxes&quot; on US tech companies that build AI data centers overseas, aiming to keep the facilities in the US and preserve an AI edge over China; he gave no tax rate, timetable or legislative details and said he had not yet told officials inside his own administration.

telegram · zaihuapd · Nov 21, 03:26

**「Background」** The remarks came at a wide-ranging White House press conference where Trump promoted data centers and said US companies’ facilities should stay on US soil \[tool-1-1\]\[tool-1-2\]. He also urged communities to negotiate payments from developers, as local areas have opposed projects over electricity demand and noise.

**「Impact」** Trump also urged US communities to accept data centers and to negotiate payments from developers, a pitch aimed at localities that have opposed projects over electricity demand and noise.

<details><summary>References</summary>
<ul>
<li><a href="https://www.nytimes.com/live/2026/11/20/us/trump-news-conference">Live Updates: Trump Promotes Data Centers and Speaks on...</a></li>
<li><a href="https://www.theguardian.com/us-news/2026/nov/20/trump-datacenters-white-house">Trump threatens ‘tremendous penalties’ for US tech firms that build ...</a></li>

</ul>
</details>

**Tags**: `#US policy`, `#AI infrastructure`, `#data centers`, `#tax policy`, `#US-China tech competition`

---