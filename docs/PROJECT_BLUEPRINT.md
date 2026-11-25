# Airline Review Intelligence (ARI)
## Project Blueprint: Requirements, Architecture and Development Plan

**Project:** Airline Review Intelligence (ARI)  
**Document:** Project Blueprint  
**Status:** Foundational project specification  
**Version:** 1.0

---

# 1. Project Overview

Airline Review Intelligence (ARI) is a cloud-connected platform designed to collect, consolidate, analyse and monitor publicly available airline passenger reviews.

The platform will transform unstructured passenger feedback into structured intelligence that helps users understand airline performance, identify recurring service issues, compare airlines and monitor changes in passenger experience over time.

ARI will combine:

- Review collection from permitted public sources and official APIs.
- Data cleaning, validation and duplicate detection.
- Reviewer contribution analysis using observable public information.
- AI-assisted sentiment, topic and service-quality analysis.
- Airline performance measurement and comparison.
- Interactive dashboards and downloadable reports.
- Research monitoring, alerts and optional stakeholder communication.
- A modular multi-agent architecture.

The platform should be designed for expansion. New airlines, review sources, analytical methods, integrations and agents should be added without requiring a complete redesign.

# 2. Vision and Objectives

## 2.1 Vision

To create a reliable airline passenger-review intelligence platform that converts public passenger feedback into actionable, evidence-based airline performance insights.

## 2.2 Primary objectives

1. Collect publicly accessible airline reviews from approved sources.
2. Build a centralised and structured review database.
3. Preserve original review text and source information.
4. Identify duplicate, incomplete, suspicious and low-information reviews without automatically treating negative reviews as unreliable.
5. Analyse passenger sentiment, complaints, positive experiences and service categories.
6. Compare airlines using consistent and transparent indicators.
7. Track airline performance over time.
8. Generate dashboards, reports, research alerts and analytical summaries.
9. Maintain an auditable record of data collection and AI-generated assessments.
10. Provide optional intelligence about relevant airline business stakeholders using legitimate public business information.

# 3. Scope

## 3.1 Core platform modules

### A. Airline Management

Maintain a central register of airlines.

Potential fields:

- Airline ID
- Airline name
- IATA code
- ICAO code
- Country
- Region
- Website
- Airline type
- Operational status
- Date added
- Notes

Support airline aliases and historical names where necessary.

### B. Review Source Management

Maintain a register of review sources.

For each source, record:

- Source ID
- Source name
- Source website
- Source type
- API availability
- Access method
- Collection permissions and restrictions
- Terms-of-service reference
- Collection frequency
- Last successful collection
- Source reliability notes
- Active/inactive status

Possible source categories include:

- Official review APIs.
- Public review platforms.
- Publicly accessible airline feedback pages.
- Other permitted public datasets.
- Approved third-party data providers.

Do not assume that a website can be collected from merely because its pages are publicly visible. Check its terms, access restrictions and applicable law.

### C. Review Collection

Collect reviews and associated metadata from approved sources.

Potential fields:

- Review ID
- Source review ID
- Airline ID
- Source ID
- Reviewer public identifier, where available
- Review title
- Original review text
- Rating
- Review date
- Collection date
- Travel date, where publicly available
- Route, where publicly available
- Cabin class
- Aircraft type
- Trip purpose
- Verified-travel indicator, where supplied by the source
- Source URL
- Language
- Raw metadata
- Collection method
- Collection status

Preserve the original source text. Do not overwrite it with AI summaries or corrected text.

Store missing information as NULL rather than inventing values.

### D. Review Validation and Deduplication

The validation engine should:

- Detect exact duplicates.
- Identify likely near-duplicates.
- Compare source identifiers.
- Identify incomplete records.
- Validate rating ranges and dates.
- Identify inconsistent metadata.
- Flag suspicious patterns for human review.
- Maintain links between original and duplicate records.

A suspected duplicate or suspicious review should be flagged, not automatically deleted.

### E. Reviewer Intelligence

Analyse publicly observable reviewer contribution patterns.

Possible indicators:

- Number of public contributions, where accessible.
- Account age, where accessible.
- Review frequency.
- Review history consistency.
- Diversity of reviewed businesses or airlines.
- Public verification indicators supplied by the source.
- Repeated text patterns.
- Unusual review timing patterns.

Do not attempt to discover private email addresses, phone numbers, home addresses or hidden personal information.

Do not infer sensitive personal characteristics or attempt to identify anonymous reviewers.

Keep reviewer analysis separate from airline business-contact intelligence.

### F. Review Quality Assessment

Assess the usefulness and evidential quality of an individual review.

Possible dimensions:

- Specificity and detail.
- Relevance to airline services.
- Description of an actual experience.
- Clarity.
- Presence of supporting context.
- Internal consistency.
- Potential duplication.
- Source verification indicators.

