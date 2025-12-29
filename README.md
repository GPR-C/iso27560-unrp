# ISO/IEC 27560-1 Universal Notice Receipt Profile

**International Standard for Transparency in Consent and Data Processing**

---

## What is the Universal Notice Receipt Profile?

The **ISO/IEC 27560-1 Universal Notice Receipt Profile** operationalizes Convention 108+ transparency requirements as deployable infrastructure. It provides standardized mechanisms for controller identification and bilateral proof-of-notice **before** personal data processing begins.

**Core Components**:

- **Controller Identification Records (CIRs)**: Machine-readable controller identity and processing claims discoverable at `/.well-known/notice.txt` before processing, for example '/transparency/notice.txt`
- **Anchored Notice & Consent Receipts (ANCR/MVCR)**: Cryptographically verifiable bilateral records synchronized between controller and individual
- **Notice Event Logs**: Immutable audit trails tracking all transparency state changes across processing contexts
- **Four TATA Levels**: Transparency and Trust Assurance levels (L1 self-assertion → L4 high-assurance active state) enabling proportional deployment

**Architectural Principle**: **Controller-ID First** — controller identification disclosed before any device identifiers or personal data collection, inverting surveillance-by-default architecture.

---

## Why It Matters

### Regulatory Capacity Infrastructure

ISO/IEC 27560-1 provides **enforcement infrastructure at scale** for privacy regulators:

- **Discoverable compliance**: Regulators can verify controller claims via public CIR registries without prior surveillance
- **Automated monitoring**: Notice event logs enable algorithmic detection of material changes, consent invalidation, or unlawful processing
- **Cross-border coordination**: Standardized transparency records enable "Commonwealth Effect" — coordinated enforcement across jurisdictions
- **Reduced administrative burden**: Controllers maintain one set of transparency records consumable by multiple regulators

### Privacy-Enabling Control

This is **privacy-enabling data control**, not privacy-preserving data protection:

- **Individual agency**: Individuals control which controllers they choose to trust through verifiable CIRs, without corporate identification requirements
- **Consent by default with 2FN**: PII Principal as Master Controller — individual self-identifies and binds identity to chosen CIRs (surveillance inversion)
- **Glass-box transparency**: Real-time visibility into processing activities through notice event logs and active state signaling
- **Portable consent**: ANCR receipts enable consent portability across services without vendor lock-in

**Key Distinction**: Controllers using individual data (service uses consent); individuals NOT "users" of services that process their data.

---

## Quick Start for Implementers

### Level 1 (Self-Assertion) — Minimal Deployment

**Goal**: Publish basic controller transparency

1. **Create Controller Identification Record** at `/.well-known/notice.txt`:
    - controller_name, controller_id (UUID or registered identifier)
    - contact_info (privacy officer email/URL)
    - lawful_basis (consent, contract, legitimate_interest, etc.)
    - processing_purposes, data_categories, retention_period
2. **Initialize Notice Event Log**: Start logging notice_issued events
3. **Deploy in services**: Reference CIR in privacy notices, cookie banners, APIs

**Outcome**: Discoverable baseline transparency with no third-party dependencies

### Level 2 (Registered Controller) — Registry Integration

**Goal**: Verifiable controller registration

1. Register controller with authorized registry (e.g., ICO Controller Registry, GDTA registry)
2. Obtain registered controller_id and embed in CIR
3. Enable optional notice receipts with registry timestamp

**Outcome**: Registrar-verified controller identity, foundation for ANCR

### Level 3 (ANCR) — Cryptographic Receipts

**Goal**: Bilateral proof-of-notice with cryptographic integrity

1. Implement ANCR issuance: Generate receipt with controller signature, blind data-notary timestamp
2. Provide receipt to individual (JSON/JWT format) and store controller copy
3. Enable receipt verification API for individuals and regulators
4. Update notice event log with consent_granted, receipt_issued events

**Outcome**: Tamper-evident consent records, portable across services

### Level 4 (Active State High Assurance) — Real-Time Control

**Goal**: Real-time transparency and control with high-assurance identity

1. Deploy certified DTTO (Digital Transparency Trust Operator) notarization
2. Enable active state signaling for real-time access/revocation
3. Implement liveliness assurance (face-to-face or equivalent)
4. Provide real-time notice event log access to individuals

**Outcome**: High-assurance environments (e.g., age assurance, national ID, AI governance)

---

## Specification Documents

### Normative References

