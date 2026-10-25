# IAM System Deployment — Project Plan

Project plan for deploying an Identity and Access Management (IAM) system at
Corella Health Group (a hypothetical case organisation in regional NSW): single
sign-on, phishing-resistant MFA, HR-driven joiner-mover-leaver provisioning,
role-based access, quarterly access reviews and privileged access management.

**Released version:** `plan/IAM_ProjectPlan_v1.0.docx` (tag `v1.0`, 25 Oct 2026)

## Team

| Member | Project role | Plan sections |
|---|---|---|
| Toufiq Ahmed Joy | Project Manager (team lead) | 1, 3–6, 8 |
| Kritika Bhattarai | Resource and Communications Manager | 7, 9, 12, 14 |
| Fardin Rahman Tanvir | Quality Assurance Lead | 2, 13, References |
| Ahmed Mahir Daiyan | Change and Configuration Manager | 10, 11, Appendices |

## What's where

| Folder | Contents |
|---|---|
| `plan/` | The plan (.docx) and a PDF export |
| `schedule/` | GanttProject source `IAM_Schedule.gan`, `schedule.csv` (tasks, dates, predecessors, float), `gantt.png` |
| `wbs/` | `wbs.csv` outline and `wbs.png` diagram |
| `risk/` | `risk_register.csv` (12 risks with EMV, mitigation, contingency, trigger) |
| `change-management/` | `change_log.csv`, change process flowchart |
| `templates/` | Issue log, change request form, status report |

The CSV files are the working copies; the plan's tables are generated from the same data, so a change to one should be matched in the other.

## Working rules

- **`main` is protected.** Work on your own branch (`charter`, `schedule`, `risk`, `change-management`, `quality`, `communication`) and open a pull request. Another member reviews and approves before merging.
- **Commit messages** say what changed, area first, imperative: `risk: add EMV for high risks`, `schedule: add SS+5d link for 1.4.4`.
- **One commit per meaningful change.** Commit at the end of every work session so the history shows who did what and when.
- **Tags:** drafts are `v0.x`; the delivered plan is Release `v1.0`; approved changes after that are `baseline-1.x`.

## Raising a change

1. Copy `templates/change_request_form.md`, fill it in and send it to the Change and Configuration Manager.
2. It is logged in `change-management/change_log.csv` as `CR-###` and assessed within five working days.
3. If approved, the change is made on a branch named `cr-###`, reviewed through a pull request, merged and tagged as a new baseline.
