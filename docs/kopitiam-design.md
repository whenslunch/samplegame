# Kopitiam — Game Design Document

## Concept

Kopitiam is a fast-paced drink-making skill game set in a Singapore coffee shop. Players take orders for traditional kopi, teh, and other drinks, then physically assemble each drink by dragging, pouring, and timing ingredients on a touchscreen workstation. Orders arrive faster and grow more complex as players progress through shifts, unlocking new drink types, ingredients, and shop upgrades.

The game celebrates Singapore's unique kopitiam culture — the intricate ordering language, the theatrical sock-brewing technique, the uncle who always orders "kopi gao siew dai peng" at 7am, and the pride of a well-run drinks stall.

## Platform

- **Primary**: iOS (App Store) and Android (Google Play)
- **Engine**: Unity or Godot (2D, portrait orientation)
- **Monetization**: TBD (premium, cosmetic IAP, or ad-supported)

---

## The Kopi Language System

The heart of the game. Singapore's kopitiam ordering system is a combinatorial language — modifiers stack to create dozens of valid drinks. The player must decode each order and assemble the correct ingredients.

### Base Drinks

| Order Term | Base | Ingredients |
|---|---|---|
| Kopi | Coffee | Coffee sock-brewed + condensed milk |
| Teh | Tea | Tea sock-brewed + condensed milk |
| Milo | Milo | Milo powder + hot water + condensed milk |
| Yuan Yang | Coffee-Tea | Coffee + tea mixed + condensed milk |
| Bandung | Rose | Rose syrup + evaporated milk + water |
| Barley | Barley | Barley water + sugar |
| Chin Chow | Grass Jelly | Grass jelly drink + sugar |
| Lime Juice | Lime | Lime juice + sugar + water |
| Michael Jackson | Soy + Grass Jelly | Soy milk + chin chow |

### Modifiers

| Modifier | Meaning | Effect on Recipe |
|---|---|---|
| *(default)* | Standard | Condensed milk + standard sugar |
| **O** | Black | No milk, use sugar only |
| **C** | Evaporated | Swap condensed milk → evaporated milk + sugar |
| **Gao** | Thick/Strong | Extra coffee/tea (longer brew or double shot) |
| **Po** | Thin/Light | Less coffee/tea (short brew or half shot) |
| **Di Lo** | Extra thick | Maximum strength, minimal water |
| **Siew Dai** | Less sweet | Half the usual sweetener |
| **Gah Dai** | Extra sweet | Double the usual sweetener |
| **Kosong** | No sugar | Zero sweetener |
| **Peng** | Iced | Add ice, serve in tall glass |
| **Sua** | Fresh milk | Swap condensed milk → fresh milk |
| **Tarik** | Pulled | Pour back and forth to froth (tea only — "Teh Tarik") |

### Combination Examples

| Order | Translation | Ingredients |
|---|---|---|
| Kopi | Coffee, condensed milk | Coffee + condensed milk |
| Kopi O | Black coffee, sugar | Coffee + sugar |
| Kopi C | Coffee, evap milk | Coffee + evaporated milk + sugar |
| Kopi O Kosong | Black coffee, no sugar | Coffee only |
| Kopi Siew Dai | Coffee, less sweet | Coffee + condensed milk (half) |
| Kopi C Siew Dai | Coffee, evap, less sweet | Coffee + evaporated milk + sugar (half) |
| Kopi Gao | Thick coffee | Double coffee + condensed milk |
| Kopi Po | Light coffee | Half coffee + condensed milk |
| Kopi Peng | Iced coffee | Coffee + condensed milk + ice |
| Kopi O Peng | Iced black coffee | Coffee + sugar + ice |
| Kopi Gao Siew Dai Peng | Thick iced coffee, less sweet | Double coffee + condensed milk (half) + ice |
| Kopi C Kosong Peng | Iced coffee, evap, no sugar | Coffee + evaporated milk + ice |
| Kopi Di Lo | Extra thick coffee | Triple coffee + condensed milk, minimal water |
| Teh | Tea, condensed milk | Tea + condensed milk |
| Teh O | Black tea, sugar | Tea + sugar |
| Teh C | Tea, evap milk | Tea + evaporated milk + sugar |
| Teh O Peng | Iced black tea | Tea + sugar + ice |
| Teh C Peng | Iced tea, evap | Tea + evaporated milk + sugar + ice |
| Teh Tarik | Pulled tea | Tea + condensed milk + pull action |
| Teh C Siew Dai | Tea, evap, less sweet | Tea + evaporated milk + sugar (half) |
| Teh Gao Peng | Thick iced tea | Double tea + condensed milk + ice |
| Milo | Hot Milo | Milo + hot water + condensed milk |
| Milo Peng | Iced Milo | Milo + water + condensed milk + ice |
| Milo Dinosaur | Iced Milo + powder | Milo + water + condensed milk + ice + Milo powder on top |
| Milo Godzilla | Dinosaur + ice cream | Milo Dinosaur + scoop of ice cream |
| Yuan Yang | Coffee-tea mix | Coffee + tea + condensed milk |
| Yuan Yang Peng | Iced coffee-tea | Coffee + tea + condensed milk + ice |

