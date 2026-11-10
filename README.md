<div align="center">

# AcadStart

**One platform for the whole school day: for management, teachers, parents and students.**

*Know where your child is at every handover · talk to the school by voice in your own language · switch from paper in a day.*

![Status](https://img.shields.io/badge/status-prototype%20%2F%20design-orange)
![Region](https://img.shields.io/badge/launch-Tamil%20Nadu-blue)
![Languages](https://img.shields.io/badge/languages-Tamil%20%7C%20English-green)
![Mobile](https://img.shields.io/badge/mobile-Flutter-02569B)
![Backend](https://img.shields.io/badge/backend-FastAPI%20%2B%20PostgreSQL-009688)

</div>

> **Status:** 🧪 Prototype / design phase. This README is the product and technical blueprint for the prototype. Code lands module by module, following the [game plan](#9-game-plan).
> **Working name:** "AcadStart" is a placeholder.

---

## Table of contents
1. [Why this exists](#1-why-this-exists)
2. [What makes AcadStart different](#2-what-makes-acadstart-different)
3. [Who it's for](#3-who-its-for)
4. [Feature map](#4-feature-map)
5. [Prototype feature set](#5-prototype-feature-set)
6. [System architecture](#6-system-architecture)
7. [How each feature works and performs](#7-how-each-feature-works-and-performs)
8. [Privacy, security & compliance by design](#8-privacy-security--compliance-by-design)
9. [Game plan](#9-game-plan)
10. [Scale-up features (open-ended)](#10-scale-up-features-open-ended)
11. [Tech stack](#11-tech-stack)
12. [Planned repository layout](#12-planned-repository-layout)
13. [Non-functional targets](#13-non-functional-targets)
14. [Glossary](#14-glossary)
15. [Contributing & license](#15-contributing--license)

---

## 1. Why this exists
Most private schools in India still run on paper registers, the paper school diary, Excel sheets and dozens of one-way WhatsApp groups. Parents chase fee receipts and wonder where the bus is. At dismissal, children are often handed over on verbal trust. Teachers re-enter the same data into several school and government systems. Management has no single view of the school.

AcadStart aims to be **the one app a school actually needs**:
- **Wedge first:** fees, attendance, homework, the school diary and parent communication, the things a school uses every single day.
- **Signature features nobody else combines:** a door-to-door **Custody Chain**, a **voice-first Tamil assistant** with two-way translated messaging, and **Snap-to-Digitise** onboarding.
- **Compliance built in:** approved-fee-only billing, public fee disclosure, EMIS/UDISE+-friendly exports, and child-data protection under India's DPDP Act.

## 2. What makes AcadStart different

| | Typical school app in India | **AcadStart** |
|---|---|---|
| **Child safety** | Bus GPS dot on a map (if any) | 🛡️ **Custody Chain**: every handover verified and logged, *home → bus → gate → class → gate/bus → home*, with alerts only when something's wrong |
| **Dismissal** | Verbal trust at the gate | 🔑 **Safe Handover**: pre-approved adults with photo + rotating QR, one-time pickup passes, instant parent confirmation |
| **Parent communication** | English text broadcasts in WhatsApp groups | 🗣️ **Voice-first, two-way translated**: parents ask and reply by Tamil voice note, teachers read and write in English |
| **Getting started** | Weeks of manual data entry | 📸 **Snap-to-Digitise**: photograph paper registers and marks sheets, confirm, done |
| **School diary & slips** | Paper diary, signed slips lost in bags | ✍️ **Digital diary and permission slips** with one-tap sign-off and a live "who hasn't signed" board |
| **Records** | Locked in the vendor's system | 📜 **Parent-held, signed, QR-verifiable records**, shared only with consent, with full data export |

Inspiration from abroad, adapted for India: dismissal management (PikMyKid, US), government parent consent apps (Parents Gateway, Singapore), translated family messaging (TalkingPoints, US), and verifiable credentials (Europass, EU). The **Custody Chain** combination (transport + gate + attendance in a single handover timeline) is AcadStart's own.

## 3. Who it's for
| Role | What they get |
|---|---|
| 🏫 **Management / Admin** | Live dashboard: attendance, fee collection, buses on the road, custody exceptions, unsigned slips, parent tickets. Configures classes, fee structures, routes, staff and gates. |
| 👩‍🏫 **Teacher** | Class and timetable overview, one-tap offline attendance, Snap-to-Digitise for paper registers, homework, diary notes, translated two-way messages with parents. |
| 👨‍👩‍👧 **Parent / Guardian** | The child's day as one timeline (custody, attendance, homework, diary), fee dues and online payment, live bus and ETA, permission slips, authorised pickups, records wallet. Tamil or English, text or voice. |
| 🎒 **Student** | Timetable, assignments and due dates, announcements, certificates. |
| 🚌 **Driver / Bus attendant** | Trip start/stop, boarding and drop confirmation per child (feeds the Custody Chain), route view, GPS fallback when the bus has no device. |
| 🛂 **Gate staff** | Gate mode: scan arrivals, verify pickups against approved adults with photo, log every handover. |

All roles live in **one mobile app with role-based views**, plus a **web admin panel** for school offices.

## 4. Feature map
```mermaid
mindmap
  root((AcadStart))
    Signature
      Custody Chain
      Safe Handover at the gate
      Voice-first Tamil assistant
      Two-way translated messaging
      Snap-to-Digitise
    Daily core
      Offline attendance
      Homework and assignments
      Digital diary
      Permission slips
      Circulars and calendar
      Timetable and cafeteria menu
    Money
      Approved-heads fee billing
      UPI and card payments
      Digital receipts
      Public fee disclosure
    Transport
      Live bus map and ETA
      AIS-140 device integration
      Driver app fallback
      Route simulator
    Records
      Unique IDs
      Signed QR certificates
      Parent-approved sharing
```

## 5. Prototype feature set
The prototype is deliberately focused: enough to run a real school day end to end, plus the three signature features.

| # | Module | Prototype scope | Roles |
|---|---|---|---|
| M0 | **Clickable demo** | No-backend interactive walkthrough of every role, leading with the Custody Chain and voice assistant | — |
| M1 | **Foundation + Snap-to-Digitise** ⭐ | Multi-school tenancy, phone-OTP login, roles, setup wizard, unique IDs, Excel/CSV import, and **photo-to-data import of paper registers and marks sheets** | Admin, Teacher |
| M2 | **Daily core + Digital diary** | Offline-first attendance and absence alerts, homework, circulars, events calendar, timetable, cafeteria menu, **digital diary notes and permission slips with one-tap sign-off** | Teacher, Parent, Student, Admin |
| M3 | **Fees** | Fee structures locked to **approved fee heads**, invoices, instalments and concessions, UPI/card payments (gateway test mode), receipts, reminders, **public fee-disclosure page** | Admin, Parent |
| M4 | **Transport + Safe Handover + Custody Chain** ⭐ | Routes and stops, live bus map and ETA, AIS-140 device ingest + driver-app fallback + route simulator, boarding/drop confirmation, **gate mode with authorised-pickup verification**, and the **child's custody timeline with exception alerts** | Parent, Driver, Gate staff, Admin |
| M5 | **Voice-first assistant + translated messaging** ⭐ | WhatsApp + push; AI assistant answering in **Tamil or English, by text or voice note**; **two-way translated teacher ↔ parent messaging** with the original always available | Parent, Teacher, Admin |
| M6 | **Identity & records** | Unique IDs with optional national/state ID links, **digitally signed QR-verifiable certificates** (events, achievements, supporting transfer records), parent-approved sharing | Parent, Admin, Teacher |

⭐ = signature feature

**Out of scope for the prototype** (see [Scale-up](#10-scale-up-features-open-ended)): exams and report cards, fee AutoPay, supplies marketplace, admissions CRM, HR/payroll, library/inventory/hostel, and government integrations beyond file export.

## 6. System architecture

### 6.1 High-level view
```mermaid
flowchart TB
  subgraph CL["Clients"]
    direction TB
    MA(["📱 Mobile app<br/>Parent · Teacher · Student<br/>Driver · Gate staff"])
    WA(["🖥️ Web admin<br/>School office · Management"])
    PUB(["🌐 Public pages<br/>Fee disclosure · Verify certificate"])
    WAPP(["💬 WhatsApp<br/>text + voice notes"])
  end

  subgraph ED["Edge"]
    direction TB
    GW["🔐 API gateway<br/>Auth · Rate limits · Tenant routing"]
    WS["⚡ Realtime gateway<br/>WebSocket fan-out"]
    ING["📡 Telematics ingest<br/>MQTT · TCP · HTTP"]
    WH["🔔 Webhook receiver<br/>WhatsApp · Payments"]
  end

  subgraph CORE["Core services · modular monolith"]
    direction TB
    ID["🪪 Identity + Tenancy"]
    ACA["📚 Academics<br/>attendance · homework · timetable"]
    COM["📣 Communication<br/>diary · slips · notifications"]
    FEE["💳 Fees + Payments"]
    TRN["🚌 Transport<br/>routes · trips · ETA"]
    CUS["🛡️ Custody Chain<br/>handovers · exceptions"]
    REC["📜 Records + Credentials"]
  end

  subgraph AIL["AI layer"]
    direction TB
    AST["🤖 Assistant<br/>tool-calling · guardrails"]
    SPE["🗣️ Speech + Translation<br/>Tamil ⇄ English"]
    DIG["📸 Snap-to-Digitise<br/>vision extraction"]
  end

  subgraph DATA["Data"]
    direction TB
    PG[("🐘 PostgreSQL<br/>row-level security")]
    RD[("⚡ Redis<br/>live state · pub/sub · queues")]
    OBJ[("🗂️ Object storage")]
    AUD[("🧾 Audit log")]
  end

  subgraph EXT["External services"]
    direction TB
    PGW{{"💳 Payment gateway · UPI"}}
    WBA{{"💬 WhatsApp Business API"}}
    PUSH{{"🔔 Push · SMS"}}
    LLM{{"🧠 LLM · STT · TTS · Vision"}}
    MAP{{"🗺️ OSM · OSRM"}}
    GPS{{"🚌 AIS-140 devices"}}
    GOV{{"🏛️ EMIS · UDISE+ export"}}
  end

  CL ==>|"HTTPS · WebSocket · WhatsApp"| ED
  EXT -.->|"GPS pings · webhooks"| ED
  ED ==> CORE
  CORE <==>|"scoped tools"| AIL
  CORE ==> DATA
  CORE -.->|"payments · push · maps · export"| EXT
  AIL -.->|"model calls"| EXT

  classDef client fill:#E0E7FF,stroke:#4F46E5,stroke-width:1.5px,color:#1E1B4B
  classDef edg fill:#CFFAFE,stroke:#0891B2,stroke-width:1.5px,color:#083344
  classDef core fill:#DCFCE7,stroke:#16A34A,stroke-width:1.5px,color:#052E16
  classDef ai fill:#FCE7F3,stroke:#DB2777,stroke-width:1.5px,color:#500724
  classDef data fill:#FEF3C7,stroke:#D97706,stroke-width:1.5px,color:#451A03
  classDef ext fill:#F1F5F9,stroke:#64748B,stroke-width:1.5px,color:#0F172A
  classDef sig fill:#FDE047,stroke:#A16207,stroke-width:3px,color:#422006

  class MA,WA,PUB,WAPP client
  class GW,WS,ING,WH edg
  class ID,ACA,COM,FEE,TRN,REC core
  class AST ai
  class PG,RD,OBJ,AUD data
  class PGW,WBA,PUSH,LLM,MAP,GPS,GOV ext
  class CUS,SPE,DIG sig

  style CL fill:#6366F10F,stroke:#6366F1,stroke-dasharray:5 5
  style ED fill:#0891B20F,stroke:#0891B2,stroke-dasharray:5 5
  style CORE fill:#16A34A0F,stroke:#16A34A,stroke-dasharray:5 5
  style AIL fill:#DB27770F,stroke:#DB2777,stroke-dasharray:5 5
  style DATA fill:#D977060F,stroke:#D97706,stroke-dasharray:5 5
  style EXT fill:#64748B0F,stroke:#64748B,stroke-dasharray:5 5
```
<sub>🟨 Yellow nodes = signature features. Solid arrows = request/data flow, dotted = realtime push or export.</sub>

**Design choices**
- **Modular monolith first:** one deployable backend with strict module boundaries. It's cheap to run and easy to change, and modules can later be split into services (transport, custody and messaging are the first candidates).
- **Tenant isolation in the database:** every row carries `institution_id`, enforced by PostgreSQL **row-level security**.
- **Realtime off the hot path:** bus positions and custody events flow through Redis pub/sub to the WebSocket gateway, not through the main database.
- **AI behind narrow interfaces:** the assistant can only call scoped tools, and speech, translation and vision are swappable adapters (cloud APIs or self-hosted Indic models).
- **Every integration is an adapter:** payment gateway, WhatsApp provider, LLM/speech/vision vendors, maps and GPS device vendors can all be replaced.

### 6.2 Data model: academics, fees and onboarding
```mermaid
erDiagram
  INSTITUTION ||--o{ ACADEMIC_YEAR : runs
  INSTITUTION ||--o{ STAFF : employs
  INSTITUTION ||--o{ FEE_STRUCTURE : "approved (versioned)"
  ACADEMIC_YEAR ||--o{ SECTION : contains
  SECTION ||--o{ ENROLMENT : has
  STUDENT ||--o{ ENROLMENT : "enrolled via"
  STUDENT }o--o{ GUARDIAN : "cared for by"
  STAFF ||--o{ SECTION : "class teacher of"
  SECTION ||--o{ ATTENDANCE : records
  SECTION ||--o{ HOMEWORK : assigned
  FEE_STRUCTURE ||--o{ FEE_HEAD : lists
  ENROLMENT ||--o{ INVOICE : billed
  INVOICE ||--o{ PAYMENT : "settled by"
  STAFF ||--o{ DIGITISE_JOB : uploads

  INSTITUTION {
    uuid id
    string acad_id "AS-INST-xxxx"
    string udise_code "optional"
    string board "State / CBSE / ICSE"
  }
  STUDENT {
    uuid id
    string acad_id "AS-STU-xxxx"
    string emis_id "optional, state"
    string apaar_id "optional, consented"
  }
  FEE_STRUCTURE {
    uuid id
    string approval_ref "fee committee order"
    date valid_from
    date valid_to
    bool locked
  }
  DIGITISE_JOB {
    uuid id
    string kind "attendance / marks / admissions"
    string image_ref "auto-deleted"
    float avg_confidence
    string status "review / committed"
  }
```

### 6.3 Data model: safety, communication and records
```mermaid
erDiagram
  STUDENT ||--o{ HANDOVER_EVENT : "custody timeline"
  TRIP ||--o{ HANDOVER_EVENT : "bus events"
  GUARDIAN ||--o{ AUTHORISED_PICKUP : registers
  AUTHORISED_PICKUP }o--|| STUDENT : "may collect"
  ROUTE ||--o{ STOP : has
  ROUTE ||--o{ TRIP : "scheduled as"
  VEHICLE ||--o{ TRIP : runs
  STUDENT }o--o| STOP : "boards at"
  NOTICE ||--o{ ACKNOWLEDGEMENT : collects
  GUARDIAN ||--o{ ACKNOWLEDGEMENT : signs
  GUARDIAN ||--o{ MESSAGE : "sends / receives"
  STUDENT ||--o{ CREDENTIAL : "holds (wallet)"
  GUARDIAN ||--o{ CONSENT_GRANT : gives

  HANDOVER_EVENT {
    uuid id
    string type "board / alight / gate-in / present / release"
    string from_custodian
    string to_custodian
    string method "device / QR / driver tap / teacher"
    datetime at
  }
  AUTHORISED_PICKUP {
    uuid id
    string name
    string relation
    string photo_ref "encrypted"
    bool one_time
    datetime valid_until
  }
  NOTICE {
    uuid id
    string type "diary / circular / permission slip"
    bool needs_signature
    datetime deadline
  }
  MESSAGE {
    uuid id
    string original_lang "ta / en"
    string original_text
    string translated_text
    string audio_ref "deleted after transcription"
  }
  CREDENTIAL {
    uuid id
    string type "transfer-record / event / achievement"
    string signature "Ed25519"
    string status "active / revoked"
  }
  CONSENT_GRANT {
    uuid id
    string purpose
    string recipient
    datetime expires_at
  }
```

## 7. How each feature works and performs

### 7.1 Foundation + Snap-to-Digitise ⭐
**Onboarding a school in one day.** The setup wizard runs school profile → academic year → classes and sections → staff → students and guardians. Excel/CSV import auto-maps columns and previews errors before commit.

**Snap-to-Digitise** turns paper into data without retyping:
```mermaid
flowchart LR
  A(["📸 Teacher photographs<br/>register or marks sheet"]) --> B["Quality check<br/>blur · glare · crop"]
  B -->|retake| A
  B --> C["Vision model<br/>table → structured rows"]
  C --> D["Roster matching<br/>names ↔ class list"]
  D --> E{"Confidence<br/>per cell"}
  E -->|high| F["Auto-filled"]
  E -->|low| G["Highlighted<br/>for review"]
  F & G --> H(["✅ Teacher confirms"])
  H --> I[("Committed<br/>+ audit log")]
  H -.-> J["🗑️ Image deleted after<br/>retention window"]

  classDef step fill:#E0E7FF,stroke:#4F46E5,color:#1E1B4B
  classDef ai fill:#FCE7F3,stroke:#DB2777,color:#500724
  classDef ok fill:#DCFCE7,stroke:#16A34A,color:#052E16
  classDef warn fill:#FEF3C7,stroke:#D97706,color:#451A03
  class A,B,J step
  class C,D,E ai
  class F,H,I ok
  class G warn
```
- **Roster-aware:** extracted names are matched against the class list, so handwriting errors snap to real students.
- **Human in the loop:** nothing is committed without the teacher's confirmation, and low-confidence cells are highlighted.
- **Works for:** daily attendance registers, marks registers, old admission registers (bulk back-filling).
- **Logins and IDs:** phone + OTP for everyone. Permanent internal IDs (`AS-INST-…`, `AS-TCH-…`, `AS-STU-…`). UDISE+ code, EMIS ID and APAAR ID are optional linked fields, never primary keys. Aadhaar is never required.
- **Targets:** a 1,000-student school live within **one working day**; a 40-row register page digitised and confirmed in **under 2 minutes**; **≥ 95%** of cells correct before review.

### 7.2 Attendance: offline-first
```mermaid
sequenceDiagram
  autonumber
  participant T as 👩‍🏫 Teacher app
  participant L as 📦 On-device DB
  participant API as ⚙️ Backend
  participant N as 🔔 Notifications
  actor P as 👨‍👩‍👧 Parent
  rect rgba(79, 70, 229, 0.08)
  Note over T,L: Works with no network
  T->>L: Mark absentees (everyone present by default)
  L-->>T: Saved locally ✓
  end
  rect rgba(22, 163, 74, 0.08)
  Note over L,API: Sync when online
  L->>API: Push batch (idempotent, versioned)
  API->>API: Resolve conflicts + audit trail
  API->>N: Absent list + custody check
  N->>P: "Arjun is marked absent today"
  end
```
- A class of 40 is marked in **under 30 seconds**. Absence alerts arrive **within 5 minutes** of sync.
- Attendance is also a Custody Chain checkpoint (see 7.5). "Arrived at gate but not marked present" raises an exception.

### 7.3 Digital diary and permission slips
```mermaid
sequenceDiagram
  autonumber
  participant AD as 🏫 School office
  participant CO as 📣 Communication
  actor PA as 👨‍👩‍👧 Parent
  rect rgba(8, 145, 178, 0.08)
  AD->>CO: New slip · "Zoo trip on 21 Nov · sign by 15 Nov"
  CO->>PA: App + WhatsApp notification in Tamil or English
  PA->>CO: Tap "I consent" + OTP
  CO-->>AD: Live board · 312 signed · 41 pending
  CO->>PA: Auto-reminder to pending parents 24 h before deadline
  end
```
- Replaces the paper diary: teacher notes, circular acknowledgements and event consent, each with a timestamped, verifiable sign-off.
- Any optional payment linked to a slip is handled only where the school's approved fee rules permit it, and is kept separate from tuition fees.
- **Target:** acknowledgement status visible to the school in **real time**.

### 7.4 Fees and payments: approved heads only
```mermaid
sequenceDiagram
  autonumber
  participant A as 🏫 Admin
  participant F as 💳 Fee service
  actor P as 👨‍👩‍👧 Parent
  participant G as 🏦 Payment gateway
  rect rgba(217, 119, 6, 0.08)
  Note over A,F: Setup
  A->>F: Fee structure + approval reference
  F->>F: Lock · only approved heads billable
  end
  rect rgba(22, 163, 74, 0.08)
  Note over F,G: Collect
  F->>P: Invoice + dues reminder
  P->>G: Pay by UPI or card
  G-->>F: Signed webhook · payment captured
  F->>F: Verify, idempotent update, allocate to heads
  F->>P: Digital receipt
  F->>A: Collection dashboard updated
  end
```
- **Approved-heads lock:** invoices may only contain heads from the active approved structure, matching Tamil Nadu's private-school fee regulation.
- **No hidden parent charges:** no app or convenience fee is added for parents.
- **Public fee-disclosure page**, generated from the locked structure.
- **Money never touches AcadStart:** the gateway settles directly to the school's bank account. A nightly reconciliation job catches missed webhooks.
- **Target:** receipt **≤ 10 s** after payment.

### 7.5 Transport, Safe Handover and the Custody Chain ⭐
**The Custody Chain** treats the child's day as a series of verified handovers between custodians. Normal handovers are logged quietly; parents and the school are alerted only on exceptions.

```mermaid
stateDiagram-v2
  direction LR
  state "🏠 With family" as Home
  state "🚌 On morning bus" as BusIn
  state "🚪 Entered school gate" as Gate
  state "📚 Present in class" as InClass
  state "🚌 On return bus" as BusOut
  state "🤝 Handed to authorised adult" as Released
  state "⚠️ Exception" as Exception

  [*] --> Home
  Home --> BusIn : boarded · device or driver tap
  Home --> Gate : dropped by parent · gate scan
  BusIn --> Gate : bus arrived · gate scan
  Gate --> InClass : marked present
  InClass --> BusOut : boarded return bus
  InClass --> Released : released at gate · QR verified
  BusOut --> Released : dropped at stop · guardian confirmed
  Released --> [*]

  BusIn --> Exception : no gate scan in 20 min
  Gate --> Exception : not present by first period
  InClass --> Exception : pickup by unlisted adult
  BusOut --> Exception : missed stop or off-route

  classDef ok fill:#DCFCE7,stroke:#16A34A,color:#052E16
  classDef move fill:#CFFAFE,stroke:#0891B2,color:#083344
  classDef alert fill:#FEE2E2,stroke:#DC2626,stroke-width:2px,color:#7F1D1D
  class Home,InClass,Released ok
  class BusIn,Gate,BusOut move
  class Exception alert
```

**What the parent sees** (one timeline, in Tamil or English):

| Time | Event | Verified by |
|---|---|---|
| 07:42 | Boarded Bus 3 at Gandhi Nagar stop | Bus attendant tap + GPS |
| 08:15 | Entered school, Gate 1 | Gate scan |
| 08:30 | Present in Class 5B | Teacher attendance |
| 15:40 | Handed to *Amma* at Gate 2 | Rotating QR + photo check |

**Safe Handover at the gate:**
```mermaid
sequenceDiagram
  autonumber
  actor PA as 👨‍👩‍👧 Parent
  participant APP as 📱 Parent app
  participant CU as 🛡️ Custody service
  participant GA as 🛂 Gate staff app
  actor AD as 🧑 Adult collecting
  rect rgba(22, 163, 74, 0.08)
  Note over PA,CU: Before dismissal
  PA->>APP: Register authorised adults · photo + relation
  PA->>APP: Or issue a one-time pass for today
  APP->>CU: Store pass · time window
  end
  rect rgba(8, 145, 178, 0.08)
  Note over GA,AD: At the gate
  AD->>GA: Shows rotating QR or pass
  GA->>CU: Verify child ↔ adult + time window
  alt Authorised
    CU-->>GA: ✅ Photo + name for visual check
    GA->>CU: Confirm handover
    CU-->>APP: "Handed to Ravi (uncle) at Gate 2"
  else Not authorised
    CU-->>GA: ⛔ Do not release
    CU-->>APP: 🚨 Alert parent + admin
  end
  end
```

**Bus tracking pipeline, built for the 7:30 am rush:**
```mermaid
flowchart LR
  subgraph SRC["Sources"]
    D1["📡 AIS-140 device"]
    D2["📱 Driver app<br/>fallback"]
    SIM["🧪 Route simulator<br/>demo + load tests"]
  end
  SRC -->|ping every 5–10 s| ING["Ingest<br/>normalise · de-jitter"]
  ING --> POS[("Redis<br/>latest position")]
  ING --> ETA["ETA engine<br/>polyline + history"]
  ETA --> GEO{"Geofence rules"}
  GEO -->|2 stops away| NOTIF["🔔 Parent alert"]
  GEO -->|arrived · off-route| CUS["🛡️ Custody Chain"]
  POS --> PS["Pub/Sub per trip"] --> WSG["WebSocket nodes"] --> MAP(["🗺️ Parent live map<br/>own child's bus only"])
  ING -.->|batched| HIST[("Trip history")]

  classDef src fill:#E0E7FF,stroke:#4F46E5,color:#1E1B4B
  classDef proc fill:#CFFAFE,stroke:#0891B2,color:#083344
  classDef store fill:#FEF3C7,stroke:#D97706,color:#451A03
  classDef out fill:#DCFCE7,stroke:#16A34A,color:#052E16
  classDef sig fill:#FDE047,stroke:#A16207,stroke-width:3px,color:#422006
  class D1,D2,SIM src
  class ING,ETA,GEO,PS,WSG proc
  class POS,HIST store
  class NOTIF,MAP out
  class CUS sig
  style SRC fill:#6366F10F,stroke:#6366F1,stroke-dasharray:5 5
```
- **Hardware first, phone as backup:** many school buses already carry mandated AIS-140 trackers, so AcadStart integrates those instead of selling hardware.
- **Peak-load math:** 1,500 buses × 1 ping / 5 s ≈ 300 msg/s, which is small. The real peak is ~50,000 parents watching at 7:30 am, handled by horizontally scaled WebSocket nodes, with fallback to a cached 15-second poll.
- **Privacy by scope:** a parent sees only their own child's bus, only during that trip.
- **Targets:** map **≤ 10 s** behind reality; ETA error **≤ 3 min**; custody-exception alert **≤ 60 s** after the rule triggers; handover confirmation to the parent **≤ 30 s** after a gate scan.

### 7.6 Voice-first Tamil assistant + two-way translated messaging ⭐
```mermaid
sequenceDiagram
  autonumber
  actor P as 👨‍👩‍👧 Parent
  participant W as 💬 WhatsApp
  participant S as 🗣️ Speech + Translation
  participant AI as 🤖 Assistant
  participant T as 🔧 Scoped tools
  participant TC as 👩‍🏫 Teacher app
  rect rgba(219, 39, 119, 0.08)
  Note over P,T: Ask the school by voice
  P->>W: 🎙️ Voice note in Tamil
  W->>S: Audio
  S->>AI: Tamil transcript
  AI->>T: get_bus_eta(child) · get_fee_dues(child)
  T-->>AI: Bus 3 is 6 min away · ₹4,500 due 15 Nov
  AI->>S: Answer text in Tamil
  S-->>W: 🔊 Voice reply + text
  W-->>P: Reply in Tamil
  end
  rect rgba(79, 70, 229, 0.08)
  Note over TC,P: Talk to the teacher across languages
  TC->>S: "Please send the signed form tomorrow" (English)
  S->>W: Tamil translation, tagged auto-translated
  W-->>P: Message in Tamil
  P->>W: 🎙️ Tamil voice reply
  W->>S: Audio
  S-->>TC: English text + original Tamil transcript
  end
```
- **Tool-calling, not open data access:** the assistant can only call narrow tools (`get_homework`, `get_attendance`, `get_fee_dues`, `get_bus_eta`, `get_custody_timeline`, `get_circulars`, `get_menu`), and only for children linked to the verified phone number.
- **Languages:** Tamil, English and code-mixed "Tanglish", by text or voice. Translations are always tagged as automatic, with the original one tap away.
- **School glossary:** class names, subjects and staff names are kept untranslated, to avoid mistranslating proper nouns.
- **Escalation:** complaints, sensitive or out-of-scope questions become tickets for the school office.
- **Cost control:** a small fast model handles routine questions, with a larger model only for complex ones. Common answers (today's menu) are cached, and each school has a message quota.
- **Targets:** text reply **≤ 5 s**; voice reply **≤ 8 s**; ≥ 70% of routine office queries answered without staff.

### 7.7 Identity and verifiable records
```mermaid
sequenceDiagram
  autonumber
  participant S1 as 🏫 Current school
  participant R as 📜 Records service
  actor G as 👨‍👩‍👧 Guardian
  participant S2 as 🏫 New school / organiser
  rect rgba(217, 119, 6, 0.08)
  Note over S1,G: Issue
  S1->>R: Issue credential · event, achievement, transfer record
  R->>R: Sign with school key (Ed25519) + QR
  R->>G: Appears in the child's wallet
  end
  rect rgba(22, 163, 74, 0.08)
  Note over G,S2: Share with consent
  S2->>G: Request records
  G->>R: Approve (OTP) · choose items · set expiry
  R->>S2: Time-limited access link
  S2->>R: Verify signature + revocation ✓
  end
```
- **Parent-held, consent-based**, verifiable by anyone via QR (W3C Verifiable Credentials data model).
- **Complements the official TC** issued through the state system (EMIS in Tamil Nadu); it doesn't replace it.
- **Never shared by default:** conduct remarks, health notes, custody logs. No cross-school profiles of children.

### 7.8 Management dashboard
Live tiles for attendance %, custody exceptions, buses on the road, fee collection vs. due, unsigned slips and open parent tickets. Drill down by class and section. Exports in EMIS/UDISE+-friendly formats, so staff don't type the same data twice.

## 8. Privacy, security & compliance by design
| Area | Approach |
|---|---|
| **Children's data (DPDP Act 2023 + Rules 2025)** | School = data fiduciary, AcadStart = processor. Verifiable guardian consent. Purpose limitation to education and child safety. **No ads, no profiling or behaviour scoring of children, no facial recognition.** |
| **Custody Chain data** | Handover and location logs visible only to the child's guardians and authorised staff. Detailed logs kept for a short, configurable window (default 90 days), then summarised. Pickup photos encrypted and shown only at the gate during verification. |
| **Voice and images** | Voice notes deleted after transcription (default 24 h). Scanned register images deleted after confirmation + a short retention window. AI providers are contractually barred from training on school data. |
| **Data residency** | All data hosted in India. |
| **Tenant isolation** | PostgreSQL row-level security; per-tenant encryption keys for sensitive fields. |
| **Access control** | Role-based; teachers see only their sections, parents only their children, gate staff only dismissal verification. All admin actions are audit-logged. |
| **Security** | TLS, encryption at rest, OTP rate limits, signed webhooks, secrets vault, dependency scanning, **third-party security audit (VAPT) before any real data**. |
| **Fee regulation** | Approved-heads lock, approval references, public disclosure, no parent-side app fees. |
| **Payments** | Licensed gateway; direct settlement to the school; AcadStart never holds funds. |
| **Prototype rule** | **Synthetic data only** until the security audit and legal review of consent flows are done. |

## 9. Game plan
```mermaid
gantt
  title AcadStart · prototype to pilot (indicative)
  dateFormat YYYY-MM-DD
  axisFormat %b %Y
  section Phase 0 · Validate
  Clickable demo M0                      :active, p0a, 2026-11-15, 21d
  School conversations and pilot commitments :p0b, 2026-11-25, 75d
  section Phase 1 · Prototype
  M1 Foundation + Snap-to-Digitise       :p1a, 2026-12-01, 25d
  M2 Daily core + Digital diary          :p1b, after p1a, 21d
  M3 Fees and payments                   :p1c, after p1b, 25d
  M4 Transport + Custody Chain           :crit, p1d, after p1c, 28d
  M5 Voice assistant + translation       :crit, p1e, after p1d, 21d
  M6 Identity and records                :p1f, after p1e, 18d
  section Phase 2 · Pilot
  Security audit and legal review        :p2a, 2027-04-20, 30d
  Pilot onboarding                       :p2b, 2027-05-05, 30d
  Go-live with academic year             :milestone, 2027-06-04, 0d
  section Phase 3 · Scale-up
  Next-tier features and new districts   :p3, 2027-07-01, 180d
```

### Phase 0: Validate (now → Feb 2027)
- **Build:** M0 clickable demo, leading with the Custody Chain timeline, a Tamil voice-note exchange and a Snap-to-Digitise run.
- **Do:** demo to ~10–15 private schools (Coimbatore and Chennai first); capture their top pains, current tools and decision makers.
- **Exit criteria:** **≥ 5 schools committed to a pilot** for the June 2027 academic year. Otherwise revisit scope before writing production code.

### Phase 1: Prototype (Dec 2026 → Apr 2027)
Build M1 → M6 on synthetic data, one module at a time, each with a demo script, seed data for a fictional Tamil Nadu school, automated tests for critical paths (fee lock, webhooks, consent, tenant isolation, custody exception rules) and load tests for the morning peak.
**Exit criteria:** a full simulated school day runs end to end:
- A paper register is snapped and imported.
- Attendance is marked offline and synced.
- A permission slip is signed.
- A fee is paid by UPI (test mode).
- Two buses are tracked, and the Custody Chain completes for a class, with one simulated exception caught.
- A parent asks by Tamil voice note and a teacher replies in English.
- A certificate is issued and verified by QR.

### Phase 2: Pilot (Apr → Jul 2027)
- Security audit; legal review of consent flows and data-processing agreements.
- On-ground onboarding with Snap-to-Digitise; teacher training (≤ 1 hour); gate staff training (≤ 30 min); parent rollout via WhatsApp invite links.
- **Exit criteria (first 8 weeks):** ≥ 70% of parents active weekly; ≥ 60% of fees paid online; custody timeline complete for ≥ 95% of bus-riding students; ≥ 80% slip sign-off within deadline; zero data-isolation incidents.

### Phase 3: Scale-up (from Jul 2027)
Grow by district cluster, ship the most-requested items below, harden infrastructure, and add Puducherry and further states through configurable regional compliance packs.

## 10. Scale-up features (open-ended)
> This list is **intentionally open-ended**: it grows with what schools, parents and teachers actually ask for. Pilot feedback sets the priorities, not this order. Have an idea? Open an issue with the `feature-idea` label.

**Next tier (first candidates after the pilot)**
- [ ] **Fee AutoPay + sibling wallet**: UPI AutoPay mandates for monthly or term fees, one account for all children (even across AcadStart schools), reminders timed to salary dates
- [ ] **State Sync Pack**: enter once, generate ready-to-upload EMIS/UDISE+ files with a "what's due" checklist
- [ ] **Parent learning nudges**: 2–3 short Tamil/English messages a week on what the child is learning and a 5-minute home activity
- [ ] **Attendance nudges**: research-informed, non-shaming outreach to parents of frequently absent children, with teacher escalation
- [ ] **NEP Holistic Progress Card**: learning-outcome (mastery) gradebook with self, peer and parent inputs
- [ ] **Teacher Copilot**: lesson-plan drafts from the syllabus calendar, worksheets from the exact chapter, report-card remark drafts (teacher approves)
- [ ] **Verified Event Passport**: inter-school events and olympiads registered with verified records, results issued back as credentials

**Academics**
- [ ] Exams, marks entry and report cards (State Board, CBSE and ICSE formats)
- [ ] Automatic timetable generation (constraint solver) and substitution management
- [ ] Curriculum coverage tracking
- [ ] LMS: study material, online classes, quizzes
- [ ] Co-curricular and sports records; house points

**Parents & students**
- [ ] School-supplies marketplace: booklists, uniforms and stationery from local vendors, **parent's free choice**, transparent pricing, fully separate from school fees
- [ ] Parent–teacher meeting scheduling
- [ ] Leave requests and early pick-up requests (into Safe Handover)
- [ ] Cafeteria pre-orders, allergy flags and canteen wallet
- [ ] Student portfolio and achievements timeline
- [ ] More languages (Hindi, Malayalam, Telugu, Kannada, …)

**Safety & transport**
- [ ] RFID/NFC cards as extra Custody Chain scan methods
- [ ] SOS/panic-button integration with AIS-140 devices
- [ ] Anonymous safe-reporting channel for students and parents to the counsellor or POCSO committee
- [ ] Visitor management and gate passes
- [ ] Driver behaviour analytics (speeding, harsh braking) from device data
- [ ] Route optimisation for new admissions

**Management & operations**
- [ ] Admissions CRM: enquiries, applications, follow-ups
- [ ] HR, staff attendance and payroll (via payroll-provider integrations)
- [ ] Library, inventory, assets and hostel
- [ ] Multi-campus and school-chain dashboards
- [ ] Fee instalments/EMI via licensed financing partners
- [ ] Accounting exports (Tally etc.) and GST-ready reports

**Identity, records & openness**
- [ ] Teacher-held verified profile (qualifications and service history, consent-based)
- [ ] DigiLocker integration (subject to approval as a partner)
- [ ] Deeper EMIS / UDISE+ / APAAR interoperability, subject to official access
- [ ] Open API + webhooks on an open data standard, with one-click full export (no lock-in)
- [ ] Alumni records and verified transcripts

**Platform**
- [ ] White-label apps for school chains
- [ ] Higher-education edition (credits, semesters, placements)
- [ ] Puducherry, then other states, via regional compliance packs
- [ ] _…your idea here_

## 11. Tech stack
| Layer | Choice | Why |
|---|---|---|
| Mobile app | **Flutter** (one app, role-based views incl. gate mode) | One codebase for Android and iOS; fast on 2 GB Android phones; offline SQLite; camera and QR built in |
| Web admin | **Next.js + TypeScript + Tailwind** | Fast to build data-heavy admin screens |
| Backend | **Python (FastAPI)** as a modular monolith | Strong AI ecosystem, typed, async |
| Database | **PostgreSQL** + row-level security | Integrity for fees, custody and records; tenant isolation in the DB |
| Realtime | **Redis** pub/sub + **WebSockets**; **MQTT/TCP** device ingest | Live maps and custody events without touching the main DB |
| Maps | **OpenStreetMap + OSRM** (self-hosted), optional commercial maps | Predictable costs |
| Messaging | **WhatsApp Business API**, FCM/APNs push, DLT-registered SMS fallback | Parents already live on WhatsApp |
| Payments | **Licensed Indian payment gateway** (UPI, cards, netbanking) | Direct settlement to schools |
| AI: assistant | **LLM with tool-calling** (small model for routine, larger for complex) | Strict tool scoping; Tamil/English |
| AI: speech | **Tamil/English STT + TTS** (cloud APIs or Indic open models such as AI4Bharat) | Voice-first parents |
| AI: translation | **LLM or Indic MT models** (e.g., IndicTrans2) with a school glossary | Accurate names and school terms |
| AI: vision | **Vision-language model + OCR** with roster matching | Snap-to-Digitise |
| Credentials | **Ed25519**, W3C Verifiable Credentials, QR | Verifiable without the platform |
| Infra | Docker, India-region cloud, GitHub Actions CI | Simple start; split modules as needed |
| Observability | Structured logs, metrics, tracing, uptime alerts | The morning rush must never surprise us |

## 12. Planned repository layout
```
acadstart/
├── apps/
│   ├── mobile/            # Flutter app: parent · teacher · student · driver · gate
│   ├── admin-web/         # Next.js admin panel
│   └── demo/              # M0 clickable demo
├── services/
│   └── api/               # FastAPI modular monolith
│       ├── identity/      ├── academics/     ├── communication/
│       ├── fees/          ├── transport/     ├── custody/
│       ├── records/       └── ai/            # assistant · speech · translation · digitise
├── tools/
│   ├── route-simulator/   # replays bus routes for demos and load tests
│   └── seed-data/         # synthetic Tamil Nadu school (incl. sample paper registers)
├── infra/                 # docker-compose, deployment, CI
└── docs/                  # ADRs, API docs, runbooks
```

## 13. Non-functional targets
| Metric | Prototype target |
|---|---|
| API latency (p95) | ≤ 300 ms |
| Bus position freshness on the parent map | ≤ 10 s |
| Handover confirmation to the parent after a gate scan | ≤ 30 s |
| Custody exception alert after the rule triggers | ≤ 60 s |
| Concurrent parent viewers at peak | 50,000 (load-tested) |
| Payment receipt after capture | ≤ 10 s |
| Assistant reply (text / voice) | ≤ 5 s / ≤ 8 s |
| Snap-to-Digitise: 40-row page reviewed and committed | < 2 min, ≥ 95% cells correct pre-review |
| Mobile app install size | ≤ 30 MB |
| Devices | Android 8+ with 2 GB RAM on 4G; attendance works offline |
| School onboarding | 1,000-student school live in 1 working day |
| Availability (pilot) | 99.5% monthly, prioritised for 7–9 am and 2–5 pm |

## 14. Glossary
| Term | Meaning |
|---|---|
| **AIS-140** | Indian standard for vehicle tracking devices and emergency buttons in public and school transport |
| **APAAR ID** | "One Nation One Student" academic ID, generated with parental consent |
| **Custody Chain** | AcadStart's verified, door-to-door log of who is responsible for a child at each point of the school day |
| **DPDP Act** | Digital Personal Data Protection Act 2023, India's data-protection law, with special rules for children |
| **EMIS** | Tamil Nadu's Educational Management Information System, the state's system of record for students and schools |
| **UDISE+** | National school database; issues school codes and student numbers (PEN) |
| **TC** | Transfer Certificate, issued when a student leaves a school |
| **Fee committee** | State body that fixes or approves private-school fees |
| **Verifiable credential** | A digitally signed record whose authenticity can be checked independently |

## 15. Contributing & license
The project is in its design phase and not yet open for code contributions. Feedback and ideas are welcome via **Issues** (`feature-idea`, `question`).

**License:** not yet chosen. Until a license is added, all rights are reserved by the author.

---
<div align="center"><sub>Maintained by <a href="https://github.com/Vijay190899">@Vijay190899</a></sub></div>
