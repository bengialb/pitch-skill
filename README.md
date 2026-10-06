# Pitch Skill

An agent skill for turning a product and its evidence into a pitch you can say aloud, with slide cues, a focused demo and a rehearsal plan.

Use it for investor pitches, jury presentations, customer demos and product launches. It follows the [Agent Skills format](https://agentskills.io/specification), so the same instructions can be installed in Claude Code, GitHub Copilot in VS Code, Codex and other compatible agents.

## Install

With Node.js installed, run this in your project directory:

```sh
npx skills add bengialb/pitch-skill
```

Choose `pitch` and the agents you want to use. The [skills CLI](https://github.com/vercel-labs/skills) handles their installation locations. Add `--global` if you want a personal installation across projects.

For a manual installation, download this repository or clone it:

```sh
git clone https://github.com/bengialb/pitch-skill.git
```

Copy the entire `skills/pitch` folder, including its references, to your agent's skills directory:

| Agent | Project directory | Invoke |
|---|---|---|
| [Claude Code](https://code.claude.com/docs/en/skills) | `.claude/skills/pitch/` | `/pitch` |
| [GitHub Copilot in VS Code](https://code.visualstudio.com/docs/agent-customization/agent-skills) | `.github/skills/pitch/` | `/pitch` |
| Codex | `.agents/skills/pitch/` | `$pitch` |
| Other compatible agents | The agent's supported skills directory | Ask it to use the `pitch` skill |

The final directory should contain `SKILL.md` directly, with `references/` beside it. If you already have a skill named `pitch`, review it before replacing it. Start a fresh agent session if the installed skill doesn't appear.

## Try it

```text
Use the pitch skill to prepare a 3-minute pitch for a nontechnical jury.
Here are my product description, current evidence and judging criteria: [paste them].
Give me the spoken script, slide/demo cues, estimated timing and Q&A.
Flag any facts you still need.
```

Or work on a smaller piece:

```text
Use the pitch skill to rewrite only the opening of this customer demo.
Keep the facts and my tone. Don't add pricing or pilot offers: [paste the opening].
```

[More prompts](examples/prompts.md) cover an investor pitch and a product demo. You can specify your audience, duration and preferred output language in the request.

## What it helps with

- A spoken script with a clear opening, supporting evidence and a specific next step.
- Slide and demo cues that connect what you say to what the audience sees.
- An estimated time budget, a shorter fallback and likely Q&A answers.
- A revision of just the section you need, such as an opening or one slide.

It separates customers, pilots, usage and revenue. Timing estimates include pauses and demo actions, and remain estimates until you rehearse. The instructions work with the evidence you provide; they don't invent traction or add commercial commitments on your behalf.

## How we developed it

We analyzed startup pitch recordings, product demos and launch presentations, using video analysis and speech transcripts to examine openings, evidence placement, demo sequences and closing asks. The following examples informed the skill:

| Recording | What we studied |
|---|---|
| [DoorDash: YC Demo Day](https://www.youtube.com/watch?v=YNAOXokK--o) | Explaining an unsolved context before showing operational evidence |
| [GitLab: YC W15](https://www.youtube.com/watch?v=HmrDjvv_ENQ) | Placing usage evidence early and explaining the mechanism behind an advantage |
| [Retool: YC W17](https://www.ycombinator.com/companies/retool) | Making an unfamiliar category understandable through a specific customer job |
| [Dropbox: TechCrunch50](https://www.youtube.com/watch?v=frsVoYyKpTk) | Following the same file through a visible before-and-after demo |
| [Cloudflare: Disrupt SF 2010](https://www.youtube.com/watch?v=711BkXJ0-Co) | Connecting technical explanations to an observable user benefit |
| [Getaround: Startup Battlefield](https://www.youtube.com/watch?v=70YdTfEqVrY) | Addressing adoption barriers through a product demonstration |
| [Scrub Daddy: opening excerpt](https://www.linkedin.com/posts/entrepreneurial-student_entrepreneurialstudent-studententrepreneur-activity-7392470877159878656-1pRV) | Testing a claim with a visible comparison |
| [Dropbox: early screen demo](https://www.linkedin.com/posts/sequoia_heres-the-viral-video-drew-houston-and-arash-activity-7283177970087686144-GVSu) | Explaining features through actions and their results |
| [Figma: retrospective pitch walkthrough](https://www.youtube.com/watch?v=C1UUVdN3kdQ) | Connecting a vision to working prototypes and recognizing a fragmented product story |
| [Slack: product film](https://www.youtube.com/watch?v=B6zVzWU95Sw) | Showing everyday friction in an existing workflow |
| [Tesla Roadster: launch report and interview](https://www.youtube.com/watch?v=Mc8aOgUI-6Y) | Connecting product benefits to a staged longer-term plan |
| [iPhone: Macworld 2007](https://www.youtube.com/watch?v=VQKMoT-6XSg) | Building understanding through familiar uses and controlled repetition |
| [Tesla Model 3: unveiling](https://www.youtube.com/watch?v=Q4VGQPk2Dl8) | Connecting prior stages, product benefits and adoption obstacles |
| [Andrew Mason: Startup School 2010](https://jacquesmattheij.com/startup-school-2010/andrew-mason/) | Examining a broad vision against a concrete first use case |

These examples have different purposes and formats. We adapted the patterns to the audience and available evidence rather than requiring a single deck sequence. The [structure guide](skills/pitch/references/structures.md) explains those choices.

The [source notes](skills/pitch/references/source-notes.md) record the analysis method and observations for each entry. The review covered 20 links, with narrative analysis for 14 entries; the notes also distinguish a Ring negotiation excerpt, indirect Coinbase evidence and inaccessible original recordings. The iPhone, Model 3 and Andrew Mason observations came from speech transcripts. The notes retain those limits and document rejected automated analyses.

These are editorial interpretations of the presentations. The research doesn't establish that a pitch technique caused a company's later success. Videos and third-party materials remain with their original owners; this repo contains our instructions and commentary.

## Files

```text
skills/pitch/
  SKILL.md                     Portable skill instructions
  references/source-notes.md   Source observations and analysis methods
  references/structures.md     Narrative choices and timing example
  agents/openai.yaml           Optional Codex interface metadata
examples/prompts.md             Example requests with fictional inputs
```

The skill has no scripts or required video-analysis service. Your agent supplies the model and any presentation tools needed for the requested output. The optional interface metadata doesn't change the portable instructions.

## Validation and contributions

We check the skill's frontmatter, local reference links and installation file layout. Earlier development included response reviews for three fictional requests. We haven't measured persuasion or audience comprehension in a controlled test, or run the skill inside every supported agent.

For source corrections or failures in a real pitch, open an issue with the request, expected behavior and relevant excerpt. Remove confidential product or customer information first. Contributions should improve the pitch decisions without adding invented evidence or imposing one deck format on every audience.

## License

[MIT](LICENSE). You can use, modify and share the repository content under that license. Linked videos, transcripts and slides retain their owners' rights.
