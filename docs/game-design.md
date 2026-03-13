# Game Design Document — Safe Passage

## Concept

Safe Passage is an interactive narrative game where players follow characters through realistic scenarios involving human trafficking recruitment. Through branching story choices, players learn to recognize red flags, practice protective behaviors, and build awareness of trafficking patterns common in Southeast Asia.

## Design Pillars

1. **Educate, don't traumatize** — Show consequences through implication and emotion, not graphic content
2. **Agency over helplessness** — Players always have a path to safety; rewind mechanics mean no permanent failure
3. **Respect, not rescue narratives** — Characters are smart people in difficult situations, not victims to be saved
4. **Culturally specific, universally accessible** — Stories reflect real patterns; UI works across literacy levels
5. **Offline-first, share-native** — Full gameplay without internet; sharing is a core feature

## Core Mechanics

### Branching Narrative

- Players read story scenes with dialogue and scene art
- At critical moments, 2-3 choices appear
- Choices are color-coded with subtle guidance:
  - **Green** — Protective/safe action
  - **Red** — Risky/dangerous action
  - **Blue** — Investigative/neutral action
- Each choice leads to different narrative outcomes and branching paths
- Stories converge toward 3 possible endings per character

### Consequence System

- **Risky choices** trigger a narrative consequence followed by a "Red Flag" educational card explaining the real-world danger signal
- **Safe choices** trigger positive narrative progress with a "What You Did Right" reinforcement card
- Players can **rewind** after seeing a bad consequence — they learn through experiencing the result, then get a second chance
- No permanent fail states; the game rewards learning, not perfection

### Awareness Score

- Tracks cumulative learning across all story chapters
- Increases when players make safe choices or read Red Flag cards
- Displayed on the journey map between chapters
- Unlocks collectible safety badges (e.g., "Verifier," "Trusted Network Builder")

### Journey Map

- Visual progress tracker between chapters
- Shows completed chapters, current position, and locked future chapters
- Displays past choices (both good and bad) as learning history
- Chapter badge shows position (e.g., "Chapter 2 of 5")

## Characters and Story Arcs

### Mali — Labor Trafficking

- **Age**: 17
- **Location**: Rural Thailand
- **Scenario**: Offered a "restaurant job" in Bangkok by a family friend (Khun Prasert)
- **Red flags taught**: Urgency pressure, ID confiscation, no written contract, isolation from family
- **Structure**: 5 chapters, 3 endings

**Chapter outline:**

1. **The Market** — Mali meets Khun Prasert at the village market. He offers a restaurant job with "good tips, free room and board."
   - Choice: Leave tomorrow / Tell mother first / Ask for a reference
2. **The Phone Call** — If Mali told her mother, family verifies and discovers the scam. New opportunity appears online.
   - Choice: Respond to online ad / Research the company / Ignore it
3. **The Bus Station** — A new, seemingly more legitimate offer arrives. Mali must decide whether to travel.
   - Choice: Go with verification steps / Go without telling anyone / Stay and seek local work
4. **The City** — Mali navigates the city. Depending on prior choices, she encounters safe or dangerous situations.
   - Choice: Varies based on path
5. **The Resolution** — Story concludes with one of three endings

**Endings:**

- **Best ending**: Mali finds legitimate work through a verified agency, sends money home safely
- **Growth ending**: Mali connects with an NGO through her school counselor, receives skills training
- **Rescue ending**: Mali gets into a bad situation but uses knowledge to seek help and escape

### Somchai — Scam Compound

- **Age**: 22
- **Location**: Phnom Penh, Cambodia
- **Scenario**: Sees an online ad for high-paying IT work across the border
- **Red flags taught**: Too-good-to-be-true salary offers, cross-border recruitment, passport surrender, compound isolation
- **Structure**: 5 chapters, 3 endings

**Key trafficking pattern**: The post-2020 scam compound phenomenon — fake IT/crypto jobs luring workers to fortified compounds in Cambodia, Myanmar, and Laos where they are forced to run online scams.

### Rina — Domestic Servitude

- **Age**: 15
- **Location**: Jakarta, Indonesia
- **Scenario**: A kind older woman offers to sponsor her education in another city in exchange for "housework"
- **Red flags taught**: Grooming by trusted figures, false education promises, debt bondage, isolation tactics
- **Structure**: 5 chapters, 3 endings

**Key trafficking pattern**: Domestic servitude through education promises — common across Indonesia, Philippines, and Myanmar. Perpetrators often known to the family.

### Anh — Forced Labor at Sea

- **Age**: 19
- **Location**: Hai Phong, Vietnam
- **Scenario**: Recruited for a fishing boat job overseas, promised good wages
- **Red flags taught**: Bait-and-switch wages, passport confiscation, no-escape situations at sea, labor broker deception
- **Structure**: 5 chapters, 3 endings

**Key trafficking pattern**: Forced labor on fishing vessels — endemic in the Thai fishing industry and throughout SE Asian waters. Workers trapped at sea for months or years.

## Game Flow

```
Title Screen
  → Language Selection (7 languages)
  → Character Selection (4 characters)
    → Chapter 1: Story scenes + dialogue
      → Choice Point (2-3 options)
        → Consequence (Red Flag or Smart Move card)
          → Continue or Rewind
    → Journey Map (progress + awareness score)
    → Chapter 2-5: Repeat pattern
  → Story Completion
    → Stats summary (red flags learned, safe choices, awareness %)
    → Share button
    → Real helpline numbers
    → Play another character
```

## Engagement and Retention

- **4 distinct stories** provide replay value (each ~15-20 minutes)
- **Collectible badges** reward learning milestones
- **Share mechanic** drives organic distribution — "I got 85% awareness, can you beat it?"
- **Rewind system** encourages exploration of all branches
- **Offline play** means no connectivity barrier to continued engagement
- **Short chapter length** (~3-5 minutes) fits mobile usage patterns

## Content Safety

- No graphic depictions of violence or abuse
- Dangerous situations are implied through dialogue and narrative, not shown visually
- Characters always have agency and a path to safety
- Content reviewed by trafficking survivors and NGO partners (planned)
- Age-appropriate for 13+ audience
- Real helpline numbers displayed at story completion and accessible from menu

## Localization

### Priority languages (Phase 1)

| Language | Script | Countries |
|---|---|---|
| Thai | Thai script | Thailand |
| Khmer | Khmer script | Cambodia |
| Vietnamese | Latin (with diacritics) | Vietnam |
| Bahasa Indonesia | Latin | Indonesia |
| Tagalog | Latin | Philippines |
| English | Latin | All (bridge language) |

### Phase 2

| Language | Script | Countries |
|---|---|---|
| Burmese | Myanmar script | Myanmar |
| Lao | Lao script | Laos |
| Bahasa Melayu | Latin | Malaysia |

### Localization considerations

- All text externalized for translation
- Character names can be localized to feel native to each country
- Scenarios can be customized per region (e.g., fishing labor more relevant in Vietnam/Thailand)
- UI must support variable text length (Thai and Khmer text can be significantly longer than English)
- Font must support all target scripts (Noto Sans family)

## Technical Target

- **Platform**: PWA (Progressive Web App)
- **Initial download**: Under 5 MB (core), under 15 MB (with all story content)
- **Offline**: Full gameplay without internet after initial load
- **Min device**: Android 8+ with 1 GB RAM, 720p screen
- **Browser**: Chrome 70+, Samsung Internet, Firefox
- **Web fallback**: Same PWA serves as desktop web experience
- **No app store required**: Installable from browser, avoids store approval delays
