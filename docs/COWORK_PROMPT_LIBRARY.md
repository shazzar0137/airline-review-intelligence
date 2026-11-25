# COWORK PROMPT LIBRARY
## Airline Review Intelligence (ARI)

A reusable collection of prompts for researching, designing, building, testing and maintaining ARI.

**Important:** Before using any prompt, instruct Cowork to read:

- `PROJECT_BLUEPRINT.md`
- `CLAUDE_COWORK_MASTER_INSTRUCTION.md`
- `COWORK_PROMPT_LIBRARY.md`
- `docs/PROJECT_STATUS.md`, if available.

Do not ask Cowork to repeat work already completed.

---

# PROMPT 1 – Resume ARI Project

```text
Resume the Airline Review Intelligence (ARI) project.

First read:
- PROJECT_BLUEPRINT.md
- CLAUDE_COWORK_MASTER_INSTRUCTION.md
- COWORK_PROMPT_LIBRARY.md
- docs/PROJECT_STATUS.md
- docs/ARCHITECTURE.md
- docs/ARCHITECTURE_DECISIONS.md

Inspect the actual repository and current implementation.

Determine:
1. Current development stage.
2. What has been completed.
3. What has been tested.
4. What remains incomplete.
5. Current blockers.
6. Whether any previous decisions need review.
7. The next highest-priority task.

Do not repeat completed work.
Do not assume that documented work is implemented.
Verify important claims against the actual files and tests.

Present a concise status report and recommend the next action.
Do not begin a major implementation task without explaining its scope.
```

# PROMPT 2 – Stage 0: Full Open-Source and Reuse Audit

```text
Conduct the Stage 0 discovery and reuse audit for Airline Review Intelligence.

Do not start building the application yet.

Your objective is to identify existing solutions that can be reused, configured, extended or integrated before custom development begins.

Research these areas:

1. Airline review collection APIs and permitted data sources.
2. Existing airline review analysis platforms.
3. Review collection and scraping frameworks, subject to legal and source restrictions.
4. Review deduplication and validation libraries.
5. Sentiment analysis and multilingual NLP tools.
6. Topic extraction and classification libraries.
7. Review quality assessment approaches.
8. Reviewer contribution analysis tools.
9. Airline benchmarking and performance analytics.
10. Database and backend solutions.
11. Dashboard and visualisation libraries.
12. n8n templates and integrations.
13. AI agent frameworks and orchestration tools.
14. Reporting and notification solutions.
15. Public business contact research tools.

Search GitHub, official documentation, APIs, open-source repositories and relevant commercial services.

For every candidate, assess:
- What it does.
- Whether it actually solves an ARI requirement.
- Licence.
- Maintenance status.
- Documentation.
- Compatibility.
- Security.
- Dependencies.
- Deployment requirements.
- Costs.
- Limitations.
- Whether it can be integrated into ARI.

Classify each candidate:
REUSE, CONFIGURE, EXTEND, INTEGRATE, BUILD, DEFER or REJECT.

Do not assume that a tool supports airline review collection without verifying it.

Do not assume public web pages can be collected without restrictions.

Deliver:
- docs/REUSE_AUDIT.md
- docs/ARCHITECTURE.md
- docs/ARCHITECTURE_DECISIONS.md
- docs/OPEN_QUESTIONS.md
- Updated docs/PROJECT_STATUS.md

Recommend a minimum viable architecture and explain why it is preferable to alternatives.

Do not start major implementation until the findings are presented for review.
```

# PROMPT 3 – Find Existing GitHub Projects

