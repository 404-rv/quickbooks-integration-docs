# QuickBooks Integration Project

**Status:** In Development - Production Setup
**Created:** January 6, 2026
**Purpose:** Internal QuickBooks API integration for The Curative Co.

---

## Project Overview

This project contains the documentation and configuration for The Curative Co.'s internal QuickBooks integration. The integration connects to QuickBooks Online via the Router MCP service to access financial data for internal business operations.

## Current Status

### ✅ Completed
- Sandbox environment setup and testing
- Service connectivity verification
- All 9 QuickBooks API actions tested and working
- EULA and Privacy Policy created

### 🔄 In Progress
- Production credentials application
- Intuit Developer Portal compliance tasks

### 📋 Pending
- Host domain and URL configuration
- App category selection
- Hosting information submission

## Files in This Project

- **EULA.md** - End-User License Agreement for internal use
- **PRIVACY-POLICY.md** - Privacy policy documenting data access and handling
- **README.md** - This file

## API Access Scope

The integration accesses:

### Customer & Vendor Data
- Names, emails, addresses, phone numbers, websites

### Financial Data
- Invoices and invoice details
- Receipts and payment records
- Account balances and transactions

### Banking Data
- Company bank account information
- Transaction records

## Technical Details

**Integration Method:** Router MCP Service
**Authentication:** OAuth 2.0
**Environment:**
- Sandbox: ✅ Active and tested
- Production: 🔄 Pending credentials

**Available Actions:**
1. `get_company_info` - Company settings and metadata
2. `list_customers` - Customer management
3. `get_customer` - Individual customer details
4. `list_invoices` - Invoice operations
5. `get_invoice` - Individual invoice details
6. `list_accounts` - Chart of accounts
7. `list_items` - Products and services
8. `list_vendors` - Vendor management
9. `query` - SQL-like queries for complex data retrieval

## Test Results (Sandbox)

**Date:** January 6, 2026

- ✅ Service discovery working
- ✅ Company info retrieval successful
- ✅ Customer listing with pagination
- ✅ Invoice filtering (unpaid invoices test)
- ✅ Response times: 291ms - 1,468ms

## Next Steps

1. Complete Intuit Developer Portal requirements:
   - [ ] Add host domain, launch URL, disconnect URL
   - [ ] Select app category
   - [ ] Provide hosting information

2. Obtain production credentials

3. Configure production environment in Router MCP

4. Test production connectivity

5. Deploy for internal use

## Compliance

This integration is for **internal use only** by authorized personnel of The Curative Co.

- All data remains within company control
- No external sharing or third-party access
- Follows company data security policies
- Complies with applicable data protection regulations

## Contact

For questions about this integration:
**The Curative Co.**
Website: thecurative.co

---

**Last Updated:** January 6, 2026
