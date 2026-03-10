# Tamago — Product Requirements Document v3

**Version:** 3.0 (Conversational Voice + React Native)
**Date:** 2026-03-11
**Author:** Kato (AI Chief of Staff)
**Status:** Ready for Implementation
**Sprint:** 3-5 Day MVP
**Primary Target:** Intentional Meal Preppers
**Tech Stack:** React Native + Expo + NativeWind + Supabase

---

## 1. Executive Summary

**Tamago** is a voice-first, gamified cooking app for 25-40yo home cooks who meal prep. Think Duolingo meets meal prep — but with a **conversational voice interface** that feels like chatting with a cooking coach who knows your fridge.

**North Star Metric:** Users who complete 3+ cooking sessions in Week 1 have 4x higher Week 12 retention.

**MVP Scope:** Cook Now + Meal Prep flows (Meal Prep is the secret sauce).

**Key Differentiator:** Conversational voice flow — users walk through their kitchen, describe what they have, and Tamago asks clarifying questions to generate a personalized meal prep plan.

---

## 2. Problem Statement

Home cooks aged 25-40 who meal prep weekly face three compounding problems:

1. **Decision paralysis** — "What should I cook this week?" leads to scrolling 30+ minutes, then defaulting to the same 5 meals
2. **No structured progression** — Unlike fitness or language learning, cooking has no skill tree
3. **Friction in planning** — Static forms and dropdowns don't match how people actually think about cooking ("I have chicken, rice, and some teriyaki... what can I make?")

**Why now:**
- Meal prep is mainstream (SouperCubes, TikTok meal prep = billions of views)
- Voice AI costs dropped 90% in 2025 (Whisper free, ElevenLabs generous free tier)
- Conversational AI (ChatGPT, Claude) trained users to talk naturally to apps
- No one combines conversational voice + gamification + meal prep

**Tamago's wedge:** Conversational voice-first meal planning = unoccupied intersection.

---

## 3. Target User Segments

### Primary: "Prep-Day Priya" (Intentional Meal Prepper)
- **Age:** 28, software engineer, lives with partner
- **Cooking:** Meal preps every Sunday (3-4 hours), cooks dinner 2-3x/week
- **Pain:** Repeats same 6 meals. Recipe discovery is overwhelming.
- **Motivation:** Wants variety without decision fatigue. Loves streaks (has 400-day Duolingo streak)
- **LTV (90-day):** $450-540
- **Retention:** 60% Week 12 if 3+ cooks in Week 1

### Secondary: "Level-Up Leo" (Gym Bro Adjacent)
- **Age:** 34, marketing manager, cooking for family of 3
- **Cooking:** Cooks dinner 4-5x/week, weekend batch cooking
- **Pain:** Wants to go beyond basics but doesn't know how
- **Motivation:** Competitive — wants to feel like he's progressing
- **LTV (90-day):** $320-400

---

## 4. Multi-Flow Architecture

### Flow Philosophy
**Simple base → Conversational funnel → Personalized experience**

### Two MVP Flows

| Flow | User Intent | MVP? | Description |
|------|-------------|------|-------------|
| **Cook Now** | "What's for dinner tonight?" | ✅ Yes | One meal, immediate. <20 min recipes. |
| **Meal Prep** | "I'm cooking 3-5 meals at once" | ✅ Yes | **Conversational voice flow** — user describes fridge, Tamago asks clarifying questions, generates personalized plan. |

### Phase 2+ (Post-MVP)
- Macro Meals (gym bro flow)
- Host Dinner (dinner party flow)
- TikTok creator import

---

## 5. Onboarding (90 seconds max)

### Screen 1: Welcome (10 sec)
```
┌─────────────────────────────────┐
│  🍳 Tamago                      │
│                                 │
│  "What's for dinner?"           │
│                                 │
│  [Get Started]                  │
└─────────────────────────────────┘
```

### Screen 2: Primary Intent (15 sec)
```
┌─────────────────────────────────┐
│  How do you usually cook?       │
│                                 │
│  📦 I meal prep                 │
│     (cook 3-5 meals at once)    │
│                                 │
│  🍽️  Just tonight              │
│     (one meal at a time)        │
│                                 │
│  [Skip for now]                 │
└─────────────────────────────────┘
```

