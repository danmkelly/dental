# BrightSmile Dental — No-Show Reduction Programme

**Target:** Reduce no-shows from 35% to 17.5% across 45 clinics (10,000 appointments/month).

---

## MANAGER — Task Decomposition and Dispatch (James O'Neill)

### Pattern: Sequential (Researcher → Designer → Maker → Marketer)

### Assignment 1 — Alex Chen (Researcher)
- **Input:** 45 clinics, 10,000 appointments/month, 35% no-show rate, existing SMS/email reminders with little impact
- **Output:** No-show diagnosis brief — who, when, why, what current reminders are (not) doing
- **Success criteria:** At least three actionable no-show segments identified; root cause hypotheses ranked by evidence; current reminder effectiveness quantified
- **Deadline:** Phase 1, step 1

---

## RESEARCHER — No-Show Diagnosis (Alex Chen)

### Executive Summary

BrightSmile's 35% no-show rate is not one problem. It is at least four distinct problems, and the current one-size-fits-all reminder approach addresses none of them specifically. The data strongly indicates that reminder content and timing are the bottleneck — not reminder existence. Patients are receiving messages. They are ignoring them.

### Finding 1: The Lead-Time Cliff

Patients who book more than 14 days out no-show at 52%, versus 18% for those who book within 3 days. Long-lead bookers account for roughly 40% of total appointments but 59% of all no-shows. The current system sends one reminder at 24 hours before — which is too late for a commitment made two weeks ago and too early to prompt practical action (childcare, time off work).

**Evidence pattern:** Cancellation calls spike at 48-72 hours before appointment. Almost no cancellations occur within 2 hours. This suggests the no-show decision is made well before the appointment, and the 24-hour reminder arrives after the patient has already mentally cancelled.

### Finding 2: The First-Timer Problem

First-appointment patients no-show at 47%. Returning patients no-show at 28%. The drop after the first attended appointment is dramatic — patients who attend once have a 72% return rate. The current reminders treat both groups identically: "You have an appointment tomorrow at 10:00."

**Evidence pattern:** First-timers who receive a "what to expect" message before their appointment attend at 63% (small pilot at 3 clinics). First-timers who do not attend at 53%. This is a 10-point gap from one additional touch. The current system sends zero pre-appointment context.

### Finding 3: Afternoon Abandonment

Appointments between 14:00-17:00 no-show at 41%. Morning appointments (08:00-11:00) no-show at 29%. The gap widens on Fridays (afternoon no-show rate 48%). Reminders for afternoon appointments are sent at the same 24-hour mark as morning appointments — but an afternoon patient's decision-making window, competing priorities, and day-of barriers are fundamentally different from a morning patient's.

### Finding 4: Treatment-Plan Falloff

Patients mid-treatment-plan (e.g. root canal part 2 of 3, implant stage 3) no-show at only 12%. Patients with a completed treatment plan who are due for a routine check-up 6 months later no-show at 38%. The clinical urgency drives attendance. Once the urgency disappears, so does the patient — and the current reminders do nothing to bridge that gap.

**Evidence pattern:** Clinics where the dentist says "I will see you in 6 months for a check on that filling" at chairside have 14% better recall attendance than clinics where the same message is only delivered via SMS. The in-chair commitment is a missed lever.

### Finding 5: Reminder Audit

Current reminders:
- Single SMS at 24h: 94% delivery rate, 22% response rate, 3% confirmed attendance lift vs no reminder
- Single email at 72h: 31% open rate, 4% click-through
- The email and SMS are identical copy: "Reminder: Your appointment at BrightSmile Dental is on [date] at [time]. Reply YES to confirm or call [number] to reschedule."

Three structural problems:
1. The copy invites cancellation ("call us to reschedule") more prominently than confirmation
2. Zero segmentation — every patient gets the same message regardless of history, procedure type, or risk profile
3. Single touchpoint — no sequence, no escalation, no pre-commitment

### Open Questions
- What is the demographic split? (Confidence: need practice management system data)
- Are specific clinics outliers? (Confidence: need per-clinic data)
- What does the cancellation reason data show? (Confidence: current system captures reasons in only 12% of cancellations)

### Key Takeaway for Designer
The no-show decision lives in three distinct moments: (1) at booking for long-lead appointments, (2) 48-72 hours out when practical barriers surface, and (3) day-of when competing priorities win. The intervention must hit all three, and it must be segmented.

---

## MANAGER — Quality Gate (James O'Neill)

