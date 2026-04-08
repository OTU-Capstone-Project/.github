<div align="center">

# 🏢 OTU Capstone Project

**Welcome to the official GitHub organization for our Ostim Technical University Software Engineering Capstone Project. We are a team of 5 senior engineering students dedicated to building enterprise-grade, AI-driven software solutions.**

---

## 🚀 Corporate Transportation & Operations Management Platform

We are redefining corporate transportation needs in the Turkish and global markets beyond a simple ride-hailing service, transforming it into a fully-fledged **B2B SaaS + B2C Marketplace hybrid platform**. By bringing traditional companies' manually operated processes under digital discipline, we aim to reduce costs and minimize the operational workload while simultaneously serving individual customers through a public marketplace.

> **Current Version: v2.5 — Production-Ready** &nbsp;|&nbsp; ~23,000+ LoC &nbsp;|&nbsp; 90+ Commits &nbsp;|&nbsp; 178 Source Files

<br>

### 🏗️ 3 Main Architectural Layers

<div align="left" style="display: inline-block; text-align: left; max-width: 800px;">

Our system is built upon the following three core operational pillars:

1. **B2B Corporate Automation Layer:** The main SaaS dashboard where companies manage their internal transportation policies, multi-level approval workflows, department-based budgeting, and driver operations — all secured behind role-based access control with four distinct user roles (Admin, Assistant, Finance, Driver).
2. **B2C Public Marketplace:** A customer-facing marketplace where individual users discover transportation services from registered companies, place orders, track trips in real time, and leave ratings — fully integrated into the same backend infrastructure through an atomic bridging mechanism.
3. **Shared Operational Core:** B2C orders automatically generate B2B reservations and driver tasks via atomic transactions. Status changes are bidirectionally synchronized between both layers, creating a single source of truth for all operational data.

</div>

<br><br>

### 🧠 AI & Engineering Layer (The X-Factors)

<div align="left" style="display: inline-block; text-align: left; max-width: 800px;">

The artificial intelligence and engineering modules that differentiate our platform and transform it into a true technology product:

* **NLP Smart Dispatcher (AI Dispatcher):** A natural language processing layer powered by **Google Gemini 2.5 Flash** that automatically extracts structured reservation data (type, locations, date, time, passenger count) from a single WhatsApp-style message. Supports Turkish relative date/time expressions ("Yarın", "Cuma saat 14:30").
* **Decision-Support Cost Estimator:** The new-reservation form automatically calculates the operational cost using the Haversine formula for route distance combined with real-world fuel price and vehicle depreciation constants (`₺4.575/km`), pre-filling the cost field while leaving the customer price field blank for manual negotiation.
* **Driver Trust Score & Safety Index:** An analytics engine that processes passenger feedback using NLP sentiment analysis (heuristic keyword matching + optional Gemini AI scoring) and calculates a weighted overall score: `rating × 0.7 + ai_sentiment_score × 0.3`, clamped to a 1.0–5.0 scale.
* **AI Carpooling & Route Optimization:** Smart optimization that identifies employees heading in the same direction using clustering algorithms, providing up to 40% cost savings.

</div>

<br>

---

### ⚙️ Technology Stack

<div align="left" style="display: inline-block; text-align: left; max-width: 800px;">

| Layer | Technologies |
|---|---|
| **Frontend** | Vue.js 3.5 · TypeScript 5.7 · Vite 6 · Tailwind CSS 4 · Vue Router 4.5 · VueUse 11 |
| **Maps & Charts** | Leaflet 1.9 · ApexCharts 5 (dual-series charts) · Nominatim / OpenStreetMap geocoding |
| **Exports** | jsPDF + AutoTable (DejaVu Sans, full Turkish support) · SheetJS / xlsx |
| **Backend** | FastAPI 0.115 · Python 3.12 · SQLAlchemy 2.0 (async) · Alembic 1.14 · Pydantic v2 |
| **Auth** | Dual-chain JWT (B2B `company_id` token + B2C `client` token, HS256) · bcrypt passwords |
| **Database** | PostgreSQL 16 · asyncpg · 12 core tables · multi-tenant `company_id` isolation |
| **AI** | Google GenAI SDK (Gemini 2.5 Flash) |
| **Real-time** | WebSocket (`ws/notifications`) · per-company connection pooling · auto-reconnect |
| **Infrastructure** | Docker & Docker Compose · PGAdmin 4 · Uvicorn hot-reload · Vite HMR |

