# humanizer

A [Claude Code skill](https://code.claude.com/docs/en/skills) that strips the telltale signs of
AI-generated writing and brings the writer's own voice forward. 43 named patterns, each with before/after
examples, plus a detect-only audit mode.

## Why

Most AI text gets caught long before anyone runs a detector. Readers recognize the tells:
"testament to", perfect triads, em dashes everywhere, bolded list headers, a "challenges and
future prospects" section, an upbeat recap ending. This skill names each tell, shows the fix,
and then does the harder half of the job: bringing the writer's own voice forward so the result
reads like a person wrote it. It never invents opinions, experiences, or facts to get there,
because a fake human voice is as easy to spot as the chatbot one.

It is based on Wikipedia's [Signs of AI writing](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing)
guide, maintained by WikiProject AI Cleanup from observations of thousands of AI-generated texts.

## Install

```bash
mkdir -p ~/.claude/skills/humanizer
curl -o ~/.claude/skills/humanizer/SKILL.md \
  https://raw.githubusercontent.com/WolfurX/humanizer/main/SKILL.md
curl -o ~/.claude/skills/humanizer/LICENSE \
  https://raw.githubusercontent.com/WolfurX/humanizer/main/LICENSE
```

Or clone and copy. Claude Code picks it up automatically; it triggers when you ask it to
humanize or de-AI a text, when it reviews a draft before publishing, and when it writes
user-facing prose of its own.

## Two modes

**Edit** rewrites the text: patterns out, meaning intact, voice preserved. Guardrails keep the
minimum effective edit, so a rough draft with a real voice still sounds like the same person
afterward, just without the tells.

**Detect** audits without rewriting: each pattern found, the offending line quoted, the fix in
a few words. It never claims to know whether AI wrote the text. Detectors guess; named patterns
are evidence you can check yourself.

## What it covers, in one breath

Significance inflation, notability name-dropping, superficial -ing analyses, promotional
tone, weasel attributions, guesses dressed as facts, formulaic "challenges" sections,
faux-insight setups, recap endings,
AI vocabulary, filler, hedging, copula avoidance, negative parallelisms, rule-of-three overuse,
synonym cycling, false ranges, passive voice and subjectless fragments, em dash overuse, colon
reveals, punchy kickers, rhetorical questions, sentence-opener tics, forced metaphors,
aphorism formulas, persuasive authority tropes, narrated candor, false concessions, launch-copy
introductions, signposting, fragmented headers, reassurance kickers, boldface overuse,
inline-header lists, title case, emojis, mismatched quote marks, hyphenation errors, chatbot
artifacts, knowledge-cutoff disclaimers, sycophancy, leaked placeholders and tool residue, and
the styled callout box that marks a document as machine-made before a single word is read.

## Voice calibration

Give it a sample of your own writing and it matches your sentence length, word choice, and
punctuation habits instead of imposing a house style.

## Lineage

Wikipedia's Signs of AI writing guide, via [blader/humanizer](https://github.com/blader/humanizer)
(MIT, Siqi Chen), extended with additional patterns; the useful parts of
[petergyang/no-ai-slop](https://github.com/petergyang/no-ai-slop) (MIT, Peter Yang) merged in,
including the detect mode and the minimum-effective-edit guardrails; and the useful parts of
[conorbronsdon/avoid-ai-writing](https://github.com/conorbronsdon/avoid-ai-writing) (MIT, Conor
Bronsdon), including the never-inject guardrails, six patterns, and the whole-piece tests.
Pairs with
[document-design](https://github.com/WolfurX/document-design), which guards the layout side of
the same problem.

## License

MIT
