# Autonomous Threat Record Lifecycle

This guide summarizes a threat-record workflow for moving from manual auditing to
machine-led vulnerability mitigation across distributed software and hardware
ecosystems.

## Purpose

A threat record should be treated as a living intelligence asset rather than a
static ticket. Each record starts with a verifiable discovery, then accumulates
standardized metadata, severity context, root-cause analysis, and remediation
state so automated systems can decide when software or infrastructure is exposed
and when it has been repaired.

## Lifecycle stages

1. **Foundational report.** Capture the authoritative vulnerability statement,
   affected product, impacted versions, and references. Keep this layer concise
   so it remains a stable source of truth for later enrichment.
1. **Data enrichment.** Add normalized severity, exploitability, operational
   exposure, and root-cause information. This turns a notification into a
   prioritizable security decision.
1. **Unified taxonomy.** Classify the flaw by weakness, cause, danger, and
   technology location. Consistent taxonomy makes records comparable across
   ecosystems such as Go, npm, Python, containers, and AI services.
1. **Version history mapping.** Track affected, unaffected, and unknown states
   across both continuous development history and fixed release snapshots.
1. **Automated mitigation loop.** Use the normalized identity and vulnerability
   state to cross-reference registries, triage contextual risk, and initiate
   remediation without waiting for manual audits.

## Metadata model

Threat records intended for autonomous processing should include the following
fields where available:

| Metadata | Description | Automation use |
| --- | --- | --- |
| Software identity | Package, product, component, ecosystem, and version range. | Matches scanned assets to known records. |
| Weakness taxonomy | CWE, vulnerability class, architectural pattern, or exploit primitive. | Groups related flaws and highlights systemic design issues. |
| Severity and exploitability | CVSS or equivalent scoring plus known exploitation status. | Prioritizes queue order and service-level objectives. |
| Root cause | Implementation bug, configuration issue, exposed alternate channel, or architectural weakness. | Distinguishes patchable defects from redesign work. |
| Operational context | Network reachability, authentication requirements, asset criticality, and compensating controls. | Converts generic risk into environment-specific risk. |
| Version state | Affected, unaffected, fixed, and unknown ranges with source references. | Enables safe automated upgrade or rollback decisions. |

## Alternate-channel risk

Unprotected alternate channels are especially important because they can bypass
primary gateways and policy enforcement points. Records for these findings should
call out the alternate path explicitly, such as a management endpoint, debug
interface, hidden socket, mirrored register, shadow register, direct hardware
link, or secondary API path. Naming the bypass path helps reviewers identify
whether compensating controls protect only the primary channel or the complete
attack surface.

## Linear and snapshot history

Automated remediation depends on precise version semantics:

* **Linear history** records the continuous development timeline, including when
  a flaw was introduced, fixed, regressed, or backported.
* **Snapshot history** records discrete release artifacts and whether each
  artifact is affected, unaffected, or unknown.

Maintaining both views lets scanners reason about source branches and deployed
artifacts without assuming that every branch receives fixes in the same order.

## Mitigation loop checklist

Use this checklist when adding or enriching a record:

- [ ] Establish a normalized software identity.
- [ ] Cross-reference authoritative vulnerability registries and vendor
      advisories.
- [ ] Classify the weakness and root cause with shared taxonomy.
- [ ] Map affected, unaffected, and unknown version ranges.
- [ ] Add severity, exploitability, and operational exposure context.
- [ ] Define the recommended remediation or compensating control.
- [ ] Confirm the record has enough structure for automated triage and repair.

## Outcome

A complete threat record gives security teams and scanners a common language for
understanding what is vulnerable, why it is vulnerable, where it appears in the
software supply chain, and which remediation action should be taken. This is the
foundation for an autonomous defensive loop that continuously detects, prioritizes,
and repairs vulnerabilities across modern infrastructure.