**Total valid combinations**: 70+ drinks from the modifier system alone, before specials.

---

## Core Gameplay Loop

```
Customer arrives → Order appears (text + voice) → Player assembles drink → Serve → Score → Next customer
```

### The Workstation

The player's screen is a top-down/angled view of a drink-making station with ingredient zones:

```
┌─────────────────────────────┐
│  ORDER QUEUE (top bar)      │  ← Incoming orders scroll left to right
│  "Kopi O Peng"  "Teh C"    │     Timer bar under each order
├─────────────────────────────┤
│                             │
│     ┌───────────────┐       │
│     │  DRINK GLASS  │       │  ← Central workspace: the cup/glass
│     │  (assembly    │       │     being assembled
│     │   area)       │       │
│     └───────────────┘       │
│                             │
├─────────────────────────────┤
│ ☕  🫖  🥛  🍬  🧊  💧  │  ← Ingredient tray (drag to glass)
│ Coffee Tea  CM  Sugar Ice Water│
│ 🍫  🌹  🥤  🍋  🫙  🍦  │
│ Milo Rose EvapM Lime Syrup IC │
└─────────────────────────────┘
```

### Assembling a Drink — Step by Step

Each drink requires specific actions in a logical order:

1. **Select glass type** — Hot cup (small) or iced glass (tall) based on whether order includes "Peng"
2. **Brew the base** — Drag coffee sock / tea sock to the cup and hold for brew time
   - Normal = 2 seconds hold
   - Gao = 3 seconds hold (longer brew)
   - Po = 1 second hold (shorter brew)
   - Di Lo = 4 seconds hold
   - Over-brew = burnt (fail)
3. **Add sweetener** — Drag condensed milk, sugar, or nothing based on modifiers
   - Default = full condensed milk pour
   - O = sugar spoon
   - C = evaporated milk + sugar
   - Siew Dai = half pour (release early)
   - Gah Dai = double pour
   - Kosong = skip
   - Sua = fresh milk
4. **Add water** — Hot water to fill (amount varies by strength)
5. **Special actions**:
   - Peng = add ice cubes (drag 3-4 cubes)
   - Tarik = pull action (swipe up-down repeatedly to froth)
   - Milo Dinosaur = sprinkle Milo powder on top (shake gesture)
   - Milo Godzilla = add ice cream scoop
6. **Serve** — Drag finished drink to the serving counter

### Timing and Scoring

| Factor | Points | Penalty |
|---|---|---|
| Correct drink | +100 base | — |
| Speed bonus | +10 to +50 | Decreases as timer runs |
| Perfect brew time | +25 bonus | — |
| Wrong ingredient | — | Drink rejected, customer upset |
| Missed order (timeout) | — | Customer leaves, -1 life |
| Burnt brew (over-hold) | — | Must restart drink |
| Streak bonus | ×1.5 after 5, ×2 after 10 | Resets on mistake |

---

## Progression System

### Shift Structure

The game is organized into **shifts** (levels) across a career progression:

| Stage | Shifts | Drinks Available | Orders/Min | Mechanics |
|---|---|---|---|---|
| **Trainee** | 1-5 | Kopi, Teh (basic) | 1-2 | Tutorial, no modifiers |
| **Junior** | 6-15 | + O, C modifiers | 2-3 | Two-modifier combos |
| **Regular** | 16-30 | + Gao, Po, Siew Dai, Peng | 3-4 | Three-modifier combos, ice drinks |
| **Senior** | 31-50 | + Milo, Yuan Yang, Tarik | 4-5 | Pull mechanic, specials |
| **Uncle/Auntie** | 51-75 | + Di Lo, Gah Dai, Kosong, Sua | 5-7 | Full modifier set |
| **Legend** | 76-100 | + Bandung, Barley, Chin Chow, MJ | 6-8 | All drinks, surprise orders |
| **Kopitiam King** | 100+ | Everything | 8+ | Endless mode, leaderboard |

### Unlock System

