# Requirements: Cricket Event OS (Legends & Stars T20 International Challenge)

## 1. Purpose
A software platform that runs a 50,000-seat, fully ticketed T20 international: selling seats, verifying entry, managing sponsors and broadcast deals, watching crowd safety, and using AI agents to propose daily actions. People approve every agent action.

## 2. Two levels of scope
| Level | What it is |
|---|---|
| **Prototype (this folder)** | `index.html`: single-file app in plain HTML, CSS and JavaScript with simulated data. Shows every module working end to end in the browser. |
| **Production target** | React frontend, Node.js (or Spring) backend, PostgreSQL, payment gateway, mobile app. Described below; not built here. |

## 3. Users
| User | Needs |
|---|---|
| Fan | Find seats, pay, receive a ticket, get answers |
| Gate steward | Scan tickets fast, see refusals and the right gate |
| Event director | Live sales, revenue, risks |
| Sponsorship manager | Pipeline by stage and value |
| Security lead | Queue lengths, incidents, alerts |
| Finance lead | Revenue against the 93.89 crore expense plan |

## 4. Functional requirements
### 4.1 Seat map and booking
- FR-1: 13 blocks totalling 50,000 seats: General G1 to G6 (30,000), Premium P1 to P4 (14,000), VIP V1 and V2 (4,500), Corporate Box C1 (1,500).
- FR-2: Price per seat: General ₹800, Premium ₹3,000, VIP ₹15,000, Corporate Box ₹50,000 (planning prices).
- FR-3: Choose up to 10 seats in a block; taken seats cannot be chosen.
- FR-4: Checkout needs a name and valid email; payment goes through a gateway (test mode in the prototype).
- FR-5: Production: seats are held for a short time during payment and sold once, enforced by the database.

### 4.2 QR ticket verification
- FR-6: Every booking gets a unique ID and a signed token shown as a QR code.
- FR-7: Scanning checks the signature, then marks the booking used. A repeat scan is refused.
- FR-8: The scan tells the steward which gate to use by ticket category: General 1 to 4, Premium 5 and 6, VIP 7, Corporate Box 8.
- FR-9: Production: tokens are signed on the server with a private key; scanners work offline using a signed list and sync later.

### 4.3 Analytics dashboard
- FR-10: Seats sold, occupancy, ticket revenue and fans inside, updated on every booking and scan.
- FR-11: Occupancy and revenue by category, and signed revenue against plan (tickets 20.85, sponsorship 35.00, broadcast 50.00 crore).

### 4.4 Sponsor and broadcast management
- FR-12: Nine deals (title, 4 associates, venue, partners, TV, streaming) with target value and stage: Lead, Pitched, Negotiating, Signed.
- FR-13: Weighted pipeline shown against the 35 crore sponsorship and 50 crore broadcast targets.

### 4.5 Security monitoring
- FR-14: Queue length per gate with colour warning above 100 and 150.
- FR-15: Incident log with zone, description and severity.
- FR-16: Production: queue numbers come from turnstile and camera counts; face recognition only where the law allows and with a published privacy notice.

### 4.6 AI agents (human approval required)
- FR-17: Six agents: ticketing, sponsorship, security, fan engagement, broadcast, analytics.
- FR-18: Each reads live data and proposes actions; a person approves each one; approved actions are logged with time.
- FR-19: Production: agents call a language model with approved tools (read data, draft messages); they cannot spend money, change prices or message fans without approval.

### 4.7 Ticket assistant
- FR-20: Answers about prices, availability, gates, schedule, refunds, parking and booking IDs.
- FR-21: Production: language-model assistant grounded on event data, with a handoff to human support.

## 5. Production architecture
| Layer | Choice | Notes |
|---|---|---|
| Frontend | React | Same modules as the prototype |
| API | Node.js (Express or NestJS) or Spring Boot | REST plus WebSocket for live counts |
| Database | PostgreSQL | tables: events, blocks, seats, bookings, tickets, scans, deals, incidents, agent_actions |
| Payments | Razorpay or similar | Server confirms payment by webhook before issuing tickets |
| Auth | Email OTP for fans; role-based for staff | |
| Mobile | React Native or PWA | Ticket wallet, schedule, live score |
| Agents | Server-side jobs calling a language model | Tool access limited; every action logged |
| Hosting | Cloud with autoscaling, CDN | Needed for launch-day surge |

## 6. Non-functional requirements
- Security: payment data never stored on our servers; HTTPS everywhere; signed tokens; role-based staff access; audit log for scans and agent approvals.
- Reliability: no double sale of a seat; gate scan works offline.
- Performance: a scan completes in under 2 seconds; booking page handles launch-day surge (load tested before sales open).
- Accessibility: keyboard use for the seat map, labelled controls, visible focus, sufficient contrast, wheelchair seats offered.
- Privacy: collect only name and email; follow applicable Indian data-protection law.
- Testing: unit tests for pricing, seat locking, token signing; end-to-end tests for booking and scanning; load test before launch.

## 7. Acceptance criteria
- AC-1: Booking 3 seats shows ₹ total = 3 × category price and issues a ticket.
- AC-2: Booked seats show as taken in the seat map and cannot be picked again.
- AC-3: A valid ticket scans once; the second scan is refused.
- AC-4: A tampered token is refused.
- AC-5: Moving a deal to Signed raises signed revenue in Analytics.
- AC-6: A gate queue above 150 appears in the Security agent's proposals.
- AC-7: Agent actions are logged only after Approve is pressed.
- AC-8: Assistant answers a prices question and a booking-ID question correctly.

## 8. Limits of the prototype
- Data is simulated and resets on reload.
- The token signature is a simple demo hash with the secret in the page. It is not secure; real signing happens on a server.
- The QR drawing is a sample pattern, not a scannable code.
- The assistant uses fixed rules, not an AI model.
- No real payment, email or SMS is sent.