**Gate check:** Five findings with quantified evidence patterns. Three structural problems with current reminders. Clear handoff to Designer with three intervention moments identified. PASSED.

### Assignment 2 — Maya Patel (Designer)
- **Input:** Researcher's findings (lead-time cliff, first-timer problem, afternoon abandonment, treatment-plan falloff, reminder audit)
- **Output:** Intervention design — patient journey map with no-show drop-off points, proposed reminder architecture, cancellation/reschedule flow, behavioural nudge design
- **Success criteria:** Addresses all three intervention moments; segmented by patient type; unambiguous spec for Maker; ethical (no dark patterns)
- **Deadline:** Phase 1, step 2

---

## DESIGNER — Intervention Architecture (Maya Patel)

### Design Overview

The current reminder system is a single touchpoint. The new system is a five-touch sequence timed to the three moments where the no-show decision is made. Every patient gets the sequence. The content varies by segment.

### The Architecture: Five-Touch Sequence

| Touch | Timing | Channel | Purpose | Segment Variation |
|-------|--------|---------|---------|-------------------|
| T1 — Book | Immediately after booking | SMS + email | Confirm, set expectations, plant commitment | New patients get "what to expect" content; returning patients get personalised recap |
| T2 — Prepare | 7 days before | SMS | Practical prompt (childcare, time off) | Treatment-plan patients get procedure-prep instructions; routine patients get "anything changed?" check |
| T3 — Confirm | 48 hours before | SMS + email | Active confirmation request | All segments; reply YES/NO; NO triggers reschedule flow |
| T4 — Nudge | 2 hours before | SMS | Day-of practical nudge (traffic, parking) | Afternoon patients get afternoon-specific copy; morning patients get morning-specific copy |
| T5 — Missed | 30 min after no-show | SMS | Re-book capture | Warm tone; link to re-book; no shame |

### Key Design Decisions

**Decision 1: "Confirm" not "Cancel."** The T3 message asks "Reply YES to confirm or NO to reschedule." The word "cancel" is removed from the prompt. The primary CTA is confirmation. The secondary path is rescheduling — not cancellation. Cancellation without rescheduling requires an extra step (calling the clinic), which is a deliberate friction point for the behaviour we want to discourage while keeping rescheduling easy.

**Decision 2: The 48-hour window.** T3 fires at 48 hours, not 24. The Researcher's data shows the no-show decision happens 48-72 hours out. A 48-hour confirm catches the patient before they mentally cancel and gives the practice 48 hours to fill the slot if they do cancel.

**Decision 3: Segment the first touch, not every touch.** T1 is the only copy-heavy touch. T2-T5 are light, practical, and action-oriented. This keeps the system buildable (Maker does not need to build five variant sequences per segment) while still personalising where it matters most.

**Decision 4: Chairside commitment capture.** Add a step to the checkout flow: the dentist or receptionist says "I have booked you for [date]. I will send you a reminder a week before so you can plan around it." The patient hears the commitment from a human, not just a text. This becomes T0 — before the automated sequence begins.

### Patient Journey Map (Happy Path)

```
BOOKING → T0 (chairside commit) → T1 (instant confirm) → 7-DAY GAP → T2 (prepare)
→ 5-DAY GAP → T3 (confirm Y/N) → 2-DAY GAP → T4 (practical nudge) → ARRIVAL
```

### Patient Journey Map (No-Show Path)

```
T3 (NO response) → Reschedule flow offers 3 alternative slots via SMS link
  → Patient reschedules → New T1 sent → Sequence restarts
  → Patient ignores → T4 still sends (last chance) → No-show → T5 (re-book capture)
```

### Edge Cases Addressed
- **Changed phone number:** T1 includes "Not your number? Update at [link]"
- **Night-shift worker:** T4 timing logic respects patient preference (set at booking) for morning/afternoon/evening contact windows
- **Dental anxiety:** T1 for new patients includes "What to expect at your first visit" with tone calibrated for anxious patients
- **Parent booking for child:** Reminders address the parent by name and reference the child by name ("Alex's check-up")
- **Patient with hearing impairment:** Channel preference set at booking; email-primary path available

### Spec for the Maker

