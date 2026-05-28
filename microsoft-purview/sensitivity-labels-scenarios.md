# Sensitivity Labels – Practical Scenarios

Hands-on documentation of 4 real-world sensitivity label configurations in Microsoft Purview.

---

## Scenario 1 – Internal Strict Document (HR / Payroll)

**Use case:** A document containing salary data or HR records, accessible only to specific roles within the organization.

### Label configuration

| Setting | Value |
|---|---|
| Label name | `Internal - Highly Confidential` |
| Scope | Files, Emails |
| Encryption | Enabled |
| Assign permissions | Specific users/groups only |
| Allowed roles | HR Department, Finance, C-Level |
| Content expiry | Never |
| Allow offline access | Limited (7 days) |

### Steps

1. Open **Microsoft Purview** → **Information Protection** → **Labels**
2. Create new label → Name: `Internal - Highly Confidential`
3. Under **Encryption** → Enable → Assign permissions now
4. Add groups: `HR-Team@company.com`, `Finance@company.com`
5. Set permissions: **Co-Owner** for HR, **Reviewer** for Finance
6. Publish label via **Label Policies** → assign to HR and Finance users

### Screenshot

<!-- Add screenshot: label encryption settings -->

### Notes

---

## Scenario 2 – External Client Document (View Only, Expiry, No Print)

**Use case:** A document sent to a client. The client can read it, but cannot print, copy, or access it after the expiry date.

### Label configuration

| Setting | Value |
|---|---|
| Label name | `External - Client Confidential` |
| Scope | Files |
| Encryption | Enabled |
| Assign permissions | Authenticated users (external allowed) |
| Allowed roles | Viewer only |
| Content expiry | 30 days from labeling |
| Allow offline access | Never |
| Print | Disabled |
| Copy/paste | Disabled |

### Steps

1. Create label → Name: `External - Client Confidential`
2. Under **Encryption** → Enable → Let users assign permissions: **Do Not Forward**
   - Or: Assign permissions now → Add external domain → `Viewer` only
3. Set **content expiration**: 30 days
4. Disable offline access
5. Under **Content marking** → add footer: `Confidential – External Use Only`
6. Publish to users who send documents to clients

### Screenshot

<!-- Add screenshot: expiry and viewer permissions settings -->

### Notes

---

## Scenario 3 – Collaborative Document with External Partner (Editor with Restrictions)

**Use case:** A shared document with a partner organization. They can edit but cannot share further or remove the label.

### Label configuration

| Setting | Value |
|---|---|
| Label name | `External - Partner Collaboration` |
| Scope | Files |
| Encryption | Enabled |
| Assign permissions | Specific external domain |
| Allowed roles | Co-Author (edit, no re-share) |
| Forward / Share | Disabled |
| Label removal | Requires justification |

### Steps

1. Create label → Name: `External - Partner Collaboration`
2. Under **Encryption** → Assign permissions now
3. Add external domain: `partner-company.com` → Permission level: **Co-Author**
   - Co-Author allows: edit, save — does NOT allow: share, change permissions
4. Under **Label policies** → Enable **Require users to provide justification to remove a label**
5. Optional: add watermark with user's email via **Content marking**
6. Publish to relevant internal teams (e.g. Project Managers, Account Managers)

### Screenshot

<!-- Add screenshot: Co-Author permission level for external domain -->

### Notes

---

## Scenario 4 – Confidential Email (Label Applied to Email, Not Just Files)

**Use case:** An email containing sensitive information (legal, HR, financial). The label prevents forwarding and encrypts the email body and attachments.

### Label configuration

| Setting | Value |
|---|---|
| Label name | `Confidential - Internal Email` |
| Scope | **Emails** (and Files) |
| Encryption | Enabled |
| Do Not Forward | Enabled |
| Encrypt-Only | Optional alternative |
| Auto-labeling | Optional: trigger on keywords (e.g. "salary", "NDA") |

### Steps

1. Create label → Name: `Confidential - Internal Email`
2. Under **Scope** → select **Email** (in addition to Files)
3. Under **Encryption** → Enable → Choose **Do Not Forward**
   - Recipients can read the email but cannot forward, print, or copy content
4. Optional – Auto-labeling:
   - Go to **Auto-labeling policies**
   - Trigger condition: email contains sensitive info types (e.g. `EU Social Security Number`, `Credit Card Number`)
   - Apply label automatically
5. Publish label to all users or specific groups

### Screenshot

<!-- Add screenshot: Do Not Forward setting and email scope selection -->

### Notes

---

## Summary

| Scenario | Label Name | External Access | Expiry | Print | Edit |
|---|---|---|---|---|---|
| HR / Payroll | Internal - Highly Confidential | No | Never | Yes (internal) | Co-Owner / Reviewer |
| Client Document | External - Client Confidential | Yes (view only) | 30 days | No | No |
| Partner Collaboration | External - Partner Collaboration | Yes (edit) | Never | No | Co-Author |
| Confidential Email | Confidential - Internal Email | No forward | Never | No | N/A |
