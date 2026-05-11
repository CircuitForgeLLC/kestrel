# Kestrel — Government Appointment Booking

> *Part of the Circuit Forge LLC "AI for the tasks you hate most" suite.*

**Status:** Backlog — not yet started. Peregrine must prove the model first.

## What it does

Kestrel monitors appointment availability at government offices — DMV, passport agencies, Social Security offices, USCIS Application Support Centers, courts — and auto-books the moment a slot opens. Sends reminders with a checklist of required documents.

The kestrel hovers perfectly still in the air before diving with precision. That's the metaphor: watch and wait, then strike the instant an appointment opens.

## Why it's hard

Government appointment systems are:
- Chronically overbooked (passport offices, USCIS biometrics)
- Updated sporadically — cancellations open and fill in minutes
- Scattered across different booking systems (Login.gov, agency-specific portals, state DMV sites)
- Unforgiving of missed appointments (back to the queue)

## Core pipeline

```
Configure target agency + deadline urgency
→ Monitor booking portal (polling + change detection)
→ Alert when slot opens → Auto-book if within preferences
→ Send confirmation + document checklist reminder
```

## Key differentiators vs. Peregrine

- Time-critical real-time monitoring vs. batch job discovery
- Booking automation: Playwright form-fill on detected availability
- Document checklist generator: per-appointment-type required docs
- Multi-office monitoring: find the closest available slot across locations

## Product code (license key)

`CFG-KSTR-XXXX-XXXX-XXXX`

## Tech notes

- Shared `circuitforge-core` scaffold
- Appointment monitor: background daemon with configurable poll interval
- Portal adapters: Login.gov, USCIS, individual state DMV systems
- Playwright for form submission on slot detection
- Push notifications: ntfy.sh / Pushover / email alert on slot found
