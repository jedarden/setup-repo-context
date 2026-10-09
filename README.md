# Set up repository context

Give a coding agent different guidance where the work changes. `setup-repo-context`
inspects a repository's real workflows and helps create the smallest useful
hierarchy of `AGENTS.md` instructions.

**Read:** [the skill](skills/setup-repo-context/SKILL.md) ·
**Download:** [v0.1.0 ZIP](https://github.com/jedarden/setup-repo-context/archive/refs/tags/v0.1.0.zip) ·
**Article:** [My agents adapt to where they work in the codebase. Here’s how.](https://drafts.jedarden.com/notes/dynamic-context-with-agents-md/)

The companion article is a **private draft and requires authorized access**.
The skill and this repository are public and work independently of the article.

## What it does

- Finds instruction boundaries from existing code, test commands, and documented constraints.
- Preserves useful rules and avoids a new file in every directory.
- Names exactly which inherited defaults a local rule replaces.
- Distinguishes instruction scope, discovery, and precedence.
- Checks representative files and tasks spanning several scopes, with an honest record of checks run and gaps.

The result is a small patch or a justified no-change finding, plus evidence for
the rules. A successful command with zero tests is not treated as validation.
The skill contains Markdown and optional Codex UI metadata; it has no bundled
executables or runtime dependencies.

## Install

Review [SKILL.md](skills/setup-repo-context/SKILL.md) before installing. In Codex,
ask the built-in skill installer:

```text
Use $skill-installer to install the skill from
https://github.com/jedarden/setup-repo-context/tree/v0.1.0/skills/setup-repo-context
```

Or download and extract the versioned ZIP above. From the extracted repository
directory, install the complete skill folder into the location supported by
your agent. Current Codex documentation supports `~/.agents/skills` for user
skills and `.agents/skills` at a repository root. This user-level copy stops
if the destination already exists:

```sh
(
  set -eu
  skill_destination="$HOME/.agents/skills/setup-repo-context"
  if [ -e "$skill_destination" ] || [ -L "$skill_destination" ]; then
    printf '%s\n' 'Skill already exists; review it before replacing it.' >&2
    exit 1
  fi
  mkdir -p "$HOME/.agents/skills"
  cp -R skills/setup-repo-context "$skill_destination"
)
```

Select it with `/skills` or `$` in supported Codex interfaces. Restart the
client if a newly installed skill does not appear. Consult the
[current skill documentation](https://learn.chatgpt.com/docs/build-skills)
for your client. Other agents have their own installation and discovery rules.
Copy the skill folder, not this entire repository, into a skill directory.

## Use

Start in the repository you want to improve:

```text
Use $setup-repo-context to inspect this repository and propose the smallest
useful set of scoped AGENTS.md changes. Show a concrete patch without editing
the repository. Preserve existing rules and identify unsupported assumptions.
For representative files and a task crossing two scopes, show the instruction
chains, resulting behavior, and verification commands.
```

To apply the result:

```text
Use $setup-repo-context to implement the agreed instruction changes, preserve
unrelated edits, and verify the resulting instruction chains and check plan.
```

The skill does not assume every agent automatically reads nested files, and
does not grant permission to install tools, commit, deploy, or publish. Those
actions follow the user's request and the target repository's instructions.

## Source and license

[Forgejo](https://git.ardenone.com/jedarden/setup-repo-context) is the source of
truth; [GitHub](https://github.com/jedarden/setup-repo-context) is its read-only
mirror. The ZIP is pinned to `v0.1.0`; `main` may contain later changes.

Released under the [MIT License](LICENSE). You can use, adapt, and redistribute
the skill under those terms.
