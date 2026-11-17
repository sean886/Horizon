---
layout: default
title: "Horizon Summary: 2026-11-17 (EN)"
date: 2026-11-17
lang: en
---

> From 48 items, 14 important content pieces were selected

---

**Technology News**
1. [vLLM v0.34.0 makes memory-aware KV cache default, drops Model Runner V1](#item-tech-news-1) ⭐️ 8.0/10
2. [Jiff 1.0 Brings a Stable Rust Datetime Library](#item-tech-news-2) ⭐️ 8.0/10
3. [Optimizely reportedly served malware via third-party scripts on Zoom, GitLab](#item-tech-news-3) ⭐️ 8.0/10
4. [US Extends Advanced AI Chip Export Controls to Remote Access](#item-tech-news-4) ⭐️ 8.0/10
5. [Carnegie Mellon launches CS Learn with free full-semester lectures on YouTube](#item-tech-news-5) ⭐️ 7.0/10
6. [Report: Windows 11 Telemetry Tracks Which Coding Agents and Dev Tools You Run](#item-tech-news-6) ⭐️ 7.0/10
7. [Microsoft blames major email outage on July fix defect](#item-tech-news-7) ⭐️ 7.0/10
8. [Marimba pairs frozen Qwen3-ASR encoder with calibrated speech-query readouts](#item-tech-news-8) ⭐️ 7.0/10
9. [duetto steers a frozen music transformer for live jazz accompaniment](#item-tech-news-9) ⭐️ 7.0/10
10. [Amazon Says AI Agents Stole API Keys to Fund More Model Calls](#item-tech-news-10) ⭐️ 7.0/10
11. [Alibaba, Tencent, Moonshot Limit Offensive Cyber Capabilities in New Models](#item-tech-news-11) ⭐️ 7.0/10

**Financial News**
1. [Intel and CEO sued by shareholders after 28.6% stock plunge](#item-finance-news-1) ⭐️ 8.0/10
2. [Nvidia CEO Jensen Huang resigns, with ETF experts weighing AI trade rotation](#item-finance-news-2) ⭐️ 7.0/10
3. [Cantor Fitzgerald&\#x27;s reported Nvidia stake cut draws scrutiny amid Lutnick China questions](#item-finance-news-3) ⭐️ 7.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [vLLM v0.34.0 makes memory-aware KV cache default, drops Model Runner V1](https://github.com/vllm-project/vllm/releases/tag/v0.34.0) ⭐️ 8.0/10

vLLM v0.34.0, a release with 1,061 commits from 412 contributors, makes extensible, memory-aware KV cache sizing the default on CUDA and ROCm and removes Model Runner V1, leaving Model Runner V2 as the only GPU runner. The new default sizes the cache from memory free after CUDA graph capture and warmup; the release notes say this yields a larger cache \(MiniMax-M3 on H200: 433k to 672k tokens\) but can raise per-token decode latency by 6–18% on some H200 models at concurrency 128, with opt-outs via --gpu-memory-utilization 0.9 or --no-enable-extensible-kv-cache. Upgrading also changes the default --block-size from 16 to 64, drops ROCm 7.2 artifacts in favor of ROCm 10.0, and requires huggingface\_hub &gt;=2.0.0, tokenizers &gt;=0.23.3, and timm &gt;=1.0.30. The release adds 10 models, including Mistral Large 4, and reports speedups such as up to 1.95x decode for Step5 on 4xGB200 and 1.24–1.40x faster long-prompt TTFT for GLM-5.3.

github · khluu · Nov 16, 23:22

**「Background」** vLLM is an open-source LLM inference and serving engine. Its KV cache stores attention key/value tensors for tokens already processed, avoiding recomputation during decoding; cache capacity therefore limits how many tokens can be held for concurrent requests and directly affects throughput and latency.

**「Impact」** Existing vLLM deployments must remove VLLM\_USE\_V2\_MODEL\_RUNNER=0 because it now fails at startup, port custom V1 logits processors to vllm.v1.worker.gpu.sample.logits\_processor, and pass --block-size 16 explicitly if they depend on the old default; ROCm 7.2 users must move to ROCm 10.0 images and wheels. Because the new KV cache default can improve throughput while worsening per-token latency, latency-sensitive services should benchmark and use the documented opt-outs.

**Tags**: `#vLLM`, `#LLM inference`, `#open source`, `#KV cache`, `#performance`

---

<a id="item-tech-news-2"></a>
### [Jiff 1.0 Brings a Stable Rust Datetime Library](https://burntsushi.net/jiff/) ⭐️ 8.0/10

Jiff 1.0, a datetime library for Rust by burntsushi, has reached a stable 1.0 release. The release gives Rust developers a new option for date-and-time handling and has prompted discussion of API design and time-scale handling. The available material does not specify compatibility with existing libraries or which non-UTC time scales are supported.

hackernews · burntsushi · Nov 16, 16:53 · [Discussion](https://news.ycombinator.com/item?id=50519744)

**「Background」** Jiff is a Rust datetime library whose stated design goal is to provide high-level datetime primitives that are difficult to misuse while keeping reasonable performance. It also has a comparison page for other prominent open-source Rust datetime libraries, and a September 2026 comparison listed Jiff’s minimum Rust version as 1.70, versus 1.62.0 for chrono 0.4.45 and 1.88.0 for time.

**「Impact」** Rust developers can now evaluate Jiff 1.0 as a stable-versioned dependency for new date-time code; teams with specialized requirements, such as the orbital-simulation use case raised in comments, must check whether it covers the needed time scales and date ranges before adopting it.

**「Community discussion」** A former chrono maintainer said he took on that project because he thought its API could be improved, then left because attempts at improvement met resistance and caused burnout, and he expressed gratitude to burntsushi for writing Jiff. Other commenters praised Jiff&\#x27;s explicit acknowledgment that it is not the right tool for every use case and hoped for wider adoption, while a user working on solar-system simulations asked how Jiff handles time scales generally and whether UT1 could be added, citing needs from microseconds to gigayears.

<details><summary>References</summary>
<ul>
<li><a href="https://github.com/BurntSushi/jiff">GitHub - BurntSushi/jiff: A datetime library for Rust that ...</a></li>
<li><a href="https://docs.rs/jiff/latest/jiff/_documentation/comparison/index.html">jiff::_documentation::comparison - Rust - Docs.rs</a></li>
<li><a href="https://www.pistack.xyz/posts/2026-09-21-rust-datetime-libraries-chrono-jiff-time-hifitime-comparison/">Tired of Timezone Bugs in Rust? chrono vs jiff vs time vs ...</a></li>

</ul>
</details>

**Tags**: `#Rust`, `#datetime library`, `#time scales`, `#API design`, `#open source`

---

<a id="item-tech-news-3"></a>
### [Optimizely reportedly served malware via third-party scripts on Zoom, GitLab](https://blog.report-uri.com/worlds-largest-brands-infected-with-malware-via-optimizely/) ⭐️ 8.0/10

A Report-URI blog post reports that Optimizely was compromised and used to serve malware through its third-party scripts on high-traffic sites including Zoom and GitLab. According to a commenter quoting the post, Optimizely&\#x27;s CDN served exactly the code it was given, so this was not a CDN cache-poisoning attack, and Optimizely&\#x27;s own www and login sites also carried the code. The initial access path remains unresolved: the report says it is unknown whether attackers compromised an Optimizely system, a credential with cross-customer access, or something else.

hackernews · kristjansson · Nov 16, 23:00 · [Discussion](https://news.ycombinator.com/item?id=50524767)

**「How the third-party script risk works」** Optimizely Web is a widely used testing and optimization tool that sites embed as a third-party script. Because that script runs inside the host page, a hostile version can affect visitors across many unrelated sites without those sites changing their own code—the pattern Report URI documented when it found 188 infected Optimizely script files across 178 organizations.

**「Impact」** Site operators that embed Optimizely&\#x27;s client-side snippet face a third-party script supply-chain exposure: code delivered through a trusted optimization vendor can be malicious even when the vendor&\#x27;s CDN is functioning normally. Because the report leaves the initial-access path unresolved, affected customers cannot yet rule out compromised credentials or cross-customer access, making a review of vendor access and snippet behavior a concrete action concern.

**「Community discussion」** Commenters focused on the structural risk of third-party tag management: stickfigure argued that tools like Google Tag Manager traded engineering control for marketing autonomy and bloated pages, while mcoliver called the incident avoidable and urged vendor security checks, phased rollouts, and even self-hosting scripts. eax-eip highlighted the report&\#x27;s admission that initial access is unknown and that the CDN was not cache-poisoned, and skybrian questioned why sites handling sensitive data would be exposed to the same script.

<details><summary>References</summary>
<ul>
<li><a href="https://shiftdelete.net/en/optimizely-malware">Optimizely Malware Hit 178 Sites: What It Stole and What to Do</a></li>
<li><a href="https://vinish.dev/optimizely-web-experimentation-supply-chain-attack-malicious-javascript">Optimizely Supply Chain Attack: Flaw Put Malicious JavaScript ...</a></li>

</ul>
</details>

**Tags**: `#supply-chain security`, `#third-party JavaScript`, `#web security`, `#malware`, `#Optimizely`

---

<a id="item-tech-news-4"></a>
### [US Extends Advanced AI Chip Export Controls to Remote Access](https://www.reuters.com/legal/litigation/us-issues-rule-protect-advanced-ai-chips-being-accessed-remotely-2026-11-16/) ⭐️ 8.0/10

The U.S. Commerce Department issued an interim final rule on Nov. 16 extending export controls on advanced AI chips and servers to remote access, targeting third-country data centers used to circumvent restrictions. The rule also requires licenses for reexports of AI chips to Indonesia, Malaysia, Singapore, Thailand, and Brazil. It was drafted under the lead of the Treasury Department and the National Security Council, according to the source, and may further tighten China&\#x27;s access to advanced chips.

telegram · zaihuapd · Nov 16, 14:44

**「Background」** Export controls have traditionally regulated the physical shipment or reexport of controlled hardware; they did not clearly cover a foreign data center offering remote computing access to advanced AI chips and servers. That distinction created a potential circumvention route through third countries, which the new interim final rule is intended to close.

**「Impact」** Data-center operators and cloud providers that reexport advanced AI chips to Indonesia, Malaysia, Singapore, Thailand, or Brazil now face a license requirement, and providers offering remote access to controlled chips must assess whether cross-border cloud arrangements fall under the expanded controls.

<details><summary>References</summary>
<ul>
<li><a href="https://wccftech.com/the-u-s-shuts-chinas-access-to-advanced-chips-via-singapore-brazil-indonesia-malaysia-and-thailand-as-scott-bessent-gives-nvidia-10-days-to-show-it-did-not-goose-its-revenues/">The U.S. Shuts China&#x27;s Access To Advanced Chips Via Singapore ...</a></li>

</ul>
</details>

**Tags**: `#AI chip export controls`, `#remote access`, `#data centers`, `#US-China tech policy`, `#semiconductors`

---

<a id="item-tech-news-5"></a>
### [Carnegie Mellon launches CS Learn with free full-semester lectures on YouTube](https://www.cs.cmu.edu/learn/) ⭐️ 7.0/10

Carnegie Mellon&\#x27;s Griffin School of Computer Science has launched CS Learn, publishing full semesters of lectures from current CMU computer science courses for free on YouTube, with one course premiering each day during launch week and more courses planned for January. Phillip Compeau, who runs CS Learn, said a few students built tools that automate much of the production work, allowing a small team to produce the courses. Commenters highlighted Tianqi Chen&\#x27;s ML Systems course and the upcoming 15-259 Probability and Computing.

hackernews · pcompeau · Nov 16, 20:43 · [Discussion](https://news.ycombinator.com/item?id=50522980)

**「Background」** The new release is not Carnegie Mellon&\#x27;s first free online computer science offering: CMU already runs CS Academy, a free interactive high-school curriculum that includes teacher training, an online textbook, and technical support, according to a CMU demonstration. In the launch discussion, project lead Phillip Compeau also acknowledged that MIT began publishing open courseware roughly 25 years earlier.

**「What learners should expect」** The release is confirmed as video lectures; no comment confirms that assignments, homework, or assessments will be posted, and a request for core courses such as 15-122, 15-150, 15-151, 15-251, and 15-451 was not answered.

**「Community reaction」** Commenters welcomed specific courses, including ML Systems and 15-259 Probability and Computing, while asking for core CS courses and whether assignments will accompany the videos. One commenter argued that learning fundamentals properly makes AI a power tool rather than a replacement.

<details><summary>References</summary>
<ul>
<li><a href="https://www.youtube.com/watch?v=hztO5vaBTRs">Demonstration of Carnegie Mellon CS Academy - YouTube</a></li>

</ul>
</details>

**Tags**: `#computer science education`, `#open courseware`, `#online learning`, `#CMU`, `#YouTube`

---

<a id="item-tech-news-6"></a>
### [Report: Windows 11 Telemetry Tracks Which Coding Agents and Dev Tools You Run](https://xusheng.dev/posts/windows-coding-agent-telemetry/) ⭐️ 7.0/10

A post on xusheng.dev, dated November 16, 2026, reports that Windows 11 telemetry collects data identifying which coding agents and developer tools are installed or used on a machine, framing it as a privacy and platform-trust issue for developers. The item as supplied contains no article text, so the specific telemetry fields, the collection mechanism, and whether the data is linked to identifiable users or machines cannot be verified here; the claim rests on the author&\#x27;s analysis alone. The report drew enough attention on Hacker News to prompt a broader discussion about moving development work off Windows.

hackernews · cwaffles · Nov 16, 22:58 · [Discussion](https://news.ycombinator.com/item?id=50524736)

**「How Windows diagnostic telemetry works」** Windows&\#x27; optional diagnostic reporting runs through the Connected User Experiences and Telemetry service \(DiagTrack\), which hosts components such as AggregatorHost.exe and produces ETW-based reports. The investigation behind this report reverse-engineered a component called MissionControlAggregator and found that it generates a compact usage bitmap showing whether particular coding agents and developer tools have run, rather than a transcript of coding sessions; the researcher tested on Windows 11 build 26200.9974 with DLL version 10.0.26100.9818 and reported finding no prompts or session content. The relevant distinction is that this information is queued through optional diagnostic reporting rather than being collected by a separate mechanism.

**「Impact for developers」** Developers evaluating Windows for AI-assisted workflows now have a concrete reason to check what their tooling exposes before installing coding agents, and the supplied discussion suggests some are treating the report as a prompt to test Linux instead — one commenter describes running Linux from an external drive to evaluate it, another says the switch takes about a week for web-centric work. Commenter herf argues the more urgent gap is sandboxing: Microsoft&\#x27;s MXC sandbox shipped only on October 7 and Claude Code does not yet support it, so agents on Windows run unsandboxed or under WSL.

**「Community discussion」** Much of the thread is about Linux as an alternative: s\_dev claims most single-player games now run perfectly on Linux while multiplayer still has problems, and dead\_hn\_theory says the adjustment period is about a week for people whose tools are already web-based. Countering the purely negative reading, herf argues that non-invasive telemetry about which agents developers use could help Microsoft prioritize missing sandboxing features, which they say the platform needs urgently.

<details><summary>References</summary>
<ul>
<li><a href="https://xusheng.dev/posts/windows-coding-agent-telemetry/">Windows 11 Is Collecting Data on Which Coding Agents and ...</a></li>
<li><a href="https://windowsforum.com/news/windows-11-optional-telemetry-can-report-coding-agent-usage-research-finds.452631/">Windows 11 Optional Telemetry Can Report Coding Agent Usage ...</a></li>
<li><a href="https://www.startuphub.ai/ai-news/technology/2026/windows-11-logs-which-coding-agent-you-ran">Windows 11 logs which coding agent you ran | StartupHub.ai</a></li>

</ul>
</details>

**Tags**: `#windows-telemetry`, `#privacy`, `#developer-tools`, `#ai-coding-agents`, `#linux`

---

<a id="item-tech-news-7"></a>
### [Microsoft blames major email outage on July fix defect](https://www.theregister.com/saas/2026/11/16/microsoft-blames-monster-email-outage-on-software-defect-introduced-in-july-fix/5310026) ⭐️ 7.0/10

Microsoft attributed a major email outage to a software defect introduced in a July fix, The Register reported. The report frames the incident as a post-mortem with lessons about regressions, testing gaps, and load recovery; the supplied material does not include the full technical timeline or the number of users affected.

hackernews · Bender · Nov 16, 13:18 · [Discussion](https://news.ycombinator.com/item?id=50517321)

**「Background」** The defect originated in a fix for Microsoft 365 networking gateway servers that was deployed starting in July 2026 and ran globally for more than three months without visible problems, according to an incident report. By November 12, NPR was reporting that Microsoft was scrambling to restore a widespread Outlook and email outage, several days before the company published its explanation.

**「Impact」** For customers, the outage shows that a vendor-side regression can take email offline without any change on their side, leaving detection and recovery to Microsoft&\#x27;s own remediation.

**「Community discussion」** Commenters compared the recovery to an electricity grid black start, with one arguing that demand must be brought back in controlled blocks, and another asking why Microsoft did not throttle or randomly sample incoming connections to let the service recover gradually. A separate thread questioned whether it is acceptable for a lower-end test environment to pass the July code while failing to expose a concurrency bug present in production.

<details><summary>References</summary>
<ul>
<li><a href="https://cybersecuritynews.com/microsoft-outage-incident-report/">Microsoft Reveals How a Hidden Windows Bug Took Down Microsoft ...</a></li>
<li><a href="https://www.npr.org/2026/11/12/nx-s1-6039343/outlook-down-widespread-outage-microsoft-email">A negative Outlook: Microsoft scrambles to fix email outage : NPR</a></li>

</ul>
</details>

**Tags**: `#Microsoft 365`, `#outage post-mortem`, `#site reliability`, `#software regression`, `#Exchange Online`

---

<a id="item-tech-news-8"></a>
### [Marimba pairs frozen Qwen3-ASR encoder with calibrated speech-query readouts](https://www.reddit.com/r/MachineLearning/comments/1xxsqro/marimba_a_system_one_model_for_speech_r/) ⭐️ 7.0/10

Marimba, a compact speech model detailed in a new arXiv paper, answers typed yes/no, choice, and score questions over 8-second audio windows and returns calibrated probabilities, using one frozen Qwen3-ASR-0.6B encoder pass to serve all questions. The authors report matching or beating Qwen3-Omni \(30B-A3B\) on 6 of 9 tests over 1,000 public questions, 100% language ID on 300 FLEURS clips, and speaker-change AUROC of 0.966–0.980 on AMI and VoxConverse. They report that turn-end AUROC reaches 0.930 versus 0.982 for Smart Turn v3.2 on Smart Turn&\#x27;s own test set—though the turn-end readout was trained on Smart Turn data—and that every head is at chance on CochlScene scene classification. Code, Apache-2.0 weights, and a \`pip install marimba-audio\` package are linked.

reddit · r/MachineLearning · /u/solanotodesch · Nov 16, 15:47

**「Background」** Marimba&\#x27;s premise is to avoid running a separate model for every audio question: one pass through a frozen Qwen3-ASR-0.6B encoder produces representations that lightweight readouts and calibrated scoring reuse across term, language, turn-end, and speaker queries. The post is a follow-up to an earlier teaser, with the paper now released alongside code, Apache-2.0 weights, and a demo.

**「Impact」** For developers, the reusable frozen encoder pass reduces the cost of asking multiple query types about the same 8-second window, but the chance-level CochlScene result means new tasks should be validated rather than assumed to transfer. Term spotting also depends on scoring ASR hypotheses plus Platt calibration, which the authors acknowledge may not be equivalent to a dedicated keyword-spotting baseline.

**Tags**: `#speech recognition`, `#calibration`, `#model efficiency`, `#Qwen3-ASR`, `#audio understanding`

---

<a id="item-tech-news-9"></a>
### [duetto steers a frozen music transformer for live jazz accompaniment](https://www.reddit.com/r/MachineLearning/comments/1xxkyh3/steering_a_pretrained_music_transformer_at/) ⭐️ 7.0/10

A developer has built duetto, a real-time jazz partner for a MIDI keyboard that plays solo, comping, and walking bass parts alongside a player. Rather than fine-tuning, it uses the pretrained Anticipatory Music Transformer unchanged and controls generation at sampling time: a rule layer masks disallowed notes such as out-of-register pitches, a waiting hand, or off-beat bass notes, and biases likely ones such as current chord tones, downbeat guide tones, and the next note of a quoted phrase. Phrases come from transcribed solos in the Weimar Jazz Database, segmented where soloists breathed, transposed to the tune&\#x27;s chords, and developed over a chorus; in the Autumn Leaves demo at 160 bpm, about 61% of solo notes came from quoted phrases or the theme. The server keeps roughly one second of music sampled ahead and resamples the unplayed part when the player plays, with the developer reporting about 12 ms/note for the medium model and 18 ms/note for the large model on a 3080 Ti, and about 90 ms/note for the large model on a Jetson Orin Nano. The developer notes that the system can drift from the player, respond unpredictably, and become too phrase-book-like with heavy bias or insufficiently jazzy with little bias, and provides a demo and code free for noncommercial use.

reddit · r/MachineLearning · /u/GGAllin43 · Nov 16, 09:19

**「Background」** The Anticipatory Music Transformer \(Thickstun et al., arXiv 2306.08620, first posted June 2023 and revised July 2024\) is a pretrained symbolic-music model built around &quot;anticipation&quot;: it interleaves event and control sequences so that generated material can follow a given part, and its authors report it matches autoregressive baselines while producing high-quality accompaniments. duetto keeps that checkpoint unchanged and imposes musical rules only on the logits at sampling time, making it an alternative to fine-tuning the model on jazz data.

**「Impact」** For developers working with symbolic music models, duetto offers a concrete implementation of inference-time control that avoids retraining the underlying transformer, and its reported Jetson Orin Nano latency indicates the large model can still run in a live setting. The published code is free only for noncommercial use, so commercial integration would require separate permission.

<details><summary>References</summary>
<ul>
<li><a href="https://arxiv.org/abs/2306.08620">[2306.08620] Anticipatory Music Transformer</a></li>
<li><a href="https://paperswithcode.co/paper/2306.08620">Anticipatory Music Transformer (arXiv...) | Papers with Code</a></li>

</ul>
</details>

**Tags**: `#music generation`, `#inference-time control`, `#transformers`, `#constrained decoding`, `#open source`

---

<a id="item-tech-news-10"></a>
### [Amazon Says AI Agents Stole API Keys to Fund More Model Calls](https://cybernews.com/security/amazon-autonomous-cybercrime-artex-framework/) ⭐️ 7.0/10

Amazon reportedly disrupted a campaign in which AI agents, driven by the open-source penetration-testing framework Artex, stole API keys from internet-exposed AI applications including LiteLLM and Dify, validated them, and added them to a shared pool used to pay for additional large-model calls. The activity began on October 3 and was blocked on November 5 by Amazon&\#x27;s MadPot honeypot network, according to Cybernews. Amazon attributed the operation to a China-related threat group with medium confidence, said not all listed targets were compromised, and notified AWS customers that may have been affected.

telegram · zaihuapd · Nov 16, 13:00

**「Background」** LiteLLM is an open-source AI gateway that puts 100+ model providers, MCP tools and agents behind a single API while centrally holding upstream provider keys and budgets; Dify and One API are comparable self-hosted LLM application and proxy platforms. Because one exposed instance can concentrate many providers&\#x27; credentials, these deployments hold exactly what an attacker needs — working, billable model access — behind a single endpoint. Coverage of the same campaign by The Hacker News likewise describes agents probing internet-exposed AI apps for the AI provider keys stored inside them.

**「Exposure and response」** Operators running internet-exposed AI gateways such as LiteLLM, One API, and Dify should treat the AI provider keys stored in those applications as potentially compromised and rotate them, since the harvested credentials were reportedly validated and pooled to fund further model calls rather than used for a single intrusion. Because these gateways sit in the path of an organization&\#x27;s model traffic, a stolen key can expose access to multiple upstream providers at once, so the response needs to cover every provider credential configured on the affected instance, not just the gateway&\#x27;s own authentication token.

<details><summary>References</summary>
<ul>
<li><a href="https://thehackernews.com/2026/11/amazon-uncovers-ai-agent-campaign.html">Amazon Uncovers AI Agent Campaign Targeting LiteLLM , Dify , and...</a></li>
<li><a href="https://docs.litellm.ai/">LiteLLM documentation | liteLLM</a></li>
<li><a href="https://github.com/BerriAI/litellm">GitHub - BerriAI/ litellm : The fastest, litest AI Gateway. Rust core with...</a></li>
<li><a href="https://thehackernews.com/2026/11/amazon-uncovers-ai-agent-campaign.html">Amazon Uncovers AI Agent Campaign Targeting LiteLLM , Dify , and...</a></li>
<li><a href="https://cybelangel.com/blog/the-litellm-supply-chain-attack/">The LiteLLM Breach: 153 GB of AI and Cloud Credentials Exposed</a></li>

</ul>
</details>

**Tags**: `#AI agents`, `#cybersecurity`, `#API key theft`, `#cloud security`, `#threat intelligence`

---

<a id="item-tech-news-11"></a>
### [Alibaba, Tencent, Moonshot Limit Offensive Cyber Capabilities in New Models](https://www.bloomberg.com/news/articles/2026-11-16/china-s-top-ai-firms-limit-cyber-capabilities-in-latest-models) ⭐️ 7.0/10

Alibaba, Tencent and Moonshot have reportedly reduced offensive cyber capabilities in their newest models while improving defensive performance, according to a Bloomberg report summarized in the source item. Alibaba&\#x27;s latest flagship Qwen is not being released with full weights, so users cannot download and customize the complete version. The changes follow a draft export-control rule published last month by China&\#x27;s Ministry of Commerce that would ban exports of AI tools capable of attacking critical infrastructure or government networks; Tencent reportedly cut cyber functions before releasing Hy4 this month.

telegram · zaihuapd · Nov 17, 02:20

**「Background」** Reuters reported that Tencent released its Hy4 model on Nov. 4 after filtering cybersecurity training data related to exploit development, reverse engineering, and penetration testing to reduce offensive use. The current Bloomberg report says Alibaba, Tencent, and Moonshot have extended that approach to newer models, while Alibaba is withholding full Qwen weights as China&\#x27;s Commerce Ministry draft export rules would bar exports of AI tools capable of attacking critical infrastructure or government networks.

**「Impact」** Developers who need to fine-tune or inspect Alibaba&\#x27;s flagship Qwen cannot do so because the full weights are not released, restricting local customization; organizations deploying Chinese models should also factor the draft export-control rule into procurement and compliance planning.

<details><summary>References</summary>
<ul>
<li><a href="https://www.analyticsinsight.net/news/tencent-launches-hy4-ai-model-with-restricted-cybersecurity-training-data">Tencent Launches Hy4 AI Model with Restricted Cybersecurity ...</a></li>
<li><a href="https://www.reuters.com/legal/litigation/tencent-rolls-out-ai-model-trained-with-limited-cybersecurity-data-amid-hacking-2026-11-04/">Tencent rolls out AI model trained with limited cybersecurity ...</a></li>

</ul>
</details>

**Tags**: `#AI governance`, `#cybersecurity`, `#export controls`, `#open-weight models`, `#Chinese AI industry`

---

## Financial News

<a id="item-finance-news-1"></a>
### [Intel and CEO sued by shareholders after 28.6% stock plunge](https://www.investing.com/news/stock-market-news/intel-sued-by-shareholders-following-29-stock-plunge-5028171) ⭐️ 8.0/10

Intel and its CEO were sued by shareholders in a proposed class action alleging the company concealed weak PC demand and inventory buildup, after its below-expectations fourth-quarter forecast was followed by a 28.6% one-day stock plunge and about $140 billion in lost market value. The suit, led by a Michigan pension fund and filed last Friday in San Jose federal court, also names the CFO as a defendant.

telegram · zaihuapd · Nov 16, 11:10

**「Background」** The case is a securities class action—a lawsuit in which investors collectively claim a company misled them—and it covers purchases from July 23 to Oct. 29, after Intel&\#x27;s Oct. 29 fourth-quarter forecast missed expectations and its shares fell 28.6% the next day.

**Tags**: `#英特尔`, `#股东集体诉讼`, `#股价暴跌`, `#业绩指引`, `#半导体`

---

<a id="item-finance-news-2"></a>
### [Nvidia CEO Jensen Huang resigns, with ETF experts weighing AI trade rotation](https://www.cnbc.com/2026/11/14/nvidia-ai-trade-data-centers-congress.html) ⭐️ 7.0/10

Jensen Huang has resigned as Nvidia’s CEO, and ETF experts interviewed by CNBC said Big Tech and other AI chip suppliers could gain if investors lose trust in Nvidia. Yorkville Ives cut its Nvidia price target to $225 from $300 while keeping a buy rating; Nvidia reports third-quarter earnings next Tuesday under interim CEO Colette Kress.

rss · CNBC Finance · Nov 16, 12:13

**「Background」** Nvidia co-founder Jensen Huang resigned as CEO on Thursday amid reports of alleged extramarital affairs, including with a suspected Chinese government asset; Chief Financial Officer Colette Kress became interim CEO. Democrats won control of Congress in the Nov. 3 midterms after candidates campaigned to rein in AI development and slow the data-center buildout.

**「Impact」** Yorkville Ives estimates that Democratic gains that swept control of Congress could prevent 10% of planned data centers from being built at the low end, or 15%-20% at the high end—a forecast that could affect cloud capacity and AI-chip demand.

<details><summary>References</summary>
<ul>
<li><a href="https://finance.yahoo.com/markets/stocks/articles/nvidia-ceo-jensen-huang-resigns-140651041.html?fr=sycsrp_catchall">Nvidia CEO Jensen Huang resigns in wake of affair, spy scandal Nvidia CEO Jensen Huang resigns amid spy scandal : NPR Jensen Huang resigns as Nvidia CEO after alleged affairs Timeline of a scandal: How Jensen Huang&#x27;s abrupt resignation ... Silicon Valley and Trump rally behind Nvidia CEO after his ... Jensen Huang Scandal: Timeline That Led To His Resignation ...</a></li>
<li><a href="https://foreignpolicy.com/2026/11/05/midterm-results-ai-data-centers-texas-georgia-ohio/">Midterm Results Reflect AI , Data Center Concerns</a></li>

</ul>
</details>

**Tags**: `#Nvidia`, `#AI trade`, `#ETFs`, `#data centers`, `#US Congress`

---

<a id="item-finance-news-3"></a>
### [Cantor Fitzgerald&\#x27;s reported Nvidia stake cut draws scrutiny amid Lutnick China questions](https://www.cnbc.com/2026/11/13/howard-lutnick-nvidia-jensen-huang-china-cantor-fitzgerald.html) ⭐️ 7.0/10

Cantor Fitzgerald, now led by Commerce Secretary Howard Lutnick’s sons, reported a 49% decline in its Nvidia share count between September 2025 and March 2026, to 1.78 million shares worth $310 million, CNBC reported, as Axios reported Lutnick repeatedly resisted a China chip-smuggling crackdown. Nvidia CEO Jensen Huang resigned Thursday; CNBC reported no evidence that Cantor’s holdings changes were tied to intelligence warnings or that Lutnick shared nonpublic information.

rss · CNBC Finance · Nov 16, 12:14

**「Background」** Howard Lutnick spent decades at Cantor Fitzgerald — he joined the firm in 1983 — before leaving in February 2025 to become U.S. commerce secretary, and the Wall Street firm is now led by his sons Brandon and Kyle, which is why its Nvidia holdings and financing relationships are being examined for possible conflicts of interest.

<details><summary>References</summary>
<ul>
<li><a href="https://en.wikipedia.org/wiki/Howard_Lutnick">Howard Lutnick - Wikipedia</a></li>

</ul>
</details>

**Tags**: `#Nvidia`, `#U.S. export controls`, `#China tech policy`, `#conflict of interest`, `#Commerce Department`

---