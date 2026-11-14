# humanizer

A [Claude Code skill](https://code.claude.com/docs/en/skills) that strips the telltale signs of
AI-generated writing and brings the writer's own voice forward. It names 43 patterns, each with
before and after examples, and has a detect-only audit mode.

## Why

Most AI text gets caught long before anyone runs a detector. Readers recognize the tells:
"testament to", perfect triads, em dashes everywhere, bolded list headers, a "challenges and
future prospects" section, an upbeat recap ending. This skill names each tell, shows the fix,
and then does the harder half of the job, which is bringing the writer's own voice forward so
the result reads like a person wrote it. It never invents opinions, experiences, or facts to get
there, because a fake human voice is as easy to spot as the chatbot one.

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

Or clone and copy. Claude Code picks it up automatically. It triggers when you ask it to
humanize or de-AI a text, when it reviews a draft before publishing, and when it writes
user-facing prose of its own. To update, run the same commands again.

## How it works

**Edit** rewrites the text to remove the patterns while keeping its meaning and voice.
Guardrails keep the minimum effective edit, so a rough draft with a real voice still sounds like
the same person afterward, just without the tells. Before it hands back a rewrite, it checks that
the paragraphs build on each other and that each one adds something new.

**Detect** audits without rewriting. It lists each pattern found, quotes the offending line, and
gives the fix in a few words. It never claims to know whether AI wrote the text. Detectors guess,
while named patterns are evidence you can check yourself.

Give it a sample of your own writing and it matches your sentence length, word choice, and
punctuation habits. A written house style wins on mechanics such as heading case, quote marks,
hyphenation, and spelling, but it never excuses the AI patterns themselves.

When a sentence needs a fact the draft doesn't contain, the skill asks for it or leaves a visible
flag such as [NEEDS NAME]. Flags are fine in a draft, and every one has to be resolved before the
text is sent.

## What it covers, in one breath

Significance inflation, notability name-dropping, superficial -ing analyses, promotional tone,
weasel attributions, guesses dressed as facts, formulaic "challenges" sections, faux-insight
setups, recap endings, AI vocabulary, filler, hedging, copula avoidance, negative parallelisms,
rule-of-three overuse, synonym cycling, false ranges, passive voice and subjectless fragments, em
dash overuse, colon reveals, punchy kickers, rhetorical questions, sentence-opener tics, forced
metaphors, aphorism formulas, persuasive authority tropes, narrated candor, false concessions,
launch-copy introductions, signposting, fragmented headers, reassurance kickers, boldface overuse,
inline-header lists, title case, emojis, mismatched quote marks, hyphenation errors, chatbot
artifacts, knowledge-cutoff disclaimers, sycophancy, leaked placeholders and tool residue, and the
styled callout box that marks a document as machine-made before a single word is read.

## Other languages

The skill works in any language. It writes natively instead of drafting in English and
translating, and it flags the signs of translated text, such as idioms rendered word for word,
false friends, English word order and punctuation, and the wrong formal or informal "you". Its
English grammar and typography rules apply only to English. When it doesn't know a language's
conventions well, it says so and asks for a native writing sample instead of guessing. The main
examples are in English, and the language guidance includes examples from Spanish, French,
German, Italian, Japanese, Indonesian, and Russian.

## Works with document-design

humanizer fixes the words, and [document-design](https://github.com/WolfurX/document-design) fixes
the layout of rendered documents and charts. A document can pass every check here and still look
generated because of its callout boxes and badges, so install both. document-design's exit
checklist runs humanizer as its prose step. Where the two overlap, as with emoji headings,
bold-label lists, and too many headings, humanizer catches the tell in the text and
document-design catches it in the template that produced it. Both skills give the same fix for a
required warning and defer to the same house style.

## Lineage

Wikipedia's Signs of AI writing guide, via [blader/humanizer](https://github.com/blader/humanizer)
(MIT, Siqi Chen), extended with additional patterns. The useful parts of
[petergyang/no-ai-slop](https://github.com/petergyang/no-ai-slop) (MIT, Peter Yang) are merged in,
including the detect mode and the minimum-effective-edit guardrails. So are the useful parts of
[conorbronsdon/avoid-ai-writing](https://github.com/conorbronsdon/avoid-ai-writing) (MIT, Conor
Bronsdon), including the never-inject guardrails, six patterns, and the whole-piece tests.

## License

MIT. See [LICENSE](LICENSE) for the full notice, including the adapted portions.
