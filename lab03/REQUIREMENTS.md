# CampusPulse requirements

Name or team: Fatima Alteneiji

Date: 2026-09-08

Status: validated draft

Use the source IDs `S1` to `S6` from the lab handout. Keep every requirement
short enough to test and trace.

## 1. Release scope

### In scope

- A browser-based, mobile-responsive service that uses university sign-in for the pilot population of 5,000 students and 200 groups.
- Verified group profiles, an official verification badge, group following, and a combined feed of announcements and events.
- Collaborative drafting by approved group officers, controlled publishing, and university-wide or members-only audiences.
- Event RSVP with private-by-default attendee identity and optional public-name consent.
- Notifications to RSVP'd students when an event's time or place changes.
- Reports, immediate hiding, retained moderation evidence, recorded decisions, group appeals, and protection against repeated identical announcements.
- Cancellation of events and deletion of their attendance data within 30 days.

### Out of scope

- Native mobile applications.
- Direct messages.
- Accounts for external users who do not use university sign-in.
- Payments or ticket sales.
- Video hosting.
- Artificial-intelligence recommendations.

## 2. User requirements

Write at least five customer-readable needs. Use one need per line and trace it
to the stakeholder evidence.

Format: `UR-1 [Must] ... [Source: S1]`

- UR-1 [Must] Students can follow verified groups and view their announcements and events in one feed. [Source: S1]
- UR-2 [Must] A student's RSVP and name are private by default. [Source: S1, S5]
- UR-3 [Could] A student can choose to make their name visible on an event's attendee list. [Source: S1]
- UR-4 [Must] Approved group officers can collaborate on drafts, while people without publishing approval cannot publish for the group. [Source: S2]
- UR-5 [Must] Group officers can limit each event to the whole university or to group members. [Source: S2]
- UR-6 [Must] Students who RSVP receive notice when an event's time or place changes. [Source: S2]
- UR-7 [Must] Moderators can review a report's content and reason, hide the reported event immediately, and retain evidence and the decision-maker's identity for an appeal. [Source: S3]
- UR-8 [Must] An official badge identifies only a group that Student Affairs has checked. [Source: S4, S6]
- UR-9 [Must] The pilot supports 5,000 university students and 200 groups using university sign-in. [Source: S4]
- UR-10 [Must] CampusPulse collects only necessary personal data and deletes attendance data within 30 days after an event is cancelled. [Source: S5]
- UR-11 [Should] Groups can appeal a moderation decision without automatically making hidden content visible. [Source: S3]
- UR-12 [Should] Students can complete the feed, event, and RSVP journeys on a phone and with a screen reader. [Source: S1]
- UR-13 [Could] An approved officer receives a warning before publishing an announcement identical to one the same group recently published. [Source: S6]

## 3. Functional requirements

Write at least six observable system behaviours. Start each one with "The
system shall" and trace it to one or more user requirements.

Format: `FR-1 [Must] The system shall ... [Source: UR-1]`

- FR-1 [Must] The system shall let a signed-in student follow or unfollow a verified group and shall include currently followed groups' published announcements and visible events in that student's feed. [Source: UR-1, UR-9]
- FR-2 [Must] The system shall record a new RSVP with attendee-list visibility set to private, regardless of the visibility of earlier RSVPs. [Source: UR-2]
- FR-3 [Could] The system shall let a student change only their own RSVP-name visibility between private and public. [Source: UR-3]
- FR-4 [Must] The system shall let an approved officer save a draft and let another approved officer for the same group edit that draft. [Source: UR-4]
- FR-5 [Must] The system shall reject a publish request when the signed-in user does not hold publishing approval for the group. [Source: UR-4]
- FR-6 [Must] The system shall require an officer to select either university-wide or members-only visibility before publishing an event, and shall withhold a members-only event from non-members. [Source: UR-5]
- FR-7 [Must] The system shall create a notification for every current RSVP holder when an approved officer publishes a change to an event's time or place. [Source: UR-6]
- FR-8 [Must] The system shall store, with each report, an immutable snapshot of the reported event and the reporter's selected reason and entered explanation. [Source: UR-7]
- FR-9 [Must] The system shall let an authorized moderator hide a reported event and shall record the moderator's university identity, action, reason, and timestamp without deleting the report snapshot. [Source: UR-7]
- FR-10 [Must] The system shall display the official badge only when the group's verification status has been set to verified by an authorized Student Affairs user. [Source: UR-8]
- FR-11 [Must] The system shall authenticate pilot users through university sign-in and reject access after authentication fails. [Source: UR-9]
- FR-12 [Must] The system shall start the attendance-data deletion period when an approved officer cancels an event and shall remove the event's identifiable RSVP records when that period expires. [Source: UR-10]
- FR-13 [Should] The system shall let an approved group officer submit an appeal that names the moderation decision and includes an explanation, while keeping the hidden event unavailable to ordinary users. [Source: UR-11]
- FR-14 [Could] The system shall warn an approved officer when the announcement being published has the same normalized title and body as an announcement that the same group published in the previous 24 hours. [Source: UR-13]

