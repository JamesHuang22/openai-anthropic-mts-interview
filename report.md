# OpenAI & Anthropic — Member of Technical Staff (Software Engineer) Interview Process & Actual Questions, 2025–2026

**Prepared for:** Senior backend engineer — Amazon SDE II, 6 years distributed systems — targeting AI-engineer / MTS SWE roles
**Research date:** 22 October 2026 (PDT). Sources prioritised from 2025–2026; the freshest question-bank analyses are from October 2026.
**Method / confidence note:** Neither company publishes its full loop or question bank. Everything below is synthesised from candidate reports (Glassdoor, Blind, 1point3acres, Reddit as cited by guides), prep-platform guides built on those reports (IGotAnOffer, Hello Interview, interviewing.io via press coverage), and two October-2026 question-bank counts (Land the Lab: n=144 reported OpenAI questions, n=72 reported Anthropic questions). Labels used throughout:

- **CONFIRMED PATTERN** — multiple independent sources agree.
- **SINGLE / ANECDOTAL** — one report or one synthesis only; treat as possible, not expected.
- **CONFLICTING** — sources disagree; both versions are given.

> ⚠️ The single most important meta-finding: **both loops vary by team.** Every credible source says the same thing — ask your recruiter for your exact loop (rounds, format, AI policy, take-home vs live) in the first call. There is no single canonical loop at OpenAI ("decentralised"), and Anthropic loops vary by org (Research vs Applied/Product) and level.

---

## Summary — the 30-second version

| | OpenAI MTS SWE | Anthropic MTS SWE |
|---|---|---|
| Core identity of loop | Production-coding machine test | Build-and-extend coding + values veto |
| Coding style | Practical, high-volume, build-from-scratch in CoderPad, 3–5 growing parts; plus a **refactoring/debugging** round for seniors | **90-min CodeSignal** 4 progressive levels + live practical coding (crawler, dedupe, profiler traces) |
| AI in live rounds | No AI, **no autocomplete** (Oct 2026 reports); docs allowed | No AI by default (official candidate guidance); docs/search allowed. Application/prep use of Claude explicitly allowed since mid-2025 policy reversal |
| System design flavour | More classic/product-shaped (31/50 classic per Oct 2026 count) + AI-native (ChatGPT serving, vector DB, GPU scheduler) | More AI-infra-shaped (21/29 AI/ML per Oct 2026 count); **math-first**, written in a shared Google Doc; inference batching is the signature prompt |
| Hardest / most-failed round | Coding bar itself — reportedly no recovery from a weak coding score even if everything else is aced; refactoring round surprises seniors | **Culture / Values round — #1 rejection reason**, per recruiters and multiple guides; also team-matching can stall/reject after passing |
| ML depth for generalist SWE | Conceptual: KV cache, batching, streaming, token/rate-limit economics. From-scratch PyTorch only for ML/research MTS tracks | Conceptual + a dedicated **LLM & prompt-engineering round** in many loops: token management, rate limits, cost, multi-step LLM calls, failure modes |
| Timeline (reported range) | 2–8 weeks typical; fastest 3–4 weeks; referral-to-screen alone can take ~6 weeks | ~3–4 weeks when fast; 4 weeks–3+ months with team matching; references run *during*, not after |
| Level/team | Level (most external hires L4/L5) and team often decided **after** the loop; downlevelling reported | Team placement after the loop for broad postings; can wait 2–8 weeks in matching |

---

# PART I — OPENAI

## O1. Full interview loop structure

**CONFIRMED PATTERN (IGotAnOffer, updated 14 Oct 2026; Hello Interview; Glassdoor Oct 2026):**

1. **Resume screen** — extremely competitive. Emphasis on scale/impact, quantified results, systems work for infra teams.
2. **Recruiter call — 30–45 min.** Background, "Tell me about yourself / Walk me through your resume / Why OpenAI?" Also logistics, teams hiring, timeline. *Not purely administrative:* the October 2026 Land the Lab analysis says the recruiter call asks your view on AGI and AI safety and "a weak answer on AI safety can end the process there" — treat that as a real gate, prepare a safety view before this call. Source: https://medium.com/@landthelab/the-12-coding-questions-openai-keeps-asking-its-screen-bans-autocomplete-ce9011f08817
3. **Hiring manager screen — 20–30 min** (IGotAnOffer ordering; some loops put HM later / HM runs the final behavioral round — order varies by team). Background, career goals, technology relevant to the team, past systems and trade-offs; research/applied roles: deep dive on a research output/project.
4. **Skills-based assessment — one of three formats** (no single standard):
   - Live coding / pair coding on CoderPad or HackerRank (most commonly reported), *or*
   - A system-design screen (more likely for senior roles), *or*
   - A take-home via HackerRank / private repo (team-dependent; see O6).
   - **Variant reported Oct 2026 (multiple candidates + Land the Lab):** *two* 60-min screens — one coding, one system design — sometimes on the same day. One Glassdoor Oct 2026 candidate reported a single 90-min CoderPad session combining coding + a short design discussion.
