# Microsoft Purview — Information Protection

Hands-on documentation of Microsoft Purview Information Protection, focused on Sensitivity Labels and their practical application in real-world business scenarios.

## Contents

| File | Description |
|---|---|
| [`sensitivity-labels-scenarios.md`](./sensitivity-labels-scenarios.md) | Main documentation — 2 scenarios, 5 labels, full design rationale |

## Scenarios

**Scenario 1 — HR / Payroll**
Internal payroll document control with external distribution. Two labels: Payroll Standard (general staff) and Payroll Executive (senior leadership). Covers access control, GDPR considerations, and permission granularity.

**Scenario 2 — External Client Collaboration (Tax Incentive Process)**
Multi-phase consulting engagement with an external client. Three labels: CE-Contract (contract signing), CE-ClientData (confidential data transfer), CE-TaxSubmission (final submission with controlled protection removal). Covers least privilege across departments, RMS compatibility with government systems, and audit trail design.

## Screenshots

Screenshots are organized by scenario under [`screenshots/`](./screenshots/):

- [`scenario-1/`](./screenshots/scenario-1/) — 8 screenshots covering Scenario 1 label configuration
- [`scenario-2/`](./screenshots/scenario-2/) — pending

## Environment

| | |
|---|---|
| Tenant | Microsoft 365 Business Premium — contact@mariusbrinaru.de |
| Portal | Microsoft Purview compliance portal |
