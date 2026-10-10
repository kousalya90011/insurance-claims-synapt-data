# Insurance Claims Synapt Dossiers Dataset

A benchmark dataset of **10,000 structured, relationship-aware insurance claim dossiers** optimized for **Synapt AI document ingestion**, entity extraction, and knowledge-graph relationship traversal.

## Dataset Highlights
- **Total Dossiers**: 10,000 structured text dossiers (`.txt`) organized across 10 manageable batches of 1,000 claims each.
- **Lines of Business**: Auto, Property, Home, Renters, Business.
- **Adjudication Outcomes**: Approved, Denied, Pending, Under Review.
- **Purity & Privacy**: Strictly excludes ground-truth target leakage (`is_fraud_flagged_ground_truth`) and contains zero personal PII (SSNs, phone numbers, personal email addresses).
- **Synapt Ingestion Optimization**: Utilizes consistent surrogate business identifiers (`CLM-C00000xxxxx`) to avoid false telephone classification by automated PII scrubbers while preserving 100% graph relationship topology.

## Directory Structure
```
dossiers/
├── batch_01_claims_0000000000_0000000999/ (1,000 dossiers: CLM-C000000000.txt to CLM-C000000999.txt)
├── batch_02_claims_0000001000_0000001999/ (1,000 dossiers: CLM-C000001000.txt to CLM-C000001999.txt)
├── batch_03_claims_0000002000_0000002999/ (1,000 dossiers: CLM-C000002000.txt to CLM-C000002999.txt)
├── batch_04_claims_0000003000_0000003999/ (1,000 dossiers: CLM-C000003000.txt to CLM-C000003999.txt)
├── batch_05_claims_0000004000_0000004999/ (1,000 dossiers: CLM-C000004000.txt to CLM-C000004999.txt)
├── batch_06_claims_0000005000_0000005999/ (1,000 dossiers: CLM-C000005000.txt to CLM-C000005999.txt)
├── batch_07_claims_0000006000_0000006999/ (1,000 dossiers: CLM-C000006000.txt to CLM-C000006999.txt)
├── batch_08_claims_0000007000_0000007999/ (1,000 dossiers: CLM-C000007000.txt to CLM-C000007999.txt)
├── batch_09_claims_0000008000_0000008999/ (1,000 dossiers: CLM-C000008000.txt to CLM-C000008999.txt)
└── batch_10_claims_0000009000_0000009999/ (1,000 dossiers: CLM-C000009000.txt to CLM-C000009999.txt)
```

## Canonical Dossier Schema
Each claim dossier contains authoritative metadata followed by explicit entity-relationship assertions for automated graph extraction:

```text
CLAIM DOSSIER
Claim ID: CLM-C000004314
Policy ID: POL-16283089
Claim Type: Property
State: TX
Policyholder Tenure: 14.8 years
Previous Claims: 0
Incident Date: 2024-08-16
Claim Filed Date: 2024-09-20
Claim Amount: $7,878.91
Deductible: $500.00
Claim Status: Under Review
Resolution Time: Unresolved / Pending
Claim Narrative: Claim CLM-C000004314 for property policy in TX...

RELATIONSHIPS
- Claim CLM-C000004314 is covered by Policy POL-16283089.
- Claim CLM-C000004314 concerns an incident in TX on 2024-08-16.
- Claim CLM-C000004314 has outcome Under Review.
- Claim CLM-C000004314 has claim type Property.
```

## Knowledge Graph Capabilities
- **Multi-Claim Policy Sharing**: Multiple claims link to identical policy entities (e.g., `CLM-C000004314` and `CLM-C000005902` connect to `POL-16283089`).
- **Graph Traversal**: Enables `trident_traverse` queries to discover historical frequency, sibling loss patterns, and cross-claim policyholder exposure.
