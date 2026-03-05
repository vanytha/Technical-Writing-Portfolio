# How Payment Authorization Works in a SaaS Platform

This document explains the end-to-end flow of a **payment authorization** in a typical SaaS application — from the moment a user submits card details to the point where the system logs the result.

---
<p align="center">
 <img width="983" height="642" alt="payment process" src="https://github.com/user-attachments/assets/365c5d2f-c1ae-4997-a719-35bf0e6e5665" />
</p>

## 1) User Input

The user enters payment details in the SaaS checkout UI (web or mobile).

**Typical inputs:**
- Card number, expiry date, CVV
- Cardholder name
- Billing address (optional, but common for fraud checks)
- Amount and currency
- Email / user ID (for receipts and account mapping)
 ## Example Payment Input

| Field | Example Value |
|------|---------------|
| Card Number | 4242 4242 4242 4242 |
| Expiry Date | 12/27 |
| CVV | 123 |
| Cardholder Name | John Doe |
| Billing Address | 123 Main Street, New York, NY, 10001, US |
| Amount | 499.00 |
| Currency | USD |
| Email / User ID | john.doe@email.com | 

---
## 2) Payment Request to Moneris API

The backend server formats the payment details and sends them to the **Moneris Payments API** for processing.

### Typical inputs:
- Order ID  
- Total amount  
- Currency code  
- Customer ID  
- Payment method  
- Card details (number, expiry date, CVV)  
- Cardholder name  
- Billing address  
- Customer email  
- Transaction type  

---

## Example API Request (Conceptual)

| Field | Value |
|------|------|
| Order ID | ord_1001 |
| Amount | 499.00 |
| Currency | USD |
| Customer ID | cus_12345 |
| Payment Method | card |
| Card Number | 4242424242424242 |
| Expiry Month | 12 |
| Expiry Year | 2027 |
| CVV | 123 |
| Cardholder Name | John Doe |
| Billing Address | 123 Main Street, New York, NY, 10001, US |
| Email | john.doe@email.com |
| Transaction Type | purchase |

---

