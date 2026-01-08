# QuickBooks Production Setup

## Current Status
✅ Production credentials obtained from Intuit Developer Portal
- Client ID: [saved securely]
- Client Secret: [saved securely]

## Configuration Steps

### 1. Update Router MCP Environment Variables

Edit `C:\Users\richa\.claude.json` and update the `router-mcp` section's `env`:

```json
"QUICKBOOKS_CLIENT_ID": "YOUR_PRODUCTION_CLIENT_ID",
"QUICKBOOKS_CLIENT_SECRET": "YOUR_PRODUCTION_CLIENT_SECRET",
"QUICKBOOKS_REFRESH_TOKEN": "NEEDS_TO_BE_GENERATED",
"QUICKBOOKS_REALM_ID": "YOUR_PRODUCTION_REALM_ID",
"QUICKBOOKS_SANDBOX": "false"
```

### 2. Generate Production Refresh Token

**IMPORTANT:** You need to go through OAuth flow once to get a production refresh token.

**Option A: Use OAuth Playground (Recommended)**
1. Go to: https://developer.intuit.com/app/developer/playground
2. Select your app (404 ACCT MCP)
3. Select scopes: `com.intuit.quickbooks.accounting`
4. Click "Get authorization code"
5. Sign in with your QuickBooks Online account
6. Grant permissions
7. Copy the **Refresh Token** from the response

**Option B: Manual OAuth Flow**
If you need to do this programmatically, we can create a simple OAuth helper script.

### 3. Get Your Production Realm ID (Company ID)

This is your actual QuickBooks company ID, not the sandbox one.

**How to find it:**
1. Log into QuickBooks Online: https://app.qbo.intuit.com
2. Look at the URL - it will contain your Realm ID
3. Format: `https://app.qbo.intuit.com/app/homepage?realmId=XXXXXXXXXX`
4. The number after `realmId=` is your production Realm ID

### 4. Test Production Connection

After updating all credentials, restart Claude Code and test:
```
- Get company info
- List customers
- Verify data matches your real QuickBooks account
```

## Important Notes

- **Backup current config** before making changes
- **Sandbox vs Production:** Make sure QUICKBOOKS_SANDBOX is set to "false"
- **Security:** Never commit production credentials to version control
- **Refresh Token:** The refresh token doesn't expire (unless revoked), so save it securely

## Troubleshooting

If you get authentication errors:
1. Verify Client ID and Client Secret are correct
2. Ensure Realm ID is correct (production, not sandbox)
3. Verify refresh token was generated for production, not sandbox
4. Check that QUICKBOOKS_SANDBOX="false"

---

**Last Updated:** January 6, 2026
