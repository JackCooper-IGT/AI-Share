# AI-Share

A library of shareable AI skills, prompts and templates, maintained as plain-text files in Git. Shared instructions are generic; each user supplies their own accounts, permissions and personal settings.

## Available skills

| Skill | Purpose | Required access |
| --- | --- | --- |
| [Estimate timesheet hours](Skills/estimate-timesheet-hours/SKILL.md) | Propose daily category totals from work evidence for user review. Does not write or submit timesheets. | Available work evidence, such as calendar entries, messages, agent activity, Git history, issue trackers or user-provided logs. No particular service is mandatory. |

## Repository layout

```text
AI-Share/
├── README.md
├── AGENTS.md
├── .gitattributes
├── .gitignore
└── Skills/
    └── estimate-timesheet-hours/
        └── SKILL.md
```

Keep skill folders directly under `Skills/`. Use descriptive, lowercase, hyphenated names rather than category folders such as `Admin/`. Group related skills in the index when the collection grows.

Add `Prompts/` for standalone reusable prompts and `Templates/` for reusable output templates when there are files to store in them. A skill's own supporting resources belong inside its skill folder.

Each skill has a `SKILL.md` entry point with YAML `name` and `description` fields followed by Markdown instructions. The name matches the skill folder.

Add supporting files only when needed:

- `references/`: supporting documentation.
- `scripts/`: reusable executable helpers.
- `assets/`: templates and other resources used by that skill.

## Installing a skill

Choose a skill from the index above. Install its entire folder, including any supporting files, into the location supported by your AI agent. Keeping files in this repository does not automatically install them.

### Ask your AI to install it

Replace `<repository URL>` with this repository's GitHub URL, then give your agent this prompt:

```text
Install the estimate-timesheet-hours skill from <repository URL>.
The skill folder is Skills/estimate-timesheet-hours.
Use your supported skill installation method and include all supporting files.
Tell me where it was installed, which revision was used, and what settings or integrations it needs.
If a skill with that name is already installed, explain the differences before replacing it.
```

For Codex, you can use the built-in installer:

```text
$skill-installer Install estimate-timesheet-hours from <repository URL>, at Skills/estimate-timesheet-hours.
```

Other agents may have different installation mechanisms. See the [official Codex skill guidance](https://learn.chatgpt.com/docs/build-skills) for current installation options.

### Install manually

1. Clone or download this repository at the revision you want to use.
2. Copy `Skills/estimate-timesheet-hours/` into your agent's supported skills directory, preserving the folder and its contents.
3. Follow that agent's instructions to discover or reload installed skills.
4. Provide the settings and authorized data access described in `SKILL.md`.

If your tool does not support installed skills, you can provide `SKILL.md` as instructions for a conversation. This does not register a persistent skill, and referenced supporting files must also be available.

### Configure and update

Skills do not supply credentials, connectors or permissions. Each user supplies their own authorized access. The timesheet skill needs a date, timezone and category rules, plus normal working-day length and rounding rules where applicable. It can use available work evidence; no particular service is mandatory.

Keep personal settings outside the shared source files. To update an installed skill, explicitly request the desired revision and preserve any local customizations. Installing a copy does not automatically keep it synchronized with this repository.

## Sharing and versions

Share a link to the individual skill folder when someone wants one skill, or the root README when they want to browse the collection. A folder link includes supporting resources that a link to `SKILL.md` alone may omit. Recipients need access to the repository if it is private.

Use a commit or release tag for a reproducible version; use the default branch when the recipient wants the latest changes. In installation prompts, state the tag or commit when a specific version matters.

The Git repository is the source distribution. No package build is required for these instruction files. Share a ZIP of an entire skill folder when a recipient needs an offline copy. Markdown remains authoritative; generate `.txt` copies only when required.

### Skill version numbers

Each skill declares its own version in `SKILL.md` frontmatter:

```yaml
metadata:
  version: "1.0.0"
```

This is a library convention for identifying an installed copy. It does not automatically select a Git revision, manage updates, or register a hosted API version.

Use `MAJOR.MINOR.PATCH` and increment the version when the skill's instructions or supporting resources change:

- Patch: corrections or clarifications that preserve the existing workflow and expectations.
- Minor: additions that preserve existing usage, such as an optional evidence source or output option.
- Major: incompatible changes to required settings, dependencies, scope or output expectations.

Keep the current version authoritative in `SKILL.md`; do not duplicate it in the catalogue. Pure root-documentation edits do not change a skill's version. When several edits are made together for one release, choose one appropriate version bump for the final change.

For a stable skill release, use a Git tag such as `estimate-timesheet-hours-v1.0.0` on the commit containing that version. Tags are repository-wide snapshots; the prefix identifies the skill being released. Create tags when releasing, not on every edit. Pin installation to that tag or a commit for reproducibility; the metadata number alone does not pin content. No release tag has been created yet.

## Where instructions belong

The root README contains the catalogue, installation, sharing and version guidance. Each skill's `SKILL.md` contains its workflow instructions, required capabilities, user settings and output expectations.

Add a skill-specific README only when substantial setup guidance justifies it. Link to it from `SKILL.md`, and keep shared installation instructions here rather than duplicating them.

## Maintaining the library

- Keep one authoritative copy of each shared file here and review changes with Git.
- Keep instructions generic. Use configurable settings or clearly labelled fictional examples for context that varies by user.
- Keep private settings, credentials and real work evidence outside this repository. Ignore rules are a convenience, not a substitute for reviewing what is committed.
- Add each new skill to the index above, including its purpose and dependencies. Add prompt and template indexes when those collections exist.
- Verify links, frontmatter and any scripts changed before sharing.

See [AGENTS.md](AGENTS.md) for guidance to AI agents editing this repository.

## Reuse terms

No licence has been selected yet. Before publishing for general reuse, add a licence that states the intended permissions.
