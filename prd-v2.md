# Tamago — Product Requirements Document v2

**Version:** 2.0 (Multi-Flow Architecture)
**Date:** 2026-03-11
**Author:** Kato (AI Chief of Staff)
**Status:** Ready for Implementation
**Sprint:** 3-5 Day MVP
**Primary Target:** Intentional Meal Preppers

---

## 1. Executive Summary

**Tamago** is a voice-first, gamified cooking app for 25-40yo home cooks who meal prep. Think Duolingo meets meal prep — interactive voice guidance, streaks, achievements, and modular "Lego cooking" that adapts to user intent.

**North Star Metric:** Users who complete 3+ cooking sessions in Week 1 have 4x higher Week 12 retention.

**MVP Scope:** Cook Now + Meal Prep flows (absorbs One-Meal Cooks as subset).

---

## 2. Problem Statement

Home cooks aged 25-40 who meal prep weekly face three compounding problems:

1. **Decision paralysis** — "What should I cook this week?" leads to scrolling 30+ minutes, then defaulting to the same 5 meals
2. **No structured progression** — Unlike fitness or language learning, cooking has no skill tree
3. **Dirty hands UX gap** — Every recipe app requires scrolling/tapping mid-cook. Hands are covered in chicken juice.

**Why now:**
- Meal prep is mainstream (SouperCubes, TikTok meal prep = billions of views)
- Voice AI costs dropped 90% in 2025 (Whisper free, ElevenLabs generous free tier)
- Duolingo proved gamification drives daily retention (DAU/MAU >50%)
- No one combines voice-first + gamification + cooking

**Tamago's wedge:** Voice-first gamified cooking = unoccupied intersection.

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

### Phase 2+: Host, TikTok Follower, One-Meal Cook
- **Host:** Infrequent (0.5x/week), premium tier opportunity ($14.99/mo)
- **TikTok Follower:** Low LTV ($60-100), high churn — ignore until Phase 3
- **One-Meal Cook:** No habit formation, price-sensitive — absorbed into Cook Now flow

---

## 4. Multi-Flow Architecture

### Flow Philosophy
**Simple base → Intelligent funnel → Personalized experience**

All users see the same home screen. Flow entry is determined by:
1. Onboarding intent selection
2. Voice command parsing
3. Contextual UI taps

### Four Flows

| Flow | User Intent | MVP? | Description |
|------|-------------|------|-------------|
| **Cook Now** | "What's for dinner tonight?" | ✅ Yes | One meal, immediate. <20 min recipes. |
| **Meal Prep** | "I'm cooking 3-5 meals at once" | ✅ Yes | Batch cook + freeze/store. Lego cooking UI. |
| **Macro Meals** | "I need high-protein, fixed rotation" | ❌ Phase 2 | Gym bro flow. Macro tracking, rotation planner. |
| **Host Dinner** | "I'm cooking for guests" | ❌ Phase 3 | Dinner party flow. Wine pairing, timeline, impress factor. |

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

