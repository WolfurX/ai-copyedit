# humanizer

A [Claude Code skill](https://code.claude.com/docs/en/skills) that strips the telltale signs of
AI-generated writing and puts a real voice back in. 37 named patterns, each with before/after
examples, plus a detect-only audit mode.

## Why

Most AI text gets caught long before anyone runs a detector. Readers recognize the tells:
"testament to", perfect triads, em dashes everywhere, bolded list headers, a "challenges and
future prospects" section, an upbeat recap ending. This skill names each tell, shows the fix,
and then does the harder half of the job: putting personality back so the result reads like a
person wrote it, not like slop that has been laundered.

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

Significance inflation, promotional tone, weasel attributions, faux-insight setups, AI
vocabulary, filler, hedging, copula avoidance, negative parallelisms, rule-of-three overuse,
synonym cycling, false ranges, em dash overuse, colon reveals, punchy kickers, rhetorical
questions, sentence-opener tics, forced metaphors, signposting, reassurance kickers, boldface
overuse, inline-header lists, title case, emojis, curly quotes, chatbot artifacts, sycophancy,
and the styled callout box that marks a document as machine-made before a single word is read.

## Voice calibration

Give it a sample of your own writing and it matches your sentence length, word choice, and
punctuation habits instead of imposing a house style.

## Lineage

Wikipedia's Signs of AI writing guide, via [blader/humanizer](https://github.com/blader/humanizer)
(MIT, Siqi Chen), extended with additional patterns; the useful parts of
[petergyang/no-ai-slop](https://github.com/petergyang/no-ai-slop) (MIT, Peter Yang) merged in,
including the detect mode and the minimum-effective-edit guardrails. Pairs with
[document-design](https://github.com/WolfurX/document-design), which guards the layout side of
the same problem.

## License

MIT
