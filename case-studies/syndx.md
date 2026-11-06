# SynDx — engineering and product case study
### Offline-first clinical workflow and decision-support research

**Repository:** [Creater-jod/synDx](https://github.com/Creater-jod/synDx)  
**Collaboration evidence:** [Merged pull request #1 — Jawa](https://github.com/Creater-jod/synDx/pull/1)  
**Project owner:** Creater-jod  
**My GitHub account:** jayawanth3107

## My collaboration record

I collaborated on SynDx through pull request **#1**, titled **Jawa**.

- Opened under the GitHub account jayawanth3107.
- Merged into main on **17 September 2026**.
- The PR records **5 commits** and **356 changed files**.
- Its changed paths span the Android/Kotlin application, web client, backend services, model/data pipeline, tests and project documentation.

This is a team repository. The PR is evidence of my collaboration and submitted work; it is not a claim that I independently authored or own every component in the repository.

## The product problem

SynDx explores a practical workflow for low-connectivity healthcare settings: capture structured patient and visit information, preserve work when the network is unreliable, surface configured safety checks, and make a case available for clinician review.

The design goal is to support a health worker and a clinical reviewer while keeping automated outputs subordinate to human judgement.

## Product experience

The repository documents a guided clinical workflow that includes:

- Patient and visit context
- Signs, measurements and structured intake
- Entry verification
- Triage/review information
- Next-action and referral guidance
- Doctor review and audit history

The PWA uses a high-contrast warm-paper visual direction intended for low-cost Android devices and bright environments. Large touch targets and a sequential flow reduce the need to interpret a dense clinical dashboard.

## System architecture

The documented web workflow combines:

- **Client:** installable progressive web app with a cached application shell.
- **Backend:** modular Node.js and Express API.
- **Database:** SQLite with structured repositories and parameterized query paths.
- **Model service:** separate Python FastAPI service for the Wilson-disease phenotype research models.
- **Offline behavior:** local draft persistence and a queued mutation/synchronisation flow.
- **Review:** clinician review actions and an application-level audit history.

![SynDx software stack diagram](https://raw.githubusercontent.com/Creater-jod/synDx/main/reports/syndx_diagrams/fig3_1_software_stack.png)

## Engineering decisions worth understanding

### Deterministic safety checks are separate from model output
Configured emergency-vitals rules are evaluated deterministically and are not delegated to a language model. The design keeps urgent safety logic separate from probabilistic research inference.

### Offline drafts need safe replay
The client preserves draft work and tracks mutation states before and after connectivity returns. Client mutation identifiers support duplicate protection when queued work is retried.

### The model service has a narrow research scope
The documented clinical model uses a single-center cohort of **185 Wilson-disease cases** for a neurological-versus-hepatic phenotype task. The class distribution is imbalanced (163 neurological and 22 hepatic cases). This is preliminary research, not evidence of a broad rare-disease classifier.

### Human review remains part of the workflow
The doctor review experience supports confirmation or override with a note. The system should not be described as autonomous diagnosis or prescription software.

## Testing and evidence

The repository's October 2026 project-status document reports **98 automated tests passing** across backend, offline/PWA, draft/sync, multimodal-safety and model-pipeline test suites.

That is software test evidence—not clinical validation. Clinical performance, external generalisation and real-world workflow impact require separate studies.

## Implemented, simulated and planned capabilities

| Area | Repository-documented status |
|---|---|
| Guided PWA and offline app shell | Implemented |
| Local drafts and sync queue | Implemented |
| Deterministic emergency-vitals rules | Implemented as software rules |
| Wilson phenotype model service | Research prototype |
| Federated learning | Local simulation, not a live clinic network |
| Broad multi-disease classifier | Not trained |
| Public-chain smart contract audit | Not established |
| Multimodal eye/voice modules | Planned, not active |

The audit history is an application-level hash-chain prototype; it should not be presented as a deployed public blockchain or as proof of clinical-grade tamper resistance.

## What this project demonstrates

- Product thinking for constrained operating environments
- Separation of user workflow, backend services and research inference
- Offline-state and retry design
- Structured data handling and provenance awareness
- Safety boundaries and human-in-the-loop review
- The importance of documenting model limitations alongside headline metrics

## Further engineering work

- Independent validation on larger, representative datasets
- Device-level offline testing and recovery testing
- Security and privacy review for real clinical data
- Stronger audit-integrity verification against independent checkpoints
- Clear model-to-interface traceability and calibrated explanations
- Physical-clinic pilot studies with clinical governance

## Scope and safety statement

SynDx is documented as a **clinical decision-support research prototype**, not a certified medical device. Example patient records are synthetic. It must not be used as a standalone diagnostic system or as a substitute for a qualified medical professional.
