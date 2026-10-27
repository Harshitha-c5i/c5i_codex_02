---
name: desktop-web-migration
description: Assess a legacy desktop business application for migration to the web. Use to inventory its UI, business logic, data and database dependencies, compatibility and security risks, and produce a phased migration plan. Requires explicit user approval before any code or configuration is changed.
---

# Desktop to web migration assessment

Use this skill to investigate a legacy desktop business application and prepare a reviewable migration assessment. The default deliverable is analysis and a plan, not implementation.

## Approval gate

- You may inspect project files and produce findings, diagrams, risk analysis, and a migration plan without approval.
- Do not create, edit, move, or delete application code, tests, build configuration, deployment configuration, database schema, or other implementation files until the user explicitly approves the proposed implementation.
- Before asking for approval, finish the investigation and present a concrete proposal: scope, target architecture, affected areas/files where known, migration phases, validation approach, and material risks.
- Approval must be explicit and must apply to the proposed scope. A request to analyze, assess, or plan is not approval to implement. If the user approves only part of the proposal, limit changes to that part.
- After approval, make only the approved changes. If implementation reveals a material scope change or a new high-impact risk, stop before that additional change and present an updated proposal for approval.
- Do not treat this approval gate as a reason to delay read-only discovery or preparation of the plan.

## Assessment workflow

### 1. Establish scope and evidence

- Identify the application purpose, business workflows, user roles, supported operating systems, deployment model, and migration goals from repository evidence and user-provided context.
- Inspect documentation, project manifests, source, tests, schemas, deployment files, and configuration examples. Avoid exposing secrets; report the presence and location of sensitive configuration without reproducing its values.
- Distinguish observed facts from assumptions and unknowns. Cite paths and symbols for repository findings; do not claim a dependency or behavior without evidence.
- If important context is unavailable, continue with repository-grounded analysis and list targeted questions or assumptions in the deliverable.

### 2. Inventory the existing application

Document the following, as applicable:

- **UI:** windows, forms, screens, menus, dialogs, navigation, accessibility, user roles, and interaction patterns.
- **Business logic:** domain rules, calculations, validation, workflows, reports, batch jobs, and where each rule is implemented.
- **Data and database:** database engine, schemas, tables, relationships, constraints, stored procedures, queries, files, local caches, and data ownership.
- **Dependencies and integrations:** operating-system APIs, hardware/peripherals, file formats, identity systems, network services, external APIs, scheduled tasks, and third-party libraries.
- **Operational behavior:** installation, updates, backups, recovery, audit logging, monitoring, concurrency, and offline use.

Use an evidence table with component, current responsibility/dependency, evidence, migration concern, and confidence. Mark missing evidence as unknown rather than filling gaps with guesses.

### 3. Assess security and compatibility risks

For each material risk, state likelihood or uncertainty, impact, evidence, and a practical mitigation or discovery action. Consider:

- Authentication, authorization, roles, session handling, identity integration, and least privilege.
- Sensitive data exposure, encryption in transit and at rest, secret handling, logging, auditability, retention, and backup access.
- Input validation, injection risks, file upload/download handling, cross-site request forgery, cross-site scripting, and API access controls where relevant.
- Data migration correctness, integrity constraints, duplicate or malformed records, privacy, retention, rollback, and downtime.
- Browser and operating-system support, UI behavior differences, accessibility, localization, printing, scanners, serial/USB devices, local file access, and offline workflows.
- Network latency, concurrent access, transaction boundaries, scaling, availability, and recovery objectives.
- Licensing, unsupported runtimes, vendor lock-in, and compatibility of existing integrations.

Do not perform intrusive security testing or access production systems as part of this assessment. Keep findings at the level supported by available evidence.

### 4. Propose a target architecture

Describe a candidate web architecture that maps current responsibilities to web UI, API/backend services, data storage, identity, integrations, and operations. Tie each proposed component to an observed requirement. Identify decisions that need stakeholder input; do not present assumptions as settled choices. Include an explicit plan for desktop-only capabilities such as printing, peripherals, local files, and offline use.

### 5. Build a phased migration plan

Provide ordered phases with objectives, scope, dependencies, deliverables, validation/exit criteria, risks, and rollback or fallback strategy. A useful starting structure is:

1. Discovery and stakeholder validation.
2. Data and integration foundations, including security and identity design.
3. A small end-to-end pilot workflow.
4. Incremental workflow migration with coexistence or controlled rollout.
5. Data cutover, operational readiness, and user transition.
6. Decommissioning after reconciliation and acceptance.

Tailor or combine phases to the evidence. Identify parallel-running needs, data synchronization rules, cutover criteria, and a way back for each phase where applicable. Avoid unsupported dates, estimates, or claims of guaranteed parity.

## Deliverable format

Unless the user asks for another format, return:

1. Executive summary and scope.
2. Evidence-based inventory of UI, business logic, data/database, integrations, and operations.
3. Current architecture and key data/workflow flows.
4. Candidate target architecture and unresolved decisions.
5. Security and compatibility risk register with mitigations.
6. Phased migration plan with dependencies and exit criteria.
7. Assumptions, unknowns, and targeted questions.
8. Approval request for a clearly bounded next implementation phase, if implementation is desired.

Keep the report actionable and distinguish facts, inferences, and recommendations.

## If implementation is approved

- Reconfirm the approved scope in your working plan and inspect the applicable project instructions before editing.
- Implement incrementally at the approved phase boundary. Preserve existing behavior until its replacement is validated, and avoid unrelated refactoring.
- Add or update tests and migration/operations documentation appropriate to the approved change.
- Run the repository's documented checks and report exact commands and results. Do not claim checks passed unless run.
- Review the diff for unintended changes, data-loss paths, exposed secrets, and unapproved scope before reporting completion.
