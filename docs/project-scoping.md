\# Progressive Data Sync Tool — Project Scoping Document



\*\*Project:\*\* `prog-data-sync-tool`

\*\*Organization:\*\* Bluebonnet Data

\*\*Status:\*\* Draft / Open for Discussion

\*\*Last updated:\*\* TBD



\---



\## 1. Purpose



This document is intended to help organize early discussion and development for the Progressive Data Sync Tool project.



The goal is to turn a broad idea into a clearer set of use cases, open questions, technical workstreams, and possible MVP paths so contributors can begin working in parallel without losing sight of the campaign need.



This is a working document. It is expected to evolve as the team clarifies requirements, evaluates tools, and identifies the first campaign use case.



\---



\## 2. Executive Summary



Political campaigns and progressive organizations often rely on multiple data platforms that do not easily communicate with each other. Donor, voter, volunteer, outreach, and call-time data may live across tools such as NGP, VAN/VoteBuilder, CallTimeAI, L2, ActBlue, and other campaign technology platforms.



For smaller campaigns and organizations, moving data between these systems is often manual, expensive, error-prone, or dependent on custom one-off volunteer work. Existing commercial tools may solve parts of this problem, but they are not always accessible to the kinds of campaigns and organizations Bluebonnet supports.



This project explores whether Bluebonnet can build a reusable, open-source framework or toolkit for common political data sync needs.



The initial focus should be narrow:



\* Identify one or two concrete campaign use cases.

\* Evaluate existing open-source tools.

\* Define a safe and achievable MVP.

\* Build something useful enough to validate the approach.

\* Document patterns that can be reused for future campaigns.



Longer term, this project could become a reusable toolkit or platform that helps Bluebonnet volunteers, and eventually campaign staff or data volunteers, configure, run, monitor, and audit common data sync workflows.



\---



\## 3. Background



This project emerged from overlapping needs across current Bluebonnet campaign projects. The common pattern is that campaigns need to move, compare, or reconcile data between political tools.



The initial discussion identified a broad need for plug-and-play data sync automations for common political data platforms. There is also interest in eventually supporting Zapier-like triggered workflows, though that is likely a later phase.



The project should build on existing open-source progressive data tooling where possible rather than reinventing everything from scratch.



Potential existing resources include:



\* Parsons

\* Community Tech Alliance / dbt-cta

\* dlt

\* Dagster

\* Automatisch

\* Activepieces

\* n8n



\---



\## 4. Problem Statement



Bluebonnet-supported campaigns often need to synchronize, compare, or reconcile data across political technology platforms. Today, these workflows are often handled manually, through one-off scripts, or through tools that may be too expensive or inaccessible for smaller campaigns.



This creates several problems:



\* Data may become stale or inconsistent across systems.

\* Volunteers may duplicate effort across campaigns.

\* Manual imports and exports increase the risk of errors.

\* Campaigns may lack visibility into which records match, conflict, or are missing.

\* There may be limited auditability when data is added, changed, or removed.

\* Sensitive campaign, voter, volunteer, and donor data must be handled carefully.



The project should investigate whether Bluebonnet can create reusable, secure, and auditable patterns for common political data sync needs.



\---



\## 5. Project Goals



The project should aim to:



1\. Identify common data sync needs across current and future campaigns.

2\. Evaluate existing open-source tools that could support those needs.

3\. Build on existing progressive data tooling where possible, especially Parsons.

4\. Define a safe and achievable MVP.

5\. Create reusable patterns for data extraction, comparison, matching, syncing, logging, and auditing.

6\. Reduce duplicated volunteer effort across campaigns.

7\. Provide a foundation for future plug-and-play data sync automations.

8\. Keep security, privacy, and auditability central from the beginning.

9\. Make the project approachable for volunteer contributors with different technical backgrounds.



\---



\## 6. Non-Goals



To keep the initial project manageable, the first phase should not attempt to:



\* Replace NGP, VAN, VoteBuilder, ActBlue, CallTimeAI, L2, or any other source platform.

\* Build a full CRM.

\* Build a full data warehouse platform.

