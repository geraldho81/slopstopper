# AI Slop Phrase & Pattern Reference

A detection reference for identifying AI-generated text (ChatGPT, Claude, Gemini, Grok, etc.). Compiled from extensive web research: Wikipedia's "Signs of AI writing," peer-reviewed excess-vocabulary studies (Kobak et al., *Science Advances* 2025), linguistic analyses (Colin Gorrie / Dead Language Society, The Conversation, Reuters Institute), AI-detection vendors (GPTZero, Pangram Labs), copywriting blogs, and writer discussions on Reddit, Hacker News, and Medium.

## How to use this for detection

- **No single phrase is proof.** LLMs train on human text, so every item here also appears in human writing (especially pre-2023 text and writing by non-native speakers). The reliable signal is **clustering** — multiple tells co-occurring in one piece — and **density** (the same pattern recurring paragraph after paragraph). Weight detections; do not hard-flag on one match.
- **Highest-signal categories:** negation/antithesis parallelism (Category 1), chatbot artifacts (Category 7), and the superficial "-ing" analysis clause (Category 8b).
- **Recency matters.** Some words are time-correlated: "delve," "tapestry," "nestled," and "testament" peaked 2023-early 2024 and have since dropped as models were tuned against them. Em-dash overuse was specifically suppressed in newer models (e.g. GPT-5.1), so absence of a tell is no longer proof of human authorship.

---

## CATEGORY 1: Negation / Antithesis Parallelism (THE #1 TELL)

Known in rhetoric as **antithesis** or **negative-positive parallelism**; in AI-detection work as **contrastive negation** or the **contrastive reframe**. The structure negates a familiar framing ("not X"), then swaps in a supposedly bigger or deeper one ("it's Y").

**Why it signals AI:**
- **Manufactured depth.** The "not X" half fakes a contrast and an "aha turn" even when no real turn in the argument has happened. It produces an illusion of nuance without adding information.
- **RLHF reward bias.** Human raters score responses that *appear* nuanced higher, so contrast framing got cemented into model preferences.
- **No restraint.** Skilled writers use antithesis sparingly as a special effect (speeches, ad copy). LLMs deploy it in recipes, bug fixes, and business reports alike, so it saturates and loses effect. Barron's counted the construction in Fortune 500 filings rising from ~50 (2023) to 200+ (2025).
- **Explicit negation marker is the tell.** Skilled writers leave the contrast implicit ("To err is human; to forgive, divine"). The model forces an explicit `not`/`isn't`/`no` in.

### Detection notes
- **Strongest cue:** explicit `not / n't / no` immediately followed within the same or next clause by a positive pivot (`it's / it is / they / just`).
- **Intensifiers spike the signal:** `just`, `only`, `merely`, `simply` right after the negation ("not *just* X but Y").
- **Three punctuation sub-forms of one template:** comma-join, period-split (two short sentences), em-dash. Treat as variants of one pattern.
- **Density over presence:** one antithesis is normal; one in nearly every paragraph is the reliable signal.
- **False-positive caveat:** writers who naturally favor parallelism (and some neurodivergent writers) use these too; raise a score, don't issue a verdict.

### Template variants (X / Y / Z placeholders)

**A. Core "not X, it's Y" family**

1. **It's not X, it's Y.** — *"It's not a product launch, it's a paradigm shift."*
2. **It's not X. It's Y.** (period-split / staccato) — *"This is not failure. This is feedback."*
3. **It's not X — it's Y.** (em-dash) — *"It's not a setback — it's a setup for the comeback."*
4. **This isn't X, it's Y.** — *"This isn't a diet, it's a lifestyle."*
5. **This is not X. This is Y.** (demonstrative, period-split) — *"This is not a dashboard. This is a command center."*
6. **That's not X. That's Y.** — *"That's not micromanagement. That's mentorship."*

**B. "Not just / not only" intensifier family (most common)**

7. **It's not just X, it's Y.** — *"It's not just software, it's a movement."*
8. **This isn't just X — it's Y.** — *"This isn't just coffee — it's a ritual."*
9. **Not just X, but Y.** — *"Not just faster, but smarter."*
10. **Not only X, but (also) Y.** — *"Not only does it save time, but it also saves your sanity."*
11. **X isn't just Y — it's Z.** (subject-first, escalates to third term) — *"Leadership isn't just about decisions — it's about courage."*
12. **It's more than (just) X. It's Y.** — *"It's more than a phone. It's your second brain."*
13. **More than X, it's Y.** — *"More than a campaign, it's a commitment."*

