# InsuriFyx: AI-Powered Parametric Income Insurance

**Protecting the Backbone of India's Platform Economy.**

InsuriFyx is a hackathon prototype for parametric income protection designed specifically for food delivery partners (Zomato, Swiggy, etc.). Unlike traditional insurance, InsuriFyx uses live environmental data, rule-based risk scoring, and automated trigger handling to detect income-disrupting events such as heavy rain, poor air quality, and simulated platform outages, then generates claims without manual paperwork.

---

## Features at a Glance

- **Zero-Touch Claims**: No forms, no evidence, no adjusters. Claims are generated automatically when supported trigger conditions are met.
- **Real-Time Monitoring**: Continuous polling of live weather and AQI signals, with automated trigger evaluation across supported zones.
- **Dynamic Pricing**: Weekly premiums are calculated from plan type, zone risk, platform loading, and current environmental conditions.
- **Admin Trigger Simulation**: Admin users can simulate supported trigger events to demo policy activation, claims generation, and settlement flow.
- **Fraud Checks**: Rule-based checks flag impossible movement, suspicious policy timing, repeated claims, and sensor mismatch patterns.

---

## Tech Stack

### Frontend
- **Framework**: React (Vite)
- **Styling**: Tailwind CSS / Vanilla CSS
- **Routing**: React Router
- **Icons**: Lucide React (implied)

### Backend
- **Runtime**: Node.js
- **Framework**: Express
- **ORM**: Prisma
- **Database**: PostgreSQL
- **Automation**: Cron-style polling and rule-based trigger processing

---

## Parametric Triggers

Claims are initiated when thresholds are crossed according to currently integrated or simulated sources:

| Trigger Category | Data Source | Threshold |
| :--- | :--- | :--- |
| **Heavy Rainfall** | Open-Meteo weather API | Rainfall threshold crossed in a monitored zone |
| **Air Quality (AQI)**| Open-Meteo air quality API | AQI threshold crossed in a monitored zone |
| **Platform Outage** | Simulated platform status check | Rule-based outage condition or manual admin simulation |

---

## Architecture & Automation

### 1. Dynamic Premium Calculation
A rule-based pricing flow combines plan configuration, zone-level baseline risk, platform loading, and live environmental conditions to produce a weekly premium quote and payout cap.

### 2. Fraud & Anti-Spoofing
To reduce obvious abuse in the prototype, InsuriFyx applies lightweight server-side and client-assisted checks:
- **GPS Physics**: Detection of impossible velocity spikes from submitted location history.
- **Device Sensors**: Validation of accelerometer patterns against claimed GPS movement.
- **Claim Heuristics**: Repeated claim windows, repeated same-zone claims, and policy-after-trigger scenarios are flagged.

### 3. Live Data + Rule-Based Automation
The backend polls supported Bengaluru zones on a schedule, fetches live environmental readings, evaluates trigger thresholds, and auto-generates claims for eligible active policies. Platform outage handling is currently simulated for demo purposes.

---

## Getting Started

### Prerequisites
- Node.js (v18+)
- PostgreSQL
- NPM or Yarn

### Installation

1. **Clone the repository**:
   ```bash
   git clone https://github.com/riddhi2106/Catalysts
   cd Catalysts
   ```

2. **Backend Setup**:
   ```bash
   cd backend
   npm install
   npm run prisma:generate
   npm run prisma:migrate
   npm run prisma:seed
   npm run dev
   ```

   Create a `.env` file in `backend/` with:
   ```env
   DATABASE_URL=postgresql://...
   JWT_SECRET=replace-with-a-strong-secret
   FRONTEND_URL=http://localhost:5173
   RAZORPAY_KEY_ID=rzp_test_...
   RAZORPAY_KEY_SECRET=...
   ```

3. **Frontend Setup**:
   ```bash
   cd ../frontend
   npm install
   npm run dev
   ```

4. **Access the App**:
   The application will be running at `http://localhost:5173`.


### Seeded Demo Zones

The default seeded workers use supported Bengaluru zones wired into the live environmental data service:

- `Koramangala`
- `Indiranagar`
- `HSR Layout`

### Prototype Notes

- Live weather and AQI data are fetched from Open-Meteo, with deterministic fallback values if the API is unavailable.
- Trigger polling and claim generation are automated, but still prototype-grade.
- Platform outage checks are simulated.
- Razorpay order creation and verification are implemented; production payout hardening is still limited.

---

## Mission & Impact

In India, a single disrupted evening shift can wipe out 20-30% of a delivery partner's weekly income. This isn't just about "rain" - it's about the hours a worker never gets the chance to work. InsuriFyx aims to bridge this gap by providing an automated safety net that respects the time and effort of the gig workforce.

---

## Pitch Deck

https://drive.google.com/file/d/136mdF3juqC4BisELrKttuGIM93XcwEsZ/view?usp=sharing
