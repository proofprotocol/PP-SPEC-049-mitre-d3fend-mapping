# PP-SPEC-049: Proof of Efficacy Mapping to MITRE D3FEND™

| Field | Value |
|---|---|
| Status | DRAFT v0.1 |
| Author | Craig Ellrod, Nebulonium, Inc. (dba HACKERverse®) |
| Date | October 8, 2026 |
| License | CC BY 4.0 |
| Maps to | MITRE D3FEND™ (mapped against D3FEND 1.6.0) |
| Series | Proof Protocol Framework Mapping Specifications |

---

## 1. Purpose

This specification defines how MITRE D3FEND™ defensive tactics, defensive techniques, digital artifacts, and D3FEND relationships to offensive techniques can be bound to Proof Protocol control descriptors, test cases, evidence, and efficacy results.

D3FEND remains authoritative for its own terminology, identifiers, ontology, and architecture. This document defines a **Proof Protocol mapping** and does not supersede or modify D3FEND.

## 2. Scope

D3FEND is a knowledge graph of cybersecurity countermeasures maintained by The MITRE Corporation and funded by the National Security Agency (NSA) Cybersecurity Directorate. As of October 2026 the D3FEND website identifies the current release as D3FEND 1.6.0. D3FEND organizes defensive techniques under the tactics Model, Harden, Detect, Isolate, Deceive, Evict, and Restore, relates defensive techniques to digital artifacts, and relates those artifacts to offensive techniques drawn from MITRE ATT&CK® and other catalogs.

Unlike a threat framework, D3FEND describes defensive capability. It supplies a vocabulary for **what a control claims to do**. Proof Protocol supplies an independent evidence model for determining whether that control actually did it under adversarial conditions.

Independent witnessing and evidence-capture implementation are defined elsewhere in the Proof Protocol specification family.

## 3. Core Question

Proof of efficacy asks:

> **Was there a control, and did it work?**

A D3FEND defensive technique describes a class of countermeasure. A product or configuration may claim to implement that technique against a given offensive behavior. Proof Protocol binds the D3FEND technique, the targeted digital artifact, the offensive test case, the control, observed behavior, downstream outcome, and evidence into a result that can be independently examined.

## 4. Metric Definitions

Against a defined adversarial corpus, each case is recorded as **blocked**, **detected**, **missed**, or **INVALID**.

Relevant measurements include:

- containment rate;
- detection rate;
- miss rate;
- false-positive rate against paired benign cases;
- robustness against variants, bypass, suppression, manipulation, or evasion of the claimed defensive technique;
- version-level results; and
- INVALID status when required evidence is incomplete or broken.

Target levels are engagement- and risk-specific rather than imposed by this mapping.

## 5. Evidence Produced

Mapped tests can produce:

- **Proof records** binding D3FEND technique, digital artifact, and offensive-technique context, test case, control, system/version, verdict, timestamp, and evidence references;
- **ProofStamp™** trusted timestamps bound to evidence/verdict objects;
- **ProofBundle™** packages containing proof records, metrics, corpus manifests, and environment/context;
- **ProofRegister™** records for issued proof artifacts; and
- corpus and environment manifests identifying the tested adversarial conditions.

## 6. Mapping to MITRE D3FEND™

D3FEND identifiers SHOULD be recorded exactly as published in the D3FEND release being mapped (for example D3-FH for a defensive technique, or the corresponding d3f: ontology term), together with the D3FEND version. This specification does not redefine D3FEND classes, techniques, or artifacts.

| MITRE D3FEND™ context | Proof Protocol treatment | Evidence |
|---|---|---|
| Defensive tactic (Model, Harden, Detect, Isolate, Deceive, Evict, Restore) | Classify the control claim by the defensive objective it asserts. | Control descriptor |
| Defensive technique (D3-...) | Bind the D3FEND technique identifier to the control claim under test. | Control descriptor; proof record |
| Ontology term (d3f:...) | Record the machine-readable term where implementations exchange ontology data. | Corpus/test metadata |
| Digital artifact | Identify the artifact the control observes or acts on and the artifact the adversarial test targets. | Environment descriptor; target evidence |
| Artifact relationship | Use the relationship to select where outcome evidence MUST be collected. | Target/outcome evidence |
| Related offensive technique (ATT&CK or other catalog) | Select independently authored adversarial test cases that exercise the offensive behavior the defense claims to counter. | Corpus manifest |
| Defensive technique execution | Capture evidence that the claimed countermeasure was present, configured, and active during the test. | Control state evidence |
| Detection outcome (Detect tactic) | Record whether the control identified the exercised condition. | Detection result |
| Hardening, isolation, or eviction outcome | Determine whether the adversarial objective reached the protected artifact or target. | Target/outcome evidence |
| Deception outcome (Deceive tactic) | Record whether the adversary interacted with the decoy and whether that interaction was detected. | Execution and detection evidence |
| Restore outcome | Record whether the protected artifact or service was returned to the asserted state. | Recovery evidence |
| System/version context | Bind D3FEND version and material control, policy, sensor, and environment versions to the result. | Environment descriptor |

## 7. Interoperability Rules

