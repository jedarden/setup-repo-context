---
name: setup-repo-context
description: Design or improve scoped AGENTS.md instructions from a repository's actual workflows. Use when asked to set up, audit, or reorganize repository context for coding agents; ordinary code changes do not require this workflow.
---

# Set up repository context

Create the smallest useful instruction hierarchy: shared rules at their common
ancestor, specialized guidance where the work changes. Every proposed rule
should answer: **what will an agent do differently, and what evidence supports
that choice?** A root file alone may be sufficient.

## Establish the current agreement

- Determine the repository root and the requested scope. Inspect the working
  tree and applicable existing instructions before edits; preserve unrelated
  changes and existing requirements.
- Honor the requested mode. A request to review or propose produces findings
  and a concrete patch for review. A request to implement authorizes scoped
  instruction edits without another confirmation. Installation, commits,
  publication, and changes to agent configuration require their own existing
  authority; this skill does not supply it.
- Inventory instruction files and relevant package manifests, test scripts,
  CI configuration, contribution docs, and representative source files. Use
  bounded searches. Exclude dependency caches, generated output, vendored
  code, and unrelated repositories from broad traversal.
- Identify the agent environment from available context. Account for its
  supported instruction filenames, overrides, and configuration. Do not
  assume every file named `AGENTS.md` is automatically loaded or that two
  instruction files in one directory are combined.

## Find boundaries from evidence

Look for changes in test commands, working directories, compatibility
requirements, generation workflows, interface conventions, and data migration
rules. Verify candidates against the repository instead of assigning rules
from directory names alone.

For each useful boundary, record its path, the decision that changes there,
and a source supporting the rule. Inspect command definitions and their
prerequisites; distinguish an existing command from one successfully run.
Never invent a runnable check to fill a template. If a command or constraint
cannot be established, describe the uncertainty outside the instruction patch.

Prefer a parent rule with a precise scope over another file when that is
clearer. Do not add a file for every directory, duplicate inherited text, or
import the author's personal tools and policies into an unrelated project.
Place generation guidance in a maintained ancestor or source directory, not
inside generated or vendored output.

## Write the minimum useful guidance

Keep standing rules brief. Link to existing detailed references for procedures
that only some tasks need. Preserve meaningful rules when reorganizing them;
explain any proposed removal or replacement.

Include exact working directories and verified command definitions where
available. Describe the trigger and success condition of a check. Keep
repository-wide requirements at the root and local additions at the narrowest
useful boundary.

Name any default being replaced, verify that it applies to the affected files,
and limit the replacement to its actual scope. A local migration check replacing
a backend test *default for SQL-only changes* does not waive tests for application
code in the same task. Ambiguous
conflicts need resolution; proximity alone does not explain the intended rule.
Preserve higher-priority instructions and authorization boundaries.

Keep these three concepts distinct:

- **Scope:** the files a rule governs, normally the directory subtree.
- **Discovery:** how the current agent finds and reads that rule.
- **Precedence:** how applicable instructions resolve an explicit conflict.

When compatible with the environment, add a short root rule to inspect the
applicable nested instructions before editing each area, including when a task
crosses into a new subtree. Already-read sibling rules may remain in the
conversation; that does not make them applicable everywhere.

For Codex-specific loading claims, consult the current
[official AGENTS.md documentation](https://learn.chatgpt.com/docs/agent-configuration/agents-md).
Its documented startup chain follows the project root to the starting working
directory; deliberate inspection during a task is a separate action. Do not
claim automatic nested discovery without checking the actual environment.

## Verify decisions and report evidence

Review the proposed or implemented diff for lost requirements, contradictions,
repetition, unsupported commands, broken references, and excessive combined
instruction size along a path.

For a representative file in each changed scope, show its applicable
instruction chain, any replaced default, the resulting action, and the checks
with working directories. Include one task spanning two scopes: show how the
next scope is discovered and combine the checks for all affected files.

Use a realistic task to test behavior, such as adding a field to both a route
and an existing database schema. A useful plan names the new migration and
upgrade check as well as the route check; merely listing instruction filenames
does not establish that the guidance worked. Keep a plan-only evaluation
separate from an actual agent run or successful command execution. Run a
disposable example only when authorized and useful; do not modify product code
merely to exercise these instructions.

Return the changed or proposed paths, why each boundary exists, evidence for
the rules, the representative task results, and any remaining uncertainty.
Respect existing verification gates. State checks not run and why. If the
existing instructions already meet the need, report that without adding files.