```text
Research existing GitHub repositories that could contribute to ARI.

Search by capability rather than only by the phrase "airline review intelligence".

Investigate:
- Review collection.
- Review management.
- Web data ingestion.
- Airline data.
- Sentiment analysis.
- Topic modelling.
- Review deduplication.
- Data quality.
- NLP pipelines.
- Dashboard components.
- AI agents.
- Workflow automation.
- Contact management.
- Reporting.

For each repository:
1. Provide the exact GitHub URL.
2. Explain what it does.
3. Identify the relevant ARI module.
4. Check its licence.
5. Check its last meaningful update.
6. Check stars and community activity as secondary indicators.
7. Inspect dependencies and architecture.
8. Identify security concerns.
9. Explain integration effort.
10. Recommend whether to reuse, extend, integrate, defer or reject.

Do not recommend repositories based on their README alone.
Inspect their actual structure and code where possible.

Identify the best candidates and explain the gaps that would still require custom development.
```

# PROMPT 4 – Review Source and API Research

```text
Research permitted sources of airline passenger reviews for ARI.

For each source, investigate:
- Official API availability.
- Authentication.
- Public access options.
- Available review fields.
- Pagination.
- Rate limits.
- Historical review availability.
- Collection frequency.
- Terms of service.
- Commercial-use restrictions.
- Attribution requirements.
- Data retention restrictions.
- Estimated integration complexity.
- Costs, if applicable.

Separate:
A. Official APIs.
B. Licensed third-party providers.
C. Public datasets.
D. Public web pages where collection is permitted.
E. Sources that are unsuitable or restricted.

Do not claim that a source supports automated collection unless verified.

Do not bypass CAPTCHA, authentication, paywalls or technical restrictions.

Recommend the best sources for the first MVP and explain the limitations.

Save findings in docs/REVIEW_SOURCE_RESEARCH.md.
```

# PROMPT 5 – Architecture Review

```text
Review the proposed ARI architecture against the project blueprint and actual repository.

Evaluate:
- Frontend.
- Backend.
- Database.
- Review ingestion.
- Python processing.
- n8n automation.
- AI model integration.
- Agent orchestration.
- Dashboard.
- Reporting.
- Deployment.
- Security.
- Monitoring.

Compare suitable alternatives.

Assess whether the proposed Next.js/React/TypeScript, Supabase/PostgreSQL, Python, n8n and configurable AI architecture is appropriate.

Do not automatically approve the proposed stack.

Identify:
- Unnecessary complexity.
- Duplicate components.
- Missing services.
- Vendor lock-in.
- Cost risks.
- Security risks.
- Scalability concerns.
- Integration problems.

Recommend the simplest architecture that satisfies the requirements.

Update the architecture documentation and record important decisions.
```

# PROMPT 6 – Database Design

```text
Design and review the ARI database.

First inspect the current schema, source files and requirements.

Consider these entities:
- Airlines.
- Airline aliases.
- Review sources.
- Reviews.
- Raw review data.
- Reviewers.
- Review quality assessments.
- Reviewer reliability assessments.
- Sentiment analyses.
- Review topics.
- Service categories.
- Airline performance scores.
- Score methodologies.
- Collection jobs.
- Collection logs.
- Duplicate candidates.
- Contacts.
- Contact sources.
- Research alerts.
- Reports.
- Outreach campaigns.
- Outreach messages.
- Agent runs.
- Agent configurations.
- Audit logs.

Do not create every table automatically.

Determine which entities are necessary for the MVP and which should be deferred.

For the recommended design, provide:
- Entity descriptions.
- Primary keys.
- Foreign keys.
- Relationships.
- Constraints.
- Indexes.
- Data types.
- Nullable fields.
- Audit requirements.
- Security considerations.

Preserve original review text and source metadata.
Store AI-generated analysis separately.
Use NULL for unavailable values.

Produce:
- docs/DATABASE_SCHEMA.md
- docs/DATA_DICTIONARY.md
- Database migrations where approved.

Check the design for duplicate data, unnecessary complexity and future extensibility.
```

# PROMPT 7 – Review Collection Pipeline

