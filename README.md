<div align="center">

# Brainstorm Studio

**A Claude skill that runs a real brainstorming session and pushes you past the obvious to 100+ ideas.**

![License](https://img.shields.io/badge/license-MIT-blue?style=flat-square)
![Claude Skill](https://img.shields.io/badge/Claude-Skill-D97757?style=flat-square)
![Python](https://img.shields.io/badge/python-3-3776AB?style=flat-square)

</div>

## What it does

Ask Claude for ideas and you usually get the first ten obvious ones. Brainstorm Studio makes Claude run a *facilitated* session instead: it draws on a library of 108 techniques (SCAMPER, Six Thinking Hats, Reverse Brainstorming, First Principles, Crazy 8s, Worst Possible Idea and more), keeps shifting the angle so ideas don't run dry, and logs everything to a file you can resume later. It ends with a one-of-a-kind HTML keepsake of the session.

It is for anyone who wants to think divergently about a name, a feature set, content, a strategy or a project. It is not for implementation plans, code or task breakdowns.

## Pick how much Claude contributes

| Stance | What Claude does |
|---|---|
| **Facilitator** | Only asks questions and sets constraints. Every idea is yours. |
| **Creative Partner** | Facilitates and trades ideas with you, "yes, and" style. Each idea is tagged by author. |
| **Ideate for me** | Runs the whole session itself and shows you the result. |

## Example prompts

- "Let's brainstorm names for my podcast."
- "I'm stuck on how to grow my newsletter. Give me ideas."
- "What are my options for a side project I can build with my kids?"
- "Brainstorm features for a habit-tracking app. Ideate for me."

## Features

- **108 techniques in 13 categories**, from `structured` and `creative` to `absurdist`, `biomimetic`, `quantum` and `speculative_future`. Served on demand, never dumped into the chat.
- **Technique composer page**: an offline HTML page where you choose the stance and tick techniques, then paste one block back to Claude.
- **Resumable sessions**: every idea, decision and insight goes into an append-only `.memlog.md`. Attach it in a new chat to continue.
- **Idea tally**: a running count at each change of technique, to keep you heading for 100+.
- **Converge phase**: when you are ready to narrow down, Claude runs one of affinity clustering, impact-effort, NUF test, forced ranking, PMI or MoSCoW.
- **Wrap-up artifacts**: an HTML keepsake designed around your topic, and an optional short `brainstorm-intent.md` to feed into a brief, spec or the next chat.
- **Your own techniques**: add favourites and new techniques in `customize.toml`.

## What you get

Each session creates a folder like `brainstorming/brainstorm-<topic>-<date>/` containing:

```text
.memlog.md            # the full record of the session (resume from this)
brain-selector.html   # the technique composer page
brainstorm.html       # the keepsake (wrap-up)
brainstorm-intent.md  # optional distilled summary
```

## Install

You need Python 3 for the bundled scripts (standard library only, nothing to install).

**Claude app:** zip the `skills/brainstorm-studio` folder (the zip must contain the `brainstorm-studio` folder with `SKILL.md` inside) and upload it as a custom skill in Claude's Skills settings.

```bash
cd skills
zip -r brainstorm-studio.zip brainstorm-studio -x "*/__pycache__/*" "*.DS_Store"
```

**Claude Code:** copy the skill folder into your skills directory.

```bash
# for all your projects
cp -r skills/brainstorm-studio ~/.claude/skills/
# or for one project
cp -r skills/brainstorm-studio .claude/skills/
```

## Usage

Just ask Claude to brainstorm. Claude greets you, asks what you are brainstorming and why, then offers the composer page. Open it, choose your stance and techniques, click **Copy prompt** and paste the result back. Prefer chat? Say "let's do it in chat" and Claude helps you pick.

Say "pick", "prioritize" or "make it real" to start converging, and "I'm done" to wrap up. To resume, attach the `.memlog.md` from an earlier session.

You can also run the helper scripts yourself (from `skills/brainstorm-studio`):

```bash
python3 scripts/brain.py --file assets/brain-methods.csv categories
python3 scripts/brain.py --file assets/brain-methods.csv random --category wild -n 3
python3 scripts/brain.py --file assets/brain-methods.csv html --out brain-selector.html
```

The first command prints the 13 categories with their technique counts (for example `absurdist 6`, `structured 15`).

## Configuration

Edit `skills/brainstorm-studio/customize.toml`. Anything you say in chat overrides it for that run.

| Setting | Default | What it does |
|---|---|---|
| `favorite_techniques` | `[]` | Techniques Claude reaches for first |
| `additional_techniques` | `[]` | Extra techniques or whole new categories |
| `persistent_facts` | `[]` | Facts or house rules kept in mind all session |
| `output_dir` | `{output_folder}/brainstorming` | Where sessions are saved |
| `output_folder_name` | `brainstorm-{topic_slug}-{date}` | Name of each session folder |
| `external_handoffs` | `[]` | Send results on to tools like Notion or Drive |
| `on_complete` | `""` | Instruction to run when a session finishes |

## Project structure

```text
skills/brainstorm-studio/
├── SKILL.md          # the skill: how a session runs
├── customize.toml    # settings
├── assets/
│   ├── brain-methods.csv   # the 108 techniques
│   └── brain-icons.json    # icons for the composer page
├── references/       # one file per mode and phase (facilitator, partner, autonomous, converge, finalize, resume, headless)
└── scripts/
    ├── brain.py      # serves techniques and builds the composer page
    └── memlog.py     # append-only session log
```

## Contributing

Contributions are welcome, especially new techniques. See [CONTRIBUTING.md](CONTRIBUTING.md).

## Support

Open an issue to report a bug or suggest a change. For security problems, see [SECURITY.md](SECURITY.md).

## License

[MIT](LICENSE).

## Acknowledgements

Brainstorm Studio is a modified copy of the `bmad-brainstorming` skill from [BMAD-METHOD](https://github.com/bmad-code-org/BMAD-METHOD) by BMad Code, LLC (MIT License). It is not affiliated with or endorsed by BMad Code, LLC. The list of changes is in [LICENSE](LICENSE).