A negative review can be high quality. A positive review can be low quality.

Sentiment must not determine review quality.

The score should be explainable, configurable and supported by recorded evidence.

### G. Sentiment and Topic Analysis

Use AI and rule-based analysis to identify:

- Positive sentiment.
- Negative sentiment.
- Neutral or mixed sentiment.
- Main complaints.
- Positive service experiences.
- Emerging issues.
- Recurring themes.
- Service-specific topics.

Potential service categories:

- Booking and reservations.
- Ticketing and payment.
- Check-in.
- Boarding.
- Baggage handling.
- Flight delays and cancellations.
- Customer service.
- Cabin crew.
- In-flight comfort.
- Food and beverages.
- Seat quality.
- Entertainment and connectivity.
- Cleanliness.
- Accessibility.
- Refunds and compensation.
- Loyalty programmes.
- Safety-related feedback.

The system should support multilingual reviews and retain the original language.

AI-generated translations and interpretations must be stored separately from the original text.

### H. Airline Performance Engine

Calculate comparable airline performance indicators using transparent and configurable methodologies.

Potential dimensions:

- Overall passenger rating.
- Service quality.
- Customer support.
- Punctuality-related experience.
- Baggage experience.
- Cabin experience.
- Booking experience.
- Value perception.
- Complaint frequency.
- Positive experience frequency.
- Review quality-adjusted indicators.
- Changes over time.

The scoring methodology must account for sample size, review quality, source differences and data coverage.

Do not present an airline ranking as statistically reliable when the underlying sample is insufficient.

### I. Contact Intelligence

Research publicly available airline business contacts for legitimate professional communication.

Potential information:

- Airline corporate website.
- Official customer relations contact.
- Media or press contact.
- Public corporate telephone number.
- Public business email address.
- Relevant department.
- Publicly listed stakeholder name and professional role.
- Source URL.
- Date verified.
- Verification status.

Keep these records separate from passenger reviewer records.

Do not discover or infer private contact details.

### J. Outreach and Right of Reply

The platform may support optional professional communication with airline stakeholders.

Potential uses:

- Requesting an airline's response to a research finding.
- Sharing an analytical report.
- Requesting clarification of a publicly reported issue.
- Sending research updates.
- Managing stakeholder responses.

Outreach must be optional and approval-controlled.

Before enabling campaigns, assess applicable privacy, data protection, electronic communications and anti-spam requirements.

Include:

- Human approval before sending.
- Approved sender identities.
- Suppression and unsubscribe handling where applicable.
- Contact-source records.
- Message logs.
- Rate limits.
- Clear purpose and recipient relevance.
- No automated mass outreach without approval.

Pre-warmed email infrastructure should be evaluated only if a justified communication requirement emerges. It is not a core prerequisite for ARI.

### K. Dashboards and Reporting

The initial dashboard should contain five primary visualisations:

1. Review collection trends.
2. Airline rating comparison.
3. Passenger sentiment distribution.
4. Common complaints and positive themes.
5. Service ratings by cabin class.

Additional dashboard capabilities:

- Filter by airline.
- Filter by date range.
- Filter by country or region.
- Filter by source.
- Filter by cabin class.
- Filter by service category.
- Compare airlines.
- View trends over time.
- Drill down from aggregate results to individual source reviews where permitted.
- Export data and reports.

Initial export formats should include CSV and JSON. PDF and Excel reporting can be added where useful.

# 4. Scoring Framework

ARI must maintain three distinct scoring systems.

## 4.1 Review Quality Score

Measures how useful and informative a review is for analysis.

It should consider detail, relevance, specificity, consistency and available evidence.

It must not reward positive sentiment or penalise negative sentiment.

## 4.2 Reviewer Reliability Indicator

Summarises observable public contribution patterns.

It is an indicator, not proof of a reviewer's identity, honesty or motives.

It must not use private information or sensitive personal inference.

Where there is insufficient public information, return an unavailable or low-confidence result rather than inventing a score.

## 4.3 Airline Performance Score

Measures airline performance using aggregated passenger feedback.

It should account for:

- Review volume.
- Review quality.
- Source coverage.
- Time period.
- Service dimensions.
- Sample size.
- Data completeness.
- Statistical uncertainty.

The methodology, weights and limitations must be documented.

Do not allow an opaque AI model to silently determine the final score.

# 5. Data and Database Architecture

## 5.1 Preferred initial database

Evaluate Supabase with PostgreSQL as the initial managed database option.

The final decision must follow the Stage 0 technology and reuse audit.

## 5.2 Proposed entities

