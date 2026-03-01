# SOP: Software Release Process

| Field | Value |
|---|---|
| **SOP ID** | SOP-ENG-002 |
| **Version** | 1.3 |
| **Owner** | Release Manager |
| **Last Reviewed** | 2025-01 |
| **Next Review** | 2025-07 |
| **Status** | Active |

---

## Purpose

This SOP defines the standard process for releasing new versions of Shipyard to production. It ensures releases are predictable, well-communicated, and reversible in the event of a critical issue.

---

## Scope

**Applies to:** Engineering, QA, and Release Management.
**Covers:** All scheduled production releases (major, minor, and patch).
**Does not cover:** Hotfixes (see SOP-ENG-003), internal tooling releases, or staging deployments.

---

## Release Types

| Type | Version Format | Cadence |
|---|---|---|
| **Major** | X.0.0 | Quarterly |
| **Minor** | X.Y.0 | Bi-weekly |
| **Patch** | X.Y.Z | As needed |

---

## Prerequisites

- [ ] All work for the release is merged to the `release` branch
- [ ] QA sign-off received in the release tracking ticket
- [ ] Release notes drafted and reviewed (see Step 2)
- [ ] Rollback plan documented in the release ticket
- [ ] Release scheduled in the team calendar and communicated to Support

---

## Procedure

### Step 1 — Create Release Branch

**Action:** Create a release branch from `main` using the format `release/vX.Y.Z`.
**Expected outcome:** Release branch exists and is frozen for new feature work. Only bug fixes may be merged at this stage.

---

### Step 2 — Draft Release Notes

**Action:** Release Manager drafts release notes using the standard template (see `docs/release-notes-template.md`). Engineering leads review for accuracy.

Release notes must include:
- New features (with brief user-facing description)
- Bug fixes (with ticket references)
- Deprecations or breaking changes (clearly flagged)
- Known issues

**Expected outcome:** Release notes reviewed and approved by Engineering lead and Product Manager.

---

### Step 3 — QA Sign-Off

**Action:** QA runs the full regression suite against the release branch. All P1/P2 bugs must be resolved before sign-off. P3/P4 bugs may be deferred with documented approval.
**Expected outcome:** QA lead posts sign-off comment in the release tracking ticket.

---

### Step 4 — Deploy to Staging

**Action:** Deploy the release branch to the staging environment. Run smoke tests.
**Expected outcome:** All smoke tests pass. Staging environment reflects the upcoming production state.

---

### Step 5 — Production Deployment

**Action:** Release Manager initiates production deployment via Shipyard's CI/CD pipeline during the approved maintenance window (Tuesdays and Thursdays, 10:00–12:00 PM ET).
**Expected outcome:** Deployment completes without errors. Automated health checks pass.

> **Note:** If deployment fails or health checks do not pass within 15 minutes, initiate rollback immediately (see Rollback Procedure below).

---

### Step 6 — Post-Deployment Verification

**Action:** Engineering on-call monitors error rates, latency, and key metrics in Datadog for 30 minutes post-deployment.
**Expected outcome:** All metrics within normal thresholds. No spike in support tickets.

---

### Step 7 — Communicate & Publish

**Action:** Release Manager publishes release notes to the Shipyard changelog. Support team is notified. Status Page updated if applicable.
**Expected outcome:** Customers and internal stakeholders are informed of the new release.

---

## Rollback Procedure

If a critical issue is identified post-deployment:

1. Release Manager declares a rollback in `#releases` Slack channel
2. Engineering triggers rollback via CI/CD pipeline (previous stable build)
3. Notify Support team immediately
4. Open a P1 incident ticket and follow [SOP-OPS-001: Incident Response](./sop-incident-response.md)

---

## Verification

- Version number in production matches the intended release
- Release notes are published to the changelog
- Datadog metrics stable 30 minutes post-deployment
- No new P1/P2 tickets opened within 1 hour of release

---

## Escalation

| Situation | Contact |
|---|---|
| Deployment pipeline failure | DevOps on-call |
| QA sign-off blocked by unresolved P1 bug | Engineering Director |
| Release needs to be postponed | Release Manager + Product Manager |

---

## Related Documents

- [SOP: Incident Response](./sop-incident-response.md)
- Release Notes Template (`docs/release-notes-template.md` — internal)
- Shipyard CI/CD Pipeline Guide (internal)

---

## Changelog

| Version | Date | Author | Change |
|---|---|---|---|
| 1.0 | 2023-05-01 | J. Chandler | Initial version |
| 1.1 | 2023-11-14 | J. Chandler | Added rollback procedure |
| 1.2 | 2024-04-02 | J. Chandler | Updated deployment window, added staging step |
| 1.3 | 2025-01-15 | J. Chandler | Minor clarifications, updated contacts |
