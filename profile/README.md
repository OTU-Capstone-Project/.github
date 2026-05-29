<div align="center">

# 🏢 OTU Capstone Project

**Welcome to the official GitHub organization for our Ostim Technical University Software Engineering Capstone Project.**

---

<h1 align="center"> Rotakur: Unified Fleet Supply & Mobility Marketplace</h1>
<p align="center">
  <i>An AI-driven logistics platform optimizing operational efficiency and sustainable CO2 reduction by connecting corporate fleets directly to B2B event organizations and B2C marketplace users.</i>
</p>

</div>

<!-- Başlık grubu ile ana özet arasında profesyonel boşluk katmanı -->
<br />
<br />

<p align="justify">
  We are redefining the global mobility market by bridging the gap between enterprise event organizers, B2B corporate fleets, and B2C end-users. Moving beyond simple ride-hailing and static hourly rentals, Rotakur is a fully-fledged <b>Multi-Tenant B2B Procurement SaaS + B2C Marketplace hybrid infrastructure</b>. By bringing traditional, fragmented transportation procurement and driver orchestration under strict digital control, we maximize operational margins, eliminate dead mileage, and provide an autonomous allocation engine powered by advanced AI and real-time telemetry.
</p>

<br />
<br />

<div align="center">
  <h3>🎬 Executive Technical Demo</h3>
  <a href="https://www.youtube.com/watch?v=cwtYrzFHKOc">
    <img src="https://img.youtube.com/vi/cwtYrzFHKOc/maxresdefault.jpg" alt="Rotakur Executive Technical Demo" width="100%" style="max-width: 850px; border-radius: 12px; box-shadow: 0 10px 30px rgba(0,0,0,0.5); border: 1px solid #333;" />
  </a>
  <p align="center">
    <sub><i>Click the thumbnail above to watch our 1-Minute Executive Technical Demo on YouTube.</i></sub>
  </p>
</div>

<br />

### 🏗️ 4 Core Architectural Pillars

Our system is built upon a strictly isolated, highly scalable PostgreSQL-first infrastructure, divided into four interconnected enterprise layers:

1. **B2B Organization Portal (The Demand Side):** An elite multi-step workspace where corporate event managers design large-scale logistics portfolios, seed complex participant/guest matrices, define strict vehicle requirement profiles, and manage high-level executive financial approvals.
2. **B2B Fleet Operator Dashboard (The Supply Side):** A dedicated multi-tenant SaaS console where transport operators handle internal company policies, driver registries, vehicle asset compliance, and S3/MinIO cloud document lifecycles.
3. **Dual-Tenant Procurement Hub (Dealer Hub Marketplace):** The core bidding nexus where organization and fleet operators collide. Features role-locked access workflows ensuring that operational staff handle driver/vehicle assignments while financial staff manage tax overrides, margins, and audit-logged contract negotiations.
4. **B2C Public Marketplace & Shared Core:** A customer-facing portal for individual bookings and multi-stop itineraries, atomically bound to the shared core engine so B2C requests dynamically compile into standard driver tasks and cross-tenant telemetry pipelines in a single unified transaction block.

<br />

### 🧠 AI & Engineering Layer (The X-Factors)

The proprietary technologies and deep engineering modules that transform Rotakur from a standard dashboard into an autonomous operations infrastructure:

* **NLP Smart Dispatcher & Context-Aware Chatbot:** Powered by Google Gemini 2.5 Flash and `pgvector`. Extracts structured reservation data directly from WhatsApp-style raw text, and drives a Redis-cached RAG chatbot that understands the active marketplace context.
* **OSRM Multi-Stop Routing & Dynamic Geofencing:** Replaced basic straight-line math with real road-network polyline decoding via OSRM. Features dynamic city-level bounding boxes and strict POI protection (locking critical infrastructure like airports/terminals) to prevent phantom bookings.
* **Dual-Tenant State Machine & Audit Negotiation:** Governs complex procurement workflows across distinct corporate entities. Features a locked state machine (`DRAFT_OPERATIONAL` → `PENDING_FINANCE` → `UNDER_FINANCIAL_REVIEW` → `APPROVED`) driven by a context-aware chat log allowing role-bound financial revisions with strict data isolation.
* **AI Surge Pricing & Real-Time P&L Engine:** A dynamic pricing engine that calculates binding fares based on peak-hour multipliers and demand density. Simultaneously, the system computes the exact operational cost (fuel + depreciation) per OSRM distance, surfacing the Net P&L margin *before* the trip even starts.
* **Sustainable Carpooling (Shared Ride) Algorithm:** A smart matching engine that pairs compatible B2C orders within a ±2-hour window and a 20km radius (Haversine). It merges trips, applies automated discounts, and tracks exact DEFRA-compliant CO₂ savings for ESG reporting.
* **Driver Trust Score & U-ETDS Compliance:** Processes passenger feedback using NLP sentiment analysis to calculate a weighted safety and service score. All trip data is seamlessly structured for automated regulatory reporting to the Turkish Ministry of Transport (U-ETDS).

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
| **Auth & RBAC** | Dual-chain JWT (Company vs Client) · Granular RBAC (Coordinator, Event Manager, Org Dealer, Fleet Admin, Fleet Assistant, Fleet Accountant, Fleet Driver) |
| **Database** | PostgreSQL 16 · asyncpg · 14 core tables · multi-tenant `company_id` schema isolation |
| **AI** | Google GenAI SDK (Gemini 2.5 Flash) |
| **Real-time** | WebSocket (`ws/notifications`) · per-company connection pooling · auto-reconnect |
| **Infrastructure** | Docker & Docker Compose · PGAdmin 4 · Uvicorn hot-reload · Vite HMR |