### Screen 3: Weekly Theme Preference (20 sec)
```
┌─────────────────────────────────┐
│  Pick a cuisine theme for       │
│  this week (optional):          │
│                                 │
│  [🥢 Asian]  [🍝 Italian]       │
│  [🌮 Mexican] [🍛 Indian]       │
│  [🥗 Mediterranean] [No Theme]  │
│                                 │
│  [Continue]                     │
└─────────────────────────────────┘
```

### Screen 4: Voice Setup (15 sec)
```
┌─────────────────────────────────┐
│  Quick question:                │
│                                 │
│  Want to talk to Tamago?        │
│  "I have chicken and rice..."   │
│                                 │
│  [Enable Voice] [Maybe Later]   │
│                                 │
│  (Takes 10 sec to set up)       │
└─────────────────────────────────┘
```

---

## 6. Home Screen

```
┌─────────────────────────────────┐
│  Good evening, Priya 👋         │
│                                 │
│  🔥 Week 3 streak! (2/3 meals)  │
│  ▓▓▓▓▓▓▓▓▓░░░░░ Level 12       │
│                                 │
│  ┌─────────────────────────┐   │
│  │ 🎤 "Hey Tamago, what's  │   │
│  │     for dinner?"        │   │
│  │     [Hold to Speak]     │   │
│  └─────────────────────────┘   │
│                                 │
│  This Week: Japanese Theme 🇯🇵   │
│  [Mon✓] [Tue✓] [Wed] [Thu]     │
│                                 │
│  ┌─────────────────────────┐   │
│  │ 🍳 Cook Now             │   │
│  │ Quick dinner tonight    │   │
│  │ → Chicken Teriyaki      │   │
│  └─────────────────────────┘   │
│                                 │
│  ┌─────────────────────────┐   │
│  │ 🍱 Meal Prep            │   │
│  │ Sunday batch cooking    │   │
│  │ → Talk to Tamago        │   │
│  └─────────────────────────┘   │
│                                 │
│  [Home] [Explore] [Profile]     │
└─────────────────────────────────┘
```

---

## 7. Flow Details

### 7.1 Cook Now Flow (One Meal, Immediate)

**User Journey:**
```
Home → Cook Now → Recipe Grid (filtered <20 min, difficulty tags) → Select → Cook Mode → Complete
```

**Recipe Grid Filters:**
- Time: <15 min, <20 min, <30 min
- Cuisine: Asian, Italian, Comfort, etc.
- Difficulty: Easy, Medium, Hard (for ambitious cooks)

### 7.2 Meal Prep Flow — CONVERSATIONAL VOICE (The Secret Sauce)

**User Journey:**
```
Home → Meal Prep → Voice Conversation → Plan Generated → Cook Mode → Storage Guide → Complete
```

**Conversational Voice Flow:**

```
┌─────────────────────────────────┐
│  🎤 Tamago: "Hey! What are you  │
│  looking to prep this week?"    │
│                                 │
│  👤 User: "I need 5 meals for   │
│  the week, have a few events.   │
│  I have beef, rice, beans,      │
│  broccoli, spinach, carrots,    │
│  and some teriyaki sauce. Can   │
│  we do something Japanese?"     │
│                                 │
│  [Listening...]                 │
│                                 │
│  [Submit] [Cancel]              │
└─────────────────────────────────┘
```

**Tamago Follow-Up Questions (AI-generated):**
```
┌─────────────────────────────────┐
│  🎤 Tamago: "Got it! A few      │
│  quick questions:               │
│                                 │
│  1. How long will you freeze    │
│     these meals? (1-2 weeks?)   │
│                                 │
│  2. What portion size? (Single  │
│     servings or family-sized?)  │
│                                 │
│  3. How healthy? (Low-carb,     │
│     balanced, or indulgent?)    │
│                                 │
│  4. Can you grab Japanese curry │
│     cubes nearby?               │
│                                 │
│  [Answer by Voice]              │
└─────────────────────────────────┘
```