\* Build a full Zapier competitor in Phase 1.

\* Support every political data platform immediately.

\* Automate writes to production systems before read-only validation is proven.

\* Solve all entity resolution problems automatically.

\* Build a fully self-service product before Bluebonnet-assisted workflows are proven.

\* Commit to a specific hosting model before requirements and risk constraints are better understood.



\---



\## 7. Target Users



\### Bluebonnet Volunteers



Volunteers who support campaigns with data, analytics, reporting, engineering, and operations needs. In the first phase, the tool may require technical volunteers to configure and run workflows.



\### Campaign Liaisons



Bluebonnet volunteers or project leads who work directly with campaigns and need to understand data movement, sync status, and risks.



\### Campaign Staff or Data Volunteers



Longer term, campaign-side staff or volunteers may be able to use the tool directly, especially if the project evolves toward a more self-service interface.



\---



\## 8. Candidate Campaign Use Cases



The project appears to have at least two initial campaign-driven use cases.



\### Use Case A: MN-01 Data Sync / Reconciliation



MN-01 appears to be a strong candidate for an initial pilot, pending confirmation of the exact need, systems involved, data access, and campaign readiness.



Possible needs:



\* Compare records across two political tools.

\* Identify matched and unmatched records.

\* Produce a discrepancy or reconciliation report.

\* Eventually sync selected records from one system to another.



\### Use Case B: TX Campaign Data Sync and Automation



The TX campaign appears to have a related need, potentially including both data sync and workflow automation.



Possible needs:



\* Move records between political tools.

\* Trigger actions based on changes in a source system.

\* Explore Zapier-like automations in a later phase.



\### Future Use Cases



Future campaigns may need similar workflows involving:



\* NGP / VAN / VoteBuilder

\* CallTimeAI

\* L2

\* ActBlue

\* Additional campaign-specific tools

\* Data warehouses or reporting destinations



\---



\## 9. Recommended MVP Direction



The MVP should be deliberately small, safe, and useful.



\### Recommended Starting Point



A strong candidate MVP is:



> A read-only comparison and reconciliation workflow between two political data platforms for one pilot campaign.



The MVP should answer a question like:



> Given data from Platform A and Platform B, how many records exist in each system, how many likely match, and which records appear unmatched or inconsistent?



This approach would provide value while avoiding the highest-risk behavior: writing changes back into campaign systems.



\### MVP Capabilities



The MVP could include:



1\. Connect to or ingest data from one or two defined sources.

2\. Extract a limited set of records.

3\. Normalize records into a shared structure.

4\. Perform basic matching or entity resolution.

5\. Produce a read-only comparison report.

6\. Log what was extracted, compared, and matched.

7\. Avoid writing changes back to source systems.



\### MVP Outputs



The first useful output could be a report showing:



\* Total records in Platform A

\* Total records in Platform B

\* Number of likely matches

\* Number of records only in Platform A

\* Number of records only in Platform B

\* Records requiring manual review

\* Matching criteria used

\* Timestamp of run

\* Data source metadata

\* Warnings or errors



\### Why Start Read-Only?



A read-only MVP reduces risk while still proving core value. It allows the team to test connectors, schemas, matching logic, and reporting without risking accidental data modification in campaign systems.



The team should confirm whether read-only reconciliation is sufficient for the first MVP or whether the first pilot requires a limited one-way sync.



\---



\## 10. Future Phases



\### Phase 1: Discovery and Read-Only MVP



\* Confirm campaign use case.

\* Confirm source systems.

\* Evaluate Parsons and other tools.

\* Build a basic read-only comparison workflow.

\* Generate a reconciliation report.

\* Document implementation decisions.



\### Phase 2: One-Way Sync



\* Add carefully controlled write capability.

\* Support one-directional sync from a source system to a target system.

\* Require dry-run mode before execution.

\* Maintain audit logs of proposed and completed changes.

\* Include rollback or remediation guidance where possible.



\### Phase 3: Scheduled Syncs



\* Add scheduling or orchestration.

\* Support recurring jobs.

