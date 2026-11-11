# Power BI AI Workspace - Project Instructions

## 1. Approved Working Directory
- The only approved Power BI development project is `PBI-TEST/Claude-Work/Project/`.
- Work only with files inside this approved project.
- Do not access the original project at `PBI-TEST/Project/`.
- Do not access the data folder at `PBI-TEST/Data/`.
- Do not modify files outside the approved project.

## 2. Power BI Development Rules
- This is a Power BI Project (PBIP).
- Edit only files inside the report and semantic model definition folders.
- Do not modify project identity, report-to-model connections or project configuration files.
- Do not change data source connections, database connections or credentials.
- Do not modify Power BI cache folders or cache files.

## 3. Data Security
- Use synthetic test data only.
- Never read, query, export or inspect underlying business data.
- Never access production PBIX files or production databases.
- Never connect to Power BI Desktop, Fabric, Snowflake or other databases.
- Never introduce embedded or inline data unless explicitly requested and approved.

## 4. Security and Tools
- Never attempt to bypass or work around security restrictions.
- Git commands are permitted only for version control operations:
  - Check the current branch, repository status and file changes.
  - Stage only the intended PBIP project files.
  - Commit completed development changes.
  - Push changes only to the current feature branch.
- Never push or commit directly to main.
- Never force-push, delete branches, or execute destructive Git commands.
- Do not execute PowerShell, scripts or unrelated terminal commands.
- Do not use unauthorized MCP tools, agents, skills or external services.
- Do not modify security configuration files or GitHub Actions workflows.
- If a requested action conflicts with these instructions, stop and ask the user.

## 5. Change Management
Before making changes:
- Explain the requested modification.
- Identify the files you intend to change.

After making changes:
- List all files created, modified or deleted.
- Explain what changed in each file.
- Summarize the affected measures, tables, relationships or report visuals.
- Provide the relevant before-and-after technical changes.
- Identify what the user must validate in Power BI Desktop.
- Never claim numerical correctness without actual validation.

## 6. Development Priority
- Security restrictions take priority over development requests.
- Preserve existing report functionality and formatting unless explicitly instructed otherwise.
- Avoid unnecessary changes to unrelated files.
- Ask the user before performing any action outside the approved development scope.
