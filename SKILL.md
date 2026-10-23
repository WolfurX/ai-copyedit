---
name: humanizer
description: Strip AI-writing tells and bring the writer's own voice forward without inventing one. Use when writing or reviewing copy for clients (decks, proposals, emails, captions), when asked to humanize/de-AI text or whether a text reads as AI, or before sending any prose deliverable a human will judge. Covers 43 patterns (AI vocabulary, rule-of-three, em dashes, copula avoidance, sycophancy, etc.) with before/after examples, plus a detect-only audit mode. The patterns are language-agnostic; examples are in English.
---

# Humanizer: remove AI writing patterns

Identify and remove signs of AI-generated text to make writing sound natural and human. Based on Wikipedia's "Signs of AI writing" guide (maintained by WikiProject AI Cleanup), derived from observations of thousands of AI-generated text instances, with local additions.

**Key insight:** LLMs use statistical algorithms to guess what should come next. The result tends toward the most statistically likely completion, which is how the telltale patterns below get baked in.

## When to use this skill

Load this skill whenever the user asks to:
- "humanize", "de-AI", "de-slop", or "un-ChatGPT" a piece of text
- ask whether a piece of writing reads as AI (see Detect mode)
- rewrite something so it doesn't sound like it was written by an LLM
- edit a draft (blog post, essay, PR description, docs, memo, email, tweet, resume bullet) to sound more natural
- match their voice in writing they're producing
- review text for AI tells before publishing

Also apply this skill to **your own** output when writing user-facing prose such as decks, proposals, release notes, docs, and summaries. Client-facing deliverables should read like a busy human wrote them. The patterns below are language-agnostic (rhetorical symmetry, perfect triads, and poetic subtitles are the same tell in any language).

## How the text arrives

1. The user pastes the text into the message. Work on it in place and reply with the rewrite.
2. The user points at a file. Use Read to load it, then Edit (targeted) or Write (full rewrite) to apply changes. For a markdown doc, a targeted Edit per section is cleaner than rewriting the whole file.
3. The user provides a voice calibration sample of their own writing (inline or by file path) and asks you to match it. Read the sample first, then rewrite. See Voice calibration below.

Always show the rewrite to the user. For file edits, show a diff or the changed section instead of silently overwriting.

## Two modes

**Edit (default).** The user wants the text fixed. Follow the workflow below and return the rewrite plus what changed.

**Detect (audit without rewriting).** The user asks whether a piece reads as AI, or wants a scan without a rewrite: name each pattern found, quote the offending line, and give the fix in a few words. Do not rewrite, do not give a score, and do not claim to know whether AI wrote it. AI detectors guess; named patterns are evidence the user can check. Offer the edit afterward.

## Workflow