5. **Final loop ("onsite", virtual by default, SF onsite optional) — 4–6 hours, 4–6 interviewers, over 1–2 days** (per OpenAI's own interview guide as cited by IGotAnOffer/Hello Interview):
   - Coding #2 (build-from-scratch, larger than the screen)
   - **Refactoring / debugging coding** (especially senior loops — see O2/O6)
   - System design (a second, deeper design round if you already had a design screen)
   - **Project presentation / retrospective** — 45 min in Oct 2026 reports: a few slides on 1–2 projects you led, then rapid probing on ownership, alternatives considered, and "what happens at 10× scale." Senior/staff candidates should expect this.
   - Behavioral with a senior/hiring manager (leadership, ownership)
   - Cross-functional / collaboration behavioral (in some loops)
6. **Decision, levelling, team matching — ~1 week, up to ~2 weeks.** Levelling and team matching happen *at the end*, not upfront; most external hires land L4 or L5, senior candidates calibrated L5/L6 (TrueInterview synthesis). References may be requested at decision stage (two, including a manager, per that synthesis). Downlevelling relative to prior title is commonly reported. Faster if you have a competing-offer deadline — tell the recruiter early.

**What each stage evaluates:** recruiter = motivation + safety/mission view + team fit; screen = independent practical coding (explicitly: a round is failed if the interviewer must give multiple substantive hints, per IGotAnOffer); design screen = concrete API + schema; onsite design = scaling, retries/idempotency, production correctness; project presentation = real ownership depth (strong coders reportedly fail by staying shallow); behavioral/HM = ownership, ambiguity, conflict, mission.

**Recent changes 2025–2026:**
- **No AI, no autocomplete in coding screen and onsite coding** — documentation allowed (Land the Lab, Oct 2026, n=144). Practice with autocomplete *off*.
- **SINGLE-SOURCE / EMERGING:** Some loops now include a beta **"agentic coding" round** — you use an AI coding agent on a codebase too large to handle by hand; the only round where AI use is explicitly allowed (SupaCV 2026 playbook: https://supacv.com/blog/interview-playbook/openai). One FDE-track report also described an AI-allowed coding round with screen-sharing + narration. Do not assume it; ask.
- Early-career candidates may get a timed online assessment before the screens (Land the Lab).

Sources: https://igotanoffer.com/en/advice/openai-software-engineer-interview · https://www.hellointerview.com/guides/openai/l4 · https://www.glassdoor.ie/Interview/OpenAI-Interview-E2210885-RVW93521232.htm (Oct 2026 report, via search index) · https://trueinterview.io/study/openai-interview-process

## O2. Coding interview questions

**Pattern — CONFIRMED across Hello Interview, IGotAnOffer, Glassdoor, Land the Lab:** Deliberate shift *away* from LeetCode. Problems are production-shaped, multi-part (3–5 growing parts), high code volume — "typing the whole time." Production quality counts: structure, naming, edge cases, **tests**. Python is the safest language (interviews mostly in Python; several candidates said C++ cost them time — TrueInterview). A finished, tested solution beats an unfinished clever one; in the screen, 2–3 parts done cleanly is the reported usual bar.

### O2a. The classic reported families (2024–2026, multiple sources)

| Problem | Description / follow-ups | Type |
|---|---|---|
| **Resumable iterator** | Implement iterator with `getState()/setState()` (or pause/resume); Part 1 for lists, then resumable JSON **file** iterator, then **multi-file** iterator handling empty files, then 2D/3D variants, async variant. TDD emphasis — write tests first. Also reported on 1point3acres. | Practical / state |
| **In-memory SQL / database** | Tables, INSERT / SELECT with WHERE, GROUP BY, ORDER BY, JOINs. Variant (Glassdoor, offer-accepted candidate): simple insert/select/delete **structured as an LSM tree — memtable + tombstones** instead of wiping records | Practical / build |
| **`cd` command** | `cd(current, target)` handling `.`, `..`, absolute paths; Part 2: `~`; Part 3: symlink dict — longest/more-specific match wins, detect symlink cycles (e.g. A→B→A, return null) | Practical / parsing |
| **Spreadsheet / Excel formula evaluator** | Cells referencing cells (`=A1+B2`), evaluate in dependency order, **detect circular references** | Graph dressed as product |
| **Key-value store family** | (i) Serialize/deserialize KV where keys/values contain any characters incl. delimiters → length-prefix encoding (Redis-protocol style). (ii) **Versioned / time-travel KV:** `put(k,v)`, `get(k)`, `get(k, timestamp)`. (iii) LRU cache `get/put` with eviction (the one classic LeetCode-style item that does recur) | Data structure |
| **Concurrent web crawler** | Multi-threaded crawl from seed URL, dedupe URLs, handle failures, rate limiting | Concurrency |
| **GPU credit / billing calculator & ledger** | Given GPU usage data + pricing rules, compute remaining credit; Oct 2026 variant: **GPU credit ledger with out-of-order events**, credits with different expiration/usage rules | Practical / stateful |
| **Scheduler** | Build a small scheduler *class*, interviewer keeps adding requirements until it is "a different problem" (Glassdoor Oct 2026). Also: design a task scheduler in Python (Aced/Exponent candidate report, Apr 2026) | Practical |
| Others in IGotAnOffer's Glassdoor/Blind list | Alien-dictionary character order; number of islands; topological sort + cycle detection; dependency version-constraint checker; simple ORM layer (save/query/update/delete); data-loader class + write its tests; fix a race condition and justify the synchronisation primitive; UI mockup implementation from provided CSS + data API (full-stack loops) | Mixed |

Source for table: https://www.hellointerview.com/blog/openai-coding-questions · https://igotanoffer.com/en/advice/openai-software-engineer-interview (§3.1) · https://www.linkjob.ai/interview-questions/openai-coding-interview/ (detailed resumable-iterator and `cd` part-by-part breakdowns)

> Note on generic lists: Some sites (e.g. codinginterview.com) list Two Sum, Valid Parentheses, Top-K Frequent, Kth Largest as "OpenAI questions." These appear to be generic LeetCode filler, **not** corroborated by the candidate-report-based sources above, which consistently say the opposite. Do not centre prep on them.

### O2b. Most-reported in Sept–Oct 2026 (Land the Lab count, n=84 coding questions; 10 of top 12 re-asked since 1 Sep 2026)

General SWE tier: memory allocator (`malloc`/`free` + coalescing); threshold infection spread on a grid; social follow graph with point-in-time snapshots; toy-language type inference (generics + tuples); count/map a cluster tree with message passing; turn-based monster team battle simulator; data-labelling scheduler with prefix-balanced models.
Next tier: **fault-tolerant work queue with leases and retries**; persistent KV store with binary snapshots; extensible chat app with command bots; three-card showdown; **IPv4 range iterator with reverse + CIDR support**; entropy from logits (stable, then streaming).
ML-flavoured items in the top 12 are covered in O4.
Source: https://medium.com/@landthelab/the-12-coding-questions-openai-keeps-asking-its-screen-bans-autocomplete-ce9011f08817 — *single synthesis, but with stated methodology (144 questions, last-asked dates to 16 Oct 2026); treat the ranking as directional, the problem descriptions as reported.*

### O2c. Refactoring / debugging round (senior loops — CONFIRMED, multiple candidates)

- Given existing code with issues: refactor and fix it under time pressure. Candidates warn it is easy to burn 15 minutes just reading — form a theory early.
- Reported example: a log-file parser running in O(n²) — debug it, improve complexity, refactor for clarity without changing behaviour, and explain how you'd test the changes (IGotAnOffer).
- Full-stack variant: the onsite coding round *is* a refactoring exercise (raise the abstraction of messy code), not an algorithm question (DesignGurus full-stack guide: https://www.designgurus.io/blog/openai-full-stack-engineer-interview).
- Some infra loops add a 75-min systems-coding round on concurrency (Land the Lab — single source).

**The bar:** Hello Interview, from multiple candidates: OpenAI "won't pass you if you have a 2/4 or low 3/4 on coding even if you ace everything else." Coding cannot be compensated by design/behavioural strength.

## O3. System design interview questions

**Format:** 45–60 min, Excalidraw, virtual. Often *two* design touches: a screen (grades concrete API + storage schema) and an onsite round (grades scaling under fast growth, retries/idempotency, production correctness). Senior expectation: own the whole process, discuss sharding/consistency/rate limiting, cross-cutting concerns (ops toil, security, privacy), build-vs-buy, bottlenecks down to OS level. Oct 2026 count: **31 of 50 design questions are classic system design** — do not over-index on AI-only prompts.

**Reported prompts (IGotAnOffer system-design guide, updated Sep 2026, + Land the Lab):**

*Classic / product:* Design Slack; Design TikTok; Design Yelp / a notifications service; online chess game; a payment system; a sandboxed cloud IDE; collaborative document editing; large-scale search; real-time analytics pipeline.
*Platform / infra:* Design GitHub Actions from scratch; webhook delivery system (delivery, caching, schema, retries/failure handling); API for an in-memory database; **rate limiter for a public API**; fault-tolerant web-crawler service at 10M req/s; devbox / CI-CD system; distributed power-grid control system (Oct 2026 list).
*AI-native:* Serve ChatGPT / design ChatGPT at hundreds of millions of weekly users (you may be told to treat model serving as a black box); **LLM-powered enterprise search** (natural-language queries over internal docs, RBAC, embeddings + full-text, ranking — IGotAnOffer's worked example); **GPU scheduling system** allocating compute across competing workloads; **vector database** for billions of embeddings; real-time NSFW-content detection on ChatGPT outputs (model choice, latency, feedback loop); AI video-generation service on a scarce GPU pool / text-to-video system; scalable LLM training system (compute + data constraints); design an AI chatbot.

**Depth expected for this candidate's level (senior, ~L5):** capacity estimates, API + schema in concrete form, data flow read/write paths, failure modes, and LLM-specific reasoning where relevant: streaming (SSE vs WebSockets, first-token latency), dynamic/continuous batching, KV cache, token-throughput vs p95 latency trade-off, admission control / load shedding (429 + Retry-After, fair queues, drop low-priority first) — the last set from Educative's OpenAI design FAQ: https://www.educative.io/courses/openai-system-design-interview-questions (prep-site framing, not a verbatim candidate report).

Sources: https://igotanoffer.com/en/advice/openai-system-design-interview · https://igotanoffer.com/en/advice/generative-ai-system-design-interview

## O4. ML / AI-specific and domain questions

**For generalist SWE MTS — CONFIRMED pattern:** You are *not* expected to derive transformers. You *are* expected to reason about model-backed systems: LLM APIs, streaming, token counting/budgets, rate limits, batching, KV cache at a conceptual level, GPU workload trade-offs, evals and safety layers as system components. Familiarity "helps outside ML roles too" (TrueInterview). Build 1–2 small things on the OpenAI API with proper tests — a Glassdoor offer-accepted candidate credited exactly that over LeetCode prep.

**For ML-focused MTS / Research Engineer — from-scratch ML coding is real (4 of the top-12 most-reported coding questions in Oct 2026 are ML coding, though ML coding is only 8 of 84 overall):**
- Find the planted bugs in a small **Transformer training script** (onsite coding, last reported 2 Oct 2026)
- Find noisy annotators and retrain a classifier without them
- Matrix product scan with autograd + hand-written backward pass
- Vectorised nearest-neighbour classifier implemented as a linear layer
- Find and fix bugs in a ~300-line transformer implementation, **then add KV caching** (DesignGurus: https://www.designgurus.io/blog/openai-interview-guide)
- Implement `all_gather` across a communication channel that drops messages
- Explain why layer normalisation improves training stability; how a transformer learns long-range dependencies
- Derive the expected number of iterations of a probabilistic function
- ML roles get a Colab notebook screen (autocomplete off): write PyTorch/NumPy by hand — broadcasting and a backward pass without looking anything up.

**Inference-infrastructure depth (for infra MTS interviews):** prefill (compute-bound) vs decode (memory-bound), paged attention, speculative decoding, quantisation trade-offs (FP8 / INT8 / INT4), tensor vs pipeline parallelism, estimating max throughput from GPU count — from https://www.techinterview.org/post/3233475331/ai-inference-infrastructure-interview-prep-2026-vllm-triton/ (general 2026 inference-prep synthesis, not OpenAI-specific reporting — flagged as background, not a reported OpenAI question list).

## O5. Behavioural / culture / values questions

**CONFIRMED reported questions:**
- "Why OpenAI?" — asked multiple times, including "Why this lab, and not another one?" (HM round: "Why OpenAI over the other labs?")
- "What would you do if told to ship without safety testing?" (Land the Lab, Oct 2026 — reported as an HM/behavioural question)
- AGI / safety view at the *recruiter* stage; "What is your view on where AI is headed, and how we will use it?"; "Where do you see AI going wrong, or being misused?"; "What draws you to the mission here, and how does it connect to your own work?"; "How do you see the social impact of AGI?"; "What's your view on the balance between open research and commercialisation?" (last two from a candidate experience write-up, dev.to — single source)
- "How do you balance velocity with safety constraints? What would make you delay a launch under executive pressure?" (reported via Aced PM guide — PM-flavoured, same theme)
- Standard-but-probed-hard: Tell me about yourself; a project/accomplishment you're most proud of; walk me through a large technical program you led; a particularly complex technical problem and your approach; a difficult technical trade-off; influencing a decision without authority; a time you made a mistake; managing conflicting priorities; disagreement with a cross-functional partner; disagreement with your manager; trouble communicating with stakeholders.

**What they're scoring (IGotAnOffer):** navigating disagreement constructively, growth mindset / acting on feedback, comfort with ambiguity, resilience under shifting priorities, clear communication across technical depths. InterviewQuery synthesis adds mission alignment specifically.

**Values framework cited in 2026 coaching content (SupaCV, medium confidence — OpenAI does not publish a single leadership-principles rubric):** Values — *Humanity first; Act with humility; Feel the AGI; Ship joy.* Operating principles — *Find a way; Creativity over control; Update quickly; Intense focus.* Source: https://supacv.com/blog/interview-playbook/openai. (Note: OpenAI's public Charter/principles language has been revised over time; anchor answers in the mission — "ensure AGI benefits all of humanity" — and your own reasoning rather than reciting a list.)

**Project presentation questions (reported):** Did you work on this end-to-end? How long did it run? Technical challenges and how you handled them? Who did you work with? What did you learn / do differently? Plus the Oct 2026 probes: what you *personally* owned, why you chose X over the alternative, what happens at 10× scale.

## O6. Take-home / practical exercises

**CONFIRMED: team-dependent, not universal.** Some teams send a take-home *instead of or in addition to* the live screen; many loops have none.

- **Webhook delivery service (Hello Interview, platform SWE candidate — the most concrete take-home report found):** register endpoints, accept events, retry failed deliveries with backoff, dead-letter queue for permanent failures, delivery-status API. 48-hour submission window, ~6 hours of work, Python/FastAPI/SQLite, submitted via private GitHub repo; instructions prioritised clean code + tests over completing every feature. **Live follow-up:** defend choices (why SQLite? what changes for production?), then add HMAC signature verification + event-type filtering live; interviewer surfaced a worker-crash bug leaving a delivery "stuck in progress" to debug together. AI tools may be allowed for the take-home itself if instructions permit — that permission does **not** carry into the live review; you must be able to explain and modify everything.
  Source: https://www.hellointerview.com/guides/openai/l4
- Generic form (IGotAnOffer): self-contained engineering problem via HackerRank — design/implement a small system or refactor code; deep-dived in a later round. Other guides cite 4–8 hours expected effort.
- Data-science take-homes (~48h A/B-test slide deck + 1h review) exist but are **not** the SWE track — do not confuse.
- Debugging exercises: the refactoring round in O2c functions as the in-loop practical exercise for seniors; separate debugging phone screens (backend: data-parsing bugs, race conditions in parallel execution, N+1 query) are also reported at OpenAI by a senior/staff product-engineering candidate write-up (Medium, Oct 2026 — single source).

## O7. What distinguishes successful candidates / common rejection reasons (OpenAI)

- Failing coding is unrecoverable (see O2 bar quote); needing multiple substantive hints = fail even if you reach a solution (IGotAnOffer).
- "NeetCode was mostly useless for this loop" (Glassdoor candidate who got an offer) — LeetCode-only prep is the most common prep mismatch.
- Refactoring round: reading too long without forming a theory.
- Project presentation: staying shallow on ownership/trade-offs/scale.
- Weak or generic safety/AGI answer — can end the process at the *recruiter* call.
- Strength signals: production-quality code with tests from the first part (so extensions are cheap), independent problem-solving, DDIA-level distributed-systems depth, and a specific, reasoned "Why OpenAI."

---

# PART II — ANTHROPIC

## A1. Full interview loop structure

**CONFIRMED PATTERN (Hello Interview 2026, IGotAnOffer updated 19 Oct 2026, InterviewQuery, Land the Lab Oct 2026):**

0. **Application** — includes a written **"Why Anthropic?"** question on many postings (strong responses ~200–400 words; valued highly — ChillInterview guide from current postings: https://www.chillinterview.com/learn/interview-guides/anthropic-software-engineer-interview-guide). Order note: the CodeSignal can arrive *before* the recruiter call.
1. **Recruiter screen — 15–30 min.** Background, motivation, role fit. **Mission/values-aware from minute one** (FrontierLoop synthesis of 60+ accounts) — a generic "frontier AI is exciting" answer is filtered here. Questions: Tell me about yourself; Why Anthropic *specifically*?; Why this role?; Walk me through your resume; career goals 3–5 years.
2. **Online assessment — CodeSignal, 90 min (the first technical filter).** One project in **4 progressive levels** (some candidates report a 6-part variant — use your invitation). You must pass a level's tests to unlock the next; each level extends the *same* code. See A2 for families and the scoring conflict. Often waived for referrals/seniors (FrontierLoop — single synthesis, plausible but unconfirmed officially).
3. **Live technical screen — ~55–60 min.** Practical implementation with an engineer in CodeSignal/Colab (some report Replit), Google Meet. Base problem ≈ ⅓ of the hour; the rest is follow-ups on scale, IO- vs CPU-bound reasoning, and parallelism. Docs/web search allowed; AI not (see A6 policy).
4. **Hiring manager screen — ~60 min.** Deep dive on your background: walk your career, then per project — Why that decision? Trade-offs? What would you do differently? How do you know it worked? Also team fit and early culture signal. Non-ML background: own it, explain the transition story (IGotAnOffer).
5. **Virtual onsite — split over TWO days (distinctive).** Typically 4–5 rounds × ~55 min:
   - *Day/Loop 1:* coding + system design. **If Loop 1 fails, Loop 2 is cancelled** (Miami/InterviewQuery compilation; Land the Lab concurs: "a weak first onsite day can cancel the second").
   - *Day/Loop 2:* hiring-manager conversation (if not already done), **project deep dive** (present a project you owned end-to-end ~20 min — candidates report using Notion — then ~40 min of probing on decisions, cross-team coordination, trade-offs), a second coding round in some loops, and the **Culture / Values interview** (see A5).
   - Some loops include the **LLM & prompt-engineering round** in the technical loop (see A4) — IGotAnOffer lists it as a standard technical-loop round; other guides treat it as team-dependent. Ask your recruiter.
6. **References + team matching — in parallel, 2–4+ weeks, sometimes 6–8.** References are checked *during* the cycle, sometimes even during the final round (InterviewQuery candidate report: three references contacted at various points including during the final round). Team matching is the opaque stage: you interview against a general bar for broad postings, then match to a team (Claude.ai, API, enterprise, agents, platform, infra) based on your interests/experience + org needs. **Candidates can be turned away at matching for lack of seats despite passing every round** (Implicator/interviewing.io reporting). No feedback is given at any rejection stage; reapply after 12 months (or sooner if something material changed).
7. **Offer & negotiation** — negotiation is *expected* (FrontierLoop) — note this **conflicts** with a Jobright/Blind-derived claim that Anthropic "does not negotiate"; more recent syntheses say negotiate. Treat compensation specifics as out of scope here; the actionable point is: don't assume the first offer is final, and don't disclose current comp/offers early.

**Timeline — CONFLICTING ranges, honestly:** IGotAnOffer: 4 weeks to 3+ months (Glassdoor); other guides: 3–4 weeks end-to-end when fast; Land the Lab counts 8 touchpoints. The variance is mostly team matching.

**Tools/format facts (official careers guidance as cited):** all interviews over Google Meet; live coding in CodeSignal / Google Colab; system design often **typed into a shared Google Doc**, not drawn (Land the Lab: design grades API, data model, request flow, handling stated load, ≥1 failure case — in prose). Python by default.

**Recent changes 2025–2026:**
- **AI-use policy reversed and clarified mid-2025** (Fortune, 21 Jul 2025): applications — draft yourself first, *then* use Claude to refine; prep — Claude explicitly encouraged; take-homes — no Claude unless stated; live interviews — no AI unless the interviewer says otherwise. Full detail in A6.
- **SINGLE-SOURCE / EMERGING:** Some 2026 loops add a round where you **write and review code with Claude Code** — AI use expected there (Land the Lab, both companies' syntheses mention agent-era rounds). The other 4 technical rounds still ban AI by default.
- Application-stage detection: Anthropic reportedly uses LLMs to detect CodeSignal code "engineered to pass tests rather than solving the problem" (IGotAnOffer) — write genuine, general code, not test-shaped hacks.

Sources: https://www.hellointerview.com/guides/anthropic/swe · https://igotanoffer.com/en/advice/anthropic-interview-process · https://www.interviewquery.com/guides/anthropic-software-engineer · http://dev.to/frontierloop/what-the-anthropic-openai-swe-interview-loop-is-actually-like-from-60-reported-accounts-1c3g

## A2. Coding interview questions

**Pattern — CONFIRMED:** Practical, build-and-extend, *not* puzzle LeetCode (with graph/DP/string topics appearing inside practical shells). Two venues with different feels: the timed CodeSignal (speed + refactorability under a clock; silent, test-driven) and live coding (communication weighted heavily — FinalRoundAI: if you stop talking for >90 seconds, many interviewers read it as a communication failure; narrate decisions and dead ends).

### A2a. CodeSignal OA families (90 min, 4 levels — CONFIRMED, multiple guides + a full candidate write-up)

1. **In-memory database — the most frequently reported.** Detailed candidate write-up (Linkjob, 2026): records keyed by string key, each record = field→value string pairs. Level 1: `SET <key> <field> <value>`, `GET`, `DELETE` (+ field delete). Later levels (across guides): filtered **SCAN** by field/value prefix, **TTL** expiry with timestamps, backup/restore / persistence and compression.
   Full write-up: https://www.linkjob.ai/interview-questions/anthropic-software-engineer-interview/
   Live-round variant (LeetCodeWizard): "Implement an in-memory key-value store. Start with SET, GET, DELETE. Now add filtered scans by value prefix. Now add TTL expiry timestamps."
2. **Banking system** — account creation + balance queries → transfers → transaction history with filtering / top spenders → interest / time-dependent logic, cashback, account merges; edge cases: negative balances, refunds, timeouts.
3. **File system simulator** — create/read → permissions model → symlinks, mounting; circular-reference and permission-inheritance edge cases.
4. **Others confirmed across guides:** package manager (install → dependency resolution → version constraints → conflict resolution); build system (task scheduling → DAG execution → caching → parallelism); text editor (insert/delete → undo/redo → rope/collaborative); constrained file cache; cloud-database simulation with transactional consistency; worker time-tracking / task scheduling with time-range queries.

Sources: https://www.sundeepteki.org/advice/anthropic-codesignal-assessment-guide · https://fonzi.ai/blog/anthropic-codesignal

**Scoring — CONFLICTING, do not trust any single threshold:**
- Sundeep Teki guide: scored /600, **520+ generally advances** (≈3 of 4 levels fully green).
- FinalRoundAI FAQ: **800+/850 consistently moves forward**, 750–799 borderline (different scale — likely a different CodeSignal framework/version).
- IGotAnOffer: candidates with **590–600 (near-perfect) reported NOT advancing** — score is necessary-not-sufficient, weighed with resume/experience/references; Hello Interview concurs: candidates have advanced with less than perfect *and* been rejected with perfect scores.
Practical takeaway: aim to fully complete Levels 1–3 fast and clean (budget ~20–25 min/level) and make real progress on Level 4; build Level 1 *extensibly* — the assessment is explicitly "how fast can I implement/refactor my code" (candidate quote, Hello Interview). Glassdoor Apr 2026: "Not LeetCode but more about writing code fast to a spec and refactoring quickly as more constraints are added per stage."

### A2b. Live / onsite coding — the known families

**Top 5 most-reported, each re-asked 18 Sep – 13 Oct 2026 (Land the Lab, n=63 known-round questions; coding is the most-reported round, 19/63):**
1. **Fix a function-cache key function, then make it durable** (last: 13 Oct 2026)
2. **Concurrent same-host web crawler** (5 Oct 2026)
3. **Image transform pipeline with a wall-clock budget** — apply transformations described in JSON to image data (5 Oct 2026)
4. **Deduplicate files by size, then content hash** (18 Sep 2026)
5. **Reconstruct call stacks from enter/exit traces** — the sampling-profiler problem (18 Sep 2026)

Next tier: banking system with transfers/cashback/merges; **distributed mode/median across worker shards**; **greedy longest-match tokenizer**.
Source: https://medium.com/@landthelab/the-5-coding-questions-anthropic-keeps-asking-and-the-round-most-people-fail-562d414e4173 (also http://dev.to/landthelab/the-5-coding-questions-anthropic-keeps-asking-and-the-round-most-people-fail-503f)

**Other reported live problems (multiple guides):**
- **Sampling profiler / stack traces:** write a function that determines the **longest-running function from stack-trace samples** (Miami compilation; ChillInterview: "parse periodic stack samples and reconstruct the longest-running function")
- Web crawler: start synchronous, then make it asynchronous/concurrent, bounded, dedupe, handle failures (LeetCode 1242 Web Crawler Multithreaded is the cited practice analogue)
- Parse all URLs from a list and count matches for a given domain (+ async design and scaling follow-ups) (IGotAnOffer)
- Serialize/deserialize a list of strings; text justification (justify a list of words within a given width); LRU cache + "now make it persistent"; interpreter-style simulation / instruction parsing that detects infinite loops; streaming message-ordering tasks; multi-stage data-mutation tasks (DataFord/ChillInterview compilations)
- Scale a token-generating function to 100,000 req/s — blurs into design (IGotAnOffer lists it under live coding)

**Perturbation warning (CONFIRMED theme):** the bank is small and well-known, so interviewers *perturb* problems mid-round to test whether you can operate, not recall. Knowing the families is table stakes; surviving the twist is the test. **Over-engineering is a named failure mode** — Anthropic's value "Do the simple thing that works" ("We don't invent a spaceship if all we need is a bicycle") is applied literally in coding: a simple loop that works beats a clever architecture.

## A3. System design interview questions

**Format — CONFIRMED:** ~55 min; often in a **shared Google Doc** (write API/data model/failure case in prose). **21 of 29 reported design questions are AI-systems/ML** (Land the Lab). Two Anthropic-specific twists:
1. **Math-first:** do capacity/GPU/bandwidth arithmetic early and let it drive the design; then keep it *simple* — over-engineering is the most-reported design failure (FrontierLoop, verbatim across sources).
2. **Interviewer-steered pacing (single-guide but detailed — Coditioning):** the interviewer may timebox topics, jump between data model → failure modes → consistency, and drive the order. A rigid sequential framework breaks; think modularly, use micro-recaps ("Given X, choosing Y because Z; downside W accepted because…"), and note uncovered territory explicitly.
3. **Safety/ops as first-class criteria:** abuse prevention + rate-limit enforcement points, what gets logged vs redacted for privacy, misuse/adversarial usage, incident response + rollback — weighted more heavily than at typical big tech (Coditioning rubric synthesis).

**Reported prompts:**
- **Design an inference batching system — the signature prompt (most frequently reported in 2026).** Single GPU, up to 100 inputs per batch, users submit synchronously and wait; design intake → batching → GPU execution → return each response to the correct user. Follow-up: scale to a GPU fleet (routing/load balancing, capacity tracking, failover when a GPU dies mid-batch). Depth expected: continuous batching, KV-cache memory, prefill vs decode, GPU-count estimates, protecting the service while new GPUs warm up. Sources: https://www.designgurus.io/answers/detail/what-to-expect-in-the-anthropic-system-design-interview · https://www.theforwarddeployed.io/interviews/anthropic/questions · https://aitechconnect.in/tips/design-inference-batching-system-interview-answer-2026 (Sep 2026, attributes the prompt to Anthropic via multiple guides)
- **Batched LLM inference API / LLM inference serving platform** (general form of the above)
- **Design a token-generation service at 100,000 req/s** — throughput math, horizontal scaling, routing, real bottlenecks
- **Design Claude's chat service** (reported Mar 2024; still in current guides) — message history, streaming responses, conversation management; variant: design a system for an LLM to handle multiple questions in a single conversation thread; 1-on-1 chat system deep-dive variant (offline delivery, message ordering via sequence numbers, WebSocket scaling via consistent hashing — Jobright/1point3acres/Blind synthesis)
- **Design a distributed search system — 1B documents, 1M QPS, incl. an LLM inference component at ~10K req/s** (Sep 2025) — sharding, replication, caching, hotspots
- **Design a hybrid search system** — text retrieval + semantic similarity, top-k over 10M documents in <50 ms (Sep 2025)
- **Data indexing pipeline / concurrent web crawler for ~1B documents** — robots.txt, rate limiting, circular references (Sep 2025)
- **Performance debugging scenario** — p95 latency spiked 100 ms → 2000 ms: build monitoring to detect it, prioritise optimisations (Sep 2025)
- **Design a distributed AI model downloader / distribute a model checkpoint / large model files across a cluster** (+ file distribution across thousands of machines with bandwidth constraints; file cache system)
- **Design an AI prompt playground**; data platform with sensitivity tiers; (research track) ML configuration system — short flexible configs vs strict typed validation
- **Design an LLM API with a safety layer** — Constitutional-AI-style principles in the request path, batching vs real-time trade-off, updating the safety layer without downtime (Jobright synthesis: https://jobright.ai/blog/anthropic-technical-interview-questions-complete-guide-2026/)
- **GPU scheduling system using credits** — preemption (can high-priority interrupt low?), preventing monopolisation, node failures; periodic credit allocation vs dynamic market (Jobright, citing Glassdoor reports)
- **Design-doc REVIEW variant (important, multiple reports):** "Here's a junior developer's design for an inference batching system — review it and explain what you'd change"; another candidate (Aced/Exponent, Staff/L6): asked to review an existing design doc, then deep-dive on failure handling and overload protection. Practise *critiquing* designs, not only producing them.
- GenAI-framed: "How would you design a language model that minimises harmful outputs while still being useful and expressive?" (IGotAnOffer GenAI guide, from Glassdoor/Reddit reports)

Sources: https://www.coditioning.com/blog/15/anthropic-system-design-interview-questions · https://igotanoffer.com/en/advice/anthropic-interview-process

## A4. ML / AI-specific and domain questions

**Anthropic explicitly does NOT require ML background for SWE MTS:** ~half its technical staff had no prior ML experience when they joined (Anthropic careers page, cited by nearly every guide). The bar is *AI-native engineering judgement*, not research depth.

**The LLM & prompt-engineering round (in many SWE loops — IGotAnOffer lists it as a standard technical-loop round; worked in Google Colab):** interviewers test whether you understand how LLMs work, *where they fail*, and how to design around the limitations. Reported tasks:
- Design effective prompts for a specific use case; reason about a *systematic* prompt-engineering approach
- Build systems that call LLM APIs efficiently — **token management, rate limits, cost models**
- Design multi-step reasoning systems where multiple LLM calls coordinate
- (Applied-AI track, different role but illustrative of the flavour: retrieval scorer, token-budget allocator, tool-use orchestrator — "build something that works and reason about its failure modes")

**Concepts a generalist SWE should be able to discuss (inferred from the design + LLM rounds above, CONFIRMED as design-round depth):** tokens and context-window budgeting (count before sending, reserve output budget, summarisation/pinning strategies for long conversations); continuous batching; KV cache (what it stores, why decode is memory-bound, memory growth with sequence length × batch); prefill vs decode; streaming for latency masking; RAG pipeline shape (chunking, embeddings, vector search, hybrid retrieval, citations/grounding) and *when NOT to use RAG / when to fine-tune instead*; evals (how you'd know a system works beyond eyeballing); guardrails (prompt injection direct/indirect, PII handling, input/output filters, red-teaming); model routing/fallbacks and cost-latency trade-offs.

**ML-focused MTS / Research Engineer (for contrast — deeper):** "Explain the architecture of a Transformer — key components and why they matter"; "How would you optimise a model for inference latency?" (quantisation, distillation, hardware acceleration); design a distributed training pipeline with fault tolerance; numpy-style array operations and occasionally hand gradient computation; research brainstorm ("How would you detect hallucinations in a language model?" / "Design an experiment to detect whether a model is being deceptive rather than merely wrong"); a research presentation / paper deep dive. Sources: https://jobright.ai/blog/anthropic-technical-interview-questions-complete-guide-2026/ · https://www.sundeepteki.org/advice/the-ultimate-ai-research-scientist-interview-guide-cracking-anthropic-openai-google-deepmind-top-ai-labs-in-2026 (research-track guide — its SWE claims are thinner; use for ML-track contrast only)

## A5. Behavioural / culture / values questions

**This is Anthropic's defining round — treat it as a technical round.** A *separate, standalone* Culture/Values interview (~60 min, sometimes two interviewers — one asks, one shadows; the interviewer can be **non-technical, from any department**, and a low rating is effectively a veto). Bloomberg Businessweek (May 2026) + interviewing.io's founder: it "is where most candidates fail, per Anthropic recruiters"; a recruiter told one candidate people are rejected "because of the behavioural aspect of things, even if they have done really well technically." Candidates describe it as "almost like a therapy session" — probing how you *felt*, with follow-ups several levels deep. **Pre-packaged STAR stories are the most common way to fail it**; scripted answers and flattery backfire; updating your position under a good argument is the behaviour being tested.

**CONFIRMED reported questions:**
- "What are some **unusual beliefs** that you hold, and how have you defended those beliefs in uncomfortable situations?" — Daniela Amodei (co-founder/president), describing the test on a 2025 podcast; corroborated by Bloomberg. Source: https://www.beckershospitalreview.com/healthcare-information-technology/ai/what-it-takes-to-get-a-job-at-anthropic/
- "Tell me about a time you had a **moral conflict** with the work. Who did you talk to? What did they say that **changed your mind**?" / "Tell me about a time you built something against your values" (variant)
- "What **concerns / critique** do you have with Anthropic's mission or direction?" — *not a trap; agreeing with everything is the weak answer.* A specific, well-reasoned disagreement offered without hostility scores higher.
- "How do you balance delivery speed with security/safety concerns?"
- "Tell me about a time you received negative feedback — how did you handle it?"
- "Describe a time you disagreed with your manager and **later changed your mind**"
- "What are the ethical risks of deploying agentic AI systems in high-stakes environments?"
- "Tell me about a time you made a safety-first decision, even if it meant a trade-off"
- "Tell me about a time when a technical misjudgment led to a project delay. What did you learn?"
- "Describe a time you had a technical disagreement with a colleague. How did you resolve it?"
- "What would you do if, midway through a project, you realised it was actually unfeasible?"
- "Tell me about a time you had to push back on a technical direction you disagreed with"
- Expect **negative-framed** probing throughout: teams you didn't like, strategies you found limiting, feedback that was hard to receive (Miami compilation).
- SINGLE-REPORT (Blind, via Hello Interview): asked whether they'd accept **Anthropic's stock falling to zero** in pursuit of its mission — the trade-off made personal.
- Every interviewer, every round, asks some version of **"Why Anthropic?"**

**Hiring-manager round questions:** project walk-throughs with Why/trade-off/what-differently probing (A1.4); "What did you personally own?"; a 0→1 system or large migration; the most technically difficult system you built.

**Anthropic's stated values (prepare against these, in your own words):** Act for the global good; Hold light and shade; Be good to our users; Ignite a race to the top on safety; **Do the simple thing that works**; Be helpful, honest, and harmless; Put the mission first. Primary sources to actually read: *Core Views on AI Safety*, the *Responsible Scaling Policy*, Constitutional AI paper, Dario Amodei's essays (recruiters may send safety reading before the onsite).

## A6. Take-home / practical exercises

**For core SWE MTS: there is usually NO multi-day take-home** — the 90-min CodeSignal *is* the timed practical exercise (do not confuse the two). Take-homes appear for:
- **Research Scientist / Research Engineer:** ~48-hour window problem set/dataset, or a ~5-hour time-boxed project (API exploration / model evaluation). Reviewed for reasoning process: a write-up showing what you tried, what failed and why, and what you'd do with more time beats a clean write-up that hides it (FinalRoundAI synthesis).
- **Performance Engineer:** specialised 2-hour timed take-home — optimise a core kernel (loop unrolling, memory coalescing, op fusion; GPU-kernel-like). AI tools *permitted* here; one candidate reported ~8× improvement, >600/1000 needed to advance (Jobright, citing 1point3acres — single-source detail, treat numbers cautiously).
- **Applied AI Engineer (adjacent role):** 3–4h extended live build / take-home — build a small Claude-powered app against a fictional customer brief; graded on shipped behaviour, API hygiene, handling ambiguity (GetPerspective synthesis).
- **Code-review practical:** the design-doc review in A3 functions as Anthropic's review exercise in the SWE loop.

**Official AI-use policy (updated mid-2025 — CONFIRMED via Fortune coverage + Anthropic candidate guidance as cited by Hello Interview/IGotAnOffer):**
- Application materials: create your first draft yourself, *then* you may use Claude to refine it.
- Interview preparation: Claude explicitly encouraged ("Use Claude to research Anthropic, practice your answers, and prepare questions for us").
- Take-homes: "Complete these without Claude unless we indicate otherwise."
- Live interviews / CodeSignal: **no AI assistance unless explicitly indicated** — including Claude, ChatGPT, code generation, and AI autocomplete. Ordinary documentation/web lookup *is* allowed in technical interviews.
Source: https://www.metaintro.com/blog/inside-anthropic-brutal-hiring-process-bans-ai-interviews · https://www.hellointerview.com/guides/anthropic/swe

## A7. What distinguishes successful candidates / common rejection reasons (Anthropic)

- **Culture round is the #1 filter** (see A5) — ahead of any technical round.
- **Over-engineering** (coding *and* design) — violates "do the simple thing that works."
- **Silent coding** in live rounds; not narrating dead ends.
- **Generic "Why Anthropic"** ("interesting AI problems," "Claude is impressive") — recruiters actively filter for mission specificity: reference the Responsible Scaling Policy, Constitutional AI, interpretability, and connect them to *your* systems experience (e.g. agent safety as a software-architecture problem: containment, least privilege, observable execution, blast-radius limits).
- **Speed without extensibility in CodeSignal** — rushing Level 1 with a brittle structure that must be rewritten at Level 3; alternatively, perfecting early levels and running out of time.
- **Team-matching stall** — passing everything, then no seat; keep other processes alive, state team interests clearly, have references ready early.
- Strength signals: start simple → make it work → absorb the new constraint → name the trade-off → harden (ChillInterview's summary of the recurring pattern); math-first simple designs; genuine, specific, *skeptical* values answers (including a real critique of Anthropic).

---

# PART III — Comparison table

| Dimension | OpenAI MTS SWE | Anthropic MTS SWE |
|---|---|---|
| Loop shape | Recruiter → HM → skills assessment (coding *or* design *or* take-home) → final 4–6 rounds / 1–2 days | Recruiter → CodeSignal OA → live screen → HM → onsite over **2 days** (Day 2 gated on Day 1) → references + team matching |
| Decentralisation | High — "process varies by team" in nearly every report | Moderate — round *set* is more standard (values round is universal), order/format varies by org |
| First technical filter | Live CoderPad/HackerRank, 60–90 min, one problem in 3–5 parts | Timed CodeSignal, 90 min, 4 unlock-gated levels of one project |
| Signature coding families | Resumable iterator, in-memory SQL/LSM store, `cd`+symlinks, spreadsheet, versioned KV, GPU credit ledger | In-memory DB (OA), banking system (OA), crawler, file dedupe, stack-trace profiler, function-cache durability |
| Refactoring/debugging | **Dedicated round** in senior onsite loops | Absorbed into build-and-extend + design-doc review |
| Design tool / style | Excalidraw; candidate-led; classic + product prompts common | Shared Google Doc, prose; interviewer may steer; AI-infra prompts dominant |
| Signature design prompt | LLM enterprise search; ChatGPT serving; GPU scheduler; vector DB | **Inference batching on GPUs**; token service @100K rps; Claude chat; search @1B docs/1M QPS |
| ML bar for generalist SWE | Conceptual LLM-systems literacy; build on the API | Same + an explicit LLM/prompt-engineering round in many loops |
| ML bar for ML MTS | From-scratch PyTorch: transformer bug-fix + KV cache, autograd, all_gather | Transformer explanation, inference optimisation, distributed training design; research roles add brainstorm + presentation |
| Values assessment | Woven in: recruiter gate + HM/behavioural; "ship without safety testing?" | **Dedicated 60-min round with veto power**; unusual-beliefs probe; critique-of-Anthropic expected |
| Bar-raiser equivalent | No named bar-raiser reported; hiring committee + levelling at the end. Coding score acts as the hard gate | No named bar-raiser; the **Culture interviewer functions as the bar-raiser/veto**, plus team matching as a second late gate |
| Project deep dive | 45-min presentation, rapid ownership/scale probing | ~20-min presentation + ~40 min probing, often Notion-based |
| Take-home | Team-dependent; webhook-service report is the concrete example; 48h window | Rare for SWE (CodeSignal instead); common for research/perf/applied tracks |
| AI-tool policy | No AI / no autocomplete in coding rounds; docs OK; emerging agentic round in *some* loops | Codified by stage (mid-2025): prep OK, application refine OK, take-home/live no unless stated |
| Timeline | 2–8 weeks | 3–4 weeks fast; up to 3+ months with matching |
| Most-reported failure | Weak coding score; LeetCode-only prep; shallow project dive | Values round; over-engineering; generic mission answer; matching stall |
| Negotiation (context only) | Reported as holding firmer | Reported as expected (one older synthesis disagrees) |

---

# PART IV — Prioritised prep plan

*Tailored for: Amazon SDE II, 6 years distributed systems. Your unfair advantages: production distributed systems, incidents, scale, ownership stories. Your gaps vs these loops: Python-from-scratch coding speed without autocomplete/IDE, LLM-systems vocabulary, and (for Anthropic) values-round depth. Prep in this order — it is ranked by failure-rate × gap.*

### P0 — Do these first (highest failure-rate items)

1. **Build-and-extend coding in Python, timed, autocomplete OFF, in CoderPad/CodeSignal-like editors.** This is *both* companies' core test and the biggest style change from Amazon's loop. Drill, in order, until each fits in ~50–60 min with tests:
   - In-memory DB/KV: SET/GET/DELETE → scan/filter → TTL → persistence/compression (serves Anthropic OA *and* OpenAI KV/LSM variants)
   - Resumable iterator (list → JSON files → multi-file → nested)
   - Banking/ledger system incl. a GPU-credit-ledger variant with out-of-order events and expirations
   - `cd` with symlinks; spreadsheet with cycle detection
   - Concurrent web crawler (bounded, deduped, failure handling) — then make every other solution concurrent once it works
   - File dedupe (size → hash); stack-trace profiler (longest-running function from samples); function cache + durability
   Rules of the drill: working code in part 1 before optimising; write tests as you go; narrate out loud the entire time (Anthropic live rounds punish silence); after finishing, add one surprise requirement and absorb it *without rewriting*.
2. **One project deep-dive, weaponised.** Pick your strongest Amazon system (owned end-to-end, with an incident and a hard trade-off). Prepare: 20-min Anthropic cut and 45-min OpenAI cut (slides). Rehearse the probes: What did *you* own vs the team? Why X over Y? Metrics — how do you know it worked? The incident, honestly. What at 10× scale breaks first? What would you do differently? Shallow here fails strong coders at *both* labs.
3. **Your values/safety positions — written, specific, defensible 3 follow-ups deep.**
   - *Anthropic version:* Read Core Views on AI Safety, the Responsible Scaling Policy, and the Constitutional AI paper summary. Form: one genuine agreement, one genuine **critique** of Anthropic's direction, one story of a moral conflict at work (who you talked to, what changed your mind), one unusual belief you've defended, one time you changed your mind, one safety-first trade-off you actually made. Practise *updating* your view mid-conversation when pushed with a good argument.
   - *OpenAI version:* A reasoned view on AGI timelines/impact, open research vs commercialisation, misuse risks, and a direct answer to "What would you do if told to ship without safety testing?" + "Why OpenAI over Anthropic/DeepMind?" that is not interchangeable between labs.

### P1 — System design, lab-flavoured (your strength — adapt the flavour, don't relearn the basics)

4. Practise these five prompts end-to-end, 55 min each, **with capacity math in the first 10 minutes**: (a) inference batching system, single GPU → GPU fleet (Anthropic signature); (b) LLM-powered enterprise search with RBAC (OpenAI signature); (c) token-generation / LLM inference service @100K rps (continuous batching, KV-cache memory budgeting, prefill vs decode, admission control, streaming); (d) Claude/ChatGPT chat service (history, streaming, multi-question threads); (e) one classic (webhook delivery or rate limiter or GitHub Actions) — OpenAI still asks classics heavily.
5. Practise **in Anthropic's format** at least twice: typed into a doc, interviewer interrupting/steering, plus one **design-review** rep (critique a deliberately flawed inference-batching design: failure handling, overload protection).
6. LLM-systems cheat-sheet to be able to *use*, not recite: tokens/context budgeting, KV cache, continuous vs static batching, speculative decoding (idea), quantisation (FP8/INT8/INT4 trade-off), PagedAttention (idea), SSE vs WebSocket streaming, 429/Retry-After + fair queuing, semantic caching, RAG vs fine-tuning decision, evals (offline sets, LLM-as-judge limits, regression gates).

### P2 — ML literacy for a generalist (days, not weeks)

7. Transformer in one hour, engineer-level: tokenisation (BPE, greedy longest-match), embeddings + position, self-attention, why KV cache works, layer norm's role, prefill/decode. Be able to whiteboard a forward pass and explain long-range dependencies. Build one tiny thing on each API (a RAG over your own docs with evals + a token/rate-limit-aware client) — cited by a successful OpenAI candidate as the prep that actually helped.
8. *Only if targeting ML/infra MTS tracks:* PyTorch/NumPy from scratch — attention, a transformer block, hand-written backward for a simple op, KV-cache implementation, transformer bug-hunting reps, all_gather semantics. Skip this for generalist SWE loops; it is a poor use of time there (ML coding is 8/84 reported OpenAI coding questions overall).

### P3 — Logistics that actually move outcomes

9. On the recruiter call, ask: exact round list and order; live vs take-home; is there a design *screen* as well as an onsite design; AI policy for *your* rounds; language/environment (CoderPad vs CodeSignal vs Colab); what level you're being looped for. Both labs' loops vary too much to prep blind.
10. Have **two references (one a manager) identified and briefed before the onsite** — Anthropic checks during the cycle; OpenAI may request at decision. Tell both recruiters about competing deadlines early (both labs accelerate).
11. Rehearse the two "Why?" answers to 90 seconds each, lab-specific, and *different from each other* — using your Anthropic answer at OpenAI (or vice versa) is a named recruiter-screen failure at both.

### Suggested sequence (if ~4 weeks part-time)
Week 1: P0.1 coding families 1–3 + start P0.3 reading. Week 2: P0.1 families 4–6 + P0.2 project dive. Week 3: P1 designs (5 prompts + 1 review rep) + P2. Week 4: timed full mocks (one OpenAI-shaped: coding + refactor + design; one Anthropic-shaped: 90-min CodeSignal simulation + values mock), values-answer stress-test, logistics.

---

## Could not verify / open questions

- **No primary question bank exists.** Glassdoor/Blind posts are paywalled/anonymised; most detail comes from prep-platform syntheses of those reports (IGotAnOffer, Hello Interview, InterviewQuery, DesignGurus) and two Oct-2026 counts by Land the Lab, whose methodology notes state the text was AI-drafted and checked against its data. Question *descriptions* are consistent across independent sources; exact *frequencies/rankings* rest mainly on Land the Lab's counts and should be treated as directional.
- **CodeSignal passing score: unresolved conflict** (520/600 vs 800/850 vs near-perfect scorers rejected) — likely different CodeSignal frameworks across years/roles. No source resolves it; the report presents all three.
- **PrepInsta:** searched specifically; no dedicated, substantive OpenAI/Anthropic MTS page surfaced in results — it contributed nothing usable, contrary to the mission's expectation. LeetCode Discuss similarly surfaced only via analogues (e.g. LC 1242 for Anthropic's crawler); 1point3acres posts are login-walled (titles corroborate the resumable-iterator / `cd` / SQL families only).
- **"Bar raiser" as a named round:** no source reports an Amazon-style bar raiser at either company. The functional equivalents are identified in the comparison table (OpenAI: coding gate + hiring committee; Anthropic: Culture interviewer veto + team matching) — that mapping is this report's synthesis, not a company's term.
- **Agentic / Claude Code interview rounds (2026):** reported by single syntheses for both companies (SupaCV for OpenAI; Land the Lab for Anthropic). Plausible and worth asking the recruiter about, but not yet a confirmed standard round.
- **Anthropic LLM & prompt-engineering round for SWE:** listed as standard by IGotAnOffer, treated as team-dependent elsewhere. Unresolved — ask the recruiter.
- Salary/compensation was out of scope except where it touched negotiation expectations, where sources conflict (noted in A1).

## Sources

**OpenAI**
- IGotAnOffer — OpenAI Software Engineer Interview (updated 14 Oct 2026) — https://igotanoffer.com/en/advice/openai-software-engineer-interview
- IGotAnOffer — OpenAI System Design Interviews (updated 21 Sep 2026) — https://igotanoffer.com/en/advice/openai-system-design-interview
- Hello Interview — OpenAI Coding Interviews 2025: Real Questions from Real Candidates — https://www.hellointerview.com/blog/openai-coding-questions
- Hello Interview — OpenAI L4 Interview Guide (2026, incl. webhook take-home report) — https://www.hellointerview.com/guides/openai/l4
- Land the Lab (Medium, Oct 2026) — The 12 coding questions OpenAI keeps asking (n=144) — https://medium.com/@landthelab/the-12-coding-questions-openai-keeps-asking-its-screen-bans-autocomplete-ce9011f08817
- Glassdoor — OpenAI SWE interview, Oct 2026 (via search index) — https://www.glassdoor.ie/Interview/OpenAI-Interview-E2210885-RVW93521232.htm
- InterviewQuery — OpenAI Software Engineer Interview Guide (candidate account mirroring the Glassdoor report) — https://www.interviewquery.com/guides/openai-software-engineer
- DesignGurus — OpenAI Interview Guide (ML/research questions, behavioural) — https://www.designgurus.io/blog/openai-interview-guide
- DesignGurus — OpenAI Full Stack Engineer Interview (refactoring round) — https://www.designgurus.io/blog/openai-full-stack-engineer-interview
- SupaCV — How OpenAI Interviews in 2026 (values list, agentic-coding beta) — https://supacv.com/blog/interview-playbook/openai
- TrueInterview — OpenAI Interview Process & Questions — https://trueinterview.io/study/openai-interview-process
- Linkjob — 2026 OpenAI Coding Interview Question Bank (resumable iterator, `cd` detail) — https://www.linkjob.ai/interview-questions/openai-coding-interview/
- Educative — OpenAI System Design Interview Questions (LLM-serving FAQ) — https://www.educative.io/courses/openai-system-design-interview-questions
- TechInterview — AI Inference Infrastructure Interview Prep 2026 (background) — https://www.techinterview.org/post/3233475331/ai-inference-infrastructure-interview-prep-2026-vllm-triton/

**Anthropic**
- IGotAnOffer — Anthropic Interview Process & Timeline (updated 19 Oct 2026) — https://igotanoffer.com/en/advice/anthropic-interview-process
- Hello Interview — Anthropic Software Engineer Interview Guide (2026) — https://www.hellointerview.com/guides/anthropic/swe
- Land the Lab (Medium/dev.to, Oct 2026) — The 5 coding questions Anthropic keeps asking (n=72) — https://medium.com/@landthelab/the-5-coding-questions-anthropic-keeps-asking-and-the-round-most-people-fail-562d414e4173
- FrontierLoop (dev.to, 25 Jun 2026) — Anthropic & OpenAI loops from 60+ reported accounts — http://dev.to/frontierloop/what-the-anthropic-openai-swe-interview-loop-is-actually-like-from-60-reported-accounts-1c3g
- Coditioning — Anthropic System Design Interview Questions (Sep 2025 confirmed prompts) — https://www.coditioning.com/blog/15/anthropic-system-design-interview-questions
- University of Miami / InterviewQuery — Get a Job at Anthropic (May 2026; coding/design/behavioural lists, two-loop onsite) — https://customcareer.miami.edu/blog/2026/05/14/get-a-job-at-anthropic-interview-process-and-top-questions/
- Linkjob — My 2026 Anthropic SWE Interview Process and Actual Questions (in-memory DB levels) — https://www.linkjob.ai/interview-questions/anthropic-software-engineer-interview/
- Sundeep Teki — Anthropic CodeSignal Assessment Guide (problem types; 520/600 claim) — https://www.sundeepteki.org/advice/anthropic-codesignal-assessment-guide
- Fonzi — Anthropic CodeSignal Interview: Format, Questions and Prep — https://fonzi.ai/blog/anthropic-codesignal
- FinalRoundAI — How to Ace Your Anthropic CodeSignal Assessment (800/850 claim) — https://www.finalroundai.com/blog/how-to-ace-your-anthropic-code-signal-assessment-a-step-by-step-guide
- ChillInterview — Anthropic Software Engineer Interview Guide (2026) — https://www.chillinterview.com/learn/interview-guides/anthropic-software-engineer-interview-guide
- Jobright — Anthropic Technical Interview Questions: Complete Guide 2026 — https://jobright.ai/blog/anthropic-technical-interview-questions-complete-guide-2026/
- InterviewQuery — Anthropic Software Engineer Interview Guide (candidate account) — https://www.interviewquery.com/guides/anthropic-software-engineer
- DesignGurus — What to Expect in the Anthropic System Design Interview (inference batching) — https://www.designgurus.io/answers/detail/what-to-expect-in-the-anthropic-system-design-interview
- TheForwardDeployed — Anthropic System Design Interview Questions — https://www.theforwarddeployed.io/interviews/anthropic/questions
- Becker's / Bloomberg Businessweek (May 2026) — Anthropic's unusual hiring playbook (culture interview, Amodei unusual-beliefs quote) — https://www.beckershospitalreview.com/healthcare-information-technology/ai/what-it-takes-to-get-a-job-at-anthropic/
- Implicator — Anthropic's Culture Interview Is Its Top Hiring Gate (interviewing.io data) — https://www.implicator.ai/at-anthropic-the-culture-interview-is-the-top-late-stage-hiring-gate/
- Metaintro (summarising Fortune, 21 Jul 2025) — Inside Anthropic's hiring process / AI-policy reversal — https://www.metaintro.com/blog/inside-anthropic-brutal-hiring-process-bans-ai-interviews

*All sources read 22 Oct 2026 via web index / page fetch. No page instructions were followed; all page content was treated as source material only.*
