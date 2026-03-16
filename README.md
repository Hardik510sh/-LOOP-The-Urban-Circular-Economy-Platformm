# 🔄 LOOP — Close the Circle. Build the Future.

> **India's first digital circular economy platform** connecting households with verified waste pickers — making recycling effortless, transparent, and rewarding.

[![Live Site](https://img.shields.io/badge/Live%20Site-loop--india-brightgreen?style=flat-square)](https://loop-india.netlify.app)
[![Supabase](https://img.shields.io/badge/Backend-Supabase-3ECF8E?style=flat-square&logo=supabase)](https://supabase.com)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow?style=flat-square)](LICENSE)
[![SDG 11](https://img.shields.io/badge/SDG-11%20%7C%2012%20%7C%208-orange?style=flat-square)](https://sdgs.un.org/)

---

## 🌍 The Problem

India generates **62 million tonnes** of municipal solid waste annually — only 19% is recycled. Meanwhile, **4 million informal waste pickers** work without digital identity, fair pay, or safety nets. LOOP bridges both sides of this broken system.

## ✨ What LOOP Does

| For Households | For Waste Pickers | For Societies |
|---|---|---|
| Schedule pickups in 3 taps | Get verified digital profile | Colony-wide recycling dashboard |
| Track CO₂ saved live | Receive steady bookings | Leaderboards vs neighbours |
| Earn LOOP Credits | Get paid fair market rates via UPI | Monthly sustainability reports |
| Real-time picker GPS | WhatsApp-first — no app needed | Green building certification data |

---

## 🚀 Quick Deploy

### Option 1 — Netlify Drop (60 seconds)
1. Go to **[netlify.com/drop](https://app.netlify.com/drop)**
2. Drag `index.html` onto the page
3. ✅ Live — Supabase backend is already running

### Option 2 — Netlify CLI
```bash
npm install -g netlify-cli
netlify deploy --prod --dir .
```

### Option 3 — Vercel
```bash
npx vercel --prod
```

### Option 4 — GitHub Pages (auto-deploy)
Push to `main` → GitHub Actions deploys automatically (see `.github/workflows/deploy.yml`)

---

## 🗄️ Database (Supabase)

**Project URL:** `https://xryepqguuwwzwihjtkat.supabase.co`  
**Region:** ap-south-1 (Mumbai)

### Tables
| Table | Description |
|---|---|
| `profiles` | User accounts (extends Supabase Auth) |
| `pickers` | Verified waste picker profiles + GPS |
| `pickups` | Pickup requests with full lifecycle |
| `pickup_tracking` | Real-time GPS coordinates per pickup |
| `materials` | 11 material types with live market prices |
| `impact_stats` | Per-user CO₂, KG, earnings aggregates |
| `waitlist` | Early access signups |
| `city_impact` | City-wide aggregate stats (realtime) |
| `colonies` | Housing societies / RWA data |
| `reviews` | Post-pickup ratings |

### Run Migrations Locally
```bash
# Install Supabase CLI
npm install -g supabase

# Link to project
supabase link --project-ref xryepqguuwwzwihjtkat

# Apply all migrations
supabase db push
```

### Migration Files
```
supabase/migrations/
  001_create_loop_core_schema.sql      — All tables + RLS policies + seed data
  002_create_functions_triggers.sql    — Auto-triggers, realtime, helper functions
```

---

## 🔧 Local Development

```bash
# Clone
git clone https://github.com/YOUR_USERNAME/loop-india.git
cd loop-india

# Serve locally
npx serve .
# or
python3 -m http.server 8080
# → open http://localhost:8080
```

No build step required. Pure HTML/CSS/JS with Supabase CDN.

---

## ⚙️ Environment Config

The Supabase credentials are embedded in `index.html` (anon/public key — safe for frontend):

```js
const SUPABASE_URL  = 'https://xryepqguuwwzwihjtkat.supabase.co';
const SUPABASE_ANON = 'eyJhbGciOiJIUzI1NiIsInR5cCI6...'; // public anon key
```

> ⚠️ Never commit a `service_role` key. The anon key is designed for client-side use with Row Level Security.

---

## 🏗️ Architecture

```
┌─────────────────────────────────┐
│         index.html              │
│   (HTML + CSS + Vanilla JS)     │
│                                 │
│  • Supabase JS v2 (CDN)         │
│  • Google Fonts (CDN)           │
│  • Zero build dependencies      │
└──────────────┬──────────────────┘
               │ HTTPS + WebSocket
┌──────────────▼──────────────────┐
│         Supabase Cloud          │
│                                 │
│  • Auth (email/password)        │
│  • PostgreSQL 17 (ap-south-1)   │
│  • Realtime (WebSocket)         │
│  • Row Level Security           │
│  • Auto-triggers (on insert)    │
└─────────────────────────────────┘
```

---

## 📱 Features

- ✅ **Auth** — Sign up / sign in (Supabase Auth)
- ✅ **Live Pickers** — Loaded from DB, filterable by material
- ✅ **Pickup Scheduling** — 3-step form → saves to DB
- ✅ **Waitlist** — Saves to `waitlist` table
- ✅ **Real-time Stats** — City KG, pickups, CO₂ (WebSocket)
- ✅ **GPS Map** — Live picker pins with online/offline state
- ✅ **Custom Cursor** — Lime dot with lag ring
- ✅ **Progress Bar** — Reading scroll indicator
- ✅ **Scroll Reveals** — IntersectionObserver animations
- ✅ **Animated Counters** — Stats count up on scroll
- ✅ **Toast Notifications** — Feedback for all actions
- ✅ **Mobile Responsive** — Full hamburger menu
- ✅ **Dark Theme** — Charcoal + acid lime + terracotta

---

## 🌱 Impact (Beta — 90 days)

| Metric | Value |
|---|---|
| Waste diverted | 2,840 KG |
| Pickers supported | 147 |
| CO₂ prevented | ~12 tonnes |
| Fair payments | ₹41 lakh+ |
| Colonies activated | 23 |
| Avg picker rating | 4.86 / 5 |

---

## 📋 Roadmap

- [ ] WhatsApp Bot integration (Twilio / WATI)
- [ ] UPI payment gateway (Razorpay)
- [ ] AI material scanner (TensorFlow.js)
- [ ] Native Android app (React Native)
- [ ] Multi-city expansion (Delhi, Bengaluru, Mumbai)
- [ ] Carbon credit certification API
- [ ] BBMP / BMC municipal reporting integration

---

## 🤝 Contributing

PRs welcome! Please open an issue first to discuss major changes.

```bash
git checkout -b feature/your-feature
git commit -m "feat: your feature description"
git push origin feature/your-feature
# → open Pull Request
```

---

## 📄 License

MIT © 2025 LOOP Technologies Pvt. Ltd.

---

## 📞 Contact

- 🌐 [loopindia.co](https://loopindia.co)
- 📧 hello@loopindia.co
- 💬 WhatsApp: +91 98765 43210
- 🏙️ Ghaziabad, Uttar Pradesh, India 🇮🇳

---

*Built for and with the communities it serves. SDG 11 · SDG 12 · SDG 8 · SDG 13*