### Screen 2: Primary Intent (15 sec) — THE MONEY QUESTION
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
│  💪 I track macros              │
│     (fixed meals, repeat)       │
│                                 │
│  🎉 I cook for others           │
│     (dinner parties, guests)    │
│                                 │
│  [Skip for now]                 │
└─────────────────────────────────┘
```

### Screen 3: Kitchen Inventory (20 sec)
```
┌─────────────────────────────────┐
│  What's in your kitchen?        │
│  (Tap all that apply)           │
│                                 │
│  🍗 Protein (chicken, beef)    │
│  🍚 Carbs (rice, pasta)        │
│  🥦 Veggies                    │
│  🥫 Canned goods               │
│  🧊 Freezer space              │
│  ⏱️ 30 min or less             │
│                                 │
│  [Continue]                     │
└─────────────────────────────────┘
```

### Screen 4: Storage Setup (30 sec) — Critical for Meal Preppers
```
┌─────────────────────────────────┐
│  How do you store meals?        │
│                                 │
│  🧊 Freezer containers         │
│  📦 Glass meal prep boxes      │
│  🥫 Ziplock bags               │
│  🍱 I don't store              │
│                                 │
│  How many meals at once?        │
│  [3-4] [5-7] [8+]              │
│                                 │
│  [Continue]                     │
└─────────────────────────────────┘
```

### Screen 5: Voice Setup (15 sec)
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

**Total Time:** ~90 seconds engaged, 30 seconds if skip-heavy.

---

## 6. Home Screen (Post-Onboarding)

```
┌─────────────────────────────────┐
│  Good evening, Xavier 🌙        │
│                                 │
│  ┌─────────────────────────┐   │
│  │ 🎤 "I have chicken..."   │   │  ← Voice bar (always visible)
│  └─────────────────────────┘   │
│                                 │
│  Your Plan                      │
│  ┌─────┬─────┬─────┬─────┐     │
│  │ Mon │ Tue │ Wed │ Thu │     │  ← Horizontal week scroller
│  │ 🍗  │ 🍝  │ 🥗  │ 🍛  │     │
│  └─────┴─────┴─────┴─────┘     │
│                                 │
│  Quick Start                    │
│  ┌──────────────┬──────────────┐│
│  │ 🍳 Cook      │ 📦 Meal      ││
│  │   Now        │   Prep       ││
│  └──────────────┴──────────────┘│
│                                 │
│  ┌──────────────┬──────────────┐│
│  │ 💪 Macro     │ 🎉 Host      ││
│  │  Meals       │  Dinner      ││
│  └──────────────┴──────────────┘│
│                                 │
│  🔥 3-day streak!               │
└─────────────────────────────────┘
```

**Design Notes:**
- Voice bar always visible (primary entry point)
- Week scroller shows planned meals (Meal Prep flow)
- Quick Start cards expose all 4 flows without clutter
- Streak banner at bottom (gamification always visible)

---

## 7. Flow Details

### 7.1 Cook Now Flow (One Meal, Immediate)

**User Journey:**
```
Home → Cook Now → Recipe Grid (filtered <20 min) → Select → Cook Mode → Complete
```

**Recipe Grid Filters:**
- Time: <15 min, <20 min, <30 min
- Cuisine: Asian, Italian, Comfort, etc.
- Difficulty: Easy, Medium

**Cook Mode:**
- Full-screen step-by-step
- Voice reads each step aloud
- Tap or say "next" to advance
- Built-in timers with haptic alerts
- Completion: XP earned, streak update, photo upload prompt

### 7.2 Meal Prep Flow (Batch Cook + Store) — PRIMARY MVP FLOW

**User Journey:**
```
Home → Meal Prep → Lego Cooking UI → Build Meal → Scale (4→8→12 servings) → Cook Mode → Storage Guide → Complete
```

**Lego Cooking UI:**
```
┌─────────────────────────────────┐
│  Build Your Meal                │
│                                 │
│  1. Pick Protein                │
│  ┌──────┬──────┬──────┐        │
│  │🍗    │🥩    │🐟    │        │
│  │Chicken│Beef │Salmon│        │
│  └──────┴──────┴──────┘        │
│                                 │
│  2. Pick Carb                   │
│  ┌──────┬──────┬──────┐        │
│  │🍚    │🍝    │🥔    │        │
│  │Rice  │Pasta │Potato│        │
│  └──────┴──────┴──────┘        │
│                                 │
│  3. Pick Veg                    │
│  ┌──────┬──────┬──────┐        │
│  │🥦    │🥕    │🫑    │        │
│  │Broc. │Carrot│Pepper│        │
│  └──────┴──────┴──────┘        │
│                                 │
│  4. Pick Sauce                  │
│  ┌──────┬──────┬──────┐        │
│  │🥘    │🍯    │🌶️    │        │
│  │Tery. │Honey │Spicy │        │
│  └──────┴──────┴──────┘        │
│                                 │
│  ─────────────────────────────  │
│  = Chicken Teriyaki Bowl        │
│    450 cal | 35g protein        │
│    Makes: 4 servings            │
│    Cook: 25 min                 │
│                                 │
│  [Start Cooking] [Save for Later]│
└─────────────────────────────────┘
```

**Scaling Logic:**
- User picks base servings (4)
- Slider: 4 → 8 → 12 → 16
- Ingredients auto-recalculate
- Cook time adjusts (+5 min per 4 servings)

**Storage Guide (Post-Cook):**
```
┌─────────────────────────────────┐
│  🎉 Meal Prep Complete!         │
│                                 │
│  You made 8 servings            │
│                                 │
│  🧊 Freezer (4 servings)        │
│  - Use within 3 months          │
│  - Label: "Teriyaki 3/11"       │
│  - Reheat: Microwave 3-4 min    │
│                                 │
│  📦 Fridge (4 servings)         │
│  - Use within 4 days            │
│  - Reheat: Microwave 2-3 min    │
│                                 │
│  [Set "Eat By" Reminders]       │
└─────────────────────────────────┘
```

### 7.3 Macro Meals Flow (Phase 2)
- Macro-filtered recipes (high protein, low carb, etc.)
- Rotation planner (repeat weekly without boredom)
- Grocery integration (same ingredients, different meals)

### 7.4 Host Dinner Flow (Phase 3)
- Dinner party templates (appetizer → main → dessert)
- Wine pairing suggestions
- Timeline generator ("Start rice at 6:15 PM")
- Guest dietary restrictions tracker

---

## 8. Voice Integration

### Voice-First Routing Architecture

```
User speaks → iOS Speech Framework (on-device, free)
           → Intent classifier (meal prep / cook now / macro / host)
           → Flow router → Correct UI
           