```text
Design or implement the ARI review collection pipeline.

Before coding, inspect:
- Approved review sources.
- Existing connectors.
- Existing collection code.
- Database schema.
- Source-specific permissions.

The pipeline should support:
1. Source configuration.
2. Scheduled collection.
3. API pagination.
4. Rate limiting.
5. Retry handling.
6. Error logging.
7. Raw data preservation.
8. Field normalisation.
9. Duplicate candidate detection.
10. Database insertion or update.
11. Collection summaries.

Do not bypass source restrictions.

Do not fabricate missing review fields.

Preserve source review IDs and URLs where available.

Keep raw and normalised records separate where appropriate.

Test with a small sample before enabling larger collection jobs.

Document the workflow and its limitations.
```

# PROMPT 8 – Review Quality Scoring

```text
Design ARI's Review Quality Score.

The score measures the informational quality and analytical usefulness of a review.

It must not measure whether the review is positive or negative.

Evaluate possible dimensions:
- Specificity.
- Detail.
- Relevance.
- Experience context.
- Clarity.
- Internal consistency.
- Supporting evidence.
- Duplicate likelihood.
- Source verification indicators.

Define:
1. Scoring dimensions.
2. Weighting options.
3. Score range.
4. Confidence level.
5. Missing-data treatment.
6. Explanation format.
7. Human review triggers.
8. Test cases.

A short negative review must not automatically be treated as false.
A detailed negative review may be high quality.
A positive review may be low quality.

Keep the original review unchanged.

Store the score, explanation, methodology version and model information separately.

Produce docs/SCORING_METHODOLOGY.md and test examples before implementation.
```

# PROMPT 9 – Reviewer Reliability Indicator

```text
Design the ARI Reviewer Reliability Indicator.

Use only information that is legitimately and publicly observable.

Potential indicators include:
- Public contribution history.
- Review frequency.
- Account age where available.
- Diversity of contributions.
- Repeated content patterns.
- Public verification indicators.
- Consistency of contribution history.

Do not:
- Discover private email addresses or phone numbers.
- Identify anonymous reviewers.
- Infer sensitive personal characteristics.
- Treat a negative opinion as evidence of dishonesty.
- Present a score as proof of identity or truthfulness.

Define:
- Available input fields.
- Scoring dimensions.
- Confidence limitations.
- Missing-data treatment.
- Human review requirements.
- Explainable output.

If the available information is insufficient, return an unavailable or low-confidence result.

Keep this indicator separate from Review Quality Score and Airline Performance Score.
```

# PROMPT 10 – Airline Performance Scoring

```text
Design ARI's Airline Performance Score.

The objective is to compare passenger-reported airline performance using transparent and defensible methods.

Consider:
- Overall ratings.
- Service-specific ratings.
- Review volume.
- Review quality.
- Source coverage.
- Review recency.
- Cabin class.
- Sample size.
- Data completeness.
- Statistical uncertainty.

Define:
1. Performance dimensions.
2. Weighting methodology.
3. Normalisation.
4. Minimum sample thresholds.
5. Confidence indicators.
6. Time-period comparisons.
7. Source-bias limitations.
8. Methodology versioning.

Avoid misleading rankings when the sample size is small.

Do not silently change weights.

Provide an explanation of every score.

Produce sample calculations and test cases before implementation.
```

# PROMPT 11 – Sentiment and Topic Analysis

```text
Design ARI's sentiment and topic analysis pipeline.

It should support:
- Positive sentiment.
- Negative sentiment.
- Neutral sentiment.
- Mixed sentiment.
- Multiple topics in one review.
- Service-category classification.
- Complaint extraction.
- Positive experience extraction.
- Emerging issue detection.
- Multilingual review handling.

Initial service categories should include:
- Booking.
- Check-in.
- Boarding.
- Baggage.
- Delays and cancellations.
- Customer service.
- Cabin crew.
- In-flight comfort.
- Food and beverages.
- Entertainment and connectivity.
- Cleanliness.
- Accessibility.
- Refunds and compensation.
- Loyalty programmes.

Preserve original text and language.
Store translations and AI interpretations separately.
Allow multiple topics per review.
Include confidence values where supported.
Do not force uncertain reviews into a category.

Evaluate existing NLP tools before building custom models.

Provide test cases covering short, long, multilingual, mixed-sentiment and ambiguous reviews.
```

