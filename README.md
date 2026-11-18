# LFDT-Lineth Governance

This repository holds the declarative GitHub organization configuration for LFDT-Lineth. The source of truth is [config.yaml](config.yaml), which defines team structure, formation, members, repository visibility, and team permissions. When changes are merged, CLOWarden reconciles the live organization state to match this file.

## What is here
- `config.yaml`: team structure, memberships, and repository access
- `lineth.svg` and `lineth.png`: logo assets used by the project
- `CODEOWNERS`: required reviewers for changes to `config.yaml`
- `LICENSE`: Apache 2.0

## Making changes
1. Edit `config.yaml`.
2. Keep team names and formation references defined before they are used.
3. Validate the YAML before opening a pull request.
4. Sign off every commit (`git commit -s`). The DCO check is required.
5. Read CLOWarden's validation comment on the pull request. It lists exactly what will change.
6. Merge after the required owners have reviewed it. CLOWarden applies the changes to the organization immediately.

## Rules for `config.yaml`
- **Teams need a maintainer.** Every team needs at least one maintainer, and one is enough. A team defined only by `formation` takes its maintainers and members from the teams it lists.
- **Maintainers manage the team, not repositories.** Repository access comes only from the `teams` map of each entry under `repositories`.
- **References must be defined.** Every `formation` entry and every team named under `repositories` must exist under `teams`. If an undefined reference reaches `main`, the configuration is invalid and CLOWarden cannot show what later pull requests change until it is removed.
- **Permissions** are `read`, `triage`, `write`, `maintain`, or `admin`.
- **New repositories are created from this file.** Add an entry under `repositories` and CLOWarden creates the empty repository on merge. Do not create repositories by hand: an organization ruleset restricts it.

```yaml
teams:
  - name: team-example
    maintainers:
      - github-handle
    members:
      - another-handle
repositories:
  - name: example-repo
    teams:
      lineth-admin: admin
      team-example: maintain
    visibility: public
```
