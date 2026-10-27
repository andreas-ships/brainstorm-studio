# Contributing to Brainstorm Studio

Thanks for helping! This page gets you from clone to pull request.

## Set up

Fork the repository on GitHub, then clone your fork. You need Python 3 only
(standard library, nothing to install).

## Make a change

1. Create a branch: `git checkout -b fix/short-description`
2. Make your change. Technique ideas go in `skills/brainstorm-studio/assets/brain-methods.csv`
   (columns: `category,technique_name,description,detail,provenance,good_for,audience`).
3. There is no automated test suite yet. Run these checks and describe them in your PR:

   ```bash
   cd skills/brainstorm-studio
   python3 scripts/brain.py --file assets/brain-methods.csv categories
   python3 scripts/brain.py --file assets/brain-methods.csv html --out /tmp/selector.html
   python3 scripts/memlog.py init --workspace /tmp/session --field topic=test --field goal=test --field mode=partner
   ```

4. Commit with a clear, short message.
5. Open a pull request and describe what changed and why.

## Rules of the skill

- Keep `SKILL.md` and the files in `references/` consistent with each other.
- Scripts stay standard-library only.
- Do not commit session output (`brainstorming/`, `.memlog.md`).

## Report a bug or ask for a feature

Open an issue using the templates. For security problems, see [SECURITY.md](SECURITY.md).
