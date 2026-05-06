# Deep dive: Toddle — IB-native LMS, dual-cloud AI, India-headquartered

_Filed 6 May 2026._

> **Lede:** Toddle is the IB-native LMS that has spent the last eighteen months trying to convince schools it's also a serious AI platform — five Demo Days in fifteen months, AI grading on by default in 2025, conversational analytics in November 2025, and five "AI-powered learning interfaces" announced in February 2026 — and so far the architecture story is genuinely interesting and the user-experience story is genuinely mixed. Compared to the Canvas multi-vendor architecture filed earlier today, Toddle's AI plumbing is *more* private-by-construction (PII never leaves Toddle's trust boundary) and *less* swappable (single vendor, single product, no LTI agent layer). Whether that's the right trade for an international school is exactly the question.

## What Toddle is

Toddle is a teaching-and-learning platform built **for the IB continuum first** and adapted for non-IB schools later. Headquarters: Bengaluru, India. Founders: Deepanshu Arora (CEO, ex-McKinsey, IIT Kanpur), Nikhil Poonawala (CTO), Gautam Arora (CDO), Misbah Jafary (COO), Parita Parekh — five-co-founder team, founded 2019, product launched March 2021. The company also runs **Toddler's Den**, a 10-school Reggio-inspired preschool network in India that pre-dates the SaaS business — the founders were running schools before they were running a software company, which is a rarer profile in this market than it sounds. ([Toddle company profile PDF](https://cloud.toddleapp.com/assets/toddleapp.com/internship/About_Toddle_Company_Profile_and_Overview.pdf); [ASU GSV speaker bio](https://asugsvsummit.com/speakers/deepanshu-arora); [Crunchbase](https://www.crunchbase.com/person/deepanshu-arora))

Customer base, vendor-stated:
- **2,500+ schools across 100+ countries** as of the 2026 marketing cycle, up from "2,000+" through 2025. ([Toddle homepage](https://www.toddleapp.com/))
- **40,000+ educators across 1,500+ schools** per FOBISIA's affiliate listing. ([FOBISIA](https://www.fobisia.org/our-members/affiliate-members/toddle))
- **20,000+ PYP educators across 1,000+ PYP schools** — the IB-PYP base is the marquee. ([Toddle MYP page](https://www.toddleapp.com/ib-myp/))
- "1 in every 3 MYP schools" globally as of September 2022 (vendor-stated, not independently verified). ([Toddle MYP page](https://www.toddleapp.com/ib-myp/))
- **FOBISIA affiliate member**, the federation of British international schools in Asia — the closest thing Toddle has to a peer-school stamp in the international-school market in Asia. ([FOBISIA](https://www.fobisia.org/our-members/affiliate-members/toddle))

The competitor Toddle is most often compared against in the IB world is **ManageBac** (Faria Education Group, ~3,000 IB World Schools served). Toddle has been actively winning takeaways from Schoology and from Google Classroom + ManageBac stacks — Castilleja School (California, K-12 girls' independent) replaced 10 years of Schoology with Toddle in August 2024, after PowerSchool's acquisition of Schoology shifted the product towards larger districts. ([Castilleja Counterpoint](https://castillejacounterpoint.com/3561/news/castilleja-replaces-schoology-with-toddle-as-lms/); [ManageBac homepage](https://www.managebac.com/)) Western Academy of Beijing publicly migrated *three* platforms across PYP/MYP/DP onto Toddle. ([Toddle case study](https://www.toddleapp.com/learn/blog-post/how-western-academy-of-beijing-replaced-three-tech-platforms-with-toddle/)) AISB (American International School of Bucharest) consolidated from Google Classroom + ManageBac onto Toddle — and that one didn't go smoothly; see sceptic's corner.

## What changed in the last twelve months

Toddle has been shipping at Demo-Day pace — five "Demo Day" releases in fifteen months. The product is clearly the most active surface in the IB-LMS market right now. In order:

1. **Demo Day #3.0 (Dec 2024) — AI Tutors launched.** Conversational tutor surfaces inside the LMS. ([Demo Day #3.0](https://www.toddleapp.com/toddle-demo-day-december-2024/))
2. **Demo Day 4.0 (Mar 2025) — "world's most powerful AI suite for education".** AI Curriculum Design Assistant; AI-assisted Grading; worksheet generator. The "AI grading" rollout is the one that drew the most outside attention — see Common Sense Media note below. ([Demo Day 4.0](https://www.toddleapp.com/toddle-demo-day-march-2025/); [Bespoke Learning recap](https://bespokelearning.io/blog/future-assessment-ai-assisted-grading-toddle))
3. **Demo Day 5.0 (Nov 2025) — AI Insights.** Conversational data-analytics layer over school data: teachers "talk to their data" — ask questions like "which Year 9 students slipped on Criterion C this term?" — and the system answers in natural language with cited sources. **Critically: PII stays inside Toddle's trust boundary; never sent to third-party LLMs.** When the model can't answer, vendor description says it "says so plainly." ([Demo Day 5.0](https://www.toddleapp.com/toddle-demo-day-november-2025/))
4. **Demo Day 6.0 (Feb 2026) — five AI-powered learning interfaces.** This is the headline feature of 2026 so far. Five distinct student-facing AI surfaces inside Toddle: ([Demo Day 6.0](https://www.toddleapp.com/toddle-demo-day-february-2026/))
   - **Whiteboard** — AI follows students drawing/annotating, prompts them to clarify labels and connections in real time.
   - **Video Explorer** — AI pauses video at key moments, asks comprehension questions, "nudges thinking forward."
   - **Code Editor** — pair-programming-style AI that flags issues early and asks Socratic questions as students write code.
   - **Speaking Practice Tool** — language-practice surface with feedback on pronunciation, diction, fluency.
   - **Document Editor** — Socratic critic mode for student writing.
   - All five marketed as operating "in a teacher-controlled, safe environment."
5. **Demo Day 7.0 (Apr 2026) — 40+ new capabilities.** The biggest single drop. Highlights: course planning + timetabling unified into one calendar view; **public curriculum websites** schools can publish for parents, accreditation bodies, boards (always-current, auto-generated from Toddle); **external-assessment ingestion** for NAPLAN, PAT, MAP, etc., into a unified tracking and reporting layer; expanded SIS sync depth; daily-timetable-changes manageable in-app. ([Demo Day 7.0](https://www.toddleapp.com/toddle-demo-day-april-2026/))

A separate "Toddle × Microsoft" track shipped through 2025–2026: integrated Teams calls scheduled from Toddle Calendar, OneDrive/SharePoint file pickers inside Toddle assignments, Outlook calendar sync. ([Toddle × Microsoft](https://www.toddleapp.com/toddle-x-microsoft/))

## The AI architecture — and how it differs from Canvas

This is the part worth reading carefully if Canvas is the reference point. The Canvas deep dive filed earlier today described a **multi-vendor architecture stitched along open standards** (LTI, MCP, BYO-LLM-key) with the trade-off that the LMS itself runs the orchestration. Toddle has gone the **opposite direction on swappability** and the **same direction on data isolation**, with a different cloud topology.

What Toddle's Trust Vault states (vendor-stated; sources below):

| Surface | Model layer | How it's plumbed |
|---|---|---|
| Most AI features | **Anthropic Claude via AWS Bedrock** | Inside Toddle's own AWS account. Bedrock is the access layer; data stays inside Toddle's AWS perimeter. |
| Some AI features | **OpenAI models via Azure OpenAI Service** | Inside Toddle's Azure perimeter. Vendor states "no data or requests are sent to OpenAI's servers." |
| AI Insights (data-analytics layer) | **Self-hosted LLMs inside Toddle's trust boundary** | PII never reaches external LLMs at all. |
| Third-party LLM interactions generally | Vendor states **all interactions are pseudonymised** before leaving Toddle's perimeter. | Names, IDs, etc., replaced with tokens before any external call. |

([Toddle Third-Party Service Providers](https://www.toddleapp.com/3rdparty/); [Trust Vault](https://trust.toddleapp.com/); [Privacy Center](https://www.toddleapp.com/privacy-center/); [Privacy Policy](https://www.toddleapp.com/privacy-policy/))

Common Sense Media confirmed the encryption-and-anonymisation posture in their AI rating: *"all interactions between Toddle and the large language models (LLMs) that power Toddle AI are fully encrypted and anonymized, which provides strong protection against personally identifiable information (PII) being shared with third parties."* Toddle AI received a **"Pass Full"** privacy rating — Common Sense Media's top tier — meaning it cleared their minimum bar. ([Common Sense Media — Toddle AI rating](https://www.commonsensemedia.org/ai-ratings/toddle); [Common Sense Privacy Evaluation](https://privacy.commonsense.org/evaluation/Toddle-AI))

**The structural contrast with Canvas, in two sentences.** Canvas has *three named external AI providers* exposed through *three distinct seams* (LTI, MCP, BYO-key) and lets the institution choose at each seam. Toddle has *the same two underlying providers as Canvas* (Anthropic Claude, OpenAI models) but they're **plumbed inside Toddle's own cloud accounts**, the school doesn't choose, and there's no LTI-equivalent for swapping the Toddle AI surface for a different vendor's tutor. Toddle's bet is that **stricter data isolation by default** is more valuable to international schools than **provider-swappability at the seams**. Whether that bet is right depends on what a procurement office is actually trying to optimise for.

The Canvas-style "what surface, what provider" matrix doesn't really fit Toddle, because **all the AI surfaces are Toddle products with Toddle UX**. The closest you can get to a separation is: (a) AI Insights = self-hosted, never external; (b) student-facing learning interfaces and AI grading = Bedrock-Claude or Azure-OpenAI under the hood, pseudonymised. There's no equivalent of Canvas's "the institution brings its own LLM key" lever.

## Security & compliance posture

Strong on paper, with the caveat that the May 2026 Instructure breach has reset the bar for what "strong" means.

- **SOC 2 Type II** completed. ([Privacy Center](https://www.toddleapp.com/privacy-center/))
- **ISO/IEC 27001** certified. ([Privacy Center](https://www.toddleapp.com/privacy-center/))
- **ISO/IEC 27701** certified — the privacy-information-management extension to 27001. This is rarer in the LMS market than 27001-only and worth flagging. ([Privacy Center](https://www.toddleapp.com/privacy-center/))
- **iKeepSafe FERPA + COPPA** certifications.
- **1EdTech TrustEd Apps™ Data Privacy** certification. ([Privacy Center](https://www.toddleapp.com/privacy-center/))
- **ST4S badge** (Australian state-school AI vetting framework).
- **Australian Privacy Principles (APPs)** alignment. ([Toddle APPs page](https://www.toddleapp.com/australianprivacyprinciples/))
- **Encryption at rest and in transit**, AWS-hosted infrastructure.
- **Data residency options:** Ireland (EU), Sydney (Australia), Singapore (Singapore), Dubai (UAE), Northern Virginia (US), and a separately-isolated Mainland China region (the China region is firewalled from the global five for political/regulatory reasons; schools migrating into China data residency follow a documented process). ([Privacy Policy](https://www.toddleapp.com/privacy-policy/); [China data centre migration guide](https://help.toddleapp.com/en/articles/9531001-migration-guide-for-schools-moving-to-china-data-center))
- **Stated 99.9% uptime**, real-time backups. ([Toddle homepage](https://www.toddleapp.com/))
- **Breach disclosure policy:** notify affected school "without undue delay, consistent with applicable laws and Toddle's internal data-breach policy." ([Privacy Policy](https://www.toddleapp.com/privacy-policy/))

What's missing from public material that you'd want for an RFP:
- **Public penetration-testing summary** — not visible on the public Trust Vault preview; behind a portal request.
- **Vulnerability disclosure programme** — no public-facing programme/bug bounty surfaced in research.
- **Specific incident-response timelines** — the disclosure language is "without undue delay," not numerical (e.g. "within 72 hours").

**No publicly disclosed breaches were found in research.** That's the relevant headline against the Canvas backdrop. Instructure has now had two confirmed breaches in eight months (Sept 2025 and May 2026, the latter a 275M-user / 9,000-school ShinyHunters incident covered in the morning brief). Toddle's track record by contrast is clean as far as public disclosures go — the absence of evidence is not evidence of absence, but the contrast is meaningful in 2026.

For external assessment data ingestion (Demo Day 7.0 — NAPLAN, PAT, MAP into Toddle), the data-flow disclosure for that pipeline specifically would be a fair RFP question — the public material announces the capability without the data-handling detail.

## Financials and ownership

Worth attention. Toddle is **venture-funded but not at break-out scale**, and the 2025 round looks more like a bridge than a Series B.

- **Total funding to date: $29.6M across 8 rounds.** ([Tracxn](https://tracxn.com/d/companies/toddle/__3B33fAVQzPSpDqLVkMcONIlrJBQCSiOIjCF44VUYf88/funding-and-investors))
- **Series A — $17M, Feb 2023**, led by Sequoia Capital India (now Peak XV Partners), with Matrix Partners, Beenext, Better Capital, Tenacity Ventures, Trifecta. ([Inc42](https://inc42.com/buzz/edtech-startup-toddle-secures-17-mn-funding-from-sequoia-capital-others/); [Tenacity Ventures](https://www.tenacity.vc/news/teaching-tool-company-toddle-raises-17-million-in-funding-from-sequoia-matrix-others))
- **Most recent round — $6.06M on 24 January 2025.** Single named investor disclosed; classified as Series A extension on some trackers. **No Series B has been announced.** ([Tracxn](https://tracxn.com/d/companies/toddle/__3B33fAVQzPSpDqLVkMcONIlrJBQCSiOIjCF44VUYf88/funding-and-investors); [PitchBook](https://pitchbook.com/profiles/company/277907-41); [Clay](https://www.clay.com/dossier/toddle-funding))
- **Cap table (per Tracxn):** Funds 56.46%, founders 34.08%, ESOP pool 8.13%, angels 1.34%.
- **Employee count:** ~430-500 (Glassdoor / LinkedIn estimates, not vendor-confirmed).

What this means in plain English. **Edtech funding has been depressed for two years** — Crunchbase News tracks edtech funding stuck at multi-year lows. ([Crunchbase News](https://news.crunchbase.com/venture/edtech-funding-stays-low/)) A $6M round nearly two years after a $17M Series A, in a depressed funding climate, with the runway extending into a market where customers are evaluating LMS platforms aggressively — that's a profile to ask direct questions about, not a profile to panic about. The product velocity (five Demo Days in fifteen months) suggests the company is shipping hard, which is what you want to see during a stretched runway.

For an RFP, the question to put on the table directly: *"What's your runway and your path to operating-cash-flow positive, and if there's a gap, what's the bridge plan?"* You'd ask Instructure the same kind of question (they have public 10-Q filings; Toddle is private, so you ask), and Faria/ManageBac the same.

## Standards and integrations — the seams audit

Where the open-standards picture matters for swappability:

| Standard | Toddle support | Notes |
|---|---|---|
| **LTI 1.3** | Yes — for assignments and resources, as a *consumer*. | Schools can plug LTI-compliant tools *into* Toddle. The reverse direction (Toddle as an LTI-providable surface inside another LMS) is not the architecture. |
| **OneRoster** | SIS-roster sync supported via OneRoster-like flows; specific OneRoster 1.2 conformance not loudly stated. | Toddle's documented SIS integrations name Veracross, Blackbaud, PowerSchool, Sentral with roster, term grades, timetable, attendance sync. |
| **MCP / agent interop** | **No public MCP-style agent layer.** No "third-party agent plugs into Toddle's orchestration" story. | Different design choice from Canvas. |
| **BYO LLM key** | **No.** Models are vendor-chosen and routed through Toddle's own cloud accounts. | Trade-off for the data-isolation architecture. |
| **Data export / portability** | **3-notification, 60-day window** before deletion at contract end; up to 365-day "secure copy" retention; immediate-deletion option on request. | Documented; format specifics ("what does the export look like?") not loudly published. |
| **Google Workspace** | Deep — Drive picker, Calendar, SSO. | ([Toddle integrations](https://www.toddleapp.com/integrations/)) |
| **Microsoft 365** | Deep — Teams calls, OneDrive picker, Outlook sync, SharePoint. | ([Toddle × Microsoft](https://www.toddleapp.com/toddle-x-microsoft/)) |
| **Apple Schoolwork** | Not in the named-integration list. Not surfaced in research. | Worth asking directly if Apple Schoolwork is part of a school's daily workflow. |

**Read in plain language.** Toddle has *one* of the three Canvas seams (LTI as consumer for tools coming in), doesn't expose the other two (no agent-interop standard, no BYO-key), and trades that for a tighter cloud-and-data perimeter. If "swap-ready" is the procurement frame, Toddle scores lower than 2026 Canvas. If "data stays in our vendor's perimeter, full stop" is the procurement frame, Toddle scores higher.

## Sceptic's corner

Three things to keep firmly in view.

**1. The AISB student-paper takedown is the most-honest negative review on the public record.** *The Bite*, the student paper at the American International School of Bucharest, published *"Switching to Toddle: A Change that Missed the Mark"* documenting AISB's transition off Google Classroom + ManageBac onto Toddle. Their survey of 46 student respondents found over 75% reported parents were *only slightly satisfied or not satisfied at all*. Quotes from AISB's own teachers (cited in the article) include that Toddle takes *"double the clicks and the time to create something that used to be done fairly easily in Google Classroom."* Specific student/parent complaints catalogued: deadlines that can't be extended on summative tasks; difficulty knowing how to add feedback and post grades; classroom-time wasted hunting for tasks; parent inboxes flooded by notification-forwarding. AISB's Secondary Principal is quoted defending the consolidation logic. ([The Bite — Switching to Toddle: A Change that Missed the Mark](https://thebite.aisb.ro/switching-to-toddle-a-change-that-missed-the-mark/); follow-up [Lord of the Screens: One Toddle to Rule them All](https://thebite.aisb.ro/lord-of-the-screens-one-toddle-to-rule-them-all/)) Whatever you think of the methodology, it's a peer-school international school's student paper — voiced by the actual users — and the criticisms cluster around UX complexity and notification volume. Both are addressable, but they're worth weighing against the vendor's product-velocity story. Demo Day 7.0's "calendar view, daily-timetable changes in-app" features look directly aimed at this kind of feedback, but whether the underlying complexity-tax is fixed is an open question that user research at peer schools would answer.

**2. The Common Sense Media "Pass Full" privacy rating is paired with explicit teacher-attention warnings.** Common Sense applauded the encryption-and-anonymisation posture, but the same review notes: *"Toddle AI is a generative AI teaching assistant that lacks transparency. Teachers should pay careful attention to their AI-assisted work, especially as it relates to student progress reporting, which can impact grades and assessment. If Toddle AI generates progress reports that draw inferences and conclusions from otherwise incomplete information, this could be harmful to student success, confidence, and mental health."* They also flag: *"features for instructing educators about AI and its limitations are not currently available, and this is concerning given that Toddle AI is now available to all schools that use the Toddle platform."* Translation: privacy posture is good, **AI-literacy scaffolding shipped with the product is thin**. ([Common Sense Media review](https://www.commonsensemedia.org/ai-ratings/toddle))

**3. AI-grading is the surface that gets the most independent challenge.** Toddle's AI grading is teacher-review-required (output visible only to the teacher, who must approve before sharing) — that's the safety design. But the broader literature on AI grading (Marc Watkins, Fordham Institute, etc.) is steadily more sceptical: bias risk, opacity, the displacement of teacher judgement under time-pressure. ([Marc Watkins — Dangers of using AI to grade](https://marcwatkins.substack.com/p/the-dangers-of-using-ai-to-grade); [Fordham Institute — Human stakes of AI grading](https://fordhaminstitute.org/national/commentary/human-stakes-ai-grading)) Common Sense Media's own framing is direct: *"It is critical for teachers to assess all output from Toddle AI for unfair bias and risk of harm. At the time of writing, Toddle AI has not discussed if or how the company approaches risk management and fairness in their AI development."* The teacher-review-required gate is good design; what's missing is the published bias-audit / fairness-evaluation programme behind the gate. An RFP question worth putting in writing: *"Show me the bias-and-fairness evaluation methodology for AI grading and AI feedback, the evaluation results, and the cadence of re-evaluation."*

A quieter fourth: **the AI-progress-report use case is the highest-stakes, lowest-instrumented surface.** When AI summarises a student's term across multiple data points and surfaces that to families, the inference space is wide and the consequences are real. Watch this surface specifically; ask harder questions there than at the worksheet-generator surface.

## What's not yet visible

A short, honest list of things worth knowing that the public material doesn't answer:

- **Per-student pricing.** Custom-quote model only; Capterra and SaaSWorthy list "tiered" with no published numbers. ([Capterra](https://www.capterra.com/p/251547/Toddle/))
- **Specific Series B status / runway disclosure.** The January 2025 round looks like a bridge; no public confirmation of a planned Series B.
- **Apple Schoolwork integration depth.** Not in the integration list; needs a direct ask if it matters to a school's daily Apple workflow.
- **Live-proctoring / lockdown-browser depth for high-stakes assessments.** Surfaced as a known gap in G2-aggregated user feedback. ([G2 reviews summary](https://www.g2.com/products/toddle/reviews))
- **AI-fairness evaluation methodology** specifically. See sceptic's corner.
- **Independent peer-reviewed evaluations.** As with Canvas, peer-reviewed studies of Toddle in real classrooms are essentially absent — most public material is vendor-curated or trade press.
- **Pen-test / vulnerability-disclosure programme.** Trust Vault portal access required.

## What it means for an international school evaluating LMS in 2026-27

A working summary, written in the same procurement frame the Canvas dive used.

**Where Toddle is genuinely strong.**
- IB-native — PYP, MYP, DP designed-in, not bolted-on. The 2025 PYP refresh is being supported in-product (event scheduled for May 16, 2026). For an IB-continuum school, this is a real procurement asset.
- Data isolation architecture — PII never leaves Toddle's cloud perimeter; AI Insights is fully self-hosted. Stronger by-construction than the Canvas seams-with-disclosure approach.
- Compliance stack — SOC 2 Type II, ISO 27001, ISO 27701, 1EdTech TrustEd Apps, iKeepSafe FERPA+COPPA — is competitive for any LMS in this market.
- No publicly disclosed breaches in the 24-month window — meaningful contrast with the Canvas track record.
- Product velocity — five Demo Days in fifteen months — means the gaps you'd find in a 2024 evaluation may close before contract start. Equally, this can be a disorientation tax on teachers.
- Multi-region data residency — including a politically isolated China region — matters for international schools with multi-jurisdiction parent data.

**Where Toddle is genuinely weaker than the 2026 Canvas reference.**
- Less swappable. No MCP-equivalent for agent interop; no BYO-LLM-key on student-facing AI; LTI 1.3 only as consumer. If you want to swap the AI tutor for a different vendor's later, you're swapping the whole platform.
- Smaller / privately-funded. $29.6M total raised; depressed funding climate; bridge-shaped 2025 round. Not a balance-sheet you can read like Instructure's public filings.
- AI-literacy-and-fairness scaffolding shipped with the product is thinner than the privacy posture would suggest. The teacher-review-required gate is necessary; published bias-audit is not yet there.
- UX-complexity tax is the most-cited negative in real-school user feedback. Demo Day 7.0 looks aimed at this; needs verification with peer schools that have lived the migration.

**Questions worth putting to Toddle by name in any RFP exchange.**
1. *Show me the AI architecture diagram by surface — which Toddle product calls Bedrock-Claude, which calls Azure-OpenAI, which is fully self-hosted, what data is pseudonymised before leaving the Toddle perimeter at each surface.*
2. *Bias-audit and fairness-evaluation methodology for AI grading and AI feedback — methodology, results, re-evaluation cadence.*
3. *Data-export format and completeness — gradebook export, AI-generated artefacts (rubrics, feedback comments, progress-report drafts), portfolio data — what's in the bundle at contract end?*
4. *Per-surface ability to disable AI from the admin console — student-facing tutor off, AI grading on, AI Insights on, AI-progress-reports off — is this granular, or is it bundled?*
5. *Penetration testing — most recent test date, summary of high/critical findings, remediation status.*
6. *Series B / runway disclosure — what's the bridge plan if a Series B doesn't close in 2026?*
7. *External-assessment-data pipeline (NAPLAN, PAT, MAP into Toddle) — data residency for that pipeline specifically, and the data-processing agreement layer.*
8. *AI-literacy resources shipped with the product for teachers and students — what's there, what's the cadence of refresh, what's the curriculum-coverage commitment?*
9. *Apple Schoolwork integration — depth, roadmap, and timeline if not present today.*
10. *IB academic-honesty layer — how Toddle's AI surfaces intersect with IB academic-integrity policy, especially at DP level for IA / EE work.*

**Where it sits against the 2026 Canvas reference architecture.** Two different bets, both defensible.

- Canvas (2026): *"We expose three named external AI providers along three open-standards seams; we let you swap; we run an orchestration layer; we just had two breaches in eight months."*
- Toddle (2026): *"We hide the AI providers behind our own cloud-and-data perimeter; we don't let you swap; we built a self-hosted analytics layer on top; we have a clean public breach record."*

Neither is universally better. Which one a school should prefer is a function of which property — *standards-based swappability* or *vendor-perimeter data isolation* — best matches that school's risk model, IT capacity to manage multi-vendor surfaces, and IB-curriculum specificity. For an IB-continuum international school, Toddle's by-construction data isolation is a real asset and the IB-native design is a real asset; the sceptic-corner items are real costs. The procurement question worth answering before reading vendor decks is which axis the school is actually optimising for.

## Sources

Toddle primary
- [Toddle homepage](https://www.toddleapp.com/)
- [Toddle product overview](https://www.toddleapp.com/product/product-overview/)
- [Toddle company profile PDF (corporate overview)](https://cloud.toddleapp.com/assets/toddleapp.com/internship/About_Toddle_Company_Profile_and_Overview.pdf)
- [Demo Day #3.0 — AI Tutors (Dec 2024)](https://www.toddleapp.com/toddle-demo-day-december-2024/)
- [Demo Day 4.0 — AI suite (Mar 2025)](https://www.toddleapp.com/toddle-demo-day-march-2025/)
- [Demo Day 5.0 — AI Insights (Nov 2025)](https://www.toddleapp.com/toddle-demo-day-november-2025/)
- [Demo Day 6.0 — five AI-powered learning interfaces (Feb 2026)](https://www.toddleapp.com/toddle-demo-day-february-2026/)
- [Demo Day 7.0 — 40+ capabilities (Apr 2026)](https://www.toddleapp.com/toddle-demo-day-april-2026/)
- [What's New at Toddle](https://www.toddleapp.com/whats-new/)
- [Toddle AI feature page](https://www.toddleapp.com/ai/)
- [Toddle × Microsoft](https://www.toddleapp.com/toddle-x-microsoft/)
- [Toddle integrations (50+ tools)](https://www.toddleapp.com/integrations/)
- [Toddle IB-MYP page](https://www.toddleapp.com/ib-myp/)
- [Toddle IB-PYP page](https://www.toddleapp.com/ib-pyp/)
- [Toddle IB-DP page](https://www.toddleapp.com/ib-dp/)
- [Toddle IB-continuum schools page](https://www.toddleapp.com/ib-continuum/)
- [Toddle pricing page](https://www.toddleapp.com/pricing/)

Trust, privacy, security
- [Toddle Privacy Center](https://www.toddleapp.com/privacy-center/)
- [Toddle Privacy Policy](https://www.toddleapp.com/privacy-policy/)
- [Toddle GDPR page](https://www.toddleapp.com/gdpr/)
- [Toddle Australian Privacy Principles](https://www.toddleapp.com/australianprivacyprinciples/)
- [Toddle Third-Party Service Providers](https://www.toddleapp.com/3rdparty/)
- [Toddle Trust Vault](https://trust.toddleapp.com/)
- [Toddle privacy policy overview (Help Center)](https://support.toddleapp.com/en/articles/8612535-our-privacy-policy)
- [Toddle China data centre migration guide](https://help.toddleapp.com/en/articles/9531001-migration-guide-for-schools-moving-to-china-data-center)

Independent / case study
- [Common Sense Media — Toddle AI rating](https://www.commonsensemedia.org/ai-ratings/toddle)
- [Common Sense Privacy Evaluation — Toddle AI](https://privacy.commonsense.org/evaluation/Toddle-AI)
- [The Bite (AISB Bucharest student paper) — Switching to Toddle: A Change that Missed the Mark](https://thebite.aisb.ro/switching-to-toddle-a-change-that-missed-the-mark/)
- [The Bite — Lord of the Screens: One Toddle to Rule them All](https://thebite.aisb.ro/lord-of-the-screens-one-toddle-to-rule-them-all/)
- [Castilleja Counterpoint — Castilleja replaces Schoology with Toddle](https://castillejacounterpoint.com/3561/news/castilleja-replaces-schoology-with-toddle-as-lms/)
- [Toddle case study — Western Academy of Beijing replaces three platforms with Toddle](https://www.toddleapp.com/learn/blog-post/how-western-academy-of-beijing-replaced-three-tech-platforms-with-toddle/)
- [Toddle case study — GEMS International School Al Khail](https://www.toddleapp.com/learn/case-study/how-switching-from-google-to-toddle-changed-the-perception-of-curriculum-planning-at-gems-international/)
- [FOBISIA affiliate listing — Toddle](https://www.fobisia.org/our-members/affiliate-members/toddle)

Funding / company / leadership
- [Inc42 — Toddle Series A $17M (Sequoia + others)](https://inc42.com/buzz/edtech-startup-toddle-secures-17-mn-funding-from-sequoia-capital-others/)
- [Tenacity Ventures — Toddle $17M Sequoia/Matrix Series A](https://www.tenacity.vc/news/teaching-tool-company-toddle-raises-17-million-in-funding-from-sequoia-matrix-others)
- [Tracxn — Toddle funding rounds and investors](https://tracxn.com/d/companies/toddle/__3B33fAVQzPSpDqLVkMcONIlrJBQCSiOIjCF44VUYf88/funding-and-investors)
- [PitchBook — Toddle profile](https://pitchbook.com/profiles/company/277907-41)
- [Clay — Toddle funding dossier](https://www.clay.com/dossier/toddle-funding)
- [Crunchbase — Deepanshu Arora](https://www.crunchbase.com/person/deepanshu-arora)
- [ASU GSV — Deepanshu Arora speaker bio](https://asugsvsummit.com/speakers/deepanshu-arora)
- [Crunchbase Toddle company profile](https://www.crunchbase.com/organization/toddle-8e3e)
- [Crunchbase News — edtech funding stays low](https://news.crunchbase.com/venture/edtech-funding-stays-low/)

AI-grading and analysis context
- [Bespoke Learning — AI-Assisted Grading: Future of Assessment, Toddle 4.0](https://bespokelearning.io/blog/future-assessment-ai-assisted-grading-toddle)
- [Marc Watkins — The Dangers of using AI to Grade](https://marcwatkins.substack.com/p/the-dangers-of-using-ai-to-grade)
- [Fordham Institute — The human stakes of AI grading](https://fordhaminstitute.org/national/commentary/human-stakes-ai-grading)
- [Toddle AI grading FAQs](https://help.toddleapp.com/en/articles/11958919-faqs-for-ai-grading)

Comparison context
- [ManageBac homepage (Faria Education Group)](https://www.managebac.com/)
- [G2 — Toddle reviews](https://www.g2.com/products/toddle/reviews)
- [Capterra — Toddle](https://www.capterra.com/p/251547/Toddle/)

Status / monitoring
- [StatusGator — Toddle status monitoring](https://statusgator.com/services/toddle)
