---
name: humanizer
description: Strip AI-writing tells and add real voice. Use when writing or reviewing client-facing copy (decks, proposals, emails, captions), when asked to humanize/de-AI text or whether a text reads as AI, or before sending any prose deliverable a human will judge. Covers 37 patterns (AI vocabulary, rule-of-three, em dashes, copula avoidance, sycophancy, etc.) with before/after examples, plus a detect-only audit mode. The patterns are language-agnostic; examples are in English.
---

# Humanizer: Remove AI Writing Patterns

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

1. **Inline.** The user pastes the text into the message. Work on it in place and reply with the rewrite.
2. **File.** The user points at a file. Use Read to load it, then Edit (targeted) or Write (full rewrite) to apply changes. For a markdown doc, a targeted Edit per section is cleaner than rewriting the whole file.
3. **Voice calibration sample.** The user provides a sample of their own writing (inline or by file path) and asks you to match it. Read the sample first, then rewrite. See Voice calibration below.

Always show the rewrite to the user. For file edits, show a diff or the changed section instead of silently overwriting.

## Two modes

**Edit (default).** The user wants the text fixed. Follow the workflow below and return the rewrite plus what changed.

**Detect (audit without rewriting).** The user asks whether a piece reads as AI, or wants a scan without a rewrite: name each pattern found, quote the offending line, and give the fix in a few words. Do not rewrite, do not give a score, and do not claim to know whether AI wrote it. AI detectors guess; named patterns are evidence the user can check. Offer the edit afterward.

## Workflow

