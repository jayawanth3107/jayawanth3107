# Ride Hub
### Flutter workshop technician and service-management app

Ride Hub is a technician-focused application concept for organizing vehicle-service work from a single workspace. It brings the technician's daily task list, task progress, service history and invoice actions into a straightforward app flow.

> **Portfolio note:** This file documents the project and its known product flows. The runnable Flutter source has not yet been published in this profile repository; this documentation must not be mistaken for a complete source-code release.

## Product goal

Help an automobile workshop technician quickly understand:
- which jobs are assigned,
- which services are in progress,
- what vehicle and service each task relates to,
- what work has already been completed,
- where to find an invoice or start a re-booking flow.

The design prioritizes a quick scan of work over a dense administrative dashboard.

## Main user journey

1. **Sign in** — enter the technician workspace.
2. **Dashboard** — review total and active workload, then scan assigned service cards.
3. **Task details** — open a service job, inspect its vehicle and work information, and follow its progress.
4. **History** — revisit previous service records.
5. **Invoice actions** — generate or print a service invoice and expose a re-booking action.
6. **Profile** — review technician details and skills, edit profile information, or log out.

## Product modules

| Module | Purpose | Known experience |
|---|---|---|
| Dashboard | Daily work overview | Total/active summary and task cards |
| Task details | Focused service execution | Vehicle context, task status and progress |
| History | Past work lookup | Service records with invoice and re-book actions |
| Invoice | Service record output | PDF invoice and print flow |
| Profile | Technician identity | Name, role, technician ID and skill list |

## Dashboard and task model

The current dashboard design uses sample workload values (12 total tasks and 5 active tasks) and representative vehicle-service cards. Example tasks previously used in the app include:

- Engine Repair — Toyota Camry 2022
- Oil Change — Honda City 2023
- AC Service — Maruti Suzuki 2023
- Wheel Alignment — Ford EcoSport 2020
- Battery Replacement — Tesla Model 3 2023

Task cards distinguish **Pending** and **In Progress** states and show a progress percentage. These are demonstration values, not live workshop data.

## UX decisions

### Make work scannable
Vehicle name, model year, service type, status and progress should be visible before opening a task. This reduces navigation for a technician checking several jobs.

### Keep navigation predictable
The primary navigation is organized around Dashboard, History and Profile. The dashboard header is reserved for the dashboard rather than repeated on every destination.

### Keep task detail focused
A task card opens a dedicated detail screen. The detail view should retain its own context rather than forcing the technician to reconstruct the task from the dashboard.

### Make service records actionable
History is not only an archive. Invoice viewing/printing and re-booking are placed close to the completed service record.

### Reduce profile complexity
The technician profile focuses on identity and practical skills. Editing the profile is the main settings action, with logout kept separate and confirmed.

## Suggested engineering model

The following is a proposed domain model for a standalone implementation. It is a design recommendation, not a claim about the current source-code schema.

| Entity | Example fields |
|---|---|
| Technician | id, name, role, skills |
| Vehicle | id, make, model, year |
| ServiceTask | id, vehicleId, serviceType, status, progress, assignedTechnicianId |
| ServiceRecord | id, taskId, completedAt, notes |
| Invoice | id, serviceRecordId, lineItems, total, generatedAt |

A task status should be represented by a defined state rather than free-form text. Progress should be constrained to a valid range and updated through a controlled task action.

## Quality and acceptance checks

| Area | Acceptance check |
|---|---|
| Navigation | Dashboard, History and Profile remain reachable from the main navigation |
| Task state | Pending and In Progress are visually distinct and readable |
| Progress | Displayed progress stays within 0–100% |
| Task identity | Vehicle and service details remain consistent between card and detail view |
| History | A completed service can be reopened without changing its original record |
| Invoice | PDF generation and print action handle empty or missing invoice data safely |
| Re-book | Re-book action starts a new service request rather than modifying the historical job |
| Profile | Edit and logout actions are clearly separated; logout asks for confirmation |
| Responsive UI | Cards and navigation remain usable on narrow screens |

## Technology

- **Flutter** — application UI and navigation.
- **PDF/printing workflow** — invoice output in the app experience.

## Next engineering steps

1. Publish the complete Flutter source in a dedicated Ride Hub repository.
2. Add screenshots of Dashboard, Task Details, History, Invoice and Profile.
3. Document actual package versions, data persistence and navigation structure from the source.
4. Add unit/widget tests for task state, progress boundaries, invoice formatting and logout flow.
5. Add a demo build or short walkthrough video.

## Scope and honesty

This document describes the screens and behaviors established in the project work. It does not claim production deployment, live workshop integrations, real customer data, backend architecture or test results that have not been verified from a published source repository.
