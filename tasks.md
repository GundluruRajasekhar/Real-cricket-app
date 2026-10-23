# Tasks: Cricket Event OS

## Done in the prototype (`index.html`)
- [x] 13-block seat map and 200-seat section view
- [x] Checkout with name and email checks, test-mode payment, signed ticket token
- [x] Gate scanner: valid, duplicate and tampered tokens handled; gate assigned by category
- [x] Analytics: occupancy, revenue by category, signed revenue against plan
- [x] Sponsor and broadcast pipeline with stage odds
- [x] Gate queue sensors (simulated) and incident log
- [x] Six agents with approve-before-action and action log
- [x] Rule-based ticket assistant
- [x] Keyboard-usable controls, labels, visible focus, mobile layout

## Phase 1: Backend foundation (weeks 1 to 3)
- [ ] Create repository with `frontend/`, `backend/`, `db/`
- [ ] PostgreSQL schema: events, blocks, seats, bookings, tickets, scans, deals, incidents, agent_actions
- [ ] Seed 50,000 seats across the 13 blocks
- [ ] REST API: list blocks and seats, hold seats, create booking
- [ ] Seat hold with expiry; unique constraint so a seat sells once
- [ ] Email OTP login for fans; role-based login for staff

## Phase 2: Payments and tickets (weeks 3 to 5)
- [ ] Integrate a payment gateway in test mode
- [ ] Issue tickets only after the payment webhook is verified
- [ ] Server-side token signing with a private key
- [ ] Real QR code generation and email delivery
- [ ] Refund and transfer rules written and shown at checkout

## Phase 3: Gate and operations (weeks 5 to 7)
- [ ] Scanner web app for stewards with offline signed list and sync
- [ ] Live counts over WebSocket
- [ ] Analytics dashboard on real data with charts
- [ ] Sponsor module: contacts, notes, files, status history
- [ ] Incident log with roles and audit trail

## Phase 4: AI agents (weeks 7 to 9)
- [ ] Define tools each agent may use (read data, draft message); no spend or price change
- [ ] Connect agents to a language model
- [ ] Keep human approval for every action; log inputs, proposal, approver
- [ ] Replace the keyword assistant with a model grounded on event data, with human handoff
- [ ] Test agents against sample scenarios, including bad data

## Phase 5: Mobile and accessibility (weeks 9 to 10)
- [ ] Mobile app or PWA: ticket wallet, schedule, live score
- [ ] Screen-reader and keyboard test of the seat map
- [ ] Contrast and zoom checks

## Phase 6: Quality and launch readiness (weeks 10 to 12)
- [ ] Unit tests: pricing, seat holds, token signing
- [ ] End-to-end tests: book, scan, refuse duplicate
- [ ] Load test for launch-day surge (target set with the ticketing partner)
- [ ] Security review: secrets, access roles, input checks, dependency audit
- [ ] Privacy notice; legal review of any face recognition
- [ ] Deploy with monitoring and backups

## Event-side tasks (from the first project)
- [ ] Sign broadcast and sponsor deals before committing player fees
- [ ] Confirm venue, date, teams, permits, insurance, board sanction

## Submission checklist
- [ ] Deployed link
- [ ] Video link
- [ ] MVP link
- [ ] Four files: index.html, requirements.md, readme.md, tasks.md
