---
name: estimate-timesheet-hours
description: Estimate daily timesheet hours from available work evidence and propose category totals for review. Use for daily timesheet estimates; do not use to write or submit timesheets.
metadata:
  version: "1.0.0"
---

# Estimate Timesheet Hours

Prepare a read-only estimate for one workday in the user's local timezone. The output is a proposal that requires the user's approval; never edit or submit a timesheet with this skill.

## Settings

Use settings supplied by the user or established in their timesheet workflow:

- Requested date and local timezone.
- Timesheet categories, projects and the rules for assigning work to them.
- Relevant repositories, accounts and connected work sources.
- Normal working-day length, if applicable.
- Required rounding increment or timesheet precision, if applicable.

Ask for missing settings when they materially affect the estimate. Do not assume a particular employer, project, timezone, working-day length or rounding increment. If categories are unknown, provide a provisional breakdown for review before proposing final category totals.

## Evidence

Use available, authorized sources for the requested local date. Suitable sources include:

- Calendar entries for scheduled meeting and leave intervals.
- Work messages and conversations as timestamped activity anchors.
- AI assistant or coding-agent task and turn timestamps as activity anchors, when accessible.
- Git activity in repositories relevant to the user's work.
- Issue-tracker activity and context.
- User-provided work logs, diary entries, recorded durations or corrections.

Examples of services include Outlook, Teams, Codex and Jira; equivalent tools may be used. Use only sources accessible in the current environment. Report unavailable sources when their absence materially limits confidence.

Keep searches bounded to the requested local day. Convert source timestamps to the selected timezone. Include direct links when a source returns them. Missing evidence is uncertainty, not zero work.

## Estimation rules

- Calendar start and end times describe scheduled intervals, not proof of attendance. Remove cancelled events, account for known changes, and distinguish confirmed attendance or leave from scheduled-only evidence.
- Treat messages, assistant turns, Git events and issue events as evidence that work occurred near a time, not proof of continuous duration. Do not count a whole gap merely because activity surrounds it.
- Cross-check sources and form conservative, non-overlapping work blocks. Avoid counting the same activity again when it appears in multiple sources.
- Distinguish recorded or user-confirmed durations from inferred durations. Label scheduled-only intervals clearly.
- Assign each block using the user's category rules. Do not automatically assign meetings or administration to a particular category; some workflows allocate them to projects.
- Exclude known unpaid breaks according to the user's timesheet rules.
- Use the normal working-day length only as a reference when one is known. Never invent work to reach it. Show unexplained time explicitly and do not force overtime back down to the reference total.
- Apply the configured rounding rule to proposed entries. If none is known, show the estimated durations without inventing a timesheet rounding requirement.
- Treat user corrections as direct evidence. If a correction conflicts materially with other evidence, explain the discrepancy briefly and resolve it with the user.

## Output

Return one concise breakdown showing the important intervals or work blocks, evidence source, category, hours and whether each duration is recorded, user-confirmed, scheduled-only or inferred.

Then show:

- Each configured timesheet category: proposed hours.
- Total: proposed hours.
- Unexplained: hours, when a known reference day contains time that the evidence does not explain. State the reference used.

Flag material uncertainty and ask the user to approve or correct the proposed figures. For example: `Approve`, or `Project A 5.5, Meetings / Other 2.0`.

Approval validates the estimate. Writing or submitting it requires a separate authorized workflow.
