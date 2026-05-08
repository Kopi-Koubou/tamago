# Tamago — Design Spec

**Version:** 1.0
**Date:** 2026-05-08
**Status:** Ready for implementation
**Companion Docs:** `prd.md`, `idea.md`

---

## 1. Purpose

This document defines the product experience, screen behavior, UI system, and interaction patterns for Tamago.

Tamago is a **meal-prep copilot for freezer-first users**. The product is optimized for people who batch cook, portion, freeze, store, and reheat meals across the week.

The core design hypothesis is:

> **Voice is the fastest way for users to express prep intent. Rendered UI is the best way for the app to return choices, logistics, and action.**

This does **not** mean the entire app should behave like a voice-generated UI system.

Important boundary:
- **Voice-first planning** is one major magic moment to test
- The app overall should still feel like a **well-designed touch product**
- Users must be able to inspect, refine, correct, and proceed using touch controls
- AI-generated or AI-assembled UI should be constrained to specific, legible templates rather than arbitrary runtime layouts

---

## 2. Product Experience Goals

### 2.1 Primary Goal
Help a user go from:
- vague weekly prep intent
- scattered ingredients
- storage constraints
- minimal energy

to:
- a concrete plan
- clear meal cards
- storage/reheat confidence
- easy refinement
- an execution-ready cooking flow

### 2.2 Experience Goals
1. **Low-friction input** — user can speak naturally instead of filling long forms
2. **High-legibility output** — user sees plans as structured UI, not text walls
3. **Storage confidence** — freezer/fridge/reheat guidance must feel first-class
4. **Touch confidence** — the UI must remain easy to control without further voice input
5. **Tasteful presentation** — the product should feel warm, modern, premium, and calm

### 2.3 Anti-Goals
Tamago should not feel like:
- a giant chat transcript
- a generic recipe browser with AI pasted on top
- a loud voice assistant that talks too much
- a magical black box with no editable structure
- a fully dynamic UI generator with inconsistent layouts

---

## 3. Design Principles

### 3.1 Voice In, UI Out
Use voice to capture intent quickly. Use UI to present structure, comparison, and action.

### 3.2 Templates Over Chaos
AI can fill data into known surfaces. It should not invent arbitrary page structures in MVP.

### 3.3 Logistics Are Core Content
Storage type, lifespan, portioning, reheating, and shopping gaps are core value, not side metadata.

### 3.4 Touch Always Wins on Precision
When the user wants to swap, compare, edit, confirm, or correct, touch interactions should be preferred over extra voice turns.

### 3.5 Every Screen Must Reduce Cognitive Load
The user should be able to scan each screen in seconds and know what to do next.

---

## 4. Primary User and Use Context

### Primary User
**Freezer-First Priya**
- uses SouperCubes or meal prep containers
- batch cooks weekly
- wants reliable freezer/fridge planning
- values variety but hates planning fatigue
- wants meal prep to feel organized and repeatable

### Typical Contexts
- on couch planning the week
- standing in kitchen checking ingredients
- mid-prep with hands busy
- deciding whether meals should go into fridge or freezer
- checking reheating/storage later in the week

### Key User Questions
- What can I prep from what I have?
- Will this freeze well?
- How many meals does this cover?
- What do I need to buy?
- How should I portion this?
- How long will it last?
- What should I eat first?

---

## 5. Information Architecture

### Primary App Sections
1. **Home**
2. **Plan**
3. **Cook**
4. **Library / History**
5. **Profile**

### Primary Navigation Behavior
- Bottom tab navigation for stable app areas
- Contextual drill-down for active plans and cooking sessions
- Persistent return path to the active plan/cook session

### MVP IA Notes
- The app should emphasize **Plan** and **Cook** over generic browsing
- Recipe exploration is secondary to weekly planning
- Home should point toward current prep status, not a content feed

---

## 6. Core Experience Loop

### Loop Summary
1. User declares prep intent
2. App parses and confirms intent
3. App asks 1-2 clarifying questions if needed
4. App renders a structured prep plan
5. User refines with touch
6. User starts cooking
7. App guides prep, portioning, and storage
8. App records outcomes and supports reuse later

### Magic Moments in the Loop
1. **Messy spoken input becomes structured intent**
2. **Structured plan replaces text sludge**
3. **Storage/reheat guidance feels genuinely useful**
4. **Refinement via touch is fast and satisfying**
5. **Cooking and storage execution feel organized**

---

## 7. Screen Specifications

## 7.1 Onboarding

### Goal
Collect enough setup context to personalize planning without feeling form-heavy.

### Required Inputs
- freezer / fridge / mixed prep preference
- typical meals per prep session
- storage format
- full meals vs components

### Screen Sequence