- **New drinks** unlock as players advance through stages
- **Ingredients** appear on the workstation as they become available
- **Stall upgrades** earned with coins:
  - Bigger cup rack (queue more drinks at once)
  - Better sock (faster brew time)
  - Auto ice machine (one-tap ice instead of dragging cubes)
  - Second burner (brew two things at once)
  - Express counter (faster serving animation)
- **Cosmetics**: Stall decorations, cup designs, apron patterns

### Stars and Mastery

Each shift awards 1-3 stars:

- ⭐ Complete the shift (serve all customers, max 3 lost)
- ⭐⭐ Lose no customers
- ⭐⭐⭐ Perfect score (no mistakes, all speed bonuses)

Stars unlock bonus content and are required to advance past certain gates.

---

## Customer System

### Customer Types

| Type | Behavior | Visual |
|---|---|---|
| **Regular Uncle** | Simple orders, patient, good tips | Older man in polo shirt |
| **Auntie** | Moderate orders, moderate patience | Woman with market bag |
| **Office Worker** | Complex orders, impatient | Business attire, checking watch |
| **Student** | Milo/iced drinks, patient | School uniform or casual |
| **Picky Foodie** | Very specific modifiers, low patience | Trendy clothes, phone out |
| **Tourist** | Points at menu confusedly, extra patient | Camera, bewildered expression |
| **The Regular** | Same order every time, expects you to remember | Recurring character |
| **Taxi Uncle** | Fastest order, shortest patience | Walks up already talking |
| **Influencer** | Orders Milo Godzilla, wants it photogenic | Ring light glow |

### Customer Patience

Each customer has a patience meter (timer bar). Patience varies by:

- Customer type (Uncle = patient, Office Worker = impatient)
- Time of day in-game (morning rush = less patience)
- Stage difficulty (higher stages = faster timers)

When patience runs out, the customer leaves and the player loses a life. 3 lost customers per shift = game over for that shift.

### Regular Customer Memory

Some customers become **regulars** who visit every few shifts. After their third visit, their order appears as just their name:

