---
layout: default
title: "Horizon Summary: 2026-11-24 (EN)"
date: 2026-11-24
lang: en
---

> From 38 items, 12 important content pieces were selected

---

**Technology News**
1. [Ladybird browser reaches first alpha for macOS and Linux](#item-tech-news-1) ⭐️ 8.0/10
2. [Zhipu Releases GLM-5.4 Loop Transformer, Accessible via Coding Plan](#item-tech-news-2) ⭐️ 8.0/10
3. [Anthropic posts claimed Claude-discovered VP≠VNP Lean 4 proof, pending review](#item-tech-news-3) ⭐️ 8.0/10
4. [NariQ Claims Near-BF16 Qwen3.8-27B at 3 Bits in 10 GB](#item-tech-news-4) ⭐️ 7.0/10
5. [Codex2api Releases Suspected Backdoored After Account Hijack](#item-tech-news-5) ⭐️ 7.0/10
6. [Meta AI Chief Warns Superintelligence Control Risk, Cites Unreviewed Proof](#item-tech-news-6) ⭐️ 7.0/10
7. [Alpöge&\#x27;s AI-assisted Riemann Hypothesis Lean proof alleged vacuous](#item-tech-news-7) ⭐️ 7.0/10
8. [EU coalition urges Apple browser case over WebKit limits](#item-tech-news-8) ⭐️ 7.0/10
9. [Singapore Says It Won&\#x27;t Be a Conduit for U.S. Chip Controls Evasion](#item-tech-news-9) ⭐️ 7.0/10

**Technology Blog**
1. [vLLM Day-0 Support for ERNIE 5.5 Flash via Plugin](#item-tech-blog-1) ⭐️ 7.0/10

**Financial News**
1. [Williams: Fed Still Has &\#x27;Work to Do&\#x27; on Inflation](#item-finance-news-1) ⭐️ 7.0/10
2. [Shanghai Metro to adjust fares for first time in 21 years](#item-finance-news-2) ⭐️ 7.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [Ladybird browser reaches first alpha for macOS and Linux](https://ladybird.org/posts/alpha/) ⭐️ 8.0/10

Ladybird, an independent browser with its own HTML parser, CSS engine, layout, JavaScript and WebAssembly implementations, published its first alpha, so macOS and Linux users can now install prebuilt binaries instead of compiling from source. It still borrows HarfBuzz for text shaping, Skia for 2D graphics, ffmpeg for video and SQLite from outside the project. Writing after testing it, Simon Willison reports a lightweight, responsive UI that rendered most sites correctly, including ffmpeg compiled to WebAssembly and a Pyodide REPL; Datasette Lite failed with &quot;undefined is not a function \(evaluated from &\#x27;navigator.serviceWorker.startMessages&\#x27;\)&quot;, a service-worker gap already flagged with a FIXME in the source. Ladybird runs each tab in its own WebContent process, and the October 2026 project newsletter credits AI coding agents with 75,650 new web-platform-tests passes, taking Ladybird to 2,184,722 subtests—ahead of Safari&\#x27;s 2,172,990 but behind Firefox and Chrome—alongside a new JavaScript JIT, style and layout moved to their own thread, and a rewritten WebAssembly engine that improved 7x on JetStream 3. The alpha announcement warns that some sites will not work and the browser will crash sometimes, and asks users to report broken sites from inside the browser and to opt in to sending crash reports.

hackernews · janvdberg · Nov 23, 16:13 · [Discussion](https://news.ycombinator.com/item?id=50614249)

**「Background」** Ladybird grew out of SerenityOS and implements most of a browser itself — HTML parsing, CSS, layout, JavaScript and WebAssembly — leaning on outside projects only for pieces such as HarfBuzz text shaping, Skia 2D graphics, ffmpeg video and SQLite. Ahead of the alpha, the project moved parts of its LibJS engine from C++ to Rust \(a February 2026 change it credited partly to AI coding agents\) and reported an October 2026 burst of work that added 75,650 passes on the roughly 2.25 million-subtest web-platform-tests suite, landed a new JavaScript JIT, moved style and layout to their own thread, and replaced its C++ WebAssembly engine with Cranelift-based code that it said was 7x faster on JetStream 3.

**「What to expect」** Users can treat the alpha as a testable daily-use candidate rather than a drop-in replacement: pages relying on unfinished platform features such as service workers will break, so Willison filed issue \#15515 for the Datasette Lite failure. Because the build ships with in-browser broken-site reporting and reviewable crash reports, the practical next step for early adopters is exercising real sites and filing those reports rather than assuming compatibility.

**「Community reaction」** Commenters largely corroborated the compatibility reports: freakynit said every site tested rendered correctly while noting slightly jerky scrolling, and alentred said tricky sites including a Proxmox NoVNC view loaded, with remote display feeling snappier than in Firefox. kvuj framed the reliance on Skia and SQLite as a trade-off that helped the browser while losing some of the original SerenityOS hacker spirit, and drnick1 argued that Ladybird should eventually address fingerprinting with spoofed or randomized values and more granular permissions.

**Tags**: `#browsers`, `#open source`, `#Ladybird`, `#browser engine`, `#alpha release`

---

<a id="item-tech-news-2"></a>
### [Zhipu Releases GLM-5.4 Loop Transformer, Accessible via Coding Plan](https://z.ai/blog/glm-5.4) ⭐️ 8.0/10

Z.ai has released GLM-5.4, its first model built on a looped transformer architecture, in which a group of weight-shared layers runs for multiple iterations to refine hidden states and deepen the network without increasing parameter count. The model is not currently available as open weights and cannot be reached through the regular Z.ai API, so access requires the Coding Plan subscription; its key works with the shared OpenAI-compatible Responses API at https://api.z.ai/api/v1. In the source&\#x27;s hands-on comparison, GLM-5.4 produced pelican SVGs similar in quality to GLM-5.3, and both look much closer to OpenAI and Anthropic outputs than the distinctive GLM-5.1 and GLM-5.2 generations.

hackernews · foohis · Nov 23, 10:06 · [Discussion](https://news.ycombinator.com/item?id=50609685)

**「Background」** A standard Transformer runs each layer once per forward pass, while a looped transformer reuses a group of weight-shared layers for several iterations, refining the hidden states and adding effective depth without increasing the parameter count. GLM-5.4 is Z.ai&\#x27;s first model built this way, arriving shortly after Thinking Machines Lab&\#x27;s Inkling 2 Mini, which the lab says runs its middle layers three times per token to apply more reasoning with fewer tokens on tasks such as agentic coding.

**「Impact」** Teams that need open weights or the standard API cannot adopt GLM-5.4 yet; those willing to use the Coding Plan can point an OpenAI-compatible client at the shared endpoint, but third-party tools such as the llm-zai plugin may need updates before they recognize the new model.

**「Community discussion」** One commenter welcomed Zhipu&\#x27;s technical transparency compared with Western labs and explained loop transformers as a way to reduce the memory-bandwidth cost of moving each layer through the chip once per token, while a practitioner said Chinese models&\#x27; &quot;marathon thinking&quot;—extended self-checking even on simple tasks—makes completion times much higher than frontier models and suspected it helps benchmark scores while hurting everyday use.

<details><summary>References</summary>
<ul>
<li><a href="https://thinkingmachines.ai/news/inkling-2-mini/">Introducing Inkling 2 Mini - Thinking Machines Lab</a></li>
<li><a href="https://openrouter.ai/thinkingmachines/inkling-2-mini">Inkling 2 Mini - API Pricing &amp; Benchmarks | OpenRouter</a></li>

</ul>
</details>

**Tags**: `#LLMs`, `#GLM-5.4`, `#looped transformers`, `#coding assistants`, `#model release`

---

<a id="item-tech-news-3"></a>
### [Anthropic posts claimed Claude-discovered VP≠VNP Lean 4 proof, pending review](https://github.com/anthropics/formal-math/blob/main/vp-vnp/README.md) ⭐️ 8.0/10

A Telegram post says Anthropic published a paper, “VP ≠ VNP over every field,” and a Lean 4 formalization for a result it says was found by an internal research Claude model; the paper and code were both written by AI. The paper claims a superpolynomial arithmetic-circuit lower bound for the Hamiltonian cycle polynomial, implying VP is a proper subclass of VNP and resolving Valiant’s 1979 algebraic-complexity conjecture; it addresses arithmetic circuits, not P versus NP. The repository says an audit against three standard axioms and an independent nanoda kernel check found no \`sorry\` outside reserved files, but no human mathematician has read the proof end to end, and Lean cannot by itself confirm that the formal statement matches the claimed theorem. Appendix Q lists discrepancies, and the result remains pending independent human review of both the proof and the statement’s equivalence.

telegram · zaihuapd · Nov 24, 06:02

**「Background」** VP versus VNP is the algebraic-circuit analogue of P versus NP, posed by Leslie Valiant in 1979: VP contains polynomial families computable by polynomial-size arithmetic circuits, while VNP contains those whose coefficients are definable by such circuits. The question has remained open since then, which is why a claimed separation—rather than a lower bound for a restricted circuit model—would be a major complexity-theory result.

**「Impact」** Complexity theorists and Lean users should treat the claim as an unreviewed preprint rather than a settled resolution; before citing it, they need independent confirmation that the formal statement—including the issues listed in Appendix Q—is equivalent to VP≠VNP and that the proof has been reviewed by human experts.

<details><summary>References</summary>
<ul>
<li><a href="https://explainx.ai/blog/anthropic-claude-vp-vnp-valiant-lean-proof-claimed-vs-verified-2026">VP ≠ VNP Lean Proof: Claimed vs Verified (2026) - explainx.ai</a></li>
<li><a href="https://interestingengineering.com/ai-robotics/claude-proves-vp-not-vnp-valiant-conjecture">Claude claims to prove VP ≠ VNP in Valiant&#x27;s 47-year-old ...</a></li>

</ul>
</details>

**Tags**: `#complexity theory`, `#Lean 4`, `#AI for math`, `#formal verification`, `#Anthropic`

---

<a id="item-tech-news-4"></a>
### [NariQ Claims Near-BF16 Qwen3.8-27B at 3 Bits in 10 GB](https://huggingface.co/nari-labs/Qwen3.8-27B-NariQ-GGUF) ⭐️ 7.0/10

NariQ has released 3-bit-and-lower GGUF quantizations of Qwen3.8-27B, claiming near-BF16 quality in a roughly 10 GB file. On its reported benchmarks, the 3-bit and 2.5-bit versions stay close to BF16: DeepSWE 41.0 and 41.9 versus 39.8, Terminal-Bench 2.1 63.8 and 60.2 versus 62.6, and AIME 25+26 98.3 and 96.5 versus 97.7; the 2-bit file falls to 28.6, 52.4, and 86.0. Decode speed is described as comparable to other quants on an RTX PRO 6000, but the results are vendor-reported and the files currently require NariQ&\#x27;s llama.cpp fork.

hackernews · toebee · Nov 23, 13:42 · [Discussion](https://news.ycombinator.com/item?id=50611402)

**「Why a third-party quant exists」** Quantization rewrites a model&\#x27;s weights at lower numeric precision than the original BF16 checkpoint, trading fidelity for a much smaller memory footprint; GGUF is the file format that llama.cpp-based runtimes load. The underlying Qwen3.8-27B is an open-weight dense vision-language model from Qwen, which is what lets an outside lab repackage it, and the same model is also offered through hosted inference APIs.

**「Impact」** Local users can fit the 27B model into a roughly 10 GB file, but running it requires the nari-labs llama.cpp fork, and the reported 3-bit context-length result falls from 88.9 at 4K to 70.7 at 64K on an RTX PRO 6000.

**「Community discussion」** Commenters questioned the benchmark claims: WithinReason said the plots suggest most gains come from a harness difference rather than the model, and Retro\_Dev asked what information is lost at lower bit widths, while rao-v praised the use of multiple held-out task types despite general skepticism toward QAT-style quants. jedbrooke reported about 3.8 tok/s on an 18 GB M3 Pro with the 3.0-bpw file and asked whether a 16 GB Mac could run it.

<details><summary>References</summary>
<ul>
<li><a href="https://openrouter.ai/qwen/qwen3.8-27b">Qwen 3 . 8 27 B - API Pricing &amp; Benchmarks | OpenRouter</a></li>

</ul>
</details>

**Tags**: `#quantization`, `#LLM inference`, `#local AI`, `#GGUF`, `#benchmark evaluation`

---

<a id="item-tech-news-5"></a>
### [Codex2api Releases Suspected Backdoored After Account Hijack](https://github.com/WormW/codex2api-incident-2026-11) ⭐️ 7.0/10

A Telegram report says the codex2api author&\#x27;s account was compromised and the attacker pushed tags that bypassed the main branch, causing Release builds to ship a backdoored version. Version 3.1.11 reportedly removed authentication, amounting to unauthenticated remote command execution, while a workflow exfiltrated 16 GitHub Actions secrets and affected at least 21 repositories under the same account. Users who installed or updated to versions 3.1.10–3.1.12 are advised to stop using them immediately, roll back to 3.1.9, and rotate GitHub tokens, SSH keys, and database and DeepSeek API keys. The report is secondhand and framed as suspected \(疑似\); the claims have not been independently verified here.

telegram · zaihuapd · Nov 23, 11:21

**「Background」** GitHub Actions workflows can access repository secrets, and release pipelines commonly build from pushed tags rather than only from a protected branch, so a compromised maintainer account can publish code that never passed through the main-branch path. A March 2025 compromise of the tj-actions/changed-files action similarly leaked CI/CD secrets from repositories that used it, according to The Hacker News.

**「Impact」** Because the malicious releases were published via tags rather than the main branch, protection rules on main would not have blocked them, so anyone running 3.1.10–3.1.12 should treat their GitHub tokens, SSH keys, and database and DeepSeek credentials as exposed and rotate them after rolling back to 3.1.9.

<details><summary>References</summary>
<ul>
<li><a href="https://thehackernews.com/2025/03/github-action-compromise-puts-cicd.html">GitHub Action Compromise Puts CI/CD Secrets at Risk in Over ...</a></li>

</ul>
</details>

**Tags**: `#supply-chain-security`, `#security-incident`, `#github-actions`, `#secrets-management`, `#open-source-security`

---

<a id="item-tech-news-6"></a>
### [Meta AI Chief Warns Superintelligence Control Risk, Cites Unreviewed Proof](https://thenextweb.com/news/metas-ai-chief-says-superintelligence-is-arriving-and-control-is-at-risk) ⭐️ 7.0/10

Meta Chief AI Officer and Superintelligence Labs head Alexandr Wang said in a long X post that superintelligence is no longer a &quot;someday&quot; issue and that humans may struggle to control systems capable of unlimited self-improvement or 1,000 times human intelligence. He cited a claimed Riemann hypothesis proof by mathematician Levent Alpöge, produced with Anthropic&\#x27;s Claude and machine-verified on Saturday through Lean and Mathlib, as evidence that AI&\#x27;s gap to top humans is down to specific knowledge, engineering integration, and experimentation. The proof has no human-readable version yet, and the item offers no independent confirmation of the claim; Wang called for urgent investment in safety, alignment, and protection research.

telegram · zaihuapd · Nov 23, 12:49

**「Background」** The Riemann hypothesis is a 167-year-old open problem in mathematics. According to Al Jazeera and Clarín, Levent Alpöge, an Anthropic mathematician, announced on November 20, 2026 that he and Claude had claimed to find a proof — the specific claim Wang cites as evidence that AI is approaching top human mathematical work.

<details><summary>References</summary>
<ul>
<li><a href="https://www.aljazeera.com/economy/2026/11/23/ai-superintelligence-arriving-warns-top-meta-executive">Artificial superintelligence ‘arriving’, warns top Meta ... | Al Jazeera</a></li>
<li><a href="https://www.clarin.com/us-news/who-is-levent-alpoge-the-anthropic-mathematician-who-claims-solved-the-riemann-hypothesis-with-claude_0_2WdGvYKBVM.html">Who is Levent Alpöge ? The Anthropic mathematician who claims he...</a></li>

</ul>
</details>

**Tags**: `#AI safety`, `#superintelligence`, `#Riemann hypothesis`, `#Lean theorem proving`, `#Meta AI`

---

<a id="item-tech-news-7"></a>
### [Alpöge&\#x27;s AI-assisted Riemann Hypothesis Lean proof alleged vacuous](https://x.com/i/web/status/2124987173439209561) ⭐️ 7.0/10

A reported AI-assisted Lean formalization of the Riemann Hypothesis and a generalized version, attributed to Alpöge and Claude, is alleged to be vacuous despite compiling: researchers reportedly found key definitions written as tautologies and geometric conditions effectively empty. The release reportedly included 17 million lines of Lean across 175,000 files but no human-readable proof; Lean and Mathlib community members said the next day they had “full confidence” that the code proved the proposition. On 23 November, Alpöge reportedly conceded that “250,000 pages is a joke” and that the code is “full of garbage but compiles,” calling the criticism entirely reasonable. The account comes from an aggregator summary, so the claims and the status of any formal proof remain unverified here.

telegram · zaihuapd · Nov 24, 01:29

**「Background」** Earlier accounts place the Lean formalization&\#x27;s development between Oct. 6 and Nov. 16, 2026, with Alpöge and Claude finishing the core proof on Nov. 15 and extending it to the Generalized Riemann Hypothesis the next day; a Nov. 21 report said the Lean community had declared the proof correct after verification of its 17 million lines. The dispute turns on the distinction between a proof assistant accepting code and that code actually encoding the intended theorem—the issue raised when critics said key definitions were vacuous.

**「Impact」** Researchers and developers relying on Lean formalizations would need to verify that definitions are nontrivial and that the stated theorem is the intended one, because a proof that compiles can still be vacuous; the reported case reinforces the need for human-readable statements and independent review before treating AI-generated formalizations as evidence.

<details><summary>References</summary>
<ul>
<li><a href="https://en.wikipedia.org/wiki/Riemann_hypothesis">Riemann hypothesis - Wikipedia</a></li>
<li><a href="https://www.zerohedge.com/science/did-claude-just-solve-maths-most-famous-problem-even-anthropics-mathematician-admits-timing">Mathematicians Confirm Claude Solved Math&#x27;s Most... | ZeroHedge</a></li>
<li><a href="https://eu.36kr.com/en/p/4083142892196993">Exclusive Interview: The Lead Researcher Behind Claude &#x27;s Riemann ...</a></li>

</ul>
</details>

**Tags**: `#AI for mathematics`, `#Lean theorem proving`, `#formal verification`, `#research integrity`, `#Claude`

---

<a id="item-tech-news-8"></a>
### [EU coalition urges Apple browser case over WebKit limits](https://appleinsider.com/articles/26/11/23/eu-urges-to-challenge-apples-grip-on-iphone-browsers?utm_source=rss) ⭐️ 7.0/10

A coalition claiming to represent 45,000–55,000 EU businesses and organizations, including Mozilla and Shopify, has sent a letter asking the European Commission to open a case against Apple over iPhone browser restrictions. The signatories argue that although the Digital Markets Act lets rival browsers use their own engines in the EU, technical and legal requirements prevent them from migrating existing EU users away from WebKit, while businesses remain dependent on the App Store to reach users. The coalition estimates that moving half of native iOS apps to the web would save EU businesses €11 billion a year in development costs and €1.3 billion in App Store fees; the letter is advocacy pressure, not a confirmed Commission action, and signatures are open until December 3, 2026.

telegram · zaihuapd · Nov 24, 03:02

**「Background」** The request is framed around the EU Digital Markets Act, under which Apple already allows competing browsers in the EU to use their own engines. The coalition argues that technical and legal requirements still make it impractical for browser makers to move existing EU users off WebKit, while businesses remain dependent on the App Store to reach iPhone users.

**「Practical effect」** For EU browser makers and developers, the immediate effect is continued dependence on Apple&\#x27;s WebKit and App Store distribution: the coalition says no vendor has successfully migrated existing EU users off WebKit, despite the DMA allowance for alternative engines. The letter itself does not change Apple&\#x27;s rules; any relief would require the Commission to open and pursue a case.

<details><summary>References</summary>
<ul>
<li><a href="https://www.yahoo.com/news/politics/articles/eu-coalition-presses-eu-commission-191706516.html?fr=sycsrp_catchall">EU Coalition Presses EU Commission to Act on Apple Browser ...</a></li>

</ul>
</details>

**Tags**: `#Apple`, `#EU DMA`, `#browser competition`, `#WebKit`, `#tech policy`

---

<a id="item-tech-news-9"></a>
### [Singapore Says It Won&\#x27;t Be a Conduit for U.S. Chip Controls Evasion](https://www.bloomberg.com/news/articles/2026-11-24/singapore-won-t-be-conduit-to-skirt-us-chip-curbs-wong-says) ⭐️ 7.0/10

Singapore Prime Minister Lawrence Wong said the country will not be used as a conduit for companies seeking to evade U.S. chip export controls, and that authorities are investigating Megaspeed&\#x27;s purchases of Nvidia chips. The statement followed the U.S. Commerce Department&\#x27;s addition of Megaspeed and six other Southeast Asian firms to a trade blacklist a day earlier. The Federal Register cited a &quot;significant risk&quot; that the firms could divert advanced computing products to unauthorized users, and the list includes affiliates in Malaysia and Thailand. Reuters reported that Alibaba&\#x27;s Singapore subsidiary Apex Enterprise Solutions was also listed; Alibaba said it has never transferred controlled advanced computing chips.

telegram · zaihuapd · Nov 24, 05:03

**「Background」** The US Commerce Department added Megaspeed and six other Southeast Asian companies to its trade blacklist one day before Wong’s remarks, according to the report. The Federal Register cited a “significant risk” that the firms would transfer advanced computing products to unauthorized users.

**「Impact」** The Entity List additions restrict US exports to Megaspeed-linked entities in Singapore, Malaysia, and Thailand, so suppliers and customers in those jurisdictions should screen the named companies before any advanced-chip transaction. Alibaba&\#x27;s denial that its Singapore subsidiary Apex Enterprise Solutions transferred controlled chips also shows that the designations create a compliance and reputational dispute for affiliated firms.

<details><summary>References</summary>
<ul>
<li><a href="https://www.reuters.com/business/us-blacklist-megaspeed-chip-firm-linked-nvidia-scandal-source-says-2026-11-23/">US blacklists Alibaba subsidiary and Megaspeed linked to ...</a></li>
<li><a href="https://casrai.org/news/bis-adds-megaspeed-seven-entities-entity-list-final-rule-2026">BIS Adds Seven Megaspeed Entities to Entity List — CASRAI</a></li>

</ul>
</details>

**Tags**: `#chip export controls`, `#AI hardware`, `#Singapore`, `#Nvidia`, `#US tech policy`

---

## Technology Blog

<a id="item-tech-blog-1"></a>
### [vLLM Day-0 Support for ERNIE 5.5 Flash via Plugin](https://vllm.ai/blog/2026-11-24-ernie-5-5-flash-preview) ⭐️ 7.0/10

rss · vLLM Blog · Nov 24, 00:00

**「Background」** Baidu&\#x27;s ERNIE team and vLLM released day-0 vLLM support for ERNIE 5.5 Flash Preview, a 280B-parameter sparse mixture-of-experts model with 14B active parameters per token and a 1M-token context, aimed at reasoning and long-horizon agent and tool-use tasks. The practical challenge was serving a new architecture with unusual attention, MoE and output-head structures without maintaining a fork or waiting for a model-specific image or nightly build.

**「Solution」** Their answer is the vLLM-ERNIE plugin, a standalone package installed alongside the official vllm==0.32.0 wheel; vLLM discovers it through the vllm.general\_plugins entrypoint and registers architecture module paths lazily, so the model code is imported only when config.json names ERNIE and other models pay no overhead. The plugin supplies ERNIE model code and kernels, while vLLM core retains attention kernels, KV-cache management, speculative decoding, parallelism and the server. The model has 43 layers: 37 Heavily Compressed Attention layers and 6 MLA-DSA layers, plus VHA cross-head mixing, Multi-Router Latent MoE and a MultiMax output head. Dedicated fused kernels fold precomputable weights and eliminate intermediate-memory round trips, with the authors reporting 1.55x-6.53x per-kernel speedups over naive implementations and bitwise-identical results for several fusions. FlashIndexer adds token-dependent head routing and threshold pre-filtering to reduce sparse-indexing cost, reported as 1.4x at 1M context. The checkpoint uses MXFP4 routed experts with W4A8 QAT and FP8 elsewhere, FP8 KV cache and FP4 indexer; a bundled three-layer DSpark draft model proposes up to seven tokens and is claimed to exceed 4.0 mean acceptance on coding and agent workloads. Data-parallel attention with expert parallelism, attention TP2/4/8, PD disaggregation over Mooncake and CPU KV offload are also supported.

**「Takeaway」** The larger lesson is that a thin, lazily registered plugin can decouple model-specific kernels and features from vLLM&\#x27;s release cadence, enabling day-0 support while preserving upstream serving features; the performance figures, however, remain vendor-reported without benchmark methodology.

**Tags**: `#vLLM`, `#ERNIE`, `#MoE inference`, `#kernel fusion`, `#speculative decoding`

---

## Financial News

<a id="item-finance-news-1"></a>
### [Williams: Fed Still Has &\#x27;Work to Do&\#x27; on Inflation](https://www.cnbc.com/2026/11/23/john-williams-fed-inflation-rate-hikes.html) ⭐️ 7.0/10

New York Fed President John Williams said the Fed still has &quot;work to do&quot; to bring inflation back to its 2% target and indicated further rate increases can unfold over time, ahead of the Dec. 8-9 policy meeting. The report said markets are fully pricing a quarter-point increase from the current 3.75%-4% target range.

rss · CNBC Finance · Nov 23, 21:02

**「Background」** Inflation has stayed well above the Fed&\#x27;s 2% goal while the economy keeps growing, and officials have disagreed over how quickly to raise rates, with Williams emphasizing a measured approach.

**Tags**: `#Federal Reserve`, `#monetary policy`, `#interest rates`, `#inflation`, `#John Williams`

---

<a id="item-finance-news-2"></a>
### [Shanghai Metro to adjust fares for first time in 21 years](https://weibo.com/1699432410/5368461393397183) ⭐️ 7.0/10

Shanghai Metro will introduce a distance-based fare system on Dec. 1, its first fare adjustment in 21 years, with a 3-yuan base fare for journeys of 0–4 km and 1-yuan increments for subsequent distance bands. It will also sell four multi-ride tickets—35, 45, 60 and 90 rides for 190, 210, 270 and 390 yuan—from Nov. 26, and offer a 10% discount after 90 yuan of monthly spending through the same payment channel, aimed at reducing the effect on frequent riders.

telegram · zaihuapd · Nov 23, 10:45

**「Background」** Shanghai Metro fares had gone unchanged for 21 years; under the new structure a rider pays a 3 yuan base fare for the first 4 km, then 1 yuan more for each following band \(4, 4, 4, 7, 7, 10 and 10 km, then every 15 km beyond 50 km\), so longer journeys cost more.

**Tags**: `#Shanghai Metro`, `#public transit fares`, `#fare adjustment`, `#commuter costs`, `#urban transport policy`

---