\* Add monitoring and alerting.

\* Improve logging and error handling.



\### Phase 4: Workflow Automation



\* Explore Zapier-like triggered actions.

\* Evaluate whether tools like Automatisch, Activepieces, n8n, or custom orchestration make sense.

\* Support event-based workflows only after core data sync patterns are reliable.



\### Phase 5: Broader Reusability / Self-Service



\* Improve documentation and onboarding.

\* Support more connectors.

\* Add configuration-driven workflows.

\* Consider a UI or lightweight admin interface.

\* Enable trained campaign staff or data volunteers to run approved workflows.



\---



\## 11. Candidate Technical Building Blocks



This section is exploratory. No final technical decisions have been made.



\### Parsons



Parsons is a Python package built for the progressive ecosystem. It includes connectors and shared patterns for some political data platforms.



Potential role:



\* Source and destination connectors

\* Shared political data models

\* Existing community knowledge

\* Foundation for sync workflows



\### dlt



dlt may be useful as a lightweight Python-native data loading tool.



Potential role:



\* Extract/load pipeline framework

\* Local development friendliness

\* Lower infrastructure burden than heavier tools

\* Python-first volunteer workflows



\### Dagster



Dagster may be useful for orchestration if the project needs more structured pipelines.



Potential role:



\* Job orchestration

\* Asset-based data workflows

\* Scheduling

\* Observability

\* Local and deployed execution options



\### dbt-cta / Community Tech Alliance



Community Tech Alliance’s public dbt work may provide useful reference patterns for progressive data models, transformations, and warehouse design.



Potential role:



\* Data modeling references

\* Transformation logic

\* Shared conventions



\### Automatisch / Activepieces / n8n



These tools may be relevant for later workflow automation phases.



Potential role:



\* Self-hosted workflow automation

\* Trigger/action workflows

\* Possible foundation for future automation

\* Useful comparison points even if not adopted



\---



\## 12. Key Design Questions



The project needs to answer several design questions before implementation can be scoped confidently.



\### Product Shape



Should this become:



\* A Python library?

\* A command-line tool?

\* A lightweight web app?

\* A set of reusable connectors and scripts?

\* A playbook plus implementation templates?

\* A full self-service product eventually?



Initial recommendation: start as a small, volunteer-operated framework or CLI workflow before committing to a UI or full platform.



\### Hosting and Deployment



Options to evaluate:



\* Local machine

\* Volunteer-managed cloud deployment

\* Campaign-managed deployment

\* Bluebonnet-managed deployment

\* Hybrid model



Important considerations:



\* Who runs the tool?

\* Who owns credentials?

\* Where is data stored?

\* Who can access logs?

\* How are multiple users supported?



\### Data Storage



The project should minimize stored data wherever possible.



Possible storage needs:



\* External ID mappings

\* Sync run metadata

\* Match decisions

\* Audit logs

\* Error logs

\* Configuration metadata



The team should avoid storing unnecessary sensitive data.



\### Credentials and Secrets



The project needs a clear approach for:



\* API keys

\* OAuth tokens

\* Credential rotation

\* Local secrets

\* Cloud secrets

\* Access control

\* Avoiding secrets in logs or GitHub



\### Entity Resolution



The project needs to define matching rules for person, donor, or contact records.



Possible matching approaches:



\* Exact match on platform IDs

\* External ID mapping table

\* Email matching

\* Phone matching

\* Name + address matching

\* Fuzzy matching

\* Manual review queue



Entity resolution should begin conservatively.



\### Auditability



Every workflow should produce enough metadata to answer:



\* What data was accessed?

\* When did the workflow run?

\* What records were matched?

\* What records were changed, if any?

\* Who ran the workflow?

\* What configuration was used?

\* What errors occurred?



Auditability is especially important before any write operations are allowed.



\---



\## 13. Risks and Mitigations



\### Risk: Sensitive Data Exposure



Campaign, voter, donor, and volunteer data may be highly sensitive.



Mitigation:



\* Minimize stored data.

\* Avoid committing sample production data.

\* Use mock data for development.

\* Define credential handling early.

