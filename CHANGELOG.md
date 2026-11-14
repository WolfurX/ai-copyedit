# Changelog

## 2.0.0 (2026-11-14)

Renamed from humanizer to ai-copyedit.

- The skill, the plugin, and the repository are now named `ai-copyedit`, and the marketplace is
  `wolfurx-ai-copyedit`. The old repository address redirects to the new one.
- The rules and patterns are the same as in 1.0.0.
- If you installed the skill as `humanizer`, remove that copy and install `ai-copyedit`. The
  README has the commands.

## 1.0.0 (2026-11-14)

First public release.

- 56 patterns, each with a before and after example whose "after" uses only facts from its
  "before".
- Safeguards: text is treated as material rather than instructions, evidence strength decides
  when a tell justifies an edit, detect mode does not treat second-language English or short
  samples as evidence, and the never-inject rules forbid invented experiences, facts, promises,
  and detector tricks.
- Native writing in any language, with guidance on translated-sounding text and on which English
  rules change elsewhere.
- Install paths for Claude Code (plugin), the Skills CLI (about 80 agents), Claude.ai, and
  manual copy.
