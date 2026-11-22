---
layout: default
title: "Horizon Summary: 2026-11-22 (EN)"
date: 2026-11-22
lang: en
---

> From 23 items, 9 important content pieces were selected

---

**Technology News**
1. [GnuPG/GPGME Flaw Affects Pre-2.3.0 Versions; RCE Label Disputed](#item-tech-news-1) ⭐️ 8.0/10
2. [Claimed Lean verification of Riemann Hypothesis draws scrutiny](#item-tech-news-2) ⭐️ 8.0/10
3. [A Monitor&\#x27;s USB Ethernet Path Cut Download Speed by 75%](#item-tech-news-3) ⭐️ 7.0/10
4. [Muru: AI-Assisted Rust Server for Python ASGI/WSGI Apps](#item-tech-news-4) ⭐️ 7.0/10
5. [Microsoft previews RDMA over USB4 to pool PCs for local AI](#item-tech-news-5) ⭐️ 7.0/10
6. [OpenRouter flags possible third-party reads of MiniMax prompts](#item-tech-news-6) ⭐️ 7.0/10
7. [Zhejiang University reports first hardware QRAM demo on superconducting chip](#item-tech-news-7) ⭐️ 7.0/10

**Technology Blog**
1. [Avoiding Catastrophic Blunders Is the Core of Good Coding](#item-tech-blog-1) ⭐️ 6.0/10

**Financial News**
1. [Trump backs Commerce chief Lutnick amid scrutiny of China chip sales, says he hopes Huang apologizes and returns](#item-finance-news-1) ⭐️ 7.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [GnuPG/GPGME Flaw Affects Pre-2.3.0 Versions; RCE Label Disputed](https://lists.gnupg.org/pipermail/gnupg-announce/2026q4/000517.html) ⭐️ 8.0/10

A disclosure on the GnuPG announcement mailing list, titled &quot;RCE in Gnupg,&quot; concerns a GPGME vulnerability that commenters say affects all software using GPGME versions before 2.3.0, whether linked as a shared library, DLL, or statically. The RCE characterization is disputed in the discussion, where one commenter calls it a double free bug rather than an RCE chain. A commenter who said GitLab informed them on 2026-11-12 reported that the bug was disclosed on 2026-11-20, earlier than the originally planned 2026-11-25 date, because GitLab had to update for the separate Ruby2Shell bug. The supplied material includes no official advisory text or independent verification of the impact.

hackernews · gdgghhhhh · Nov 21, 08:32 · [Discussion](https://news.ycombinator.com/item?id=50587208)

**「Background」** GPGME is a library used by GnuPG-related applications, including mail clients and GitLab&\#x27;s signed-commit path, so a flaw in versions before 2.3.0 affects software that links it as well as the command-line tools. The disclosure followed a coordinated timeline: GitLab informed the maintainers on 2026-11-12, the original date was 2026-11-25, and the bug was published on 2026-11-20 after GitLab brought its own update forward because of the Ruby2Shell bug. A commenter also noted that Red Hat had carried a downstream fix for five years while upstream did not.

**「Affected deployments」** Commenters say every application linked against GPGME before 2.3.0 is affected — whether as a shared library, DLL, or static link — naming Gpg4win, GnuPG Desktop, most mail and many XMPP clients, Samba, and Flatpak. For GitLab, which handles signed commits, a commenter points to an Omnibus patch and calls code execution in that path &quot;pretty bad,&quot; while another commenter disputes the RCE framing and describes the flaw as a double free; upgrades to GPGME 2.3.0 or later are the stated remedy. One commenter asked whether tools such as apt that are not listed are unaffected, and no answer was supplied in the thread.

**「Community Discussion」** Commenters dispute the RCE framing, with one calling it &quot;a double free bug, not an RCE chain,&quot; and another saying Red Hat reportedly fixed it five years ago while upstream missed it. Others highlight GitLab&\#x27;s signed-commit path as a serious code-execution concern and list Gpg4win, GnuPG Desktop, most mail clients, many XMPP clients, Samba, and Flatpak as examples of software that may use affected GPGME versions.

**Tags**: `#security vulnerability`, `#GnuPG`, `#GPGME`, `#double free`, `#open source`

---

<a id="item-tech-news-2"></a>
### [Claimed Lean verification of Riemann Hypothesis draws scrutiny](https://leanprover-community.github.io/blog/posts/riemann-hypothesis/) ⭐️ 8.0/10

A Hacker News discussion is focused on a claimed Lean formal verification of the Riemann Hypothesis, but the supplied material provides no theorem statement, proof artifact, or independent confirmation, so the claim remains unverified. Commenters debated whether multiple Lean kernels and self-consistency proofs make a checker bug implausible, and they discussed the reported role of Claude and Levent in producing the formalization. For mathematicians and Lean users, the central issue is whether the proof can be reproduced against a trusted kernel and whether it relies on unproven assumptions.

hackernews · g-b-r · Nov 21, 14:36 · [Discussion](https://news.ycombinator.com/item?id=50589618)

**「Background」** The discussion concerns a claimed machine-checked proof of the Riemann Hypothesis: in Lean, a proof is accepted only if a small kernel verifies every step against the formal statement, so statement fidelity and kernel soundness are central questions. External summaries describe the claim as Anthropic researcher Levent Alpöge&\#x27;s 175,187-file Lean archive, announced around November 20, 2026, and report that Lean and Mathlib community members certified the 17-million-line library&\#x27;s statement and proof on November 21 after compilation and statement-matching checks.

**「Verification still in progress」** Andrew Sutherland&\#x27;s verification page reports that, as of 21 November 2026, the published Lean source compiles without errors and five headline theorems have been checked, with the remaining checks still running. Anyone citing or building on the result should treat it as only partially verified until that page reports completion, since a remaining check could still expose a mismatch between the formal statement and the claimed theorem.

**「Community Discussion」** rcr-anti argued that a kernel bug is now vanishingly unlikely because several implementations, including con-leche and con-ron, have self-consistency proofs, while thejokeisonme countered that a fake Collatz refutation previously passed an independent checker and that the checkers are not as independent as sometimes claimed. Other commenters credited Levent with getting strong results from Claude and speculated that the formalization covers a large chunk of modern mathematics.

<details><summary>References</summary>
<ul>
<li><a href="https://casrai.org/news/anthropic-levent-alpoge-claude-lean-riemann-hypothesis-claim-2026">175,000-File Lean Riemann Hypothesis Proof Claim — CASRAI</a></li>
<li><a href="https://www.unite.ai/lean-and-mathlib-communities-certify-claude-assisted-riemann-proof/">Lean and Mathlib Communities Certify Claude-Assisted Riemann ...</a></li>
<li><a href="https://math.mit.edu/~drew/grh/">RH Lean proof: verification files - MIT Mathematics</a></li>

</ul>
</details>

**Tags**: `#formal-verification`, `#Lean`, `#Riemann-Hypothesis`, `#AI-for-mathematics`, `#proof-checking`

---

<a id="item-tech-news-3"></a>
### [A Monitor&\#x27;s USB Ethernet Path Cut Download Speed by 75%](https://blog.tymscar.com/posts/studiodisplayethernet/) ⭐️ 7.0/10

A blog post documents a 75% download-speed drop for a user routing Ethernet through a monitor&\#x27;s USB hub and adapter, not through the display itself. The author traces the slowdown to added latency, adapter buffering, and dropped packets, framing it as an opaque USB-hub interaction rather than a monitor defect. The account is a single-setup debugging case, not a product-wide finding.

hackernews · soheilpro · Nov 21, 10:36 · [Discussion](https://news.ycombinator.com/item?id=50587875)

**「Background」** USB hubs and Ethernet adapters add a hop between a computer and the network, and that hop can introduce latency and buffering. TCP throughput depends on timely acknowledgments and is sensitive to round-trip time and packet loss, so a path that works for browsing can still throttle large downloads.

**「Impact」** For users with a monitor dock or USB hub, the practical check is to compare throughput with the Ethernet adapter connected directly to the host and then test another adapter; a commenter summarizing the post says a different adapter fixed it, and another says enabling flow control helped a similar MacBook/Thunderbolt-dock setup.

**「Community discussion」** Commenters debated the framing: one argued the real culprit is the USB network switch and the monitor is incidental, while another said readers had misunderstood the article&\#x27;s explanation that latency delayed acknowledgments, filled the adapter buffer, and caused drops. A separate commenter reported a similar issue lasting over a year with a MacBook and Thunderbolt dock, saying that enabling flow control was &quot;good enough.&quot;

**Tags**: `#USB hubs`, `#Ethernet adapters`, `#network latency`, `#packet loss`, `#hardware debugging`

---

<a id="item-tech-news-4"></a>
### [Muru: AI-Assisted Rust Server for Python ASGI/WSGI Apps](https://simonwillison.net/2026/Nov/21/muru/) ⭐️ 7.0/10

Graham Dumpleton, who started mod\_wsgi 20 years ago, has introduced Muru, an AI-assisted Rust server for running ASGI and WSGI Python applications in both development and production. Dumpleton has documented the early-stage project in 18 posts published between November 4 and November 21, 2026, covering worker architecture, import-once/fork-many behavior, HTTPS in development, WSGI/ASGI coexistence, releases without restarts, canary deployments, Kubernetes integration, scaling to zero, and a tracing toolbar. The posts describe intended capabilities and design decisions rather than independent performance results or broad adoption; Dumpleton says he decides what is not good enough yet and will keep polishing Muru until he would trust it.

rss · Simon Willison · Nov 21, 23:56

**「Background」** WSGI and ASGI are Python interfaces between web applications and the servers that run them. Dumpleton began mod\_wsgi, an Apache module for hosting Python web applications, 20 years ago; Muru is a separate server project rather than a new mod\_wsgi release.

**「Deployment consideration」** For teams maintaining WSGI applications, Muru&\#x27;s documented design could allow them to add ASGI features such as WebSockets or gRPC without immediately replacing their existing WSGI stack, including by handing requests to ASGI in the same worker. Because the project is early-stage and the source provides no performance results or adoption evidence, compatibility and production readiness still require independent testing before migration.

<details><summary>References</summary>
<ul>
<li><a href="https://grahamdumpleton.me/">Home - Graham Dumpleton</a></li>
<li><a href="https://docs.muruhq.dev/">Muru</a></li>

</ul>
</details>

**Tags**: `#Python`, `#ASGI/WSGI`, `#Rust`, `#web servers`, `#open source`

---

<a id="item-tech-news-5"></a>
### [Microsoft previews RDMA over USB4 to pool PCs for local AI](https://videocardz.com/newz/microsoft-brings-rdma-over-usb4-to-windows-allowing-multiple-pcs-to-run-one-local-ai-model) ⭐️ 7.0/10

Microsoft released a Windows developer preview of RDMA over USB4 that lets multiple PCs share memory and GPU resources to run a single local AI model over ordinary USB4 connections, without a dedicated network card or switch. In a demonstration, three AMD Ryzen AI Max+ 395 systems ran a 4-bit quantized Qwen3-235B-A22B model at about 18.5 tokens per second. Microsoft said the capability will be distributed through Windows Insider and it remains an early developer preview.

telegram · zaihuapd · Nov 21, 06:13

**「Background」** RDMA, or remote direct memory access, lets one machine access another machine&\#x27;s memory directly rather than sending data through the usual network stack; that is the mechanism needed to treat multiple computers as a single pool for a tightly coupled workload. Coverage of Microsoft&\#x27;s developer preview describes it as an addition to Windows&\#x27; NetworkDirect interface, which lets compatible AI frameworks use the combined memory and GPU resources of several connected PCs.

**「What it means for local AI developers」** Developers can now split a model too large for a single machine across two or more USB4-connected PCs while keeping the existing RDMA API, so pooling memory and GPU compute no longer requires a dedicated NIC or switch. The scaling has a cost: in Intel&\#x27;s tests, adding a fourth PC increased generation throughput but delayed the start of output, so larger clusters trade time-to-first-token for capacity. Hardware validation is still narrow, with the demo and community testing centered on AMD&\#x27;s Ryzen AI Max+ 395.

<details><summary>References</summary>
<ul>
<li>Microsoft previews linking Windows PCs over USB4 to run larger AI ...</li>
<li><a href="https://techcommunity.microsoft.com/blog/microsoftusbblog/introducing-rdma-over-usb4%C2%AE-on-windows-run-larger-local-ai-models-across-pcs/4574602">Introducing RDMA over USB4® on Windows: run larger local AI ...</a></li>
<li><a href="https://xenospectrum.com/en/windows-rdma-usb4-local-ai/">Microsoft Previews RDMA over USB4 for Windows, Splitting ...</a></li>

</ul>
</details>

**Tags**: `#Windows`, `#RDMA`, `#USB4`, `#local AI inference`, `#distributed computing`

---

<a id="item-tech-news-6"></a>
### [OpenRouter flags possible third-party reads of MiniMax prompts](https://news.ycombinator.com/item?id=50585962) ⭐️ 7.0/10

OpenRouter has notified users that some requests sent to MiniMax models may have been read by a third party, according to a notice reported on Hacker News. Security researchers who sent prompts containing test URLs between July and October 2026 found that the URLs were accessed 40 to 130 hours later, and OpenRouter attributed the issue to MiniMax and forwarding providers AtlasCloud, Novita and StreamLake. OpenRouter removed the “zero data retention” label from the affected endpoints and advised users with sensitive credentials to change API keys and passwords. The report is a secondary summary; OpenRouter had not published the notice on its website, and the underlying technical details were not provided.

telegram · zaihuapd · Nov 21, 06:53

**「What the “zero data retention” label covered」** OpenRouter is a routing layer that forwards API requests to third-party model providers and resellers, and its “zero data retention” tag signified that a given endpoint claimed not to log or store prompts and outputs. Because MiniMax traffic could pass through intermediaries such as AtlasCloud, Novita and StreamLake, the tag described a multi-party chain rather than a single operator.

**「Impact」** Developers and organizations that sent secrets, personal data or regulated data through these MiniMax endpoints should assume those prompts may have been exposed and rotate affected API keys and passwords. Teams relying on the zero-data-retention label for compliance should also reassess use of those endpoints until OpenRouter or the providers publish details.

<details><summary>References</summary>
<ul>
<li><a href="https://www.kucoin.com/news/flash/minimax-zero-data-retention-policy-found-to-leak-user-prompt-links">MiniMax&#x27;s &quot;Zero Data Retention&quot; Policy Found to Leak User ...</a></li>
<li><a href="https://arstechnica.com/security/2026/11/a-leaky-ai-supply-chain-is-exposing-secret-user-data-at-an-alarming-rate/">A leaky AI supply chain is exposing secret user data at an ...</a></li>

</ul>
</details>

**Tags**: `#AI 安全`, `#数据隐私`, `#API 平台`, `#安全事件`, `#LLM 推理`

---

<a id="item-tech-news-7"></a>
### [Zhejiang University reports first hardware QRAM demo on superconducting chip](https://finance.sina.com.cn/stock/2026-11-21/doc-iniznhsk3530826.shtml) ⭐️ 7.0/10

A Zhejiang University team reports demonstrating a quantum random access memory \(QRAM\) prototype on real hardware for the first time, using its own superconducting chip, &quot;Tianmu-2.&quot; According to the report, the chip ran prototypes retrieving 4-bit and 8-bit data with 80.9% and 60.4% accuracy respectively, cut circuit depth by more than 30% versus an unoptimized approach, and showed local noise resilience in the architecture for the first time. The work is said to be published in Nature Physics. The team&\#x27;s stated next step is scaling up the QRAM design. The account comes from a brief Sina Finance aggregation without direct paper details, so the publication and metrics are as reported rather than independently verified, and the 8-bit result remains low-accuracy at small scale.

telegram · zaihuapd · Nov 21, 08:31

**「Background」** QRAM is a proposed quantum memory that can be addressed with a superposition of addresses and return the corresponding data, potentially letting quantum algorithms fetch many stored values in parallel. Most QRAM schemes have remained theoretical or required hardware beyond current experiments; the Zhejiang University device is a small superconducting prototype that tested only 4- and 8-bit retrieval, making it an early experimental step rather than a practical memory.

**「Impact」** For developers of quantum algorithms that depend on efficient data loading, this prototype is not yet a usable QRAM component: 60.4% accuracy for 8-bit retrieval is well below what algorithmic speedups generally assume, so such designs should still treat QRAM as an experimental primitive rather than an available hardware capability. The reported circuit-depth reduction of more than 30% and local noise resilience are the most actionable results for other superconducting QRAM builders, but scaling beyond 8 bits remains unproven.

<details><summary>References</summary>
<ul>
<li><a href="https://arxiv.org/abs/2506.16682">[2506.16682] Experimental realization of the bucket-brigade ... Quantum random access memory put to the test - Nature Zhejiang University Achieves Breakthrough with World’s First ... A bucket-brigade quantum random access memory - Nature Chinese Scientists Demonstrate Quantum Random Access Memory ... From Experimental Demonstration to Fault-Tolerant Quantum ... [2609.11333v1] Quantum Random Access Memory Implementation ...</a></li>

</ul>
</details>

**Tags**: `#quantum computing`, `#QRAM`, `#superconducting qubits`, `#hardware research`

---

## Technology Blog

<a id="item-tech-blog-1"></a>
### [Avoiding Catastrophic Blunders Is the Core of Good Coding](https://seangoedecke.com/to-code-well-avoid-blunders/) ⭐️ 6.0/10

rss · Sean Goedecke · Nov 22, 00:00

**「Background」** Sean Goedecke argues that writing good code is less about having brilliant insights than about avoiding catastrophic mistakes, particularly in large commercial codebases worked on by big teams. He suggests many engineers wrongly equate skill with clever abstractions or tactics.

**「Solution」** Drawing analogies to chess and tennis, Goedecke claims that programming offers no durable winning advantage: one blunder can turn an elegant codebase into a janky one. He lists blunders such as introducing a parallel system, creating a second source of truth, making a safe synchronous operation delicately asynchronous, adding subtle failure points, and complicating a key interface. The cardinal sins, in his view, are inconsistency and unnecessary requirements. Inconsistency breaks trust because engineers must hunt for surprises instead of assuming code works sensibly; unnecessary requirements are sticky because later engineers lack the context to remove them, and they interact combinatorially with new features. His heuristics are to fit a task into the codebase as normally as possible and trim it to the smallest set of requirements, treating thoughts of a clever pattern as a warning sign of distraction. He adds that current coding agents are about as consistent as humans but much worse at avoiding unnecessary requirements.

**「Takeaway」** Goedecke concludes that great programming does not require cleverness—and that cleverness can even be a disadvantage. What matters is attention to detail and a laser focus on consistency and on skipping unnecessary requirements.

**Tags**: `#software engineering`, `#code quality`, `#maintainability`, `#technical debt`, `#engineering judgment`

---

## Financial News

<a id="item-finance-news-1"></a>
### [Trump backs Commerce chief Lutnick amid scrutiny of China chip sales, says he hopes Huang apologizes and returns](https://www.reuters.com/world/us/trump-says-he-still-backs-lutnick-urges-nvidias-huang-apologize-2026-11-20/) ⭐️ 7.0/10

President Trump said on Nov. 20 that he still supports Commerce Secretary Howard Lutnick, saying he is &quot;doing a good job&quot; despite scrutiny of how Lutnick handled chip sales to China amid the Nvidia affair. Trump also said he hopes Jensen Huang, the Nvidia CEO who has resigned, will &quot;come back after a serious apology,&quot; and said he had discussed the matter with Chinese President Xi Jinping — a claim that contradicts Treasury Secretary Scott Bessent&\#x27;s statement that the call did not involve Huang.

telegram · zaihuapd · Nov 21, 05:03

**「Background」** Nvidia CEO Jensen Huang resigned in mid-November 2026 after disclosures that he had affairs with an employee and a woman linked to Chinese intelligence. Separately, lawmakers are scrutinizing how the Commerce Department, led by Howard Lutnick, oversaw Nvidia&\#x27;s chip exports to China and enforced export controls.

<details><summary>References</summary>
<ul>
<li><a href="https://www.cnbc.com/2026/11/13/nvidia-scandal-lutnick-chip-sales.html">Nvidia scandal draws in Commerce Secretary Lutnick, who ...</a></li>
<li><a href="https://www.nytimes.com/2026/11/17/technology/jensen-huang-nvidia-statement.html">Jensen Huang Says He Would Return as Nvidia CEO if Asked ...</a></li>

</ul>
</details>

**Tags**: `#US-China chip policy`, `#Nvidia`, `#Trump administration`, `#Commerce Department`, `#executive turnover`

---