**Generated Plan:**
```
┌─────────────────────────────────┐
│  🍱 Your Japanese Meal Prep     │
│                                 │
│  Based on your fridge + prefs:  │
│                                 │
│  🍗 Chicken Teriyaki Bowl       │
│     (4 servings, 25 min)        │
│     🧊 Freeze: 3 months         │
│     🔥 Reheat: 3 min            │
│                                 │
│  🍛 Japanese Curry Rice         │
│     (4 servings, 40 min)        │
│     🧊 Freeze: 2 months         │
│     🔥 Reheat: 4 min            │
│                                 │
│  🥗 Spinach Gomae               │
│     (Side dish, 10 min)         │
│     🧊 Freeze: 1 month          │
│                                 │
│  Total: ~75 min cook time       │
│  5 meals for the week ✓         │
│                                 │
│  [Start Cooking] [Adjust Plan]  │
└─────────────────────────────────┘
```

**Key Design Principles:**
- **Conversational, not form-based** — User talks naturally, Tamago asks clarifying questions
- **Voice-led, but UI supports** — User can switch to typing/tapping anytime
- **Contextual follow-ups** — Tamago remembers fridge inventory, preferences, past cooks
- **Iterative refinement** — "Adjust Plan" lets user tweak (swap protein, change cuisine)

---

## 8. Voice Architecture (Conversational Mode)

### Research Directions

**Inspired by:**
- ChatGPT Voice Mode (flowy, interruptible, contextual)
- Claude's conversational style (warm, clarifying questions)
- Gemini's multi-turn memory (remembers context across turns)

### MVP Approach

**Phase 1 (MVP — 3-5 days):**
- Wake word + push-to-talk ("Hold to Speak")
- Single-turn voice input (user speaks, Tamago processes, responds)
- Follow-up questions via text (with voice reply option)
- Fallback: Tap/keyboard input if voice fails

**Phase 2 (Post-MVP — Weeks 2-4):**
- Multi-turn conversational mode (interruptible, like ChatGPT Voice)
- Voice-first throughout entire flow
- Contextual memory across sessions ("Last week you made teriyaki, want to try something different?")

**Phase 3 (Month 2+):**
- Ambient voice mode (no wake word, always listening during cook)
- Proactive suggestions ("You usually prep on Sunday, want to start?")

### Technical Research Needed

| Question | Owner | ETA |
|----------|-------|-----|
| ElevenLabs conversational API? | Yuki | 1 day |
| Whisper streaming for interruptible input? | Yuki | 1 day |
| Expo Speech module capabilities? | Yuki | 1 day |
| ChatGPT Voice Mode teardown (how do they do it?) | CRI | 2 days |

---

## 9. Gamification Mechanics (Weekly Streaks)

### XP System (Revised)

| Action | XP | Rationale |
|--------|----|-----------|
| Complete first recipe | 100 XP | Onboarding completion bonus |
| Complete a recipe | 50 XP | Base reward |
| First time cooking a cuisine | 25 XP | Encourages variety |
| Complete under par time | 15 XP | Speed bonus |
| **Upload fridge balance** | **75 XP** | **Reduces food waste, recurring hook** |
| **Log reheating a meal** | **25 XP** | **Confirms consumption, not just prep** |
| Rate a recipe | 5 XP | Feedback loop |
| Daily login | 10 XP | Habit formation |
| **Weekly theme completion** | **150 XP** | **Encourages planned variety** |
| Photo upload | 10 XP | Social sharing potential |

### Weekly Streaks (Strava-Style)

**Logic:**
- Streak = weeks with 2+ cooking sessions (not daily)
- Traveling? Still maintain streak with 2 cooks that week
- More sustainable than daily streaks

| Milestone | Badge | Retention Hook |
|-----------|-------|----------------|
| 1 week | "Week Warrior" | First win |
| 4 weeks | "Monthly Prep Master" | Habit formed |
| 12 weeks | "Quarterly Chef" | Long-term commitment |
| 52 weeks | "Year of Tamago" (Legendary) | Ultimate achievement |

### Level Progression (Batched)

