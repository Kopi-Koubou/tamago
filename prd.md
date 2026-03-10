# Tamago - Product Requirements Document

**Version:** 1.0
**Date:** 2026-03-11
**Author:** Kato (AI Chief of Staff)
**Status:** Ready for Implementation
**Sprint:** 3-5 Day MVP

---

## 1. Problem Statement

Home cooks aged 25-40 who meal prep weekly face three compounding problems:

1. **Decision paralysis** — "What should I cook this week?" leads to scrolling 30+ minutes on recipe apps, then defaulting to the same 5 meals
2. **No structured progression** — Unlike fitness or language learning, cooking has no skill tree. People cook the same things for years without leveling up
3. **Dirty hands UX gap** — Every recipe app requires scrolling and tapping mid-cook. Hands are covered in chicken juice. Phone gets gross or ignored

**Why now:**
- Meal prep is mainstream (SouperCubes, TikTok meal prep content = billions of views)
- Voice AI costs dropped 90% in 2025 (Whisper is free, ElevenLabs has generous free tier)
- Duolingo proved gamification drives daily retention in learning apps (DAU/MAU >50%)
- No one has combined voice-first + gamification + cooking. The gap is wide open

**Competitive landscape:**
| App | Voice | Gamification | Meal Prep Focus | Problem |
|-----|-------|-------------|-----------------|---------|
| Mealime | No | No | Yes | Boring, no engagement loop |
| Paprika | No | No | No | Power user tool, not fun |
| Pestle | No | No | No | Recipe import only |
| Crouton | No | No | No | Timer-focused |
| Duolingo | Yes | Yes | N/A | Not cooking |

**Tamago's wedge:** Voice-first gamified cooking = unoccupied intersection.

---

## 2. Target User Personas

### Persona 1: "Prep-Day Priya" (Primary)
- **Age:** 28, software engineer, lives with partner
- **Cooking:** Meal preps every Sunday (3-4 hours), cooks dinner 2-3x/week
- **Pain:** Repeats the same 6 meals. Knows she should learn more but recipe discovery is overwhelming
- **Motivation:** Wants variety without decision fatigue. Loves streaks (has 400-day Duolingo streak)
- **Device:** iPhone 15, often propped on kitchen counter
- **Willingness to pay:** $5-10/month if it saves her Sunday planning time

### Persona 2: "Level-Up Leo" (Secondary)
- **Age:** 34, marketing manager, cooking for family of 3
- **Cooking:** Cooks dinner 4-5x/week, weekend batch cooking
- **Pain:** Wants to go beyond basics but doesn't know how. Can't justify cooking classes ($200+)
- **Motivation:** Competitive — wants to feel like he's progressing. Shares achievements with friends
- **Device:** iPhone 14 Pro, uses AirPods while cooking
- **Willingness to pay:** $10/month for structured skill progression