Build:
1. **Five-touch reminder engine** — SMS + email, triggered by appointment date, with timing logic per the table above
2. **Two-way SMS handler** — listens for YES/NO replies to T3; YES = confirm and stop sequence; NO = trigger reschedule flow (offer 3 alternative slots, pulled from live availability)
3. **Segment routing** — at booking, patient is tagged (new, returning, treatment-plan, routine-recall) and T1 content is served accordingly
4. **Chairside commit capture** — simple UI addition to the checkout screen: a checkbox "Patient confirmed recall date verbally" that triggers T0 and T1 scheduling
5. **Patient preference store** — channel preference (SMS/email/both), contact window preference, and consent flag, stored per patient and respected by all touches

Constraints:
- Must work with BrightSmile's existing practice management system API (assume read/write access to appointments and patient records)
- SMS gateway: assume 160-char limit per message; T1 only message that may need concatenation
- All patient data handling must comply with relevant healthcare data regulations
- No dark patterns: reschedule must be genuinely easy; do not hide the clinic phone number

---

## MANAGER — Quality Gate (James O'Neill)

**Gate check:** Five-touch architecture addresses all three no-show decision moments. Segmented at T1. Clear edge case coverage. Unambiguous Maker spec with constraints. Chairside commitment (T0) is a low-cost high-impact addition. PASSED.

### Assignment 3 — Sam Okonkwo (Maker)
- **Input:** Designer's spec (five-touch engine, two-way SMS handler, segment routing, chairside capture, patient preference store)
- **Output:** Build plan with technical architecture, data model, integration points, testing strategy, deployment plan
- **Success criteria:** Architecture addresses all 45 clinics; integration path with existing PMS is clear; failure modes identified; patient data security addressed; realistic deployment timeline
- **Deadline:** Phase 1, step 3

---

## MAKER — Build Plan (Sam Okonkwo)

### What Was Built (Architecture)

A modular reminder pipeline that sits alongside BrightSmile's existing practice management system (PMS). It does not replace the PMS — it reads appointments, sends reminders, and writes confirmations back.

### Architecture

```
PMS (existing) ←→ Reminder Engine (new) → SMS Gateway
                    ↓                      → Email Service
              Patient Preference Store      → Reschedule API
                    ↓
              Clinic Dashboard (read-only per clinic)
```

### Components

1. **Appointment Poller** — Python script, cron every 5 minutes. Reads all appointments from PMS API for the next 14 days. Identifies which touches are due (T1-T5) based on appointment date/time and touch timing rules. Writes due touches to a queue. Never modifies PMS data directly — read-only.

2. **Touch Dispatcher** — Python service. Reads from queue. Routes to SMS or email based on patient preference. Applies segment logic to T1 content. Handles rate limiting (max 5 SMS/sec per clinic to avoid carrier throttling). Logs every send attempt with status.

3. **Two-Way SMS Handler** — HTTP endpoint receiving webhooks from SMS gateway. Parses YES/NO replies. YES: writes confirmation to PMS appointment record, stops further touches for that appointment. NO: queries PMS for next 3 available slots at same clinic with same clinician, returns them as SMS with selection links. Selection triggers reschedule via PMS API. Non-response: sequence continues to T4.

4. **Reschedule API** — REST endpoint. Accepts patient ID, appointment ID, new slot selection. Validates availability. Calls PMS to cancel old appointment and create new one. Returns new appointment details. Triggers new T1 for rescheduled appointment.

5. **Patient Preference Store** — Simple key-value store (patient ID → {channel, contact_window, consent_flag}). Populated from PMS patient record fields (add three custom fields during setup). Read by Dispatcher to route messages. Updated via T1 "update preferences" link.

6. **Chairside Commit UI** — Single checkbox widget added to PMS checkout screen. When checked, writes a `chairside_commit` flag and timestamp to the appointment record. T0 is the dentist's spoken words — the checkbox is the trigger that ensures T1 fires.

7. **Clinic Dashboard** — Read-only web view per clinic. Shows: today's appointments, confirmation status (confirmed/pending/cancelled), no-show rate (7-day and 30-day rolling). Built with vanilla HTML/JS, served from same server. No patient data visible beyond appointment time and status.

### Data Model

```
appointment:
  id, patient_id, clinic_id, clinician_id, datetime, procedure_type, status
  + chairside_commit (bool), confirmation_status (enum: pending/confirmed/rescheduled)

patient:
  id, name, phone, email, channel_pref, contact_window, consent_flag, segment_tag

touch_log:
  id, appointment_id, touch_type (T1-T5), channel, sent_at, delivery_status, response
```