| Level | Title | XP Required | Unlock |
|-------|-------|-------------|--------|
| 1-5 | Kitchen Rookie | 0-500 | Basic recipes |
| 6-10 | Home Cook | 500-1,500 | Intermediate recipes |
| 11-20 | Sous Chef | 1,500-5,000 | Advanced recipes + weekly themes |
| 21-30 | Head Chef | 5,000-12,000 | Expert recipes |
| 31-40 | Master Chef | 12,000-25,000 | Create & share recipes |
| 41-50 | Kitchen Legend | 25,000+ | Gold profile badge |

---

## 10. Technical Architecture (React Native + Expo)

### Stack

| Layer | Technology |
|-------|------------|
| **Framework** | React Native (cross-platform) |
| **Styling** | NativeWind (Tailwind for RN) |
| **SDK** | Expo SDK (managed workflow) |
| **Backend** | Supabase (Postgres + Auth + Storage) |
| **Voice STT** | Expo Speech Recognition + Whisper API fallback |
| **Voice TTS** | ElevenLabs API + Expo Speech fallback |
| **State** | Zustand (lightweight) |
| **Navigation** | Expo Router (file-based) |

### Project Structure

```
tamago/
├── app/                          # Expo Router (file-based routing)
│   ├── (tabs)/                   # Tab navigation
│   │   ├── index.tsx             # Home screen
│   │   ├── explore.tsx           # Recipe browser
│   │   └── profile.tsx           # User stats
│   ├── onboarding/               # Onboarding flow
│   ├── cook-now/                 # Cook Now flow
│   ├── meal-prep/                # Meal Prep conversational flow
│   └── _layout.tsx               # Root layout
├── components/
│   ├── RecipeCard.tsx
│   ├── VoiceBar.tsx
│   ├── WeekStreak.tsx
│   ├── LegoCookingPicker.tsx
│   └── StorageGuide.tsx
├── services/
│   ├── voice.ts                  # Voice orchestration (STT + TTS)
│   ├── supabase.ts               # Supabase client
│   ├── gameEngine.ts             # XP, streaks, levels
│   └── notifications.ts          # Push notifications
├── store/
│   ├── useUserStore.ts           # User state (XP, level, streak)
│   ├── useRecipeStore.ts         # Recipe data
│   └── useSessionStore.ts        # Active cook state
├── data/
│   └── recipes.json              # 10 curated recipes
├── assets/                       # Images, fonts, sounds
├── app.json                      # Expo config
├── tailwind.config.js            # NativeWind config
└── package.json
```

### Expo Modules Needed

| Module | Purpose |
|--------|---------|
| `expo-speech` | TTS playback |
| `expo-av` | Audio recording (for STT) |
| `expo-notifications` | Streak reminders |
| `expo-background-fetch` | Weekly streak calculation |
| `expo-camera` | Dish photo upload |
| `expo-image-picker` | Fridge photo upload |

### Supabase Schema (Unchanged)

```sql
-- Same schema as PRD v2, confirmed RN-compatible
CREATE TABLE users (...);
CREATE TABLE recipes (...);
CREATE TABLE cooking_sessions (...);
CREATE TABLE user_achievements (...);
```

---

## 11. MVP Feature Priorities

### P0 (Must Have — Days 1-3)
- [ ] Onboarding (4 screens, intent picker)
- [ ] Home screen (voice bar, week scroller, flow cards)
- [ ] Cook Now flow (recipe grid → cook mode)
- [ ] **Meal Prep conversational voice flow** (the secret sauce)
- [ ] Voice bar (push-to-talk, STT parsing)
- [ ] Voice TTS (ElevenLabs pre-gen + fallback)
- [ ] Gamification (XP, weekly streaks, levels, badges)
- [ ] Timers (concurrent, haptic + sound)

### P1 (Should Have — Days 4-5)
- [ ] Profile screen (stats, achievements, level badge)
- [ ] Push notifications (streak reminders, daily picks)
- [ ] Meal prep mode (storage instructions, "eat by" reminders)
- [ ] Supabase sync (user profile, cooking sessions)
- [ ] Offline support (cache recipes, no voice offline)

