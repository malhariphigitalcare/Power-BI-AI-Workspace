# Power BI AI Workspace

An AI-assisted Power BI development project using Power BI Project (PBIP), Claude Code and GitHub security controls.

## 1. Project Overview

This repository provides a controlled environment for AI-assisted Power BI development.

Claude Code can help developers modify approved Power BI report and semantic model definitions while security controls help protect data files, project configuration and repository instructions.

**Approved development project:**

`PBI-TEST/Claude-Work/Project/`

Synthetic test data is used for development and validation.

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

## 3. Security Files and Their Responsibilities

| File | Purpose |
|---|---|
| `CLAUDE.md` | Provides project instructions and development boundaries for Claude. |
| `.claude/settings.json` | Defines Claude Code permission restrictions. |
| `.gitignore` | Prevents specified local files and cache folders from being added to Git. |
| `.github/workflows/security-checks.yml` | Runs automated repository security checks. |
| `README.md` | Documents the project and its security controls. |

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

- PBIX, PBIT and PBIDS
- ABF
- XLSX, XLS, XLSM and XLSB
- CSV and TSV
- Parquet
- DB, SQLite and other specified database formats

Power BI `.pbi` cache folders are also prohibited.

**Exception:** The approved synthetic test file below is permitted by the workflow:

`PBI-TEST/Claude-Work/Project/SecurityTest/probe.csv`

This exception applies only to the automated GitHub Actions file check. It does not override Claude's file-reading permissions.

### Check 2: TMDL Content Validation

The workflow scans tracked `.tmdl` files for two prohibited patterns:

```text
Binary.FromText
DATATABLE(
```

If either pattern is detected, the workflow fails.

These checks are intended to prevent specific forms of embedded data from being introduced into the semantic model.

### Check 3: Workflow Result

The workflow produces one of two outcomes:

**Success**
- No prohibited tracked files are found.
- No prohibited TMDL patterns are detected.

**Failure**
- A restricted file or Power BI cache folder is found.
- A prohibited TMDL pattern is detected.

The failed status can prevent a Pull Request from being merged when the corresponding check is configured as required in the branch protection ruleset.

## 5. Claude Code Security Restrictions

The repository-level `.claude/settings.json` defines restrictions intended to:

- Block reading and editing specified data file types.
- Protect Power BI cache folders.
- Protect the original project and source data folders.
- Protect security instructions and configuration files.
- Restrict terminal and PowerShell execution.
- Restrict MCP tools, Agent, Skill and built-in web tools.
- Prevent bypassing configured permission restrictions.

The root-level `CLAUDE.md` provides additional development instructions and identifies the approved PBIP working directory.

Permission settings must be verified in the actual Claude Code execution environment. Instructions in `CLAUDE.md` are not substitutes for technically enforced permissions.

## 6. GitHub Development and Review Process

The intended development process is:

1. Start from the approved `main` branch.
2. Create a separate working branch for a development task.
3. Make and review PBIP definition changes.
4. Commit and push the changes.
5. Open a Pull Request targeting `main`.
6. Allow GitHub Actions security checks to run.
7. Obtain the required review and approval.
8. Merge the approved changes into `main`.

Branch protection and required status checks must be configured in GitHub repository settings.

## 7. Important Security Limitations

The current automated workflow is a focused security check, not a complete security scanner.

It currently does not:
- Detect every possible way of embedding data into TMDL.
- Validate all Power Query data-source changes.
- Scan all files for passwords, API keys or other secrets.
- Validate numerical correctness of Power BI calculations.
- Independently enforce approval for changes to security configuration files.

These areas require additional controls and review.

The workflow scans the current tracked repository contents. It does not independently inspect every historical commit.

## 8. Power BI Development and Release Process

PBIP is maintained in GitHub as the development source.

After AI-assisted development:

1. Review the technical changes in GitHub.
2. Validate the updated PBIP in Power BI Desktop.
3. Check calculations, visuals and data refresh.
4. Save the approved report as a versioned PBIX.
5. Distribute the PBIX to other developers.

Example release naming:

`Finance_V1_2026-11-10.pbix`

`Finance_V2_2026-11-12.pbix`

PBIX releases are maintained separately from the GitHub source repository.

## 9. Development Principle

**Claude develops. GitHub tracks and reviews. Automated checks inspect defined security conditions. Power BI Desktop validates. The developer approves and distributes the final PBIX.**