- Airlines
- AirlineAliases
- ReviewSources
- Reviews
- ReviewRawData
- Reviewers
- ReviewQualityAssessments
- ReviewerReliabilityAssessments
- SentimentAnalyses
- ReviewTopics
- ServiceCategories
- AirlinePerformanceScores
- ScoreMethodologies
- CollectionJobs
- CollectionLogs
- DuplicateCandidates
- Contacts
- ContactSources
- ResearchAlerts
- Reports
- OutreachCampaigns
- OutreachMessages
- AgentRuns
- AgentConfigurations
- AuditLogs

The final schema should be developed and documented by the architecture and database specialists.

Avoid creating unnecessary tables before requirements and relationships are understood.

## 5.3 Data principles

- Preserve original source data.
- Store AI analysis separately.
- Maintain source attribution.
- Use stable identifiers.
- Use timestamps consistently.
- Record collection and processing history.
- Use NULL for unavailable values.
- Track changes to scoring methodologies.
- Keep audit logs for important operations.
- Apply appropriate access controls.
- Support backup and recovery.

# 6. Proposed Technical Architecture

The following is a proposed starting point, not a mandatory stack. Cowork must validate it against existing projects, reusable components, cost, maintenance and compatibility before implementation.

| Layer | Initial candidate | Purpose |
|---|---|---|
| Frontend | Next.js, React, TypeScript | User interface and dashboards |
| Backend/API | Existing reusable backend or suitable API layer | Business logic and integrations |
| Database | Supabase / PostgreSQL | Structured storage |
| Automation | n8n | Scheduled workflows and integrations |
| Data processing | Python | Cleaning, validation and analysis |
| Visualisation | Recharts or suitable existing library | Dashboard charts |
| AI | Configurable model provider | Classification, extraction and analysis |
| Version control | GitHub | Source code and documentation |
| Deployment | Vercel or suitable alternative | Cloud application hosting |
| Optional worker | Python local/cloud worker | Controlled data processing |

The architecture should remain modular and avoid unnecessary dependence on one AI provider.

## 6.1 Hybrid deployment

ARI should support:

- A cloud-hosted application.
- A cloud database.
- Cloud automation workflows.
- Optional local processing workers.
- Secure communication between components.

Local processing should be optional, not a requirement for ordinary platform use.

# 7. Data Collection and Compliance

ARI must follow a responsible data collection policy.

Permitted approaches may include:

- Official APIs.
- Licensed data providers.
- Public datasets with suitable usage rights.
- Public pages where collection is permitted.
- Explicitly authorised integrations.

Prohibited approaches include:

- Bypassing CAPTCHA.
- Circumventing authentication.
- Accessing private or restricted content without authorisation.
- Evading paywalls.
- Ignoring applicable platform restrictions.
- Collecting private passenger contact information.
- Misrepresenting the platform or its identity.

Implement source-specific rate limits, retry controls, error handling and collection logs.

# 8. Operational ARI Agent Architecture

ARI is expected to support specialised agents. These are operational agents within the finished platform and are separate from the development specialists used by Claude Cowork.

Initial operational agents:

1. **Source Discovery Agent** – discovers and evaluates potential review sources.
2. **Airline and Source Research Agent** – researches airlines and source metadata.
3. **Review Collection Agent** – retrieves reviews through approved methods.
4. **Reviewer Intelligence Agent** – analyses observable public reviewer contribution patterns.
5. **Review Validation and Deduplication Agent** – validates records and identifies duplicate candidates.
6. **Review Quality Assessment Agent** – evaluates review quality.
7. **Sentiment and Topic Analysis Agent** – classifies sentiment and extracts themes.
8. **Airline Performance Scoring Agent** – calculates airline performance indicators.
9. **Research Monitoring Agent** – monitors changes and emerging issues.
10. **Notification and Reporting Agent** – prepares alerts and reports.
11. **Contact Intelligence Agent** – researches official airline business contacts.
12. **Outreach Campaign Agent** – supports approved professional communication.
13. **Agent Cost and Performance Monitoring Agent** – tracks usage, errors, performance and costs.

Agents should have defined inputs, outputs, permissions and responsibilities.

Do not give every agent unrestricted access to every system.

Human approval is required for sensitive or external actions.

# 9. Security and Privacy

Implement:

- Authentication.
- Role-based access control.
- Least-privilege permissions.
- Secure secret management.
- Database access policies.
- Input validation.
- API security.
- Audit logging.
- Backup and recovery.
- Rate limiting.
- Error monitoring.
- Data retention policies.
- Secure deployment practices.

Never store API keys, passwords or credentials in public repositories.

Use environment variables and appropriate secret-management facilities.

# 10. Development Principles

## 10.1 Reuse before building

Before implementing any major feature, investigate whether an existing solution already provides it.

Search:

- GitHub repositories.
- Open-source libraries.
- Existing APIs.
- n8n templates.
- Claude plugins and skills.
- Existing database schemas.
- Reusable dashboard components.
- Existing review-analysis systems.
- Commercial services where appropriate.

