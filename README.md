# LFDT-Lineth Governance

This repository holds the declarative GitHub organization configuration for LFDT-Lineth. The source of truth is [config.yaml](config.yaml), which defines teams, members, repository visibility, and team permissions. When changes are merged, CLOWarden reconciles the live organization state to match this file.

## What is here
- `config.yaml`: teams, memberships, and repository access
- `CODEOWNERS`: required reviewers for changes to `config.yaml`
- `LICENSE`: Apache 2.0

## Making changes
1. Edit `config.yaml`.
2. Keep team names defined before they are referenced by repositories.
3. Validate the YAML before opening a pull request.
4. Merge after the required owners have reviewed it.