Fallback: Whisper API ($10 budget = ~1,600 minutes)
```

### Supported Voice Commands

| Command | Action |
|---------|--------|
| "Hey Tamago, cook now" | Opens Cook Now flow |
| "Hey Tamago, meal prep" | Opens Meal Prep flow |
| "Hey Tamago, I have chicken and rice" | Lego cooking: protein=chicken, carb=rice |
| "Hey Tamago, what can I make?" | Recipe suggestions based on inventory |
| "Hey Tamago, next" | Advance cooking step |
| "Hey Tamago, repeat" | Re-read current step |
| "Hey Tamago, timer 5 minutes" | Set timer |
| "Hey Tamago, I'm done" | Complete current step |

### $10 Voice Budget Allocation

| Item | Cost |
|------|------|
| ElevenLabs TTS pre-gen (10 recipes) | ~$6 |
| ElevenLabs TTS live testing | ~$2 |
| Whisper API fallback testing | ~$2 |
| **Total** | **~$10** |

---

## 9. Gamification Mechanics

### XP System

| Action | XP |
|--------|----|
| Complete a recipe | 50 XP |
| First time cooking a cuisine | 25 XP bonus |
| Complete under par time | 15 XP bonus |
| Rate a recipe | 5 XP |
| Daily login | 10 XP |
| Photo upload | 10 XP |

### Level Progression

| Level | Title | XP Required |
|-------|-------|-------------|
| 1-5 | Kitchen Rookie | 0-500 |
| 6-10 | Home Cook | 500-1,500 |
| 11-20 | Sous Chef | 1,500-5,000 |
| 21-30 | Head Chef | 5,000-12,000 |
| 31-40 | Master Chef | 12,000-25,000 |
| 41-50 | Kitchen Legend | 25,000+ |

### Streaks

- **Daily streak:** Cook at least 1 recipe per day
- **Streak freeze:** 1 free per week (additional cost 100 XP)
- **Milestones:** 7 days (badge), 30 days (badge + flair), 100 days (gold frame)
- **Recovery:** Missed yesterday? "Recovery cook" available for 24 hours

### Achievements (MVP — 15 badges)

| Badge | Condition |
|-------|-----------|
| First Flame | Complete your first recipe |
| Streak Starter | 3-day streak |
| Week Warrior | 7-day streak |
| Month Master | 30-day streak |
| Speed Demon | Complete under par time |
| World Traveler | Cook from 5 cuisines |
| Prep Pro | Complete 5 meal prep recipes |
| Night Owl | Cook after 9 PM |
| Early Bird | Cook before 8 AM |
| Variety Pack | Cook 10 different recipes |
| Five Star | Rate 10 recipes |
| Shutterfly | Upload 5 dish photos |
| Level 10 | Reach level 10 |
| Level 25 | Reach level 25 |
| Centurion | Cook 100 total recipes |

---

## 10. Technical Architecture

### iOS App (SwiftUI)

```
tamago/
├── TamagoApp.swift
├── Models/
│   ├── Recipe.swift
│   ├── CookingStep.swift
│   ├── UserProfile.swift
│   ├── Achievement.swift
│   └── CookingSession.swift
├── Views/
│   ├── Home/
│   │   ├── HomeView.swift
│   │   └── RecipeCard.swift
│   ├── Cook/
│   │   ├── CookingView.swift
│   │   ├── StepView.swift
│   │   ├── TimerView.swift
│   │   └── CompletionView.swift
│   ├── Flows/
│   │   ├── CookNowView.swift
│   │   ├── MealPrepView.swift
│   │   ├── LegoCookingView.swift
│   │   └── StorageGuideView.swift
│   ├── Profile/
│   │   ├── ProfileView.swift
│   │   └── AchievementGrid.swift
│   └── Onboarding/
│       └── OnboardingView.swift
├── Services/
│   ├── VoiceService.swift
│   ├── SpeechRecognitionService.swift
│   ├── ElevenLabsService.swift
│   ├── WhisperService.swift
│   ├── GameEngine.swift
│   ├── TimerService.swift
│   ├── NotificationService.swift
│   └── SupabaseService.swift
├── Data/
│   ├── RecipeStore.swift
│   ├── UserStore.swift
│   └── recipes.json (10 curated recipes)
└── Resources/
    ├── Audio/ (Pre-generated TTS)
    ├── Assets.xcassets
    └── Sounds/