Evaluate:

- Licence.
- Maintenance activity.
- Compatibility.
- Security.
- Documentation.
- Dependencies.
- Cost.
- Extensibility.
- Data ownership.
- API restrictions.

Classify each candidate:

- REUSE
- CONFIGURE
- EXTEND
- INTEGRATE
- BUILD
- DEFER
- REJECT

Do not rebuild a capability simply because custom development is possible.

## 10.2 Evidence-based implementation

Do not invent:

- API capabilities.
- Review-source permissions.
- Data availability.
- Test results.
- Deployment status.
- Completed features.
- Performance figures.

Clearly distinguish verified facts, assumptions, recommendations and unresolved questions.

## 10.3 Modular development

Develop and test modules independently before integrating them.

Maintain clear interfaces between the frontend, backend, database, automation workflows and AI services.

# 11. Development Roadmap

## Stage 0 – Discovery and Reuse Audit

- Inspect the repository and existing project files.
- Identify reusable GitHub projects and libraries.
- Research review-source APIs and permissions.
- Evaluate existing review-analysis solutions.
- Compare technology options.
- Identify costs, limitations and risks.
- Produce the architecture decision record.
- Recommend the minimum viable architecture.

**Gate:** Do not begin major implementation until the reuse audit and architecture proposal are reviewed.

## Stage 1 – Project Foundation

- Set up repository structure.
- Establish development environment.
- Configure project conventions.
- Create environment-variable templates.
- Establish issue tracking and documentation.
- Configure basic CI checks where appropriate.

## Stage 2 – Database and Backend

- Finalise data model.
- Implement database schema.
- Configure authentication and permissions.
- Create APIs and data-access services.
- Implement audit logging.
- Add sample and test data.

## Stage 3 – Frontend and Dashboard

- Create application layout.
- Implement airline management.
- Implement review browsing.
- Build the five initial dashboard charts.
- Add filters and drill-downs.
- Add export functionality.

## Stage 4 – Collection and Automation

- Implement approved source connectors.
- Configure n8n workflows where appropriate.
- Add scheduled collection.
- Implement retries and error handling.
- Add collection monitoring and logs.

## Stage 5 – AI and Scoring

- Implement sentiment analysis.
- Implement topic extraction.
- Implement review quality assessment.
- Implement reviewer reliability indicators.
- Implement airline performance scoring.
- Document methodologies and confidence limitations.

## Stage 6 – Advanced Intelligence and Communication

- Research monitoring.
- Alerts and reports.
- Contact intelligence.
- Optional right-of-reply workflow.
- Approved outreach functionality.
- Agent cost and performance monitoring.

## Stage 7 – Testing, Deployment and Release

- Functional testing.
- Integration testing.
- Security testing.
- Data-quality testing.
- Performance testing.
- User acceptance testing.
- Deployment.
- Documentation.
- Backup and recovery verification.

# 12. Minimum Viable Product

The first release should prioritise:

1. Airline register.
2. Review source register.
3. Approved review collection from at least one suitable source.
4. Central review database.
5. Review validation and duplicate detection.
6. Sentiment and topic analysis.
7. Review quality assessment.
8. Initial airline performance indicators.
9. Five dashboard charts.
10. CSV and JSON export.
11. Basic user authentication.
12. Audit and collection logs.

Advanced outreach and extensive multi-agent automation should not delay the initial working product.

# 13. Required Project Documentation

Maintain:

- PROJECT_BLUEPRINT.md
- CLAUDE_COWORK_MASTER_INSTRUCTION.md
- COWORK_PROMPT_LIBRARY.md
- README.md
- docs/ARCHITECTURE.md
- docs/DATABASE_SCHEMA.md
- docs/API_SPECIFICATION.md
- docs/DATA_DICTIONARY.md
- docs/REUSE_AUDIT.md
- docs/ARCHITECTURE_DECISIONS.md
- docs/SECURITY_AND_PRIVACY.md
- docs/DATA_COLLECTION_POLICY.md
- docs/SCORING_METHODOLOGY.md
- docs/TEST_PLAN.md
- docs/DEPLOYMENT_GUIDE.md
- docs/PROJECT_STATUS.md
- docs/CHANGELOG.md

Update documentation when implementation decisions change.

# 14. Definition of Success

ARI should be considered successful when it can:

- Collect permitted public airline reviews reliably.
- Preserve source attribution and original review content.
- Store and retrieve structured review data.
- Identify duplicate and incomplete records.
- Produce explainable review-quality assessments.
- Analyse sentiment and recurring themes.
- Calculate transparent airline performance indicators.
- Display useful comparisons and trends.
- Export data and reports.
- Monitor collection and processing failures.
- Protect credentials and user data.
- Be extended without redesigning the entire platform.

**End of Project Blueprint**
