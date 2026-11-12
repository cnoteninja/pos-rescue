# POS Rescue

**Get the lane back open.**

A plain-language troubleshooting guide for store clerks. Pick the symptom,
follow the steps, get the register working again — or get rescue help.

## What it is

A single static web page (`index.html`). No backend, no login, no external
dependencies — except one optional, user-tapped live check (see below).
It works on a clerk's phone during a rush.

- 17 step-by-step flows: register won't boot, frozen software, cash drawer, stuck drawer, scanner, receipt printer, card reader, reader pairing, chip declines, POS offline, kitchen display, online orders, app after an update, end-of-day batch, end-of-day totals, new-clerk basics, and a 15-minute first-shift walkthrough.
- **v3 — Describe it in plain words:** a symptom search box at the top. Type what's wrong ("printer blinking red", "cajón no abre") and it points at the closest fix. Works in English and Spanish, no backend.
- **v3 — Incident log + owner dashboard:** every fix or escalation is logged on the device (localStorage, nothing leaves the phone). The owner dashboard shows this month at a glance — how many problems, how many fixed on the spot, the most common problem, and recent incidents. The monthly "what broke, what we fixed" summary is built from this log.
- **v3 — Rescue tickets:** from the escalation card, open a rescue ticket by text — it sends the rescue line a ticket number (PR-YYMMDD-NNN), the problem, and the time, so it's in the queue even if no one picks up right away. Open tickets live on the owner dashboard with a "Mark fixed" button.
- **v3 — Live outage check:** a "Check live status" button. For Square it reads Square's public status feed live (the only vendor feed a browser page can read directly). For Toast, Clover and Aloha it opens that vendor's own status page. If the check can't run, it says so and links through. It never blocks the guide.
- Vendor picker (Square / Toast / Clover / Aloha / Other) — steps name the system's exact menus where they differ.
- Full Spanish toggle (every flow, step, and button), persisted in localStorage.
- Works offline once saved to the phone's home screen; weekly prevention checklist; response-time promise (answered within 15 minutes, evenings and weekends).
- Each step asks "Did that fix it?" — Yes ends in Fixed, No moves to the next step, and every flow ends in Fixed or the escalation card.
- Safety first: it never tells anyone to open sealed payment hardware,
  handle card details, or share an admin password. Steps that could void a
  warranty or support contract say "Stop — call your vendor."

## Setup

`CONFIG.rescuePhone` at the top of the script is the Google Voice / business
number shown on the escalation card — currently 440-770-8561. The owner's
personal number is never in this file. Tests (`node pos-rescue-test.js`,
local only, never pushed) verify all 17 flows, the vendor picker, the
Spanish toggle, the checklist, and the phone-number guard.

## Serve it

Any static host works. GitHub Pages: enable Pages on this repo (branch:
main, folder: root) and the guide is live at
`https://cnoteninja.github.io/pos-rescue/`.
