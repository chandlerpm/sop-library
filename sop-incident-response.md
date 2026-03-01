# SOP: P1/P2 Incident Response

| Field | Value |
|---|---|
| **SOP ID** | SOP-OPS-001 |
| **Version** | 2.1 |
| **Owner** | Director of Engineering |
| **Last Reviewed** | 2025-01 |
| **Next Review** | 2025-07 |
| **Status** | Active |

---

## Purpose

This SOP defines the standard response procedure for Priority 1 (P1) and Priority 2 (P2) incidents affecting Shipyard's production environment. It ensures consistent, coordinated, and documented responses that minimize customer impact and support post-incident review.

---

## Scope

**Applies to:** All engineering, DevOps, and on-call personnel.
**Covers:** Production incidents classified as P1 (critical, service down or severely degraded) or P2 (major feature impaired, significant customer impact).
**Does not cover:** P3/P4 incidents, staging environment issues, or scheduled maintenance windows.

---

## Incident Severity Definitions

| Severity | Definition | Response Time |
|---|---|---|
| **P1** | Full outage or data loss affecting all or most customers | 15 minutes |
| **P2** | Major feature unavailable or severely degraded for a significant customer subset | 30 minutes |
| **P3** | Minor feature impaired, workaround available | Next business day |
| **P4** | Cosmetic issue, no functional impact | Scheduled sprint |

---

## Prerequisites

- [ ] Access to the `#incidents` Slack channel
- [ ] Access to the Shipyard on-call rotation schedule (PagerDuty)
- [ ] Access to production monitoring dashboards (Datadog)
- [ ] Incident Commander role assigned (see Step 2)

---

## Procedure

### Step 1 — Detect & Declare

An incident may be detected via automated alert, customer report, or internal discovery.

**Action:** Post in `#incidents` Slack channel: `🚨 INCIDENT DECLARED — [P1/P2] — [brief description] — [time]`
**Expected outcome:** Team is notified. Incident thread begins.

---

### Step 2 — Assign Incident Commander (IC)

The first responder on call assumes the IC role unless they hand off to a more senior engineer.

**Action:** IC posts in the incident thread: `IC: [Name]`
**Expected outcome:** Single point of coordination is established.

---

### Step 3 — Assess & Communicate

**Action:** IC assesses scope, posts an initial customer-facing status update to the Shipyard Status Page within 15 minutes of declaration.
**Expected outcome:** Customers are informed. Internal stakeholders (CTO, Support lead) are notified via direct message.

Status update template:
```
We are aware of an issue affecting [feature/service]. Our team is actively investigating.
We will provide an update by [time]. We apologize for the inconvenience.
```

---

### Step 4 — Investigate & Mitigate

**Action:** Engineering team investigates root cause. IC coordinates parallel workstreams as needed.
**Expected outcome:** A mitigation (not necessarily a full fix) is identified and applied to restore service.

Update the incident thread every 30 minutes with status, even if there is no new information.

---

### Step 5 — Resolve & Communicate

**Action:** Once service is restored, IC posts resolution in `#incidents` and updates the Status Page.
**Expected outcome:** All affected parties are informed. Incident is marked resolved.

Resolution update template:
```
This incident has been resolved as of [time]. [Brief description of fix].
We are conducting a post-incident review and will share findings with affected customers.
```

---

### Step 6 — Post-Incident Review (PIR)

**Action:** IC schedules a PIR within 48 hours of resolution. PIR document is created in Notion using the PIR template.
**Expected outcome:** Root cause, timeline, and action items are documented. PIR is shared with Engineering and Leadership.

---

## Verification

- Service metrics return to normal thresholds in Datadog
- Status Page shows all systems operational
- PIR document is complete and linked in the incident Slack thread

---

## Escalation

| Situation | Contact |
|---|---|
| IC unavailable | Secondary on-call (PagerDuty rotation) |
| Data loss or breach suspected | CTO + Legal immediately |
| Incident exceeds 2 hours unresolved | VP Engineering |

---

## Related Documents

- [SOP: Release Process](./sop-release-process.md)
- Post-Incident Review Template (Notion — internal link)
- Shipyard Status Page Admin Guide (internal)

---

## Changelog

| Version | Date | Author | Change |
|---|---|---|---|
| 1.0 | 2023-03-10 | J. Chandler | Initial version |
| 2.0 | 2024-06-01 | J. Chandler | Added P2 procedures, updated escalation contacts |
| 2.1 | 2025-01-15 | J. Chandler | Updated status update templates, review cadence |
