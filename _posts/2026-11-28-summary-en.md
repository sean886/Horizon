---
layout: default
title: "Horizon Summary: 2026-11-28 (EN)"
date: 2026-11-28
lang: en
---

> From 31 items, 11 important content pieces were selected

---

**Technology News**
1. [OpenSec discloses 9.8-severity pre-auth Linux nfsd root flaw](#item-tech-news-1) ⭐️ 8.0/10
2. [WebRTC Card-Skimming Scripts Reportedly Found on Shopping Sites](#item-tech-news-2) ⭐️ 7.0/10
3. [Essay examines how proof-checker bugs yield false computer-checked proofs](#item-tech-news-3) ⭐️ 7.0/10
4. [State AGs sue SpaceX over Grok&\#x27;s alleged CSAM and intimate-image output](#item-tech-news-4) ⭐️ 7.0/10
5. [Google Research claims DeepCrossAttention delivers up to 3x speedup](#item-tech-news-5) ⭐️ 7.0/10
6. [SemiAnalysis Benchmarks Trainium3 Inference Against Nvidia GB300](#item-tech-news-6) ⭐️ 7.0/10
7. [Minecraft Bedrock Resource-Pack Flaw Affects 26.52–26.63, Fixed in 26.65](#item-tech-news-7) ⭐️ 7.0/10
8. [Microsoft moves to replace some third-party Windows drivers](#item-tech-news-8) ⭐️ 7.0/10

**Financial News**
1. [中国国常会部署稳市机制，优化中央汇金类“平准基金”功能](#item-finance-news-1) ⭐️ 8.0/10
2. [蜜雪冰城5亿元入股DeepSeek，后者新一轮融资规模约1000亿元](#item-finance-news-2) ⭐️ 7.0/10
3. [China&\#x27;s Central Bank Lowers Minimum Purchase for Large-Denomination CDs to 100,000 Yuan](#item-finance-news-3) ⭐️ 7.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [OpenSec discloses 9.8-severity pre-auth Linux nfsd root flaw](https://opensec.in/blog/nfs2root-cve-2026-99362) ⭐️ 8.0/10

OpenSec disclosed CVE-2026-99362, a CVSS 9.8 pre-authentication heap overflow in the Linux kernel NFS server nfsd that it says can give an unauthenticated attacker a root shell through a single connection to tcp/2049. The flaw has existed since Linux 3.16 in 2014 and affects hosts with NFSv4.1 or 4.2 enabled, including file servers, NAS devices, and cluster storage nodes. Fixes have been released in Linux 6.12.117, 6.18.61, 7.3.2, and 7.4-rc1; administrators must upgrade the kernel and reboot. The CVE was made public on November 20, 2026, and the advisory recommends firewall rules restricting tcp/2049 where immediate upgrading is not possible.

telegram · zaihuapd · Nov 27, 12:57

**「Background」** NFSv4.1 and 4.2 clients bundle multiple operations into a single compound request, and the session&\#x27;s SEQUENCE operation carries reply-size and caching parameters that nfsd uses when sizing buffers. Red Hat&\#x27;s advisory describes CVE-2026-99362 as an out-of-bounds memory write triggered when a remote client negotiates a minimal cached reply size and then sends crafted compound requests containing SEQUENCE operations; NVD lists the CVE as recently published in its dataset in November 2026.

**「Impact」** Any host exposing nfsd on tcp/2049 with NFSv4.1 or 4.2 enabled is reachable before authentication, so network exposure alone is sufficient for an attack attempt. Applying a fixed kernel requires a reboot before the patch takes effect, and organizations that cannot do so immediately must restrict tcp/2049 at the firewall.

<details><summary>References</summary>
<ul>
<li><a href="https://access.redhat.com/security/cve/cve-2026-99362">CVE-2026-99362 - Red Hat Customer Portal</a></li>
<li><a href="https://nvd.nist.gov/vuln/detail/cve-2026-99362">NVD-CVE-2026-99362</a></li>

</ul>
</details>

**Tags**: `#Linux kernel`, `#NFS`, `#security vulnerability`, `#CVE-2026-99362`, `#remote root`

---

<a id="item-tech-news-2"></a>
### [WebRTC Card-Skimming Scripts Reportedly Found on Shopping Sites](https://www.infohawk.com/news/2026-11-27-black-friday-webrtc-skimmer) ⭐️ 7.0/10

An InfoHawk report dated Nov. 27, 2026, reportedly describes credit card skimming scripts on popular shopping sites that use WebRTC. The supplied analysis says the scripts highlight risks from third-party JavaScript embedded in e-commerce pages. The material does not identify affected merchants, script operators, or the number of sites, and it provides no independent confirmation.

hackernews · scanr · Nov 27, 15:40 · [Discussion](https://news.ycombinator.com/item?id=50668145)

**「How checkout skimming works」** Magecart-style web skimming works by compromising third-party JavaScript that online shops load into checkout pages; The Hacker News notes that a modern checkout can load dozens of such scripts and that Sansec has counted more than 100,000 sites hit by web-skimming and supply-chain attacks. The reported WebRTC variant follows that pattern, with the skimmer and stolen card data likely traveling over a WebRTC channel that security tools watch less closely. A connect-src rule that blocks the two web requests needed before WebRTC opens is one mitigation identified in coverage of the incident.

**「What merchants should do」** The five named stores — Lascana, Samsonite, American Tourister, Revolve and FWRD — had the skimmer planted in the week before Black Friday and took action only after being contacted, so other retailers should treat third-party JavaScript on checkout pages as an active compromise path rather than a theoretical one. Because WebRTC data channels have previously been documented carrying skimmer payloads and stolen data past Content Security Policy controls, e-commerce teams cannot rely on CSP alone here and should pair script inventory and integrity checks with monitoring for WebRTC traffic originating from payment pages.

**「Community discussion」** Commenters pushed back on treating WebRTC as the root cause: one argued the same skimming could be done with ordinary HTTP requests and that embedded third-party scripts are the real vulnerability, while another said the report justifies ad blocking. Others questioned why ad and third-party code is not sandboxed to prevent client-side JavaScript execution.

<details><summary>References</summary>
<ul>
<li><a href="https://daily.dev/posts/credit-card-skimming-scripts-using-webrtc-found-on-popular-shopping-sites-mr8zgdbaf">Credit card skimming scripts using WebRTC found on...</a></li>
<li><a href="https://thehackernews.com/search/label/Magecart">Magecart — Latest News, Reports &amp; Analysis | The Hacker News</a></li>
<li><a href="https://www.infohawk.com/news/2026-11-27-black-friday-webrtc-skimmer">Credit card skimming scripts using WebRTC found on popular ...</a></li>
<li><a href="https://thehackernews.com/2026/03/webrtc-skimmer-bypasses-csp-to-steal.html">WebRTC Skimmer Bypasses CSP to Steal Payment Data from E ...</a></li>

</ul>
</details>

**Tags**: `#web security`, `#credit card skimming`, `#WebRTC`, `#third-party scripts`, `#e-commerce`

---

<a id="item-tech-news-3"></a>
### [Essay examines how proof-checker bugs yield false computer-checked proofs](https://cr.yp.to/proofs/falseccp.html) ⭐️ 7.0/10

The linked essay examines how bugs in proof checkers can produce false computer-checked proofs, so acceptance by a checker does not by itself establish that a proof is valid. It is a cautionary technical analysis rather than a report of a new exploit. The discussion supplies concrete context: Metamath&\#x27;s set.mm and iset.mm require five independently created verifiers in five programming languages, and one commenter reports a proof that passed both Lean and a then-week-old nanoda by exploiting a different bug in each.

hackernews · \_tk\_ · Nov 27, 15:26 · [Discussion](https://news.ycombinator.com/item?id=50667989)

**「Background」** The essay&\#x27;s concern has a recent concrete precedent: a postmortem of Lean kernel soundness bug \#14576, covering an AI-assisted disproof of the Collatz conjecture, describes how an invalid proof passed Lean and also slipped past the independent Rust-based checker nanoda because of a separate bug in projection-node verification. Lean&\#x27;s Leonardo de Moura subsequently reported that both bogus proofs are rejected by nanoda and by external checkers not built on the Lean runtime.

**「Impact」** Teams that accept formal proofs should treat the checker as part of their trusted computing base and, where assurance matters, require independent verifiers rather than one successful run; the Metamath model shows what that looks like in practice.

**「Community discussion」** Commenters pushed back on treating a single bad check as a broad indictment: twotwotwo and dwheeler stress that soundness bugs are real but that multiple independent checkers, such as Metamath&\#x27;s five-verifier requirement, make successful deception much harder, while gr\_norm argues that all known soundness bugs in decades-old systems would fit in a tweet and remain comfortably acceptable for 99.9% of software. andai raises a separate limitation: an agent can prove an implementation correct against its own mistaken formalization of the requirement, yielding a formally verified result that is wrong in intent.

<details><summary>References</summary>
<ul>
<li><a href="https://aitoolly.com/ai-news/article/2026-08-02-lean-kernel-soundness-bug-14576-postmortem-of-the-ai-assisted-collatz-conjecture-disproof-and-fix">Lean Kernel Bug #14576: Postmortem and Technical Analysis | AIToolly</a></li>
<li><a href="https://leodemoura.github.io/blog/2026-8-24-postmortem-for-the-kernel-soundness-bug-hunt/">Postmortem for the Kernel Soundness Bug Hunt — Leonardo de Moura</a></li>

</ul>
</details>

**Tags**: `#formal verification`, `#proof assistants`, `#soundness bugs`, `#Lean`, `#Metamath`

---

<a id="item-tech-news-4"></a>
### [State AGs sue SpaceX over Grok&\#x27;s alleged CSAM and intimate-image output](https://www.oag.state.va.us/media-center/news-releases/jay-jones/3162-attorneys-general-jones-and-rayfield-file-suit-against-spacex-parent-company-of-x-xai-and-grok-over-creation-and-promotion-of-child-exploitation-and-non-consensual-images-on-platform) ⭐️ 7.0/10

State attorneys general, including Virginia Attorney General Jay Jones and Rayfield, sued SpaceX—described in the action as the parent company of X, xAI, and Grok—over allegations that Grok generated child sexual abuse material and non-consensual intimate images. The suit seeks to stop Grok from producing such content, but the allegations have not been established in court. The available account does not specify the number of participating states or the precise relief sought.

hackernews · DeepLogin · Nov 27, 19:42 · [Discussion](https://news.ycombinator.com/item?id=50670855)

**「Earlier demands and litigation」** The suits follow earlier pressure over the same conduct: a coalition of state attorneys general, including New Jersey&\#x27;s acting attorney general, sent xAI a letter demanding it stop Grok from producing non-consensual intimate images and child sexual abuse material, and a child sexual abuse survivor had already sued xAI alleging it ignored industry-standard safeguards while generated CSAM spread on X. The new filings move that pressure from demand letters and private litigation into consumer-protection lawsuits brought by Oregon and Virginia against SpaceX Super Intelligence.

**「Impact」** The suit puts X/xAI in the path of state enforcement that relies on existing consumer-protection, child-safety, and criminal authorities rather than a new AI-specific statute. That approach increases compliance risk for platform and AI operators beyond this case, though First Amendment and Section 230 limits may constrain the remedies states can obtain and against whom.

**「Community discussion」** Commenters questioned whether Grok&\#x27;s safeguards were unusually permissive or had to be tricked, and one asked why the users who allegedly made the images are not the target. Another asserted—without support in the item—that Supreme Court precedent protects AI-generated CSAM when no real children are involved; that is a commenter&\#x27;s legal opinion, not an established fact.

<details><summary>References</summary>
<ul>
<li><a href="https://www.engadget.com/2325111/two-states-sue-spacex-over-sexually-explicit-grok-deepfakes/">Two States Sue SpaceX Over Sexually Explicit Grok Deepfakes</a></li>
<li><a href="https://www.theguardian.com/technology/2026/sep/03/elon-musk-ai-grok-child-porn-lawsuit">Child sexual abuse survivor alleges Elon Musk’s AI... | The Guardian</a></li>
<li><a href="https://www.tapinto.net/towns/phillipsburg/sections/around-new-jersey/articles/acting-ag-davenport-demands-immediate-action-from-xai-to-stop-production-of-nonconsensual-intimate-images-and-child-sexual-abuse-material">Acting AG Davenport Demands Immediate Action from xAI to... | TAPinto</a></li>
<li><a href="https://www.lexology.com/library/detail.aspx?g=8ac74728-f1b0-423a-be4e-f714c3a6d402">Abusive Images Are Posted on an Online Platform —Now... - Lexology</a></li>
<li><a href="https://www.theverge.com/ai-artificial-intelligence/855832/grok-undressing-children-csam-law-x-elon-musk">Grok is undressing children — can the law stop it? | The Verge</a></li>
<li><a href="https://factually.co/fact-checks/justice/state-attorneys-general-online-nonconsensual-sexual-imagery-remedies-08ecba">How have U.S. state attorneys general historically han...</a></li>

</ul>
</details>

**Tags**: `#AI governance`, `#generative AI`, `#content safety`, `#platform liability`, `#xAI/Grok`

---

<a id="item-tech-news-5"></a>
### [Google Research claims DeepCrossAttention delivers up to 3x speedup](https://research.google/blog/supercharging-transformer-residual-connections/) ⭐️ 7.0/10

Google Research published a blog post describing DeepCrossAttention, a transformer residual-connection and attention technique that it claims reaches comparable model quality up to 3x faster. The supplied material contains only the headline claim and reader comments—no methodology, model sizes, hardware, benchmark setup, or independent verification—so both the quality parity and the speedup remain unverified. No availability, code, or compatibility details are provided for researchers who might want to test it.

hackernews · ComputedCamp995 · Nov 27, 23:06 · [Discussion](https://news.ycombinator.com/item?id=50672565)

**「Background」** Standard transformer residual connections combine a layer’s output with earlier representations through fixed sums. DeepCrossAttention, described in a February 2025 arXiv paper, instead uses learnable, input-dependent weights and depth-wise cross-attention to combine outputs from earlier layers, aiming to prevent the information dilution that Google Research associates with traditional residual connections.

**「Impact」** For transformer researchers and engineers, the immediate consequence is that the result cannot yet be evaluated for compatibility with existing training or inference stacks: the supplied material gives no model sizes, hardware, benchmark setup, or code.

**「Community discussion」** Commenters did not discuss benchmark methodology; one criticized the post&\#x27;s use of line charts for comparisons that are not temporal, and another asked whether the technique could compound with existing speed methods such as MTP and Dflash. Those are reader reactions, not evidence about the claimed speedup.

<details><summary>References</summary>
<ul>
<li><a href="https://research.google/blog/supercharging-transformer-residual-connections/">Supercharging transformer residual connections - Google Research</a></li>
<li><a href="https://arxiv.org/abs/2502.06785">[2502.06785] DeepCrossAttention: Supercharging Transformer ...</a></li>

</ul>
</details>

**Tags**: `#transformer architectures`, `#attention mechanisms`, `#model efficiency`, `#Google Research`, `#LLM training`

---

<a id="item-tech-news-6"></a>
### [SemiAnalysis Benchmarks Trainium3 Inference Against Nvidia GB300](https://newsletter.semianalysis.com/p/trainium3-inferencex) ⭐️ 7.0/10

SemiAnalysis published a Trainium3 deep dive and microbenchmark analysis arguing that AWS&\#x27;s custom accelerator can trade blows with, or beat, Nvidia&\#x27;s GB300 on cost per generated token at total cost of ownership for inference. Its AgentX coding-agent replay and InferenceX Pareto-frontier tests place a Trainium3 PDS + vLLM configuration ahead of every accelerator except Vera Rubin across the TCO-versus-p90-interactivity curve. The analysis attributes part of the advantage to a ground-up ML microarchitecture with tiles as a first-class primitive and Trainium Descriptor Generation Engines reaching peak HBM bandwidth utilization at small message sizes, which it says Nvidia GPUs cannot do. These are SemiAnalysis benchmark claims developed with AWS Annapurna Labs input; the supplied excerpt gives no absolute numbers, so they are not independent confirmation of a production breakthrough.

rss · Semianalysis · Nov 27, 15:54

**「Background」** Trainium is AWS&\#x27;s family of custom machine-learning accelerators, and Trainium3 succeeds Trainium2. AWS claims that Trn3 UltraServers using Trainium3 offer up to 4.4x higher performance, 3.9x higher memory bandwidth, and 4x better performance per watt than Trn2 UltraServers.

**「Cost-per-token trade-off for agentic serving」** For teams serving coding-agent or other decode-heavy inference, SemiAnalysis&\#x27;s AgentX replay puts Trainium3 at $1.05 per chip-hour against $2.31 for GB300 NVL72, with up to 2.28x better performance per dollar — but that gain is tied to running the tested stack \(Trainium3 PDS with vLLM\) and comes with 4.9 TB/s of HBM bandwidth per chip versus 8.0 TB/s on GB300, so workloads that are purely bandwidth-bound at low batch may see the advantage shrink or invert. The figures come from SemiAnalysis&\#x27;s own UBenchX/InferenceX suites, run with AWS Annapurna architecture-team assistance, rather than an independent production deployment.

<details><summary>References</summary>
<ul>
<li><a href="https://aws.amazon.com/ec2/instance-types/trn3/">Gen AI Compute Instance - Amazon EC2 Trn3 UltraServers - AWS</a></li>
<li><a href="https://newsletter.semianalysis.com/p/trainium3-inferencex">AWS Challenger: Trainium3 Inference and Microarchitecture ...</a></li>
<li><a href="https://cryptobriefing.com/trainium3-nvidia-gb300-inference-benchmark/">Trainium3 competes with Nvidia GB300 in inference performance ...</a></li>
<li><a href="https://www.kucoin.com/news/flash/amazon-trainium3-outperforms-nvidia-gb300-in-cost-efficiency-for-ai-inference">Amazon Trainium3 Outperforms Nvidia GB300 in Cost ... - KuCoin</a></li>

</ul>
</details>

**Tags**: `#AWS Trainium`, `#AI hardware`, `#inference`, `#microarchitecture`, `#custom silicon`

---

<a id="item-tech-news-7"></a>
### [Minecraft Bedrock Resource-Pack Flaw Affects 26.52–26.63, Fixed in 26.65](https://www.zaikei.co.jp/article/20261119/878386.html) ⭐️ 7.0/10

A resource-pack vulnerability in Minecraft Bedrock allowed packs containing a content.zipe file to alter Ore UI files and run hidden scripts, according to developer 8Crafter, who disclosed it on Reddit on November 15. 8Crafter reported confirmed impact on versions 26.52 through 26.63, with earlier versions possibly affected, across PC, mobile, and console; Java Edition is unaffected. With resource-pack auto-download enabled when joining a server or Realm, players could receive such a pack without installing it manually; described exploits include deleting all saves, exposing the player&\#x27;s IP, silently opening arbitrary URIs on Windows, and launching a batch file to download malware. Mojang fixed the issue in version 26.65; AxmBro released a read-only Windows detection tool that finds content.zipe files but cannot determine whether a pack is malicious, and the report cites no CVE or primary advisory.

telegram · zaihuapd · Nov 27, 18:04

**「Background」** Resource packs in Minecraft Bedrock can carry UI definitions and scripts, not only textures, and servers or Realms can offer them for automatic download when that setting is enabled. Ore UI is the game&\#x27;s interface framework, so a pack able to alter its files crosses from cosmetic content into executable behavior.

**「Update before joining」** Players who join servers or Realms with automatic resource-pack downloads should update Bedrock to 26.65 before connecting, because earlier 26.52–26.63 builds remain exposed to packs that can delete worlds or fetch malware on Windows. AxmBro&\#x27;s Windows scanner can flag a content.zipe file but cannot determine whether a pack is malicious, so a clean scan is not a substitute for patching.

<details><summary>References</summary>
<ul>
<li>Minecraft Bedrock Malware Flaw: Update, Scan, Back Up</li>

</ul>
</details>

**Tags**: `#Minecraft Bedrock`, `#security vulnerability`, `#resource packs`, `#malware`, `#game security`

---

<a id="item-tech-news-8"></a>
### [Microsoft moves to replace some third-party Windows drivers](https://www.techspot.com/news/114721-microsoft-wants-replace-most-third-party-device-drivers.html) ⭐️ 7.0/10

Microsoft confirmed at Ignite 2026 that it is developing new drivers for entire hardware classes and will rely more on built-in Windows drivers, aiming to keep more third-party code out of the kernel. Printing is the first focus, with the recently introduced Windows Ready Print mode intended to replace legacy third-party print drivers. Windows product manager Mehmet Kucukgoz said SoundWire and SDCA audio drivers will soon become built-in Windows components, while I3C bus, USB Ethernet, and MIPI camera drivers are also in development; Microsoft separately launched a Driver Quality Initiative to raise reliability, quality, and security standards and encourage third-party developers and OEMs to use built-in drivers where possible.

telegram · zaihuapd · Nov 28, 02:09

**「Background」** Device drivers on Windows are conventionally supplied by hardware vendors and OEMs as kernel-mode code, so each third-party driver adds a component running with high privilege in the operating system core. Microsoft has already applied the in-box model to printing through its recent Windows Ready Print mode, which replaced legacy third-party print drivers, and it introduced a Driver Quality Initiative at its Windows Hardware Engineering Conference to raise driver reliability, quality and security standards.

**「Impact」** Third-party driver developers and OEMs are being encouraged to rely on Windows&\#x27; built-in drivers rather than custom kernel code, including for OEM-specific drivers. For affected printer, audio, USB Ethernet, I3C, and camera hardware, the practical step is to check whether the built-in drivers cover the device&\#x27;s features and align OEM customizations with that guidance.

**Tags**: `#Windows`, `#device drivers`, `#kernel security`, `#Microsoft`, `#hardware ecosystem`

---

## Financial News

<a id="item-finance-news-1"></a>
### [中国国常会部署稳市机制，优化中央汇金类“平准基金”功能](https://www.tmtpost.com/nictation/8220182.html) ⭐️ 8.0/10

中国国务院常务会议于11月27日提出，要加力发挥“国家队”稳市作用，进一步优化中央汇金公司的类“平准基金”功能，并提供充足流动性保障；同时要求推动上市公司加大分红回购力度、完善保险、企业年金、社保基金等中长期资金入市支持引导政策。会议未公布具体规模、工具安排或时间表。

telegram · zaihuapd · Nov 27, 05:35

**「Background」** Central Huijin is a state-owned investment company that has described itself as the market’s “national team,” playing a quasi-“stabilization fund” role — stepping in to buy shares or funds when prices fall sharply \(tool-1-3\).

<details><summary>References</summary>
<ul>
<li><a href="https://36kr.com/p/3242170090487424">A股 史 上最强“ 稳 市 组合拳”，脉络清晰了-36氪</a></li>

</ul>
</details>

**Tags**: `#资本市场`, `#国常会`, `#中央汇金`, `#平准基金`, `#中长期资金`

---

<a id="item-finance-news-2"></a>
### [蜜雪冰城5亿元入股DeepSeek，后者新一轮融资规模约1000亿元](https://m.sohu.com/a/1107027659_115479) ⭐️ 7.0/10

据搜狐报道，DeepSeek 完成第二轮融资，募资规模为1000亿至1055亿元人民币，投后估值约6155亿元；蜜雪冰城通过天津砺思星深基金认缴5亿元，为31家新增出资人之一。

telegram · zaihuapd · Nov 27, 06:33

**「Background」** The reported second round follows DeepSeek&\#x27;s first raise, which brought in more than $7.4 billion at a valuation above $50 billion, The Wall Street Journal reported.

<details><summary>References</summary>
<ul>
<li>DeepSeek Looks to Double Workforce as Fresh Funding Fuels Growth - WSJ</li>

</ul>
</details>

**Tags**: `#DeepSeek`, `#AI financing`, `#Mixue Bingcheng`, `#China venture capital`, `#Tech investment`

---

<a id="item-finance-news-3"></a>
### [China&\#x27;s Central Bank Lowers Minimum Purchase for Large-Denomination CDs to 100,000 Yuan](https://www.news.cn/fortune/20261127/70789d77822242cc82216f51a416f872/c.html) ⭐️ 7.0/10

The People&\#x27;s Bank of China published new rules on November 27 cutting the minimum individual purchase for large-denomination certificates of deposit to 100,000 yuan from 200,000 yuan, and the institutional minimum to 5 million yuan from 10 million yuan. The rules take effect on March 21, 2027, alongside separate deposit and lending rate rules requiring financial institutions to set rates independently and barring improper methods such as attracting deposits with high interest.

telegram · zaihuapd · Nov 27, 11:36

**「Background」** Large-denomination certificates of deposit are bank deposits with a regulatory minimum purchase size; the previous floors were set under interim rules issued in 2015.

**「Impact」** The lower threshold widens access for individual savers with at least 100,000 yuan, while the pricing rules restrict banks&\#x27; use of above-market deposit rates to compete for funding.

**Tags**: `#央行新规`, `#大额存单`, `#存款利率`, `#银行业监管`

---