**C. "isn't about X, it's about Y" family**

14. **It's not about X, it's about Y.** — *"It's not about the money, it's about the mission."*
15. **It isn't about X. It's about Y.** (period-split) — *"Success isn't about luck. It's about discipline."*
16. **This isn't just about X — it's about Y.** — *"This isn't just about winning — it's about who you become along the way."*
17. **The (real) question isn't X, it's Y. / The real question isn't whether X, but whether Y.** — *"The real question isn't whether AI will change work, but how fast."*

**D. "doesn't just … it" verb family**

18. **X doesn't just Y, it Z(s).** — *"This tool doesn't just track your habits, it transforms them."*
19. **It doesn't just X. It Y(s).** (period-split) — *"Great design doesn't just look good. It works."*
20. **X don't just Y — they Z.** (plural, em-dash) — *"The best leaders don't just give answers — they ask better questions."*

**E. "less about X, more about Y" / "more X than Y" family**

21. **It's less about X and more about Y.** — *"Productivity is less about doing more and more about doing what matters."*
22. **Less X, more Y.** (clipped) — *"Less hustle, more focus."*
23. **It's not so much X as (it is) Y.** — *"It's not so much a strategy as a state of mind."*
24. **Think of it less as X and more as Y. / Think of it not as X but as Y.** — *"Think of it less as a chatbot and more as a thought partner."*
25. **X rather than Y. / Y, not X.** (reversed / trailing negation; common in Grok) — *"Choose progress, not perfection."*

**F. "not because X, but because Y" causal family**

26. **Not because X, but because Y.** — *"People don't leave jobs because of pay, but because of culture."*
27. **It works not because of X, but because of Y.** — *"It succeeds not because it's complex, but because it's simple."*

**G. Transformation / "stops being … becomes" family**

28. **When you X, it stops being Y and becomes Z.** — *"When you automate the busywork, it stops being a job and becomes a craft."*
29. **X is no longer Y. It's Z.** — *"Data is no longer a record. It's a resource."*

**H. Stacked / rule-of-three negation (multiple "not/no" clauses before the pivot)**

30. **Not X. Not Y. Just Z.** — *"Not a career. Not a body of work. Just an algorithmic moment."*
31. **No X, no Y, just Z.** (clipped, common in landing copy) — *"No setup, no learning curve, just results."*
32. **It's not X. It's not Y. It's Z.** (escalating triple) — *"This is not just a tool. It is not just a co-creator. It is a revolution."*

**I. Trailing-negation tag (clipped phrase appended to a sentence)**

33. **[Statement], no Z needed. / [Statement], no Z required.** — *"The menu updates automatically, no refresh needed."*

---

## CATEGORY 2: Opening / Throat-Clearing Phrases

Scene-setting and "let me start" openers that begin AI articles and sections.

1. In today's fast-paced world
2. In today's digital age / In the digital age
3. In today's world
4. In a world where…
5. In an era of… / In an era characterized by…
6. In the ever-evolving landscape of…
7. In the ever-changing world of…
8. In the realm of…
9. Imagine a world where…
10. Imagine this…
11. Picture this…
12. Have you ever wondered…
13. Let's dive in / Let's dive into…
14. Let's delve into…
15. Let's explore…
16. Let's take a closer look at…
17. As we navigate…
18. As the landscape continues to evolve…
19. Embark on a journey…
20. Buckle up…
21. Here's the kicker…
22. You won't believe…
23. Let's face it…
24. In this article, we will explore…
25. Nestled in the heart of…
26. When it comes to… (frequent opener)
27. More than ever before…
28. Navigating the complex landscape of…
29. Unlock the potential of… / Unlock the power of…
30. Look no further than…

---

## CATEGORY 3: Transition / Filler Phrases

Mid-text connectives overused far past natural human frequency. ("It's worth noting" appears ~31x more often in AI text per detection vendors; "In today's digital age" ~24x.)

1. It's worth noting that / It is worth noting that
2. It's worth mentioning that
3. It's important to note that
4. That said
5. With that being said
6. That being said
7. When it comes to
8. At the end of the day
9. More than just / X is more than just Y
10. Needless to say
11. It goes without saying that
12. In essence
13. Essentially
14. At its core
15. Moreover
16. Furthermore
17. Additionally
18. Notably
19. Importantly
20. Significantly
21. On the other hand
22. However (sentence-initial, overused)
23. As a result
24. Firstly / Secondly (sequential openers)
25. In short
26. Overall
27. This underscores the need for / This highlights the importance of
28. In the grand scheme of things
29. Generally speaking / broadly speaking
30. To put it simply