# PROMPT 12 – Dashboard Development

```text
Design and implement the initial ARI dashboard.

The first five charts must be:

1. Review collection trends.
2. Airline rating comparison.
3. Passenger sentiment distribution.
4. Common complaints and positive themes.
5. Service ratings by cabin class.

Include:
- Airline filters.
- Date filters.
- Source filters.
- Cabin-class filters.
- Service-category filters.
- Comparison views.
- Drill-downs.
- Empty states.
- Loading states.
- Error states.
- Export options.

Use actual database data where available.

Do not use fabricated sample figures in production views.
Clearly label demonstration data.

Review responsive behaviour and usability.

Reuse existing dashboard components and libraries where suitable.
```

# PROMPT 13 – n8n Automation Research

```text
Research how n8n can support ARI.

Investigate existing templates and integrations before building workflows.

Potential workflows:
1. Scheduled review collection.
2. API pagination and ingestion.
3. Data validation.
4. Duplicate checks.
5. AI analysis triggers.
6. Research monitoring.
7. Alert generation.
8. Report generation.
9. Error notifications.
10. Agent cost monitoring.

For each workflow, identify:
- Trigger.
- Inputs.
- Processing steps.
- Outputs.
- Credentials required.
- Failure handling.
- Retry strategy.
- Logging.
- Cost implications.
- Human approval requirements.

Separate work that belongs in n8n from work better handled by application code or Python.

Do not use n8n for every operation simply because it is available.

Recommend the minimum useful automation setup.
```

# PROMPT 14 – Contact Intelligence

```text
Design the ARI Contact Intelligence module.

Its purpose is to identify legitimate public business contacts associated with airlines.

Research:
- Official corporate contacts.
- Customer relations departments.
- Media and press contacts.
- Public corporate telephone numbers.
- Public business email addresses.
- Publicly listed professional stakeholders.

For each contact, record:
- Organisation.
- Department.
- Publicly listed name, where available.
- Professional role.
- Public business contact details.
- Source URL.
- Verification date.
- Verification status.

Do not discover private personal contact details.
Do not infer hidden email addresses.
Do not mix passenger reviewer records with airline business contacts.

Evaluate reusable contact-management tools before implementing custom functionality.

Document privacy and data protection considerations.
```

# PROMPT 15 – Right of Reply and Outreach

```text
Evaluate an optional ARI stakeholder communication module.

Potential functions:
- Request an airline's response to a research finding.
- Share a report.
- Request clarification.
- Send research updates.
- Track responses.

Do not activate automated outreach without explicit approval.

Assess:
- Legal and privacy requirements.
- Anti-spam obligations.
- Sender identity.
- Contact-source records.
- Recipient relevance.
- Suppression lists.
- Unsubscribe handling where applicable.
- Message logs.
- Rate limits.
- Human approval.

Evaluate whether existing email services or campaign tools can be integrated.

Assess pre-warmed email infrastructure only if there is a demonstrated need.

Do not make outreach a dependency of the core review intelligence MVP.
```

# PROMPT 16 – Security and Privacy Audit

```text
Conduct a security and privacy audit of ARI.

Inspect:
- Authentication.
- Authorisation.
- Database permissions.
- API security.
- Secret management.
- Environment variables.
- Input validation.
- Logging.
- Data retention.
- Backup procedures.
- External integrations.
- AI data handling.
- Review-source permissions.
- Contact intelligence.
- Outreach controls.

Search the codebase for exposed credentials and unsafe configuration.

Do not print secrets in the report.

Prioritise findings by severity:
- Critical.
- High.
- Medium.
- Low.
- Informational.

For each finding, provide:
- Evidence.
- Affected component.
- Risk.
- Recommended remediation.
- Verification method.

Do not claim the system is secure simply because no obvious issue was found.
```

