# ekko-technology — Project Portfolio Page

## Overview

Astra is a fast, keyboard-driven CLI planner for students to track academic activities (tasks, lectures, tutorials, exams) and compute their GPA. It stores data in simple text/CSV files for transparency and portability. My role focused on the entire GPA feature set, Astra's architecture, parser functionalities, key activity commands, and elevating the Developer Guide with accurate, maintainable diagrams.

## Summary of Contributions

### Code contributed

- Code Dashboard: [Link to Personal Code Panel from Cohort's Code Dashboard](https://nus-cs2113-ay2526s1.github.io/tp-dashboard/?search=ekko&sort=groupTitle&sortWithin=title&timeframe=commit&mergegroup=&groupSelect=groupByRepos&breakdown=true&checkedFileTypes=docs~functional-code~test-code~other&since=2025-09-19T00%3A00%3A00&filteredFileName=&tabOpen=true&tabType=authorship&tabAuthor=Kurokishi592&tabRepo=AY2526S1-CS2113-W12-1%2Ftp%5Bmaster%5D&authorshipIsMergeGroup=false&authorshipFileTypes=docs~functional-code~test-code&authorshipIsBinaryFileTypeChecked=false&authorshipIsIgnoredFilesChecked=false)
- GitHub commits: https://github.com/AY2526S1-CS2113-W12-1/tp/commits/master?author=Ekko-Technology

I authored and maintained code in the `astra.activity` and `astra.command` packages, focusing on task priority, deadline updates, and the activity creation commands.

### Enhancements implemented (high level)

- Add commands for activities

  - `AddTaskCommand` — implemented parsing for description, `/by <YYYY-MM-DD> <HH:MM>` and `/priority <number>`; validated priority bounds (between 1 and taskCount+1), shifted existing priorities on insert, persisted to Notebook, and provided readable task messages.
  - `AddExamCommand`, `AddLectureCommand`, `AddTutorialCommand` — implemented/maintained input parsing, validation of required fields (dates/times/day-of-week/place as appropriate), and persistence.

- Change priority feature (`ChangePriorityCommand`)

  - Implemented numeric priority rebalancing for tasks: when a task's priority is changed, other tasks' priority numbers are shifted to preserve a contiguous 1..N range.
  - Implemented detailed validation and UI messages for edge cases (missing `/to` flag, invalid integers, out-of-range priorities, etc.)


- Change deadline feature (`ChangeDeadlineCommand`)
  - Implemented date/time parsing and validation for deadline updates; preserved existing task state and ensured Notebook persistence after updates.
  - Added helpful error messages for malformed date/time tokens.

### Summary of Contributions

This section follows the PPP format required for the module. Each subsection below documents a distinct contribution area.

1) Code contributed

- Code Dashboard: ([ekko-technology-dashboard-link](https://nus-cs2113-ay2526s1.github.io/tp-dashboard/?search=ekko&sort=totalCommits%20dsc&sortWithin=title&timeframe=commit&mergegroup=&groupSelect=groupByNone&breakdown=true&checkedFileTypes=functional-code~other~test-code~docs&since=2025-09-19T00%3A00%3A00&filteredFileName=))

- GitHub commits (selected): https://github.com/AY2526S1-CS2113-W12-1/tp/commits/master?author=Ekko-Technology&after=4c1099ebbc3fd8d8f4204742700d8897518b15ae+34


2) Enhancements implemented

- Add commands (create flows)
  - `AddTaskCommand`: full parsing and validation for the `task <desc> /by <YYYY-MM-DD> <HH:MM> /priority <n>` form, bounds-checking for priority (1..taskCount+1), shifting existing priorities on insert, and persistence to `Notebook`.
  - `AddExamCommand`, `AddLectureCommand`, `AddTutorialCommand`: implemented/maintained parsing and validation for required fields (dates/times/place/day), and ensured consistent persistence behavior.

- Change priority (`ChangePriorityCommand`)
  - Implemented priority rebalancing algorithm that updates numeric priority labels of affected tasks so the label set remains contiguous (1..N). Added validation for missing flags, non-integer input, out-of-range values, non-task selection, and same-priority no-ops.
  - Ensured the command updates numeric labels only and preserves the `ActivityList` ordering (indices remain stable).

- Change deadline (`ChangeDeadlineCommand`)
  - Implemented robust date/time parsing and validation for deadline updates, preserved task state, updated deadline fields, and persisted changes.

3) Contributions to the User Guide (UG)

- I added usage examples and error-handling notes for activity creation commands (`task`, `exam`, `lecture`, `tutorial`) and for `changedeadline` / `changepriority` flows. These help end users understand valid input forms and expected error messages.

4) Contributions to the Developer Guide (DG)

- I authored and updated several PlantUML sequence diagrams and their exported PNGs used in the Developer Guide. My DG contributions focused on making diagrams accurate and maintainable. Key diagrams I added/updated:
  - `docs/diagrams/checkCurrent_sequence.puml` → `docs/images/checkCurrent_sequence.png`
  - `docs/diagrams/checkPriority_sequence.puml` → `docs/images/checkPriority_sequence.png`
  - `docs/diagrams/changePriority_sequence.puml` → `docs/images/changePriority_sequence.png`
  - `docs/diagrams/ChangeDeadline_sequence.puml` → `docs/images/changeDeadline_sequence.png`

- Implementation notes for DG work:
  - Added explicit diagram names after `@startuml` to avoid unnamed-diagram warnings.
  - Corrected lifelines and deactivation semantics where diagrams diverged from code (e.g., `CheckCurrent` uses a local `ArrayList<Task>` in code rather than creating a new `ActivityList`).
  - Ensured diagrams show `Notebook.saveToFile(...)` persistence steps where applicable.

5) Contributions to team-based tasks

- Helped debug parsing and priority edge cases across the codebase.
- Participated in maintaining checkstyle and code quality for files I edited.

6) Review / mentoring contributions

- Reviewed PRs related to activity parsing and priority implementation; provided feedback on error messages, assertions, and test coverage.




