# Thusa Mosotho ka Litokomane

**Thusa Citizen Helpline** is a Sesotho and English helpline prototype for Lesotho's Home Affairs services: national IDs, passports, and birth and death registration. It tells people what to bring, tracks their application and lets them book a visit, so they don't make wasted trips to a district office.

This repository holds the interactive prototype and the pilot proposal behind it.

> ⚠️ **Prototype with fictional data.** Thusa is not an official government service. Requirements, fees and office details in the demo are placeholders, not official Home Affairs information. Application numbers, names and records are made up, and no SMS is sent.

---

## Live demo

**▶ [Open the Thusa Citizen Helpline prototype](https://claude.ai/artifact/6hQo2ZGvc8YSaffhWCJFzH)**

The demo runs on claude.ai. Sign in to get live AI answers, voice input and read-aloud, and data that's shared between viewers.

---

## What's in this repository

| File | What it is |
|---|---|
| [`Thusa Citizen Helpline.html`](Thusa%20Citizen%20Helpline.html) | The interactive prototype, a single self-contained HTML page |
| [`Proposal - Sesotho Citizen Services Assistant.pdf`](Proposal%20-%20Sesotho%20Citizen%20Services%20Assistant.pdf) | The 6-page pilot proposal: problem, design, phasing, budget, risks, success measures and next steps |
| `README.md` | This file |

---

## The problem

Home Affairs backlogs push people into long queues and repeat trips, and many of them travel in from rural districts. In April 2026 about 50,000 passport applications were pending. Some district offices could issue as few as 10 passports a day. The national ID backlog grew from 30,000 in 2013 to 110,000 by 2024.

AI can't print documents. It can stop people travelling for nothing, cut incomplete applications and take routine status questions off counter staff.

---

## What the prototype shows

The page has three views, chosen with the tabs at the top.

### 1. Citizen's phone
A simulated phone with the three channels a citizen would use:

- **Chat (WhatsApp-style).** Ask in Sesotho or English. Claude answers only from a small sample knowledge base. It can look up an application by receipt number, find free visit times and book a visit.
- **USSD `*123#`.** A numbered menu that works on any phone with no data: check status, see what to bring, book a visit or leave a message for an agent.
- **Voice line.** Speak a question and hear the answer read aloud. Where speech input isn't available you can type instead.

A side panel, **What the helpline did**, shows each lookup, booking and knowledge source behind an answer.

### 2. Office dashboard
The view for Home Affairs staff at the three pilot offices (Maseru, Mokhotlong and Qacha's Nek):

- Headline numbers: conversations, the share of status checks answered without a visit (target 60%), documents ready but not collected, visits booked and hand-offs to a person
- An applications table where staff update status. Marking an application **Ready** queues a simulated "ready to collect" SMS, translated into Sesotho when the applicant prefers it.
- Booked visits against each office's weekly capacity
- A chart of what people ask about
- **Daily summary:** Claude drafts a short note for the office manager from the day's activity

### 3. Record digitising
Upload a scanned paper register page (a fictional sample is included). Claude reads the handwriting and fills in the fields, flagging any field it's unsure of. A clerk checks every field before the record is saved.

### Try these

- `Is my passport ready? My number is P-2026-104233`
- `Ke hloka eng ho nchafatsa passport?` *(Sesotho: what do I need to renew a passport?)*
- `Book me a visit in Mokhotlong for a national ID`
- `I lost my ID card, what should I do?`

Other fictional application numbers to try: `ID-2026-058812` (ready), `P-2026-102994` (needs more documents), `B-2026-021145` (ready).

---

## How it works

The prototype is one HTML file with inline CSS and JavaScript. It has no build step and no dependencies beyond Google Fonts.

When the page is opened as a claude.ai artifact, it uses these runtime capabilities:

| Capability | Used for |
|---|---|
| `sample` (with images) | Claude's answers, tool calls (lookup, free times, booking), SMS translation, the daily summary and reading register images |
| `db` + `user` | Shared applications, bookings, conversations, SMS outbox and saved records |
| `dictation` | Speech input on the chat and voice line |
| `tts` | Reading answers aloud |

Every capability is optional. If you open the HTML file directly in a browser, the layout, tabs and USSD menus still work. Live AI answers, voice and shared data show as unavailable.

**Design rules built into the assistant:**

- It answers only from an approved knowledge base and never invents fees, rules or dates
- It never asks for an ID number, address or other personal details. The receipt number is enough to check status.
- It never decides who qualifies for a document and holds no biometric data
- Complaints and hard cases go to a human agent

---

## The pilot proposal at a glance

| | |
|---|---|
| **Lead ministry** | Home Affairs, with the Ministry of Public Service and MICSTI |
| **Channels** | Toll-free voice line, SMS, USSD and WhatsApp |
| **Where** | Maseru plus two rural district offices chosen with Home Affairs |
| **Duration** | 18 months, with a stop-or-scale review at month 9 |
| **Cost** | US$583,000 to US$1.1 million (planning estimate, including 10% contingency) |
| **Headline target** | 60% of status questions answered without an office visit |

**Success measures by month 18:** avoidable repeat visits halved, applications rejected for missing documents down 30%, at least 90% of ready documents triggering an SMS, and user satisfaction of 4 out of 5 or higher.

**Safeguards:** a data protection impact assessment before launch, minimal data kept in Lesotho, no biometrics, and open-source code owned by government. Engineers from the National University of Lesotho and local firms build alongside any vendor.

The full rationale, budget lines, risks and funding partners are in the [proposal PDF](Proposal%20-%20Sesotho%20Citizen%20Services%20Assistant.pdf).

---

## Status

This is a concept prototype that supports a proposal to the Ministry of Home Affairs. Proposed next steps are to brief the Principal Secretary for Home Affairs and MICSTI's AI strategy team, agree the pilot offices, check what the passport, ID and civil registration systems can share, and turn the proposal into a funder concept note.

---

*Author: Palo Moshoeshoe*
