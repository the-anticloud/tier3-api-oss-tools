# L5 Narrow / L2 General Classification — api-oss-tools
**Platform:** Anticloud | **PAX:** 27B | **IP:** USPTO pending 2026, Anticloud FZ LLE
**Domain:** Sovereign CLI toolbox: utilities for AIOSS chain management, PAX model ops, benchmarking

## L5 Narrow
api-oss-tools specializes in sovereign cli toolbox: utilities for aioss chain management, pax model ops, benchmarking within the Anticloud sovereign deployment boundary. All operations stay local — no cloud services, no external APIs, no data exfiltration. The narrow scope ensures deterministic, auditable behavior that PAX 27B can reason about precisely.

## L2 General
L2 General means api-oss-tools is available to all 9 Anticloud tiers without per-tier configuration. The same API serves hospital, defense, robotics, and research deployments.

## PAX Integration
PAX 27B is available as a tool subcommand: `anticloud tool pax --prompt '...' --max-tokens 256`

## AIOSS Audit Relevance
Every tool invocation (command hash + args hash + output hash + exit code) is AIOSS-chained: H_n = SHA3-256(H_{n-1} || entry_hash_n || timestamp_n).
Tamper-evident, offline-verifiable, zero cloud dependency.

## Regulatory / Compliance
NIST SSDF (operational tooling), ISO 25010 (usability)