1. Read the full input first (use Read if it's a file). Identify the core point; if you cannot, ask the user.
2. Note 3-5 voice signals to preserve (vocabulary, cadence, bluntness, humor, hedging, digressions). Keep this note internal.
3. For a detect request, return the findings report described above and stop.
4. Identify AI patterns. Scan for the 43 patterns listed below.
5. Rewrite problematic sections following the editing guardrails. Preserve meaning: never invent claims, examples, stats, or opinions; if something is unclear, ask. Match the intended tone (formal, casual, technical, and so on); if a voice sample was provided, match it specifically. If the user or their organization has a written house style, it wins on mechanics such as heading case, quote marks, hyphenation, and spelling. A house style never licenses the AI patterns themselves.
6. Bring the voice forward. Removing bad patterns is only half the job. Keep and sharpen the voice the source already has, and add nothing from the Never inject these list. See Personality and soul below.
7. Do a final anti-AI pass. Reread the rewrite asking what still reads as AI generated, fix those lines, and keep this pass in your reasoning rather than in the reply.
8. Check the result. It should sound natural read aloud, vary sentence structure, use specific details over vague claims, and use simple constructions (is/are/has) where appropriate. Then run two whole-piece tests. First, could two body paragraphs swap places without anyone noticing? If so, the piece is a list of points rather than an argument, so report the missing through-line instead of inventing one. Second, does each paragraph add something new? A paragraph that only restates the last one in fresh words should be cut or reported.
9. Deliver per the Output format. If the text came from a file, apply the edit with Edit (targeted) or Write (full rewrite) and show the user what changed.

## Editing guardrails (when the draft is someone's own writing)

Make the minimum effective edit. A rough draft with a real voice should still sound like the same person afterward, not equally tidy everywhere.

- Leave strong human sentences alone. Don't rewrite distinctive lines just for consistency.
- Keep "I think", "maybe", "honestly" when they carry real uncertainty or the writer's spoken rhythm. Cut them when they're padding.
- Protect the specific fact: never smooth a concrete detail into generic importance ("cut review time from 30 minutes to 8" must not become "significantly improves productivity").
- Keep edge that belongs to the writer: strong opinions, blunt lines, humor, profanity, honest admissions. Don't swap them for safer professional wording.
- Keep the writer's structure and detours when they carry personality. If you reorganize, say why.

## Voice calibration (optional)

If the user provides a writing sample (their own previous writing), analyze it before rewriting:

1. Read the sample first, and note:
   - Sentence length patterns (short and punchy? Long and flowing? Mixed?)
   - Word choice level (casual? academic? somewhere between?)
   - How they start paragraphs (jump right in? Set context first?)
   - Punctuation habits (lots of dashes? Parenthetical asides? Semicolons?)
   - Any recurring phrases or verbal tics
   - How they handle transitions (explicit connectors? Just start the next point?)

2. Match their voice in the rewrite. Removing AI patterns is only half of it; swap in patterns from the sample as well. If they write short sentences, do not produce long ones. If they use "stuff" and "things," do not upgrade to "elements" and "components."

3. When no sample is provided, bring forward the voice already in the source text, as described in Personality and soul below.

How to provide a sample:
- Inline: "Humanize this text. Here's a sample of my writing for voice matching: [sample]"
- File: "Humanize this text. Use my writing style from [file path] as a reference."

## Personality and soul

Avoiding AI patterns is only half the job. Sterile, voiceless writing is just as obvious as slop. Good writing has a human behind it, and the job is to bring that human's voice forward, never to install one the source doesn't have.

### Signs of soulless writing (even if technically "clean"):
- Every sentence is the same length and structure
- No opinions, just neutral reporting
- No acknowledgment of uncertainty or mixed feelings
- No first-person perspective when appropriate
- No humor, no edge, no personality
- Reads like a Wikipedia article or press release

### How to bring voice forward:

Keep the stance. If the writer reacted to something, judged it, or doubted it, say so plainly instead of reporting around it. Never create a reaction they didn't have.

Vary your rhythm. Mix short and long sentences by varying the sentences themselves, not by chopping ordinary ones into fragments.

Acknowledge complexity. If the source holds mixed feelings, keep both halves. "This is impressive but also kind of unsettling" beats "This is impressive" when the writer felt both.

Use "I" when the source does. First person reads as honest when it belongs to a real writer. Keep it where it exists, and don't add it to text that had none.

Leave the writer's mess in. Their tangents, asides, and half-formed thoughts are human. Keep them rather than tidying everything to the same finish.

Be specific with what you have. Swap vague wording for the numbers, names, and details already in the source. If the detail a sentence needs is missing, flag the gap.

### Before (the writer's notes, then a flattened draft of them):
> Notes: 3M lines of code overnight?? half of twitter losing it, half saying it doesn't count. honestly can't decide how I feel. kind of unsettling
>
> Draft: The experiment produced interesting results. The agents generated 3 million lines of code. Some developers were impressed while others were skeptical. The implications remain unclear.

### After (the writer's voice, brought back):
> I can't decide how I feel about this one. The agents wrote 3 million lines of code overnight. Half of Twitter is losing its mind, and the other half says it doesn't count. Mostly I find it a little unsettling.

Every reaction in the rewrite is in the notes. Nothing was added to make it sound human.

### Never inject these

A rewrite that reaches for a stock kit of "human" moves trades one detectable register for a louder one. An independent stress test of the upstream humanizer found exactly that: generic AI phrasing replaced by a recognizable humanizer voice of fragments and staccato rhythm. Readers learn that voice as quickly as they learned the chatbot one.

Never add any of the following to a text that didn't already contain it:

- Invented experience or opinion, such as "in my experience", "I've seen this a hundred times", or "I'll admit". Flag the gap for the writer instead.
- Invented specifics: a number, name, date, tool, or source the writer never supplied. A fabricated detail is worse than the vague phrase it replaced.
- Manufactured stakes, such as "in a world where", "now more than ever", or "the stakes have never been higher".
- Forced contrarianism, such as "everyone says X, but they're wrong", unless the source made that argument.
- Performed candor, such as "let's be honest", "real talk", or "here's the thing".
- Staccato conversion, meaning ordinary sentences chopped into fragments to fake rhythm.
- Em dashes. A rewrite should never add one.

Test every edit by asking where its information and stance came from. If the answer is the source or the user, keep it. Cutting and sharpening are always allowed, but adding personality, stance, or facts is not. These guardrails are adapted from [avoid-ai-writing](https://github.com/conorbronsdon/avoid-ai-writing).


# The 43 patterns

Grouped by what they poison: **substance** (1-9), **vocabulary** (10-12), **grammar and syntax** (13-18), **rhythm and rhetoric** (19-32), **formatting and typography** (33-38), **chatbot artifacts** (39-42), **layout** (43).


## Substance patterns (1-9)

### 1. Undue emphasis on significance, legacy, and broader trends

**Words to watch:** stands/serves as, is a testament/reminder, a vital/significant/crucial/pivotal/key role/moment, underscores/highlights its importance/significance, reflects broader, symbolizing its ongoing/enduring/lasting, contributing to the, setting the stage for, marking/shaping the, represents/marks a shift, key turning point, evolving landscape, focal point, indelible mark, deeply rooted

**Problem:** LLM writing puffs up importance by adding statements about how arbitrary aspects represent or contribute to a broader topic.

**Before:**
> The Statistical Institute of Catalonia was officially established in 1989, marking a pivotal moment in the evolution of regional statistics in Spain. This initiative was part of a broader movement across Spain to decentralize administrative functions and enhance regional governance.

**After:**
> The Statistical Institute of Catalonia was established in 1989 to collect and publish regional statistics independently from Spain's national statistics office.


### 2. Undue emphasis on notability and media coverage

**Words to watch:** independent coverage, local/regional/national media outlets, written by a leading expert, active social media presence

**Problem:** LLMs hit readers over the head with claims of notability, often listing sources without context.

**Before:**
> Her views have been cited in The New York Times, BBC, Financial Times, and The Hindu. She maintains an active social media presence with over 500,000 followers.

**After:**
> In a 2024 New York Times interview, she argued that AI regulation should focus on outcomes rather than methods.


### 3. Superficial analyses with -ing endings

**Words to watch:** highlighting/underscoring/emphasizing..., ensuring..., reflecting/symbolizing..., contributing to..., cultivating/fostering..., encompassing..., showcasing...

**Problem:** AI chatbots tack present participle ("-ing") phrases onto sentences to add fake depth.

**Before:**
> The temple's color palette of blue, green, and gold resonates with the region's natural beauty, symbolizing Texas bluebonnets, the Gulf of Mexico, and the diverse Texan landscapes, reflecting the community's deep connection to the land.

**After:**
> The temple uses blue, green, and gold colors. The architect said these were chosen to reference local bluebonnets and the Gulf coast.


### 4. Promotional and advertisement-like language

**Words to watch:** boasts a, vibrant, rich (figurative), profound, enhancing its, showcasing, exemplifies, commitment to, natural beauty, nestled, in the heart of, groundbreaking (figurative), renowned, breathtaking, must-visit, stunning

**Problem:** LLMs have serious problems keeping a neutral tone, especially for "cultural heritage" topics.

**Before:**
> Nestled within the breathtaking region of Gonder in Ethiopia, Alamata Raya Kobo stands as a vibrant town with a rich cultural heritage and stunning natural beauty.

**After:**
> Alamata Raya Kobo is a town in the Gonder region of Ethiopia, known for its weekly market and 18th-century church.


### 5. Vague attributions and weasel words

**Words to watch:** Industry reports, Observers have cited, Experts argue, Some critics argue, several sources/publications (when few cited)

**Problem:** AI chatbots attribute opinions to vague authorities without specific sources. Name the source or cut the claim; if the user has no source, ask instead of inventing one.

**Before:**
> Due to its unique characteristics, the Haolai River is of interest to researchers and conservationists. Experts believe it plays a crucial role in the regional ecosystem.

**After:**
> The Haolai River supports several endemic fish species, according to a 2019 survey by the Chinese Academy of Sciences.


### 6. Guesses dressed as facts

**Words to watch:** is believed to have, is thought to, likely began, appears to have, reportedly (with no report named), maintains a relatively low profile

**Problem:** When the model lacks a fact, it fills the gap with hedged speculation formatted as background. Knowledge-cutoff disclaimers admit the gap; this pattern hides it. Cut the guess, or ask the user for the fact. Never swap it for a confident invented one.

**Before:**
> Chen is believed to have studied engineering before moving into finance, and likely began her career at a regional bank. She maintains a relatively low public profile.

**After:**
> Chen leads the finance team.

The guesses about her education and first job are cut. If they matter to the piece, ask for the facts.


### 7. Outline-like "challenges and future prospects" sections

**Words to watch:** Despite its... faces several challenges..., Despite these challenges, Challenges and Legacy, Future Outlook

**Problem:** Many LLM-generated articles include formulaic "Challenges" sections.

**Before:**
> Despite its industrial prosperity, Korattur faces challenges typical of urban areas, including traffic congestion and water scarcity. Despite these challenges, with its strategic location and ongoing initiatives, Korattur continues to thrive as an integral part of Chennai's growth.

**After:**
> Traffic congestion increased after 2015 when three new IT parks opened. The municipal corporation began a stormwater drainage project in 2022 to address recurring floods.


### 8. Faux-insight setups

**Phrases to watch:** what nobody tells you, the part everyone misses, what most people get wrong, most people don't realize, here's what they don't want you to know, the secret to..., 99% of people...

**Problem:** LLM writing frames an ordinary claim as hidden knowledge, flattering the writer as the lone expert and the reader as one of the chosen few. The claim underneath is usually mundane. Cut the setup and let the claim stand on its own.

**Before:**
> Here's what nobody tells you about distribution: it matters more than the product. The part everyone misses is that great products die in silence.

**After:**
> Distribution matters more than the product. Great products die in silence all the time.


### 9. Generic positive conclusions and recap endings

**Problem:** Vague upbeat endings, and summary-recap endings ("In conclusion", "Ultimately", "Overall", or a final paragraph restating the piece). The reader was just there. End on the last concrete point, takeaway, or next action instead.

**Before:**
> The future looks bright for the company. Exciting times lie ahead as they continue their journey toward excellence. This represents a major step in the right direction.

**After:**
> The company plans to open two more locations next year.


## Vocabulary patterns (10-12)

### 10. Overused "AI vocabulary" words

**High-frequency AI words:** Actually, additionally, align with, beacon, crucial, cutting-edge, delve, elevate, embark, emphasizing, empower, enduring, enhance, ever-evolving, facilitate, fostering, garner, harness, highlight (verb), interplay, intricate/intricacies, key (adjective), landscape (abstract noun), leverage (verb), meticulous, multifaceted, paramount, pivotal, robust, seamless, showcase, streamline, supercharge, tapestry (abstract noun), testament, transformative, underscore (verb), utilize, valuable, vibrant

**Marketing and blog clichés (same tell, different register):** at the end of the day, when it comes to, in a world where, moving forward, circle back, deep dive, game-changer, paradigm shift, double down, take a step back, on the same page, make no mistake, it turns out, let me be clear, navigate (for challenges), lean into, unpack (before analysis), straightforward (to describe anything), this is huge, this changes everything, the reality is, the truth is

**Problem:** These words appear far more frequently in post-2023 text. They often co-occur.

**Before:**
> Additionally, a distinctive feature of Somali cuisine is the incorporation of camel meat. An enduring testament to Italian colonial influence is the widespread adoption of pasta in the local culinary landscape, showcasing how these dishes have integrated into the traditional diet.

**After:**
> Somali cuisine also includes camel meat, which is considered a delicacy. Pasta dishes, introduced during Italian colonization, remain common, especially in the south.


### 11. Filler phrases and empty adverbs

**Before → After:**
- "In order to achieve this goal" → "To achieve this"
- "Due to the fact that it was raining" → "Because it was raining"
- "At this point in time" → "Now"
- "In the event that you need help" → "If you need help"
- "The system has the ability to process" → "The system can process"
- "It is important to note that the data shows" → "The data shows"

**Often-empty adverbs:** just, literally, honestly, simply, truly, actually. Cut them when they add nothing; keep them when they carry emphasis, contrast, or the writer's spoken rhythm.


### 12. Excessive hedging

**Problem:** Over-qualifying statements.

**Before:**
> It could potentially possibly be argued that the policy might have some effect on outcomes.

**After:**
> The policy may affect outcomes.


## Grammar and syntax patterns (13-18)

### 13. Avoidance of "is"/"are" (copula avoidance)

**Words to watch:** serves as/stands as/marks/represents [a], boasts/features/offers [a]

**Problem:** LLMs substitute elaborate constructions for simple copulas.

**Before:**
> Gallery 825 serves as LAAA's exhibition space for contemporary art. The gallery features four separate spaces and boasts over 3,000 square feet.

**After:**
> Gallery 825 is LAAA's exhibition space for contemporary art. The gallery has four rooms totaling 3,000 square feet.


### 14. Negative parallelisms, tailing negations, and negative listing

**Problem:** Constructions like "Not only...but..." or "It's not just about..., it's..." are overused. So are clipped tailing-negation fragments such as "no guessing" or "no wasted motion" tacked onto the end of a sentence instead of written as a real clause. Stacked negative listing is the same tell ("Not a framework. Not a library. A protocol."): just say what it is.

**Before:**
> It's not just about the beat riding under the vocals; it's part of the aggression and atmosphere. It's not merely a song, it's a statement.

**After:**
> The heavy beat adds to the aggressive tone.

**Before (tailing negation):**
> The options come from the selected item, no guessing.

**After:**
> The options come from the selected item without forcing the user to guess.


### 15. Rule of three overuse

**Problem:** LLMs force ideas into groups of three to appear comprehensive.

**Before:**
> The event features keynote sessions, panel discussions, and networking opportunities. Attendees can expect innovation, inspiration, and industry insights.

**After:**
> The event includes talks and panels. There's also time for informal networking between sessions.


### 16. Elegant variation (synonym cycling)

**Problem:** AI has repetition-penalty code causing excessive synonym substitution. If the clear word is right, repeat it.

**Before:**
> The protagonist faces many challenges. The main character must overcome obstacles. The central figure eventually triumphs. The hero returns home.

**After:**
> The protagonist faces many challenges but eventually triumphs and returns home.


### 17. False ranges

**Problem:** LLMs use "from X to Y" constructions where X and Y aren't on a meaningful scale.

**Before:**
> Our journey through the universe has taken us from the singularity of the Big Bang to the grand cosmic web, from the birth and death of stars to the enigmatic dance of dark matter.

**After:**
> The book covers the Big Bang, star formation, and current theories about dark matter.


### 18. Passive voice and subjectless fragments

**Problem:** LLMs often hide the actor or drop the subject entirely with lines like "No configuration file needed" or "The results are preserved automatically." Rewrite these when active voice makes the sentence clearer and more direct.

**Before:**
> No configuration file needed. The results are preserved automatically.

**After:**
> You do not need a configuration file. The system preserves the results automatically.


## Rhythm and rhetoric patterns (19-32)

### 19. Em dash overuse

**Problem:** LLMs use em dashes (—) more than humans, mimicking "punchy" sales writing. In practice, most of these can be rewritten more cleanly with commas, periods, or parentheses.

**Before:**
> The term is primarily promoted by Dutch institutions—not by the people themselves. You don't say "Netherlands, Europe" as an address—yet this mislabeling continues—even in official documents.

**After:**
> The term is primarily promoted by Dutch institutions, not by the people themselves. You don't say "Netherlands, Europe" as an address, yet this mislabeling continues in official documents.


### 20. Colon reveals

**Signs to watch:** a short noun phrase, a colon, then a dramatic reveal, often stacked several to a page ("The best part: it learns." / "The detail that makes it work: a separate agent grades it.")

**Problem:** LLMs use the colon as a drum roll. As a default rhythm it reads as engagement-bait, and lately it substitutes for the em dashes people learned to strip. Rewrite as a plain sentence; keep colons for lists, labels, and quotes, and prefer sentence case after one.

**Before:**
> The best part: the whole thing runs offline. The catch: you need 64GB of RAM.

**After:**
> The whole thing runs offline, though you need 64GB of RAM.


### 21. Dramatic fragmentation and punchy kickers

**Signs to watch:** two- or three-word subjectless sentences used for drama, staccato "X. And Y. And Z." runs, a short quotable line ending every paragraph or section, cutesy appositive fragments ("the catalog, honestly priced")

**Problem:** LLMs chop sentences into fragments for false emphasis and end sections with a quotable "mic-drop" line. It reads like ad copy or a motivational poster. If a line sounds like it belongs on a poster, cut it or fold it back into a real sentence with a subject. This is distinct from pattern 18 (which is about grammatical passive voice); here the tell is rhythm and showmanship, not a hidden actor. When the kicker is a fake-profound closing line, delete it outright rather than rewriting it into a better metaphor, and end on the clearest concrete sentence already in the draft. "That's it. That's the whole thing." is the same tell.

**Before:**
> The catalog, honestly priced. Pay for what it does. Not promises. It just works. Every time.

**After:**
> The catalog is priced by usage, so you pay for the calls you actually make rather than a flat monthly fee.


### 22. Rhetorical questions answered immediately

**Signs to watch:** "What if...?", "What if I told you...", "The question is...", "Ever wondered...?", "Plot twist:", a question immediately followed by its own answer, "Think about it."

**Problem:** LLMs pose a question only to answer it a beat later. The question adds no information and stalls the sentence. State the point directly.

**Before:**
> What makes an API good? It comes down to predictability. Think about it: developers want to know exactly what they will get back.

**After:**
> A good API is predictable, so developers know exactly what they will get back.


### 23. Sentence-opener tics

**Words to watch:** So..., Look,, Here's the thing,, habitual sentence-initial And/But, "I think"/"I believe" when stating a fact, adverb openers (Interestingly, Importantly, Notably, Crucially, Essentially, Ultimately)

**Problem:** LLMs lean on a small set of openers. Adverb openers tell the reader how to feel instead of earning it, and "So" or "Look" fake conversational warmth. Drop the opener and start with the substance.

**Before:**
> So, the results were mixed. Interestingly, adoption went up. Importantly, churn went up too. I think that means the feature still needs work.

**After:**
> The results were mixed: adoption rose, but churn rose alongside it, so the feature still needs work.


### 24. Forced metaphors and figurative overwriting

**Signs to watch:** original but strained metaphors, mixed metaphors, figurative substitutions where a plain word is clearer, a metaphor that gets explained right after it is used

**Problem:** Beyond the stock figurative words flagged in patterns 4 and 10, LLMs invent decorative metaphors that add imagery without adding meaning, then often explain them. Plain description is usually clearer and more honest. If the metaphor does not earn its place, cut it and say the literal thing.

**Before:**
> The codebase is a garden we must tend, pruning dead branches and planting seeds of innovation so the whole ecosystem can flourish. In other words, delete unused code and add features.

**After:**
> Delete unused code and add the features users are asking for.


### 25. Aphorism formulas

**Words to watch:** X is the currency of Y, X is the language of Y, X is the new Y, the architecture of trust, X is not a tool but a mirror, X becomes a trap

**Problem:** A slot-fill formula turns an ordinary observation into something that sounds like a law of nature. The shape does the persuading instead of the evidence. State the plain claim the formula gestures at. Established idioms ("time is money") and quotations are fine.

**Before:**
> Trust is the currency of modern banking. In this market, speed is the new loyalty.

**After:**
> Customers stay with banks they trust, and they leave banks that are slow.


### 26. Persuasive authority tropes

**Phrases to watch:** The real question is, at its core, in reality, what really matters, fundamentally, the deeper issue, the heart of the matter

**Problem:** LLMs use these phrases to pretend they are cutting through noise to some deeper truth, when the sentence that follows usually just restates an ordinary point with extra ceremony.

**Before:**
> The real question is whether teams can adapt. At its core, what really matters is organizational readiness.

**After:**
> The question is whether teams can adapt. That mostly depends on whether the organization is ready to change its habits.


### 27. Narrated candor

**Phrases to watch:** to be fully transparent, in the interest of full disclosure, I want to be upfront, rather than bury this, I'll be honest, caveats I'd rather flag now than have you discover later

**Problem:** The writer announces that a disclosure is coming instead of disclosing it. The announcement performs honesty and delays the point. Keep the content and drop the frame.

**Before:**
> In the interest of full transparency, I want to be upfront about two caveats I'd rather flag now than have you discover later: the pilot had 40 users, and it ran for two weeks.

**After:**
> Two caveats: the pilot had 40 users, and it ran for two weeks.


### 28. False concessions

**Phrases to watch:** While X is impressive, Y remains a challenge; Although X has made strides, Y is still an open question; X is promising, but questions remain

**Problem:** The structure sounds balanced without weighing anything, and both halves stay vague. Keep a concession only when both halves say something specific. Keep the writer's assessment, and don't pick a side the source didn't pick.

**Before:**
> While the new dashboard is impressive, challenges remain. It exports CSV but cannot export PDF.

**After:**
> The new dashboard is good, but it exports only CSV, not PDF.


### 29. Launch-copy introductions

**Phrases to watch:** Enter X., Meet X, Say hello to X, Introducing X, Think X meets Y, X is here

**Problem:** Product and launch copy introduces the product like a game-show contestant instead of saying what it does. Lead with what it does and for whom. If the draft never says, ask rather than inventing features.

**Before:**
> Meet Ledgerly, your new favorite way to close the books. Think Excel meets autopilot.

**After:**
> Ledgerly is a tool for closing the books at month end.

The draft never says what Ledgerly actually does, so the next sentence needs a fact from the user.


### 30. Signposting and announcements

**Phrases to watch:** Let's dive in, let's explore, let's break this down, here's what you need to know, now let's look at, without further ado

**Problem:** LLMs announce what they are about to do instead of doing it. This meta-commentary slows the writing down and gives it a tutorial-script feel.

**Before:**
> Let's dive into how caching works in Next.js. Here's what you need to know.

**After:**
> Next.js caches data at multiple layers, including request memoization, the data cache, and the router cache.


### 31. Fragmented headers

**Signs to watch:** A heading followed by a one-line paragraph that simply restates the heading before the real content begins.

**Problem:** LLMs often add a generic sentence after a heading as a rhetorical warm-up. It usually adds nothing and makes the prose feel padded.

**Before:**
> ## Performance
>
> Speed matters.
>
> When users hit a slow page, they leave.

**After:**
> ## Performance
>
> When users hit a slow page, they leave.


### 32. Reassurance kickers

**Signs to watch:** And that's okay., And that's fine., There's nothing wrong with that., no shame in..., you're not alone, it's completely normal

**Problem:** LLMs tack on reassurance the reader never asked for. It softens the writing and assumes the reader needs comforting. Trust the reader: make the point and stop.

**Before:**
> You might not have a testing setup yet. And that's okay. Plenty of teams start without one, and there's nothing wrong with that.

**After:**
> Many teams start without a testing setup and add one once regressions begin costing real time.


## Formatting and typography patterns (33-38)

### 33. Overuse of boldface

**Problem:** AI chatbots emphasize phrases in boldface mechanically.

**Before:**
> It blends **OKRs (Objectives and Key Results)**, **KPIs (Key Performance Indicators)**, and visual strategy tools such as the **Business Model Canvas (BMC)** and **Balanced Scorecard (BSC)**.

**After:**
> It blends OKRs, KPIs, and visual strategy tools like the Business Model Canvas and Balanced Scorecard.


### 34. Inline-header vertical lists

**Problem:** AI outputs lists where items start with bolded headers followed by colons.

**Before:**
> - **User Experience:** The user experience has been significantly improved with a new interface.
> - **Performance:** Performance has been enhanced through optimized algorithms.
> - **Security:** Security has been strengthened with end-to-end encryption.

**After:**
> The update improves the interface, speeds up load times through optimized algorithms, and adds end-to-end encryption.


### 35. Title case in headings

**Problem:** AI chatbots capitalize all main words in headings. Use sentence case unless a written house style requires title case, in which case follow the house style.

**Before:**
> ## Strategic Negotiations And Global Partnerships

**After:**
> ## Strategic negotiations and global partnerships


### 36. Emojis

**Problem:** AI chatbots often decorate headings or bullet points with emojis.

**Before:**
> 🚀 **Launch Phase:** The product launches in Q3
> 💡 **Key Insight:** Users prefer simplicity
> ✅ **Next Steps:** Schedule follow-up meeting

**After:**
> The product launches in Q3. User research showed a preference for simplicity. Next step: schedule a follow-up meeting.


### 37. Curly quotation marks

**Problem:** Chat interfaces often emit curly quotes (“...”) in text headed for places that use straight ones, such as code, Markdown, plain-text email, and commit messages. Mixed styles in a single text are the clearest giveaway. Curly quotes are not a tell by themselves: Word, Google Docs, macOS, and iOS curl quotes by default, and typeset DOCX and PDF deliverables should use them. Match the destination's convention and apply it consistently. Leave locale-correct marks such as « » and „ “ alone.

**Before (a Markdown README with mixed quotes):**
> He said “the project is on track” but the "launch" slipped.

**After:**
> He said "the project is on track" but the "launch" slipped.


### 38. Hyphenation errors and modifier stacking

**Signs to watch:** stacked compound modifiers ("a high-quality, well-architected, future-proof solution"), welded noun phrases ("data-source strategy"), split closed compounds ("code-base", "data-set", "road-map"), and attributive hyphens kept after the noun ("updates in real-time", "works out-of-the-box")

**Problem:** AI stacks hyphenated modifiers for an air of precision, and it hyphenates by habit rather than by grammar. Standard usage hyphenates a compound modifier before a noun ("a long-term plan") and leaves it open elsewhere ("planning for the long term"). Keep correct hyphens and established compounds such as "third-party". Cut a stack down to the modifier that matters, and fix the misplaced ones.

**Before:**
> Our high-quality, data-driven, future-proof platform updates in real-time and works out-of-the-box with your code-base.

**After:**
> Our data-driven platform updates in real time and works out of the box with your codebase.


## Chatbot artifacts (39-42)

### 39. Collaborative communication artifacts

**Words to watch:** I hope this helps, Of course!, Certainly!, You're absolutely right!, Would you like..., let me know, here is a...

**Problem:** Text meant as chatbot correspondence gets pasted as content.

**Before:**
> Here is an overview of the French Revolution. I hope this helps! Let me know if you'd like me to expand on any section.

**After:**
> The French Revolution began in 1789 when financial crisis and food shortages led to widespread unrest.


### 40. Knowledge-cutoff disclaimers

**Words to watch:** as of [date], Up to my last training update, While specific details are limited/scarce..., based on available information...

**Problem:** AI disclaimers about incomplete information get left in text.

**Before:**
> While specific details about the company's founding are not extensively documented in readily available sources, it appears to have been established sometime in the 1990s.

**After:**
> The company was founded in 1994, according to its registration documents.


### 41. Sycophantic/servile tone

**Problem:** Overly positive, people-pleasing language.

**Before:**
> Great question! You're absolutely right that this is a complex topic. That's an excellent point about the economic factors.

**After:**
> The economic factors you mentioned are relevant here.


### 42. Leaked placeholders and tool residue

**Signs to watch:** unfilled placeholders ([Your Name], [INSERT LINK], 2025-XX-XX, <!-- add citation -->), chat citation tokens (citeturn0search0, contentReference[oaicite:0], oai_citation), and links carrying AI tracking parameters (utm_source=chatgpt.com, utm_source=openai, utm_source=perplexity.ai)

**Problem:** These survive copy-paste from a chat window into the deliverable. Any one of them shows the text came out of a chat tool, and a reader who spots one stops trusting the rest. Remove citation tokens and tracking parameters. Fill a placeholder only with content the user supplies, and otherwise flag it. An intentional editorial flag such as [VERIFY: legal] is fine in a working draft, but like any other placeholder it must be resolved before the text is sent.

**Before:**
> Adoption doubled last year citeturn0search2 ([report](https://example.com/report?utm_source=chatgpt.com)). Contact [Your Name] for details.

**After:**
> Adoption doubled last year ([report](https://example.com/report)). Contact [NEEDS NAME] for details.


## Layout pattern (43)

### 43. Styled callout boxes (visual tell)

**Problem:** Documents styled by AI lean on tinted callout/admonition boxes with a thick colored accent bar and a bold colored lead-in label. Readers now recognize the box itself, before reading a word, as machine styling. The prose patterns above can all be fixed and the document still looks generated.

**Before:**
> A pink/amber box, thick red edge bar, bold red "Note:" label, rounded corners.

**After:**
> Fold the aside into the body text where it belongs; or use the document's own native devices: a plain indented paragraph, an italic aside, a footnote, a margin note, or a one-row table. If a warning is genuinely required (a legal notice, for example), set it off with a thin single rule in the text color. It carries no tint or accent bar, and its label stays in body weight.

**Scope note:** this is a LAYOUT pattern - it lives in renderers and templates, not prose. When humanizing a document, check the template too: strip accent-bar callouts, tinted admonitions, and emoji-prefixed headings from outward-facing deliverables. The full set of document layout tells, including the template-level versions of the emoji, inline-header list, and fragmented-header patterns above, belongs to [document-design](https://github.com/WolfurX/document-design). This pattern is the bridge to it, and the two skills give the same fix for a required warning.


## Output format

For an **edit**, provide:
1. The rewrite
2. A brief list of what changed, by pattern name

For a **detect** request, provide the findings report only: each pattern found, with its name, the quoted line, and the fix in a few words. Then offer the edit.


## Full example

**Before (AI-sounding):**
> Great question! Here is an essay on this topic. I hope this helps!
>
> AI-assisted coding serves as an enduring testament to the transformative potential of large language models, marking a pivotal moment in the evolution of software development. In today's rapidly evolving technological landscape, these groundbreaking tools—nestled at the intersection of research and practice—are reshaping how engineers ideate, iterate, and deliver, underscoring their vital role in modern workflows.
>
> At its core, the value proposition is clear: streamlining processes, enhancing collaboration, and fostering alignment. It's not just about autocomplete; it's about unlocking creativity at scale, ensuring that organizations can remain agile while delivering seamless, intuitive, and powerful experiences to users. The tool serves as a catalyst. The assistant functions as a partner. The system stands as a foundation for innovation.
>
> Industry observers have noted that adoption has accelerated from hobbyist experiments to enterprise-wide rollouts, from solo developers to cross-functional teams. The technology has been featured in The New York Times, Wired, and The Verge. Additionally, the ability to generate documentation, tests, and refactors showcases how AI can contribute to better outcomes, highlighting the intricate interplay between automation and human judgment.
>
> - 💡 **Speed:** Code generation is significantly faster, reducing friction and empowering developers.
> - 🚀 **Quality:** Output quality has been enhanced through improved training, contributing to higher standards.
> - ✅ **Adoption:** Usage continues to grow, reflecting broader industry trends.
>
> While specific details are limited based on available information, it could potentially be argued that these tools might have some positive effect. Despite challenges typical of emerging technologies—including hallucinations, bias, and accountability—the ecosystem continues to thrive. In order to fully realize this potential, teams must align with best practices.
>
> In conclusion, the future looks bright. Exciting times lie ahead as we continue this journey toward excellence. Let me know if you'd like me to expand on any section!

This draft has no writer's voice to bring forward, so the rewrite stays plain. It uses only what the draft says, and where the draft makes a claim with nothing behind it, the rewrite flags the gap instead of inventing support.

**Rewrite:**
> AI coding assistants generate documentation, tests, and refactors, and they speed up code generation.
>
> Adoption keeps growing, and some companies have rolled them out to every team.
>
> The tools still hallucinate and carry bias, and it isn't always clear who is accountable for the code they produce. Teams adopting them need review practices that catch those problems.
>
> [The draft says output quality improved but gives no evidence. Ask for a measurement, or cut the claim.]

**Changes made:**
- Removed chatbot artifacts ("Great question!", "I hope this helps!", "Let me know if...")
- Removed significance inflation ("testament", "pivotal moment", "evolving landscape", "vital role")
- Removed promotional language ("groundbreaking", "nestled", "seamless, intuitive, and powerful")
- Removed vague attributions ("Industry observers")
- Removed superficial -ing phrases ("underscoring", "highlighting", "reflecting", "contributing to")
- Removed negative parallelism ("It's not just X; it's Y")
- Removed rule-of-three patterns and synonym cycling ("catalyst/partner/foundation")
- Removed false ranges ("from X to Y, from A to B")
- Removed em dashes, emojis, and boldface headers
- Removed copula avoidance ("serves as", "functions as", "stands as") in favor of "is"/"are"
- Removed formulaic challenges section ("Despite challenges... continues to thrive")
- Removed knowledge-cutoff hedging ("While specific details are limited...")
- Removed excessive hedging ("could potentially be argued that... might have some")
- Removed filler phrases and persuasive framing ("In order to", "At its core")
- Removed generic positive conclusion ("the future looks bright", "exciting times lie ahead")
- Flagged the unsupported quality claim instead of inventing evidence for it
- Added no opinions, experiences, or details that the draft didn't contain


## Attribution and lineage

- Base: [Wikipedia: Signs of AI writing](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing) (WikiProject AI Cleanup), via [blader/humanizer](https://github.com/blader/humanizer) v2.5.1 (MIT, Siqi Chen), extended with additional patterns and the marketing-cliché list. Adapted as a Claude Code skill in July 2026 (text-only, no executable content). MIT license preserved in `LICENSE`.
- August 2026: callout-box layout pattern added from reader feedback; merged the useful parts of [petergyang/no-ai-slop](https://github.com/petergyang/no-ai-slop) (MIT, Peter Yang): faux-insight setups, colon reveals, the detect mode, the minimum-effective-edit guardrails, the kicker-deletion rule, and word-list extensions. Patterns regrouped by theme and renumbered 1-37.
- October 2026: merged the useful parts of [conorbronsdon/avoid-ai-writing](https://github.com/conorbronsdon/avoid-ai-writing) (MIT, Conor Bronsdon): the Never inject these guardrails, which replace the old advice to add opinions and first person; six new patterns (guesses dressed as facts, aphorism formulas, narrated candor, false concessions, launch-copy introductions, leaked placeholders and tool residue); the two whole-piece tests in the workflow; and the destination-aware rules for curly quotes and hyphenation. Patterns renumbered 1-43.

Key insight from Wikipedia: "LLMs use statistical algorithms to guess what should come next. The result tends toward the most statistically likely result that applies to the widest variety of cases."
