# TrackGuard

## AI-enabled evidence and opportunity intelligence for the creative economy

TrackGuard explores how fragmented public signals around entertainment content can be converted into reviewed evidence, creator intelligence and decision support.

The initial product focus is independent music, where evidence of real-world attention can be scattered across video platforms, radio and DJ circulation, playlists, charts, press, event references and other public sources.

Rather than treating every mention or view as proof of demand, TrackGuard is designed to collect candidate evidence, classify what that evidence appears to mean, preserve its provenance and place it behind a human review gate before it is used downstream.

## The Problem

Creators can see views, mentions, playlist placements and other activity around their work, but those signals are fragmented across platforms and often difficult to interpret.

At the same time, venues, promoters, labels and other industry participants need more credible evidence before making decisions about promotion, booking, partnerships or investment.

The core problem is therefore not simply finding attention.

It is determining:

- whether the signal actually relates to the correct content
- what type of evidence it represents
- whether it suggests demand, simple presence or catalogue activity
- where the evidence came from
- how strong or reliable the evidence appears to be
- whether a human has reviewed it
- what action the evidence may reasonably support

## Product Objective

TrackGuard is designed to create an evidence-to-action workflow:

```text
Content Identity
      ↓
Public Signal Discovery
      ↓
Candidate Evidence
      ↓
Normalization & Deduplication
      ↓
AI Classification
      ↓
Evidence & Provenance
      ↓
Human Review
      ↓
Approved Evidence
      ↓
Recommendations / Reports
      ↓
Decision Support

```
The long-term concept is broader than music: a reusable evidence and opportunity layer for entertainment and creator ecosystems.


## Current Architecture

The current prototype uses a multi-source retrieval model.

```
Artist + Track Identity
        ↓
Bubble Backend Orchestration
        ↓
General Web Retrieval + Native Video Retrieval
        ↓
Candidate Evidence Pool
        ↓
Normalize / Deduplicate
        ↓
Structured AI Classification
        ↓
Provenance + Evidence Context
        ↓
Pending Human Review
        ↓
Approve / Reject / Correct
        ↓
Reports / Recommendations / Proof

```
The retrieval paths are intentionally separated because live testing showed that one provider could not reliably provide complete coverage across source types.

The system therefore merges results into a shared candidate pool, removes duplicates while preserving provenance, and sends only the supplied evidence into structured AI classification.

The classifier does not perform new search. Retrieval and interpretation remain separate system responsibilities.

## Evidence Model

Each candidate evidence record retains enough information to support later review and traceability.

Conceptually, the system captures:

- content identity
- source URL and platform
- source title and evidence text
- retrieval provenance
- evidence classification
- confidence or signal strength
- evidence type
- explicit location when supported
- review state
- audit metadata

Candidate evidence starts hidden and pending review.

Only reviewed evidence should become visible or feed downstream reports and recommendations.

## Signal Classification

The system distinguishes between different kinds of evidence rather than treating every public reference as equal.

Examples include:

- circulation signals
- canonical or catalogue sources
- radio or DJ references
- playlists
- charts
- event listings
- press
- social video
- irrelevant or unsupported matches

The purpose is not simply to collect more data.

The purpose is to understand what type of evidence exists and whether it supports a meaningful claim.

## Areas Explored
### Multi-Source Retrieval

Testing showed that a general web search provider could miss relevant content that existed on a native platform.

The architecture therefore separates retrieval paths and merges them into a shared candidate pool rather than assuming one provider offers complete coverage.

### Provenance Preservation

When the same evidence is discovered through more than one retrieval path, the system keeps one candidate while preserving the fact that multiple retrieval methods found it.

This allows the system to deduplicate without destroying provenance.

### Structured AI Classification

AI output is constrained to a structured taxonomy rather than free-form interpretation.

This makes model output easier to validate, store, compare and review.

### Human Trust Gate

AI classification does not automatically turn a candidate into accepted evidence.

Candidates remain pending until a reviewer approves, rejects or corrects them.

The system therefore treats AI as an evidence-processing layer rather than the final authority.

### Evidence Before Recommendation

Recommendations are intended to remain linked to approved evidence.

The goal is to avoid generating advice that cannot be traced back to the observations that support it.

### Failure and Degraded Operation

The architecture is designed so that one retrieval provider failing does not automatically invalidate useful evidence returned by another provider.

Provider outcomes and processing errors can be recorded while valid results continue through the workflow.

### Responsible Data and Governance

The project treats provenance, review state, evidence quality, correction, auditability and controlled visibility as product requirements rather than after-the-fact compliance additions.

Sensitive credentials remain server-side and are kept separate from user-visible records and application outputs.

## Current Product Flow

The Phase 0 product loop is:

1. Add track and ownership details
2. Start an evidence scan
3. Review AI-generated evidence candidates
4. Approve, reject or correct evidence
5. Analyse approved evidence
6. Generate evidence-linked next steps
7. Produce shareable proof

The current prototype includes the core creator workflow, evidence review, recommendations and shareable reporting, while broader commercial capabilities remain part of the longer-term product roadmap.

## Broader Product Direction
TrackGuard starts with independent music creators but explores a broader model:

**Discover signals → verify evidence → recommend action → measure outcomes**

Potential future applications include:

- creator and catalogue intelligence
- venue and promoter decision support
- label and A&R intelligence
- campaign measurement
- rights and attribution workflows
- broader entertainment intelligence

## GSA Systems Labs

TrackGuard is a joint GSA Systems Labs project exploring the intersection of AI, evidence architecture, responsible data practices and decision-support systems.

The project demonstrates how AI-enabled systems can be designed around traceability, structured evidence, human review and operational decision-making rather than simply generating content.

[Back to GSA Systems Labs](../README.md)
