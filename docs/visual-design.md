# Visual Design Guide — Safe Passage

## Art Style

**Flat illustration** — Warm, approachable style with limited detail. Reference games: "Florence," "Alto's Adventure," "80 Days." Avoids photorealism to prevent triggering trauma in players who may have personal connections to trafficking. Silhouettes and color convey mood and emotion.

### Style Principles

- Simple geometric shapes with soft edges
- Limited color palettes per scene (3-5 dominant colors)
- Characters represented with minimal facial detail — emotion conveyed through posture, color, and context
- Environments use layered silhouettes for depth
- No graphic or violent imagery — danger is communicated through atmosphere, color shift, and narrative

## Color Palette

### Core Colors

| Color | Hex | Usage |
|---|---|---|
| Danger Red | `#E94560` | Danger indicators, CTAs, red flag cards, urgency |
| Safety Green | `#4CAF50` | Safe choices, positive outcomes, smart move cards |
| Caution Amber | `#FF9800` | Warnings, alerts, awareness meter gradient |
| Info Blue | `#3A7BD5` | Neutral/investigative choices, informational elements |
| Deep Navy | `#1A1A2E` | Primary background |
| Dark Surface | `#16213E` | Cards, panels, elevated surfaces |
| Muted Border | `#2A3A5E` | Borders, dividers, inactive elements |
| Light Text | `#D0D8E0` | Primary body text |
| Muted Text | `#8899AA` | Secondary text, descriptions |

### Color as Metaphor

- **Warm golden light** = Safety, home, truth, family
- **Cool blue/purple** = Uncertainty, the unknown, deception
- **Red accents** = Immediate threat, urgency, danger signals
- **Green tones** = Safe choices, positive outcomes, growth
- **Dark desaturation** = Danger, entrapment, loss of agency

### Scene Color Palettes

**Village/Home scenes**: Warm — sky blues, earthy browns, golden sunlight, green vegetation. Feels safe and familiar.

**Urban/Unknown scenes**: Cool — deep navy, muted purple, artificial light blues. Feels uncertain and overwhelming.

**Danger scenes**: Dark — desaturated colors, red accents, shadows. Atmosphere shifts without showing graphic content.

**Resolution scenes**: Bright — return to warm palette with green emphasis. Relief and safety restored.

## Typography

### Font Family: Noto Sans

Google's Noto font family is the only font system that supports all target scripts:

| Script | Font | Languages |
|---|---|---|
| Latin | Noto Sans | English, Vietnamese, Bahasa Indonesia, Tagalog |
| Thai | Noto Sans Thai | Thai |
| Khmer | Noto Sans Khmer | Khmer |
| Myanmar | Noto Sans Myanmar | Burmese |
| Lao | Noto Sans Lao | Lao |

### Type Scale

| Element | Weight | Size | Usage |
|---|---|---|---|
| Game title | Noto Serif 700 | 2.2em | Title screen only |
| Chapter heading | Noto Serif 700 | 1.3em | Chapter starts, section headers |
| Dialogue text | Noto Sans 400 | 0.95em | Character speech, narrative text |
| Choice text | Noto Sans 400 | 0.85em | Choice buttons |
| UI labels | Noto Sans 600 | 0.75-0.8em | Speaker names, badges, categories |
| Caption text | Noto Sans 300 | 0.7em | Helpline info, secondary details |

### Text Considerations

- Variable text length across languages (Thai/Khmer can be 30-50% longer than English)
- All text containers must accommodate expansion without breaking layout
- Minimum font size: 14px (accessibility)
- Line height: 1.5-1.7 for body text (readability across scripts)

## Screen Layout

### Mobile-First Composition

```
┌─────────────────────┐
│                     │
│    SCENE ART        │  ← Top 55% — Visual storytelling
│    (illustration)   │     Background art, characters, mood
│                     │
├─────────────────────┤
│  Speaker Name       │  ← Bottom 45% — Interaction
│                     │     Dialogue, choices, navigation
│  "Dialogue text     │
│   goes here..."     │
│                     │
│  ○ ○ ● ○            │  ← Progress dots
└─────────────────────┘
```

### Choice Point Layout