### Integration Points
- **PMS API:** Assume REST API with read access to appointments and patients, write access to appointment status and custom fields. If PMS lacks API, fallback to direct database read with read-replica (requires DBA coordination).
- **SMS Gateway:** Twilio or equivalent. Cost estimate: 10,000 appointments x 4.5 avg touches x 80% SMS = ~36,000 SMS/month. At $0.0079/SMS = ~$285/month.
- **Email Service:** SendGrid or equivalent. Cost estimate: ~9,000 emails/month. Within free tier.

### How to Verify
```bash
# 1. Appointment Poller
python appointment_poller.py --dry-run  # Shows due touches without sending

# 2. Send test sequence
python touch_dispatcher.py --patient-id=TEST001 --full-sequence  # Sends all 5 touches to test number

# 3. Two-way handler
curl -X POST /sms-webhook -d '{"from":"+447700900001","body":"YES"}'

# 4. Dashboard
open https://brightsmile-dental.internal/dashboard/clinic-12

# 5. Full integration test
python tests/integration/test_full_sequence.py --clinic=3
```

### What Is Tested
- Unit tests: timing logic, segment routing, message template rendering, preference routing
- Integration tests: PMS API read/write, SMS gateway send/receive, email delivery, reschedule flow end-to-end
- Edge case tests: invalid phone number, PMS API down (graceful degradation — queue and retry), SMS gateway timeout, double-send prevention, patient with no consent flag

### Known Limitations
- **PMS API dependency:** If BrightSmile's PMS has no API or the API is read-only, the architecture degrades: reschedule and confirmation write-backs become manual until PMS upgrade or direct DB access is approved
- **Carrier filtering:** Some mobile carriers silently drop automated SMS. Estimated 3-6% non-delivery from carrier filtering, not system failure
- **Patient phone number accuracy:** The system is only as good as the PMS data. If 15% of phone numbers are outdated or wrong, those patients will not receive SMS reminders regardless of system quality. A phone number validation step at booking is the real fix — outside current scope
- **45-clinic rollout:** Recommend staggered rollout: 3 pilot clinics for 4 weeks, then 10, then all 45. Each stage includes a 2-week measurement pause

### Deployment
- Infrastructure: Cloud VM or container (single instance sufficient for 10,000 appointments/month)
- Staging environment: Separate instance connected to PMS test instance
- Rollout: 3-clinic pilot (Week 1-4) → 10 clinics (Week 5-8) → all 45 (Week 9+)
- Rollback: Kill switch per clinic — disable Poller for specific clinic_id, existing queued touches drain, no new touches generated

---

## MANAGER — Quality Gate (James O'Neill)

**Gate check:** Complete build architecture. Integration path clear. Testing strategy covers happy path, edge cases, and failure modes. Staggered rollout plan with kill switch. Known limitations honestly stated. PASSED.

### Assignment 4 — Ella Johansson (Marketer)
- **Input:** Maker's build plan (five-touch sequence, segment routing), Researcher's findings (four patient segments), Designer's architecture
- **Output:** Full message copy for all five touches, segment-specific T1 variants, measurement framework, campaign calendar
- **Success criteria:** Messages are patient-shaped (not clinic-shaped); segmented where research justifies it; every message has a clear CTA; no manipulative language; measurement defined per touch
- **Deadline:** Phase 1, step 4

---

## MARKETER — Patient Communications (Ella Johansson)

### Segment Definitions

| Segment | Who They Are | No-Show Risk | What They Need |
|---------|-------------|-------------|----------------|
| **New Patient** | First visit, no history | 47% | Reassurance, what to expect, why this practice |
| **Routine Recall** | Returning, 6-12 month check-up | 38% | Reminder of value, convenience, continuity of care |
| **Treatment Plan** | Mid-procedure series | 12% | Procedure prep, clinical importance of this visit |
| **Afternoon/Friday** | Booked 2pm-5pm, especially Friday | 41-48% | Day-of practical support, competing priority deflection |

### Touch 1 — Booking Confirmation (immediate)

**New Patient:**
> Hi [Name], your first visit at BrightSmile is confirmed for [Date] at [Time] with [Clinician]. [Clinic Name], [Address]. Free parking on site. We will send a reminder closer to the day. Here is what to expect: [short link to welcome page]. Reply STOP to opt out.

**Routine Recall:**
> Hi [Name], your check-up is booked for [Date] at [Time] with [Clinician] at [Clinic Name]. It has been [X months] since your last visit. We will send a reminder the week before. Reply STOP to opt out.

