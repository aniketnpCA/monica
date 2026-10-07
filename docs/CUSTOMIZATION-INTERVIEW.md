# Monica customization interview

Baseline: Monica v4.1.2 (`4.x`), free/open-source, self-hosted. This is a discovery guide, not an approved feature list or deployment plan. Record answers in `docs/INTERVIEW-RESPONSES.md` (create locally or in a private location); do **not** put names, contact records, credentials, or private relationship notes in this public fork.

## How we will work

Ask one section at a time. For each requested change, capture: **current behavior → desired behavior → example using dummy data → priority (must/should/later) → acceptance test**. Mark unclear answers as open questions. Separate configuration from code changes and verify each proposed feature against v4.1.2 before committing to implement it. No Proxmox changes or personal-data imports until deployment scope and backups are approved.

## 1. Outcomes and people

1. What are the top three things Monica should help you remember or do each week?
2. Who will use it (just you, family members, collaborators)? Should anyone have separate accounts or shared access?
3. Which existing tools hold your contacts and relationship history (iPhone/iCloud, Google Contacts, other apps, CSV)? Which is authoritative for each field?
4. What data must never be stored in Monica or sent to third-party services?

## 2. Contacts and relationships

5. Which fields should a person record have? Which are mandatory, hidden, or searchable? Provide fictitious examples.
6. Which relationships matter (family, friends, colleagues, households, organizations), and how should they appear?
7. How should tags, groups, favorites, duplicates, archived contacts, and deceased contacts work?
8. Should changes in iPhone Contacts propagate into Monica, from Monica back to iPhone, both directions, or neither? What should happen on conflicts and deletions?

## 3. Interaction and follow-up workflow

9. What do you want to log (calls, messages, meetings, gifts, travel, notes)? How fast should entry from an iPhone take?
10. Which dates or intervals trigger follow-ups? What notification channel and quiet hours should apply?
11. Should messages/calls be logged manually, imported from a supported source, or automated? What permissions are acceptable? iOS restrictions must be checked before promising automatic capture.
12. Which existing stable features (debts, gifts, journal, reminders, tasks, API) need changing, and what specific friction exists today?

## 4. iPhone access and sync — choose separately

13. Is a mobile-friendly web app added to the Home Screen sufficient, or do you require a native iOS app? What must work offline?
14. Does “sync” mean contact records appearing in Apple Contacts, Monica data visible in Safari, two-way editing, calendars/reminders, or all of these?
15. For two-way contact sync: should we investigate CardDAV/bridge integration, or keep iCloud/Google Contacts as source of truth with one-way import? Define field mapping, duplicate rules, deletion policy, and sync interval.
16. Will access be LAN-only, VPN/Tailscale, or HTTPS over the public internet? Should iOS access require MFA? Decide before deployment; do not expose Monica directly without an access plan.
17. What is the minimum iPhone test: add/edit a contact, log an interaction, receive a reminder, recover from offline edits? Specify expected latency and conflict behavior.

## 5. Interface and accessibility

18. Which screens are most important (dashboard, contact sheet, search, quick-add)? Describe the ideal first screen.
19. What visual preferences matter (density, colors, typography, dark mode, one-handed use, accessibility)? Provide examples or screenshots if useful.
20. What should require fewer taps, and what should remain deliberately manual/private?

## 6. Proxmox operations (planning only)

21. Preferred isolation: dedicated LXC or VM? Docker inside a VM/LXC or direct installation? What resources, storage, domain, and network segment are available?
22. Where should database, uploads, secrets, and backups live? What backup frequency, retention, off-host copy, and restore test are required?
23. Who can administer it? What authentication, update window, monitoring, and alerting are needed?
24. Are there existing reverse proxy, TLS, VPN, email delivery, and DNS services to reuse? Record service names, not secrets, in public issues.

## 7. Prioritization and handoff

25. Rank the first three changes by impact. For each, specify a concrete acceptance test and any migration dependency.
26. What would make the first release usable without iPhone two-way sync? What is non-negotiable?
27. Confirm where private responses will be stored, who may read them, and whether sanitized GitHub issues can be created.

## Decision record template (one per change)

- ID / title:
- Requester and date:
- Problem / current behavior:
- Desired behavior / fictitious example:
- Data sensitivity and source of truth:
- Priority: must / should / later
- Approach: configuration / integration / code / research needed
- iPhone behavior and offline/conflict/deletion rules:
- Proxmox/network/backup implications:
- Acceptance test:
- Open questions / decision owner:
- Approved for implementation: no (until explicitly confirmed)

## First interview pass

Begin with questions 1–4, then 13–17. This establishes the goal and what “iPhone sync” means before selecting integrations or changing the data model.
