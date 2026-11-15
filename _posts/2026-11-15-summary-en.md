---
layout: default
title: "Horizon Summary: 2026-11-15 (EN)"
date: 2026-11-15
lang: en
---

> From 39 items, 7 important content pieces were selected

---

**Technology News**
1. [SpaceX reportedly catches Starship to end Flight 15](#item-tech-news-1) ⭐️ 9.0/10
2. [Lovable-built apps exposed passport data and 200K messages through weak RLS](#item-tech-news-2) ⭐️ 8.0/10
3. [OpenAI Reportedly Disbands Robotics Team as General Models Control Robots](#item-tech-news-3) ⭐️ 7.0/10
4. [Cloudflare open-sources Kitesurf, a stateless browser for AI agents](#item-tech-news-4) ⭐️ 7.0/10
5. [Italy fines Meta €805 million over Facebook Android gallery access](#item-tech-news-5) ⭐️ 7.0/10
6. [FAA ground stop traced to router failure after copper-to-fiber upgrade](#item-tech-news-6) ⭐️ 7.0/10

**Financial News**
1. [Nvidia CEO exit and a Democratic Congress seen reshaping the AI trade, ETF experts say](#item-finance-news-1) ⭐️ 7.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [SpaceX reportedly catches Starship to end Flight 15](https://www.spacex.com/launches/starship-flight-15) ⭐️ 9.0/10

SpaceX&\#x27;s Flight 15 reportedly ended with the Starship upper stage caught by the launch tower, according to the submitted item. The claim is presented through SpaceX&\#x27;s X post and a YouTube link rather than a detailed technical report, and no independent confirmation, reflight schedule, or payload details were included. The discussion treats the catch as progress toward fully reusable launch hardware rather than a completed operational capability.

hackernews · ls612 · Nov 14, 21:22 · [Discussion](https://news.ycombinator.com/item?id=50500963)

**「Background」** Flight 15 was SpaceX&\#x27;s 15th Starship test flight and the first to attempt catching the Ship upper stage with the launch tower&\#x27;s chopsticks. Earlier flights had successfully caught the Super Heavy booster on three test flights, but not the Ship itself.

**「Impact」** If confirmed, the recovery would give SpaceX a returned Starship available for post-flight inspection, a prerequisite for testing reflight. Commenters identify re-flying the same vehicle and catching both stages as the next milestones.

**「Community Discussion」** Commenters compared the architecture to the Space Shuttle, arguing that a reusable booster without solid boosters and a stack mounted on top avoids the configurations blamed for the Challenger and Columbia disasters. Others said the heat shield and eventual reflight, including a double catch, will determine whether the catch translates into cheaper orbital payloads, while one commenter questioned the final mass fraction to orbit.

<details><summary>References</summary>
<ul>
<li><a href="https://www.space.com/space-exploration/launches-spacecraft/spacex-says-starship-flight-15-booster-aborted-chopsticks-landing-catch-after-launch-due-to-guidance-issue-video">SpaceX still investigating why Starship Flight 15 booster... | Space</a></li>
<li><a href="https://www.cnn.com/2026/11/13/science/live-news/spacex-starship-flight-15-ship-catch">Live updates: SpaceX Starship nails historic ship catch in... | CNN</a></li>

</ul>
</details>

**Tags**: `#SpaceX`, `#Starship`, `#reusable launch`, `#spaceflight`, `#hardware engineering`

---

<a id="item-tech-news-2"></a>
### [Lovable-built apps exposed passport data and 200K messages through weak RLS](https://www.crissyfield.de/research/lovable-en/) ⭐️ 8.0/10

A security research post reports that apps built with Lovable exposed passport details and more than 200,000 private messages because of insufficient Row-Level Security. Lovable&\#x27;s head of security, posting as igorandri, confirmed in the discussion that insufficient RLS was the root cause and said Lovable scans every app automatically before publish, offers a deeper SAST scan free to all users, and lets users apply fixes, enable auto-fix, or block publishing when findings are flagged.

hackernews · armcat · Nov 14, 17:43 · [Discussion](https://news.ycombinator.com/item?id=50499017)

**「Background」** Row-Level Security \(RLS\) is PostgreSQL&\#x27;s row-by-row access-control mechanism, and Supabase exposes Postgres tables through an auto-generated Data API that client libraries call directly. Supabase historically exposed new tables in the public schema through that API by default, leaving RLS policies as the main guardrail; on October 30, 2026 it changed that default so new public-schema tables are not automatically exposed, a transition that can break apps relying on the old behavior. The Lovable apps at issue still depend on each project&\#x27;s RLS configuration.

**「Impact」** Developers using Lovable should verify RLS policies on their Supabase-backed apps; the reported exposure included passport details and private messages, showing the kind of user data at risk. Lovable says its pre-publish scan and optional SAST scan flag RLS problems and can auto-fix them.

**「Community Discussion」** Commenters focused on systemic responsibility: one argued that Supabase&\#x27;s permissive RLS defaults, chosen years ago to reduce onboarding friction, are a major cause, and said reports suggest an October 30 fix may not cover existing projects; another called for deny-by-default databases and automated auth tests for AI-generated apps. The post&\#x27;s author described the situation as fairly self-explanatory, while Lovable&\#x27;s security lead pointed to automatic pre-publish scanning and remediation tools rather than disputing the RLS root cause.

<details><summary>References</summary>
<ul>
<li><a href="https://supabase.com/docs/guides/database/postgres/row-level-security">Row Level Security - Supabase Docs</a></li>
<li><a href="https://dev.to/dave_thomas_18311ddb9c409/supabases-oct-30-change-what-breaks-what-doesnt-and-the-quick-fix-to-avoid-bg4">Supabase&#x27;s Oct 30 change: what breaks, what doesn&#x27;t, and the ...</a></li>
<li><a href="https://dev.to/cekuu35/supabase-permission-denied-after-october-30-the-exact-fix-copy-paste-sql-4d45">Supabase &quot;permission denied&quot; After October 30: The Exact Fix ...</a></li>

</ul>
</details>

**Tags**: `#security`, `#Supabase`, `#Row-Level Security`, `#AI app builders`, `#data exposure`

---

<a id="item-tech-news-3"></a>
### [OpenAI Reportedly Disbands Robotics Team as General Models Control Robots](https://fortune.com/2026/11/13/openai-disbands-robotics-team-as-its-general-models-start-running-robots/) ⭐️ 7.0/10

OpenAI has reportedly disbanded its independent robotics team and reassigned researchers to broader research groups, according to a brief Telegram summary of a Fortune report. The company reportedly says robotics remains central to its long-term vision, but that general frontier models such as GPT-6 Astra can directly control robots, making a dedicated team unnecessary. The post says OpenAI is still developing a humanoid robot, with its CEO targeting a first public demonstration in 2027, after an earlier robotics team was disbanded in 2020 and a 2024 partnership with Figure ended in February 2025. It gives no technical detail on how Astra operates robots or whether that capability is shipped or available to external developers.

telegram · zaihuapd · Nov 14, 04:00

**「Background」** OpenAI previously disbanded a robotics team in 2020 and rebuilt one in 2024; its subsequent collaboration with Figure ended in February 2025. The latest reorganization therefore returns robotics oversight to general research groups, consistent with OpenAI’s earlier shifts rather than a first-time exit from the field.

**Tags**: `#OpenAI`, `#robotics`, `#humanoid robots`, `#general-purpose models`, `#industry news`

---

<a id="item-tech-news-4"></a>
### [Cloudflare open-sources Kitesurf, a stateless browser for AI agents](https://www.phoronix.com/news/Cloudflare-Kitesurf-Open-Source) ⭐️ 7.0/10

Cloudflare has open-sourced Kitesurf, a stateless browser for AI agents, under the Apache 2.0 license. Built on Cloudflare Workers, it is designed to parse HTML, process CSS and execute JavaScript without requiring a browser container. Cloudflare says it uses less CPU and memory than Chromium and can scale on demand across its Workers network; the code is published on GitHub. No independent benchmarks, architecture details or version information were provided in the source.

telegram · zaihuapd · Nov 14, 09:33

**「Background」** Agent browser automation has generally relied on running a full Chromium-based headless browser alongside the agent, which is the heavier baseline the source compares Kitesurf against. Cloudflare describes Kitesurf as an experimental browser engine that renders pages inside V8 isolates on Workers with no Chromium underneath, and a third-party write-up says it is written mostly in Rust compiled to WebAssembly \(tool-2-1, tool-2-3\). The project&\#x27;s repository adds a deployment prerequisite: it requires Cloudflare Dynamic Workers, which are part of the Workers Paid plan \(tool-2-2\).

**「Impact」** Developers targeting Cloudflare Workers can inspect and adopt an Apache-2.0 browser component without operating Chromium containers, but the source gives no compatibility details or measured performance, so teams should validate behavior for existing browser-automation workloads.

<details><summary>References</summary>
<ul>
<li><a href="https://blog.cloudflare.com/kitesurf-open-source/">Kitesurf is now open source | Cloudflare Blog</a></li>
<li><a href="https://github.com/cloudflare/kitesurf">GitHub - cloudflare / kitesurf : Kitesurf is an experimental browser ...</a></li>
<li><a href="https://www.eesel.ai/blog/cloudflare-kitesurf">Cloudflare Kitesurf : the agent browser that trades speed... | eesel AI</a></li>

</ul>
</details>

**Tags**: `#Cloudflare`, `#AI agents`, `#browser automation`, `#open source`, `#Cloudflare Workers`

---

<a id="item-tech-news-5"></a>
### [Italy fines Meta €805 million over Facebook Android gallery access](https://www.garanteprivacy.it/home/docweb/-/docweb-display/docweb/10321080) ⭐️ 7.0/10

Italy’s privacy regulator, Garante Privacy, fined Meta €805 million after finding that Facebook’s Android app accessed the photos, videos and metadata of about 20 million Italian users without specific consent. The regulator tied the case to an album-recommendation feature launched in 2023 that was enabled by default and presented users with only a generic permission prompt. It ordered Meta to make the feature default-off and obtain separate consent within 60 days, or keep it disabled for users who have not validly authorized it.

telegram · zaihuapd · Nov 14, 14:37

**「Background」** The penalty concerns a photo-recommendation feature that Meta added to its Facebook Android app in 2023. According to the Garante, Italy&\#x27;s privacy regulator, the feature was switched on by default and relied on a broad authorization prompt rather than consent specific to that use of users&\#x27; albums.

**「Impact」** If Meta complies, Italian Facebook users will need to give explicit consent before the album-recommendation feature can use their photos, videos or metadata, and the feature must otherwise remain off by default.

**Tags**: `#privacy-regulation`, `#Meta`, `#Android-permissions`, `#consent`, `#Italy`

---

<a id="item-tech-news-6"></a>
### [FAA ground stop traced to router failure after copper-to-fiber upgrade](https://www.theverge.com/transportation/1033898/faa-ground-stop-sean-duffy-faa-copper-wire) ⭐️ 7.0/10

US Transportation Secretary Sean Duffy said on Nov. 14 that Friday’s nationwide FAA ground stop followed routine maintenance at a remote facility that replaced old copper wiring with fiber. A newly installed router then sent more than 1,000 connection requests every 4 to 5 seconds to other routers, disrupting radar signals and aircraft communications and grounding thousands of flights. Duffy said the root cause remains unclear and could be a hardware failure, a configuration error, or a mistake by contractor L3Harris.

telegram · zaihuapd · Nov 15, 02:10

**「Background」** The affected system is part of an FAA telecommunications network that the BBC described as decades old and CNBC reported is managed by contractor L3Harris Technologies. The copper-to-fiber work was therefore an upgrade to aging infrastructure rather than a new system rollout; Duffy said it was not yet known whether the fault lay in the equipment or the installation.

**「Impact」** Duffy used the incident to call for additional congressional funding for air-traffic-control modernization, linking the router failure to the agency’s aging infrastructure.

<details><summary>References</summary>
<ul>
<li><a href="https://www.nytimes.com/live/2026/11/14/us/faa-nationwide-ground-stop-flights">Thousands of Flights Are Canceled After Friday’s Nationwide Ground ...</a></li>
<li><a href="https://www.bbc.com/news/articles/cqx2wyvyr3zzo">What we know about the US ground stop and what to do if your flight...</a></li>
<li><a href="https://www.cnbc.com/2026/11/14/faa-ground-stop-flights-resume-delays.html">Ground stop followed contractor upgrade to L 3 Harris telecom system...</a></li>

</ul>
</details>

**Tags**: `#aviation infrastructure`, `#network outage`, `#router failure`, `#critical systems`, `#FAA`

---

## Financial News

<a id="item-finance-news-1"></a>
### [Nvidia CEO exit and a Democratic Congress seen reshaping the AI trade, ETF experts say](https://www.cnbc.com/2026/11/14/nvidia-ai-trade-data-centers-congress.html) ⭐️ 7.0/10

Nvidia founder and CEO Jensen Huang has resigned, and investing experts interviewed on CNBC&\#x27;s &quot;ETF Edge&quot; said Big Tech and other chipmakers such as AMD could pick up Nvidia&\#x27;s customers if trust in the company erodes. Yorkville Ives cut its Nvidia price target to $225 from $300 while keeping a buy rating; the stock ended the week at $162.85 a share, and AMD closed the week up nearly 13%.

rss · CNBC Finance · Nov 14, 15:50

**「Background」** Nvidia&\#x27;s longtime CEO Jensen Huang resigned in November 2026 over a scandal reported to involve alleged extramarital affairs, and CFO Colette Kress took over on an interim basis. Democrats also won control of Congress in the Nov. 3 elections, setting up the potential data-center pushback the ETF experts discussed.

**「Who is affected」** Chipmakers such as AMD and Broadcom could capture demand if buyers lose confidence in Nvidia, while the data-center buildout faces an estimated 10% to 20% shortfall in planned projects under a Democratic-controlled Congress, according to estimates from Yorkville Ives&\#x27; Dan Ives cited by CNBC.

<details><summary>References</summary>
<ul>
<li><a href="https://www.theguardian.com/technology/live/2026/nov/12/nvidia-ceo-jensen-huang-affairs-share-price-plunges-live-latest">Nvidia CEO Jensen Huang resigns over scandal and is replaced ...</a></li>
<li><a href="https://www.theguardian.com/technology/2026/nov/12/nvidia-ceo-jensen-huang-resigns">Jensen Huang resigns as Nvidia CEO after alleged affairs</a></li>
<li><a href="https://www.cnbc.com/2026/11/05/democrats-data-center-restrictions-midterms.html">Top Democrats call to rein in AI buildout after midterms sweep...</a></li>
<li><a href="https://www.forbes.com/sites/maryroeloffs/2026/11/05/compute-campuses-data-center-rebrand-kicks-off-big-techs-attempt-to-woo-democratic-congress/">Major AI Companies Rush To Rehabilitate Data Center Image After...</a></li>
<li><a href="https://foreignpolicy.com/2026/11/05/midterm-results-ai-data-centers-texas-georgia-ohio/">Midterm Results Reflect AI , Data Center Concerns</a></li>

</ul>
</details>

**Tags**: `#Nvidia`, `#AI trade`, `#ETFs`, `#semiconductor stocks`, `#US policy`

---