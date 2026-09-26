# Repository guide

## Scope and safe checks

This is a collection of Kandji/macOS administration examples. `Scripts/` holds Bash and Zsh scripts, `Configuration Profiles/` holds `.mobileconfig` profiles, and `Wiki_Assets/` holds documentation screenshots. Preserve the copyright/license notice in `README.md` and existing script guidance.

There is no application build, dependency manifest, automated test suite, or CI workflow. Check each changed script using its shebang: `bash -n Scripts/Name.sh` or `zsh -n Scripts/Name.sh`. On macOS, `plutil -lint "Configuration Profiles/Name.mobileconfig"` checks profile syntax without installation. Inspect affected commands and exit paths as well; syntax does not establish device-management behavior.

Scripts here can remove profiles or firmware passwords, install software, change sudoers/hostnames, or perform OS updates. Never execute them as a smoke test on the current Mac, install profiles, or enroll/change a managed device without explicit authorization for that target and operation. Runtime validation needs an authorized disposable Mac/VM with the relevant OS and management state. Treat enrollment tokens and administrator credentials as sensitive; do not reproduce profile or credential values in logs.

## Completion

Start with `git status --short` and preserve unrelated work. Complete authorized local edits and static checks autonomously, repairing issues caused by the change. Ask only when a material decision or device-action boundary remains unresolved; keep doing independent safe work. For prose-only changes, inspect referenced paths and run `git diff --check`. Report changed paths, checks actually executed, and exact runtime prerequisites still missing, keeping static validation separate from device proof.
