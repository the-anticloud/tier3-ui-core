# L5 Narrow / L2 General Classification — ui-core
**Platform:** Anticloud | **PAX:** 27B | **IP:** USPTO pending 2026, Anticloud FZ LLE
**Domain:** Sovereign UI component library: design system for all Anticloud web interfaces

## L5 Narrow
ui-core specializes in sovereign ui component library: design system for all anticloud web interfaces within the Anticloud sovereign deployment boundary. All operations stay local — no cloud services, no external APIs, no data exfiltration. The narrow scope ensures deterministic, auditable behavior that PAX 27B can reason about precisely.

## L2 General
L2 General means ui-core is available to all 9 Anticloud tiers without per-tier configuration. The same API serves hospital, defense, robotics, and research deployments.

## PAX Integration
PAX 27B generates UI components from natural language: 'Create a real-time AIOSS chain visualizer component' produces a React component with correct TypeScript types.

## AIOSS Audit Relevance
Every UI interaction event (component + action + session hash) is AIOSS-chained: H_n = SHA3-256(H_{n-1} || entry_hash_n || timestamp_n).
Tamper-evident, offline-verifiable, zero cloud dependency.

## Regulatory / Compliance
WCAG 2.1 AA (accessibility), ISO 9241-210 (human-centred design)