#### Screen A — Welcome
- brand mark
- concise product statement
- CTA: `Get Started`
- secondary action: `Preview Demo`

#### Screen B — Prep Mode
Prompt:
- “How do you usually prep?”
Options:
- Freezer-first
- Fridge-first
- Both

#### Screen C — Prep Shape
Prompt:
- “What do you usually make?”
Options:
- Full meals
- Components
- Mix of both

#### Screen D — Storage Format
Options:
- SouperCubes
- Meal prep containers
- Zip bags
- Mixed

#### Screen E — Voice Planning Intro
- introduces voice as fastest input method
- explicitly states output will be shown visually
- CTA: `Try Voice Planning`
- alternate CTA: `Skip and Use Touch`

### Key Design Requirement
Onboarding must frame voice as a useful shortcut, not a mandatory identity.

---

## 7.2 Home Screen

### Goal
Orient the user around their prep week and direct them into the next best action.

### Layout Sections
1. Greeting / context header
2. Active prep summary or empty state
3. Primary voice planning CTA
4. Quick actions
5. Recent plans / saved patterns

### Primary CTA
- prominent voice entry surface
- copy example: `Plan this week by voice`
- secondary option: `Build with touch`

### Quick Actions
- Freezer plan
- Fridge plan
- Use ingredients I have
- Repeat last plan

### Empty State
Should explain that Tamago helps with:
- weekly prep plans
- storage guidance
- reheat logistics

---

## 7.3 Voice Capture / Intent Parse

### Goal
Turn messy spoken input into a legible interpreted state.

### States
- idle
- listening
- processing
- parsed
- low confidence
- failed

### UI Requirements
The screen must show:
- transcript preview
- parsed ingredients
- parsed meal count
- storage mode
- shopping flexibility
- missing info chips

### Key Rule
This screen is not a chat transcript. It is an **intent interpretation surface**.

### User Actions
- confirm intent
- edit parsed ingredients
- retry voice
- answer via tap
- continue

---

## 7.4 Clarification Step

### Goal
Resolve only the minimum ambiguity needed to generate a useful plan.

### Rules
- ask one question at a time
- maximum 2 clarifying turns before first plan generation
- prefer chips/sliders/toggles after the first voice turn when possible

### Example Clarifications
- portion size
- storage duration
- dietary avoidance
- okay to buy extras

### UI Pattern
- question prompt
- voice answer CTA
- touch answers beneath it
- skip/default option

This is a key place where **touch-customizable UX** matters. Users should not need to keep speaking if quick taps are faster.

---

## 7.5 Generated Plan Screen

### Goal
Deliver a plan that is immediately scannable, credible, and actionable.

### Page Structure
1. plan summary header
2. high-level logistics strip
3. meal card stack
4. shopping gap section
5. refinement tray
6. primary CTA

### Plan Summary Header
Shows:
- total meals covered
- prep time
- storage mix
- likely container count

### Logistics Strip
Compact summary chips:
- freezer-friendly
- fridge items
- cook once / eat multiple days
- shopping needed / shopping light

### Meal Cards
Each card includes:
- meal title
- short one-line description
- servings / meals covered
- prep time
- freezer/fridge tags
- reheat method
- best container type
- shopping gap summary
- swap CTA

### Primary Actions
- Start Cooking
- Save Plan
- Refine Plan

### Secondary Actions
- Swap one meal
- Use more pantry ingredients
- Make more freezer-friendly
- Reduce shopping
- Fewer containers

### Design Requirement
The plan should feel like a **control panel**, not a generated essay.

---

## 7.6 Storage Logistics View

### Goal
Make prep logistics feel operational and trustworthy.

### Required Sections
- freeze now
- fridge now
- eat first
- best containers
- reheating notes

### Example Rows
- Chicken miso rice bowl → Freezer → 60 days → Microwave 4 min → SouperCube 1-cup slot
- Sesame broccoli side → Fridge → 4 days → Stovetop reheat optional → shallow container

### Why This Matters
For this ICP, logistics is a big part of the “aha.” This screen is not secondary.

---

## 7.7 Cooking Mode

### Goal
Guide execution without making the user scroll through recipe prose.

### Structure
- grouped prep tasks
- step-by-step card progression
- ingredient checklist
- timers
- portioning checkpoint
- storage checkpoint

### Key Behavior
Cooking mode should optimize for:
- large tap targets
- glanceability
- minimal reading per step
- easy resumption if interrupted

### Step Content Format
Each step card should use:
- action title
- concise instruction
- optional tip
- timer action if relevant

### End-of-Cook Summary
At completion, render:
- what goes in fridge
- what goes in freezer
- number of portions created
- eat-by guidance
- reheating reminder

---

## 7.8 Library / Saved Plans

