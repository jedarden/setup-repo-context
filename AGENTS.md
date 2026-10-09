# Repository guidance

This is a portable Markdown skill, with Codex UI metadata in
`skills/setup-repo-context/agents/openai.yaml`. `README.md` owns installation
and release instructions; `SKILL.md` owns the agent workflow. Keep them aligned.

Preserve the distinction between instruction scope, discovery, and precedence.
Derive repository rules from evidence and preserve existing requirements. Do
not make this skill imply authorization to commit, deploy, or publish.

For changes, validate the skill frontmatter and referenced files with the
available skill-creator validator. Exercise substantial behavior changes in a
disposable repository; distinguish a proposed feature plan from checks actually
run. Test installation into a disposable destination instead of replacing a
user's installed skill. This package needs no application build or npm setup.

The article link targets a private draft. Keep that access requirement explicit
until its author separately authorizes public article publication.

Forgejo origin is authoritative; GitHub is a server-side mirror. Work on main,
stage precise paths, and preserve released tags. No GitHub Actions workflow is
needed. Initial release ownership is tracked by jedarden-d32329aa in the
jedarden.com repository, including package and reciprocal-link verification.
