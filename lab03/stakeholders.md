# CampusPulse stakeholder analysis

Name or team: Fatima Alteneiji

Date: 2026-09-08

Read the stakeholder notes in the lab handout before completing this file.
Use the stakeholder types and power-interest quadrants from Week 2, Lecture 2.

Stakeholder types: end user, operations, business, regulator, negative stakeholder

Power-interest quadrants: key player, keep satisfied, keep informed, minimal effort

## S1

- Stakeholder: Student attendee
- Stakeholder type: End user
- Power-interest quadrant: Keep informed
- Main goal: Find followed groups, announcements, and events in one phone-friendly service, and RSVP without having a name exposed by default.
- Main concern: Public RSVP visibility could compromise privacy, and an inaccessible interface could exclude students who use screen readers.
- How you would involve or monitor this stakeholder: Recruit students who use phones and screen readers for prototype reviews and accessibility testing. Survey pilot users about feed usefulness and RSVP privacy before each release decision.

## S2

- Stakeholder: Group officer
- Stakeholder type: End user
- Power-interest quadrant: Key player
- Main goal: Collaborate with other approved officers to prepare and publish events or announcements for the correct audience.
- Main concern: An unapproved person could publish as the group, or RSVP attendees could miss a change to an event's time or place.
- How you would involve or monitor this stakeholder: Include officers from several group types in workflow workshops and acceptance tests. Review failed publication attempts and delivery results for event-change notifications during the pilot.

## S3

- Stakeholder: Campus moderator
- Stakeholder type: Operations
- Power-interest quadrant: Key player
- Main goal: Act quickly on harmful content while preserving enough evidence and decision history to support an appeal.
- Main concern: Immediate hiding could destroy evidence, while delayed action could leave a phishing or unsafe event visible.
- How you would involve or monitor this stakeholder: Co-design the report, hide, and appeal workflow with moderators. Run incident simulations and audit samples of moderation records for complete evidence, actor, timestamp, reason, and outcome.

## S4

- Stakeholder: Student Affairs
- Stakeholder type: Business
- Power-interest quadrant: Key player
- Main goal: Operate a credible pilot for 5,000 students and 200 groups in which an official badge reliably means that the group was checked.
- Main concern: A misleading badge, failed pilot capacity, or missed Orientation Week deadline would undermine trust and sponsorship.
- How you would involve or monitor this stakeholder: Obtain approval for badge policy and pilot scope, give fortnightly delivery and risk reports, and ask Student Affairs to accept verification and capacity tests before launch.

## S5

- Stakeholder: Data Protection Officer
- Stakeholder type: Regulator
- Power-interest quadrant: Keep satisfied
- Main goal: Limit personal-data collection, keep RSVP lists private by default, and remove cancelled-event attendance data within 30 days.
- Main concern: CampusPulse could expose attendance information, collect data without a defined need, or retain identifiable records longer than permitted.
- How you would involve or monitor this stakeholder: Request a privacy review of the data inventory, access rules, and deletion design. Provide evidence from privacy tests and scheduled retention audits, and escalate any deletion failure immediately.

## S6

- Stakeholder: Abusive or compromised account operator
- Stakeholder type: Negative stakeholder
- Power-interest quadrant: Minimal effort
- Main goal: Mislead users by imitating a verified group, publishing a phishing event, or repeatedly posting the same announcement.
- Main concern: From the project perspective, this actor threatens group authenticity, user safety, and feed quality.
- How you would involve or monitor this stakeholder: Do not involve the actor in product decisions. Monitor lookalike-group reports, suspicious links, repeated-post signals, compromised-account reports, and moderation outcomes as abuse indicators.

## Conflicts to resolve

Describe at least two real tensions. For each one, name both stakeholder IDs
and either propose a decision or write a specific question that should go back
to the stakeholders.

### Conflict 1

- Stakeholders: S1 and S5 versus S2
- What conflicts: Students and the Data Protection Officer require RSVP lists to be private by default, while officers need to reach everyone who RSVP'd when event details change. Publishing or exporting attendee names would make communication easy but would conflict with the privacy evidence.
- Proposed decision or follow-up question: Keep attendee names off public lists unless each student opts in. Let an approved officer trigger a message to the private RSVP cohort without receiving a public list of names. Ask S2 and S5: **Which officer roles, if any, require access to identifiable RSVP records for members-only events?**

### Conflict 2

- Stakeholders: S3 and S2
- What conflicts: A moderator may need to hide an event immediately, while a group officer needs a fair appeal and evidence of what was removed and why. Deleting the item would support neither an appeal nor an audit, but leaving suspected harmful content visible would expose students.
- Proposed decision or follow-up question: Separate visibility from evidence retention. An authorized moderator may hide an event immediately from ordinary users, while CampusPulse preserves a read-only snapshot, report reason, moderator identity, timestamp, and decision for the appeal workflow. Notify the group of the action and allow an appeal without restoring the event automatically.