## 4. Non-functional requirements

Write at least four measurable quality requirements. State what is measured,
the target, and the condition under which the target applies. If you introduce
a number that is not in the handout, record it as an assumption or open
question in Section 8.

Format: `NFR-1 [Must] The system shall ... [Measure: target and condition] [Source: UR-1]`

- NFR-1 [Must] The system shall serve the pilot workload without data loss and with timely responses. [Measure: with data for 5,000 student accounts and 200 groups, at least 95% of feed, event-detail, and RSVP requests complete within 2 seconds, fewer than 1% return a server error, and no committed RSVP is lost during a 60-minute test at 500 concurrent sessions.] [Source: UR-9]
- NFR-2 [Must] The system shall make the feed, event-detail, RSVP, report, and appeal journeys accessible. [Measure: before release, every named journey has zero WCAG 2.2 Level A or AA failures in automated checks and passes manual keyboard-only and screen-reader tests for all required steps.] [Source: UR-7, UR-11, UR-12]
- NFR-3 [Should] The system shall present each in-scope student journey without horizontal page scrolling on supported phone displays. [Measure: all content and controls in the feed, event-detail, and RSVP journeys remain operable at viewport widths from 320 to 430 CSS pixels at 200% browser zoom, excluding user-supplied media that opens separately.] [Source: UR-12]
- NFR-4 [Must] The system shall dispatch event-change notifications promptly. [Measure: at least 95% of notifications created after a published time or place change are handed to the configured delivery service within 5 minutes, measured over each rolling 24-hour period.] [Source: UR-6]
- NFR-5 [Must] The system shall complete cancelled-event attendance-data deletion on time. [Measure: for 100% of cancelled events, no identifiable RSVP record is returned from active application data stores at or after 30 days from the recorded cancellation timestamp.] [Source: UR-10]

## 5. User stories and acceptance criteria

Write at least three stories from different stakeholder viewpoints. Each story
needs at least two acceptance criteria. Across the set, include a failure,
permission boundary, privacy rule, or other non-happy path.

### US-1 [Must] [Source: S1, S5, UR-1, UR-2, UR-3]

As a student attendee,

I want to follow groups and RSVP privately,

so that I can find relevant events without exposing my attendance unless I choose to do so.

Acceptance criteria:

- Given a signed-in student who follows a verified group, when that group publishes an event visible to the student, then the event appears in the student's feed.
- Given any event and a student's first RSVP to it, when the RSVP is saved, then the student's name is absent from the public attendee list.
- Given a private RSVP owned by the signed-in student, when the student explicitly changes its name visibility to public, then the name appears on the attendee list; another student cannot make this change.

### US-2 [Must] [Source: S2, UR-4, UR-5, UR-6]

As an approved group officer,

I want to collaborate on audience-controlled events and notify RSVP holders of corrections,

so that accurate information reaches the right campus community.

Acceptance criteria:

- Given a draft created by one approved officer, when a second approved officer for the same group edits and publishes it with members-only visibility, then members can view it and non-members cannot.
- Given a user without publishing approval, when that user attempts to publish the draft, then publication is rejected and the draft remains unpublished.
- Given a published event with current RSVP holders, when an approved officer changes its time or place and publishes the change, then one notification is created for each current RSVP holder.

### US-3 [Must] [Source: S3, UR-7, UR-11]

As a campus moderator,

I want to hide a reported event while preserving the report, evidence, and decision record,

so that I can protect students immediately and still support an accountable appeal.

Acceptance criteria:

- Given a report with a reason and event snapshot, when an authorized moderator hides the event, then ordinary users can no longer view it and the snapshot remains available to authorized moderators.
- Given a hide action, when its audit record is opened, then it shows the acting moderator's university identity, timestamp, action, and reason.
- Given a hidden event, when an approved officer submits an appeal, then the appeal is linked to the hide decision and the event remains hidden until a separate authorized decision restores it.

### US-4 [Must] [Source: S4, S6, UR-8, UR-9]

As a Student Affairs administrator,

I want the official badge to appear only for checked groups,

so that students can distinguish verified groups from imitations during the pilot.

Acceptance criteria:

- Given an unverified group, when its profile or event is displayed, then no official badge appears.
- Given an authorized Student Affairs user who sets the group to verified, when that group's profile or event is displayed, then the official badge appears.
- Given a group officer without Student Affairs authority, when the officer attempts to set verification status, then the request is rejected and no badge appears.

