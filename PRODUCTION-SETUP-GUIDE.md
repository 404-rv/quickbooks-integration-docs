# QuickBooks Production Credentials Setup Guide

**Complete Step-by-Step Guide**
**Last Updated:** January 6, 2026
**Time Required:** 1-2 hours

---

## Table of Contents

1. [Overview](#overview)
2. [Prerequisites](#prerequisites)
3. [Phase 1: Create Compliance Documents](#phase-1-create-compliance-documents)
4. [Phase 2: Host Documents Publicly](#phase-2-host-documents-publicly)
5. [Phase 3: Configure Intuit Developer Portal](#phase-3-configure-intuit-developer-portal)
6. [Phase 4: Complete Compliance Questionnaire](#phase-4-complete-compliance-questionnaire)
7. [Phase 5: Obtain Production Credentials](#phase-5-obtain-production-credentials)
8. [Phase 6: Configure Router MCP](#phase-6-configure-router-mcp)
9. [Phase 7: Test Production Connection](#phase-7-test-production-connection)
10. [Troubleshooting](#troubleshooting)

---

## Overview

Setting up QuickBooks production credentials is more complex than most API integrations because Intuit requires:
- Public EULA and Privacy Policy documents
- Detailed compliance questionnaire (30+ questions)
- OAuth 2.0 flow with refresh tokens
- App profile configuration with URLs and hosting information

This guide documents the complete process used successfully for The Curative Co. integration.

**What You'll Get:**
- Production Client ID
- Production Client Secret
- Production Refresh Token
- Production Realm ID (Company ID)

---

## Prerequisites

### 1. Intuit Developer Account
- Create account at: https://developer.intuit.com/
- Verify email address
- Accept Developer Terms of Service

### 2. QuickBooks Online Company
- Active QuickBooks Online account (where you'll connect)
- Admin access to the company
- Know your company name and basic info

### 3. Public Web Hosting
- GitHub account (recommended - free public hosting)
- Or any public web server for hosting documents

### 4. Router MCP Installed
- Router MCP service running
- Access to configuration file (`.claude.json`)

### 5. Time Allocation
- Document preparation: 20-30 minutes
- Portal configuration: 15-20 minutes
- Compliance questionnaire: 30-45 minutes
- OAuth and testing: 10-15 minutes

---

## Phase 1: Create Compliance Documents

### Documents Required
1. End-User License Agreement (EULA)
2. Privacy Policy

### EULA Template

Create file: `EULA.md`

```markdown
# END-USER LICENSE AGREEMENT (EULA)
## QuickBooks Integration Application

**Effective Date:** [Current Date]
**Last Updated:** [Current Date]
**Company:** [Your Company Name]
**Application:** QuickBooks Data Integration (Internal Use)

---

## 1. Agreement Overview

This End-User License Agreement ("Agreement") is a legal agreement between [Your Company Name] ("Company," "we," "us," or "our") and authorized users ("User," "you," or "your") for the use of our internal QuickBooks Integration Application (the "Application").

**IMPORTANT:** This Application is designed exclusively for internal business use by authorized employees and contractors of [Your Company Name].

## 2. License Grant

### 2.1 Scope
We grant you a non-exclusive, non-transferable, revocable license to use the Application solely for internal business purposes as an authorized employee or contractor of [Your Company Name].

### 2.2 Restrictions
You may NOT:
- Transfer, sublicense, or share your access credentials
- Use the Application for personal or non-business purposes
- Attempt to reverse engineer, decompile, or disassemble the Application
- Access data beyond your authorized scope
- Export or share sensitive data outside approved channels

## 3. User Responsibilities

### 3.1 Account Security
- Maintain confidentiality of login credentials
- Report unauthorized access immediately
- Log out after each session
- Follow company security policies

### 3.2 Data Handling
- Use accessed data only for authorized business purposes
- Follow company data protection and privacy policies
- Do not share sensitive financial information externally
- Report any suspected data breaches immediately

### 3.3 Compliance
- Comply with all applicable laws and regulations
- Follow company policies regarding financial data
- Maintain professional standards when handling customer/vendor information

## 4. Application Purpose

The Application integrates with QuickBooks Online to enable authorized personnel to:
- Access and manage customer and vendor information
- Process invoices and payments
- Generate financial reports and analytics
- Perform accounting and bookkeeping tasks
- Support business operations and decision-making

## 5. Data Access and Security

The Application accesses the following data from QuickBooks:

### 5.1 Customer and Vendor Information
- Names, email addresses, physical addresses, phone numbers, websites
- Company names and contact details

### 5.2 Financial Information
- Invoices and invoice details
- Receipts and payment records
- Account balances and transactions
- Sales data and revenue information

### 5.3 Banking Information
- Company bank account details
- Transaction records
- Payment processing information

**Security Measures:**
- OAuth 2.0 authentication
- Encrypted data transmission (HTTPS/TLS)
- Role-based access controls
- Audit logging of data access

## 6. Permitted Operations

The Application can perform both **read and write operations**, including:
- Creating and updating customer/vendor records
- Generating and modifying invoices
- Recording payments and transactions
- Updating account information
- Running queries and generating reports

## 7. Intellectual Property

### 7.1 Ownership
All rights, title, and interest in the Application remain the property of [Your Company Name]. This Agreement does not grant you any ownership rights.

### 7.2 QuickBooks Integration
This Application integrates with Intuit QuickBooks Online using official APIs. QuickBooks and related trademarks are property of Intuit Inc.

## 8. Limitation of Liability

### 8.1 No Warranties
THE APPLICATION IS PROVIDED "AS IS" WITHOUT WARRANTIES OF ANY KIND, EXPRESS OR IMPLIED.

### 8.2 Limitation
TO THE MAXIMUM EXTENT PERMITTED BY LAW, [YOUR COMPANY NAME] SHALL NOT BE LIABLE FOR ANY INDIRECT, INCIDENTAL, SPECIAL, OR CONSEQUENTIAL DAMAGES.

## 9. Term and Termination

### 9.1 Term
This Agreement remains in effect as long as you are an authorized user of the Application.

### 9.2 Termination
- Your access may be terminated at any time by company management
- You may request termination of your access at any time
- Upon termination, you must cease all use of the Application
- Confidentiality obligations survive termination

### 9.3 Post-Termination
Upon termination of employment or contract:
- All access rights are immediately revoked
- You must return or delete any exported data
- Confidentiality obligations remain in effect

## 10. Changes to This Agreement

We reserve the right to modify this Agreement at any time. Users will be notified of material changes via email or internal communication. Continued use after changes constitutes acceptance.

## 11. Governing Law

This Agreement is governed by the laws of [Your Jurisdiction], without regard to conflict of law principles.

## 12. Contact Information

For questions about this Agreement or the Application:

**[Your Company Name]**
Email: [your-company-email]
Website: [your-website]

## 13. Acknowledgment

By using the QuickBooks Integration Application, you acknowledge that:
- You have read and understood this Agreement
- You agree to be bound by its terms
- You are an authorized user with legitimate business need for access
- You will comply with all security and data handling requirements

---

**Last Reviewed:** [Current Date]

**This Agreement is for internal use only and applies to authorized employees and contractors of [Your Company Name].**
```

### Privacy Policy Template

Create file: `PRIVACY-POLICY.md`

```markdown
# PRIVACY POLICY
## QuickBooks Integration Application

**Effective Date:** [Current Date]
**Last Updated:** [Current Date]
**Company:** [Your Company Name]
**Application:** QuickBooks Data Integration (Internal Use)

---

## 1. Overview

This Privacy Policy describes how [Your Company Name] ("Company," "we," "us," or "our") collects, uses, and protects information through our internal QuickBooks Integration Application (the "Application"). This Application is designed exclusively for internal business use by authorized personnel.

## 2. Scope

This policy applies to:
- All employees and authorized contractors of [Your Company Name]
- All data accessed through the QuickBooks Integration Application
- Internal business operations only

**Important:** This is an internal application. We do not share data with third parties, sell data, or use it for external marketing purposes.

## 3. Information We Access

Through the QuickBooks API integration, the Application accesses:

### 3.1 Customer and Vendor Information
- Full names
- Email addresses
- Physical addresses
- Phone numbers
- Website URLs
- Company names

### 3.2 Financial Information
- Invoices and invoice details
- Receipts and payment records
- Account balances
- Transaction histories
- Sales data

### 3.3 Banking Information
- Company bank account details
- Bank account numbers (for [Your Company Name] accounts only)
- Transaction records
- Payment processing information

## 4. How We Use Information

We use the accessed information solely for internal business purposes:

- **Financial Management:** Processing invoices, tracking payments, managing accounts receivable/payable
- **Business Analytics:** Analyzing business performance, generating reports, forecasting
- **Customer Relationship Management:** Managing customer and vendor relationships
- **Compliance:** Meeting accounting, tax, and regulatory requirements
- **Internal Operations:** Supporting day-to-day business operations and decision-making

## 5. Data Storage and Security

### 5.1 Security Measures
We implement industry-standard security measures to protect accessed data:

- Encrypted data transmission (HTTPS/TLS)
- OAuth 2.0 authentication with QuickBooks
- Role-based access controls
- Secure credential storage
- Regular security monitoring

### 5.2 Data Storage
- Data accessed through the Application is processed in real-time
- Credentials are stored securely in encrypted configuration files
- We do not maintain separate databases of QuickBooks data
- All data remains within QuickBooks unless explicitly exported for authorized business purposes

### 5.3 Access Controls
- Only authorized employees have access to the Application
- User access is logged and monitored
- Credentials are not shared between users
- Access can be revoked at any time

## 6. Data Sharing

### 6.1 Internal Sharing
Data accessed through the Application is shared only with:
- Authorized employees who require access for job functions
- Management for business analysis and decision-making
- Accounting and finance teams for financial operations

### 6.2 No External Sharing
We do NOT:
- Sell or rent data to third parties
- Share data with external marketing companies
- Use data for purposes outside of internal business operations
- Transfer data outside of [Your Company Name] except as required by law

### 6.3 Legal Requirements
We may disclose information if required by:
- Court orders or legal process
- Law enforcement requests with proper authorization
- Compliance with applicable laws and regulations
- Protection of company rights and property

## 7. Data Retention

- We access QuickBooks data as needed for business operations
- We do not indefinitely store copies of QuickBooks data outside the QuickBooks platform
- Exported reports and data are retained according to company record retention policies
- Financial records are retained as required by tax and accounting regulations

## 8. User Rights and Responsibilities

### 8.1 User Responsibilities
Authorized users must:
- Keep login credentials confidential
- Use the Application only for authorized business purposes
- Report any security incidents immediately
- Follow company data handling policies
- Log out after each session

### 8.2 User Rights
Authorized users have the right to:
- Access data relevant to their job functions
- Request information about their usage of the Application
- Report concerns about data handling
- Request access revocation at any time

## 9. Data Protection Compliance

We comply with applicable data protection laws and regulations, including:
- General Data Protection Regulation (GDPR) principles where applicable
- California Consumer Privacy Act (CCPA) requirements where applicable
- Financial data protection regulations
- Industry best practices for data security

## 10. Third-Party Services

### 10.1 QuickBooks Integration
This Application integrates with Intuit QuickBooks using official APIs:
- Intuit's Privacy Policy applies to data stored within QuickBooks
- We comply with Intuit's Developer Terms of Service
- OAuth 2.0 ensures secure authentication without storing passwords
- See Intuit's privacy policy at: https://www.intuit.com/privacy/

### 10.2 No Other Third Parties
We do not integrate with or share data with any other third-party services except as explicitly documented and approved.

## 11. Changes to This Policy

We may update this Privacy Policy as needed to reflect:
- Changes in our data practices
- New regulatory requirements
- Application updates or feature additions
- Security enhancements

Users will be notified of material changes via email or internal communication channels.

## 12. Security Incidents

In the event of a data security incident:
- Affected users will be notified promptly
- The incident will be investigated and documented
- Corrective measures will be implemented
- Regulatory notifications will be made as required by law

## 13. Contact Information

For questions, concerns, or requests regarding this Privacy Policy or data handling:

**[Your Company Name]**
Email: [your-company-email]
Website: [your-website]

**Data Protection Officer:** [if applicable]
Email: [dpo-email]

## 14. Consent

By using the QuickBooks Integration Application, you acknowledge that:
- You have read and understood this Privacy Policy
- You consent to the collection and use of information as described
- You understand this is an internal application for authorized business use only
- You agree to comply with all data handling and security requirements

---

**Last Reviewed:** [Current Date]

**This policy is subject to periodic review and updates to ensure compliance with evolving regulations and best practices.**
```

### Customization Checklist

Before using these templates, replace:
- `[Current Date]` → Today's date
- `[Your Company Name]` → Your company's legal name
- `[your-company-email]` → Support email address
- `[your-website]` → Company website
- `[Your Jurisdiction]` → Your state/country for legal purposes
- `[dpo-email]` → Data Protection Officer email (if applicable)

### Document Review

Have these documents reviewed by:
- Legal counsel (recommended)
- Compliance officer
- Data protection officer
- Management team

---

## Phase 2: Host Documents Publicly

Intuit requires publicly accessible URLs for your EULA and Privacy Policy.

### Option A: GitHub Pages (Recommended - Free)

**Step 1: Create GitHub Repository**
```bash
# Create project directory
mkdir quickbooks-integration-docs
cd quickbooks-integration-docs

# Initialize git
git init

# Copy your documents
cp path/to/EULA.md .
cp path/to/PRIVACY-POLICY.md .
cp path/to/README.md .

# Create commit
git add .
git commit -m "Initial commit: QuickBooks integration compliance documents"
```

**Step 2: Create GitHub Repository**
1. Go to: https://github.com/new
2. Repository name: `quickbooks-integration-docs` (or your choice)
3. Description: "QuickBooks integration compliance documentation"
4. **Visibility: PUBLIC** (required for Intuit to access)
5. Do NOT initialize with README (you already have one)
6. Click "Create repository"

**Step 3: Push to GitHub**
```bash
# Add remote (replace USERNAME with your GitHub username)
git remote add origin https://github.com/USERNAME/quickbooks-integration-docs.git

# Push to GitHub
git branch -M master
git push -u origin master
```

**Step 4: Get Raw URLs**

Your documents will be accessible at:
- EULA: `https://raw.githubusercontent.com/USERNAME/quickbooks-integration-docs/master/EULA.md`
- Privacy Policy: `https://raw.githubusercontent.com/USERNAME/quickbooks-integration-docs/master/PRIVACY-POLICY.md`

**Step 5: Verify URLs**

Test both URLs in a browser - you should see the markdown content displayed. If you get 404 errors, check:
- Repository is public
- File names match exactly (case-sensitive)
- Files are in the root directory
- URLs use `raw.githubusercontent.com` (not `github.com`)

### Option B: Your Own Web Server

If you prefer to host on your own domain:

1. Upload `EULA.md` and `PRIVACY-POLICY.md` to your web server
2. Ensure files are publicly accessible (no authentication required)
3. Test URLs return HTTP 200 status
4. Use HTTPS URLs (required by Intuit)

Example URLs:
- `https://yourdomain.com/legal/quickbooks-eula.html`
- `https://yourdomain.com/legal/quickbooks-privacy-policy.html`

---

## Phase 3: Configure Intuit Developer Portal

### Step 1: Create App

1. Go to: https://developer.intuit.com/app/developer/myapps
2. Click "Create an app"
3. Select platform: "QuickBooks Online"
4. App name: Choose a descriptive name (e.g., "404 ACCT MCP" or "[Company] QB Integration")
5. Click "Create app"

### Step 2: Add EULA and Privacy Policy URLs

1. In your app dashboard, find "App Profile" or "Keys & credentials"
2. Scroll to "Links" section
3. Add your URLs:
   - **EULA URL:** Your GitHub raw URL or hosted URL
   - **Privacy Policy URL:** Your GitHub raw URL or hosted URL
4. Click "Save"

### Step 3: Configure Redirect URI

1. Find "OAuth" or "Redirect URIs" section
2. Add redirect URI: `https://developer.intuit.com/v2/OAuth2Playground/RedirectUrl`
   - This is for the OAuth Playground (we'll use this to get credentials)
3. Click "Save"

**Note:** For production apps with actual OAuth flows, you'd add your own redirect URI here.

### Step 4: Add Host Domain, Launch URL, and Disconnect URL

1. Navigate to "App Profile" section
2. Fill in required fields:

**Host Domain:**
- If internal use only: Use a subdomain like `internal.yourcompany.com`
- This doesn't need to be a real, functional domain
- Example: `internal.thecurative.co`

**Launch URL:**
- Full URL where app "launches" (even if it's not a real web app)
- Example: `https://internal.yourcompany.com/quickbooks/oauth/callback`

**Disconnect URL:**
- URL called when user disconnects (can be same as launch URL)
- Example: `https://internal.yourcompany.com/quickbooks/oauth/disconnect`

**Important:** These URLs don't need to be functional for internal backend integrations. They're metadata requirements for Intuit's portal.

3. Click "Save"

### Step 5: Select App Category

1. Find "App Category" or "Categories" section
2. Select at least one category:
   - **Recommended:** "Accounting"
   - Other options: Finance, Productivity, Business Management
3. If unsure, choose "Accounting" since you're integrating with QuickBooks accounting data
4. Click "Save"

### Step 6: Provide Hosting Information

1. Find "Hosting Information" or "Where is your app hosted?" section
2. Options typically include:
   - Cloud provider (AWS, Google Cloud, Azure, etc.)
   - On-premises
   - Other
3. For internal integration, select the most accurate option:
   - If Router MCP runs on a specific cloud: Select that cloud provider
   - If on company servers: Select "On-premises"
   - If unsure: Select "Other"
4. You may need to provide additional details like IP address or region
5. Click "Save"

---

## Phase 4: Complete Compliance Questionnaire

This is the most time-consuming section (~30-45 minutes). Be thorough and accurate.

### Section 1: General Information

**Question: What does your app do?**
```
This application is an internal backend service that integrates with QuickBooks Online to access financial and customer data for business operations. It enables authorized employees to retrieve and manage QuickBooks data through a secure API integration using Router MCP (Model Context Protocol). The integration supports accounting, customer relationship management, invoicing, and financial reporting for internal business purposes only.
```

**Question: Who will use your app?**
```
Internal Use Only - Authorized employees and contractors of [Your Company Name]
```

**Question: Does your app integrate with platforms other than Intuit?**
- Select: **Yes** or **No** depending on your setup
- If Yes, list platforms (e.g., "Internal business systems, CRM, accounting tools")

### Section 2: App Information

**Question: Is this app for public use or internal use?**
- Select: **Internal use only**

**Question: How many users will access your app?**
- Provide an estimate: "1-10 users" or "10-50 users" depending on your company size

**Question: Is your app available on mobile platforms?**
- Select: **No** (unless you have a mobile component)

**Question: Does your app use generative AI or AI features?**
- Select: **No**
- **Important:** Even if you used Claude Code to build the integration, the QuickBooks integration itself doesn't use AI features

### Section 3: Authentication & Authorization

**Question: What authentication method does your app use?**
- Select: **OAuth 2.0**

**Question: How are QuickBooks access tokens stored?**
```
Access tokens are stored securely in encrypted configuration files with restricted file system permissions. Tokens are never logged, committed to version control, or transmitted to external services. Refresh tokens are used to obtain new access tokens as needed.
```

**Question: How often does your app refresh tokens?**
```
The application automatically refreshes access tokens before they expire (typically every 1 hour) using the refresh token. Refresh tokens are long-lived and securely stored in encrypted configuration.
```

**Question: How are credentials protected?**
```
- Client ID, Client Secret, and Refresh Token stored in encrypted configuration files
- File system permissions restrict access to authorized users only
- Credentials never hardcoded in source code
- No credentials exposed in logs or error messages
- Environment variables used for secure configuration management
```

### Section 4: API Usage

**Question: Which QuickBooks APIs will your app use?**
- Select: **Accounting API**
- If using others (Payments, Payroll, Time Tracking), select those too

**Question: What API operations will your app perform?**
- Select all that apply:
  - **Read data** (invoices, customers, vendors, accounts, items)
  - **Create data** (if you plan to create records)
  - **Update data** (if you plan to modify records)
  - **Delete data** (if you plan to delete records)

**Question: How frequently will your app make API calls?**
- Select: **On-demand during user interactions**
- Explanation: Router MCP is event-driven and only makes API calls when triggered by authorized user actions, not on a scheduled basis

**Question: What is the expected API call volume?**
- Estimate: "1-100 calls per day" or "100-1,000 calls per day" based on your usage
- Be realistic - you can always increase later

### Section 5: Accounting API Specific Questions

**Question: Which QuickBooks plans does your app support?**
- Select: **All plans** (Simple Start, Essentials, Plus, Advanced)
- Most integrations work across all plans

**Question: How does your app handle different QuickBooks versions?**
```
The application uses the latest QuickBooks API version and handles version differences gracefully. API responses are validated, and missing fields are handled with appropriate defaults. The integration is designed to work across all QuickBooks Online plan tiers.
```

**Question: Does your app support multiple companies/realms?**
- Select based on your needs:
  - **No** if connecting to only one QuickBooks company
  - **Yes** if supporting multiple companies/clients

**Question: How does your app handle QuickBooks data synchronization?**
```
The application retrieves data in real-time via API calls. No local database replication is performed. Data is processed and used immediately for business operations, with no persistent storage of QuickBooks data outside the QuickBooks platform except for authorized exports and reports.
```

### Section 6: Error Handling

**Question: How does your app handle API errors?**
```
The application implements comprehensive error handling:
- API errors are caught and logged with error codes and messages
- Retry logic for transient errors (rate limits, network issues)
- User-friendly error messages displayed to authorized users
- Failed operations do not corrupt data or leave partial updates
- All errors logged with timestamps and context for troubleshooting
```

**Question: Does your app log API responses for debugging?**
- Select: **Yes**
- Explanation: Error responses and intuit_tid values are logged for troubleshooting purposes, but sensitive data is redacted from logs

**Question: How are error logs protected?**
```
Error logs are stored on secure servers with restricted access. Logs are retained according to company policy (typically 30-90 days). Sensitive information (tokens, credentials, personal data) is redacted from logs. Logs are encrypted at rest and only accessible to authorized technical staff.
```

**Question: Does your app capture and use intuit_tid for error tracking?**
- Select: **Yes**
- Explanation: The intuit_tid (Intuit Transaction ID) from API responses is logged to assist with error troubleshooting and support requests

### Section 7: Security

**Question: Has your app experienced any security breaches in the past 12 months?**
- Select: **No** (if accurate)

**Question: Do you have a security incident response plan?**
- Select: **Yes**
- Brief description: "Security incidents are reported immediately to management and IT security team. Incident response includes containment, investigation, remediation, and notification as required by law."

**Question: How is data encrypted in transit?**
- Select: **HTTPS/TLS encryption for all API communications**

**Question: How is data encrypted at rest?**
```
Credentials and configuration files are encrypted at rest using operating system-level encryption. QuickBooks data is not stored locally except for temporary processing and authorized exports, which are protected with file system permissions.
```

**Question: Do you share QuickBooks data with third parties?**
- Select: **No**
- Confirm: Data is used exclusively for internal business operations and not shared with external parties

**Question: Does your app access data beyond what's necessary?**
- Select: **No**
- Explanation: The application only requests the minimum necessary scopes (accounting data) and only accesses data required for specific business functions

### Section 8: Data Handling

**Question: What data does your app access?**
List all data types:
```
- Customer information (names, emails, addresses, phone numbers)
- Vendor information (names, emails, addresses, phone numbers)
- Invoice data (amounts, dates, line items, status)
- Payment records (receipts, transactions, payment methods)
- Account information (chart of accounts, balances)
- Product/service items (names, descriptions, prices)
- Company information (business name, address, settings)
- Banking information (company bank accounts, transactions)
```

**Question: How long do you retain QuickBooks data?**
```
Real-time data is not persistently stored. Exported reports and data are retained according to company record retention policies and tax/accounting requirements (typically 7 years for financial records). Data can be deleted upon request in accordance with company policy.
```

**Question: Do users have the ability to delete their data?**
- Select: **Yes** (for internal users requesting access revocation)
- Explanation: Authorized users can request revocation of access and deletion of any exported data

**Question: Does your app comply with GDPR, CCPA, or other data protection regulations?**
- Select: **Yes**
- List applicable regulations: "GDPR principles, CCPA requirements, financial data protection regulations"

### Questionnaire Submission

**Before submitting:**
1. Review all answers for accuracy
2. Ensure all required questions are answered
3. Double-check drop-down selections are appropriate
4. Have a colleague or manager review if possible

**After submission:**
- You should receive confirmation that questionnaire is complete
- This may take a few minutes to process
- Production credentials should become available shortly after

---

## Phase 5: Obtain Production Credentials

### Option A: OAuth Playground (Recommended)

This method gets you all credentials (Client ID, Client Secret, Realm ID, Refresh Token) in one flow.

**Step 1: Navigate to OAuth Playground**
1. Go to: https://developer.intuit.com/app/developer/playground
2. Ensure you're logged into the Intuit Developer Portal

**Step 2: Select Your App**
1. From dropdown: Select your app (e.g., "404 ACCT MCP")
2. Environment: Should show "Production" (not Sandbox)

**Step 3: Configure Scopes**
1. Scopes section: Check `com.intuit.quickbooks.accounting`
2. This grants full read/write access to accounting data
3. If you need additional scopes (Payments, Payroll), select those too

**Step 4: Get Authorization Code**
1. Click "Get authorization code" button
2. You'll be redirected to QuickBooks Online sign-in
3. Sign in with the QuickBooks account you want to connect
4. **Important:** Use the production QuickBooks Online account, not sandbox

**Step 5: Grant Permissions**
1. QuickBooks will show permission screen
2. Review the permissions requested
3. Select the company you want to connect
4. Click "Connect" or "Authorize"

**Step 6: Retrieve Credentials**

After authorization, the OAuth Playground will display:

```json
{
  "access_token": "eyJlbmMiOiJBMTI4Q0JDLUhTMjU2IiwiYWxnIjoi...",
  "refresh_token": "RT1-107-H0-1776490655jrb32a85qvjlw95tijz7...",
  "token_type": "bearer",
  "expires_in": 3600,
  "x_refresh_token_expires_in": 8726400,
  "realmId": "123146183799949"
}
```

**Copy these values:**
- **Refresh Token** → `refresh_token` (starts with "RT1-")
- **Realm ID** → `realmId` (numeric ID)

**Step 7: Get Client ID and Client Secret**
1. Go back to your app in Developer Portal
2. Navigate to "Keys & credentials" or "Production keys"
3. Copy:
   - **Client ID** (alphanumeric string)
   - **Client Secret** (alphanumeric string)

### Option B: Manual OAuth Flow

If you need to implement custom OAuth:

**Step 1: Build Authorization URL**
```
https://appcenter.intuit.com/connect/oauth2?
  client_id=YOUR_CLIENT_ID
  &scope=com.intuit.quickbooks.accounting
  &redirect_uri=YOUR_REDIRECT_URI
  &response_type=code
  &state=RANDOM_STRING
```

**Step 2: User Authorizes**
- User visits URL and authorizes
- They're redirected to your redirect_uri with authorization code

**Step 3: Exchange Code for Tokens**
```bash
curl -X POST https://oauth.platform.intuit.com/oauth2/v1/tokens/bearer \
  -H "Content-Type: application/x-www-form-urlencoded" \
  -H "Authorization: Basic BASE64(client_id:client_secret)" \
  -d "grant_type=authorization_code" \
  -d "code=AUTHORIZATION_CODE" \
  -d "redirect_uri=YOUR_REDIRECT_URI"
```

Response includes `access_token`, `refresh_token`, and `realmId`.

### Credentials Summary

You should now have:
- ✅ **Client ID:** `AB25WFZUAXL90cZ5QQpqahyfrq8FPLZPAuzuuiwfT42mpte9PR` (example)
- ✅ **Client Secret:** `uNj6xFUZrPkE8M0b1lrR3xVKsltFuEWV4zsluQIz` (example)
- ✅ **Refresh Token:** `RT1-107-H0-1776490655jrb32a85qvjlw95tijz7` (example)
- ✅ **Realm ID:** `123146183799949` (example)

**Store these securely** - you'll need them for configuration.

---

## Phase 6: Configure Router MCP

### Step 1: Locate Configuration File

Find your Router MCP configuration file:
- **Location:** `C:\Users\[username]\.claude.json` (Windows)
- **Location:** `~/.claude.json` (Mac/Linux)

### Step 2: Backup Current Config

**Always backup before editing!**

```bash
# Windows PowerShell
Copy-Item "C:\Users\[username]\.claude.json" "C:\Users\[username]\.claude.json.backup"

# Mac/Linux
cp ~/.claude.json ~/.claude.json.backup
```

### Step 3: Update QuickBooks Environment Variables

Open `.claude.json` and find the `router-mcp` section under `mcpServers`.

**Before (Sandbox):**
```json
"env": {
  "QUICKBOOKS_CLIENT_ID": "SANDBOX_CLIENT_ID",
  "QUICKBOOKS_CLIENT_SECRET": "SANDBOX_CLIENT_SECRET",
  "QUICKBOOKS_REFRESH_TOKEN": "SANDBOX_REFRESH_TOKEN",
  "QUICKBOOKS_REALM_ID": "SANDBOX_REALM_ID",
  "QUICKBOOKS_SANDBOX": "true"
}
```

**After (Production):**
```json
"env": {
  "QUICKBOOKS_CLIENT_ID": "AB25WFZUAXL90cZ5QQpqahyfrq8FPLZPAuzuuiwfT42mpte9PR",
  "QUICKBOOKS_CLIENT_SECRET": "uNj6xFUZrPkE8M0b1lrR3xVKsltFuEWV4zsluQIz",
  "QUICKBOOKS_REFRESH_TOKEN": "RT1-107-H0-1776490655jrb32a85qvjlw95tijz7",
  "QUICKBOOKS_REALM_ID": "123146183799949",
  "QUICKBOOKS_SANDBOX": "false"
}
```

**Important Changes:**
1. Replace all credential values with your production credentials
2. **Change `QUICKBOOKS_SANDBOX` from `"true"` to `"false"`** ← Critical!
3. Ensure all values are strings (enclosed in quotes)
4. No trailing commas on last property

### Step 4: Validate JSON Syntax

Before saving, validate your JSON:

**Option A: Online Validator**
- Copy the entire `.claude.json` file
- Paste into: https://jsonlint.com/
- Click "Validate JSON"
- Fix any syntax errors

**Option B: Command Line**
```bash
# Windows (PowerShell with jq installed)
Get-Content .claude.json | jq .

# Mac/Linux
cat ~/.claude.json | jq .
```

If valid, you'll see formatted JSON output. If invalid, you'll see error messages.

### Step 5: Save Configuration

1. Save the `.claude.json` file
2. **Restart Claude Code** (required for changes to take effect)
3. Close and reopen your terminal/CLI

---

## Phase 7: Test Production Connection

### Step 1: Verify Service Discovery

List available QuickBooks actions:

```bash
# List all Router MCP services
mcp__router-mcp__list_services()

# List QuickBooks actions
mcp__router-mcp__list_actions(service: "quickbooks")
```

You should see 9 actions:
1. `get_company_info`
2. `list_customers`
3. `get_customer`
4. `list_invoices`
5. `get_invoice`
6. `list_accounts`
7. `list_items`
8. `list_vendors`
9. `query`

### Step 2: Test Company Info

**Request:**
```javascript
mcp__router-mcp__route_request(
  service: "quickbooks",
  action: "get_company_info",
  params: {}
)
```

**Expected Response:**
```json
{
  "CompanyInfo": {
    "CompanyName": "Your Company Name",
    "LegalName": "Your Company Legal Name",
    "CompanyAddr": {
      "City": "Your City",
      "Country": "USA"
    },
    "Email": { "Address": "your-email@company.com" },
    "Id": "123146183799949"
  }
}
```

**Verify:**
- ✅ Company name matches your production QuickBooks company
- ✅ Data looks realistic (not sandbox test data)
- ✅ Email and address match your real business
- ✅ No authentication errors

### Step 3: Test Customer Listing

**Request:**
```javascript
mcp__router-mcp__route_request(
  service: "quickbooks",
  action: "list_customers",
  params: { maxResults: 5 }
)
```

**Expected Response:**
```json
{
  "QueryResponse": {
    "Customer": [
      {
        "DisplayName": "Real Customer Name",
        "CompanyName": "Real Customer Company",
        "PrimaryEmailAddr": { "Address": "real@customer.com" },
        "Id": "12345"
      }
    ],
    "maxResults": 5
  }
}
```

**Verify:**
- ✅ Customer names are real (not "Test Customer")
- ✅ Email addresses look legitimate
- ✅ Count matches expected production data volume

### Step 4: Test Invoice Query

**Request:**
```javascript
mcp__router-mcp__route_request(
  service: "quickbooks",
  action: "list_invoices",
  params: {
    maxResults: 5,
    where: "Balance > '0'"
  }
)
```

**Expected Response:**
```json
{
  "QueryResponse": {
    "Invoice": [
      {
        "DocNumber": "1001",
        "TotalAmt": 1500.00,
        "Balance": 1500.00,
        "CustomerRef": { "name": "Real Customer" },
        "Id": "54321"
      }
    ]
  }
}
```

**Verify:**
- ✅ Invoice numbers and amounts look realistic
- ✅ Customer references match actual customers
- ✅ Balances reflect real business data

### Step 5: Performance Check

**Expected response times:**
- `get_company_info`: 200-500ms
- `list_customers`: 300-800ms
- `list_invoices`: 400-1,500ms (depends on data volume)
- `query`: 500-2,000ms (depends on query complexity)

If response times are consistently > 3 seconds, investigate network or API issues.

### Step 6: Error Testing

Test error handling by requesting a non-existent customer:

**Request:**
```javascript
mcp__router-mcp__route_request(
  service: "quickbooks",
  action: "get_customer",
  params: { id: "999999999" }
)
```

**Expected Response:**
```json
{
  "error": {
    "code": "404",
    "message": "Object not found",
    "intuit_tid": "..."
  }
}
```

Verify error is handled gracefully (not a crash).

### Troubleshooting Test Issues

**Issue: "401 Unauthorized"**
- Cause: Invalid credentials or refresh token
- Fix: Verify Client ID, Client Secret, and Refresh Token are correct
- Check: `QUICKBOOKS_SANDBOX` is set to `"false"`

**Issue: "Wrong company data returned"**
- Cause: Wrong Realm ID
- Fix: Verify Realm ID matches your production company
- Check: Log into QuickBooks Online and verify company in URL: `?realmId=XXXXXXXXXX`

**Issue: "Token expired"**
- Cause: Refresh token invalid or revoked
- Fix: Regenerate refresh token using OAuth Playground
- Note: Refresh tokens can expire if not used for 100 days

**Issue: "Cannot read properties of undefined"**
- Cause: JSON parse error or missing config
- Fix: Validate `.claude.json` syntax with JSON validator
- Check: All required environment variables are present

---

## Troubleshooting

### Common Issues and Solutions

#### 1. Authentication Errors

**Error:** `401 Unauthorized` or `Token validation failed`

**Possible Causes:**
- Wrong Client ID or Client Secret
- Expired or revoked Refresh Token
- Sandbox flag set incorrectly
- Realm ID mismatch

**Solutions:**
1. Verify credentials match Intuit Developer Portal exactly
2. Confirm `QUICKBOOKS_SANDBOX` is `"false"` for production
3. Regenerate refresh token if older than 100 days
4. Check Realm ID matches company ID from QuickBooks URL
5. Restart Claude Code after config changes

#### 2. Wrong Company Data

**Error:** Seeing sandbox data instead of production data

**Possible Causes:**
- `QUICKBOOKS_SANDBOX` still set to `"true"`
- Using sandbox Realm ID instead of production
- Using sandbox refresh token

**Solutions:**
1. Double-check `QUICKBOOKS_SANDBOX: "false"` in config
2. Verify Realm ID from production QuickBooks URL
3. Ensure OAuth Playground was used with production account
4. Clear any cached tokens and restart

#### 3. Token Refresh Issues

**Error:** `Unable to refresh access token`

**Possible Causes:**
- Refresh token expired (unused for 100+ days)
- Refresh token revoked by user
- Company disconnected the app

**Solutions:**
1. Regenerate refresh token using OAuth Playground
2. Check Intuit Developer Portal for app status
3. Verify app hasn't been disconnected in QuickBooks settings
4. Contact Intuit Support if persistent issues

#### 4. Rate Limiting

**Error:** `429 Too Many Requests`

**Possible Causes:**
- Exceeding QuickBooks API rate limits
- Too many concurrent requests

**Solutions:**
1. Implement retry logic with exponential backoff
2. Reduce request frequency
3. Batch operations where possible
4. Check rate limit details in response headers

#### 5. JSON Configuration Errors

**Error:** Claude Code fails to start or Router MCP not available

**Possible Causes:**
- Invalid JSON syntax in `.claude.json`
- Missing quotes around string values
- Trailing commas
- Special characters not escaped

**Solutions:**
1. Validate JSON using jsonlint.com
2. Ensure all credential values are strings (in quotes)
3. Remove any trailing commas
4. Use online JSON formatter to fix structure

#### 6. Permission Errors

**Error:** `Insufficient permissions` or `Access denied`

**Possible Causes:**
- Insufficient OAuth scopes granted
- User role doesn't have access to requested data
- Company settings restrict API access

**Solutions:**
1. Verify `com.intuit.quickbooks.accounting` scope was granted
2. Check user has admin/company admin role in QuickBooks
3. Review company settings in QuickBooks for API restrictions
4. Re-authorize with full permissions if needed

### Getting Help

**Intuit Developer Support:**
- Developer Forums: https://help.developer.intuit.com/
- Support Portal: https://help.developer.intuit.com/s/
- Documentation: https://developer.intuit.com/app/developer/qbo/docs/get-started

**Router MCP Support:**
- Check Router MCP documentation
- Review error logs in Claude Code
- Test with curl to isolate Router MCP vs QuickBooks issues

**Common Resources:**
- QuickBooks API Explorer: https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/account
- OAuth 2.0 Playground: https://developer.intuit.com/app/developer/playground
- API Reference: https://developer.intuit.com/app/developer/qbo/docs/api/accounting/most-commonly-used

---

## Appendix: Quick Reference

### Credentials Checklist

Production credentials required:
- [ ] Client ID (from Intuit Developer Portal)
- [ ] Client Secret (from Intuit Developer Portal)
- [ ] Refresh Token (from OAuth Playground)
- [ ] Realm ID (from OAuth Playground or QuickBooks URL)

### Environment Variables

Required in `.claude.json` router-mcp `env` section:
```json
{
  "QUICKBOOKS_CLIENT_ID": "your-production-client-id",
  "QUICKBOOKS_CLIENT_SECRET": "your-production-client-secret",
  "QUICKBOOKS_REFRESH_TOKEN": "RT1-...",
  "QUICKBOOKS_REALM_ID": "your-realm-id",
  "QUICKBOOKS_SANDBOX": "false"
}
```

### URLs to Remember

- **Developer Portal:** https://developer.intuit.com/app/developer/myapps
- **OAuth Playground:** https://developer.intuit.com/app/developer/playground
- **QuickBooks Online:** https://app.qbo.intuit.com
- **API Documentation:** https://developer.intuit.com/app/developer/qbo/docs/api/accounting

### Time Estimates

- Document preparation: 20-30 minutes
- GitHub hosting: 5-10 minutes
- Portal configuration: 15-20 minutes
- Compliance questionnaire: 30-45 minutes
- OAuth credentials: 5-10 minutes
- Configuration update: 5 minutes
- Testing: 10-15 minutes

**Total:** 1.5 - 2.5 hours (first time)

### Support Contacts

- **Intuit Support:** https://help.developer.intuit.com/s/
- **QuickBooks Community:** https://quickbooks.intuit.com/learn-support/en-us/help-articles
- **Router MCP:** [Your internal support or documentation]

---

**Document Version:** 1.0
**Last Updated:** January 6, 2026
**Based on:** Successful production setup for The Curative Co. on January 6, 2026

**Notes:**
- This guide reflects the process as of January 2026
- Intuit may update requirements or portal layout
- Always check Intuit Developer documentation for latest requirements
- Keep this document updated as processes change