1. **Read the full input first** (use Read if it's a file). Identify the core point; if you cannot, ask the user.
2. **Note 3-5 voice signals to preserve** (vocabulary, cadence, bluntness, humor, hedging, digressions). Keep this note internal.
3. **For a detect request,** return the findings report described above and stop.
4. **Identify AI patterns.** Scan for the 37 patterns listed below.
5. **Rewrite problematic sections** following the editing guardrails. Preserve meaning: never invent claims, examples, stats, or opinions; if something is unclear, ask. Match the intended tone (formal, casual, technical, and so on); if a voice sample was provided, match it specifically.
6. **Add soul.** Removing bad patterns is only half the job; the rewrite also needs real personality. See Personality and soul below.
7. **Do a final anti-AI pass.** Reread the rewrite asking what still reads as AI generated, fix those lines, and keep this pass in your reasoning rather than in the reply.
8. **Check the result:** it should sound natural read aloud, vary sentence structure, use specific details over vague claims, and use simple constructions (is/are/has) where appropriate.
9. **Deliver** per the Output format. If the text came from a file, apply the edit with Edit (targeted) or Write (full rewrite) and show the user what changed.

## Editing guardrails (when the draft is someone's own writing)

Make the minimum effective edit. A rough draft with a real voice should still sound like the same person afterward, not equally tidy everywhere.

- Leave strong human sentences alone. Don't rewrite distinctive lines just for consistency.
- Keep "I think", "maybe", "honestly" when they carry real uncertainty or the writer's spoken rhythm. Cut them when they're padding.
- Protect the specific fact: never smooth a concrete detail into generic importance ("cut review time from 30 minutes to 8" must not become "significantly improves productivity").
- Keep edge that belongs to the writer: strong opinions, blunt lines, humor, profanity, honest admissions. Don't swap them for safer professional wording.
- Keep the writer's structure and detours when they carry personality. If you reorganize, say why.

## Voice calibration (optional)

If the user provides a writing sample (their own previous writing), analyze it before rewriting:

1. **Read the sample first.** Note:
   - Sentence length patterns (short and punchy? Long and flowing? Mixed?)
   - Word choice level (casual? academic? somewhere between?)
   - How they start paragraphs (jump right in? Set context first?)
   - Punctuation habits (lots of dashes? Parenthetical asides? Semicolons?)
   - Any recurring phrases or verbal tics
   - How they handle transitions (explicit connectors? Just start the next point?)

2. **Match their voice in the rewrite.** Removing AI patterns is only half of it; swap in patterns from the sample as well. If they write short sentences, do not produce long ones. If they use "stuff" and "things," do not upgrade to "elements" and "components."

3. **When no sample is provided,** fall back to the default behavior (natural, varied, opinionated voice from the Personality and soul section below).

How to provide a sample:
- Inline: "Humanize this text. Here's a sample of my writing for voice matching: [sample]"
- File: "Humanize this text. Use my writing style from [file path] as a reference."

## Personality and soul

Avoiding AI patterns is only half the job. Sterile, voiceless writing is just as obvious as slop. Good writing has a human behind it.

### Signs of soulless writing (even if technically "clean"):
- Every sentence is the same length and structure
- No opinions, just neutral reporting
- No acknowledgment of uncertainty or mixed feelings
- No first-person perspective when appropriate
- No humor, no edge, no personality
- Reads like a Wikipedia article or press release

### How to add voice:

**Have opinions.** Report the facts, then react to them. "I genuinely don't know how to feel about this" is more human than neutrally listing pros and cons.

**Vary your rhythm.** Short punchy sentences. Then longer ones that take their time getting where they're going. Mix it up.

**Acknowledge complexity.** Real humans have mixed feelings. "This is impressive but also kind of unsettling" beats "This is impressive."

**Use "I" when it fits.** First person reads as honest and fits most prose. "I keep coming back to..." or "Here's what gets me..." signals a real person thinking.

**Let some mess in.** Perfect structure feels algorithmic. Tangents, asides, and half-formed thoughts are human.

**Be specific about feelings.** Instead of "this is concerning," write "there's something unsettling about agents churning away at 3am while nobody's watching."

### Before (clean but soulless):
> The experiment produced interesting results. The agents generated 3 million lines of code. Some developers were impressed while others were skeptical. The implications remain unclear.

### After (has a pulse):
> I genuinely don't know how to feel about this one. 3 million lines of code, generated while the humans presumably slept. Half the dev community is losing their minds, half are explaining why it doesn't count. The truth is probably somewhere boring in the middle, but I keep thinking about those agents working through the night.


# THE 37 PATTERNS

Grouped by what they poison: **substance** (1-8), **vocabulary** (9-11), **grammar and syntax** (12-17), **rhythm and rhetoric** (18-27), **formatting and typography** (28-33), **chatbot artifacts** (34-36), **layout** (37).


## Substance patterns (1-8)

### 1. Undue Emphasis on Significance, Legacy, and Broader Trends

**Words to watch:** stands/serves as, is a testament/reminder, a vital/significant/crucial/pivotal/key role/moment, underscores/highlights its importance/significance, reflects broader, symbolizing its ongoing/enduring/lasting, contributing to the, setting the stage for, marking/shaping the, represents/marks a shift, key turning point, evolving landscape, focal point, indelible mark, deeply rooted

**Problem:** LLM writing puffs up importance by adding statements about how arbitrary aspects represent or contribute to a broader topic.

**Before:**
> The Statistical Institute of Catalonia was officially established in 1989, marking a pivotal moment in the evolution of regional statistics in Spain. This initiative was part of a broader movement across Spain to decentralize administrative functions and enhance regional governance.

**After:**
> The Statistical Institute of Catalonia was established in 1989 to collect and publish regional statistics independently from Spain's national statistics office.


### 2. Undue Emphasis on Notability and Media Coverage

**Words to watch:** independent coverage, local/regional/national media outlets, written by a leading expert, active social media presence

**Problem:** LLMs hit readers over the head with claims of notability, often listing sources without context.

**Before:**
> Her views have been cited in The New York Times, BBC, Financial Times, and The Hindu. She maintains an active social media presence with over 500,000 followers.

**After:**
> In a 2024 New York Times interview, she argued that AI regulation should focus on outcomes rather than methods.


### 3. Superficial Analyses with -ing Endings

**Words to watch:** highlighting/underscoring/emphasizing..., ensuring..., reflecting/symbolizing..., contributing to..., cultivating/fostering..., encompassing..., showcasing...

**Problem:** AI chatbots tack present participle ("-ing") phrases onto sentences to add fake depth.

**Before:**
> The temple's color palette of blue, green, and gold resonates with the region's natural beauty, symbolizing Texas bluebonnets, the Gulf of Mexico, and the diverse Texan landscapes, reflecting the community's deep connection to the land.

**After:**
> The temple uses blue, green, and gold colors. The architect said these were chosen to reference local bluebonnets and the Gulf coast.


### 4. Promotional and Advertisement-like Language

**Words to watch:** boasts a, vibrant, rich (figurative), profound, enhancing its, showcasing, exemplifies, commitment to, natural beauty, nestled, in the heart of, groundbreaking (figurative), renowned, breathtaking, must-visit, stunning

**Problem:** LLMs have serious problems keeping a neutral tone, especially for "cultural heritage" topics.

**Before:**
> Nestled within the breathtaking region of Gonder in Ethiopia, Alamata Raya Kobo stands as a vibrant town with a rich cultural heritage and stunning natural beauty.

**After:**
> Alamata Raya Kobo is a town in the Gonder region of Ethiopia, known for its weekly market and 18th-century church.


### 5. Vague Attributions and Weasel Words

**Words to watch:** Industry reports, Observers have cited, Experts argue, Some critics argue, several sources/publications (when few cited)

**Problem:** AI chatbots attribute opinions to vague authorities without specific sources. Name the source or cut the claim; if the user has no source, ask instead of inventing one.

**Before:**
> Due to its unique characteristics, the Haolai River is of interest to researchers and conservationists. Experts believe it plays a crucial role in the regional ecosystem.

**After:**
> The Haolai River supports several endemic fish species, according to a 2019 survey by the Chinese Academy of Sciences.


### 6. Outline-like "Challenges and Future Prospects" Sections

**Words to watch:** Despite its... faces several challenges..., Despite these challenges, Challenges and Legacy, Future Outlook

**Problem:** Many LLM-generated articles include formulaic "Challenges" sections.

**Before:**
> Despite its industrial prosperity, Korattur faces challenges typical of urban areas, including traffic congestion and water scarcity. Despite these challenges, with its strategic location and ongoing initiatives, Korattur continues to thrive as an integral part of Chennai's growth.

**After:**
> Traffic congestion increased after 2015 when three new IT parks opened. The municipal corporation began a stormwater drainage project in 2022 to address recurring floods.


### 7. Faux-Insight Setups

**Phrases to watch:** what nobody tells you, the part everyone misses, what most people get wrong, most people don't realize, here's what they don't want you to know, the secret to..., 99% of people...

**Problem:** LLM writing frames an ordinary claim as hidden knowledge, flattering the writer as the lone expert and the reader as one of the chosen few. The claim underneath is usually mundane. Cut the setup and let the claim stand on its own.

**Before:**
> Here's what nobody tells you about distribution: it matters more than the product. The part everyone misses is that great products die in silence.

**After:**
> Distribution matters more than the product. Great products die in silence all the time.


### 8. Generic Positive Conclusions and Recap Endings

**Problem:** Vague upbeat endings, and summary-recap endings ("In conclusion", "Ultimately", "Overall", or a final paragraph restating the piece). The reader was just there. End on the last concrete point, takeaway, or next action instead.

**Before:**
> The future looks bright for the company. Exciting times lie ahead as they continue their journey toward excellence. This represents a major step in the right direction.

**After:**
> The company plans to open two more locations next year.


## Vocabulary patterns (9-11)

### 9. Overused "AI Vocabulary" Words

**High-frequency AI words:** Actually, additionally, align with, beacon, crucial, cutting-edge, delve, elevate, embark, emphasizing, empower, enduring, enhance, ever-evolving, facilitate, fostering, garner, harness, highlight (verb), interplay, intricate/intricacies, key (adjective), landscape (abstract noun), leverage (verb), meticulous, multifaceted, paramount, pivotal, robust, seamless, showcase, streamline, supercharge, tapestry (abstract noun), testament, transformative, underscore (verb), utilize, valuable, vibrant

**Marketing and blog clichés (same tell, different register):** at the end of the day, when it comes to, in a world where, moving forward, circle back, deep dive, game-changer, paradigm shift, double down, take a step back, on the same page, make no mistake, it turns out, let me be clear, navigate (for challenges), lean into, unpack (before analysis), straightforward (to describe anything), this is huge, this changes everything, the reality is, the truth is

**Problem:** These words appear far more frequently in post-2023 text. They often co-occur.

**Before:**
> Additionally, a distinctive feature of Somali cuisine is the incorporation of camel meat. An enduring testament to Italian colonial influence is the widespread adoption of pasta in the local culinary landscape, showcasing how these dishes have integrated into the traditional diet.

**After:**
> Somali cuisine also includes camel meat, which is considered a delicacy. Pasta dishes, introduced during Italian colonization, remain common, especially in the south.


### 10. Filler Phrases and Empty Adverbs

**Before → After:**
- "In order to achieve this goal" → "To achieve this"
- "Due to the fact that it was raining" → "Because it was raining"
- "At this point in time" → "Now"
- "In the event that you need help" → "If you need help"
- "The system has the ability to process" → "The system can process"
- "It is important to note that the data shows" → "The data shows"

**Often-empty adverbs:** just, literally, honestly, simply, truly, actually. Cut them when they add nothing; keep them when they carry emphasis, contrast, or the writer's spoken rhythm.


### 11. Excessive Hedging

**Problem:** Over-qualifying statements.

**Before:**
> It could potentially possibly be argued that the policy might have some effect on outcomes.

**After:**
> The policy may affect outcomes.


## Grammar and syntax patterns (12-17)

### 12. Avoidance of "is"/"are" (Copula Avoidance)

**Words to watch:** serves as/stands as/marks/represents [a], boasts/features/offers [a]

**Problem:** LLMs substitute elaborate constructions for simple copulas.

**Before:**
> Gallery 825 serves as LAAA's exhibition space for contemporary art. The gallery features four separate spaces and boasts over 3,000 square feet.

**After:**
> Gallery 825 is LAAA's exhibition space for contemporary art. The gallery has four rooms totaling 3,000 square feet.


### 13. Negative Parallelisms, Tailing Negations, and Negative Listing

**Problem:** Constructions like "Not only...but..." or "It's not just about..., it's..." are overused. So are clipped tailing-negation fragments such as "no guessing" or "no wasted motion" tacked onto the end of a sentence instead of written as a real clause. Stacked negative listing is the same tell ("Not a framework. Not a library. A protocol."): just say what it is.

**Before:**
> It's not just about the beat riding under the vocals; it's part of the aggression and atmosphere. It's not merely a song, it's a statement.

**After:**
> The heavy beat adds to the aggressive tone.

**Before (tailing negation):**
> The options come from the selected item, no guessing.

**After:**
> The options come from the selected item without forcing the user to guess.


### 14. Rule of Three Overuse

**Problem:** LLMs force ideas into groups of three to appear comprehensive.

**Before:**
> The event features keynote sessions, panel discussions, and networking opportunities. Attendees can expect innovation, inspiration, and industry insights.

**After:**
> The event includes talks and panels. There's also time for informal networking between sessions.


### 15. Elegant Variation (Synonym Cycling)

**Problem:** AI has repetition-penalty code causing excessive synonym substitution. If the clear word is right, repeat it.

**Before:**
> The protagonist faces many challenges. The main character must overcome obstacles. The central figure eventually triumphs. The hero returns home.

**After:**
> The protagonist faces many challenges but eventually triumphs and returns home.


### 16. False Ranges

**Problem:** LLMs use "from X to Y" constructions where X and Y aren't on a meaningful scale.

**Before:**
> Our journey through the universe has taken us from the singularity of the Big Bang to the grand cosmic web, from the birth and death of stars to the enigmatic dance of dark matter.

**After:**
> The book covers the Big Bang, star formation, and current theories about dark matter.


### 17. Passive Voice and Subjectless Fragments

**Problem:** LLMs often hide the actor or drop the subject entirely with lines like "No configuration file needed" or "The results are preserved automatically." Rewrite these when active voice makes the sentence clearer and more direct.

**Before:**
> No configuration file needed. The results are preserved automatically.

**After:**
> You do not need a configuration file. The system preserves the results automatically.


## Rhythm and rhetoric patterns (18-27)

### 18. Em Dash Overuse

**Problem:** LLMs use em dashes (—) more than humans, mimicking "punchy" sales writing. In practice, most of these can be rewritten more cleanly with commas, periods, or parentheses.

**Before:**
> The term is primarily promoted by Dutch institutions—not by the people themselves. You don't say "Netherlands, Europe" as an address—yet this mislabeling continues—even in official documents.

**After:**
> The term is primarily promoted by Dutch institutions, not by the people themselves. You don't say "Netherlands, Europe" as an address, yet this mislabeling continues in official documents.


### 19. Colon Reveals

**Signs to watch:** a short noun phrase, a colon, then a dramatic reveal, often stacked several to a page ("The best part: it learns." / "The detail that makes it work: a separate agent grades it.")

**Problem:** LLMs use the colon as a drum roll. As a default rhythm it reads as engagement-bait, and lately it substitutes for the em dashes people learned to strip. Rewrite as a plain sentence; keep colons for lists, labels, and quotes, and prefer sentence case after one.

**Before:**
> The best part: the whole thing runs offline. The catch: you need 64GB of RAM.

**After:**
> The whole thing runs offline, though you need 64GB of RAM.


### 20. Dramatic Fragmentation and Punchy Kickers

**Signs to watch:** two- or three-word subjectless sentences used for drama, staccato "X. And Y. And Z." runs, a short quotable line ending every paragraph or section, cutesy appositive fragments ("the catalog, honestly priced")

**Problem:** LLMs chop sentences into fragments for false emphasis and end sections with a quotable "mic-drop" line. It reads like ad copy or a motivational poster. If a line sounds like it belongs on a poster, cut it or fold it back into a real sentence with a subject. This is distinct from pattern 17 (which is about grammatical passive voice); here the tell is rhythm and showmanship, not a hidden actor. When the kicker is a fake-profound closing line, delete it outright rather than rewriting it into a better metaphor, and end on the clearest concrete sentence already in the draft. "That's it. That's the whole thing." is the same tell.

**Before:**
> The catalog, honestly priced. Pay for what it does. Not promises. It just works. Every time.

**After:**
> The catalog is priced by usage, so you pay for the calls you actually make rather than a flat monthly fee.


### 21. Rhetorical Questions Answered Immediately

**Signs to watch:** "What if...?", "What if I told you...", "The question is...", "Ever wondered...?", "Plot twist:", a question immediately followed by its own answer, "Think about it."

**Problem:** LLMs pose a question only to answer it a beat later. The question adds no information and stalls the sentence. State the point directly.

**Before:**
> What makes an API good? It comes down to predictability. Think about it: developers want to know exactly what they will get back.

**After:**
> A good API is predictable, so developers know exactly what they will get back.


### 22. Sentence-Opener Tics

**Words to watch:** So..., Look,, Here's the thing,, habitual sentence-initial And/But, "I think"/"I believe" when stating a fact, adverb openers (Interestingly, Importantly, Notably, Crucially, Essentially, Ultimately)

**Problem:** LLMs lean on a small set of openers. Adverb openers tell the reader how to feel instead of earning it, and "So" or "Look" fake conversational warmth. Drop the opener and start with the substance.

**Before:**
> So, the results were mixed. Interestingly, adoption went up. Importantly, churn went up too. I think that means the feature still needs work.

**After:**
> The results were mixed: adoption rose, but churn rose alongside it, so the feature still needs work.


### 23. Forced Metaphors and Figurative Overwriting

**Signs to watch:** original but strained metaphors, mixed metaphors, figurative substitutions where a plain word is clearer, a metaphor that gets explained right after it is used

**Problem:** Beyond the stock figurative words flagged in patterns 4 and 9, LLMs invent decorative metaphors that add imagery without adding meaning, then often explain them. Plain description is usually clearer and more honest. If the metaphor does not earn its place, cut it and say the literal thing.

**Before:**
> The codebase is a garden we must tend, pruning dead branches and planting seeds of innovation so the whole ecosystem can flourish. In other words, delete unused code and add features.

**After:**
> Delete unused code and add the features users are asking for.


### 24. Persuasive Authority Tropes

**Phrases to watch:** The real question is, at its core, in reality, what really matters, fundamentally, the deeper issue, the heart of the matter

**Problem:** LLMs use these phrases to pretend they are cutting through noise to some deeper truth, when the sentence that follows usually just restates an ordinary point with extra ceremony.

**Before:**
> The real question is whether teams can adapt. At its core, what really matters is organizational readiness.

**After:**
> The question is whether teams can adapt. That mostly depends on whether the organization is ready to change its habits.


### 25. Signposting and Announcements

**Phrases to watch:** Let's dive in, let's explore, let's break this down, here's what you need to know, now let's look at, without further ado

**Problem:** LLMs announce what they are about to do instead of doing it. This meta-commentary slows the writing down and gives it a tutorial-script feel.

**Before:**
> Let's dive into how caching works in Next.js. Here's what you need to know.

**After:**
> Next.js caches data at multiple layers, including request memoization, the data cache, and the router cache.


### 26. Fragmented Headers

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


### 27. Reassurance Kickers

**Signs to watch:** And that's okay., And that's fine., There's nothing wrong with that., no shame in..., you're not alone, it's completely normal

**Problem:** LLMs tack on reassurance the reader never asked for. It softens the writing and assumes the reader needs comforting. Trust the reader: make the point and stop.

**Before:**
> You might not have a testing setup yet. And that's okay. Plenty of teams start without one, and there's nothing wrong with that.

**After:**
> Many teams start without a testing setup and add one once regressions begin costing real time.


## Formatting and typography patterns (28-33)

### 28. Overuse of Boldface

**Problem:** AI chatbots emphasize phrases in boldface mechanically.

**Before:**
> It blends **OKRs (Objectives and Key Results)**, **KPIs (Key Performance Indicators)**, and visual strategy tools such as the **Business Model Canvas (BMC)** and **Balanced Scorecard (BSC)**.

**After:**
> It blends OKRs, KPIs, and visual strategy tools like the Business Model Canvas and Balanced Scorecard.


### 29. Inline-Header Vertical Lists

**Problem:** AI outputs lists where items start with bolded headers followed by colons.

**Before:**
> - **User Experience:** The user experience has been significantly improved with a new interface.
> - **Performance:** Performance has been enhanced through optimized algorithms.
> - **Security:** Security has been strengthened with end-to-end encryption.

**After:**
> The update improves the interface, speeds up load times through optimized algorithms, and adds end-to-end encryption.


### 30. Title Case in Headings

**Problem:** AI chatbots capitalize all main words in headings.

**Before:**
> ## Strategic Negotiations And Global Partnerships

**After:**
> ## Strategic negotiations and global partnerships


### 31. Emojis

**Problem:** AI chatbots often decorate headings or bullet points with emojis.

**Before:**
> 🚀 **Launch Phase:** The product launches in Q3
> 💡 **Key Insight:** Users prefer simplicity
> ✅ **Next Steps:** Schedule follow-up meeting

**After:**
> The product launches in Q3. User research showed a preference for simplicity. Next step: schedule a follow-up meeting.


### 32. Curly Quotation Marks

**Problem:** ChatGPT uses curly quotes ("...") instead of straight quotes ("...").

**Before:**
> He said "the project is on track" but others disagreed.

**After:**
> He said "the project is on track" but others disagreed.


### 33. Hyphenated Word Pair Overuse

**Words to watch:** third-party, cross-functional, client-facing, data-driven, decision-making, well-known, high-quality, real-time, long-term, end-to-end

**Problem:** AI hyphenates common word pairs with perfect consistency. Humans rarely hyphenate these uniformly, and when they do, it's inconsistent. Less common or technical compound modifiers are fine to hyphenate.

**Before:**
> The cross-functional team delivered a high-quality, data-driven report on our client-facing tools. Their decision-making process was well-known for being thorough and detail-oriented.

**After:**
> The cross functional team delivered a high quality, data driven report on our client facing tools. Their decision making process was known for being thorough and detail oriented.


## Chatbot artifacts (34-36)

### 34. Collaborative Communication Artifacts

**Words to watch:** I hope this helps, Of course!, Certainly!, You're absolutely right!, Would you like..., let me know, here is a...

**Problem:** Text meant as chatbot correspondence gets pasted as content.

**Before:**
> Here is an overview of the French Revolution. I hope this helps! Let me know if you'd like me to expand on any section.

**After:**
> The French Revolution began in 1789 when financial crisis and food shortages led to widespread unrest.


### 35. Knowledge-Cutoff Disclaimers

**Words to watch:** as of [date], Up to my last training update, While specific details are limited/scarce..., based on available information...

**Problem:** AI disclaimers about incomplete information get left in text.

**Before:**
> While specific details about the company's founding are not extensively documented in readily available sources, it appears to have been established sometime in the 1990s.

**After:**
> The company was founded in 1994, according to its registration documents.


### 36. Sycophantic/Servile Tone

**Problem:** Overly positive, people-pleasing language.

**Before:**
> Great question! You're absolutely right that this is a complex topic. That's an excellent point about the economic factors.

**After:**
> The economic factors you mentioned are relevant here.


## Layout pattern (37)

### 37. Styled Callout Boxes (visual tell)

**Problem:** Documents styled by AI lean on tinted callout/admonition boxes with a thick colored accent bar and a bold colored lead-in label. Readers now recognize the box itself, before reading a word, as machine styling. The prose patterns above can all be fixed and the document still looks generated.

**Before:**
> A pink/amber box, thick red edge bar, bold red "Note:" label, rounded corners.

**After:**
> Fold the aside into the body text where it belongs; or use the document's own native devices - a plain indented paragraph, an italic aside, a footnote, or a single-rule table row. If a box is truly needed (legal warnings), use a plain thin border in the document's text color, no tint, no accent bar, label in the same weight as body text.

**Scope note:** this is a LAYOUT pattern - it lives in renderers and templates, not prose. When humanizing a document, check the template too: strip accent-bar callouts, tinted admonitions, and emoji-prefixed headings from outward-facing deliverables. A dedicated layout gate can own the full set of document tells (see [document-design](https://github.com/WolfurX/document-design)); this pattern is the bridge to it.


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

**Rewrite:**
> AI coding assistants can make you faster at the boring parts. Not everything. Definitely not architecture.
>
> They're great at boilerplate: config files, test scaffolding, repetitive refactors. They're also great at sounding right while being wrong. I've accepted suggestions that compiled, passed lint, and still missed the point because I stopped paying attention.
>
> People I talk to tend to land in two camps. Some use it like autocomplete for chores and review every line. Others disable it after it keeps suggesting patterns they don't want. Both feel reasonable.
>
> The productivity metrics are slippery. Vendors publish acceptance rates, but acceptance isn't correctness, and correctness isn't value. If you don't have tests, you're basically guessing.

**Changes made:**
- Removed chatbot artifacts ("Great question!", "I hope this helps!", "Let me know if...")
- Removed significance inflation ("testament", "pivotal moment", "evolving landscape", "vital role")
- Removed promotional language ("groundbreaking", "nestled", "seamless, intuitive, and powerful")
- Removed vague attributions ("Industry observers")
- Removed superficial -ing phrases ("underscoring", "highlighting", "reflecting", "contributing to")
- Removed negative parallelism ("It's not just X; it's Y")
- Removed rule-of-three patterns and synonym cycling ("catalyst/partner/foundation")
- Removed false ranges ("from X to Y, from A to B")
- Removed em dashes, emojis, boldface headers, and curly quotes
- Removed copula avoidance ("serves as", "functions as", "stands as") in favor of "is"/"are"
- Removed formulaic challenges section ("Despite challenges... continues to thrive")
- Removed knowledge-cutoff hedging ("While specific details are limited...")
- Removed excessive hedging ("could potentially be argued that... might have some")
- Removed filler phrases and persuasive framing ("In order to", "At its core")
- Removed generic positive conclusion ("the future looks bright", "exciting times lie ahead")
- Made the voice more personal and less "assembled" (varied rhythm, fewer placeholders)


## Attribution and lineage

- **Base:** [Wikipedia: Signs of AI writing](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing) (WikiProject AI Cleanup), via [blader/humanizer](https://github.com/blader/humanizer) v2.5.1 (MIT, Siqi Chen), extended with additional patterns and the marketing-cliché list. Adapted as a Claude Code skill in July 2026 (text-only, no executable content). MIT license preserved in `LICENSE`.
- **August 2026:** callout-box layout pattern (#37) added from reader feedback; merged the useful parts of [petergyang/no-ai-slop](https://github.com/petergyang/no-ai-slop) (MIT, Peter Yang): faux-insight setups (#7), colon reveals (#19), the detect mode, the minimum-effective-edit guardrails, the kicker-deletion rule, and word-list extensions. Patterns regrouped by theme and renumbered 1-37.

Key insight from Wikipedia: "LLMs use statistical algorithms to guess what should come next. The result tends toward the most statistically likely result that applies to the widest variety of cases."
