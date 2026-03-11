# Tamago — Duolingo for Cooking

**Personal sous chef in your pocket** — a conversational AI that knows your fridge, plans your week, and guides you through cooking like a trusted kitchen partner.

---

## Project Structure

```
tamago/
├── README.md              # This file
├── pipeline.json          # Pipeline stage tracking
├── prd-v3.md              # Product requirements (v3.1)
├── idea.md                # Original idea
├── research/              # LTV analysis, user research
│
└── app-rn/                # React Native app (Expo)
    ├── app/               # App screens (Home, Cook Now, Meal Prep)
    ├── services/          # API clients (ElevenLabs, Supabase, Voice)
    ├── store/             # Zustand state management
    ├── data/              # Recipe data
    ├── SETUP.md           # Setup instructions
    └── STATUS.md          # Current build status
```

**Why two folders?**
- `tamago/` = Project docs, PRDs, pipeline tracking
- `tamago/app-rn/` = Actual React Native app code

This keeps docs separate from code. All development happens in `app-rn/`.

---

## Quick Start

```bash
cd /Users/devl/clawd/projects/tamago/app-rn
npx expo start
```

Then press `i` for iOS or `a` for Android.

---

## Current Status

| Component | Status |
|-----------|--------|
| Home Screen | ✅ Complete |
| Cook Now Flow | ✅ Complete |
| Meal Prep Conversational Flow | ✅ Complete |
| ElevenLabs TTS | ✅ Integrated |
| Supabase Backend | 🔄 Schema ready, cloud pending |

**See:** `app-rn/STATUS.md` for detailed build status.

---

## Sprint Progress

| Day | Goal | Status |
|-----|------|--------|
| Day 1 | Scaffold + Home | ✅ Complete |
| Day 2 | Meal Prep + Cook Now | ✅ Complete |
| Day 3 | Voice integration | ✅ Complete (key added) |
| Day 4 | Polish + testing | 🔄 In Progress |
| Day 5 | TestFlight | ⏳ Pending |

---

## Cost Tracking

| Metric | Value |
|--------|-------|
| Budget | $10.00 |
| Spent | $0.00 (testing now) |
| Remaining | $10.00 |
| Cost per recipe | ~$0.50-0.75 |

See: `app-rn/COST-TRACKER.md`

---

## Key Decisions

1. **Multi-turn voice** — Greenlit for MVP (cost acceptable for testing)
2. **Weekly streaks** — 3 cooks/week (Strava-style, sustainable)
3. **React Native + Expo** — Cross-platform, faster iteration
4. **Focus** — Meal Prep flow is the "secret sauce"

---

## Next Steps

1. ✅ Test voice with real ElevenLabs TTS
2. ⏳ Deploy Supabase to cloud
3. ⏳ End-to-end testing
4. ⏳ TestFlight submission (optional)
