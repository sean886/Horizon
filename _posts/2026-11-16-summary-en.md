---
layout: default
title: "Horizon Summary: 2026-11-16 (EN)"
date: 2026-11-16
lang: en
---

> From 36 items, 10 important content pieces were selected

---

**Technology News**
1. [Meta FAIR/NYU study: vision encoder pretraining optional, vision-only parameters required](#item-tech-news-1) ⭐️ 8.0/10
2. [Meituan releases LongCat-2.5 weights with Huawei-only training claim](#item-tech-news-2) ⭐️ 8.0/10
3. [Protomaps write-up argues self-hosted map tiles are now cheap and easy](#item-tech-news-3) ⭐️ 7.0/10
4. [Explainer Surveys Positional Embeddings in Modern LLMs](#item-tech-news-4) ⭐️ 7.0/10
5. [MacBook Pro OLED PWM flicker and sensitivity](#item-tech-news-5) ⭐️ 7.0/10
6. [Open-source cudamemcpy-tuner claims 5x faster pageable transfers on B300](#item-tech-news-6) ⭐️ 7.0/10
7. [Huawei Cloud launches openPangu-2.1-Pro on MaaS with token pricing](#item-tech-news-7) ⭐️ 7.0/10

**Financial News**
1. [Lutnick faces conflict-of-interest questions over sons&\#x27; firm and Nvidia](#item-finance-news-1) ⭐️ 7.0/10
2. [美光、三星、SK海力士必须应诉DRAM价格操纵指控](#item-finance-news-2) ⭐️ 7.0/10
3. [US, China, Russia leaders to hold first trilateral meeting at Shenzhen APEC](#item-finance-news-3) ⭐️ 7.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [Meta FAIR/NYU study: vision encoder pretraining optional, vision-only parameters required](https://www.reddit.com/r/MachineLearning/comments/1xx1k2o/meta_fair_nyu_unbundling_multimodal_vision/) ⭐️ 8.0/10

A Meta FAIR and NYU author team reports a controlled ablation of multimodal vision encoder design choices across 200+ models, all trained from scratch \(LLM included\) on the same data, with encoder pretraining counted against the same lifetime compute budget. The main comparisons use Qwen3-1.7B and 4B backbones with 0.4B parameters of vision capacity, a scaling ladder from 0.6B to 6.4B, 16 Cambrian VQA benchmarks at 448 px and 12 language benchmarks. Their headline claim is that separate encoder pretraining is optional: encoders pretrained with contrastive, self-supervised or two captioning objectives at best tie a from-scratch encoder at matched compute, and pretraining MetaCLIP 6.5x longer raised ImageNet linear-probe accuracy from 80.4% to 84.4% without improving VQA. Vision-only parameters, by contrast, remained necessary — encoder-free models trailed at every size from 0.6B to 6.4B and needed roughly 3x the compute to catch up — while placing the vision path before the LLM was optional: an &quot;in-fusion&quot; variant adding zero-initialized vision-only attention and FFN weights to the LLM&\#x27;s first 8 layers matched the encoder from 1.7B to 6.4B with about 13% lower time to first token \(45.0 vs 44.4 VQA at 1.7B\). The results are presented by a co-author in a Reddit post linking an alphaXiv preprint, project blog and X threads; the post text is truncated and the work has not been described here as peer-reviewed.

reddit · r/MachineLearning · /u/trungh98 · Nov 15, 17:38

**「Background」** Multimodal LLMs typically use a vision encoder that bundles three design choices: separate pretraining, parameters reserved for vision tokens, and placement before the LLM. Published models have diverged on this setup—the post cites Gemma 4 12B dropping the encoder, Kimi K3 training one from scratch and Inkling 2 Small restoring one—but comparisons are confounded by differences in data, compute and encoder pretraining. The study therefore trains 200+ models from scratch under a shared compute budget to isolate each choice.

**「Where the vision budget should go」** For teams choosing an MLLM vision architecture, the study&\#x27;s practical implication is that vision capacity should be spent on dedicated vision-only parameters rather than on a separately pretrained encoder: encoder-free models in the 0.6B–6.4B ladder trailed at every size and needed roughly 3x the compute to match, while adding zero-initialized vision-only weights to the LLM&\#x27;s first 8 layers matched the encoder with about 13% lower time to first token. Since the 3x compute gap and 13% latency figure are the authors&\#x27; own results on 16 VQA and 12 language benchmarks, they should be validated on a team&\#x27;s own data before an existing encoder pipeline is replaced.

**Tags**: `#multimodal learning`, `#vision encoders`, `#MLLM architecture`, `#pretraining`, `#model scaling`

---

<a id="item-tech-news-2"></a>
### [Meituan releases LongCat-2.5 weights with Huawei-only training claim](https://the-decoder.com/meituan-releases-a-1-6-trillion-parameter-agent-model-that-never-touched-an-nvidia-gpu/) ⭐️ 8.0/10

Meituan&\#x27;s LongCat team has released the weights for LongCat-2.5, an MIT-licensed agent and coding model that activates about 48 billion parameters per token and accepts text, image, and video input. The company says the model was trained entirely on Huawei Ascend accelerators, without Nvidia GPUs, and reports a score of 88.4 on Terminal Bench v2.1, slightly below Claude Opus 5&\#x27;s 89.1. Those training and benchmark claims have not been independently verified in the supplied material.

telegram · zaihuapd · Nov 15, 11:08

**「Background」** Meituan&\#x27;s earlier LongCat-2.0 was a 1.6-trillion-parameter model reported to be trained end-to-end on domestic Chinese accelerators rather than Nvidia GPUs. LongCat-2.5 keeps a 1.6T total/48B active MoE design, according to its Hugging Face model card, while adding native text, image, and video input for long-horizon agentic tasks.

**「Impact」** Developers and organizations can commercially use and modify LongCat-2.5 under its MIT license, but should validate its coding-agent performance on their own workloads because the 88.4 result is vendor-reported and only slightly trails Claude Opus 5&\#x27;s 89.1.

<details><summary>References</summary>
<ul>
<li><a href="https://huggingface.co/meituan-longcat/LongCat-2.5">meituan - longcat / LongCat - 2 . 5 · Hugging Face</a></li>
<li><a href="https://promptyze.com/meituans-longcat-2-0-breaks-nvidia/">Meituan ’s LongCat - 2 .0 Breaks the Nvidia Barrier — 1 . 6 T Parameters ...</a></li>

</ul>
</details>

**Tags**: `#open-source LLMs`, `#AI agents`, `#Huawei Ascend`, `#AI hardware`, `#coding models`

---

<a id="item-tech-news-3"></a>
### [Protomaps write-up argues self-hosted map tiles are now cheap and easy](https://bruceroettgers.eu/blog/protomaps/) ⭐️ 7.0/10

A practical write-up on Protomaps argues that self-hosting map tiles has become cheap and easy enough for individual developers and small projects to run their own mapping stack instead of paying a commercial tile provider. The post is a hands-on account rather than a vendor announcement; the supplied material does not include the specific hosting costs, configuration steps, or benchmarks it reports. In the accompanying discussion, developers describe comparable setups built on static object storage, including Cloudflare R2 and OpenFreeMap&\#x27;s nginx-only deployment, and cite privacy, access control, and reduced load on public tile services as the main reasons to own the infrastructure.

hackernews · bcye · Nov 15, 19:26 · [Discussion](https://news.ycombinator.com/item?id=50509837)

**「Background」** Protomaps&\#x27; approach rests on PMTiles, a cloud-native archive format that packs an entire tileset into a single file served directly from object storage; clients fetch only the byte ranges they need through HTTP range requests, so no tile server or database is required. The project presents this as letting frontend developers self-host maps as &quot;just a file,&quot; which is the mechanism behind the cheap, low-maintenance hosting the write-up describes.

**「What it means」** The constraint commenters flag is zoom-level storage rather than base map serving: one developer building an offline satellite mosaic stopped at zoom 17 because higher-resolution global coverage runs into hundreds of terabytes, which no longer fits a store-it-on-object-storage-and-serve-it-with-a-worker budget. Ordinary basemaps are small enough to host cost-effectively, which is the case that makes the side-project and privacy-driven deployments described in the thread viable.

**「From the discussion」** Commenters point to OpenFreeMap, which offers a free public tile instance with no API keys, registration, or user database and runs with no tile server at all, and to a team serving PMTiles from Cloudflare R2 to keep map infrastructure private and access-controlled. A developer building a Wikipedia walking game said Protomaps made live-rendered local street maps affordable enough that the project would not have been considered with Mapbox or Google Maps, while another cautioned that the cost picture changes sharply for high-resolution satellite imagery.

<details><summary>References</summary>
<ul>
<li><a href="https://protomaps.com/">Protomaps - The open source map in a file</a></li>
<li><a href="https://awesome-repositories.com/repository/protomaps-pmtiles">PMTiles - serve map tiles from cloud storage | Awesome Repos</a></li>

</ul>
</details>

**Tags**: `#protomaps`, `#self-hosting`, `#map-tiles`, `#open-source`, `#pmtiles`

---

<a id="item-tech-news-4"></a>
### [Explainer Surveys Positional Embeddings in Modern LLMs](https://magazine.sebastianraschka.com/p/understanding-positional-embeddings) ⭐️ 7.0/10

A technical explainer hosted on Sebastian Raschka&\#x27;s magazine examines positional embeddings in modern large language models, focusing on how the mechanism is implemented in transformer architectures. It is educational analysis rather than a new model release, benchmark, or research result. No article text was supplied with the item, so the explainer&\#x27;s specific examples, comparisons, and conclusions could not be independently checked.

hackernews · vismit2000 · Nov 15, 12:14 · [Discussion](https://news.ycombinator.com/item?id=50506376)

**「Background」** Positional embeddings are the mechanism Transformer models use to represent token order; modern LLMs commonly use rotary position embeddings \(RoPE\) or ALiBi. RoPE, introduced by Su et al. in 2021, represents relative positions as orthogonal rotations of queries and keys without adding position-specific learnable parameters, while ALiBi uses linear attention biases instead.

**「Impact」** For developers, the practical takeaway is to use the piece as an implementation overview and consult primary theoretical sources when choosing or modifying positional-embedding schemes; a commenter specifically argues that group-representation theory is needed to understand why rotary embeddings work.

**「Community Discussion」** Commenter programjames argued that the article explains only the implementation of positional embeddings, while a full understanding requires group representation theory, describing rotary positional embeddings as representations of the translation group. The comment is an opinion about the article&\#x27;s theoretical depth, not a measured comparison of methods.

<details><summary>References</summary>
<ul>
<li><a href="https://vinija.ai/models/LLM/">Vinija&#x27;s Notes • Primers • Overview of Large Language Models</a></li>
<li><a href="https://arxiv.org/pdf/2512.07805v1">Group Representational Position Encoding - arXiv.org</a></li>
<li><a href="https://apxml.com/courses/how-to-build-a-large-language-model/chapter-13-positional-encoding-variations/rotary-position-embedding-rope">Rotary Position Embedding (RoPE) Explained - apxml.com</a></li>

</ul>
</details>

**Tags**: `#positional embeddings`, `#large language models`, `#transformer architecture`, `#deep learning`, `#technical explainer`

---

<a id="item-tech-news-5"></a>
### [MacBook Pro OLED PWM flicker and sensitivity](https://macanorak.com/the-macbook-pros-oled-pwm-problem-when-a-better-display-becomes-worse-to-use/) ⭐️ 7.0/10

A MacAnorak analysis argues that the MacBook Pro’s OLED display can be harder to use for some display-sensitive people even though it is technically superior, because its pulse-width modulation \(PWM\) dimming can produce flicker. The article examines that tradeoff rather than announcing a new model or software fix. The supplied item does not include the article text or Apple specifications, so the exact PWM rate and the scope of affected users are not established here.

hackernews · MacAnorak · Nov 15, 13:15 · [Discussion](https://news.ycombinator.com/item?id=50506719)

**「Background」** OLED panels commonly regulate brightness with pulse-width modulation \(PWM\), switching pixels on and off rapidly instead of varying current continuously; OLEDs typically run at 240–480 Hz, and lower switching rates are more likely to be perceived as flicker by sensitive viewers. Apple&\#x27;s tandem OLED MacBook Pro, marketed as the &quot;PROLED XDR Display,&quot; succeeds the Mini-LED panel the range has used since 2021. Notebookcheck&\#x27;s review of the 14-inch model reported PWM at 240 Hz and noted that this could still bother sensitive users despite DC dimming.

**「Buyer consideration」** For users who are sensitive to display flicker, the practical consequence is that the OLED MacBook Pro can cause headaches or eye strain during long sessions even though its picture quality is superior, making PWM behavior rather than contrast or color the deciding factor. Because sensitivity varies widely and most people cannot perceive PWM at commercially available frequencies, affected buyers should try the machine in person before committing rather than relying on spec sheets.

**「Community discussion」** Commenters scrutinized the article’s cited 240 Hz PWM figure: one reader argued that the tandem OLED may run two panels out of phase and effectively reach 960 Hz across most usable brightness levels. Others welcomed attention to flicker sensitivity, with one citing a Nature paper suggesting humans can perceive flicker above twice a display’s refresh rate, and another calling for more research into how many people are affected.

<details><summary>References</summary>
<ul>
<li><a href="https://macanorak.com/the-macbook-pros-oled-pwm-problem-when-a-better-display-becomes-worse-to-use/">The MacBook Pro ’s OLED PWM Problem: When a ‘Better’ Display...</a></li>
<li><a href="https://www.notebookcheck.net/Amazing-OLED-panel-Apple-MacBook-Pro-14-PROLED-XDR-Review.1438048.0.html">Amazing OLED panel - Apple MacBook Pro ... - Notebookcheck Review</a></li>
<li><a href="https://screentester.io/flicker-test/">Monitor Flicker Test Online — Screen PWM vs DC Dimming</a></li>
<li><a href="https://ieeexplore.ieee.org/document/10600511">Study of the Presence of Pulse Width Modulated Flicker of the ...</a></li>
<li><a href="https://screenlab.nl/blog/pwm-sensitivity-test/">PWM Sensitivity: Why Some People Get Headaches from Monitors</a></li>

</ul>
</details>

**Tags**: `#OLED displays`, `#PWM flicker`, `#MacBook Pro`, `#hardware usability`, `#display health`

---

<a id="item-tech-news-6"></a>
### [Open-source cudamemcpy-tuner claims 5x faster pageable transfers on B300](https://www.reddit.com/r/MachineLearning/comments/1xx2n25/making_cudamemcpy_5x_faster_on_a_b300_p/) ⭐️ 7.0/10

An open-source project called cudamemcpy-tuner claims to speed up pageable CPU-to-GPU cudaMemcpy transfers by about 5x on an NVIDIA B300. In the author&\#x27;s example, a 1 GB uint8 tensor copy rose from 10.2 GB/s with a normal PyTorch \`.to\(&quot;cuda&quot;\)\` call to 51.5 GB/s when the benchmark was run under \`cmt tune\`; the post links to the code and a technical write-up but reports no independent verification. The result comes from a single benchmark on one GPU model, so the claimed speedup is not yet established across other hardware, tensor sizes, or transfer patterns.

reddit · r/MachineLearning · /u/makneeee · Nov 15, 18:20

**「Background」** CUDA copies between host and device distinguish pageable memory, which the operating system may swap out and which the driver cannot hand directly to a DMA engine, from pinned \(page-locked\) memory, which can be transferred directly. Pageable cudaMemcpy calls are consequently staged through a driver-managed pinned buffer, so they generally run well below the bandwidth that pinned transfers reach on the same link. The tool in the post targets that pageable path on an NVIDIA B300, a Blackwell Ultra-generation data-center GPU with 288 GB of memory per device.

**「Impact」** Developers working with pageable host-to-device transfers on B300 can try the tuner and compare it against their existing copy path, but should validate the 5x claim on their own tensor sizes and workloads because the published example covers only a 1 GB uint8 CPU-to-GPU copy.

<details><summary>References</summary>
<ul>
<li><a href="https://clore.ai/rent-b300.html">Rent B 300 288GB from $4.77/hr | Per-Minute GPU | Clore.ai</a></li>
<li><a href="https://gpusmith.com/articles/en/nvidia-dgx-b300-price">NVIDIA DGX B 300 Price: Specs and Lead Times Guide | GPUSmith</a></li>

</ul>
</details>

**Tags**: `#CUDA`, `#GPU memory transfers`, `#performance optimization`, `#machine learning systems`, `#open source tools`

---

<a id="item-tech-news-7"></a>
### [Huawei Cloud launches openPangu-2.1-Pro on MaaS with token pricing](https://mp.weixin.qq.com/s/8JfFmscBTDl_mPQMycD8Nw) ⭐️ 7.0/10

Huawei Cloud has launched openPangu-2.1-Pro, which it describes as an open-source Pangu model, on its MaaS model-as-a-service platform for agent development and AI coding. The company says it used more than 100,000 specialized data records to optimize Skills triggering and tool calls, and adapted the model to HarmonyOS ArkTS development and Ascend operator generation, with integration into its AgentArts, CodeArts and OfficeAce products. MaaS pricing is 0.8 yuan per million input tokens, 3.2 yuan per million output tokens, and 0.016 yuan per million cached input tokens. The announcement did not disclose the model size, license terms or benchmark results.

telegram · zaihuapd · Nov 15, 16:03

**「Background」** The launch follows Huawei Cloud&\#x27;s November 1 notice that its MaaS platform would stop selling openPangu-2.0-Flash and openPangu-2.0-Pro on November 6, 2026, with Huawei saying new openPangu versions were planned. Before the MaaS listing, openPangu-2.1-Pro had already appeared in Huawei&\#x27;s Xiaoyi Work assistant, though Huawei had not published its parameter count, active parameters, context length, or training-data details.

**「Impact」** Developers using Huawei Cloud MaaS can call openPangu-2.1-Pro at the published per-token rates, allowing cost estimates for agent and coding workloads. Teams evaluating the model for open-source use cannot assess licensing from the announcement because no license terms were provided.

<details><summary>References</summary>
<ul>
<li><a href="https://www.163.com/dy/article/LAUGH8N10511B8LM.html">华 为 小艺Work率先上线 openPangu - 2 . 1 - Pro 模 型 ，主打“鸿蒙任务增强”</a></li>
<li><a href="https://www.d1ev.com/newsflash/315764">华 为 openPangu 两款 模 型 将停售 2 . 1 - Pro 已抢先上线小艺Work...</a></li>

</ul>
</details>

**Tags**: `#Huawei Pangu`, `#open-source LLM`, `#AI agents`, `#AI coding`, `#Huawei Cloud MaaS`

---

## Financial News

<a id="item-finance-news-1"></a>
### [Lutnick faces conflict-of-interest questions over sons&\#x27; firm and Nvidia](https://www.cnbc.com/2026/11/13/howard-lutnick-nvidia-jensen-huang-china-cantor-fitzgerald.html) ⭐️ 7.0/10

Commerce Secretary Howard Lutnick is facing conflict-of-interest questions after CNBC reported that Cantor Fitzgerald, the firm his sons now lead, cut its reported Nvidia share count by 49% between September 2025 and March 2026, to 1.78 million shares; Axios reporting cited by CNBC says Lutnick had received a classified warning about Nvidia CEO Jensen Huang&\#x27;s ties to a suspected Chinese spy and resisted a crackdown on suspected chip smuggling to China. CNBC found no evidence that Lutnick shared nonpublic information or that Cantor traded on warnings, and Cantor said its Nvidia positions were immaterial and tied to client swap transactions.

rss · CNBC Finance · Nov 15, 19:58

**「Background」** Howard Lutnick left Cantor Fitzgerald to become commerce secretary in February 2025, putting him atop the department responsible for imposing the entity list, a restricted-entities roster used in U.S. export controls on advanced AI chips to China.

**Tags**: `#Nvidia`, `#export controls`, `#conflict of interest`, `#Commerce Department`, `#China`

---

<a id="item-finance-news-2"></a>
### [美光、三星、SK海力士必须应诉DRAM价格操纵指控](https://www.tomshardware.com/tech-industry/big-tech/judge-denies-motion-to-dismiss-dram-price-fixing-lawsuit-against-micron-samsung-and-sk-hynix-says-chipmakers-acted-like-hawks-flying-in-formation-finds-evidence-of-dram-collusion-plausible-after-500-percent-price-surge) ⭐️ 7.0/10

一名美国联邦法官驳回了美光、三星和SK海力士提出的撤销动议，允许一宗DRAM集体诉讼继续审理，该诉讼指控这三家公司以类似编队飞行的方式协同行事。17名个人和小型企业原告称，这三家供应商在一年内四次并行限制DRAM供应，使价格最高上涨500%；该案现在进入证据开示阶段，而不是作出任何责任认定。

telegram · zaihuapd · Nov 15, 16:39

**「Background」** The suit is a proposed class action by indirect purchasers—buyers who did not buy directly from the chipmakers—in the Northern District of California; the ruling lets their claims proceed and is not a finding that the companies broke the law.

<details><summary>References</summary>
<ul>
<li><a href="https://www.techpowerup.com/354863/samsung-sk-hynix-and-micron-fail-to-get-dram-antitrust-suit-dismissed">Samsung , SK hynix , and Micron Fail to Get DRAM Antitrust Suit ...</a></li>
<li><a href="https://litnews.ai/articles/garciaguirre-samsung-sk-hynix-micron-dram-conspiracy-suit-survives-dismissal">Judge Refuses to Dismiss DRAM Supply Conspiracy Suit Against...</a></li>

</ul>
</details>

**Tags**: `#antitrust litigation`, `#DRAM`, `#semiconductor supply`, `#price fixing`, `#memory chips`

---

<a id="item-finance-news-3"></a>
### [US, China, Russia leaders to hold first trilateral meeting at Shenzhen APEC](https://apnews.com/article/trump-xi-putin-summit-china-5fe92253ef38100bae913834a9b74d72) ⭐️ 7.0/10

China&\#x27;s Foreign Ministry said the US, Chinese and Russian leaders will meet on November 19 on the sidelines of the APEC summit in Shenzhen, in what media described as their first dedicated trilateral meeting. The meeting is not part of APEC&\#x27;s official agenda.

telegram · zaihuapd · Nov 16, 01:38

**「Background」** The 2026 APEC Economic Leaders’ Meeting is scheduled for Nov. 18–19 in Shenzhen—China’s third time hosting APEC and its first in 12 years, according to the Chinese government.

<details><summary>References</summary>
<ul>
<li><a href="https://english.www.gov.cn/news/202609/10/content_WS6aa2b5d7c6d00ca5f9a0d1fa.html">APEC CEO Summit 2026 to be held in Shenzhen from Nov. 17 to 18</a></li>

</ul>
</details>

**Tags**: `#geopolitics`, `#US-China-Russia`, `#APEC`, `#diplomacy`, `#market-risk`

---