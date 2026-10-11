# The canonical install block

One install story, one wording. `README.md`, `.changeset/*`, and every page under `docs/` must say **this** and nothing else. Change it here first, then propagate.

This fork ships `windyd-skills` through its own `windyd` marketplace. Add that marketplace before installing. The official marketplace's `mattpocock-skills` entry installs upstream, not this fork.

## Claude Code: the plugin

<canonical-block name="claude-code">

```bash
claude plugin marketplace add windyd/skills
claude plugin install windyd-skills@windyd
```

Or, from inside a session:

```
/plugin marketplace add windyd/skills
/plugin install windyd-skills@windyd
```

This fork uses the `windyd` marketplace. Enable auto-update for that marketplace if you want updates to arrive automatically.

</canonical-block>

## Codex, and other agents: skills.sh

The plugin is Claude Code only. Everywhere else, [skills.sh](https://skills.sh/windyd/skills) copies editable skill files into the project. Use the whole-set form on `README.md`:

<canonical-block name="skills-sh-whole-set">

```bash
npx skills@latest add windyd/skills
```

Pick the skills you want, and which coding agents to install them on. **The installer lets you choose which skills to take: make sure `setup-matt-pocock-skills` is one of them.**

</canonical-block>

…and the single-skill form wherever one skill is named on its own. Note that **`docs/` pages are not a consumer of this block**: ai-hero renders the install widget above the body, so a page that writes the commands out duplicates it. See [writing-docs.md](./writing-docs.md).

<canonical-block name="skills-sh-one-skill">

```bash
npx skills@latest add windyd/skills --skill=<name>
```

```bash
npx skills@latest update <name>
```

</canonical-block>

`skills@latest` is the pinned spelling in all three. The pages under `docs/` used to carry their own copy of these commands; those blocks are now deleted rather than corrected, because the site renders the install commands itself.

## The two routes are exclusive

The plugin is a managed, read-only bundle you subscribe to. skills.sh writes files you own and edit. Installing both leaves the user with every skill twice: always say "pick one".

## Marketplace source

`.claude-plugin/marketplace.json` makes the repo its own single-plugin marketplace. Keep its `windyd` marketplace name and `windyd-skills` plugin name aligned with the commands above.