- **ISO/IEC 27560:2025-1** (v1.01 Profile Specification): Draft specification (publication pending Q2 2026)
- **Council of Europe Convention 108+**: Articles 5, 8, 11, 14 (normative framework) - [Official text](https://rm.coe.int/convention-108-convention-for-the-protection-of-individuals-with-regar/16808b36f1)
- **ISO/IEC TS 27560:2023**: Published standard - [ISO catalogue](https://www.iso.org/standard/80392.html) (freely available)
- **DPCat Specification**: Interoperable cataloging for Controller Identification Records (specification in development)
- **W3C Data Privacy Vocabulary (DPV)**: [w3id.org/dpv](http://w3id.org/dpv) (semantic interoperability)
- **Convention 108+ DPV Extension**: W3C extension proposal (Q1 2026 submission)

### Implementation Guides

- **Controller Identification Record Schema**: JSON schema and examples (see specification §4.2)
- **Notice Event Log Format**: Event types, required fields, retention rules (see specification §4.4)
- **ANCR/MVCR Receipt Structure**: Signature methods, timestamp protocols (see specification §5.3)
- **TATA Level Selection Guide**: Risk-proportional transparency deployment (see specification §3.2)

### Related Standards

- **ISO/IEC 27566-1**: Age assurance frameworks - [ISO catalogue](https://www.iso.org/standard/72168.html)
- **ISO/IEC 29184:2020**: Online privacy notices - [ISO catalogue](https://www.iso.org/standard/70331.html)
- **ISO/IEC 29100:2011**: Privacy framework - [Free access](https://standards.iso.org/ittf/PubliclyAvailableStandards/)
- **ISO/IEC 27018**: PII protection in public clouds - [ISO catalogue](https://www.iso.org/standard/76559.html)

---

## Project Status

**Current Version**: ISO/IEC 27560:2025 v1.0 submission

**Development Phase**: Public comment and pilot deployment

**Submission Timeline**:

- ✅ **v1.0 Specification Complete** (December 2025)
- 🔄 **Public Review Period** (Q1 2026)
- 🔄 **Pilot Deployments  **:
    - 
- ⏳ **ISO/IEC JTC 1/SC 27/WG 5 Review** (Q2 2026)
- ⏳ **v1.1 Revision** (based on pilot feedback, Q3 2026)

**Implementation Status**:

- **CIR Reference Implementation**: GitLab repository (this repo)
- **Notice Event Log Library**: Python, JavaScript libraries (in development)
- **ANCR Validation Tools**: Receipt verification API and CLI tools (planned Q1 2026)
- **DPCat Integration**: Convention 108+ DPV extension for catalog interoperability

**Coordination Initiatives**:

- **Global Digital Transparency Alliance (GDTA)**: Regulatory capacity research and co-regulatory infrastructure (decision Feb 2, 2026)
- **Commonwealth Privacy Regulators**: Coordinated adoption for "Commonwealth Effect" enforcement
- **W3C DPVCG Engagement**: Convention 108+ DPV extension submission (Q1 2026)

---

## License

**RF-RAND IPR License** (Royalty-Free, Reasonable and Non-Discriminatory)

This profile is developed as open infrastructure for regulatory capacity. Implementers may use, modify, and deploy without licensing fees.

---

## Contributing

Contributions welcome via GitLab issues and merge requests.

**Key Areas for Contribution**:

- Reference implementations (libraries, APIs)
- Deployment case studies and pilot results
- Interoperability testing with existing privacy frameworks
- Translation and localization

**Contact**:

- **Profile Editor**: Mark Lizar, ISO/IEC 27560-1 Profile Editor
- **Organization**: Digital Transparency Lab
- **Email**: [mark@transparencylab.ca](mailto:mark@transparencylab.ca)

---

## Additional Resources

### GDTA Resources

- **GDTA Website**: [gdtagroup.org](http://gdtagroup.org) - [gdta.online](http://gdta.online) Global Digital Transparency Alliance - Forum
- **Founding Inquiries**: [founding@gdtagroup.org](mailto:founding@gdtagroup.org)

### Related Standards Bodies

- **ISO/IEC JTC 1/SC 27/WG 5**: Privacy technologies working group - [ISO Committee](https://www.iso.org/committee/45306.html)
- **W3C DPVCG**: Data Privacy Vocabularies and Controls Community Group - [W3C page](https://www.w3.org/community/dpvcg/)
- **Kantara Initiative**: Consent receipt specifications - [Kantara](https://kantarainitiative.org)

### Convention 108+ Framework

- **Convention 108+ Treaty**: [Council of Europe](https://rm.coe.int/convention-108-convention-for-the-protection-of-individuals-with-regar/16808b36f1)
- **Ratification status**: 55+ jurisdictions - [Treaty status](https://www.coe.int/en/web/conventions/full-list)
- **EU Regulation 2018/1725**: Operational model for institutional transparency - [EUR-Lex](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX:32018R1725)

---

**Last Updated**: December 29, 2025
