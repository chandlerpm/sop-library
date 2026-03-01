# SOP: Employee Offboarding

| Field | Value |
|---|---|
| **SOP ID** | SOP-HR-001 |
| **Version** | 1.2 |
| **Owner** | HR Operations |
| **Last Reviewed** | 2025-01 |
| **Next Review** | 2025-07 |
| **Status** | Active |

---

## Purpose

This SOP ensures that employee departures from Shipyard are handled consistently, securely, and respectfully — protecting company data, maintaining continuity, and treating departing employees with professionalism.

---

## Scope

**Applies to:** HR Operations, IT, Engineering Leads, and direct managers.
**Covers:** Voluntary resignations, involuntary terminations, and end-of-contract departures.
**Does not cover:** Contractor offboarding (see HR-002), temporary leave or sabbaticals.

---

## Prerequisites

- [ ] Departure confirmed and last day established
- [ ] HR has notified IT and the employee's manager
- [ ] Offboarding ticket created in Jira (template: `HR-OFFBOARD`)

---

## Procedure

### Step 1 — Knowledge Transfer (Manager)

**Timeline:** Begin at least 5 business days before last day.

**Action:** Manager works with departing employee to document:
- Current project status and open items
- Key contacts and relationships
- Access credentials or shared accounts (to be transferred, not stored personally)
- Any institutional knowledge not yet documented

**Expected outcome:** Knowledge transfer document completed and stored in the team's Notion workspace.

---

### Step 2 — Access Revocation Planning (IT)

**Timeline:** Prepare 2 business days before last day. Execute on last day.

**Action:** IT prepares a revocation checklist for all systems the employee has access to. Standard systems include:

| System | Action |
|---|---|
| Google Workspace | Disable account, transfer Drive files to manager |
| GitHub | Remove from org, transfer any personal repos if applicable |
| AWS / Cloud | Revoke IAM credentials and access keys |
| Jira / Notion / Confluence | Deactivate account |
| Slack | Deactivate account |
| PagerDuty | Remove from on-call rotations |
| Password manager (1Password) | Remove from vault access |
| VPN | Revoke credentials |

**Expected outcome:** All access revoked within 2 hours of last day end time.

---

### Step 3 — Equipment Return (IT + Manager)

**Timeline:** Last day.

**Action:** Manager confirms return of all company equipment (laptop, monitor, peripherals, access badges). IT wipes and re-images returned devices.
**Expected outcome:** Equipment returned and logged in IT asset tracker.

---

### Step 4 — Final Payroll & Benefits (HR)

**Timeline:** Completed by last day or per local legal requirements.

**Action:** HR confirms:
- Final paycheck processed (including any accrued PTO payout per company policy)
- Benefits termination date communicated to employee
- COBRA/continuation coverage information provided where applicable

**Expected outcome:** Employee has received all required final compensation and benefits information.

---

### Step 5 — Exit Interview (HR)

**Timeline:** Last week of employment (voluntary departures only).

**Action:** HR conducts a 30-minute exit interview. Notes are stored confidentially in the HR system and used only for aggregate trend analysis.
**Expected outcome:** Exit interview completed and documented.

---

### Step 6 — Close Offboarding Ticket (HR)

**Action:** HR verifies all checklist items are complete and closes the Jira offboarding ticket.
**Expected outcome:** Offboarding ticket marked Done. Departure logged in HRIS.

---

## Verification

- All system access confirmed revoked in IT access log
- Knowledge transfer document stored in team Notion workspace
- Final payroll processed
- Offboarding Jira ticket closed

---

## Escalation

| Situation | Contact |
|---|---|
| Employee becomes uncooperative or access needs emergency revocation | HR Director + IT immediately |
| Legal concerns (NDA, IP, data) | Legal counsel |
| Equipment not returned | HR Director + Office Manager |

---

## Related Documents

- SOP: Contractor Offboarding (SOP-HR-002 — internal)
- IT Access Revocation Checklist (Jira template: `HR-OFFBOARD`)
- Employee Handbook — Separation section (internal)

---

## Changelog

| Version | Date | Author | Change |
|---|---|---|---|
| 1.0 | 2023-02-15 | J. Chandler | Initial version |
| 1.1 | 2024-01-10 | J. Chandler | Added cloud access revocation steps, updated benefits section |
| 1.2 | 2025-01-15 | J. Chandler | Updated system list, clarified voluntary vs. involuntary scope |
