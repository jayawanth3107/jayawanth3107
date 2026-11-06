# Ride Hub — UI/UX case study
### Designing a technician-first workshop workflow

**Product:** Ride Hub  
**Platform:** Flutter app  
**Focus:** Task clarity, service progress, service history and invoice actions  
**Project type:** Student application project

## The design challenge

A workshop technician needs to move between today's assigned jobs and previous service records without losing the vehicle or service context. The design objective for Ride Hub is to make the next action obvious: identify the job, understand its state, open the details, then return to the work list or service history.

This is a product-design framing based on the app's existing screen set. It is not a claim that formal user research or usability testing has been completed.

## Primary user

**Workshop technician**

Needs to scan assigned work, understand the vehicle/service pairing, recognize pending versus active work, and find completed-service records when needed.

## Information architecture

- **Dashboard:** workload overview and assigned service tasks.
- **Task details:** one job's vehicle context, service information, status and progress.
- **History:** previously handled service records.
- **Invoice:** PDF output and print action for a service record.
- **Profile:** technician identity, role and skills.

## Core journey

1. Sign in to the technician workspace.
2. Scan the dashboard summary and task cards.
3. Select a service task.
4. Review the task details and progress.
5. Return to the dashboard or open History.
6. Select a completed record to view/print its invoice or begin a re-booking flow.
7. Use Profile to edit technician information or log out.

## Key interaction decisions

### 1. Put the work queue first
The dashboard is the natural starting point. Total and active workload values establish a quick overview; individual cards provide the next level of detail.

### 2. Make status visible at a glance
Pending and In Progress labels are paired with progress percentages. The user should not need to open every task merely to understand its current state.

### 3. Preserve vehicle context
Service type and vehicle make/model/year are grouped together. This reduces ambiguity when a technician is switching between multiple jobs.

### 4. Separate current work from historical records
Dashboard and History are different destinations. A historical invoice should remain a record of completed work, while re-booking should create a new service flow rather than silently editing the original record.

### 5. Keep profile actions minimal
Technician identity and skills remain the focus. Profile editing and logout are clear actions, not a long settings list.

## Visual direction

The app uses a light, card-based interface. A consistent spacing rhythm, readable type, clear status treatment and predictable bottom navigation support quick use during a busy workshop day.

The intended hierarchy is:

1. page title and workload summary,
2. service task identity,
3. status and progress,
4. task action,
5. secondary navigation.

## States that deserve explicit design

- Loading task list
- Empty task list
- Pending task
- In-progress task
- Completed service record
- Invoice being generated
- Invoice generation or print failure
- Missing vehicle/service information
- Session expiry and confirmed logout

Showing these states consistently is part of the product design—not a final polish step.

## Engineering hand-off considerations

The design implies a small set of domain objects: Technician, Vehicle, ServiceTask, ServiceRecord and Invoice. A dedicated task status model and bounded progress value help keep the dashboard and detail screen consistent.

For invoice handling, the service record should remain the source of truth. A re-book action should create a new task linked to the earlier service record, rather than overwrite historical data.

## Validation plan

| Test | What success looks like |
|---|---|
| Find an active task | A technician can identify an In Progress task from the dashboard card |
| Open a task | Vehicle and service context match the dashboard item |
| Return to work queue | Navigation preserves the user's place in the task flow |
| Find an old invoice | A service record is discoverable from History |
| Print an invoice | The generated document contains the selected service record |
| Re-book | A new job is created without modifying the old invoice |
| Use on a narrow screen | Core actions remain readable and reachable |

No usability score, time saving or customer outcome is claimed because a formal test study has not been recorded.

## Next iteration

- Add real screenshots and annotate key interactions.
- Test dashboard scanning with technicians.
- Validate touch-target size and contrast on mobile screens.
- Add widget tests for task state and progress.
- Verify PDF layout on different paper sizes and print destinations.

## Source availability

This case study is published inside the profile repository as project documentation. The full Flutter source should be moved into a dedicated public Ride Hub repository before presenting it as a source-code portfolio project.