\* Avoid logging secrets or unnecessary PII.



\### Risk: Accidental Data Modification



A sync tool could accidentally overwrite, duplicate, or delete important records.



Mitigation:



\* Start with read-only workflows.

\* Require dry-run mode before writes.

\* Add explicit confirmation for write operations.

\* Maintain audit logs.

\* Limit MVP to reporting and reconciliation unless a write use case is explicitly approved.



\### Risk: Entity Resolution Errors



Incorrect matching can cause bad merges, duplicate records, or incorrect updates.



Mitigation:



\* Begin with conservative matching.

\* Separate exact matches, likely matches, and needs-review records.

\* Avoid automated merges in early phases.

\* Preserve matching logic in logs and reports.



\### Risk: Scope Creep



The project could expand into a full ETL platform, CRM, Zapier replacement, or data warehouse before proving a basic use case.



Mitigation:



\* Define MVP narrowly.

\* Separate future phases from current scope.

\* Use GitHub Issues to track ideas without making them Phase 1 commitments.

\* Require concrete campaign use cases before building features.



\### Risk: Tooling Complexity



The team could spend too much time evaluating tools without delivering anything useful.



Mitigation:



\* Time-box research.

\* Compare tools against MVP needs.

\* Prefer simple Python-first workflows unless complexity is justified.

\* Build a small proof of concept quickly.



\### Risk: Volunteer Coordination



Volunteer projects can lose momentum if work is unclear or too broad.



Mitigation:



\* Create GitHub Issues for specific research and implementation tasks.

\* Assign issue owners where possible.

\* Keep tasks small.

\* Document decisions.

\* Hold a kickoff or scoping call after initial comments.



\---



\## 14. Proposed Workstreams



\### Workstream 1: Requirements and Campaign Use Cases



Goal: Confirm the first real campaign problem to solve.



Tasks:



\* Clarify MN-01 needs.

\* Clarify TX campaign needs.

\* Identify source and target systems.

\* Identify records/data objects involved.

\* Define what success means for the pilot.



Potential outputs:



\* Use case document

\* User stories

\* MVP acceptance criteria



\### Workstream 2: Tool Evaluation



Goal: Evaluate existing tools before building from scratch.



Tasks:



\* Evaluate Parsons for required connectors.

\* Evaluate dlt for MVP pipeline needs.

\* Evaluate Dagster for orchestration needs.

\* Review dbt-cta for relevant data modeling patterns.

\* Evaluate automation tools for future phases.



Potential outputs:



\* Tool comparison matrix

\* Recommendation for MVP stack

\* Known limitations



\### Workstream 3: Data Model and Entity Resolution



Goal: Define the minimum shared data model and matching logic.



Tasks:



\* Identify fields needed for MVP comparison.

\* Define normalized person/contact/donor schema.

\* Propose match tiers.

\* Identify manual review requirements.

\* Define external ID mapping approach.



Potential outputs:



\* MVP data model

\* Entity resolution notes

\* Matching logic proposal



\### Workstream 4: Security, Privacy, and Auditability



Goal: Define minimum safety requirements before implementation.



Tasks:



\* Define credential handling requirements.

\* Define data storage limits.

\* Define logging and audit requirements.

\* Determine whether mock data is needed.

\* Identify risks around local vs remote execution.



Potential outputs:



\* Security requirements document

\* Audit log requirements

\* Development data policy



\### Workstream 5: MVP Implementation



Goal: Build the first narrow, useful workflow.



Tasks:



\* Set up project structure.

\* Create configuration approach.

\* Implement connector proof of concept.

\* Implement read-only extraction.

\* Implement basic comparison logic.

\* Generate report output.

\* Add logging.



Potential outputs:



\* Working MVP script or CLI workflow

\* Sample mock output

\* Basic documentation



\### Workstream 6: Documentation and Project Coordination



Goal: Keep work organized and accessible.



Tasks:



\* Maintain scoping document.

\* Create and triage GitHub Issues.

\* Document decisions.

\* Track open questions.

\* Prepare kickoff agenda.

