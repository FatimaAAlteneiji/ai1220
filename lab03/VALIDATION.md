# CampusPulse requirements review

Name or team: Fatima Alteneiji

Reviewer: Fatima Alteneiji (self-review)

Date: 2026-09-08

Review the completed `stakeholders.md` and `REQUIREMENTS.md`. Refer to specific
IDs and evidence in every answer. A yes or no by itself is not enough.

## Validity

Do the requirements represent what the stakeholders need? Which IDs did you
check, and what evidence supports them?

Response:

The requirements represent each recorded stakeholder need. S1 supports the combined feed and privacy requirements in UR-1–UR-3 and the phone and screen-reader requirement in UR-12. S2 supports officer collaboration, publishing permission, audience control, and change notifications in UR-4–UR-6. S3 supports the report, hide, evidence, audit, and appeal requirements in UR-7 and UR-11. S4 supports badge integrity and pilot scale in UR-8 and UR-9. S5 supports private-by-default RSVP identity and cancellation-based deletion in UR-2 and UR-10. S6 supports verification controls and repeated-announcement warning in UR-8 and UR-13. The stakeholder analysis also resolves the privacy-versus-notification tension by sending to a private RSVP cohort rather than publishing attendee names.

## Consistency

Do any requirements contradict one another or the release scope?

Response:

No unresolved contradiction was found. UR-2 makes RSVP identity private by default, while optional UR-3 permits only the student to make their own name public; FR-2 and FR-3 preserve that distinction. UR-7 permits an immediate hide, while UR-11 and FR-13 permit an appeal without automatic restoration, so safety and due process do not conflict. The browser and responsive requirements in scope, UR-12, NFR-2, and NFR-3 do not claim a native mobile application. The six exclusions in Section 1 exactly match the Won't list in Section 6.

## Completeness

Is an important actor, normal flow, failure, permission, privacy rule, or
boundary missing?

Response:

The document includes student, group-officer, moderator, Student Affairs, Data Protection Officer, and abuse viewpoints. Normal flows appear in FR-1, FR-2, FR-4, FR-7, and FR-10. Failure and permission boundaries appear in FR-5 and FR-11 and in US-2 and US-4. Privacy and retention appear in FR-2, FR-3, FR-12, NFR-5, US-1, and US-5. Release boundaries are explicit in Sections 1 and 6. Details not supported by the source are not hidden: Q2 asks who may see identifiable RSVP records, Q3 asks for appeal and evidence-retention periods, Q4 asks for badge checks and authority, Q5 asks about backups, and Q6 asks for supported accessibility platforms.

## Realism

Can the proposed release and its quality targets reasonably be delivered? Mark
unsupported targets as assumptions or open questions.

Response:

The release is plausible because it is browser-only, limited to university sign-in, and excludes direct messages, payments, video hosting, and artificial-intelligence recommendations. The source supports the 5,000-student and 200-group data scale, but it supplies no peak traffic figure. NFR-1 therefore labels 500 concurrent sessions, two seconds, one percent, and 60 minutes as team assumptions in A1 and asks Student Affairs to confirm the peak in Q1. The accessibility, phone-viewport, and notification figures in NFR-2–NFR-4 are likewise recorded as A2–A4 rather than attributed to stakeholders. Backup deletion remains an open decision in Q5 rather than an unsupported promise.

## Verifiability

Could a tester decide whether each requirement passes or fails? Identify any
wording that is still vague.

Response:

The FRs identify an observable action and result: for example, FR-5 requires rejection of an unauthorized publication, FR-6 defines both audience choices and the non-member result, and FR-9 lists every field in the hide record. Each NFR supplies a target and a condition. The acceptance criteria use Given/When/Then conditions and include privacy, failure, and permission cases. The words **checked group**, **necessary personal data**, and **supported platform** still depend on policy decisions; Q4, a future data inventory, and Q6 must resolve those terms before final acceptance testing. FR-12 was revised because its earlier wording did not identify when the 30-day period began or which data was removed.

## One requirement you revised

- Requirement ID: FR-12
- Before: FR-12 [Must] The system shall delete attendance data within 30 days after an event is cancelled. [Source: UR-10]
- What was wrong or missing: The wording did not state who could trigger cancellation, when the deletion period began, or that identifiable RSVP records were the attendance data to remove.
- After: FR-12 [Must] The system shall start the attendance-data deletion period when an approved officer cancels an event and shall remove the event's identifiable RSVP records when that period expires. [Source: UR-10]
- Evidence or stakeholder to confirm the change: S5 supplies the 30-day cancellation rule. S2 should confirm that an approved officer is the correct cancellation actor, and S5 should confirm the meaning of identifiable RSVP records. The revised FR-12 appears in `REQUIREMENTS.md` Section 3 and in the S5–UR-10–FR-12/NFR-5–US-5 traceability row.

## Final check

- [x] Stakeholder conflicts have a decision or a follow-up question.
- [x] Scope exclusions agree with the Won't list.
- [x] Every FR and NFR traces to a user requirement.
- [x] Every NFR contains a measurable target and condition.
- [x] Traceability rows use IDs that exist in the document.
- [x] The revised requirement has also been updated in the traceability table.