1. The D3FEND version, defensive tactic, defensive technique, and digital artifact SHOULD be recorded when applicable.
2. D3FEND identifiers, names, and terminology MUST NOT be silently redefined.
3. Proof Protocol verdicts are Proof Protocol results; they are not MITRE scores, certifications, or endorsements.
4. A control's presence, configuration, activation, and efficacy are distinct facts.
5. A policy decision, alert, or control trigger does not by itself establish efficacy when the claim concerns a downstream protected outcome.
6. Target, application, tool, SIEM, vendor, or equivalent evidence SHOULD complete the evidence round trip when required to establish the result.
7. Missing required evidence MUST yield **INVALID**, not PASS.
8. Material changes to the tested system, model, policy, tools, permissions, control, environment, D3FEND mapping, or corpus SHOULD trigger retesting where they can affect the result.
9. A D3FEND relationship between a defensive technique and an offensive technique describes a possible countermeasure. It MUST NOT be treated as evidence that a control counters that offensive technique. D3FEND itself labels some offensive-technique mappings as inferred and experimental.
10. Implementing or claiming a D3FEND technique is a control claim, not an efficacy result.

## 8. Framework-Agnostic Architecture

> **Threat frameworks are pluggable inputs to Proof Protocol. Proof Protocol is framework-agnostic.**

External frameworks can identify **what to test**: threats, vulnerabilities, techniques, risk categories, controls, design assertions, identity claims, tool permissions, or other risk conditions. Proof Protocol independently establishes **whether the control worked and what evidence proves that result**.

No external framework is required for Proof Protocol to operate. A Proof Protocol implementation MAY use MITRE D3FEND™, MITRE ATT&CK®, MITRE ATLAS, CSA MAESTRO, OWASP, AIVSS, AAGATE, a proprietary threat model, another recognized framework, or no external framework at all when the test condition is otherwise sufficiently defined.

Adding, replacing, muting, or removing a framework mapping does not alter the Proof Protocol architecture, evidence model, Proof of Efficacy determination, ProofBundle™, ProofStamp™, ProofRegister™, or independent corroboration requirements.

A framework mapping therefore establishes **interoperability**, not architectural dependency.

## 9. Relationship to Proof Protocol

This mapping is part of the Proof Protocol specification family maintained by Nebulonium, Inc.

The relationship is intentionally asymmetric:

> **MITRE D3FEND™ supplies defensive technique and digital artifact context describing what a control claims to do. Proof Protocol supplies the evidence model for determining whether that control performed as claimed.**

No affiliation, endorsement, certification, or sponsorship by MITRE or the National Security Agency is implied.

## 10. Source Framework, Attribution, and License

MITRE D3FEND™ is external work maintained by The MITRE Corporation, funded by the NSA Cybersecurity Directorate, and managed by the National Security Engineering Center (NSEC), which is operated by MITRE. MITRE names, D3FEND names, identifiers, trademarks, and expressive framework content remain subject to MITRE's applicable terms. D3FEND was produced for the U.S. Government under contract and is subject to the DFARS noncommercial software rights clause noted on the D3FEND website.

The D3FEND Terms of Use (https://d3fend.mitre.org/tou) grant a non-exclusive, royalty-free license to use D3FEND for research, development, and commercial purposes. Any copy made for such purposes is authorized provided that MITRE's copyright designation and the license are reproduced in that copy. The D3FEND ontology source repository (github.com/d3fend/d3fend-ontology) is distributed under the MIT License. D3FEND pages also reference MITRE ATT&CK®, MITRE ATLAS, and Aerospace SPARTA content, each subject to its own terms.

This Proof Protocol mapping is independently authored and Licensed under the Greater Good Commercial License 1.0 (see LICENSE.md); text CC BY 4.0 under its Part S. Original inventor: Craig Thomas Ellrod (ORCID 0009-0004-1058-7666).

### Required attribution

The D3FEND Terms of Use (https://d3fend.mitre.org/tou) require reproduction of MITRE's copyright designation, which they give verbatim as:

> © 2025 The MITRE Corporation. Approved for Public Release; Distribution Unlimited #20-2338 and #23-1207.

The D3FEND website carries the following trademark statement, quoted verbatim:

> MITRE D3FEND; and the MITRE D3FEND logo are trademarks of The MITRE Corporation.

Because this specification also references ATT&CK identifiers, the ATT&CK trademark statement applies (https://attack.mitre.org/resources/legal-and-branding/terms-of-use/):

> MITRE ATT&CK and ATT&CK are registered trademarks of The MITRE Corporation.

Source cited: MITRE D3FEND™, version 1.6.0, https://d3fend.mitre.org/.

This specification reproduces only D3FEND tactic names, identifier formats, structural terms, and short factual statements about D3FEND. It does not reproduce D3FEND technique definitions, ontology content, artifact definitions, or relationship data. The copyright designation and trademark statements above are nonetheless carried in this specification, the README, and the LICENSE file. Implementations that include D3FEND content in a ProofBundle™ or corpus manifest MUST reproduce MITRE's copyright designation and license with that content as the Terms of Use require.

## 11. Versioning

This mapping is versioned independently of MITRE D3FEND™. This version was prepared against D3FEND 1.6.0. Each ProofBundle™ SHOULD record the D3FEND version used. Material upstream changes, including changes to tactics, techniques, artifacts, or offensive-technique relationships, SHOULD trigger a mapping review and, where necessary, a new version identifying the D3FEND release mapped.

---

*Proof Protocol · proofprotocol.io · CC BY 4.0*
