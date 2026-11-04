# POS Rescue

**Get the lane back open.**

A plain-language troubleshooting guide for store clerks. Pick the symptom,
follow the steps, get the register working again — or get rescue help.

## What it is

A single static web page (`index.html`). No backend, no login, no external
dependencies. It works on a clerk's phone during a rush.

- 10 step-by-step flows: register won't boot, frozen software, cash drawer,
  scanner, receipt printer, card reader, chip declines, POS offline,
  end-of-day batch, and new-clerk basics.
- Each step asks "Did that fix it?" — Yes ends in Fixed, No moves to the
  next step, and every flow ends in Fixed or the escalation card.
- Safety first: it never tells anyone to open sealed payment hardware,
  handle card details, or share an admin password. Steps that could void a
  warranty or support contract say "Stop — call your vendor."

## Setup

Open `index.html` and set `CONFIG.rescuePhone` at the top of the script to
your Google Voice / business number before sharing the link with stores.
Leave it empty until the service launches — the escalation card will say
the rescue line number is set at launch instead of showing a dead link.

## Serve it

Any static host works. GitHub Pages: enable Pages on this repo (branch:
main, folder: root) and the guide is live at
`https://cnoteninja.github.io/pos-rescue/`.
