# Repository guidance

## Purpose and scope

AI-Share is a source library of shareable AI skills, prompts and templates. Maintain portable instructions and supporting resources. Editing the library does not authorize executing a workflow against external accounts, installing it elsewhere, or publishing the repository.

## Layout and file format

- Store each skill directly under `Skills/<lowercase-hyphenated-skill-name>/SKILL.md`. Do not add category folders such as `Skills/Admin/`; use the README index to group skills if needed.
- Use Markdown for instructions and documentation. Keep `name` and `description` in each skill entry point's YAML frontmatter; match the name to the skill folder.
- Add a skill's `references/`, `scripts/` or `assets/` only when they serve its workflow.
- Put standalone reusable prompts in `Prompts/` and standalone output templates in `Templates/`. Create those folders only when adding actual content. Keep resources specific to a skill inside that skill's folder.
- Keep one authoritative copy. Do not maintain duplicate `.txt` and `.md` versions; exports may be generated on request.
- Update the root README index and links when adding, moving, removing or materially changing shared files.
- Keep catalogue, installation, sharing and version guidance in the root README. Keep workflow instructions, required capabilities, settings and output expectations in each skill's SKILL.md. Add a skill-specific README only for substantial setup guidance; link it from SKILL.md and avoid duplicating shared instructions.

## Shared instructions

- Keep account identities, employer details, real work evidence, credentials and machine-specific paths out of shared files.
- Make settings that vary by user configurable. Clearly label fictional examples.
- State required capabilities and access. Name a service only when it is required, or explicitly identify it as an example.
- Distinguish unavailable evidence from evidence that an activity did not occur.
- Preserve each workflow's scope and authorization boundaries. In particular, the timesheet estimator proposes hours; it does not write or submit them.
- Keep instructions concise and self-contained. Reference supporting files with relative paths.

## Skill versioning

Each skill stores its version as a quoted `metadata.version` string in SKILL.md frontmatter. Use MAJOR.MINOR.PATCH: patch for compatible corrections or clarifications, minor for compatible additions, and major for incompatible changes to required settings, dependencies, scope or outputs. New stable skills start at 1.0.0; explicitly experimental skills may start at 0.1.0.

Update the version when changing a skill's instructions or supporting resources. For a group of edits in one release, apply one version bump appropriate to the final change. Root-documentation-only edits do not bump skill versions. Keep the version authoritative in SKILL.md rather than duplicating it in indexes. Metadata labels the copy; a Git tag or commit pins its exact contents.

Use `<skill-name>-v<version>` for skill release tags when explicitly asked to create a release or tag. Do not automatically create tags or commits while editing.

## Validation

Review the diff for unintended changes and private information, including new untracked files. Verify skill frontmatter, folder names, README links and referenced resources. Use an available skill validator where applicable; run changed scripts when practical. Instruction-only edits normally need a content review rather than fabricated execution tests.

Preserve unrelated user changes. Do not commit, push, publish or select a licence unless requested. Do not add blanket approval gates to routine edits in this repository.