> "Ah Beng" → (player must remember it's Kopi Gao Peng)

This memory mechanic adds a unique challenge and builds attachment to characters.

---

## Special Mechanics

### Morning Rush / Lunch Rush

Timed events within a shift where orders come in rapid-fire (1.5x speed). Surviving a rush awards a bonus multiplier for the rest of the shift. Visual: queue fills up, customers crowd the counter, stress music kicks in.

### Multi-Drink Orders

Starting at the Senior stage, customers can order 2-3 drinks at once:

> "Two Kopi O, one Teh C Peng"

Player must assemble multiple drinks and serve them together. Higher complexity, higher reward.

### Teh Tarik Mini-Game

When a Teh Tarik is ordered, a special mini-game triggers:

- Two cups appear on screen
- Player swipes up and down to "pull" the tea between cups
- Rhythm-based: hit the beat markers for a perfect pull
- Too fast = spillage, too slow = flat tea
- Perfect pull = bonus points + crowd reaction ("wah!")

### Milo Dinosaur Shake

When Milo Dinosaur is ordered:

- After assembling iced Milo, player shakes the phone to sprinkle Milo powder
- Accelerometer-based: controlled shaking adds powder evenly
- Too much = powder mountain (funny but bonus points)
- Too little = customer disappointed

### Kopi Di Lo Challenge

The ultimate test. Kopi Di Lo requires:

- Maximum brew time (4 seconds — easy to over-brew and burn)
- Minimal water
- Precise condensed milk pour
- Served in a tiny cup

Getting it perfect triggers a special animation and achievement.

### Boss Customers (End of Stage)

Each stage ends with a boss customer — a legendary kopitiam character with an extremely complex order:

- **Stage 1 Boss**: "Chua Ah Ma" — Orders kopi for her whole mahjong table (4 drinks, all different)
- **Stage 3 Boss**: "Blur Sotong" — Changes his order mid-preparation
- **Stage 5 Boss**: "The Inspector" — Tests you with rapid-fire increasingly complex orders
- **Stage 7 Boss**: "Kopitiam Legend Ah Huat" — Orders every drink on the menu in sequence

---

## Endless Mode

Unlocked after completing Stage 5 (Uncle/Auntie). Customers come indefinitely with increasing speed. Compete on global and friends leaderboards.

### Leaderboard Categories

- **Longest Streak** — Most consecutive correct drinks
- **Speed Demon** — Most drinks served in 5 minutes
- **Memory Master** — Most regular customer orders remembered
- **Kopi Connoisseur** — Most unique drink types made in one session
- **Weekly Challenge** — Special modifier (e.g., "all orders are Peng this week")

---

## Daily Challenges

One special challenge per day to keep players returning:

| Day | Challenge Example |
|---|---|
| Monday | "Kopi Monday" — All orders are coffee variants, 2x speed |
| Tuesday | "Teh Tarik Tuesday" — Every other order is Teh Tarik; perfect your pull |
| Wednesday | "Wildcard" — Random modifiers added to orders mid-prep |
| Thursday | "Memory Thursday" — No order text after first 2 seconds; remember it |
| Friday | "Rush Hour" — Non-stop morning rush, survive 5 minutes |
| Saturday | "Uncle's Favorites" — All orders from regular customers (by name only) |
| Sunday | "Chill Sunday" — Relaxed pace, bonus points for perfect drinks |

---

## Audio Design

### Music

- **Ambient**: Kopitiam atmosphere — ceiling fans, clinking cups, distant conversation, occasional bird
- **Gameplay**: Upbeat but not frantic lo-fi / retro Singaporean-flavored music
- **Rush hour**: Tempo increases, percussion intensifies
- **Boss customer**: Dramatic comedic theme

### Sound Effects

- Coffee sock squeeze and pour (satisfying liquid sound)
- Condensed milk glug
- Ice cubes clinking into glass
- Teaspoon stirring
- Teh Tarik pouring arc (whoosh)
- Milo powder sprinkle
- Customer satisfaction: "Shiok!" / "Can lah!" / "Not bad ah"
- Customer frustration: "Wah so slow" / *tsk* / walks away
- Perfect drink: Cash register cha-ching + crowd murmur of approval

### Voice Lines

Customer orders are spoken in Singlish with the actual kopitiam lingo:

- "Uncle, kopi o siew dai, thanks ah"
- "Eh one teh c peng"
- "Milo dinosaur, extra powder can?"
- "Aiyah, faster lah!"

---

## Visual Style

### Art Direction

- **Style**: Colorful 2D cartoon with a warm, nostalgic kopitiam aesthetic
- **Perspective**: Slight top-down angle on the workstation
- **Color palette**: Warm browns (wood, coffee), creamy whites, pops of red/green (stall signage), condensed milk gold
- **Character art**: Exaggerated but affectionate caricatures of Singapore archetypes
- **Stall**: Classic kopitiam look — marble-top table, metal cup rack, sock filter on hook, condensed milk can with two holes punched

### UI Tone

- Bilingual labels (English + Chinese/Malay as flavor text)
- Handwritten-style fonts for menus and signs
- Kopitiam table marble texture for backgrounds
- Red plastic bag and tissue paper "chope" seat as loading screen element

---

## Social Features

### Challenge a Friend

- Send a specific shift or custom order sequence to a friend
- Compare scores on the same challenge
- "Can you handle my regular order?" — share your hardest streak

### Kopitiam Stories

- Short unlockable lore snippets about kopitiam culture
- History of the sock filter, why it's called "C," the art of Teh Tarik
- Unlocked by achieving mastery milestones

---

## Monetization Options (TBD)

| Model | Description |
|---|---|
| **Premium** ($2.99-4.99) | One-time purchase, all content included |
| **Free + Cosmetic IAP** | Free to play, buy stall skins/cup designs/character outfits |
| **Free + Ad-supported** | Watch ad to continue after game over, or remove ads for $2.99 |

Recommendation: **Premium or free + cosmetics**. Avoid pay-to-win mechanics. No energy/lives system that gates play — players should be able to play for hours uninterrupted.

---

## Why It Works for Hours

1. **Easy to learn, hard to master** — First shifts teach basics; modifier combinations create exponential complexity
2. **Flow state** — Timed drink assembly with physical gestures (drag, hold, swipe, shake) creates satisfying rhythm
3. **"One more shift" loop** — Short shifts (2-3 minutes) + star system + unlocks make stopping hard
4. **Memory challenge** — Regular customers add a unique cognitive layer that grows with playtime
5. **Cultural pride** — Singaporeans will share this; the Singlish voice lines and kopitiam details make it feel like home
6. **Competitive** — Leaderboards and friend challenges drive replayability
7. **Variety** — 70+ drink combinations mean the game keeps surprising you past hour 10
8. **Boss fights** — Stage-ending boss customers provide narrative-like peaks and satisfaction
9. **Daily pull** — Daily challenges and weekly leaderboard resets bring players back
10. **Skill ceiling** — Di Lo precision brewing, Teh Tarik rhythm, and memory recall give hardcore players something to chase
