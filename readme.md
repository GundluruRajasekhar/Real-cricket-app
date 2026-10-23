# Cricket Event OS: Legends & Stars T20 International Challenge

An event operating system for a 50,000-seat T20 international. One browser app covers seat booking, QR gate checks, analytics, sponsor pipeline, security monitoring, AI-agent proposals and a ticket assistant.

The first version of this project (event site and budget) is in the parent folder. This folder is the platform version.

## Files
| File | Purpose |
|---|---|
| `index.html` | Working prototype, one file, no install |
| `requirements.md` | Requirements, production architecture, acceptance criteria |
| `readme.md` | This file |
| `tasks.md` | Build plan from prototype to production |

## Run it
Open `index.html` in a browser. To publish, upload the folder to GitHub Pages or Vercel.

## What to try (2 minutes)
1. **Book seats:** pick block G1, click 3 seats, enter a name and email, press Pay. You get a ticket with a token.
2. **Gate scan:** pick that ticket, press Scan: valid. Press Scan again: refused as already used. Edit a letter in the token: refused as invalid.
3. **Analytics:** seats sold and revenue have risen.
4. **Sponsors:** set "TV broadcast rights" to Signed and watch the signed broadcast revenue change in Analytics.
5. **Security:** press Simulate entry wave, then log a high-severity incident.
6. **Agents:** press Run all agents, read the proposals, approve some.
7. **Ticket assistant:** ask "How much is a VIP ticket?" or paste your booking ID.

## How the pieces connect
```
Fans -> Seat map & checkout -> Bookings (signed tokens)
                                   |
Gate scanner <---- verifies -------+
     |
     v
Analytics <- Sponsors/Broadcast deals <- Agents read everything, propose actions
                                          Security sensors & incidents ->
                                   People approve -> Action log
```

## Money picture (from the budget, ₹ crore, before tax)
Revenue plan 108.75 (tickets 20.85, sponsorship 35.00, broadcast 50.00, other 2.90). Expenses 93.89 including 10% contingency. Tickets cover about 22% of expenses, so the Sponsors tab and the Analytics "signed revenue" bars matter most before player fees are committed.

## Honest status
| Area | In prototype | Needed for production |
|---|---|---|
| Seat map and booking | Working with simulated sales | Database seat locking |
| Payment | Test-mode screen only | Gateway with webhook confirmation |
| QR verification | Demo signature, sample QR image | Server-side signing, real QR, offline scanner |
| Analytics | Live from in-page data | Real database and charts |
| Sponsors | Stage editing, weighted totals | Contacts, documents, invoices |
| Security | Simulated queues, incident log | Camera and turnstile feeds, legal review of face recognition |
| Agents | Rule-based proposals with approval | Language-model agents with limited tools |
| Assistant | Keyword rules | Language-model assistant |
| Mobile app | Page is responsive | React Native app or PWA |
| Testing | Manual walkthrough above | Unit, end-to-end and load tests |

## About scores
No judge or tool has scored this project, so I cannot give an honest expected score. Judging usually rewards a working demo, a clear problem, sound security, tests and accessibility. The table above shows which of those still need work before a competition submission.

## Disclaimers
Player names, prices and sponsor values are examples and estimates. Real events need contracts, permits, insurance and tax advice.
