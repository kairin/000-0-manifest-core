# 000-0-manifest-core — AI Agent Guidelines

Single source of truth for AI agents in this repository. If `CLAUDE.md` or `GEMINI.md` exists, it points to this file.

## Security and secrets

This repository is PUBLIC. Do not add secrets, tokens, email addresses, host names, IP addresses, personal data, or the names of private repositories that are not core repositories. Read `~/Apps/000-0-workspace/docs/repository-protection.md` for shared secret rules.

Before each commit, scan the change for the items above. Use `gitleaks` if it is installed.

## Protected files

Do not rewrite these without an explicit per-file instruction from the user: `.gitignore`. Read them freely. If a task needs one changed, stop and ask. `git show origin/main:<file>` is the authoritative original.

## Project overview

This repository is the public entry point for a new device. It holds the core-repository diagram in `README.md` and, when added, `scripts/bootstrap.sh`. The private repository inventory is in `000-0-manifest-private`.

## Bootstrap script rule

`scripts/bootstrap.sh` only prepares a blank device to run the `update` command. It may:

- install `git`, GitHub CLI and a Python version that `update` needs, from the repositories that are already configured;
- tell the user to run `gh auth login`;
- clone the core repositories and install the published updater release;
- start `update`.

It must not:

- install or repair any tool that `update` or the dotfiles catalog owns;
- hold personal data, host names, email addresses or private repository names;
- add package repositories, or write sudoers or policy files;
- run a provider login.

Use POSIX `sh` only. Keep the script short. Tests use stub programs and a fake `PATH`.

## Branches and pull requests

- Never push to `main` directly after the first commit. Make a branch, push it, and open a pull request.
- New branches are named `YYYYMMDD-HHMMSS-short-name`. Never delete a branch.

## Documentation

- `README.md`: for users.
- `AGENTS.md` (this file): for agents. Update it when a tool, a command or a rule changes.

## Shared workspace policy

Read `~/Apps/000-0-workspace/docs/repository-protection.md` for delivery, branches, visibility, Git identity, and secrets. Read `~/Apps/000-0-workspace/docs/agent-instruction-files.md` for pointer rules and shared conduct. Read `~/Apps/000-0-workspace/docs/update-and-development-tools.md` before maintenance work. These references are instructions to read. If required policy is missing, the affected task is incomplete; do not clone, install, or reconstruct it.