```
┌─────────────────────┐
│                     │
│    SCENE ART        │  ← Dimmed/zoomed to create tension
│    (atmospheric)    │
│                     │
├─────────────────────┤
│  Choice prompt text │
│                     │
│  ┌─────────────────┐│
│  │ 🛡️ Safe choice  ││  ← Green border
│  └─────────────────┘│
│  ┌─────────────────┐│
│  │ ⚡ Risky choice  ││  ← Red border
│  └─────────────────┘│
│  ┌─────────────────┐│
│  │ 🔍 Investigate  ││  ← Blue border
│  └─────────────────┘│
└─────────────────────┘
```

### Consequence Card Layout

```
┌─────────────────────┐
│  ⚠️ RED FLAG        │  ← Warning banner (red) or
│  ✅ SMART MOVE      │     Success banner (green)
├─────────────────────┤
│                     │
│  Narrative text     │  ← What happened as a result
│  describing the     │     of the player's choice
│  consequence...     │
│                     │
│  ┌─────────────────┐│
│  │ 🚩 Red Flag     ││  ← Educational card with
│  │    Card          ││     real-world red flags
│  │                  ││     or protective behaviors
│  └─────────────────┘│
│                     │
│  [Continue / Rewind]│  ← Action button
└─────────────────────┘
```

## Interaction Design

### Touch Targets

- Minimum tap target: 48x48 px (Material Design guideline)
- Choice buttons: Full-width, 56px minimum height
- Comfortable one-thumb navigation (bottom-zone interaction)
- Swipe to advance dialogue (alternative to tap)

### Transitions

- Scene transitions: Crossfade (500ms)
- Dialogue advance: Slide up (200ms)
- Choice appearance: Stagger fade-in (100ms delay between choices)
- Consequence reveal: Slow fade with color shift (800ms)
- Rewind: Reverse transition effect to reinforce "going back"

### Feedback

- Choice selection: Brief haptic pulse + border glow
- Red flag reveal: Subtle screen shake + red vignette
- Safe choice: Soft green pulse from edges
- Badge earned: Pop animation + particle burst

## Scene Art Direction

### The Market (Mali, Chapter 1)

- **Mood**: Warm, familiar, safe
- **Palette**: Sky blue, brown earth, golden sun, green plants, warm orange stall roofs
- **Elements**: Market stalls with colorful goods, tropical trees, dusty ground, distant temple silhouette
- **Lighting**: Morning golden hour — long shadows, warm highlights
- **Characters**: Mali in bright clothing (stands out), stranger in darker/neutral clothing

### The Phone Message (Mali, Chapter 2)

- **Mood**: Uncertain, private, contemplative
- **Palette**: Night blue, phone screen glow (cool blue light), warm interior hints
- **Elements**: Close-up on phone screen showing a message, thought bubbles
- **Lighting**: Phone screen as primary light source — face illuminated in blue

### The City (Mali, Chapter 4)

- **Mood**: Overwhelming, unfamiliar
- **Palette**: Cool grays, neon hints, concrete, artificial light
- **Elements**: Tall buildings as silhouettes, crowded street suggestion, signs in unfamiliar script
- **Lighting**: Harsh artificial — neon signs, streetlights, no natural warmth

### Danger Moment (Any character)

- **Mood**: Trapped, realization
- **Palette**: Dark desaturated — all warmth drained, red accents only
- **Elements**: Minimalist — locked door, taken document, empty room
- **Lighting**: Single harsh light source, deep shadows

### Safe Resolution (Any character)

- **Mood**: Relief, hope, connection
- **Palette**: Return to warm — greens, golds, soft blues
- **Elements**: Home, family, community, open sky
- **Lighting**: Soft diffused daylight — no harsh shadows

## Interactive Storyboard

An interactive HTML storyboard with phone-frame mockups is available at:

```
storyboard.html
```

Open in any browser to see:

- **Screen Mockups tab** — 7 phone mockups showing title screen, character select, story scene, choice point, red flag consequence, safe consequence, journey map, and story completion
- **Story Flow tab** — Branching diagram for Mali's story and overview of all 4 character arcs
- **Visual Identity tab** — Color swatches and art direction cards
