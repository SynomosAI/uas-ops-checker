# uas-ops-checker

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Domain Profile](https://img.shields.io/badge/domain-uas-blue.svg)](domain.manifest.json)
[![Status: RESERVED](https://img.shields.io/badge/status-RESERVED-orange.svg)](domain.manifest.json)
[![MCP Checker](https://img.shields.io/badge/checker-MCP%20tool-8a2be2.svg)](checker.io.json)
[![Privacy by Design](https://img.shields.io/badge/privacy-by--design-2ea44f.svg)](privacy.json)

> **Status: RESERVED (placeholder · open for claiming)** — This repo holds the four-piece industry-access skeleton for the low-altitude UAV operations domain, waiting for a qualified operator to claim and fill in real rules.

We break "can this drone fly here, and how?" into verifiable attributes, so AI only suggests paths and never grants clearance.

**Keywords**: low-altitude flight · UAV operations · drone compliance · domain profile · evidence verification · MCP checker · privacy by design

## Quick Start

This repo is a **domain configuration pack** (not a runnable SDK). Clone it to inspect the four-piece skeleton.

```bash
# 1. Clone
git clone https://github.com/SynomosAI/uas-ops-checker.git
cd uas-ops-checker

# 2. Read the domain manifest (attributes / issuer / red lines)
cat domain.manifest.json

# 3. Read the checker I/O contract (MCP tool schema)
cat checker.io.json
```

```bash
# 4. Read the gate map (action friction levels and blocking rules)
cat gate-map.json

# 5. Read the privacy statement (default-off / minimal / withdrawable / erasable)
cat privacy.json
```

## What this domain covers

Aircraft classification and operational compliance routing.

Low-altitude flight involves airspace control, real-name registration, remote-pilot certification, liability insurance, and other requirements that change frequently. AI can lay out which path to take and which artifacts are missing; the clearance authority always stays with the regulator.

## Domain identity

| Item | Value |
|---|---|
| Domain ID | `uas` (globally unique, never reused) |
| Domain name | Low-altitude · Unmanned Aircraft System Operations |
| Profile version | `domain/1.0` |
| Current status | `RESERVED` |
| Reserved since | 2026-09-12 |

## Attribute list

| Attribute key | Type | Description |
|---|---|---|
| `uas.aircraft_class` | enum | Weight/performance class per UAV regs · micro/light/small/medium/large |
| `uas.registration_status` | enum | Real-name registration · registered/unregistered/exempt |
| `uas.operator_cert` | enum | Pilot certification and validity · none/training/certified/suspended/revoked |
| `uas.flight_zone` | enum | Intended airspace class (per regulator's live notice) · open/controlled/restricted/prohibited |
| `uas.liability_insurance` | enum | Third-party liability insurance · insured/uninsured/not_required |

## Red lines (machine-readable)

1. No clearance-type wording in prohibited or controlled airspace.
2. No "flyable" conclusion without registration or with expired pilot certification.
3. No airworthiness conclusions; airspace status follows the regulator's live notice only.

> Each red line has a matching blocking rule in `gate-map.json`. The platform validator checks "every red line is covered by a rule" — missing coverage fails validation.

## How to claim

This domain is open to qualified organizations. After claiming:

1. Fork this repo and fill in `operator` and `checker_endpoint`.
2. Calibrate attribute values and red-line wording against current rules.
3. Run the platform-side self-check (all five criteria must pass).
4. Open a PR with qualification evidence and rule references.

## License

Code and configuration are under MIT. Prose content copyrights belong to SynomosAI.

© 2026 SynomosAI. All rights reserved.
