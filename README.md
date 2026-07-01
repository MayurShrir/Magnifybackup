import os
from weasyprint import HTML

# Create directories if they don't exist
os.makedirs("/tmp", exist_ok=True)

html_content_v2 = """
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8">
    <title>Comprehensive System Administration Guide: Automated Encrypted Database Backup</title>
    <style>
        @page {
            size: A4;
            margin: 20mm 15mm;
            background-color: #ffffff;
            @bottom-right {
                content: "Page " counter(page) " of " counter(pages);
                font-family: 'Segoe UI', Arial, sans-serif;
                font-size: 8.5pt;
                color: #7f8c8d;
            }
            @bottom-left {
                content: "Internal DevOps Documentation | Magnify Production Infrastructure";
                font-family: 'Segoe UI', Arial, sans-serif;
                font-size: 8.5pt;
                color: #7f8c8d;
            }
        }
        
        body {
            font-family: 'Segoe UI', Arial, sans-serif;
            color: #2c3e50;
            line-height: 1.6;
            font-size: 10pt;
            margin: 0;
            padding: 0;
        }

        *, *::before, *::after {
            box-sizing: border-box;
        }

        .header-container {
            margin: -20mm -15mm 25px -15mm;
            padding: 30px 15mm;
            background-color: #111827;
            color: #ffffff;
            border-bottom: 5px solid #2563eb;
        }

        h1 {
            font-size: 22pt;
            margin: 0 0 8px 0;
            font-weight: 700;
            letter-spacing: -0.5px;
            color: #ffffff;
        }

        .subtitle {
            font-size: 11pt;
            color: #3b82f6;
            margin: 0;
            text-transform: uppercase;
            letter-spacing: 1.5px;
            font-weight: 600;
        }

        h2 {
            font-size: 14pt;
            color: #111827;
            border-left: 5px solid #2563eb;
            padding-left: 12px;
            margin-top: 30px;
            margin-bottom: 15px;
            page-break-after: avoid;
            font-weight: 600;
        }

        h3 {
            font-size: 11.5pt;
            color: #1f2937;
            margin-top: 20px;
            margin-bottom: 10px;
            font-weight: 600;
            page-break-after: avoid;
        }

        p {
            margin: 0 0 12px 0;
            text-align: justify;
        }

        .meta-box {
            background-color: #f9fafb;
            border: 1px solid #e5e7eb;
            border-radius: 6px;
            padding: 15px 20px;
            margin-bottom: 25px;
        }

        .meta-table {
            width: 100%;
            border-collapse: collapse;
        }

        .meta-table td {
            padding: 6px 0;
            font-size: 9.5pt;
            vertical-align: top;
        }

        .meta-table td.label {
            font-weight: bold;
            color: #4b5563;
            width: 25%;
        }

        .meta-table td.value {
            color: #1f2937;
        }

        code {
            font-family: 'Consolas', 'Courier New', monospace;
            background-color: #f3f4f6;
            padding: 2px 6px;
            border-radius: 4px;
            font-size: 9.5pt;
            color: #dc2626;
        }

        pre {
            font-family: 'Consolas', 'Courier New', monospace;
            background-color: #1f2937;
            color: #f9fafb;
            padding: 14px 18px;
            border-radius: 6px;
            font-size: 9pt;
            overflow: hidden;
            margin: 12px 0 18px 0;
            white-space: pre-wrap;
            word-wrap: break-word;
            page-break-inside: avoid;
            border-left: 4px solid #9ca3af;
        }

        ul, ol {
            margin: 0 0 15px 0;
            padding-left: 22px;
        }

        li {
            margin-bottom: 6px;
        }

        .alert-card {
            background-color: #eff6ff;
            border-left: 4px solid #2563eb;
            color: #1e40af;
            padding: 15px 18px;
            border-radius: 0 6px 6px 0;
            margin: 20px 0;
            page-break-inside: avoid;
        }

        .alert-card p {
            margin: 0;
            color: #1e3a8a;
        }
        
        .alert-warning {
            background-color: #fffbeb;
            border-left: 4px solid #d97706;
            color: #92400e;
            padding: 15px 18px;
            border-radius: 0 6px 6px 0;
            margin: 20px 0;
            page-break-inside: avoid;
        }
        
        .alert-warning p {
            margin: 0;
            color: #78350f;
        }

        .table-custom {
            width: 100%;
            border-collapse: collapse;
            margin: 15px 0;
            page-break-inside: avoid;
        }

        .table-custom th {
            background-color: #f3f4f6;
            color: #111827;
            font-weight: 600;
            text-align: left;
            padding: 10px;
            border-bottom: 2px solid #e5e7eb;
            font-size: 9.5pt;
        }

        .table-custom td {
            padding: 10px;
            border-bottom: 1px solid #e5e7eb;
            font-size: 9.5pt;
        }
    </style>
</head>
<body>

    <div class="header-container">
        <h1>System Administration Guide & SOP</h1>
        <div class="subtitle">Automated Database Backups, GPG Encryption, and Azure Blob Storage Sync</div>
    </div>

    <div class="meta-box">
        <table class="meta-table">
            <tr>
                <td class="label">Host Machine:</td>
                <td class="value">Magnify-Backend-VM (Bitnami Stack Environment)</td>
                <td class="label">Target Destination:</td>
                <td class="value">Azure Blob Storage Private Container</td>
            </tr>
            <tr>
                <td class="label">Data Format:</td>
                <td class="value">Encrypted Binary Envelopes (<code>.sql.gpg</code>)</td>
                <td class="label">Authentication Protocol:</td>
                <td class="value">Azure VM Managed Identity (Passwordless Token)</td>
            </tr>
            <tr>
                <td class="label">Automation Engine:</td>
                <td class="value">Linux Cron Daemon (System-wide Context)</td>
                <td class="label">Retention Strategy:</td>
                <td class="value">30-Day Automated Azure Lifecycle Purge</td>
            </tr>
        </table>
    </div>

    <h2>1. Executive & Security Summary</h2>
    <p>This technical directive defines the operating standards for the automated backup, data-at-rest hardening, and cloud-layer offloading pipeline configured on the <code>Magnify-Backend-VM</code>. In order to mitigate risks associated with filesystem intrusion, database compromise, or catastrophic hardware faults, a <strong>Zero-Trust Architecture</strong> has been deployed.</p>
    <p>The database instances are built, isolated, and cryptographically packed directly on-site prior to egress transmission. Egress shipping targets an isolated, non-public Azure Blob Storage infrastructure utilizing modern identity assertions rather than static account tokens or cleartext connection parameters.</p>

    <h2>2. Cryptographic Hardening (GPG Envelopes)</h2>
    <p>Backups are stored inside the target Azure Blob Storage container strictly in an <strong>encrypted binary format (<code>.sql.gpg</code>)</strong>. The system employs **GnuPG (GPG)** running a symmetric **AES-256 bit** encryption cipher algorithm.</p>
    <ul>
        <li><strong>Security Guarantee:</strong> Even in the event of an unauthenticated breach or data leak of the Azure storage container, the data payloads remain completely unreadable to unauthorized entities. Without the dedicated encryption key passphrase, it is statistically impossible to decipher or modify the underlying database schemas.</li>
        <li><strong>Secret Storage:</strong> The decryption key parameter matches the <code>ENC_KEY</code> variable value defined within the server core script configuration module. This key should be archived off-server within a dedicated, enterprise-grade credential manager.</li>
    </ul>

    <h2>3. Production Environment Script Deployment</h2>
    <p>The operational logic resides at <code>/home/bitnami/scripts/db_backup.sh</code>. The configuration uses the local Bitnami master <code>root</code> administrative access profile to ensure complete structural schemas and transactional privileges are extracted cleanly.</p>

    <h3>Required Execution Flags</h3>
    <pre>sudo chmod +x /home/bitnami/scripts/db_backup.sh</pre>

    <h3>Production Bash Code Template</h3>
    <pre>#!/bin/bash
set -e

# ==========================================
# CONFIGURATION PROFILE
# ==========================================
DB_USER="root"                                # Master Bitnami DB User Profile
DB_PASS="YOUR_BITNAMI_ROOT_PASSWORD"          # Located via /home/bitnami/bitnami_credentials
DB_NAME="YOUR_TARGET_DATABASE_NAME"
ENC_KEY="YOUR_SECURE_GPG_PASSPHRASE"         # Symmetric Key Used for AES-256 Locking
STORAGE_SA="YOUR_AZURE_STORAGE_ACCOUNT_NAME"
CONTAINER="YOUR_BLOB_CONTAINER_NAME"

# ==========================================
# AUTOMATED WORKFLOW SCHEDULER BLOCK
# ==========================================
DATE=$(date +%Y-%m-%d_%H%M%S)
SQL_FILE="/tmp/${DB_NAME}-${DATE}.sql"
ENC_FILE="${SQL_FILE}.gpg"
BLOB_NAME="${DB_NAME}-${DATE}.sql.gpg"

echo "Step 1/5: Extracting structural database dump via mysqldump..."
mysqldump -u "$DB_USER" -p"$DB_PASS" "$DB_NAME" > "$SQL_FILE"

echo "Step 2/5: Compiling cryptographic GPG AES-256 envelope..."
echo "$ENC_KEY" | gpg --batch --yes --passphrase-fd 0 --symmetric --cipher-algo AES256 -o "$ENC_FILE" "$SQL_FILE"

echo "Step 3/5: Asserting instance cloud identity via Azure Managed Identity..."
/usr/bin/az login --identity

echo "Step 4/5: Transporting encrypted payload to Azure Blob Storage Container..."
/usr/bin/az storage blob upload \
    --account-name "$STORAGE_SA" \
    --container-name "$CONTAINER" \
    --name "$BLOB_NAME" \
    --file "$ENC_FILE" \
    --auth-mode login

echo "Step 5/5: Executing secure filesystem cleaning of local volatile workspace..."
rm -f "$SQL_FILE"
rm -f "$ENC_FILE"

echo "SYSTEM MESSAGE: Automated Backup Flow Completed. Target Resource: ${BLOB_NAME}"</pre>

    <h2>4. System Scheduler Synchronization (Cron Environment)</h2>
    <p>Automation tasks execute via the background <code>cron</code> engine under the local <code>bitnami</code> session structure. The configurations are parsed line-by-line using precise scheduling matrices.</p>

    <h3>Active Cron Job Rule</h3>
    <p>Inspect the system table entries by using: <code>crontab -l</code>. The tracking entry is defined as follows:</p>
    <pre>0 0 * * * /bin/bash /home/bitnami/scripts/db_backup.sh >> /home/bitnami/scripts/backup.log 2>&1</pre>

    <table class="table-custom">
        <thead>
            <tr>
                <th>Cron Parameter</th>
                <th>Assigned Value</th>
                <th>Behavioral Definition</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td><code>0</code></td>
                <td>Minute</td>
                <td>Triggers exactly on the top of the hour.</td>
            </tr>
            <tr>
                <td><code>0</code></td>
                <td>Hour</td>
                <td>Triggers exactly at midnight (00:00).</td>
            </tr>
            <tr>
                <td><code>* * *</code></td>
                <td>Day / Month / Weekday</td>
                <td>Triggers every single calendar day perpetually.</td>
            </tr>
            <tr>
                <td><code>&gt;&gt; ... 2&gt;&amp;1</code></td>
                <td>I/O Redirection</td>
                <td>Pipes standard outputs and errors into <code>backup.log</code>.</td>
            </tr>
        </tbody>
    </table>

    <div class="alert-warning">
        <p><strong>Critical Operational Instruction:</strong> The Linux cron manager strictly requires a trailing newline character. Ensure there is a single completely empty blank line at the bottom of the crontab configuration file (press Enter at the end of the script line inside <code>crontab -e</code>). Failure to include this trailing newline causes the engine to ignore the script entirely.</p>
    </div>

    <h3>Timezone Mapping Metrics</h3>
    <p>The host server's operating clock runs natively on <strong>Coordinated Universal Time (UTC)</strong>. All crontab execution timings align with this standard:</p>
    <ul>
        <li><strong>Server Execution Target:</strong> <code>00:00 UTC</code></li>
        <li><strong>India Standard Time Equivalent:</strong> <code>05:30 AM IST</code> every morning.</li>
    </ul>

    <h2>5. Disaster Recovery & Decryption Manual</h2>
    <p>In the event of database degradation, corruption, or audit requests, follow this technical restoration sequence exactly to download, translate, and re-import data profiles.</p>

    <h3>Step 1: Download the Target Object Package from Azure Blob</h3>
    <p>Log in using the server's native Azure managed identity profile and retrieve the precise file object from your storage container down into the temporary scratch workspace:</p>
    <pre>az login --identity

az storage blob download \
    --account-name "YOUR_STORAGE_ACCOUNT_NAME" \
    --container-name "YOUR_BLOB_CONTAINER_NAME" \
    --name "YOUR_BACKUP_FILE_NAME.sql.gpg" \
    --file "/tmp/backup_encrypted.sql.gpg" \
    --auth-mode login</pre>

    <h3>Step 2: Decrypt the Secure GPG Binary Envelope</h3>
    <p>Execute the decryption command string. The terminal will explicitly request the entry of your structural passphrase credential key (the value defined in your script's <code>ENC_KEY</code> variable):</p>
    <pre>gpg -d -o /tmp/restored_database.sql /tmp/backup_encrypted.sql.gpg</pre>
    <p>Upon input validation, GPG processes the payload and outputs a clean, standardized, plain-text <code>.sql</code> data migration document into your <code>/tmp</code> directory.</p>

    <h3>Step 3: Database Restoration and Schema Injection</h3>
    <p>Inject the unencrypted schema text directly back into your production target database database environment:</p>
    <pre>mysql -u root -p YOUR_DB_NAME &lt; /tmp/restored_database.sql</pre>

    <h3>Step 4: Secure Clean Up of Temporary Files</h3>
    <p>To ensure high compliance standards, permanently eliminate all unencrypted residual assets from the system storage immediately after verification:</p>
    <pre>rm -f /tmp/restored_database.sql
rm -f /tmp/backup_encrypted.sql.gpg</pre>

    <div class="alert-card">
        <p><strong>Storage Optimization Note:</strong> Cloud infrastructure retention rules are managed completely automatically via the Azure Lifecycle Management Policy. Blobs modified more than 30 days ago are scrubbed by the platform every 24 hours at zero operational cost, preventing storage overflow.</p>
    </div>

</body>
</html>
"""

# Compile revised version HTML to PDF
input_html_path_v2 = "/tmp/backup_documentation_v2.html"
output_pdf_path_v2 = "/tmp/automated_backup_sop_v2.pdf"

with open(input_html_path_v2, "w") as f:
    f.write(html_content_v2)

HTML(filename=input_html_path_v2).write_pdf(output_pdf_path_v2)
print("PDF Version 2 successfully generated.")# Magnifybackup
