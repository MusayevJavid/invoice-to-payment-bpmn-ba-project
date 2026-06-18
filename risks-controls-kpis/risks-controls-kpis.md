# Risks, Controls and KPIs

This document defines the key risks, controls, and KPIs for the Invoice-to-Payment process.

The goal is to show how the process can be monitored and controlled to reduce operational errors, payment issues, approval delays, and reconciliation problems.

## Risks and Controls

| Risk ID | Risk                                  | Possible Impact                                                 | Control                                                                         |
| ------- | ------------------------------------- | --------------------------------------------------------------- | ------------------------------------------------------------------------------- |
| R-01    | Missing invoice data                  | Invoice cannot be validated or posted correctly.                | Mandatory field validation before invoice processing.                           |
| R-02    | Invalid or blocked vendor             | Payment may be made to an incorrect or unauthorized vendor.     | Vendor master data validation before posting and payment.                       |
| R-03    | Duplicate invoice                     | Same invoice may be paid more than once.                        | Duplicate invoice check using vendor, invoice number, amount, and invoice date. |
| R-04    | Missing PO reference                  | PO-based invoice cannot be matched with purchasing data.        | PO number validation for PO-based invoices.                                     |
| R-05    | PO / invoice / goods receipt mismatch | Incorrect invoice may be approved or paid.                      | Three-way matching between PO, invoice, and goods receipt/service confirmation. |
| R-06    | Unauthorized invoice approval         | Invoice may be approved by a user without proper authority.     | Role-based approval workflow and approval threshold rules.                      |
| R-07    | Delayed invoice approval              | Payment may be delayed and vendor relationship may be affected. | Approval queue monitoring and escalation rules.                                 |
| R-08    | Payment made before approval          | Financial control failure and potential compliance issue.       | Payment run includes only approved, posted, and due invoices.                   |
| R-09    | Payment failure                       | Vendor may not receive payment on time.                         | Bank confirmation tracking and payment exception handling.                      |
| R-10    | Reconciliation mismatch               | Accounting and bank records may not match.                      | Reconciliation check after bank confirmation.                                   |
| R-11    | Missing rejection reason              | Poor audit trail and unclear exception history.                 | Mandatory rejection reason for rejected invoices.                               |
| R-12    | Missing audit trail                   | Difficult to track decisions, status changes, and user actions. | Audit history for approvals, rejections, exceptions, postings, and payments.    |

## Key Controls

| Control ID | Control                    | Description                                                                                   |
| ---------- | -------------------------- | --------------------------------------------------------------------------------------------- |
| C-01       | Mandatory field validation | Ensures invoice number, vendor ID, amount, currency, invoice date, and due date are captured. |
| C-02       | Vendor master validation   | Confirms that vendor exists and is active before invoice posting or payment.                  |
| C-03       | Duplicate invoice check    | Identifies possible duplicate invoices before posting or payment execution.                   |
| C-04       | PO validation              | Confirms that PO-based invoices include a valid purchase order reference.                     |
| C-05       | Three-way matching         | Compares purchase order, invoice, and goods receipt/service confirmation.                     |
| C-06       | Exception routing          | Sends invalid, incomplete, or mismatched invoices to the correct review queue.                |
| C-07       | Approval workflow          | Ensures invoices requiring approval are reviewed by an authorized finance approver.           |
| C-08       | Payment eligibility check  | Ensures only approved, posted, and due invoices are included in payment runs.                 |
| C-09       | Bank confirmation tracking | Confirms whether payment was successful, failed, or pending.                                  |
| C-10       | Reconciliation control     | Confirms that payment and accounting records match before invoice closure.                    |
| C-11       | Audit trail                | Records user actions, timestamps, decisions, reasons, and status changes.                     |

## KPIs

| KPI ID | KPI                               | Description                                                             | Example Formula                                        |
| ------ | --------------------------------- | ----------------------------------------------------------------------- | ------------------------------------------------------ |
| KPI-01 | Invoice Processing Time           | Measures average time from invoice receipt to invoice posting.          | Posting Date - Received Date                           |
| KPI-02 | First-Time Match Rate             | Measures percentage of invoices matched without exception.              | Matched Invoices / Total Invoices × 100                |
| KPI-03 | Exception Rate                    | Measures percentage of invoices routed to exception handling.           | Exception Invoices / Total Invoices × 100              |
| KPI-04 | Approval Cycle Time               | Measures average time from approval request to approval decision.       | Approval Decision Time - Approval Request Time         |
| KPI-05 | Payment Success Rate              | Measures percentage of payment instructions successfully completed.     | Successful Payments / Total Payment Instructions × 100 |
| KPI-06 | Late Payment Rate                 | Measures percentage of invoices paid after due date.                    | Late Payments / Total Paid Invoices × 100              |
| KPI-07 | Reconciliation Success Rate       | Measures percentage of payments reconciled without exception.           | Matched Reconciliations / Total Reconciliations × 100  |
| KPI-08 | Duplicate Invoice Detection Rate  | Measures how many potential duplicates are detected before payment.     | Detected Duplicate Invoices / Total Invoices × 100     |
| KPI-09 | Invoice Rejection Rate            | Measures percentage of invoices rejected during validation or approval. | Rejected Invoices / Total Invoices × 100               |
| KPI-10 | Average Exception Resolution Time | Measures average time required to resolve invoice exceptions.           | Exception Resolution Date - Exception Creation Date    |

## Process Improvement Opportunities

Based on the risks and KPIs, the process can be improved by:

* Automating invoice data capture
* Strengthening duplicate invoice detection
* Improving vendor master data quality
* Reducing manual exception handling
* Defining clear approval thresholds
* Monitoring overdue approvals
* Tracking payment failures
* Improving reconciliation automation
* Using dashboards for AP process performance

## Summary

The risks, controls, and KPIs in this document help demonstrate how the Invoice-to-Payment process can be managed from both operational and control perspectives.

This section supports the Business Analyst view of process improvement by connecting process risks with measurable controls and performance indicators.
