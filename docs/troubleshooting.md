## 🛠️ `troubleshooting.md`

```markdown
# Troubleshooting — Avatar Cloud Demo

This document captures common issues and fixes during deployment.

## 1. Null Reference Error
- **Symptom:** App loaded but showed `NullReferenceException`.
- **Cause:** Connection string mismatch in `web.config`.
- **Fix:** Corrected DB name and credentials, redeployed config.

## 2. IIS Binding Conflict
- **Symptom:** IIS warning: duplicate `*:80` binding.
- **Cause:** Default IIS site + AppDemo site both bound to port 80.
- **Fix:** Removed default site binding, kept only AppDemo binding.

## 3. SQL Connectivity Blocked
- **Symptom:** Login failed from VM.
- **Cause:** SQL firewall missing VM IP.
- **Fix:** Added VM public IP to SQL server firewall rules.

## 4. RDP Access Denied
- **Symptom:** Couldn’t RDP into VM.
- **Cause:** NSG inbound rule missing or source not restricted.
- **Fix:** Added inbound rule for 3389, scoped to my workstation IP.

## 5. Diagnostic Data Missing
- **Symptom:** No logs in Log Analytics.
- **Cause:** Diagnostic settings not enabled.
- **Fix:** Configured SQL diagnostic settings → Log Analytics workspace.

## 6. SQLCMD File Execution Failure
- **Symptom:** `sqlcmd` returned error: “Cannot find the file specified.”
- **Cause:** File path was incorrect or script not saved properly.
- **Fix:** Created the SQL script dynamically using PowerShell:
 