### US-5 [Must] [Source: S5, UR-10]

As the Data Protection Officer,

I want cancelled-event attendance records removed within the stated period,

so that personal data is not retained longer than needed.

Acceptance criteria:

- Given an event with RSVPs, when an approved officer cancels it, then a cancellation timestamp is recorded and its attendance-data deletion period begins.
- Given a cancelled event whose cancellation timestamp is at least 30 days old, when active application data stores are queried, then no identifiable RSVP record for that event is returned.

### US-6 [Could] [Source: S6, UR-13]

As an approved group officer,

I want a warning before I publish a repeated announcement,

so that I can avoid accidental duplicates and notice suspicious account activity.

Acceptance criteria:

- Given an identical normalized title and body published by the same group in the preceding 24 hours, when an approved officer attempts to publish it again, then a duplicate warning identifies the earlier announcement.
- Given no identical announcement from that group in the preceding 24 hours, when an approved officer publishes, then no duplicate warning is shown.

## 6. MoSCoW summary

List requirement or story IDs in every category. The Won't category must state
what is excluded from this release.

- Must: UR-1, UR-2, UR-4–UR-10; FR-1, FR-2, FR-4–FR-12; NFR-1, NFR-2, NFR-4, NFR-5; US-1–US-5.
- Should: UR-11, UR-12; FR-13; NFR-3.
- Could: UR-3, UR-13; FR-3, FR-14; US-6.
- Won't this release: Native mobile applications, direct messages, external-user accounts, payments or ticket sales, video hosting, and artificial-intelligence recommendations.

## 7. Traceability

Add at least four complete paths. Every row should connect evidence to a user
requirement, a system requirement, and a user story.

| Stakeholder need | User requirement | System requirement | User story |
|---|---|---|---|
| S1: One place for followed groups | UR-1 | FR-1 | US-1 |
| S1 and S5: RSVP identity private by default | UR-2 | FR-2 | US-1 |
| S2: Approved officers collaborate; unauthorized users cannot publish | UR-4 | FR-4, FR-5 | US-2 |
| S2: Notify RSVP holders after time or place changes | UR-6 | FR-7, NFR-4 | US-2 |
| S3: Hide immediately but retain evidence and decision identity | UR-7 | FR-8, FR-9, NFR-2 | US-3 |
| S3: Permit appeals without automatic restoration | UR-11 | FR-13 | US-3 |
| S4 and S6: Badge means the group was checked | UR-8 | FR-10 | US-4 |
| S4: Pilot for 5,000 students and 200 groups | UR-9 | FR-11, NFR-1 | US-4 |
| S5: Delete attendance data within 30 days of cancellation | UR-10 | FR-12, NFR-5 | US-5 |
| S6: Address repeated identical announcements | UR-13 | FR-14 | US-6 |

## 8. Assumptions and open questions

Separate decisions your team has assumed from questions that still need an
answer.

### Assumptions

- A1: The NFR-1 planning baseline is 500 concurrent sessions, a 2-second response target, a 1% server-error ceiling, and a 60-minute test. These figures are team assumptions because the handout gives no Orientation Week peak-traffic figure.
- A2: NFR-2 uses WCAG 2.2 Level AA as the accessibility acceptance baseline and requires one agreed screen-reader/browser combination for each supported desktop and mobile platform.[1]
- A3: NFR-3 treats 320–430 CSS pixels and 200% browser zoom as the supported phone-display test range.
- A4: NFR-4 assumes that dispatch to the configured delivery service within 5 minutes for 95% of notifications is acceptable; delivery after handoff depends on that external service.
- A5: FR-14 treats announcements with the same normalized title and body from the same group within 24 hours as duplicates. Normalization removes leading and trailing whitespace, collapses repeated whitespace, and ignores letter case.
- A6: For NFR-5, "active application data stores" means production databases, search indexes, caches, and analytics stores queried by CampusPulse. Backup erasure or expiry needs a separate retention decision under Q5.

### Open questions

- Q1: What peak concurrent-user figure and response-time target should Student Affairs approve for Orientation Week?
- Q2: Which officer roles, if any, may view identifiable RSVP records for members-only events?
- Q3: How long may moderation evidence be retained, and within what time must an appeal receive a decision?
- Q4: Which checks must Student Affairs complete before granting an official badge, and which staff roles may grant or revoke it?
- Q5: Within what period must cancelled-event attendance data expire from backups, and how should a restoration prevent expired data from returning to active stores?
- Q6: Which browser, operating-system, and screen-reader combinations are supported for the pilot?

## 9. References

[1]: https://www.w3.org/TR/WCAG22/ "Web Content Accessibility Guidelines (WCAG) 2.2"
