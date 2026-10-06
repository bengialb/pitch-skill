# Pitch Skill

A Codex skill for turning a product and its evidence into a pitch you can say aloud, with slide cues, a focused demo and a rehearsal plan.

Built by [Bengi Albukrek](https://github.com/bengialb), founder of [Deflows](https://deflows.com), while working on product and jury presentations. The skill works with the product facts you provide; it adapts to investor, jury, customer and launch audiences.

## What you can ask for

- A spoken script with a clear opening, supporting evidence and a specific next step.
- Slide and demo cues that connect what you say to what the audience sees.
- An estimated time budget, a shorter fallback and likely Q&A answers.
- A revision of just the section you need, such as an opening or one slide.

It separates actual customers, pilots, usage and revenue. Missing evidence stays visible; it doesn't invent traction or add commercial commitments on your behalf. Timing estimates include pauses and demo actions, and remain estimates until you rehearse.

## Install in Codex

Ask Codex:

```text
Use $skill-installer to install the pitch skill from
https://github.com/bengialb/pitch-skill/tree/main/skills/pitch
```

For a manual installation, clone the repository and copy `skills/pitch` into your Codex skills directory:

```sh
git clone https://github.com/bengialb/pitch-skill.git
mkdir -p "${CODEX_HOME:-$HOME/.codex}/skills"
cp -R pitch-skill/skills/pitch "${CODEX_HOME:-$HOME/.codex}/skills/pitch"
```

If you already have a skill named `pitch`, inspect it before copying. Keep a backup if you want to replace it. Use `$pitch` on your next turn after installation.

## Try it

```text
Use $pitch to prepare a 3-minute English pitch for a nontechnical jury.
Here are my product description, current evidence and judging criteria: [paste them].
Give me the spoken script, slide/demo cues, estimated timing and Q&A.
Flag any facts you still need.
```

Or work on a smaller piece:

```text
Use $pitch to rewrite only the opening of this customer demo.
Keep the facts and my tone. Don't add pricing or pilot offers: [paste the opening].
```

[More prompts](examples/prompts.md) cover an investor pitch and a product demo. The instructions and research notes are currently in Turkish; ask for the output language you need. These are agent instructions, so using the skill requires a model session and its usual usage allowance. No video-analysis service or API key is required by the skill itself.

## How we developed it

The starting point was [Valeria Rozova-Rosenblatt's LinkedIn collection](https://www.linkedin.com/feed/update/urn:li:activity:7511350486432718848). On October 3, 2026, we resolved and checked 20 links. For 14 entries, we examined the narrative through video analysis or speech transcripts. The notes also identify a negotiation excerpt for Ring, indirect evidence for Coinbase and inaccessible original recordings for Mint, Yammer, Square and Groupon.

The collection spans different formats: demo-day talks, product demos, launch presentations, a commercial film and retrospective talks. We kept those contexts separate when adapting the techniques. Examples include Retool's explanation of an unfamiliar category, GitLab's early use of evidence and Dropbox's demonstrations of a visible product result. These are our editorial interpretations of the examples.

The [source notes](skills/pitch/references/source-notes.md) record the links, access limits and method used for each entry. Automated analysis and transcripts can contain errors. We rejected a mismatched Coinbase analysis and an incomplete Figma timeline; we used text where some video analyses failed. The research doesn't establish that a particular pitch technique caused a company's later success.

The resulting skill asks the agent to choose a structure based on the audience and evidence, connect each claim to something observable, and treat delivery time honestly. The [structure guide](skills/pitch/references/structures.md) explains the available narrative options.

## Files

```text
skills/pitch/
  SKILL.md                     Pitch instructions
  agents/openai.yaml           Codex interface metadata
  references/source-notes.md   Research methods and source observations
  references/structures.md     Narrative choices and timing example
examples/prompts.md             Example requests with fictional inputs
```

This repository contains our instructions and commentary. Videos, full transcripts and third-party slides remain with their original owners. The MIT license applies to our repository content; it doesn't grant rights to linked source material.

## Validation and contributions

Before publication, we checked the skill's frontmatter, local reference links and installation in an isolated directory. Earlier development included reviews of generated responses for three fictional requests; a later wording adjustment hasn't had a fresh independent behavior evaluation. We haven't measured persuasion or audience comprehension in a controlled test.

If you find a source error or a failure in a real pitch, open an issue with the request, expected behavior and relevant excerpt. Remove confidential product or customer information first. Contributions should improve the pitch decisions without adding invented evidence or imposing one deck format on every audience.

## License

[MIT](LICENSE). You can use, modify and share the skill under that license.
