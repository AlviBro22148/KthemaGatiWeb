# Content Requirements: FAQ, Privacy Policy & Terms of Service

This is a checklist of what each page needs to *contain*, based on how Kthema Gati actually works (mobile app + dashboard + backend, subscription plans, partner network, media uploads). Use this as the brief for writing final copy — the Privacy Policy and ToS sections in particular should still be reviewed by a lawyer familiar with Albanian/EU data protection law before publishing, since they create binding obligations.

Known facts to reuse across all three pages:
- Legal/trade name: Kthema Gati — Elbasan, Albania (confirm registered company name + NUIS/NIPT business registration number — not yet in the repo)
- Contact: info@kthemagati.al, +355 69 997 8135, Mon–Fri 08:00–18:00
- Plans: Essential €29/mo, Comfort €49/mo, VIP €99/mo — all month-to-month, no long-term contract
- 14-day free trial, no card required
- 30-day money-back guarantee
- Payment methods: Visa, Mastercard, Direct Debit, bank transfer
- Platforms: mobile app (client-facing), dashboard (staff/admin), partner garage network

---

## 1. FAQ

Group into categories; pull real answers from what the product actually does.

### Account & Getting Started
- How do I create an account? (phone number in +355 format, email, password)
- Is the 14-day trial really free / no card needed?
- Can I use the app without a subscription after the trial?
- How do I add a vehicle (brand, model, year, license plate, VIN)?
- Can I add more than one vehicle / manage a fleet?

### Booking & Repairs
- How do I submit a repair request?
- Can I attach photos/videos/voice notes of the problem? (yes — camera, gallery, mic, max ~60s video)
- How do I know which partner garage will handle my car?
- How do I track repair status in real time (Comfort/VIP only)?
- How do ratings/reviews of a completed job work?

### Plans & Billing
- What's the difference between Essential, Comfort and VIP?
- Can I upgrade/downgrade my plan mid-cycle? (yes, prorated, effective immediately)
- Is there a contract / cancellation fee? (no — month-to-month)
- What payment methods are accepted? Are payments secure?
- How does the 30-day guarantee/refund work in practice?
- Do partner discounts (10%/20%) apply automatically or do I need a code?

### Partners / Garages
- How does a garage/service provider join the network?
- Is there a cost for garages to join?
- What service types are supported (tire service, electrical, general service, rent-a-car, etc.)?

### Data & Privacy
- What happens to my photos/videos after a repair is done?
- Who can see my vehicle and repair data (link out to Privacy Policy)?
- How do I delete my account and data?

### Support
- How do I contact support, and what are response times per plan (email 24–48h / live chat 8am–8pm / 24/7 phone for VIP)?
- What do I do if I have a dispute with a partner garage over service quality?

---

## 2. Privacy Policy

Must be accurate to what the backend/mobile app actually does — write from this list, don't use generic boilerplate.

### Who we are / controller identity
- Legal entity name, registered address (Elbasan, Albania), business registration number, contact email for privacy requests (e.g. privacy@kthemagati.al or info@kthemagati.al)
- Whether Kthema Gati is the "data controller" and partner garages are "processors" or independent controllers for the service work they perform — this needs a clear answer, since invoices carry PartnerId/PartnerName

### What personal data is collected
- **Identity/contact:** full name, email, phone number (Albanian format)
- **Account/security:** password (bcrypt-hashed, never stored in plain text), user role (Client/Staff/Admin), account creation date
- **Profile:** profile picture (stored via Cloudinary)
- **Device/push:** FCM (Firebase Cloud Messaging) token, device info
- **Vehicle data:** brand, model, year, license plate, VIN
- **Service data:** repair request descriptions, scheduled date/time, status history, ratings and comments
- **Media uploads:** photos, videos, audio recordings of vehicle damage; pickup/return photos; signatures; any GPS location links attached to media — state explicitly that location data may be embedded in photos/uploads
- **Financial:** invoice amounts, payment method type, payment timestamps (clarify whether card numbers ever touch Kthema Gati servers or only a payment processor — if Visa/Mastercard/Direct Debit are handled by a third-party payment gateway, name it; if none is integrated yet, say so)

### How data is collected
- Directly from the user (registration, forms, uploads)
- Automatically (device info, FCM token, timestamps)
- From partner garages (status updates, invoices referencing the user)

### Legal basis / purpose of processing (GDPR-style, relevant since EU-facing/Riga finalist)
- Contract performance (booking and delivering repair services)
- Legitimate interest (service quality, fraud prevention, push notifications about their own requests)
- Consent (marketing communications, if any)
- Legal obligation (invoicing/tax records)

### Third parties data is shared with
- **Cloudinary** — stores all uploaded media (images, video, audio, PDFs); note it's a US-based processor, relevant for cross-border transfer disclosures
- **Firebase (Google)** — push notification delivery via FCM; same cross-border note
- **Partner garages** — receive relevant repair request + vehicle + contact data to perform the service
- **Payment processor** (name it once one is integrated) for billing
- **PostgreSQL database** — where is it hosted (which country/provider)? State this for data-residency clarity.
- State clearly: no data is sold to third parties for advertising (if true)