</div>

<br>

---

### 📦 Completed Modules

<div align="left" style="display: inline-block; text-align: left; max-width: 800px;">

#### 🏢 B2B Organization Portal (Demand & Corporate Side)
- **Multi-Step Event Seeding Wizard** — Complex event composition across four distinct stages, featuring an integrated Step 4 initial guest/participant list pre-registration module.
- **VIP & Participant Logistics Matrix** — Dynamic tabular dashboard for managing guest segments (VIP, Protocol, Standart), flight codes, pick-up times, and hotel allocations with real-time inline CRUD.
- **Logistics Requirements Blueprint** — Automated and manual definition of vehicle segment targets (VIP Van, SUV, Sedan, Shuttle) cross-compiled directly into ready-to-broadcast open tenders.
- **Finance & Invoicing Control Tower** — Unlocks the role-bound financial evaluation workspace under the "Finans & Faturalandırma" track, allowing the **Organization Dealer** to review competitive fleet bids, manage price revisions, and enabling the **Coordinator (Ahmet Saygı)** to execute final contract approvals.

#### 🛞 B2B Fleet Operator Dashboard (Supply & Execution Side)
- **Dealer Hub Procurement Console** — Ingests live marketplace tenders, allowing **Fleet Admins & Assistants** to run operational setups, matching required vehicle segments with physical inventory plates and verified **Drivers**.
- **Fleet Financial Calculation Engine** — Intercepts operational drafts by the **Fleet Accountant** to enforce base rates, inject profit margins, handle VAT/taxation, track extra KM overage metrics, and execute official bid dispatches straight into the organization finance pipeline.
- **Fleet & Personnel Management** — Full CRUD for staff and strict multi-tenant vehicle registries (Sedan, SUV, VIP), exclusive driver–vehicle assignments, and DEFRA 2024 CO₂ coefficient tracking.
- **Reservation & OSRM Routing** — Transfer & allocation types, multi-stop (waypoint) routing powered by OSRM, Geofence map validation, and Gemini 2.5 Flash NLP for parsing reservations from raw text.
- **Task Management (Kanban)** — Drag-and-drop 3-column Kanban board (`Pending → In Progress → Completed/Failed`), overdue auto-fail logic, and strict overlapping trip lock.
- **Finance & Expected vs. Realized P&L** — Real-time margin tracking comparing OSRM-derived expected operational costs against manually realized revenue. Dual-series ApexCharts, dynamic date filters, and PDF/Excel/CSV exports.
- **S3/MinIO Document Management** — Polymorphic cloud storage for official corporate, vehicle, and driver documents with drag-and-drop uploads and 15-minute presigned secure URLs.
- **Master-Detail Settings Hub** — 4-tab configuration panel (Profile, Company, Security, Preferences) including MinIO-backed company logo upload and system-wide dark mode.
- **Analytics & U-ETDS Compliance** — Live ESG/CO₂ tracking against corporate targets, and a fully compliant automated T.C. U-ETDS official regulatory reporting screen.

#### 🛒 B2C Public Marketplace
- **Service Discovery & RAG Chatbot** — Filter by service type and passenger count. Includes a floating RAG-powered Gemini Chatbot (Redis-cached) for natural language marketplace assistance.
- **Smart Booking & AI Surge Pricing** — Nominatim geocoding with city-level dynamic bounding boxes. Fares are calculated using **Gemini AI Dynamic Pricing** factoring in peak-hour multipliers, demand density, and passenger count.
- **Carpooling (Shared Ride) Engine** — Intelligent matching algorithm that pairs compatible B2C orders within a ±2-hour window and 20km radius, applying a 20% discount and calculating exact CO₂ savings.
- **Order Tracking & Trust Score** — Real-time status sync with B2B backend, plus 1–5 star ratings that feed directly into the NLP-analyzed driver Trust Score engine.

#### 📱 Driver Panel
- **Task Dashboard & Time-Window Enforcement** — Assigned trips with a strict early/late start window validation (automatically blocks starts >120m early), and 15-second polling.
- **Live GPS Telemetry** — `watchPosition` with VueUse throttled backend persistence (max 1 req/15s) recording true drop-off coordinates for accurate P&L and ESG calculations.
- **My Documents** — Direct mobile-friendly access to S3-backed personal and vehicle documents.

#### ⚙️ Infrastructure & UX
- **Notification Engine** — WebSocket instant push + DB persistent fallback, per-role filtering, and animated Toast notifications replacing legacy alerts.
- **Global Search (⌘K)** — Command palette for instant, debounced prefetch navigation across pages, dynamic reservations, drivers, and requests.
- **Dual-Chain Authentication** — Strictly isolated B2B and B2C JWT token chains, preventing cross-domain access at the framework middleware level.
- **Split-Screen Auth & Dark Mode** — Enterprise-grade responsive auth panels, system-wide `useColorMode` toggle persisted in localStorage, with `dark:` Tailwind variants throughout.

</div>

<br>

---

### 👥 Core Team

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