### Persona 3: "TikTok Tina" (Phase 3 growth)
- **Age:** 25, content creator, 50K TikTok followers
- **Cooking:** Posts 3-4 recipe videos/week
- **Pain:** No way to monetize recipes beyond brand deals. Followers can't easily replicate her recipes
- **Motivation:** Wants a platform where her audience can cook along with her recipes, building her brand
- **Device:** iPhone 16 Pro
- **Willingness to pay:** Free (she's the supply side — she brings users)

---

## 3. Core User Journey (Voice-First Cooking Flow)

### First Launch (< 2 minutes to first cook)

```
1. Splash → "What do you like to cook?" (3 category picks: Asian, Italian, Comfort, etc.)
2. Skill assessment → "How comfortable are you in the kitchen?" (Beginner / Intermediate / Advanced)
3. First recipe card → "Start your first cook!" (pre-selected based on answers, ~20 min recipe)
4. No account required until after first cook completion
```

### Active Cooking Session

```
┌─────────────────────────────────────┐
│  🍳 Chicken Teriyaki Bowl           │
│  Step 3 of 8                        │
│  ━━━━━━━━━━━░░░░░░░  37%           │
│                                     │
│  "Dice the chicken into             │
│   bite-sized cubes"                 │
│                                     │
│  🎤 Voice: "Hey Tamago, done"       │
│  ─── or tap to continue ───         │
│                                     │
│  ⏱️ Timer: 3:42 remaining           │
│  💡 Tip: Keep pieces uniform        │
│     for even cooking                │
│                                     │
│  [◀ Back]            [Next ▶]       │
└─────────────────────────────────────┘
```

**Voice commands during cook:**
- "Hey Tamago, next step" → advance
- "Hey Tamago, repeat" → re-read current step
- "Hey Tamago, timer 5 minutes" → set timer
- "Hey Tamago, what's next?" → preview next step
- "Hey Tamago, I'm done" → complete current step
- "Hey Tamago, help" → contextual tip for current step

### Post-Cook Completion

```
┌─────────────────────────────────────┐
│  🎉 Cook Complete!                  │
│                                     │
│  +50 XP earned                      │
│  🔥 3-day streak!                   │
│  🏆 "First Teriyaki" badge unlocked │
│                                     │
│  📸 Share your creation?            │
│  [Take Photo]  [Skip]               │
│                                     │
│  ⭐⭐⭐⭐⭐ Rate this recipe          │
│                                     │
│  🍱 Storing leftovers?              │
│  [Fridge: 3 days] [Freeze: 2 weeks] │
│  [Reheat instructions →]           │
│                                     │
│  [Next Recipe →]                    │
└─────────────────────────────────────┘
```

### Daily Loop (Retention)

```
Morning push notification: "🔥 Day 4 streak! Tonight's pick: 15-min Garlic Butter Shrimp"
  → User opens app
  → Sees streak, daily recipe suggestion
  → Adds to "Cook Later" or starts immediately
  → Completes cook → XP + streak maintained
  → Checks leaderboard (Phase 2)
```

---

## 4. Feature Requirements

### MVP (Phase 1) — Ship in 3-5 Days

| Feature | Priority | Description |
|---------|----------|-------------|
| **Recipe Browser** | P0 | Grid of 10 curated recipes with difficulty, time, category tags |
| **Step-by-Step Cook Mode** | P0 | Full-screen guided cooking with large text, progress bar, auto-scroll |
| **Voice Guidance (TTS)** | P0 | ElevenLabs reads each step aloud. Play/pause. Auto-advance option |
| **Voice Commands (STT)** | P0 | Whisper transcription for "next", "repeat", "timer", "done" |
| **Cooking Timers** | P0 | In-step timers with haptic + audio alerts. Multiple concurrent timers |
| **XP + Streaks** | P0 | Earn XP per recipe completed. Daily streak counter. Streak freeze (1 free) |
| **Levels** | P0 | Level 1-50 system. XP thresholds. Level badge on profile |
| **Achievements** | P1 | 15-20 badges (first cook, 7-day streak, 5 cuisines tried, speed cook, etc.) |
| **Onboarding** | P1 | 3-screen preference quiz → first recipe suggestion |
| **Meal Prep Mode** | P1 | Storage instructions, reheat guidance, portion multiplier |
| **Profile** | P1 | Stats: total cooks, streak, level, XP, badges, favorite cuisine |
| **Push Notifications** | P1 | Streak reminders, daily recipe picks (local notifications) |
| **Offline Support** | P2 | Cache recipe data for offline cooking (no voice in offline) |

### Phase 2: Social (Week 2-3)

| Feature | Description |
|---------|-------------|
| Friends list | Add friends via contact/username |
| Activity feed | "Priya cooked Teriyaki Bowl!" |
| Weekly challenges | "Cook 3 Asian dishes this week" → bonus XP |
| Leaderboards | Friends leaderboard by XP/week |
| Share cards | Instagram-story-sized completion cards |

### Phase 3: Recipe Marketplace (Month 2)

| Feature | Description |
|---------|-------------|
| User-submitted recipes | Structured recipe editor with step validation |
| Creator profiles | Follow creators, see their recipe catalog |
| TikTok import | Paste TikTok URL → AI extracts recipe → creator claims |
| Rating + reviews | 5-star + text reviews per recipe |
| Collections | User-curated recipe collections |

### Phase 4: Kitchen OS (Month 3+)

| Feature | Description |
|---------|-------------|
| Voice inventory | "I bought chicken and rice" → tracked pantry |
| AI meal planner | "What can I make with what I have?" |
| Smart shopping list | Auto-generate from selected recipes, deduplicate |
| Nutrition tracking | Calories, macros per recipe (auto-calculated) |
| Appliance integration | Connect smart oven/thermometer (stretch) |

---

## 5. Gamification Mechanics

### XP System

| Action | XP |
|--------|----|
| Complete a recipe | 50 XP |
| First time cooking a cuisine | 25 XP bonus |
| Complete a recipe under par time | 15 XP bonus |
| Rate a recipe | 5 XP |
| Daily login | 10 XP |
| Complete weekly challenge | 100 XP |
| Photo upload of finished dish | 10 XP |

### Level Progression

| Level | Title | XP Required | Unlock |
|-------|-------|-------------|--------|
| 1-5 | Kitchen Rookie | 0-500 | Basic recipes |
| 6-10 | Home Cook | 500-1,500 | Intermediate recipes unlock |
| 11-20 | Sous Chef | 1,500-5,000 | Advanced recipes unlock |
| 21-30 | Head Chef | 5,000-12,000 | Expert recipes unlock |
| 31-40 | Master Chef | 12,000-25,000 | Create & share recipes |
| 41-50 | Kitchen Legend | 25,000+ | Gold profile badge |

### Streaks

- **Daily streak:** Cook at least 1 recipe per day
- **Streak freeze:** 1 free freeze per week. Additional freezes cost 100 XP
- **Streak milestones:** 7 days (badge), 30 days (badge + profile flair), 100 days (badge + gold frame), 365 days (legendary badge)
- **Streak recovery:** Missed yesterday? "Recovery cook" available for 24 hours (cook any recipe to restore streak)

### Achievements (MVP — 15 badges)

| Badge | Condition |
|-------|-----------|
| First Flame | Complete your first recipe |
| Streak Starter | 3-day streak |
| Week Warrior | 7-day streak |
| Month Master | 30-day streak |
| Speed Demon | Complete a recipe under par time |
| World Traveler | Cook recipes from 5 different cuisines |
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

## 6. Voice AI Integration

### Architecture

```
┌──────────┐    ┌──────────────┐    ┌──────────────┐
│  User    │───▶│ iOS Speech   │───▶│ Command      │
│  speaks  │    │ Framework    │    │ Parser       │
└──────────┘    │ (on-device)  │    │ (local NLP)  │
                └──────────────┘    └──────┬───────┘
                                          │
                              ┌───────────┴──────────┐
                              │ Fallback: Whisper API │
                              │ (complex/failed parse)│
                              └──────────────────────┘

┌──────────┐    ┌──────────────┐    ┌──────────────┐
│  Recipe  │───▶│ ElevenLabs   │───▶│ AVFoundation │───▶ Speaker
│  step    │    │ TTS API      │    │ playback     │
│  text    │    │ (streaming)  │    └──────────────┘
└──────────┘    └──────────────┘
```

### STT Strategy (Speech-to-Text)

**Primary: iOS Speech Framework (free, on-device)**
- Use `SFSpeechRecognizer` for wake word detection + simple commands
- Keyword spotting for: "next", "repeat", "done", "timer", "help", "back"
- Zero API cost, works offline, low latency (<200ms)

**Fallback: OpenAI Whisper API**
- Only for complex/failed parses (e.g., "set a timer for 3 and a half minutes")
- Cost: ~$0.006/minute of audio
- Budget: $10 test budget covers ~1,600 minutes of fallback audio

### TTS Strategy (Text-to-Speech)

**Primary: ElevenLabs API**
- Voice: Warm, friendly, clear (select from ElevenLabs voice library — "Rachel" or "Sarah" style)
- Streaming mode for low latency
- Pre-generate and cache TTS for all 10 MVP recipes (store as .mp3 in app bundle)
- Cost: ~$0.30 per 1,000 characters. 10 recipes × ~2,000 chars = ~$6 for full pre-gen
- Remaining $4 budget for live generation during testing

**Fallback: AVSpeechSynthesizer (free, on-device)**
- Use Apple's built-in TTS if ElevenLabs quota exceeded or offline
- Lower quality but functional

### Voice UX Rules

1. **Always allow tap as alternative** — voice is additive, never mandatory
2. **Confirmation for destructive actions** — "Skip this recipe? Say 'yes' to confirm"
3. **No accidental triggers** — require wake word "Hey Tamago" or physical button hold
4. **Volume auto-adjust** — lower music/podcast volume during TTS playback (via AVAudioSession)
5. **Kitchen noise tolerance** — test with running water, sizzling, exhaust fan backgrounds

### $10 Test Budget Allocation

| Item | Cost |
|------|------|
| ElevenLabs TTS pre-generation (10 recipes) | ~$6 |
| ElevenLabs TTS live testing | ~$2 |
| Whisper API fallback testing | ~$2 |
| **Total** | **~$10** |

---

## 7. Technical Architecture

### iOS App (SwiftUI)

```
tamago/
├── TamagoApp.swift                    # App entry point
├── Models/
│   ├── Recipe.swift                   # Recipe data model
│   ├── CookingStep.swift              # Individual step model
│   ├── UserProfile.swift              # XP, level, streaks, achievements
│   ├── Achievement.swift              # Badge definitions
│   └── CookingSession.swift           # Active cook state
├── Views/
│   ├── Home/
│   │   ├── HomeView.swift             # Main tab — streak, daily pick, recipe grid
│   │   └── RecipeCard.swift           # Recipe preview card
│   ├── Cook/
│   │   ├── CookingView.swift          # Active cook mode (full screen)
│   │   ├── StepView.swift             # Single step display
│   │   ├── TimerView.swift            # Cooking timer overlay
│   │   └── CompletionView.swift       # Post-cook celebration
│   ├── Explore/
│   │   └── ExploreView.swift          # Browse all recipes by category
│   ├── Profile/
│   │   ├── ProfileView.swift          # Stats, achievements, level
│   │   └── AchievementGrid.swift      # Badge collection
│   └── Onboarding/
│       └── OnboardingView.swift       # Preference quiz
├── Services/
│   ├── VoiceService.swift             # STT + TTS orchestration
│   ├── SpeechRecognitionService.swift # iOS Speech Framework wrapper
│   ├── ElevenLabsService.swift        # TTS API client
│   ├── WhisperService.swift           # Whisper API fallback
│   ├── GameEngine.swift               # XP, levels, streaks, achievements logic
│   ├── TimerService.swift             # Multiple concurrent cooking timers
│   ├── NotificationService.swift      # Streak reminders, daily picks
│   └── SupabaseService.swift          # Backend sync
├── Data/
│   ├── RecipeStore.swift              # Local recipe data (JSON bundle)
│   ├── UserStore.swift                # UserDefaults + Supabase sync
│   └── recipes.json                   # 10 curated recipes (bundled)
├── Resources/
│   ├── Audio/                         # Pre-generated TTS audio files
│   ├── Assets.xcassets                # App icons, images
│   └── Sounds/                        # Timer alerts, completion sounds
└── Utilities/
    ├── Constants.swift                # API keys, config
    └── Extensions.swift               # SwiftUI + Foundation extensions
```

### Backend (Supabase)

**Tables:**

```sql
-- Users
CREATE TABLE users (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  apple_id TEXT UNIQUE,
  display_name TEXT,
  avatar_url TEXT,
  xp INTEGER DEFAULT 0,
  level INTEGER DEFAULT 1,
  current_streak INTEGER DEFAULT 0,
  longest_streak INTEGER DEFAULT 0,
  last_cook_date DATE,
  streak_freezes INTEGER DEFAULT 1,
  preferences JSONB DEFAULT '{}',
  created_at TIMESTAMPTZ DEFAULT now()
);

-- Cooking sessions
CREATE TABLE cooking_sessions (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  user_id UUID REFERENCES users(id),
  recipe_id TEXT NOT NULL,
  started_at TIMESTAMPTZ DEFAULT now(),
  completed_at TIMESTAMPTZ,
  duration_seconds INTEGER,
  xp_earned INTEGER DEFAULT 0,
  rating INTEGER CHECK (rating BETWEEN 1 AND 5),
  photo_url TEXT
);

-- Achievements
CREATE TABLE user_achievements (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  user_id UUID REFERENCES users(id),
  achievement_id TEXT NOT NULL,
  unlocked_at TIMESTAMPTZ DEFAULT now(),
  UNIQUE(user_id, achievement_id)
);

-- Recipes (for Phase 3 UGC, MVP uses bundled JSON)
CREATE TABLE recipes (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  creator_id UUID REFERENCES users(id),
  title TEXT NOT NULL,
  description TEXT,
  cuisine TEXT,
  difficulty TEXT CHECK (difficulty IN ('easy', 'medium', 'hard', 'expert')),
  prep_time_minutes INTEGER,
  cook_time_minutes INTEGER,
  servings INTEGER,
  ingredients JSONB NOT NULL,
  steps JSONB NOT NULL,
  storage_instructions JSONB,
  tags TEXT[],
  photo_url TEXT,
  rating_avg FLOAT DEFAULT 0,
  rating_count INTEGER DEFAULT 0,
  created_at TIMESTAMPTZ DEFAULT now()
);
```

**Auth:** Sign in with Apple (required for App Store). Supabase Auth handles tokens.

**Storage:** Supabase Storage for dish photos + recipe images.

**Edge Functions:** None needed for MVP. Future: recipe import from URL, AI meal planning.

### API Keys Required

| Service | Key | Cost |
|---------|-----|------|
| ElevenLabs | API key | $5/month (Starter) or pay-as-you-go |
| OpenAI (Whisper) | API key | ~$0.006/min (fallback only) |
| Supabase | Project URL + anon key | Free tier (500MB DB, 1GB storage) |
| Apple Developer | Signing certificate | $99/year (existing) |

---

## 8. Content Strategy

### MVP: 10 Curated Recipes

Selected for variety, broad appeal, meal prep friendliness, and difficulty spread:

| # | Recipe | Cuisine | Difficulty | Time | Meal Prep? |
|---|--------|---------|-----------|------|------------|
| 1 | Chicken Teriyaki Bowl | Japanese | Easy | 25 min | Yes |
| 2 | One-Pan Garlic Butter Shrimp | American | Easy | 15 min | No |
| 3 | Classic Fried Rice | Chinese | Easy | 20 min | Yes |
| 4 | Greek Chicken Sheet Pan | Mediterranean | Easy | 35 min | Yes |
| 5 | Beef Stir-Fry with Broccoli | Chinese | Medium | 25 min | Yes |
| 6 | Creamy Tuscan Chicken | Italian | Medium | 30 min | Yes |
| 7 | Thai Basil Chicken (Pad Krapao) | Thai | Medium | 20 min | Yes |
| 8 | Honey Garlic Salmon | Japanese | Medium | 20 min | No |
| 9 | Chicken Tikka Masala | Indian | Hard | 45 min | Yes |
| 10 | Korean Beef Bulgogi | Korean | Hard | 35 min | Yes |

### Recipe Data Format (JSON)

```json
{
  "id": "chicken-teriyaki-bowl",
  "title": "Chicken Teriyaki Bowl",
  "description": "Sweet and savory glazed chicken over fluffy rice with steamed veggies",
  "cuisine": "Japanese",
  "difficulty": "easy",
  "prepTimeMinutes": 10,
  "cookTimeMinutes": 15,
  "servings": 4,
  "xpReward": 50,
  "parTimeMinutes": 30,
  "tags": ["meal-prep", "high-protein", "quick"],
  "ingredients": [
    { "item": "chicken thighs", "amount": "500g", "prep": "diced" },
    { "item": "soy sauce", "amount": "3 tbsp" },
    { "item": "mirin", "amount": "2 tbsp" },
    { "item": "honey", "amount": "1 tbsp" },
    { "item": "rice", "amount": "2 cups" },
    { "item": "broccoli", "amount": "1 head", "prep": "cut into florets" }
  ],
  "steps": [
    {
      "order": 1,
      "instruction": "Cook the rice according to package instructions",
      "timer": { "minutes": 15, "label": "Rice cooking" },
      "tip": "Rinse rice 2-3 times until water runs clear for fluffier results",
      "voiceText": "Start by cooking your rice. Rinse it two to three times until the water runs clear, then cook according to package instructions. This usually takes about fifteen minutes."
    }
  ],
  "storage": {
    "fridge": { "days": 4, "instructions": "Store rice and chicken separately" },
    "freezer": { "weeks": 3, "instructions": "Freeze in individual portions without rice" },
    "reheat": "Microwave 2-3 minutes. Add a splash of water to rice to prevent drying"
  }
}
```

### Phase 3: TikTok Creator Pipeline

```
1. User pastes TikTok recipe URL into Tamago
2. AI extracts: ingredients, steps, timing (GPT-4 vision on video frames)
3. Recipe auto-generated in Tamago format
4. Push notification to creator: "Your recipe is trending on Tamago! Claim it"
5. Creator signs up → claims recipe → gets attribution + follower growth
6. Creator can edit/refine the auto-generated recipe
7. Revenue share on premium recipes (Phase 4)
```

---

## 9. Monetization

### Freemium Model

**Free Tier (forever free):**
- 10 curated recipes (MVP set)
- Voice guidance (with daily limit: 3 voice-guided cooks/day)
- XP, streaks, levels, achievements
- Basic profile + stats

**Tamago Pro ($4.99/month or $39.99/year):**
- Unlimited voice-guided cooks
- Full recipe library (50+ recipes, growing weekly)
- Meal prep planner (weekly calendar view)
- Advanced achievements
- Priority voice quality (ElevenLabs premium voices)
- No ads (if ads are added to free tier)
- Extra streak freezes (3/week vs 1/week)

**Phase 3+ additions:**
- Creator revenue share (70/30 split on premium creator recipes)
- Sponsored recipe collections (brand partnerships)
- Kitchen OS features as premium add-on

### Revenue Projections (Conservative)

| Metric | Month 1 | Month 3 | Month 6 |
|--------|---------|---------|---------|
| Downloads | 1,000 | 10,000 | 50,000 |
| Free → Pro conversion | 3% | 5% | 7% |
| Paying users | 30 | 500 | 3,500 |
| MRR | $150 | $2,500 | $17,500 |

---

## 10. Success Metrics

### North Star

**Trending on App Store — Top 50 Food & Drink category**

### Primary Metrics

| Metric | Target (Week 1) | Target (Month 1) |
|--------|-----------------|-------------------|
| D1 Retention | >40% | >40% |
| D7 Retention | >20% | >25% |
| D30 Retention | — | >15% |
| Cooks completed / DAU | >0.8 | >1.0 |
| Voice usage rate | >50% of cooks | >60% of cooks |
| Streak maintenance (7+ days) | >15% of users | >25% of users |

### Secondary Metrics

| Metric | Target |
|--------|--------|
| App Store rating | >4.5 stars |
| Onboarding completion | >80% |
| Time to first cook | <3 minutes |
| Average cook completion rate | >85% |
| Photo upload rate | >20% of cooks |
| Organic sharing (share cards) | >10% of cooks |

### Tracking Implementation

- **Analytics:** PostHog (free tier, self-hostable) or Mixpanel (free up to 20M events)
- **Events to track:** `app_open`, `onboarding_complete`, `cook_started`, `cook_completed`, `voice_command_used`, `achievement_unlocked`, `streak_maintained`, `streak_lost`, `recipe_rated`, `photo_uploaded`, `share_tapped`
- **Crash reporting:** Sentry (free tier)

---

## 11. 3-5 Day Sprint Plan

### Day 1: Foundation + Data Layer

**Morning (4 hrs):**
- [ ] Xcode project setup (SwiftUI, iOS 17+, Swift 6)
- [ ] Data models: `Recipe`, `CookingStep`, `UserProfile`, `Achievement`, `CookingSession`
- [ ] Write all 10 recipes in `recipes.json` (complete with ingredients, steps, storage, voiceText)
- [ ] `RecipeStore` — load + parse bundled JSON
- [ ] `UserStore` — UserDefaults persistence for XP, level, streak, achievements

**Afternoon (3 hrs):**
- [ ] `GameEngine` — XP calculation, level thresholds, streak logic, achievement checking
- [ ] Unit tests for GameEngine (streak edge cases, XP math, level-up triggers)
- [ ] Tab bar skeleton: Home, Explore, Profile

**Deliverable:** App launches, loads recipes from JSON, game engine works in isolation.

### Day 2: Recipe Browser + Cook Mode UI

**Morning (4 hrs):**
- [ ] `HomeView` — streak banner, daily pick, "Continue Cooking" or "Start" CTA
- [ ] `RecipeCard` — image placeholder, title, difficulty badge, time, cuisine tag
- [ ] `ExploreView` — grid layout with category filters (All, Asian, Italian, Quick, Meal Prep)
- [ ] Recipe detail sheet (ingredients list, "Start Cooking" button)

**Afternoon (3 hrs):**
- [ ] `CookingView` — full-screen step-by-step mode
- [ ] `StepView` — large text, progress bar, step counter, tip section
- [ ] Navigation: swipe/tap to advance steps, back button
- [ ] `CompletionView` — XP earned animation, streak update, achievement pop-ups

**Deliverable:** Full cooking flow works end-to-end with tap navigation. No voice yet.

### Day 3: Voice Integration + Timers

**Morning (4 hrs):**
- [ ] `SpeechRecognitionService` — iOS Speech Framework, keyword detection
- [ ] `ElevenLabsService` — TTS API client, streaming playback
- [ ] Pre-generate TTS audio for all 10 recipes (batch API call, save .mp3 files)
- [ ] `VoiceService` — orchestrator: auto-read step on entry, listen for commands

**Afternoon (3 hrs):**
- [ ] `TimerService` — multiple concurrent timers, background support, haptic + sound alerts
- [ ] `TimerView` — floating timer overlay during cook mode
- [ ] Voice command parsing: "next", "repeat", "done", "timer X minutes", "help"
- [ ] Fallback: `AVSpeechSynthesizer` when ElevenLabs unavailable

**Deliverable:** Voice reads steps aloud, user can say "next" to advance. Timers work.

### Day 4: Gamification UI + Polish

**Morning (4 hrs):**
- [ ] `ProfileView` — level badge, XP progress bar, total cooks, current streak, longest streak
- [ ] `AchievementGrid` — locked/unlocked badges with descriptions
- [ ] Achievement unlock animations (confetti, badge reveal)
- [ ] Streak banner with flame animation on HomeView
- [ ] `OnboardingView` — 3-screen quiz (cuisine preference, skill level, cooking frequency)

**Afternoon (3 hrs):**
- [ ] `NotificationService` — streak reminders (8 PM if no cook today), daily recipe pick (10 AM)
- [ ] Meal prep mode: storage instructions screen post-cook, portion multiplier on ingredients
- [ ] App icon design (egg character — Tamago = egg in Japanese)
- [ ] Launch screen + basic theming (warm colors: amber, cream, terracotta)

**Deliverable:** Full gamification loop works. App feels polished and warm.

### Day 5: Integration Testing + Ship

**Morning (4 hrs):**
- [ ] Supabase setup: create project, tables, auth (Sign in with Apple)
- [ ] `SupabaseService` — sync user profile, cooking sessions, achievements to cloud
- [ ] End-to-end testing: onboarding → browse → cook → voice → complete → XP → streak
- [ ] Edge case testing: kill app mid-cook, offline mode, timer in background

**Afternoon (3 hrs):**
- [ ] App Store metadata: screenshots (6.7" + 6.1"), description, keywords
- [ ] TestFlight build → internal testing
- [ ] Submit to App Store review
- [ ] Prepare launch tweet + initial seed user outreach plan (50 users target)

**Deliverable:** TestFlight build live. App Store submission in queue.

---

## Design Direction

Per Xavier's preferences — **warm, humanist, not generic blue**.

- **Primary palette:** Amber (#F59E0B), Cream (#FFF7ED), Terracotta (#C2410C)
- **Accent:** Warm green (#65A30D) for success states
- **Typography:** SF Pro Rounded (friendly, approachable)
- **Iconography:** Rounded, filled style. Cooking-themed custom icons
- **Animations:** Playful but not childish. Confetti on achievements, flame pulse on streaks
- **Inspiration:** Duolingo's playfulness + Apple Fitness+ warmth + Headspace's calm

---

## Open Questions (for Xavier)

1. **App name confirmation:** "Tamago" — any concerns about Japanese egg branding for a global app?
2. **Voice persona:** Should the voice have a name/character? (e.g., "Chef Tamago")
3. **Pricing:** $4.99/month feels right for MVP. Too low? Too high?
4. **Recipe selection:** Are the 10 recipes above a good spread? Want to swap any?
5. **Day 1 priority:** Voice or gamification — if we had to cut one from MVP, which stays?

---

*This PRD is designed to be directly actionable by CLI coding agents. Each section maps to implementation tasks. The sprint plan can be converted to worktree-per-day execution.*
