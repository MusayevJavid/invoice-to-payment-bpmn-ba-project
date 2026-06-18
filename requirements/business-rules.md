# Business Rules

This document defines the business rules for the Invoice-to-Payment process. Business rules describe the conditions, restrictions, and decision logic that control how invoices move through validation, approval, posting, payment, and reconciliation.

| Rule ID | Business Rule                                                                                                           |
| ------- | ----------------------------------------------------------------------------------------------------------------------- |
| BUS-R01 | An invoice cannot be posted if mandatory invoice fields are missing.                                                    |
| BUS-R02 | Vendor master data must be valid and active before invoice posting or payment execution.                                |
| BUS-R03 | A blocked or inactive vendor must trigger an invoice exception.                                                         |
| BUS-R04 | PO-based invoices must include a valid purchase order number.                                                           |
| BUS-R05 | PO-based invoices must be matched against purchase order and goods receipt or service confirmation data before posting. |
| BUS-R06 | If invoice amount, vendor, currency, or PO details do not match, the invoice must be routed to exception handling.      |
| BUS-R07 | Duplicate invoice checks must be performed before invoice posting and payment execution.                                |
| BUS-R08 | Potential duplicate invoices must be blocked or flagged for review.                                                     |
| BUS-R09 | Invoices above the defined approval threshold must be routed to a finance approver.                                     |
| BUS-R10 | A rejected invoice must include a rejection reason.                                                                     |
| BUS-R11 | Only approved invoices can be posted in the finance system.                                                             |
| BUS-R12 | Payment can only be executed for invoices with Approved, Posted, and Due status.                                        |
| BUS-R13 | Invoices with Exception, Rejected, or Pending Approval status cannot be included in a payment run.                      |
| BUS-R14 | Bank or payment provider confirmation must be recorded after payment execution.                                         |
| BUS-R15 | Failed payments must be routed to payment exception handling.                                                           |
| BUS-R16 | Paid invoices must be reconciled against bank and accounting records.                                                   |
| BUS-R17 | Reconciliation mismatches must create a reconciliation exception.                                                       |
| BUS-R18 | An invoice can be closed only after successful payment and successful reconciliation.                                   |
| BUS-R19 | All approval, rejection, exception, payment, and reconciliation actions must be recorded in the audit trail.            |
| BUS-R20 | Exception invoices must remain open until the assigned team resolves or rejects them.                                   |

## Rule Categories

| Category                    | Related Rules                      |
| --------------------------- | ---------------------------------- |
| Invoice completeness        | BUS-R01                            |
| Vendor validation           | BUS-R02, BUS-R03                   |
| PO and matching validation  | BUS-R04, BUS-R05, BUS-R06          |
| Duplicate control           | BUS-R07, BUS-R08                   |
| Approval control            | BUS-R09, BUS-R10, BUS-R11          |
| Payment control             | BUS-R12, BUS-R13, BUS-R14, BUS-R15 |
| Reconciliation control      | BUS-R16, BUS-R17, BUS-R18          |
| Audit and exception control | BUS-R19, BUS-R20                   |

## Example Decision Logic

| Condition                                 | System / Process Action              |
| ----------------------------------------- | ------------------------------------ |
| Vendor is inactive or blocked             | Route invoice to exception handling. |
| PO number is missing for PO-based invoice | Create invoice exception.            |
| Invoice amount does not match PO amount   | Send invoice to exception review.    |
| Invoice is approved and due               | Include invoice in payment run.      |
| Bank confirms successful payment          | Update payment status to Paid.       |
| Payment and accounting records match      | Close invoice.                       |
| Reconciliation does not match             | Create reconciliation exception.     |

## Purpose

These business rules help ensure that the Invoice-to-Payment process is controlled, consistent, auditable, and aligned with finance operation requirements.