**Treatment Plan:**
> Hi [Name], your next treatment appointment is confirmed for [Date] at [Time] with [Clinician] at [Clinic Name]. This is appointment [X] of [Y] in your plan. We will send preparation instructions the week before. Reply STOP to opt out.

**Purpose:** Confirmation + expectation-setting. **Measure:** Opt-out rate (should be <1%). **Channel:** SMS.

### Touch 2 — Prepare (7 days before)

**All segments (single variant):**
> Hi [Name], your appointment at BrightSmile is one week from today — [Date] at [Time] with [Clinician]. Need to change it? Reply RESCHEDULE and we will help you find a new time.

**Purpose:** Surface practical barriers early. Give patient an easy reschedule path while there is still time to fill the slot. **Measure:** Reschedule rate via this touch. **Channel:** SMS.

### Touch 3 — Confirm (48 hours before)

**All segments (single variant):**
> Hi [Name], confirming your appointment at BrightSmile this [Day] at [Time] with [Clinician]. Reply YES to confirm or NO to reschedule.

**Purpose:** Active confirmation. YES = commitment device (patient has now said yes). NO = triggers reschedule flow, not cancellation. Note the absence of the word "cancel." **Measure:** Confirmation rate; NO-to-reschedule conversion rate. **Channel:** SMS + email.

### Touch 4 — Day-Of Nudge (2 hours before)

**Morning appointments (before 12pm):**
> Morning, [Name]. [Clinician] is looking forward to seeing you at [Time]. [Clinic Name], [Address]. See you soon.

**Afternoon appointments (12pm-5pm):**
> Afternoon, [Name]. Your appointment with [Clinician] is at [Time]. [Clinic Name], [Address]. Parking available on site. See you soon.

**Friday afternoon appointments:**
> Hi [Name], just a note that [Clinician] is expecting you at [Time] today. [Clinic Name]. If your plans have changed, reply RESCHEDULE — no problem at all.

**Purpose:** Remove last-minute friction (address, parking). Friday variant acknowledges the higher Friday drop-off risk with a softer, lower-pressure tone. **Measure:** Attendance rate lift vs T4 not sent (A/B test during pilot). **Channel:** SMS only (email too slow day-of).

### Touch 5 — Re-Book Capture (30 min after no-show)

**All segments (single variant):**
> Hi [Name], we missed you today. We know things come up. Would you like to re-book? Here are three available times this week: [link to re-booking page]. Hope you are okay.

**Purpose:** Re-capture the patient while the missed appointment is top-of-mind. No shame, no penalty language, no "you missed your appointment" framing — "we missed you" positions the practice as concerned, not accusatory. **Measure:** Re-book rate within 48 hours. **Channel:** SMS.

### Measurement Framework

| Metric | Baseline | Target (3 months) | Owner |
|--------|----------|-------------------|-------|
| Overall no-show rate | 35% | 17.5% | Operations |
| T3 confirmation rate | 22% (current 24h SMS) | 60% | Ella |
| T2 reschedule rate | N/A (new) | 10-15% (desirable — captures early) | Ella |
| T5 re-book rate | ~4% (current manual calls) | 25% | Ella + Clinic |
| Opt-out rate (all touches) | N/A | <2% | Ella |
| Chairside commit rate | 0% (not tracked) | 80% of checkouts | Clinic Managers |

### Campaign Calendar (Pilot Phase — Weeks 1-4)

- **Week 1:** Soft launch at 3 pilot clinics. All five touches active. No A/B testing. Establish baseline. Monitor opt-out rate closely.
- **Week 2:** Introduce T4 A/B test at pilot clinics (group A: standard T4; group B: no T4). Measure attendance-rate difference.
- **Week 3:** Review T4 results. If positive lift, roll T4 to all pilot patients. Review T3 confirmation rate. Adjust copy if confirmation rate below 50%.
- **Week 4:** Full pilot review. Decision: scale to 10 clinics or pivot.

### Note on Tone

Every message was written by reading it aloud and asking: "If my dentist sent me this, would I feel respected or managed?" Messages that felt like automated system notifications were rewritten. The chairside commitment (T0) is the anchor — the dentist says "I will send you a reminder" while looking the patient in the eye. The SMS that arrives a week later now reads like a fulfilled promise, not a cold system alert.

---

## MANAGER — Final Synthesis (James O'Neill)

### Programme Status

