# Functional Requirements

This document defines the functional requirements for the Invoice-to-Payment process. These requirements describe how the system should behave to support invoice validation, exception handling, approval, posting, payment, bank confirmation, reconciliation, and closure.

| ID    | Functional Requirement                                                                                                             | Acceptance Criteria                                                                                                       |
| ----- | ---------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------- |
| FR-01 | The system shall capture invoice details when an invoice is received.                                                              | Invoice ID, invoice number, vendor ID, PO number, amount, currency, invoice date, received date, and due date are stored. |
| FR-02 | The system shall validate mandatory invoice fields.                                                                                | Missing mandatory fields trigger an exception status and prevent posting.                                                 |
| FR-03 | The system shall validate vendor master data.                                                                                      | Invalid, inactive, or blocked vendors are routed to exception handling.                                                   |
| FR-04 | The system shall identify whether the invoice is PO-based or non-PO-based.                                                         | Invoice type is recorded as PO or Non-PO.                                                                                 |
| FR-05 | The system shall validate the PO reference for PO-based invoices.                                                                  | Invalid or missing PO number creates an exception.                                                                        |
| FR-06 | The system shall match invoice data against purchase order data.                                                                   | Invoice amount, vendor, currency, and PO reference are compared with purchase order data.                                 |
| FR-07 | The system shall match invoice data against goods receipt or service confirmation where applicable.                                | Matching result is stored as Matched, Mismatch, or Pending Review.                                                        |
| FR-08 | The system shall check for potential duplicate invoices.                                                                           | Duplicate invoice number, vendor, amount, and invoice date combination is flagged before posting or payment.              |
| FR-09 | The system shall route invoice exceptions to the responsible review queue.                                                         | Exception reason, assigned team, timestamp, and status are recorded.                                                      |
| FR-10 | The system shall allow authorized users to approve or reject invoices requiring manual approval.                                   | Approver ID, decision, date, and reason are stored.                                                                       |
| FR-11 | The system shall post approved invoices in the finance system.                                                                     | Posting document number is generated after successful posting.                                                            |
| FR-12 | The system shall update invoice status after posting.                                                                              | Invoice status changes to Posted after successful posting.                                                                |
| FR-13 | The system shall include approved and due invoices in a payment run.                                                               | Payment run ID is generated and linked to selected invoices.                                                              |
| FR-14 | The system shall send payment instruction to the bank or payment provider.                                                         | Payment reference is created and stored.                                                                                  |
| FR-15 | The system shall receive payment confirmation or failure response from the bank or payment provider.                               | Payment status is updated as Successful, Failed, or Pending.                                                              |
| FR-16 | The system shall reconcile paid invoices against bank and accounting records.                                                      | Reconciliation status becomes Matched, Pending, or Exception.                                                             |
| FR-17 | The system shall create reconciliation exceptions for unmatched payments.                                                          | Exception record is created with reason, status, and assigned owner.                                                      |
| FR-18 | The system shall close invoices after successful payment and reconciliation.                                                       | Invoice status changes to Closed only after payment and reconciliation are completed.                                     |
| FR-19 | The system shall maintain audit history for invoice status changes and user decisions.                                             | Audit trail includes user, timestamp, action, status change, and reason.                                                  |
| FR-20 | The system shall support notifications for invoice exceptions, approval requests, payment failures, and reconciliation exceptions. | Relevant users receive notification when action is required.                                                              |

## Functional Status Values

| Status                   | Meaning                                           |
| ------------------------ | ------------------------------------------------- |
| Received                 | Invoice has been received.                        |
| Pending Validation       | Invoice is waiting for validation.                |
| Exception                | Invoice has an issue requiring review.            |
| Pending Approval         | Invoice requires manual approval.                 |
| Approved                 | Invoice has been approved.                        |
| Rejected                 | Invoice has been rejected.                        |
| Posted                   | Invoice has been posted in the finance system.    |
| Payment Pending          | Invoice is waiting for payment execution.         |
| Paid                     | Payment has been completed.                       |
| Reconciliation Pending   | Payment is waiting for reconciliation.            |
| Reconciliation Exception | Payment and accounting records do not match.      |
| Closed                   | Invoice is fully processed, paid, and reconciled. |