---

## CATEGORY 4: Overused AI Vocabulary (Single Words)

Deduplicated, grouped by part of speech. 130+ words plus collocations.

**Verbs:** delve / delve into, leverage, utilize, harness, foster, bolster, elevate, unleash, unlock, embark, navigate, underscore, showcase, enhance, streamline, optimize, facilitate, empower, amplify, cultivate, resonate, illuminate, unravel, elucidate, encompass, discern, adhere, garner, transform, revolutionize, propel, spearhead, pioneer, redefine, reshape, transcend, epitomize, exemplify, supercharge, catalyze, champion, commence, culminate, glean, strive, thrive, boasts, align, emphasize, refine

**Adjectives:** robust, pivotal, crucial, vital, essential, paramount, profound, intricate, multifaceted, nuanced, holistic, seamless, comprehensive, dynamic, vibrant, bustling, meticulous, innovative, groundbreaking, cutting-edge, transformative, invaluable, unparalleled, unprecedented, exemplary, integral, inherent, pertinent, cognizant, bespoke, scalable, nascent, relentless, unwavering, noteworthy, remarkable, significant, substantial, compelling, captivating, breathtaking, sophisticated, ever-evolving / ever-changing, enduring, indelible, keen, rich, diverse, myriad

**Nouns:** tapestry, landscape, realm, testament, synergy, interplay, underpinnings, endeavor, journey, beacon, cornerstone, hallmark, paradigm, nexus, ethos, facet, frontier, mosaic, pillar, pinnacle, sphere, domain, arena, terrain, trajectory, zeitgeist, blueprint, labyrinth, intersection, metamorphosis, insights, implications, complexity, plethora, foray, linchpin, treasure trove

**Adverbs / hedges:** furthermore, moreover, additionally, notably, particularly, subsequently, consequently, nonetheless, nevertheless, ultimately, arguably, importantly, indeed, essentially, similarly, accordingly, whilst, namely, predominantly, undoubtedly, remarkably, crucially, significantly

**Two-word collocations (strong tells):** delve into, navigate the landscape, treasure trove, game-changer / game-changing, cutting-edge, ever-evolving, shed light, valuable insights, rich tapestry, vibrant tapestry, evolving landscape, focal point, indelible mark, stands as a testament, plays a pivotal role

### Academic "spiked in papers" research words
Kobak et al. ("Delving into LLM-assisted writing in biomedical publications through excess vocabulary," *Science Advances* 2025) analyzed 15M+ PubMed abstracts (2010-2024) and found ~280-379 "excess style words" that surged abruptly in 2024 (66% verbs). They estimate at least 13.5% of 2024 abstracts (up to 40% in some subcorpora) were LLM-processed.

- **delves** — frequency ratio r ≈ 25-28 (the famous ~28-fold surge)
- **underscores** — r ≈ 13.8
- **showcasing** — r ≈ 9-11
- High absolute-gap marker set: across, additionally, comprehensive, crucial, enhancing, exhibited, insights, notably, particularly, potential, findings, within
- Other named excess words: intricate, meticulous(ly), pivotal, realm, exhibited

Notable: in COVID years the excess words were content nouns (coronavirus, pandemic); post-ChatGPT they flipped to *style* words, which is what makes them an LLM signal.

---

## CATEGORY 5: Conclusion / Wrap-Up Phrases

1. In conclusion
2. In summary
3. To summarize
4. All in all
5. Overall
6. Ultimately
7. In the end
8. The future looks bright
9. Only time will tell
10. One thing is clear / One thing is certain
11. The possibilities are endless
12. Whether you're a [X] or a [Y]
13. Whether you're looking to…
14. As we navigate [this / the future / these changes]
15. As we move forward
16. At the end of the day
17. To put it simply
18. The key takeaway is / Here's the key takeaway
19. The most important thing is
20. It all comes down to
21. When all is said and done
22. Despite these challenges, [subject] continues to thrive
23. With its [X], [subject] continues to evolve
24. From a broader perspective
25. As we look to the future

---

## CATEGORY 6: Promotional / Inflated Phrases

