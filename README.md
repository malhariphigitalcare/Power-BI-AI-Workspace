# Power BI AI Workspace

An AI-assisted Power BI development environment using Power BI Project (PBIP), Claude Code Web, GitHub version control and automated security checks.

## 1. Project Overview

This repository provides a controlled environment for AI-assisted Power BI development.

Claude Code helps developers modify approved Power BI report and semantic model definitions while repository-level instructions and security controls help protect sensitive files, project configuration and development boundaries.

**Approved development project:**

`PBI-TEST/Claude-Work/Project/`

Synthetic test data is used for development and validation.

### Project Objectives

- Develop Power BI reports using AI assistance.
- Maintain Power BI source definitions in GitHub using PBIP.
- Automate feature branch creation, commits and pushes through Claude Code Web.
- Maintain version history and review changes through GitHub Pull Requests.
- Perform static validation before committing changes.
- Validate report functionality and calculations in Power BI Desktop before merging.
- Maintain approved PBIX releases separately from the GitHub source repository.

## 2. Repository Structure

```text
Power-BI-AI-Workspace/
│
├── .claude/
│   └── settings.json
│
├── .github/
│   └── workflows/
│       └── security-checks.yml
│
├── PBI-TEST/
│   └── Claude-Work/
│       └── Project/
│           ├── SecurityTest/
│           │   ├── probe.csv
│           │   └── probe.txt
│           │
│           ├── test_sales.Report/
│           ├── test_sales.SemanticModel/
│           └── test_sales.pbip
│
├── CLAUDE.md
├── .gitignore
└── README.md
```

### Important Project Directories

| Directory | Purpose |
|---|---|
| `test_sales.Report/` | Contains report pages, visuals, layouts and report definitions. |
| `test_sales.SemanticModel/` | Contains semantic model definitions, tables, measures, relationships and TMDL files. |
| `SecurityTest/` | Contains deliberately included synthetic files used for security testing. |
| `.claude/` | Contains Claude Code permission configuration. |
| `.github/workflows/` | Contains automated GitHub Actions workflows. |

## 3. Security Files and Their Responsibilities

| File | Purpose |
|---|---|
| `CLAUDE.md` | Defines project instructions, security boundaries, Power BI development standards, validation requirements and Git workflow guidance. |
| `.claude/settings.json` | Defines Claude Code permission restrictions and protected file access rules. |
| `.gitignore` | Excludes specified local files, source datasets, Power BI files and cache folders from Git. |
| `.github/workflows/security-checks.yml` | Runs automated repository security checks. |
| `README.md` | Documents repository structure, security controls and development processes. |

### Responsibilities of CLAUDE.md

The root-level `CLAUDE.md` provides instructions covering:

- Approved Power BI working directory.
- Data security and project boundaries.
- Git version control operations.
- DAX and semantic model development.
- TMDL development conventions.
- Report visual creation and formatting.
- Visual positioning and layout management.
- File formatting and line-ending consistency.
- Static validation.
- Power BI Desktop validation.
- Development completion summaries.

### Responsibilities of .claude/settings.json

The root-level `.claude/settings.json` configures:

- File reading restrictions.
- File editing restrictions.
- Protected project and configuration files.
- Power BI cache restrictions.
- Working-directory access restrictions.
- Restricted terminal, PowerShell and MCP tools.
- Restrictions on Agent, Skill and built-in web tools.

## 4. GitHub Actions Security Checks

Workflow location:

`.github/workflows/security-checks.yml`

Workflow name:

**Power BI Security Checks**

The workflow runs when:

- Changes are pushed to the `main` branch.
- A Pull Request targets `main`.
- A workflow is manually triggered.

### Check 1: Restricted File Detection

The workflow checks all currently tracked repository files for restricted file types.

The following file extensions are blocked:

- PBIX, PBIT and PBIDS.
- ABF.
- XLSX, XLS, XLSM and XLSB.
- CSV and TSV.
- Parquet.
- DB, SQLite and other specified database formats, including MDB, MDF, LDF and BAK.

Power BI `.pbi` cache folders are also prohibited.

**Exception:** The approved synthetic test file below is permitted by the workflow:

`PBI-TEST/Claude-Work/Project/SecurityTest/probe.csv`

This exception applies only to the automated GitHub Actions file check. It does not override Claude Code file-reading restrictions.

### Check 2: TMDL Content Validation

The workflow scans tracked `.tmdl` files for two prohibited patterns:

```text
Binary.FromText
DATATABLE(
```

If either pattern is detected, the workflow fails.

These checks are intended to prevent specific forms of embedded data from being introduced into the semantic model.

### Check 3: Workflow Result

The workflow produces one of two outcomes.

**Success**

- No prohibited tracked files are found.
- No prohibited TMDL patterns are detected.

**Failure**

- A restricted file or Power BI cache folder is found.
- A prohibited TMDL pattern is detected.

The failed status can prevent a Pull Request from being merged when the corresponding check is configured as required in the repository branch protection ruleset.

### Required Status Check

The repository uses the following required GitHub Actions status check:

`Validate committed files and TMDL`

The branch protection ruleset requires the Pull Request process and successful completion of the configured check.

## 5. Claude Code Security Restrictions

The repository-level `.claude/settings.json` defines Claude Code permission restrictions intended to:

- Block reading and editing specified data file types.
- Protect Power BI cache folders.
- Protect the original project and source data folders.
- Protect security instructions and configuration files.
- Restrict PowerShell execution.
- Block MCP tools, Agent, Skill and built-in web tools.
- Prevent bypassing configured permission restrictions.

### Git Version Control Permissions

Git version control operations are permitted for approved development activities.

The root-level `CLAUDE.md` instructs Claude to:

- Check the current branch, repository status and file changes.
- Stage only intended PBIP project files.
- Commit completed development changes.
- Push changes only to the current feature branch.
- Never push or commit directly to `main`.
- Never force-push, delete branches or execute destructive Git commands.

PowerShell, scripts and unrelated terminal commands remain prohibited by project instructions.

**Important:** Git permissions and development boundaries must be understood separately:

- `.claude/settings.json` provides the configured permission restrictions.
- `CLAUDE.md` provides project-level development instructions.
- The Git restrictions in `CLAUDE.md` are instructions, not a technically enforced Git command allowlist.

Claude Code may request permission before executing Git commands, depending on the session permission settings.

### GitHub Secret Protection

GitHub Secret Protection and Push Protection are enabled to help prevent sensitive credentials and secrets from being committed to the repository.

### Security Limitations

Permission settings must be verified in the actual Claude Code execution environment. Instructions in `CLAUDE.md` are not substitutes for technically enforced permissions.

## 6. GitHub Development and Review Process

The repository uses an AI-assisted GitHub workflow for Power BI PBIP development.

### 6.1 Development Workflow

1. Start a new Claude Code Web session using the `Power-BI-AI-Workspace` repository.
2. Select the latest `main` branch as the starting branch.
3. Claude Code Web assigns an isolated feature branch for the development task.
4. Provide the Power BI development requirement in a single prompt.
5. Claude inspects the existing PBIP project, measures, TMDL definitions and report visuals.
6. Claude implements the requested changes.
7. Claude performs static validation and reviews the Git diff.
8. Claude stages and commits only the intended PBIP files.
9. Claude pushes the completed changes to the feature branch.
10. The developer creates a Pull Request targeting `main` using the Claude Code Web or GitHub interface.

### 6.2 Pull Request Review

After the Pull Request is created:

1. Review the modified and newly created files under the **Files changed** tab.
2. Confirm that only the intended files are included.
3. Review the DAX calculations and report definition changes.
4. Confirm that existing visuals and model functionality remain unchanged unless the requirement specifically involves them.
5. Check that the required GitHub Actions security checks pass.
6. Confirm that there are no unexpected merge conflicts.

### 6.3 Power BI Desktop Validation

Power BI Desktop validation must be performed before merging the Pull Request.

The validation process is:

1. Download the feature branch ZIP from GitHub.
2. Extract the ZIP into a separate local validation folder.
3. Open the `.pbip` file in Power BI Desktop.
4. Configure local data-source parameters, such as `DataFolderPath`, to point to the approved synthetic test data location.
5. Refresh the report and resolve any data-loading issues.
6. Validate newly created or modified DAX measures.
7. Verify report visuals, formatting, alignment and positioning.
8. Confirm existing report functionality has not been unintentionally affected.

The local data-source parameter must not expose personal file paths or credentials in the public GitHub repository.

### 6.4 Pull Request Merge

Only after successful Power BI Desktop validation:

1. Confirm the user has completed validation.
2. Confirm the required GitHub Actions checks have passed.
3. Merge the Pull Request into `main`.
4. Delete the temporary feature branch after successful merging.

`main` represents the approved Power BI development source.

### 6.5 Branch Management

| Branch | Purpose |
|---|---|
| `main` | Latest approved Power BI project source. |
| `claude/*` | Feature branches automatically assigned by Claude Code Web for individual development tasks. |
| `setup/*` or `docs/*` | Separate branches used for repository configuration or documentation changes. |

Guidelines:

- Use a separate feature branch for each independent development task.
- Start new development sessions from the latest `main`.
- Continue related changes within the same task session and branch.
- Do not unnecessarily create or reset an existing feature branch.
- Use fast-forward-only updates when synchronizing a feature branch with `main`, where appropriate.
- Delete temporary branches after successful merging.

## 7. Important Security Limitations

The current automated workflow is a focused security check, not a complete security scanner.

It currently does not:

- Detect every possible way of embedding data into TMDL.
- Validate all Power Query data-source changes.
- Scan all files for passwords, API keys or other secrets through the custom workflow itself.
- Validate numerical correctness of Power BI calculations.
- Validate actual visual rendering in Power BI Desktop.
- Independently enforce approval for changes to security configuration files.
- Guarantee that all Git operations comply with the project instructions.

These areas require additional controls and review.

GitHub Secret Protection and Push Protection provide additional credential-related safeguards, but they do not replace the custom workflow.

The automated workflow scans the current tracked repository contents. It does not independently inspect every historical commit.

## 8. Power BI Development and Release Process

PBIP is maintained in GitHub as the primary development source.

### 8.1 PBIP Development

The development process follows these steps:

1. Claude Code implements the requested changes in the PBIP project.
2. Changes are committed and pushed to a feature branch.
3. A Pull Request is created against `main`.
4. The developer reviews the changes and GitHub Actions results.
5. The feature branch ZIP is downloaded and opened in Power BI Desktop.
6. Local data-source parameters are configured as required.
7. The model, data refresh, DAX calculations, report visuals and existing functionality are validated.
8. The Pull Request is merged into `main` only after successful validation.

### 8.2 PBIX Release Management

After successful validation and approval:

- Save the approved report as a versioned PBIX file.
- Keep PBIX backups and release files outside the GitHub source repository.
- Distribute approved PBIX releases to other developers as required.
- Maintain separate baseline backups before significant development changes.

Example release naming:

`Finance_V1_2026-11-10.pbix`

`Finance_V2_2026-11-12.pbix`

PBIX files are excluded from the GitHub repository through `.gitignore`.

The PBIP source in GitHub and the approved PBIX release are maintained separately.

## 9. Development Principle

**Claude Code implements. GitHub manages versions and reviews changes. Automated checks validate defined security conditions. Power BI Desktop validates the actual report. The developer approves, merges and distributes the final PBIX release.**