\* Keep Slack and GitHub aligned.



Potential outputs:



\* GitHub Issues

\* Project board

\* Meeting notes

\* Contributor guide



\---



\## 15. Recommended Initial GitHub Issues



The following issues could help organize work immediately:



1\. Define MVP scope

2\. Document MN-01 campaign use case

3\. Document TX campaign use case

4\. Evaluate Parsons for MVP connectors

5\. Evaluate dlt for MVP pipeline needs

6\. Evaluate Dagster for orchestration needs

7\. Define MVP data model

8\. Define entity resolution approach

9\. Define security and credential handling requirements

10\. Define audit log requirements

11\. Decide local vs remote deployment assumptions

12\. Create sample/mock data for development

13\. Create MVP architecture proposal

14\. Create contributor setup instructions

15\. Create kickoff discussion agenda



\---



\## 16. Proposed MVP Acceptance Criteria



The MVP may be considered successful if it can:



\* Connect to or ingest data from two defined sources.

\* Normalize a limited set of records into a shared schema.

\* Compare records across sources.

\* Identify exact matches, likely matches, and unmatched records.

\* Produce a readable reconciliation report.

\* Run without writing changes back to production systems.

\* Avoid storing unnecessary sensitive data.

\* Produce basic logs showing when the job ran and what it did.

\* Be documented well enough for another Bluebonnet volunteer to run or review.



\---



\## 17. Open Questions



The following questions need input from the team:



1\. Which campaign should be the initial pilot?

2\. Is MN-01 the best first pilot, or should the team evaluate TX and MN side by side?

3\. Which two systems should the MVP compare first?

4\. What data object should be handled first: donors, contacts, volunteers, voters, call-time records, or something else?

5\. Do we have API access for the relevant systems?

6\. Can we use real campaign data for development, or do we need mock/anonymized data only?

7\. Who will run the MVP initially: Bluebonnet volunteer, campaign liaison, or campaign staff?

8\. Should the first version be a Python script, CLI, notebook, or lightweight app?

9\. Is read-only reconciliation sufficient for the MVP, or does the first pilot require a limited one-way sync?

10\. What level of entity resolution is acceptable for the MVP?

11\. What audit information is required before any sync/write capability is considered?

12\. Should the project prioritize reusable connectors, a specific campaign deliverable, or both equally?

13\. Does Bluebonnet have standards for storing credentials, handling sensitive campaign data, or deploying volunteer-built tools?

14\. What should be explicitly out of scope for the 2026 cycle?



\---



\## 18. Suggested Next Steps



\### Next 1-2 Days



\* Add this scoping document to the GitHub repository.

\* Create initial GitHub Issues based on the recommended list.

\* Ask contributors to comment on issues where they have expertise.

\* Confirm whether MN-01 is the strongest initial pilot candidate.

\* Confirm which platforms/data objects are involved in the MVP.



\### Next 1-2 Weeks



\* Hold a kickoff or scoping call.

\* Assign owners to research issues.

\* Time-box tool evaluation.

\* Finalize MVP definition.

\* Draft initial architecture proposal.

\* Begin proof-of-concept work.



\### Next 30-60 Days



\* Build read-only MVP.

\* Test with mock or approved data.

\* Produce reconciliation report.

\* Review security and auditability.

\* Decide whether to proceed to one-way sync.



\---



\## 19. Working Recommendation



The project should begin with a conservative, read-only MVP focused on comparing and reconciling records between two systems for one pilot campaign. MN-01 appears to be a strong candidate for the first pilot, but this should be confirmed by the team before implementation begins.



This allows the team to prove the core value of the project while reducing risk. It also creates a foundation for later phases involving one-way sync, scheduled syncs, and eventually workflow automation.



The first phase should emphasize:



\* Requirements clarity

\* Reusable connectors

\* Conservative entity resolution

\* Security and privacy

\* Auditability

\* Documentation

\* Small, reviewable contributions



The goal is not to build the final product immediately. The goal is to create enough structure and proof of value that Bluebonnet contributors can begin working in parallel without losing sight of the campaign need.