1. Stands as a testament / a testament to
2. Rich tapestry / rich cultural heritage
3. Plays a vital / crucial / pivotal role
4. Nestled in the heart of / nestled
5. A beacon of
6. Boasts / boasting
7. Breathtaking
8. Must-visit / must-see
9. Stunning natural beauty / natural beauty
10. Leaves a lasting impression / indelible mark
11. Vibrant
12. Bustling
13. Renowned
14. Groundbreaking
15. Cutting-edge
16. World-class / best-in-class
17. State-of-the-art
18. Marks a pivotal moment / watershed moment / paradigm shift
19. A gateway to
20. Diverse array
21. Showcasing / showcases / exemplifies
22. Commitment to
23. Seamlessly connecting / seamless integration
24. Transformative experience
25. Unprecedented growth
26. Invaluable asset
27. Treasure trove
28. Thriving [ecosystem / community / startup]
29. Rich heritage / fabric of / canvas of
30. Serves as a bridge

---

## CATEGORY 7: Hedging & Chatbot Artifacts

The strongest single tells — these rarely appear in genuine human prose.

1. I hope this helps
2. As an AI language model
3. It's important to note
4. It's important to remember / important to consider
5. It's worth noting
6. Certainly!
7. Of course!
8. Absolutely!
9. Sure!
10. Great question!
11. I'm sorry, but
12. As of my last knowledge update
13. Based on the information provided
14. I do not have access to
15. While details are limited in available sources
16. Here's a possible… / Here's a breakdown
17. Let me know if (you need anything else / you'd like)
18. Feel free to reach out / feel free to ask
19. I hope this email finds you well
20. It is advisable
21. Could potentially / may eventually
22. To some extent
23. Experts believe / studies show (vague attribution)
24. Interestingly / Surprisingly / Notably
25. That being said

---

## CATEGORY 8: Rule-of-Three, False Ranges & Superficial "-ing" Analysis

### 8a. Rule of three + "from X to Y" false ranges

**The rule-of-three tendency.** LLMs compulsively group ideas in threes (the tricolon). A single tricolon is elegant; back-to-back tricolons signal a machine. AI also extends to four or five items, betraying pattern-filling rather than choosing. The tell is saturation, not any single instance.

**The "from X to Y" false range.** AI lists loosely related items as if they sit on a real spectrum. If you can't name a meaningful midpoint between X and Y, the range is fake. The cousin "whether it's X, Y, or Z" fakes exhaustive coverage.

Rule of three:
1. `[Adjective], [adjective], and [adjective].` — *"robust, scalable, and secure"*
2. `It [verb]s X, [verb]s Y, and [verb]s Z.` — *"improve performance, address bias, and expand applications"*
3. `[Noun phrase], [noun phrase], and [noun phrase].`
4. `Not only X, but also Y, and even Z.`
5. Ascending tricolon (short, longer, longest) — mimics "Life, liberty, and the pursuit of happiness"
6. `[Verb]. [Verb]. [Verb].` punchy standalone triple — *"Plan. Build. Scale."*
7. Three parallel sentences in a row, identical shape — *"Products solve problems. Platforms create worlds. Ecosystems endure."*

"From X to Y" / coverage faking:
8. `From [domain] to [domain]` — *"from healthcare to finance"*
9. `From [small thing] to [big thing]` — *"from startups to Fortune 500 companies"*
10. `From [concept] to [concept] to [concept]` — *"from innovation to implementation to cultural transformation"*
11. `Whether it's [X], [Y], or [Z]`
12. `Whether you're a [persona], a [persona], or a [persona]`
13. `Spanning everything from [X] to [Y]`
14. `Across industries, from [X] to [Y]`

### 8b. Superficial "-ing" analysis / editorializing clauses

AI tacks a trailing present-participle clause onto a factual sentence to inject unearned significance: "main clause, comma, -ing phrase." Instruction-tuned models use this 2-5x more than humans. Giveaway verbs: highlighting, underscoring, emphasizing, reflecting, showcasing, ensuring, demonstrating, cementing.

1. `…, highlighting the importance of [X].`
2. `…, underscoring the need for [X].`
3. `…, reflecting a broader trend toward [X].`
4. `…, showcasing its versatility.`
5. `…, emphasizing the role of [X].`
6. `…, ensuring [a smooth / seamless X].`
7. `…, demonstrating its commitment to [X].`
8. `…, contributing to the broader [history / development] of [X].`
9. `…, further enhancing its significance as a [dynamic hub].`
10. `…, cementing its position as [a leader in X].`
11. `…, paving the way for [X].`
12. `…, marking a significant milestone in [X].`
13. `…, solidifying its reputation as [X].`
14. `…, illustrating the impact of [X].`
15. `…, signaling a shift toward [X].`
16. `…, making it a [vital / essential] part of [X].`

---

## CATEGORY 9: Em-Dash & Formatting Tells

**Em dashes.** LLMs use the em dash (—) far more than nonprofessional human writing of the same genre, in slots where humans use commas, parentheses, colons, or hyphens. The signature use is "punched-up" sales emphasis: a parenthetical aside in paired dashes, or a single dash before a short punchy clause. (Note: GPT-5.1 was tuned to suppress this, so absence is no longer proof of human authorship.)

1. Em-dash overuse generally (many per piece vs. 2-3 in human text)
2. Paired parenthetical em dashes: `clause — aside — clause`
3. Single em dash before a punchy fragment: `…and that's the real problem — every time.`
4. Negative-parallelism dash: `It's not X — it's Y.`
5. Excessive bold: same key terms bolded repeatedly in one paragraph
6. Bullets that start with a **bolded inline header followed by a colon**, then explanation
7. Over-reliance on bulleted / numbered lists where prose is natural
8. Bullets appearing mid-essay in otherwise running prose
9. Title-case section headings (all main words capitalized)
10. Colon-heavy titles: `Topic: A Comprehensive Guide to Subtopic`
11. Emoji as bullet markers or section icons (✅ 🚀 🔑)
12. Explicit `Pros:` / `Cons:` (or Advantages / Disadvantages) blocks
13. Curly / smart quotes ("") with consistent Oxford commas; semicolons rare
14. Uniform paragraph length plus a "Key Takeaways" / "In Conclusion" wrap-up block

---

## CATEGORY 10: Cliché Metaphors & Collocations

1. Navigate the complexities / navigating the landscape
2. Unlock the potential / unlock the secrets
3. Unveil the secrets / unleash
4. In the realm of
5. The world of
6. A game changer / game-changing
7. At the forefront of
8. Pave the way (for)
9. Shed light on
10. The heart of
11. Tip of the iceberg
12. A double-edged sword
13. Stand the test of time
14. Delve into / delving into the intricacies
15. Dive into / let's dive in
16. Embark on a journey
17. Evolving landscape / ever-evolving
18. Rich tapestry / fabric of / canvas of
19. Serves as a bridge / a bridge across divides
20. Harness the power of
21. Elevate / take it to the next level
22. Revolutionize / shape the future / reshape
23. Push the envelope
24. Out-of-the-box thinking
25. Break down silos
26. Leverage synergies / leveraging data
27. Holistic approach
28. Streamline your workflow
29. A labyrinth of
30. The intersection of [X] and [Y]
31. At its core
32. A beacon of hope
33. The cornerstone of
34. Stands at the crossroads of

---

## Key Sources

- Wikipedia: [Signs of AI writing](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing)
- Kobak et al., "Delving into LLM-assisted writing in biomedical publications through excess vocabulary" — [Science Advances](https://www.science.org/doi/10.1126/sciadv.adt3813) / [PMC](https://pmc.ncbi.nlm.nih.gov/articles/PMC12219543/)
- The Conversation: [Why AI's stylistic negation "it's not X, it's Y" is annoying and doesn't work](https://theconversation.com/slanguage-why-ais-stylistic-negation-its-not-x-its-y-is-both-annoying-and-doesnt-work-278967)
- Colin Gorrie / Dead Language Society: [Why ChatGPT writes like that](https://www.deadlanguagesociety.com/p/rhetorical-analysis-ai)
- GC AI: [Contrastive Negation](https://gc.ai/blog/ai-writing-pattern-to-know-contrastive-negation) · refine.so: [Negative parallelism](https://refine.so/blog/negative-parallelism-ai-pattern)
- Bloomberry: [AI Writing Patterns: The Complete Database](https://www.bloomberry.ai/research/ai-writing-patterns)
- GPTZero: [Breaking Free from GPT's Rule of Three](https://gptzero.me/news/the-rule-of-three/) · Pangram Labs: [Spotting AI Writing Patterns](https://www.pangram.com/blog/comprehensive-guide-to-spotting-ai-writing-patterns)
- Reuters Institute: [How AI-generated prose diverges from human writing](https://reutersinstitute.politics.ox.ac.uk/news/how-ai-generated-prose-diverges-human-writing-and-why-it-matters)
- Grammarly: [Common AI Words](https://www.grammarly.com/blog/ai/common-ai-words/) · Undetectable.ai: [GPT phrases](https://undetectable.ai/blog/gpt-phrases/) · conorbronsdon/[avoid-ai-writing (GitHub)](https://github.com/conorbronsdon/avoid-ai-writing)
