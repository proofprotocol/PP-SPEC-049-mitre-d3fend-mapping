# PP-SPEC-049: Proof of Efficacy Mapping to MITRE D3FEND™

**Status:** DRAFT v0.1  
**Author:** Craig Ellrod / Nebulonium, Inc. / HACKERverse®  
**License:** Greater Good Commercial License 1.0 (GGL-C-1.0); text CC BY-ND 4.0 under Part S. See LICENSE.md.

**Normative specification:** [`PP-SPEC-049-MITRE-D3FEND-Mapping.md`](./PP-SPEC-049-MITRE-D3FEND-Mapping.md)

## Purpose

This repository defines a Proof Protocol mapping between MITRE D3FEND™ and Proof Protocol evidence, efficacy, and proof semantics.

MITRE D3FEND™ (mapped against 1.6.0) is treated as a pluggable source of defensive technique and digital artifact vocabulary describing what a control claims to do. Proof Protocol remains framework-agnostic and independently establishes whether a selected control performed as claimed.

## Repository contents

- `PP-SPEC-049-MITRE-D3FEND-Mapping.md`: normative mapping specification
- `README.md`: repository overview
- `LICENSE`: license for original Proof Protocol material
- `CONTRIBUTING.md`: contribution guidance
- `CITATION.cff`: citation metadata

## Architectural principle

> **Threat frameworks are pluggable inputs to Proof Protocol. Proof Protocol is framework-agnostic.**

External frameworks identify what may be tested. Proof Protocol independently establishes whether a control worked and what evidence proves the result.

## Ownership and external-framework notice

This Proof Protocol mapping is independently authored. MITRE, D3FEND, ATT&CK, associated names, identifiers, trademarks, and upstream materials remain subject to their respective ownership and licensing. Mapping establishes interoperability, not dependency, endorsement, or transfer of ownership. No affiliation, endorsement, certification, or sponsorship by MITRE or the National Security Agency is implied.

Upstream attribution and trademark notice:

© 2025 The MITRE Corporation. Approved for Public Release; Distribution Unlimited #20-2338 and #23-1207.

MITRE D3FEND; and the MITRE D3FEND logo are trademarks of The MITRE Corporation.

MITRE ATT&CK and ATT&CK are registered trademarks of The MITRE Corporation.
