# Tamago — Product Requirements Document

**Version:** 3.2
**Date:** 2026-05-08
**Author:** Kurama, based on Kato PRD v3.1 + Xavier refinements
**Status:** Canonical current PRD
**Sprint Assumption:** 3-5 Day MVP achievable with multiple agents
**Primary Target:** SouperCubes users and freezer-first meal preppers
**Tech Stack:** React Native + Expo + NativeWind + Supabase

---

## 1. Executive Summary

**Tamago** is a **voice-input, UI-output meal prep copilot** for people who batch cook, portion, freeze, and reheat meals across the week.

Core thesis:

> **Voice is the fastest way for users to express planning intent. Structured UI is the best way for the app to return choices, logistics, and action.**

Tamago is not trying to be a generic recipe chatbot or a text-heavy chatbox. It is building a new interaction model for meal prep:

- user speaks naturally about ingredients, goals, storage constraints, and preferences
- Tamago thinks conversationally
- Tamago responds visually with structured cards, plans, logistics, and decision-ready interfaces
- users refine and control the result primarily through touch

At launch, Tamago targets **freezer-first meal preppers** — especially people using SouperCubes, meal prep containers, and batch-cooking workflows — because they care deeply about:

- what freezes well
- what stores well
- how long meals last
- how to portion them
- how to reheat them
- how to use what’s already in the kitchen

---

## 2. Product Thesis

### 2.1 Interaction Thesis
For meal prep planning:
- **Input should be voice-first** because users think in fragments, constraints, ingredients, and preferences
- **Output should be visual-first** because users need to compare, scan, choose, and act
- **Pure text output is insufficient** because long paragraphs are hard to parse, hard to trust, and hard to operate on

Therefore Tamago’s UX model is:

> **Voice in → intelligence layer → rendered planning UI out**

### 2.2 Important Boundary
This does **not** mean the entire app should be voice-driven or dynamically AI-generated.

For MVP:
- voice planning is one major magic moment to test
- the broader product remains a structured touch app
- AI should populate known templates rather than invent arbitrary layouts
- users must be able to refine plans through touch controls without re-speaking everything

---

## 3. Primary Launch ICP

### Primary ICP: “Freezer-First Priya”
- Uses SouperCubes or equivalent portioning/storage tools
- Batch cooks 1-2 times per week
- Wants meals that freeze and reheat well
- Cares about storage life, portion sizing, and waste reduction
- Often has ingredients on hand but struggles to convert them into a good prep plan
- Wants structure, not content overload

### Secondary ICP: “Fridge-Prep Leo”
- Preps lunches or dinners for 3-5 days
- Less freezer-heavy but still logistics-conscious
- Cares about fast planning and reliable storage guidance

### What This ICP Cares About Most
1. Will this **freeze well**?
2. How long will this **last in the fridge/freezer**?
3. How should I **portion** it?
4. Will it **reheat well**?
5. Can I make it from **what I already have**?
6. Can I generate a week plan without opening 20 tabs and thinking too hard?

---

## 4. Problem Statement

Meal preppers who batch cook and store meals face five major problems:

1. **Planning friction** — translating ingredients, time, and constraints into a weekly prep plan is mentally heavy
2. **Storage uncertainty** — most recipe apps do not tell users what actually freezes well, stores well, or reheats well
3. **Interface mismatch** — forms are rigid and chat blobs are verbose; neither matches how users actually think and choose
4. **Decision fatigue** — users fall back to the same meals because discovery and planning are too expensive
5. **Logistics blindness** — existing apps under-serve portioning, container strategy, shopping gaps, and storage timelines

Tamago’s wedge is:

> **AI that understands meal-prep logistics and returns structured, rendered decisions instead of chat sludge.**

---

## 5. Product Principles

1. **Voice In, UI Out** — users speak naturally; the app mostly answers with rendered UI
2. **Decision-Ready UI** — every response should help the user choose, compare, refine, or act
3. **Logistics Are the Product** — storage, freezeability, reheating, portioning, and shopping gaps are first-class
4. **Touch for Precision** — users should edit, swap, confirm, and refine by touch
5. **No Chat Transcript Dependence** — the current state must be legible from the UI itself

---

## 6. Magic Moments

Tamago should create multiple magic moments, not rely on one.

### Magic Moment 1 — “It understood my messy voice input”
User says:
> “I’ve got chicken thighs, broccoli, rice, miso, and I want six freezer lunches.”

Tamago converts that into a clean visual plan frame with identified ingredients, goals, and storage intent.