### Goal
Support repeatability without forcing users to re-plan from zero.

### Features
- saved plans
- recent plans
- reusable templates
- repeat with changes

### Card Metadata
- plan name
- prep type
- meals covered
- freezer/fridge split
- last used date

---

## 8. UI System and Rendering Boundaries

### Core Principle
Tamago’s MVP should use a **fixed component library** with AI-generated data and content inside it.

### AI-Rendered Surfaces
Allowed:
- plan summary
- meal cards
- logistics cards
- shopping gap list
- refinement recommendations

Not allowed in MVP:
- arbitrary layout invention
- random card types with inconsistent hierarchy
- freeform chat as the main output mode

### Touch-Customizable UI Requirement
Every important AI-generated result must expose touch controls such as:
- swap
- edit
- remove
- save
- confirm
- regenerate
- change servings
- change storage mode

This preserves product integrity and avoids overcommitting to voice-only behavior.

---

## 9. Component Inventory

### Foundational Components
- buttons
- chips
- segmented controls
- bottom sheets
- cards
- tabs
- progress bars
- timers
- toasts

### Domain Components
- VoiceCaptureBar
- ParsedIntentCard
- ClarificationCard
- PlanSummaryHeader
- MealPlanCard
- LogisticsStrip
- StorageMatrix
- ReheatBadge
- ShoppingGapList
- RefinementTray
- CookingStepCard
- PortionGuideCard

### State Components
- listening pulse
- processing shimmer
- low-confidence warning card
- retry state
- empty state

---

## 10. Interaction Model

### Voice Interaction Rules
- voice is best for broad intent capture
- touch is best for correction and precision
- the app should never force long voice-only loops

### Touch Interaction Rules
- all key decisions must be tappable
- refinement should feel incremental, not destructive
- changes should preserve user context where possible

### Regeneration Rules
If the user taps a refinement action, the app should update only the relevant part of the plan where possible rather than reflow the entire experience into confusion.

---

## 11. Visual Direction

### Tone
- warm
- clean
- modern
- calm
- smart but not sterile

### Avoid
- noisy gamification-first aesthetic
- generic chatbot bubbles
- hard enterprise dashboard vibes
- over-ornamented recipe blog styling

### UI Character
Tamago should feel like:
- a tasteful kitchen planning tool
- premium but approachable
- clear enough for logistics
- soft enough for lifestyle usage

### Visual Priorities
1. readability
2. hierarchy
3. scan speed
4. confidence
5. warmth

---

## 12. Content and Copy Style

### Voice Copy
- short
- clear
- supportive
- minimal

### UI Copy
- structured
- operational
- confidence-building
- not overly witty in critical planning moments

### Example Tone
Good:
- `Freezes well for up to 2 months`
- `Needs 2 extra ingredients`
- `Swap this meal`
- `Best eaten first`

Bad:
- long chef-like monologues
- verbose AI disclaimers
- dense markdown-like formatting inside cards

---

## 13. Accessibility and Usability

### Must-Haves
- strong contrast
- dynamic text support
- voice usage not required for completion
- all voice flows must have touch fallback
- large targets for kitchen use
- haptic feedback for important confirmations

### Kitchen Context Requirements
- support one-handed use where possible
- support quick resumption
- reduce reliance on dense reading mid-cook

---

## 14. Motion and Feedback

### Motion Principles
- subtle
- purposeful
- reassuring
- never decorative at the expense of clarity

### Important Motion Events
- voice listening activation
- parse completion
- plan generation arrival
- meal swap update
- cooking step completion
- end-of-cook summary reveal

### Feedback States
The app should always make it clear whether it is:
- listening
- thinking
- waiting for user input
- ready to proceed
- failed and recoverable

---

## 15. Design Acceptance Criteria

The design is successful if:

1. A new user can complete a first prep plan without reading a wall of text
2. A user can understand the generated plan in under 10 seconds of scanning
3. Storage/reheat guidance is visible without extra digging
4. Refinement is possible through touch without restarting the flow
5. Cooking mode feels structurally different from planning mode
6. The app feels like a product, not a chat wrapper

---

## 16. Open Design Questions

1. Should the first plan emphasize full-meal cards or component-prep cards?
2. How much information belongs on each meal card before it becomes visually dense?
3. Should storage logistics live inline on the plan screen, or behind an expandable drill-down?
4. What is the smallest render-template system that still feels magical?
5. How much streak/gamification UI should appear in MVP versus later?

---

## 17. Summary

Tamago’s design direction is:

> **voice-assisted planning with touch-first control and beautifully structured visual output**

The MVP should prove that users prefer:
- speaking their intent
- seeing a structured plan
- refining it through touch
- trusting the app’s storage and reheating guidance

That is the design bet.