### Data retention
- How long are photos/videos kept after a job closes?
- How long is service history kept (Essential plan explicitly limits to "6 months" — does data get deleted or just hidden from the UI)?
- Retention period for invoices (tax law may require years, e.g. Albanian fiscal record-keeping rules)

### User rights
- Right to access, correct, delete account/data
- How to request deletion (in-app setting vs. emailing support)
- Right to withdraw consent for marketing/push notifications
- Contact for data protection questions/complaints, and mention of Albania's data protection authority (Komisioneri për të Drejtën e Informimit dhe Mbrojtjen e të Dhënave Personale) as well as GDPR if EU users are served

### Security measures
- Password hashing (bcrypt), JWT-based authentication (mention token expiry generally, not implementation specifics)
- Role-based access control (Client/Staff/Admin)
- Note: current CORS config allows all origins in some environments — make sure production config is locked down before claiming "we secure your data" in the policy (this is an internal action item, not policy text)

### Children's privacy
- Minimum age to register (state one, e.g. 18+, since vehicle ownership/registration implies adult users)

### Cookies/tracking (dashboard + marketing site)
- Any analytics on the landing page or dashboard (none currently detected — confirm before publishing, or add a cookie banner if analytics gets added later)

### Changes to the policy
- How users are notified of material changes

---

## 3. Terms of Service

### Parties & acceptance
- Identify Kthema Gati as operator; users accept by creating an account or checking the box on the contact form
- Separate terms may be needed for **clients** (drivers) vs. **partner garages** (service providers) since they have very different obligations — consider whether this should be two documents or one with distinct sections

### Description of service
- Kthema Gati connects vehicle owners with a network of certified/partner garages for booking, tracking, and paying for repair/maintenance services via mobile app; dashboard is for staff/partner management

### Eligibility
- Minimum age, must be a legal vehicle owner/authorized user of the vehicle registered

### Account responsibilities
- Accuracy of registration info (name, phone, vehicle details)
- Responsibility for account security/password
- One account per user; consequences of sharing credentials

### Subscription plans & billing
- Exact plan names/prices/features (Essential/Comfort/VIP) — link to or mirror pricing.html so ToS and marketing page never contradict each other
- 14-day trial terms: no card required, what happens automatically at day 15 (does it auto-lapse or auto-charge? — needs a real answer, this is a common ToS trap)
- Billing cycle, proration rules for plan changes, auto-renewal, how to cancel
- 30-day refund guarantee: exact process, timeframe from which date, "no questions asked" — put a real, checkable procedure behind that marketing claim
- Consequences of failed payment (service suspension, grace period)

### Partner garage terms
- Vetting/certification claims ("certified partners") — what verification actually happens, since this is a marketing promise the ToS should back up
- Kthema Gati's role: platform/intermediary vs. party to the repair contract — critical for liability (see below)
- How partners get paid, discount obligations (10%/20% partner discounts for Comfort/VIP)

### User-submitted content
- Ownership/license for uploaded photos, videos, audio (Kthema Gati needs a license to store/display/transmit these to partner garages)
- Prohibited content (nothing illegal, no submitting content about vehicles/people without rights to do so)

### Service quality & liability
- Kthema Gati is a booking/management platform — clarify whether it's liable for the *quality of repair work itself* (usually: no, that's the garage's responsibility) vs. liable for platform errors (billing mistakes, data loss)
- Replacement vehicle / pick-up-drop-off terms (VIP plan) — conditions, limits, liability for the loaner vehicle
- Limitation of liability clause, disclaimer of warranties

### Disputes between users and partners
- Process for complaints about repair quality, pricing disputes, damage claims during service
- Kthema Gati's role in mediation (if any)

### Cancellation & termination
- User's right to cancel subscription/account anytime
- Kthema Gati's right to suspend/terminate accounts (fraud, abuse, non-payment, harassment of partners)
- What happens to data/history after account closure (ties back to Privacy Policy retention section)

### Intellectual property
- App, dashboard, branding, logo ownership by Kthema Gati

### Governing law & jurisdiction
- Albanian law, courts of Elbasan (standard for an Albania-registered company) — confirm with legal counsel, especially given EU user exposure from the GEN-E Riga recognition

### Changes to terms
- Notice period/method for material changes to plans, pricing, or terms

### Contact for legal notices
- info@kthemagati.al / registered address

---

## Open items to resolve before publishing (not content gaps, but decisions needed)
1. ~~Real phone number~~ — done, contact.html and the legal pages now use +355 69 997 8135
2. Business registration number (NUIS/NIPT) for the entity
3. Name of the actual payment processor/gateway once billing is wired up
4. Where the PostgreSQL database and Cloudinary/Firebase accounts are hosted (data residency)
5. What happens automatically when the 14-day trial ends
6. Whether "certified partner" vetting is a real process worth describing, or should be softened
7. Whether Kthema Gati vs. partner garages is the contracting party for the actual repair (drives the liability section)