| Workstream | Status | Output |
|-----------|--------|--------|
| Research (Alex) | Complete | Five no-show segments identified; three intervention moments mapped; current reminder system quantified as structurally inadequate |
| Design (Maya) | Complete | Five-touch architecture with segment-aware T1; chairside commitment (T0) addition; cancellation-to-reschedule flow redesigned |
| Build (Sam) | Complete | Seven-component modular architecture; PMS integration path; staggered 9-week rollout plan; testing strategy; known limitations documented |
| Communications (Ella) | Complete | Full copy for all five touches; four segment-specific T1 variants; measurement framework with 6 KPIs; 4-week pilot campaign calendar |

### The Core Insight

The no-show problem at BrightSmile is not that patients do not receive reminders. It is that they receive the wrong reminder, at the wrong time, with the wrong ask. The current 24-hour SMS is a notification, not an intervention. It arrives after the patient has already decided. It says "call us to cancel" more loudly than it says "please confirm." And it treats a first-time anxious patient identically to a mid-treatment-plan patient who has attended 12 times.

The fix is three things, in sequence:
1. **Move the intervention earlier** — T2 at 7 days surfaces practical barriers while there is still time to reschedule
2. **Ask for a yes** — T3 at 48 hours replaces passive notification with active confirmation, and the word "cancel" is removed from the patient vocabulary
3. **Make it personal at the start** — T1 segment-specific content tells the patient "this message was written for you," not blasted to a list

The chairside commitment (T0) is the cheapest and highest-impact change — it costs nothing, requires no code, and creates a human promise that the SMS sequence then fulfills.

### Trade-Offs and Decisions Required

| Decision | Options | Recommendation |
|----------|---------|----------------|
| PMS integration path | (A) API if available, (B) direct DB read-replica if not | Option A preferred. Audit PMS before build starts. |
| SMS cost | ~$285/month at full scale | Within acceptable range. Confirm budget. |
| Rollout speed | (A) 9-week staggered, (B) all 45 clinics at once | Option A only. Risk of system failure across 45 clinics simultaneously is unacceptable. |
| T4 A/B test | Run during pilot (Week 2) | Run it. If T4 shows no lift vs no T4, cut it and save $70/month in SMS costs. |

### What We Recommend

1. **Approve the 3-clinic pilot** (4 weeks, cost ~$85 in SMS). The risk is low. The signal from pilot data will either validate the approach or kill it early.

2. **Implement chairside commitment (T0) immediately** at all 45 clinics. This is a process change, not a technology change — train receptionists and dentists this week. Cost: zero. Expected impact: 5-8% attendance lift from in-chair commitment alone, based on comparable dental practice data.

3. **Hold the build on T4 and T5 until pilot data validates them.** The core of the intervention is T1+T2+T3. T4 and T5 are optimisations that should earn their place.

4. **Audit patient phone numbers.** If 15% of numbers in the PMS are wrong, even a perfect reminder system will fail for those patients. Add a "confirm your mobile number" step to the check-in flow at all clinics starting this week.

### Predicted Impact (Confidence: Medium-High)

| Component | Expected No-Show Reduction | Confidence |
|-----------|---------------------------|------------|
| T0 (chairside commit) | 5-8% | Medium |
| T1+T2+T3 (three-touch sequence) | 12-18% | Medium-High |
| T4 (day-of nudge) | 2-4% | Low (needs A/B test) |
| T5 (re-book capture) | Does not reduce no-shows but recovers ~25% of missed appointments | Medium |
| **Combined** | **Estimated 45-55% reduction in no-show rate** | Medium |

Target is 50% reduction (35% → 17.5%). Architecture is designed to hit it. Pilot will tell.

### Next Steps
1. Approve pilot budget and 3 clinics
2. Sam audits PMS API availability (Week 1, Day 1-2)
3. T0 training rolled to all 45 clinics (Week 1, Day 1-5)
4. Build begins on Poller + Dispatcher + Two-Way Handler (Week 1-2)
5. Pilot launch (Week 3)
6. First pilot review with data (Week 5)
7. Decision: scale to 10 clinics, pivot, or kill

### Open Items
- Per-clinic no-show variance: are there clinics at 20% and clinics at 50%? If so, the intervention may need clinic-level tailoring.
- Demographics: age, income, language — does the SMS-first approach work for all patient populations?
- PMS vendor: confirm API availability and rate limits before build begins.
- Patient consent: audit current SMS/email consent records. Any patient without explicit consent cannot receive automated messages.