# PROMPT 17 – Testing and Quality Assurance

```text
Act as ARI's QA and Testing Engineer.

Inspect the implementation and create a test plan.

Test:
- Core functionality.
- Database operations.
- API behaviour.
- Review collection.
- Pagination.
- Duplicate detection.
- Missing values.
- Invalid ratings.
- Date handling.
- Multilingual text.
- Sentiment classification.
- Scoring calculations.
- Dashboard filters.
- Exports.
- Authentication.
- Permissions.
- Error handling.

For every test, record:
- Test ID.
- Expected result.
- Actual result.
- Pass/fail status.
- Evidence.
- Defect or issue.
- Retest status.

Do not mark untested functionality as passed.

Create or update docs/TEST_PLAN.md and report actual results.
```

# PROMPT 18 – Requirements Review and Change Control

```text
Review the proposed new ARI requirements against the current project.

Inspect:
- Existing requirements.
- Project blueprint.
- Current project log.
- Architecture.
- Database schema.
- Implementation status.
- Existing source code.
- Previous decisions.

Group related requirements into broader capability areas.

For every new idea, decide:
- ACCEPT.
- MERGE.
- DEFER.
- REJECT.
- CLARIFY.

Explain:
- Business value.
- Existing functionality overlap.
- Dependencies.
- Cost.
- Complexity.
- Security and privacy implications.
- Impact on the MVP.
- Recommended priority.

Do not automatically implement every new idea.

Update the requirements register and project status where appropriate.
```

# PROMPT 19 – Project Documentation Update

```text
Review the work completed in the current session.

Update relevant documentation, especially:
- docs/PROJECT_STATUS.md
- docs/ARCHITECTURE.md
- docs/ARCHITECTURE_DECISIONS.md
- docs/REUSE_AUDIT.md
- docs/DATABASE_SCHEMA.md
- docs/SCORING_METHODOLOGY.md
- docs/TEST_PLAN.md

Only update documents affected by the work.

Record:
1. What changed.
2. Files created.
3. Files modified.
4. Tests run.
5. Test results.
6. Decisions made.
7. Outstanding issues.
8. Dependencies.
9. Next actions.

Do not claim work was completed unless it exists in the repository or has been verified.
```

# PROMPT 20 – Pre-Release Review

```text
Conduct a pre-release review of ARI.

Verify the actual implementation against the project blueprint.

Review:
- MVP requirements.
- Database integrity.
- Review source permissions.
- Data quality.
- Scoring transparency.
- Dashboard functionality.
- Authentication.
- Security.
- Privacy.
- API reliability.
- Error handling.
- Logging.
- Backup and recovery.
- Documentation.
- Deployment configuration.

Classify each requirement:
- COMPLETE AND VERIFIED.
- IMPLEMENTED BUT NOT FULLY TESTED.
- PARTIALLY COMPLETE.
- NOT STARTED.
- BLOCKED.

Identify release blockers and risks.

Do not recommend public deployment until critical security, privacy and functionality issues are resolved.

Produce a release readiness report and a prioritised remediation plan.
```

---

# How to Use This Library

Use one prompt at a time and ask Cowork to inspect the project before acting.

Recommended initial order:

1. Prompt 1 – Resume ARI Project.
2. Prompt 2 – Stage 0 Reuse Audit.
3. Prompt 3 – GitHub Project Research.
4. Prompt 4 – Review Source and API Research.
5. Prompt 5 – Architecture Review.
6. Prompt 6 – Database Design.
7. Prompts 7–13 – Build the MVP modules.
8. Prompts 14–15 – Advanced contact and communication modules.
9. Prompts 16–20 – Security, QA, documentation and release.

Do not run every prompt simultaneously. Complete the research and decision stages before implementation.

**End of Cowork Prompt Library**
