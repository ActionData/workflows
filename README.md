# ActionData Shared Workflows

Reusable GitHub Actions workflows for the ActionData org.

## Available Workflows

### `validate-openspec`

Validates OpenSpec proposal documents against a required template structure.

**Checks:**
- Title format (`# OpenSpec Proposal: \`name\``)
- Required metadata fields (Phase, Specs Affected, Dependencies) are present and non-placeholder
- Required sections (Summary, Motivation, Detailed Design, Integration Points, Testing Strategy, Migration / Rollback, References)
- Sections contain content
- Dependency cross-references resolve to known proposal filenames
- Convention checks (e.g., MCP/CRM misuse)

**Usage:**

```yaml
# .github/workflows/validate-openspec.yml
name: Validate OpenSpec Proposals

on:
  pull_request:
    paths: ['docs/proposals/**']
  push:
    paths: ['docs/proposals/**']

jobs:
  validate:
    uses: ActionData/workflows/.github/workflows/validate-openspec.yml@main
```

**Inputs:**

| Input | Default | Description |
|---|---|---|
| `proposals_dir` | `docs/proposals` | Path to the proposals directory |

**Custom proposals directory:**

```yaml
jobs:
  validate:
    uses: ActionData/workflows/.github/workflows/validate-openspec.yml@main
    with:
      proposals_dir: specs/proposals
```
