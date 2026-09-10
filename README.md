# Claude Code: context engineering for developers

A 32-slide talk for developers who already use Claude Code daily. It starts from how an
LLM reads its input, moves to the context window as the real constraint, and treats each
Claude Code feature — memory, rules, skills, commands, sub-agents, plan mode, hooks,
permissions, MCP — as a lever on that window.

Andriy · ELEKS corp. · Sept 2026

## Run it

Open `index.html` in a browser, or serve the folder:

```
python3 -m http.server 8000
```

Then visit `http://localhost:8000`. No build step, no dependencies to install.

## Presenting

| Key | Action |
| --- | --- |
| `→` / `←`, `Space` | Next / previous slide |
| `Home` / `End` | First / last slide |
| `F` | Fullscreen |
| `T` | Thumbnail rail — click to jump, drag to reorder |
| `N` | Speaker notes |
| `Cmd/Ctrl-P` | Print, one page per slide |

Every slide carries a speaker note in its `data-speaker-notes` attribute.

## Editing a slide

All slides live in `claude-code-context-engineering.dc.html`. Each one is a single
`<section>`:

```html
<section data-label="Hooks" data-screen-label="24" data-speaker-notes="...">
  ...
</section>
```

- `data-label` is the name in the thumbnail rail.
- `data-screen-label` is the slide number.
- Styling is inline on each element. Colors, type and spacing come from CSS variables
  declared in the `<helmet><style>` block at the top of the file (`--paper`, `--ink`,
  `--steel`, `--t-title`, and so on) — change a value there and it applies across the deck.
- To reorder slides, move the `<section>`. To add one, copy the nearest slide of the same
  kind and edit its contents; keep the corner rail and slide number consistent.

Design tokens come from the Industry design system, vendored in `_ds/`.

## Files

```
index.html                                  redirect to the deck
claude-code-context-engineering.dc.html     the deck — all 32 slides
deck-stage.js                               slide shell: scaling, nav, notes, print
support.js                                  component runtime
_ds/                                        Industry design system (tokens, styles)
```

## GitHub Pages

Settings → Pages → Source: **Deploy from a branch**, branch `gh-pages`, folder `/ (root)`.

```
git checkout -b gh-pages
git push -u origin gh-pages
```

The deck is then at `https://<user>.github.io/ai-slides/`. Push to `gh-pages` to update it.

## Slide list

**01** Title

*Chapter 01 — How the model reads*
**02** divider · **03** One Pass, No Memory · **04** Everything Is One Flat List ·
**05** Lost in the Middle

*Chapter 02 — The context window*
**06** divider · **07** What Fills the Window · **08** Quality vs. Fill ·
**09** /clear and /compact · **10** Five Levers on the Window · **11** Reading the Meter

*Chapter 03 — The levers*
**12** divider · **13** CLAUDE.md Load Order · **14** Leave vs. Extract ·
**15** Nested CLAUDE.md in a Monorepo · **16** Path-Scoped Rules ·
**17** Skills: Progressive Disclosure · **18** Anatomy of a Skill · **19** Slash Commands ·
**20** Sub-agents · **21** When a Sub-agent Pays Off · **22** Plan Mode ·
**23** The Plan on Disk · **24** Hooks · **25** Permissions and Deny ·
**26** MCP Servers · **27** What MCP Costs You

*Chapter 04 — A day of work*
**28** divider · **29** SDLC with Human Gates · **30** Gate, Artifact, Next Phase ·
**31** What Got Cheaper, What Got Dearer · **32** Defaults I Would Start From

Slides tagged `MECHANICS` in the corner describe how something works; `PRACTICE` slides are
recommendations.

## Round-tripping with the design tool

The deck was authored in a hosted design tool and this repo is a checkout of the same
files, so edits flow either way — but not simultaneously.

- **Repo → tool:** commit and push, then ask the tool to sync. It reads the changed files
  and the design updates.
- **Tool → repo:** export the folder again and commit over your working copy.

Edit in one place at a time. Concurrent edits in both mean a manual merge — the deck is one
large HTML file, so a merge conflict in it is tedious.

## License

MIT — see `LICENSE`.