### P2 (Phase 2 — Post-MVP)
- [ ] Multi-turn conversational voice (interruptible, ChatGPT-style)
- [ ] Fridge balance upload (photo + AI ingredient detection)
- [ ] Reheating log (confirmation + XP bonus)
- [ ] Weekly themes (cuisine-based meal suggestions)

---

## 12. 3-5 Day Sprint Plan (React Native)

### Day 1: Foundation + Data Layer
- [ ] Expo project setup (`npx create-expo-app tamago`)
- [ ] Install dependencies (NativeWind, Supabase, Zustand)
- [ ] Data models (Recipe, CookingStep, UserProfile, Achievement)
- [ ] Write 10 recipes in `data/recipes.json` (with meal_prep metadata)
- [ ] RecipeStore + UserStore (AsyncStorage persistence)
- [ ] GameEngine (XP, levels, weekly streaks, achievements)
- [ ] Tab navigation skeleton (Home, Explore, Profile)

### Day 2: Onboarding + Home Screen
- [ ] Onboarding screens (4 screens, intent picker)
- [ ] HomeView (voice bar, week scroller, flow cards)
- [ ] Flow routing logic (intent → correct UI)
- [ ] Weekly theme display
- [ ] RecipeCard + grid layout for Explore tab

### Day 3: Cook Mode + Voice MVP
- [ ] CookingView (full-screen step-by-step)
- [ ] StepView (large text, progress bar, tip section)
- [ ] CompletionView (XP animation, streak update, badges)
- [ ] VoiceService (expo-speech for TTS, expo-av for STT)
- [ ] ElevenLabs integration (pre-gen TTS for 10 recipes)
- [ ] Voice command parsing (basic: "next", "repeat", "done")
- [ ] TimerService (concurrent timers, background support)

### Day 4: Meal Prep Conversational Flow + Polish
- [ ] MealPrepView (conversational voice flow)
- [ ] Follow-up question logic (AI-generated clarifying questions)
- [ ] Plan generation (display generated meal plan)
- [ ] StorageGuideView (fridge/freezer instructions)
- [ ] ProfileView (stats, achievements, level badge)
- [ ] AchievementGrid (locked/unlocked badges)
- [ ] NotificationService (streak reminders, daily picks)
- [ ] App icon + theming (warm colors: amber, cream, terracotta)

### Day 5: Integration + Ship
- [ ] Supabase setup (create project, tables, auth)
- [ ] SupabaseService (sync user profile, cooking sessions)
- [ ] End-to-end testing (onboarding → cook → XP → streak)
- [ ] Edge case testing (kill app mid-cook, offline, background timer)
- [ ] App Store metadata (screenshots, description, keywords)
- [ ] TestFlight build → internal testing
- [ ] Submit to App Store review

---

## 13. Success Metrics

| Metric | Week 1 Target | Month 1 Target |
|--------|---------------|----------------|
| D1 Retention | >40% | >40% |
| D7 Retention | >20% | >25% |
| D30 Retention | — | >15% |
| Cooks completed / DAU | >0.8 | >1.0 |
| **Voice usage rate** | >50% | >60% |
| **Weekly streak maintenance (2+ cooks/week)** | >25% | >40% |
| **Fridge upload rate** | >10% | >20% |
| **Reheating log rate** | >30% | >50% |

**North Star:** 3+ cooking sessions in Week 1 = 4x Week 12 retention.

---

## 14. Open Questions for Xavier

1. **Conversational voice depth** — MVP: single-turn with text follow-ups. Phase 2: full multi-turn (ChatGPT Voice style). Is this the right phased approach?
2. **Weekly streak threshold** — 2 cooks/week for streak maintenance. Too low? Too high?
3. **Fridge upload bonus** — 75 XP for uploading fridge photo at end of week. Right incentive?
4. **React Native vs SwiftUI** — RN gives us cross-platform + faster iteration. Any concerns for MVP?
5. **Expo vs bare RN** — Expo managed workflow is faster but has some native module limitations. Greenlight for MVP?

---

*PRD v3 incorporates: conversational voice flow (Xavier review), weekly streaks (Strava-style), React Native + Expo stack, fridge upload + reheating log bonuses. Ready for Yuki tech spec validation + iOS/Android build agents.*
