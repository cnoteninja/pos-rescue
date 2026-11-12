# POS Rescue

**Get the lane back open.**

A plain-language troubleshooting guide for store clerks. Pick the symptom,
follow the steps, get the register working again — or get rescue help.

## What it is

A single static web page (`index.html`). No backend, no login, no external
dependencies. It works on a clerk's phone during a rush.

- 17 step-by-step flows: register won't boot, frozen software, cash drawer, stuck drawer, scanner, receipt printer, card reader, reader pairing, chip declines, POS offline, kitchen display, online orders, app after an update, end-of-day batch, end-of-day totals, new-clerk basics, and a 15-minute first-shift walkthrough.
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
