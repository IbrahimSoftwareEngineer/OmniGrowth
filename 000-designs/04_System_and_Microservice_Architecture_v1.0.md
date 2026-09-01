# 04 — System & Microservice Architecture
**Document ID:** ARC-004  
**Version:** 1.0  
**Status:** Baseline Draft

## 1. Architecture Goals
- Independent business capabilities
- Clear data ownership
- Team-size independence
- End-to-end integration
- Controlled AI capability
- Free/local development and demonstration
- Maintainable architecture

## 2. High-Level Architecture
Client → API Gateway (optional/recommended) → Business Services → service-owned databases / AI integration.

Services communicate only through documented APIs/events.

## 3. Initial Service Boundaries
### Admin Service
Owns users, roles, permissions, admin/audit data.

### Project Service
Owns projects, tasks, workflow state, assignments and progress.

### Recognition Service
Owns recognition, achievements, point ledger and optional rewards/redemption.

### Learning Service
Owns learning activities, four dimensions, enrollment, progress and completion.

### AI Integration
Owns no core business state; handles AI requests/recommendations/analysis.

## 4. Ownership Rules
- Each business service owns its domain data.
- No direct cross-service DB reads/writes.
- External references use stable IDs/contracts.
- Business rules remain with the owning service.
- AI is not the source of truth for core business state.

## 5. API Gateway
Recommended as a lightweight single client-facing entry point. No business logic. If initially unnecessary, direct service access may be used temporarily without changing domain contracts.

## 6. Service Communication
- Client → services: REST
- Project → Recognition: API or event
- Learning → Recognition: API or event
- Learning → AI: local/API integration
- Recognition → Admin: identity/context only when required

## 7. Sync vs Async
Use REST for immediate responses. Use events for independent downstream reactions where eventual consistency is acceptable. Do not introduce a broker until justified. Any broker must be free/open-source and locally runnable.

## 8. Key Workflows
### Task → Recognition
Employee → Gateway → Project Service → Project DB → completion milestone → Recognition Service → Recognition DB.

### Learning → AI
Employee → Gateway → Learning Service → structured input → AI Integration → free/local AI → validated output → user.

AI cannot directly update core business state.

## 9. Security
Authentication at the security boundary; authorization based on Admin roles/permissions; business-specific authorization enforced by services; explicit internal trust; secrets externalized and never committed.

## 10. Database Direction
Admin → Admin DB  
Project → Project DB  
Recognition → Recognition DB  
Learning → Learning DB  
AI → no business DB unless later justified.

Exact schemas are Document 05.

## 11. Failure Handling
- Invalid input → validation error.
- Unauthorized → reject.
- Service unavailable → controlled error/retry/fallback.
- Duplicate event → idempotency.
- Downstream recognition unavailable → preserve valid originating task when eventual consistency is acceptable; retry/reconcile.
- AI unavailable → safe fallback; core learning data remains intact.

## 12. Team Independence
Service boundaries depend on business responsibility, not developer count. One developer can work sequentially; multiple developers can work against contracts; joining/leaving developers can use service documentation and ownership boundaries.

## 13. Zero-Cost Constraint
Core architecture must not require paid cloud/API services. Prefer free/open-source and local tooling. AI requires a free/local path. Docker/local execution is the baseline. External integrations must document cost and no-cost fallback.

## 14. Technology Direction
- Java + Spring Boot — confirmed
- Spring Data JPA/Hibernate + MySQL-compatible local DB — confirmed
- REST + OpenAPI — confirmed
- Spring Security — confirmed
- Spring-based gateway — proposed
- Free/open-source messaging only if justified — open
- Free/local AI — confirmed constraint; technology open
- Docker — proposed/strongly recommended
- JUnit/Mockito/Spring test tooling — proposed
- Free Git-based CI — proposed

## 15. Trade-offs
Microservices add operational complexity; create only meaningful boundaries. Database-per-service improves ownership but requires APIs/events. Async messaging improves decoupling but adds infrastructure. Gateway must remain free of business logic. Local AI reduces cost but may have hardware/model limits. Advanced infrastructure is deferred until justified.

## 16. Open Decisions
Gateway timing; REST vs messaging for cross-service workflows; broker choice; authentication/token architecture; AI runtime/model; separate AI service vs adapter; service discovery need.

## 17. Acceptance Criteria
Clear service responsibilities; no cross-service DB access; at least one end-to-end cross-service workflow; enforceable security; replaceable/disableable AI; local zero-cost execution; team changes do not alter business boundaries.

## 18. Next
**05 — Database Design + ERD**, derived from the service ownership and module specifications.
