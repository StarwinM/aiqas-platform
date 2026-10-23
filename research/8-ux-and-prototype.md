# 8 UX and prototype

8 UX and prototype

Design source: AIQAS 0.1 in Paper — https://app.paper.design/file/01M4N0NETW9ZS7E1S9XRYVX5NA/p-1-0

Three original desktop mockups appear below, followed by five low-fidelity scenario drawings in Section 8.4. Together they show the interface direction and main P0 interactions. They are static designs, not an implemented or user-tested app. Names, dates, counts, XP, and rewards are illustrative. Related task: DEMO-30.

8.1 Events discovery and registration

The student searches/filters the catalog, reviews event summaries and remaining places, and chooses Join Now / RSVP. This supports FR-03 and entry to FR-05. Section 8.4 supplies event details, registration confirmation, full-capacity and unknown-result states.



Figure 4. Events catalog exported from the existing Paper artboard.

8.2 Profile and personal ticket

The student sees their profile and upcoming-event entry pass, illustrating FR-08. XP/rewards are a future direction outside P0. Section 8.4 adds ticket status, cancellation, and invalid-ticket behavior. Verified attendance does not automatically constitute a verified skill.



Figure 5. Profile and entry pass exported from the existing Paper artboard.

8.3 Participant management

The panel shows registration/check-in summaries, participants, attendance statuses, event creation, and export, illustrating FR-04/09/10. Organizers manage only their authorized clubs/events; administrators receive separately granted permissions. Section 8.4 adds publication, validation, QR verification, access rejection, and report output.



Figure 6. Admin Panel exported from the existing Paper artboard. Displayed figures are sample design data.

The added drawings cover student/organizer P0 flows, key success/failure states, and a mobile sequence. Next, review them with the three roles and record revisions, followed by implementation/device testing. Static mockups do not establish usability or complete the implementation/testing parts of DEMO-30.

8.4 P0 scenario mockups and states

Student registration

Open an event with program, location, time zone, deadline, and current seat availability. Successful registration displays explicit confirmation and the owner’s ticket link. A repeated action returns the same booking. This addresses missing availability and unclear registration status in the questionnaire.



Figure 7. Event details and registration confirmation. FR-03, FR-05, FR-06.

Ticket cancellation and exceptions

The owner views a confirmed ticket and confirms cancellation. A cancelled ticket stays visible as “Cancelled — not valid for entry”. A full event reserves no seat. After a connection failure following submission, check server-side booking status before retrying. An empty catalog explains that no events match and offers Clear filters; loading shows progress without implying registration success.



Figure 8. Ticket, cancellation, full event, and unknown request status. FR-05–FR-08.

Organizer publication

Select an authorized club; enter title, start/end time, location, capacity, and deadline. Invalid or missing fields block publication while retaining entered values. The deadline precedes the start. Successful publication opens the event; later cancellation/time changes create notification jobs.



Figure 9. Creation, validation, and publication. FR-02, FR-04, FR-11.

Attendance and reporting

Select the target event, scan a ticket or enter its code. Distinguish saved attendance, already checked in, wrong event, cancelled ticket, and access denied. CSV/PDF separates active registrations, unique attendances, and cancellations. An empty participant list explains that no registrations exist; export failure retains the list and offers retry.



Figure 10. Verification, participant statuses, and reporting. FR-02, FR-09, FR-10.

Mobile scope and administration

Mobile P0 covers discovery, details, registration status, owner ticket, and cancellation. Organizer check-in must also work on a phone; dense reports may use a scrollable table/export. An administrator grants a named user an explicit club/university scope, reviews the change, and receives confirmation. Unauthorized users see access denied without participant data. Role changes are audited.



Figure 11. Mobile event-to-ticket sequence; planned reference viewport 360 px.

Editable SVGs and matching PNGs for Figures 7–11 are in [E3]. Prototype review follows Section 9.4.