</div>

<br>

---

### 📦 Completed Modules

<div align="left" style="display: inline-block; text-align: left; max-width: 800px;">

#### B2B Corporate Dashboard
- **Personnel Management** — Full CRUD, role assignment (Admin / Assistant / Finance / Driver), department linking, activate/deactivate guards
- **Reservation Management** — Transfer & allocation types, 5-stage approval workflow, Leaflet map preview, driver conflict detection (overlapping trip lock), past-date guard, marketplace-origin badge
- **Task Management** — 5-state flow (`Pending → Assigned → In Progress → Completed / Failed`), overdue auto-fail, forward-only status transitions, 20-second polling
- **Administrative Requests** — Leave, equipment, other, reservation-cancellation request types; bidirectional notification flow; duplicate-decision auto-close; 1-cancellation-per-reservation limit
- **Finance & P&L** — Income/expense tracking with dynamic date filters (This Month / Last Month / This Year / Custom Range), real-time Net P&L merging B2C marketplace revenue + manual entries + auto-derived operational costs, dual-series monthly bar chart (ApexCharts), PDF & Excel exports
- **Analytics** — Donut/bar charts from live data, CO₂ / ESG metrics, U-ETDS compliance screen
- **Roles & RBAC** — Custom role creation with JSONB permission maps, system role protection
- **AI Dispatcher** — Gemini 2.5 Flash NLP reservation extraction from natural language messages

#### B2C Public Marketplace
- **Service Discovery** — Filter by service type and passenger count; company cards with rating, trip count, price range, CO₂/km
- **Booking Flow** — Haversine-based distance calculation, dynamic pricing (`base_price + distance × price_per_km`), Nominatim geocoding, atomic order + reservation + task creation
- **Order Tracking** — Real-time status tracking (Pending → Accepted → In Progress → Completed), trip details, cancellation
- **Ratings** — 1–5 star + text review; feeds directly into driver Trust Score calculation

#### Driver Panel
- **Task Dashboard** — Assigned trips, start/complete actions, route map preview, 15-second polling
- **Live GPS Sharing** — `watchPosition` with throttled backend persistence (max 1 request / 15s via VueUse `useThrottleFn`), `driver_lat / driver_lng / location_updated_at` stored to DB only when trip is active
- **Cancellation Requests** — 1-per-reservation limit enforced at both frontend and backend

#### Infrastructure & UX
- **Notification System** — WebSocket instant push + DB persistent fallback; zil badge (9+), per-role filtering (Admin vs. Driver), offline catch-up on reconnect
- **Split-Screen Auth** — Full-screen brand panel + form panel for B2B and B2C login/register
- **Dark Mode** — System-wide `useColorMode` toggle (sun/moon icon), persisted in localStorage, `dark:` Tailwind variants throughout
- **Toast Notifications** — Animated fade + Y-slide, 3.5s auto-dismiss, replacing all legacy `alert()` calls

</div>

<br>

---

### 👥 Core Team & Contributors

<table>
  <tr>
    <td align="center"><b>Emre</b></td>
    <td align="center"><b>Yağız Han</b></td>
    <td align="center"><b>Zeynep Bilge</b></td>
    <td align="center"><b>Ömer Faruk</b></td>
    <td align="center"><b>Ayşegül Beyza</b></td>
  </tr>
</table>

</div>
