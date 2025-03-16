# Budgets and Alerts in Azure

## Overview
This document provides a guide on setting up **Budgets and Alerts** in **Azure Cost Management + Billing**. It includes a budget limit of **$50/month** and alert thresholds at **50% ($25)** and **90% ($45)**.

## Budget Configuration
- **Budget Name:** `cst8913_monthly_budget_jaspreet`
- **Scope:** Billing Account
- **Amount:** `$50.00 USD`
- **Reset Period:** Monthly
- **Creation Date:** `March 1, 2025`
- **Expiration Date:** `February 28, 2027`

## Alert Conditions
| Type  | % of Budget | Amount |
|-------|------------|--------|
| Actual | 50%        | $25    |
| Actual | 90%        | $45    |

### **Alert Recipients**
- **Email:** `chha0038@algonquinlive.com`

## Screenshots
### Budget Alert Settings
![Budget Alert Settings](1_budget.png)

### Budget Summary
![Budget Summary](2_budget.png)

## Instructions
1. Go to **Azure Portal** → **Cost Management + Billing**.
2. Navigate to **Budgets** and click **+ Add**.
3. Enter budget details:
   - Set **Amount** to `$50`.
   - Choose **Reset Period: Monthly**.
4. Set **Alert Conditions** for **50% ($25)** and **90% ($45)**.
5. Add email recipients to receive notifications.
6. Save the budget and validate in the **Budgets** section.

---
### **Notes**
- Ensure that `azure-noreply@microsoft.com` is added to your allow list to avoid missing alerts.
- Modify the expiration date if necessary for longer tracking.

### **Repository Use**
This file is structured for GitHub documentation. Simply upload `Budgets_and_Alerts.md` along with the screenshots (`1_budget.png` and `2_budget.png`) to your repository.

