# DukaanSaathi AiGen Beta — Phase 4D Recovery, Completion Audit, and Next-Step Prompt

## Project identity
- Application: DukaanSaathi AiGen
- Namespace / applicationId: com.dukaansaathi.aigen
- Developer / Maintainer: Dipak Choudhary
- Brand: GOKUxEDITION
- Powered by: KAIxGenShop™
- Tagline: Har Dukaan Ka Digital Saathi

## Operating constraints
The current budget is ₹0. Do not activate paid services, enable paid billing, purchase resources, or incur API/cloud charges without explicit approval. Prefer existing infrastructure, deterministic logic, open-source dependencies, and verified free-tier quotas. Never assume an AI Studio model/API is free just because it is available.

Do not generate APK/AAB during intermediate development. Do not claim a test passed unless it was actually run and its output inspected. Do not mark a phase complete based only on a generated summary.

## Mandatory first step: inspect the current workspace
1. Inspect the actual current source tree before editing.
2. Read `docs/00_MASTER_INDEX_CHECKLIST.txt`, the authoritative Master Roadmap, all Phase 4D instructions, and relevant ADRs.
3. Review Phase 4A POS, Phase 4B Inventory, Phase 4C Khata, and the partially implemented Phase 4D CRM.
4. Compare the actual files with the prior Phase 4D report. The previous AI run edited 21 files and then reported quota exhaustion; therefore Phase 4D must be treated as PARTIAL and UNVERIFIED until inspected.
5. Check whether the required Phase 4D backend routes, SQL migration, API contract, tests, and test-runner registration exist. Do not assume they exist or recreate them before checking.
6. List missing required roadmap/instruction files by exact filename. If mandatory roadmap material is absent, stop before implementation and report the missing filenames.

## Work order
Follow: KEEP → FIX → UPGRADE → EXTEND → INTEGRATE → TEST → HARDEN.

### Phase 4D requirements
Implement only what the authoritative roadmap requires:
- Customer directory, contact details, and purchase history.
- Supplier directory and supplier purchase tracking.
- Supplier payable/credit ledger.
- Correct integration with existing inventory, POS and Khata where specified.
- Search, filtering, validation, offline-first Room persistence, and strict tenant isolation.
- Safe Room migration(s) and backend SQL migration(s).
- Integer-Paisa financial arithmetic. Do not use floating point for money.
- Idempotent purchase posting and ledger operations.
- Preserve financial history; use compensating entries for corrections.
- Add meaningful Android and backend tests plus regression coverage for Phases 4A–4C.

### Android and Compose audit
- Inspect MainActivity navigation state and all destinations.
- Ensure navigation state survives recomposition and supported Activity recreation.
- Verify all ViewModel dependencies and back-navigation behavior.
- Ensure database migration paths are complete from every supported previous version.
- Avoid duplicate ViewModel creation and duplicate repository/DAO wiring.
- Do not claim Android verification if JDK/Android SDK/test runner are unavailable.

### Backend and security audit
- Verify route mounting, runtime validation, authentication, tenant/shop ownership, transaction boundaries, and idempotency.
- Check that supplier purchase posting and inventory movements cannot be partially applied.
- Ensure customer purchase history is derived from authoritative bill records, not duplicated inconsistent state.
- Verify supplier payable calculations and repayment flows with integer Paisa.
- Ensure database constraints and indexes support tenant-scoped queries.
- Never trust tenantId or ownership supplied by untrusted request bodies.
- Do not log secrets, tokens, customer phone numbers, or unnecessary financial data.

### Testing and verification
Run available checks and report exact commands and real outputs:
- Backend test suite, including the new Phase 4D tests and existing Phase 1–4C regression tests.
- TypeScript type-check/lint and production build.
- Android Gradle configuration checks, compilation, unit tests, and Room migration tests only when the required JDK and Android SDK are available.
- Verify PostgreSQL only when a real DATABASE_URL is configured; do not fabricate connectivity.
- Test duplicate requests, cross-tenant access, invalid amounts, offline retries, process restart recovery, and partial-failure/rollback cases.

If a check cannot run, label it NOT VERIFIED and give the exact blocker. Backend tests do not prove Android compilation.

## Autonomous AI Engine
Do NOT implement the entire Autonomous AI Engine as part of this Phase 4D recovery unless the authoritative roadmap explicitly includes it in the current phase. Record its requirements as a separate future roadmap item. Basic deterministic local alerts must not require LLM calls. Do not expose unrestricted database, shell, arbitrary URL, or arbitrary API tools to an LLM.

## Completion report
Return:
1. Audit findings and exact source/roadmap files inspected.
2. Exact files created, modified, and deleted.
3. Database schema/migration changes and migration paths.
4. Security and tenant-isolation findings.
5. Test commands, actual pass/fail counts, and relevant output.
6. Android verification status and exact blockers.
7. Remaining defects and incomplete integrations.
8. Exact checklist/ADR changes with evidence.
9. Next roadmap phase, only after Phase 4D completion is evidenced.

Do not fabricate implementation, test results, successful integrations, or completion status. Make small, targeted changes directly in the existing workspace.