<div align="center">

# 🏢 OTU Capstone Project

**Welcome to the official GitHub organization for our Ostim Technical University Software Engineering Capstone Project.**

---

<h1 align="center"> Rotakur: Unified Corporate Fleet & Operations Marketplace</h1>

<p align="center">
  We are redefining the global mobility market by bridging the gap between B2B corporate fleets and B2C end-users. Moving beyond simple ride-hailing and static hourly rentals, Rotakur is a fully-fledged <b>B2B SaaS + B2C Marketplace hybrid platform</b>. By bringing traditional, fragmented transportation processes under strict digital orchestration, we maximize operational margins, eliminate dead mileage, and provide an autonomous allocation engine powered by advanced AI and real-time telemetry.
</p>

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

### 🏗️ 3 Main Architectural Layers

Our system is built upon a strictly isolated, highly scalable PostgreSQL-first infrastructure, divided into three core pillars:

1. **B2B Corporate Automation Layer:** A multi-tenant SaaS dashboard where companies manage their internal transportation policies, exclusive driver–vehicle assignments, S3/MinIO cloud document storage, and multi-level approval workflows. Fully secured behind granular Role-Based Access Control (Admin, Assistant, Finance, Driver).
2. **B2C Public Marketplace & RAG Concierge:** A customer-facing portal where individual users discover transportation services, define multi-stop itineraries, and place orders. It features an integrated Gemini-powered RAG chatbot for natural language assistance and real-time trip tracking.
3. **Shared Orchestration Core (The Atomic Bridge):** The engine that unites both worlds. B2C orders atomically generate B2B reservations and driver tasks within a single database transaction. Status changes, GPS telemetry, and Expected vs. Realized P&L (Profit & Loss) metrics are bidirectionally synchronized, creating a single source of truth.

<br />

### 🧠 AI & Engineering Layer (The X-Factors)

The proprietary technologies and deep engineering modules that transform Rotakur from a standard dashboard into an autonomous operations infrastructure:

* **NLP Smart Dispatcher & Context-Aware Chatbot:** Powered by Google Gemini 2.5 Flash and `pgvector`. Extracts structured reservation data directly from WhatsApp-style raw text, and drives a Redis-cached RAG chatbot that understands the active marketplace context.
* **OSRM Multi-Stop Routing & Dynamic Geofencing:** Replaced basic straight-line math with real road-network polyline decoding via OSRM. Features dynamic city-level bounding boxes and strict POI protection (locking critical infrastructure like airports/terminals) to prevent phantom bookings.
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
- **Fleet & Personnel Management** — Full CRUD for staff and strict multi-tenant vehicle registries (Sedan, SUV, VIP), exclusive driver–vehicle assignments, and DEFRA 2024 CO₂ coefficient tracking.
- **Reservation & OSRM Routing** — Transfer & allocation types, multi-stop (waypoint) routing powered by OSRM, Geofence map validation, and Gemini 2.5 Flash NLP for parsing reservations from raw text.
- **Task Management (Kanban)** — Drag-and-drop 3-column Kanban board (`Pending → In Progress → Completed/Failed`), overdue auto-fail logic, and strict overlapping trip lock.
- **Finance & Expected vs. Realized P&L** — Real-time margin tracking comparing OSRM-derived expected operational costs against manually realized revenue. Dual-series ApexCharts, dynamic date filters, and PDF/Excel/CSV exports.
- **S3/MinIO Document Management** — Polymorphic cloud storage for official corporate, vehicle, and driver documents with drag-and-drop uploads and 15-minute presigned secure URLs.
- **Master-Detail Settings Hub** — 4-tab configuration panel (Profile, Company, Security, Preferences) including MinIO-backed company logo upload and system-wide dark mode.
- **Analytics & U-ETDS Compliance** — Live ESG/CO₂ tracking against corporate targets, and a fully compliant automated T.C. U-ETDS official regulatory reporting screen.

#### B2C Public Marketplace
- **Service Discovery & RAG Chatbot** — Filter by service type and passenger count. Includes a floating RAG-powered Gemini Chatbot (Redis-cached) for natural language marketplace assistance.
- **Smart Booking & AI Surge Pricing** — Nominatim geocoding with city-level dynamic bounding boxes. Fares are calculated using **Gemini AI Dynamic Pricing** factoring in peak-hour multipliers, demand density, and passenger count.
- **Carpooling (Shared Ride) Engine** — Intelligent matching algorithm that pairs compatible B2C orders within a ±2-hour window and 20km radius, applying a 20% discount and calculating exact CO₂ savings.
- **Order Tracking & Trust Score** — Real-time status sync with B2B backend, plus 1–5 star ratings that feed directly into the NLP-analyzed driver Trust Score engine.

#### Driver Panel
- **Task Dashboard & Time-Window Enforcement** — Assigned trips with a strict early/late start window validation (automatically blocks starts >120m early), and 15-second polling.
- **Live GPS Telemetry** — `watchPosition` with VueUse throttled backend persistence (max 1 req/15s) recording true drop-off coordinates for accurate P&L and ESG calculations.
- **My Documents** — Direct mobile-friendly access to S3-backed personal and vehicle documents.

#### Infrastructure & UX
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
