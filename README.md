Invoice System

Project Description

This project is a simple invoice system that allows creating invoices, paying invoices, and processing overdue invoices. The system provides the following APIs:
- Create a new invoice
- Get a list of invoices
- Pay an invoice
- Process overdue invoices

 Assumptions and Added Functionality

 Assumptions
1. Invoice Status: The status of an invoice can be `pending`, `paid`, or `void`.
2. Payment Handling: Payments are applied to the oldest invoices first.
3. Partial Payments: Partial payments are allowed and correctly adjust the status of the invoice.
4. Overdue Processing: When processing overdue invoices:
   - If an invoice is fully paid, it is marked as paid.
   - If an invoice is partially paid, a new invoice is created for the remaining amount plus the late fee.
   - If an invoice is not paid at all, it is marked as void, and a new invoice is created for the amount plus the late fee.

 Added Functionality
1. Invoice Due Date Validation: Ensures that the due date of an invoice is in the future.
2. Enhanced Error Handling: Improved error handling and validation for API endpoints.

 API Endpoints

 Create a new invoice

POST /invoices

Request:
{
    "amount": 199.99,
    "due_date": "2021-09-11"
}
Response : 
{
    "id": "1234"
}

Get a list of invoices
GET /invoices
Response:
[
    {
        "id": "1234",
        "amount": 199.99,
        "paid_amount": 0,
        "due_date": "2021-09-11",
        "status": "pending"
    }
]

Pay an invoice
POST /invoices/1234/payments
Request:
{
    "amount": 159.99
}
Process overdue invoices
POST /invoices/process-overdue
Request:
{
    "late_fee": 10.5,
    "overdue_days": 10
}

Running the Project
Prerequisites
•	.NET Core 8.0 SDK
•	Docker
Building and Running
