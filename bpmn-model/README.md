# BPMN Model

This folder contains the BPMN 2.0 process model files for the Invoice-to-Payment process.
# BPMN Model


## Files Included

| File                              | Purpose                                                                                          |
| --------------------------------- | ------------------------------------------------------------------------------------------------ |
| `invoice-to-payment-process.bpmn` | Editable BPMN 2.0 source file that can be opened in bpmn.io, Camunda Modeler, or Bizagi Modeler. |
| `invoice-to-payment-process.svg`  | High-resolution visual export of the BPMN model for zooming and presentation purposes.           |
| `invoice-to-payment-process.pdf`  | PDF version of the BPMN model for easier sharing and review.                                     |

## Process Overview

The BPMN model represents an end-to-end Invoice-to-Payment process. It shows how a vendor invoice moves from submission to invoice receipt, validation, purchase order matching, exception handling, approval, posting, payment execution, bank confirmation, reconciliation, and final closure.

## BPMN Structure

The model uses multiple pools to separate external and internal participants:

* Vendor
* Procurement Department
* Finance / Accounts Payable
* Bank / Payment Provider

The Finance / Accounts Payable pool is divided into internal lanes:

* Invoice Processing Team
* AP Validation System / SAP
* Finance Approver
* Payment & Reconciliation Team

## BPMN Elements Used

The model includes the following BPMN elements:

* Start events
* End events
* Send tasks
* Receive tasks
* Service tasks
* User tasks
* Business rule tasks
* Manual tasks
* Exclusive gateways
* Sequence flows
* Message flows
* Exception paths

## Main Process Areas

The model covers:

* Vendor invoice submission
* Invoice receipt and data capture
* Vendor master data validation
* Purchase order reference check
* PO / invoice / goods receipt matching
* Exception handling
* Invoice approval or rejection
* Invoice posting
* Payment run preparation
* Bank/payment provider confirmation
* Payment reconciliation
* Invoice closure or reconciliation exception

## How to Open the BPMN File

To view or edit the BPMN model:

1. Download `invoice-to-payment-process.bpmn`.
2. Open [bpmn.io](https://demo.bpmn.io/).
3. Select **Open diagram from local file**.
4. Upload the `.bpmn` file.
5. Review or edit the process model.

## Disclaimer

This is an anonymized portfolio project created for demonstration purposes. It does not include confidential company data or internal documentation from any employer.
