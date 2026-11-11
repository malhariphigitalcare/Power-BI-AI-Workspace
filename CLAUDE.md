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

## 6. Power BI PBIP Development Standards

### 1. Semantic Model Development

- Inspect existing tables, columns, relationships, measures and TMDL definitions before making changes.
- Follow existing measure naming conventions, descriptions, indentation and formatting.
- Add new measures to the appropriate existing measures table.
- Reuse existing measures when appropriate instead of duplicating business logic.
- Verify that referenced tables and columns exist.
- Generate a unique lineageTag GUID for every new measure.
- Preserve existing measures, relationships, columns and model functionality unless explicitly required.

### 2. Report Visual Development

- Inspect existing report pages and visual definitions before creating new visuals.
- Use an existing visual of the same type as a template whenever possible.
- Preserve existing visual types, formatting, font sizes, styling and configuration.
- Generate unique visual IDs and filter names.
- Ensure visual folder names match the corresponding internal visual names.
- Update all measure references consistently, including projections, query references, native query references, sorting and filters.
- Do not add explicit visual titles unless requested.
- Modify existing visuals only when required by the requested layout.

### 3. Report Layout Management

- Inspect report canvas dimensions and existing visual positions before adding or repositioning visuals.
- Maintain consistent visual dimensions, spacing, alignment and formatting.
- Keep all visuals within the report canvas.
- Prevent visual overlaps.
- Preserve existing visual positions unless the requested enhancement requires a layout change.
- For multiple rows of KPI cards, maintain balanced horizontal alignment and consistent spacing.

### 4. File Formatting and Consistency

- Preserve the existing line-ending format when creating or modifying PBIP files. For TMDL and JSON files, match the corresponding existing project files, including Windows-style CRLF where applicable.
- Follow the indentation and formatting conventions of neighbouring TMDL and JSON files.
- Avoid unrelated formatting changes.
- Do not reformat entire files unnecessarily.

### 5. Static Validation

Before committing:

- Inspect modified TMDL and JSON file contents.
- Verify measure names, DAX references, lineageTag GUIDs, visual IDs and filter names.
- Verify visual folder names match their internal visual names.
- Verify visual positions, dimensions, alignment and canvas boundaries.
- Confirm existing visuals have not been unintentionally changed.
- Do not execute Python, PowerShell or other scripts for static validation.
- Review Git status and Git diff.
- Confirm only the files required for the requested enhancement have changed.
- Stage and commit only the intended files.

### 6. Power BI Desktop Validation

- Power BI Desktop validation must be completed by the user.
- Never claim that a report has been successfully tested in Power BI Desktop unless the user confirms it.
- Never claim numerical correctness based only on static file inspection.
- Provide clear validation steps covering model loading, DAX results, visual rendering, formatting and report interactions.
- The Pull Request must remain unmerged until the user confirms successful Power BI Desktop validation.

### 7. Development Completion Summary

For every development task, provide a final summary containing:

- Business requirement implemented.
- DAX measures created or modified.
- Report visuals created or modified.
- Files changed.
- Visual positioning changes, where applicable.
- Static validation results.
- Feature branch and commit details.
- Push status.
- Remaining Power BI Desktop validation steps.

## 7. Development Priority
- Security restrictions take priority over development requests.
- Preserve existing report functionality and formatting unless explicitly instructed otherwise.
- Avoid unnecessary changes to unrelated files.
- Ask the user before performing any action outside the approved development scope.
