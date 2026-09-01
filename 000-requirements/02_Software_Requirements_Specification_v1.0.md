# Software Requirements Specification (SRS)
**Document ID:** SRS-002  
**Version:** 1.0  
**Status:** Draft Baseline

## 1. Purpose
This SRS defines the initial functional and non-functional requirements for the four business modules before database, API and implementation details are finalized.

## 2. Scope
Four domains: Project & Process Orchestration; Administrative Hub; Recognition & Incentives; Holistic Learning Framework.

## 3. Requirement Classification
- **Confirmed direction:** four named modules, AI integration, microservice-oriented architecture, team-independent design, zero-budget/free-first constraint.
- **Proposed requirement:** feature suggested during detailed design but not yet confirmed.
- **Assumption:** temporary interpretation where a business rule is missing.
- **Open question:** decision required before final implementation.

## 4. Actors
- System Administrator
- Project Manager / Process Owner
- Employee / Participant
- Manager / Approver
- Executive / Stakeholder
- AI Component (recommendations/analysis only; no independent sensitive business actions)

## 5. Project & Process Orchestration
**Objective:** Organize projects and manage work through defined processes.

Proposed capabilities:
- Project CRUD/archive
- Task/work-item management
- Assignment
- Status/progress tracking
- Task dependencies
- Configurable workflow states where justified
- Traceable state changes
- Integration with downstream capabilities

Requirements:
- FR-PROJ-001: Authorized users can create/manage projects.
- FR-PROJ-002: Authorized users can create/assign/manage tasks.
- FR-PROJ-003: Track task/project status.
- FR-PROJ-004: Support task dependencies where applicable.
- FR-PROJ-005: Important state changes are traceable.
- FR-PROJ-006: Project activity has an integration mechanism.

## 6. Administrative Hub
**Objective:** Provide centralized administration and identity-related capabilities.

Capabilities:
- User profiles
- Roles/permissions
- Authentication/authorization integration
- Organizational information where required
- Administrative audit information
- Controlled identity/context for other services

Requirements:
- FR-ADMIN-001: Manage user accounts.
- FR-ADMIN-002: Support RBAC.
- FR-ADMIN-003: Support appropriate permission management.
- FR-ADMIN-004: Audit security-sensitive/administrative actions.
- FR-ADMIN-005: Other services obtain identity through defined interfaces.

## 7. Recognition & Incentives
**Objective:** Provide recognition and incentive capabilities connected to organizational activity.

Capabilities:
- Recognition/achievement records
- Points/achievement ledger if confirmed
- Rewards if required
- Redemption/approval workflows if required
- Duplicate-processing protection

Requirements:
- FR-RECO-001: Authorized recognition creation.
- FR-RECO-002: Auditable recognition/point history.
- FR-RECO-003: Configurable point rules if enabled.
- FR-RECO-004: Prevent duplicate point-changing operations.
- FR-RECO-005: Reward redemption if enabled.

## 8. Holistic Learning Framework
**Objective:** Manage professional development across Physical, Social, Mental and Spiritual dimensions.

Professional boundary: these are configurable development categories; the system does not provide medical, psychological or religious advice.

Requirements:
- FR-LEARN-001: Categorize approved activities using configured dimensions.
- FR-LEARN-002: Manage learning activities/content.
- FR-LEARN-003: Track user progress.
- FR-LEARN-004: Record completion.
- FR-LEARN-005: Support competency/progress assessment where required.
- FR-LEARN-006: Provide a controlled AI recommendation integration point.

## 9. Core Workflows
### Work completion → Recognition
Task completion → project state recorded → event/API → recognition rule → points/recognition → audit/idempotency.

### Learning completion → Recognition
Learning completion → progress recorded → milestone → recognition rule → audit.

### AI learning recommendation
User request → learning data collection → structured AI input → AI output → validation → recommendation.

### Reward redemption
Select reward → eligibility/points check → atomic transaction → approval if required → final history.

## 10. Non-Functional Requirements
- NFR-COST-001: Core development/testing/demo requires no paid subscriptions or paid APIs.
- NFR-COST-002: AI has a free/local path.
- NFR-MAI-001: Maintainable separation of concerns.
- NFR-SEC-001: Protected operations require authentication/authorization.
- NFR-SEC-002: Secrets are never committed.
- NFR-DAT-001: Clear data ownership per service.
- NFR-API-001: Consistent API conventions.
- NFR-TEST-001: Important business logic has automated tests.
- NFR-DOC-001: Services have setup/API/operational documentation.
- NFR-TEAM-001: Maintainable when developers join/leave.
- NFR-SCALE-001: Independent scaling where genuinely needed; avoid premature complexity.

## 11. Initial Security
Authentication, authorization, explicit roles/permissions, input validation, externalized secrets, auditability, and explicit inter-service trust.

## 12. Initial AI Requirements
AI must have a defined purpose, be non-critical to core data integrity, use validated output, minimize shared data, have a free/local path, and isolate provider-specific code.

## 13. Data & Integration
No direct cross-service database modification. Use documented APIs/events. Design retryable operations for idempotency. Handle downstream failures safely. Version/document integration contracts.

## 14. Open Questions
- Exact features/screens per module
- Exact roles
- Exact point/reward rules
- Need for departments/organizations
- First AI use case
- Communication mechanism per workflow
- Frontend requirement/technology
- Advanced infrastructure requirements

## 15. Out of Scope
NFT/blockchain unless required later; mandatory paid services; unnecessary production infrastructure; unnecessary service discovery; medical/psychological/religious advisory functionality.

## 16. Next Document
**Document 03 — Module Specifications**, which will provide detailed use cases, business rules, entities, workflows, permissions and acceptance criteria.