### Magic Moment 2 — “It gave me a plan, not a paragraph”
Instead of a text blob, Tamago renders:
- meal cards
- servings
- freeze/fridge tags
- reheat instructions
- shopping gaps
- cook-time summary

### Magic Moment 3 — “It understands prep logistics”
Tamago shows:
- what to freeze
- what to fridge
- how long each item lasts
- best container type
- what reheats best for lunch vs dinner

### Magic Moment 4 — “I can refine without starting over”
User can tap:
- swap protein
- make it more freezer-friendly
- reduce shopping
- make fewer containers
- increase servings

### Magic Moment 5 — “I trust it enough to use weekly”
By the second or third successful use, the user begins to rely on Tamago for real prep planning.

---

## 7. MVP User Journey

### Step 1 — Onboarding: Prep Identity
User answers:
1. Do you mostly prep for **freezer**, **fridge**, or **both**?
2. How many meals do you usually prep at once?
3. What storage format do you use most?
4. Do you prefer full meals, components, or either?

### Step 2 — First Voice Capture
Prompt:
> “Tell Tamago what you have and what kind of prep you want this week.”

### Step 3 — Parse & Render Intent
Tamago visually renders:
- detected ingredients
- target meal count
- freezer/fridge preference
- cuisine cues
- shopping flexibility

### Step 4 — Clarifying Questions
Tamago asks up to 1-2 focused questions.

Important:
- user can answer by voice **or** by touch
- touch should be preferred for quick precision inputs

### Step 5 — Plan Generation
Tamago renders a plan with:
- 2-3 prep items or meals
- servings
- total meals covered
- prep time
- freeze/fridge guidance
- reheat guidance
- shopping gaps

### Step 6 — Plan Refinement
User can tap:
- Swap meal
- Swap protein
- Make it more freezer-friendly
- Reduce shopping list
- Use more existing ingredients
- Make fewer containers
- Increase/decrease servings

### Step 7 — Execution
User enters cooking mode with:
- structured step cards
- timers
- batch-prep grouping
- portion/storage guidance

### Step 8 — Completion
Tamago summarizes:
- meals completed
- what to freeze vs fridge
- eat-by dates
- reheating notes

---

## 8. Core MVP Flows

### Flow A — Meal Prep Planner (Primary)
Intent: “Plan my prep week.”

This is the hero flow and the main source of product magic.

### Flow B — Cook Now (Secondary)
Intent: “What should I cook tonight?”

Useful, but secondary to the freezer-first wedge.

### Flow C — Storage & Reheat View (Core Utility)
Intent: “How should I store/use what I made?”

This is not a footnote. It is part of the core value proposition.

---

## 9. Required Output Schema for Generated Plans

Each generated meal or prep item must include:

- `name`
- `description`
- `servings`
- `meal_count_covered`
- `prep_time_minutes`
- `storage_type` (fridge / freezer / both)
- `fridge_life_days`
- `freezer_life_days`
- `reheat_method`
- `reheat_time_minutes`
- `best_container_type`
- `shopping_gap`
- `ingredient_usage_summary`
- `freezeability_score`
- `notes`

Optional but useful:
- `protein`
- `carb`
- `veg`
- `cuisine`
- `difficulty`

---

## 10. MVP Priorities

### P0
- onboarding for freezer/fridge prep identity
- voice capture for first-turn intent
- intent parse UI
- 1-2 clarification turns
- generated prep plan UI
- meal cards with storage/reheat guidance
- refinement actions
- cooking mode
- storage summary after cook

### P1
- save plan
- basic history
- profile with prep preferences
- push reminders
- lightweight streaks or completion tracking

### P2
- fridge photo ingredient detection
- advanced inventory tracking
- macro/nutrition planning
- cross-session personalized suggestions
- rich gamification

---

## 11. Success Metrics

### Product Metrics
- % of users who complete first voice input
- % of users who complete first generated plan
- median time from first voice input to plan generation
- % of users who accept or save first plan
- % of users who use refinement actions
- % of users who start cooking from generated plan

### ICP-Specific Metrics
- % of plans generated in freezer mode
- % of users selecting freezer-first onboarding
- % of meal cards viewed for storage guidance
- % of users interacting with reheat/storage details
- % of users returning within 7 days for another prep plan

### Experience Metrics
- transcript success rate
- clarification completion rate
- plan regeneration rate
- parse correction rate
- generation latency

---

## 12. Summary

Tamago’s MVP is best framed as:

> **a voice-native meal prep planner that turns messy spoken intent into beautiful, useful freezer/fridge planning UI**

The core test is whether users prefer:
- speaking their intent
- seeing a structured plan
- refining it through touch
- trusting the app’s storage and reheating guidance

That is the product bet.