```

### Backend (Supabase)

```sql
CREATE TABLE recipes (
  id UUID PRIMARY KEY,
  title TEXT NOT NULL,
  cuisine TEXT,
  difficulty TEXT,
  prep_time INTEGER,
  cook_time INTEGER,
  servings INTEGER,
  ingredients JSONB,
  steps JSONB,
  meal_prep JSONB,    -- {storage, freeze_days, reheat}
  macro JSONB,        -- {protein, carbs, fat}
  host JSONB,         -- {impress_factor, wine_pairing}
  created_at TIMESTAMPTZ DEFAULT now()
);

CREATE TABLE users (
  id UUID PRIMARY KEY,
  apple_id TEXT UNIQUE,
  xp INTEGER DEFAULT 0,
  level INTEGER DEFAULT 1,
  current_streak INTEGER DEFAULT 0,
  longest_streak INTEGER DEFAULT 0,
  last_cook_date DATE,
  streak_freezes INTEGER DEFAULT 1,
  preferences JSONB,
  created_at TIMESTAMPTZ DEFAULT now()
);

CREATE TABLE cooking_sessions (
  id UUID PRIMARY KEY,
  user_id UUID REFERENCES users(id),
  recipe_id TEXT,
  flow_type TEXT,  -- cook_now, meal_prep, macro, host
  started_at TIMESTAMPTZ,
  completed_at TIMESTAMPTZ,
  xp_earned INTEGER,
  rating INTEGER
);
```

---

## 11. MVP Feature Priorities

### P0 (Must Have — Days 1-3)
- [ ] Onboarding (5 screens, intent picker)
- [ ] Home screen (voice bar, week scroller, flow cards)
- [ ] Cook Now flow (recipe grid → cook mode)
- [ ] Meal Prep flow (Lego cooking UI, scaling, storage guide)
- [ ] Voice bar (always visible, STT parsing)
- [ ] Voice TTS (ElevenLabs pre-gen + fallback)
- [ ] Gamification (XP, streaks, levels, 15 achievements)
- [ ] Timers (concurrent, haptic + sound)

### P1 (Should Have — Days 4-5)
- [ ] Profile screen (stats, achievements, level badge)
- [ ] Push notifications (streak reminders, daily picks)
- [ ] Meal prep mode (storage instructions, "eat by" reminders)
- [ ] Supabase sync (user profile, cooking sessions)
- [ ] Offline support (cache recipes, no voice offline)

### P2 (Phase 2 — Post-MVP)
- [ ] Macro Meals flow
- [ ] Social features (friends, leaderboards)
- [ ] TikTok creator import
- [ ] Host Dinner flow

---

## 12. 3-5 Day Sprint Plan

### Day 1: Foundation + Data Layer
- [ ] Xcode project setup (SwiftUI, iOS 17+, Swift 6)
- [ ] Data models (Recipe, CookingStep, UserProfile, Achievement)
- [ ] Write 10 recipes in `recipes.json` (with meal_prep metadata)
- [ ] RecipeStore + UserStore (UserDefaults persistence)
- [ ] GameEngine (XP, levels, streaks, achievements)
- [ ] Tab bar skeleton (Home, Explore, Profile)

### Day 2: Onboarding + Home Screen
- [ ] OnboardingView (5 screens, intent picker)
- [ ] HomeView (voice bar, week scroller, flow cards)
- [ ] Flow routing logic (intent → correct UI)
- [ ] LegoCookingView (protein + carb + veg + sauce)
- [ ] RecipeCard + grid layout

### Day 3: Cook Mode + Voice
- [ ] CookingView (full-screen step-by-step)
- [ ] StepView (large text, progress bar, tip section)
- [ ] CompletionView (XP animation, streak update, badges)
- [ ] SpeechRecognitionService (iOS Speech Framework)
- [ ] ElevenLabsService (TTS API, pre-gen batch)
- [ ] VoiceService (orchestrator, command parsing)
- [ ] TimerService (concurrent timers, background)

### Day 4: Meal Prep Flow + Polish
- [ ] MealPrepView (batch scaling, 4→8→12 servings)
- [ ] StorageGuideView (fridge/freezer instructions)
- [ ] ProfileView (stats, achievements, level)
- [ ] AchievementGrid (locked/unlocked badges)
- [ ] NotificationService (streak reminders, daily picks)
- [ ] App icon + theming (warm colors: amber, cream, terracotta)

### Day 5: Integration + Ship
- [ ] Supabase setup (tables, auth, sync)
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
| Voice usage rate | >50% | >60% |
| Streak maintenance (7+ days) | >15% | >25% |
| **3+ cooks in Week 1** | **>30%** | **>40%** |

**North Star:** 3+ cooking sessions in Week 1 = 4x Week 12 retention.

---

## 14. Open Questions for Xavier

1. **App name:** "Tamago" — any concerns about Japanese egg branding?
2. **Voice persona:** Should the voice have a name? (e.g., "Chef Tamago")
3. **Pricing:** $4.99/month feels right. Too low? Too high?
4. **Recipe selection:** Are the 10 recipes a good spread?
5. **Day 1 priority:** Voice or gamification — if we had to cut one, which stays?

---

*PRD v2 incorporates: multi-flow architecture (CRI), LTV-driven segment focus (Koji), technical spec (Yuki), Obsidian archive (Sora). Ready for iOS build agents.*
