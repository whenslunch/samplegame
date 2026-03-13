# Research Findings — Safe Passage

## Target Audience

### Smartphone Penetration in SE Asia

Smartphone penetration has surged across SE Asia, reaching 55-70% in most target countries. Android dominates at 85-95%+ market share. Budget devices ($50-150 USD) are the norm.

| Country | Smartphone Penetration | Android Share | Primary Connectivity |
|---|---|---|---|
| Thailand | ~70% | ~85% | 4G urban, 3G rural |
| Cambodia | ~60% | ~95% | 4G urban, 2G/3G rural |
| Vietnam | ~65% | ~90% | 4G expanding rapidly |
| Philippines | ~65% | ~95% | 4G urban, 3G rural |
| Indonesia | ~60% | ~95% | 4G Java, 2G/3G outer islands |
| Myanmar | ~55% | ~95% | 3G/4G urban, 2G rural |
| Laos | ~55% | ~95% | 3G urban, 2G rural |

### Literacy and Language

- Youth literacy is high across all 7 countries (84-99%)
- Functional literacy in rural areas is lower than national statistics suggest
- Visual and audio-driven designs are essential for reaching lower-literacy populations
- Seven primary languages across unique scripts:
  - Thai, Khmer, Burmese, Lao (unique scripts)
  - Vietnamese, Bahasa Indonesia, Tagalog (Latin-based)
  - English serves as a bridge language

### Technical Constraints

- **Budget devices**: 1-2 GB RAM, 720p screens, limited storage
- **Connectivity**: Intermittent in rural areas (2G/3G); offline-first design is mandatory
- **Download size**: Must stay under 25 MB; ideally under 5 MB for initial load
- **Battery**: Power-efficient design matters for devices charged intermittently
- **Data costs**: Minimize data usage; pre-download content for offline play

## Trafficking Landscape in SE Asia

### Major Trafficking Patterns

1. **Labor trafficking** — Fishing, construction, domestic work, agriculture. Victims lured by job promises, trapped by debt bondage and document confiscation. Particularly severe in Thai fishing industry.

2. **Sex trafficking** — Victims recruited through fake job offers (restaurant, entertainment), romance deception, or family-connected recruiters. Cross-border movement is common.

3. **Scam compounds** (post-2020, rapidly growing) — Fake IT/crypto/customer-service jobs lure workers to fortified compounds in Cambodia, Myanmar, and Laos. Victims forced to run online fraud operations. This is the fastest-growing pattern and heavily underserved in awareness efforts.

4. **Domestic servitude** — Education or urban opportunity promises lead to unpaid domestic labor. Perpetrators are often known to the family. Common in Indonesia, Philippines, Myanmar.

5. **Debt bondage** — Workers take on debt for migration costs, then can never earn enough to repay. Wages are garnished, documents held, freedom restricted.

6. **Forced/child marriage** — Particularly in Myanmar, Laos, and rural areas of other countries. Often driven by economic pressure on families.

### Common Recruitment Tactics

- **Fake job advertisements** — Online and offline; salary too good to be true
- **Migration promises** — "Better life across the border"
- **Romance deception** — Online relationships used to lure victims
- **Trusted community members** — Family friends, neighbors, teachers, religious leaders
- **Social media recruitment** — Facebook, LINE, WhatsApp groups with job offers
- **Labor brokers** — Middlemen who charge fees and create debt bondage

### Key Red Flags (to teach in game)

1. Urgency pressure — "Leave tomorrow or lose the chance"
2. Document confiscation — "I'll hold your ID/passport for safekeeping"
3. No written contract — Verbal promises only, vague job descriptions
4. Too-good-to-be-true salary — Wages far above local norms
5. Isolation from family — Discouraging contact with home
6. Upfront fees or debt — "You'll pay back the travel costs from your wages"
7. Vague job description — Can't name specific employer, address, or duties
8. Cross-border travel with unfamiliar people
9. Requests to not tell family/friends about the opportunity
10. Communication cutoff — Phone taken or restricted after arrival

## Existing Games and Apps

### "Missing: Game for a Cause" (India, 2013)

- **Developer**: Indiagames / BBC Media Action
- **Platform**: Android mobile
- **Reach**: 500K+ downloads
- **Mechanic**: Puzzle/adventure game about finding a missing person
- **Takeaway**: Proved a social-cause mobile game can achieve significant reach. However, gameplay was secondary to message — players found it preachy. A game-first approach with embedded education performs better.

### "Sweatshop" (UK, 2012)

- **Developer**: Channel 4 / LittleLoud
- **Platform**: Web browser
- **Mechanic**: Resource management — players run a sweatshop, face moral dilemmas
- **Takeaway**: Moral dilemma mechanics are powerful for building empathy. However, Apple removed it from App Store for depicting child labor — demonstrates platform censorship risk (supports PWA strategy to avoid app store gatekeeping).

### NGO-backed educational apps

- Multiple organizations (IJM, World Vision, ECPAT, IOM) have produced awareness materials
- Most are informational apps, not games — low engagement and retention
- Key failure pattern: **prioritizing message over gameplay** leads to "eat your vegetables" experiences that users abandon quickly
- Key success factor: Games that are genuinely fun first, educational second

### Gap Identified

**No significant anti-trafficking game exists specifically targeting SE Asia.** The scam compound phenomenon (post-2020) is especially underserved. This represents a clear opportunity.

## Game Design Evidence

### Effective Mechanics for Behavior Change

Research on "games for change" and serious games indicates:

1. **Narrative choice games** — Strongest evidence for empathy building and perspective-taking. Players who make choices and experience consequences show higher knowledge retention than passive learners.

2. **Resource management simulations** — Effective for teaching systemic thinking. Players learn that individual decisions affect community outcomes.

3. **Social deduction games** — Good for teaching deception recognition, but require multiple players and connectivity.

4. **Quiz-based games** — Effective for knowledge testing but weak for behavior change. Better as a supplement than a core mechanic.

### Cultural Alignment

- **Collectivist cultures** in SE Asia respond better to **community narratives** over individual hero stories
- Family obligation is a primary motivator — game should acknowledge financial pressures, not dismiss them
- **Shame avoidance** is important — game should never make players feel stupid for falling for tactics (traffickers are sophisticated, not obvious)
- **Respect for elders** complicates messaging — some recruiters are trusted community members, and the game must handle this sensitively
- **Gender dynamics** vary by country — some scenarios are gender-specific

### Platform Recommendation: PWA

Progressive Web Apps are the recommended platform:

- Under 5 MB initial load
- Works offline via service worker caching
- Installable on Android home screen (looks like a native app)
- No app store gatekeeping (avoids Apple/Google content policy issues)
- Runs on any modern Android browser (Chrome, Samsung Internet)
- Single codebase serves mobile and desktop web
- Updateable without user action (service worker updates)
- Shareable via URL (critical for organic distribution)

## Concepts Evaluated

### Concept 1: "Red Flags" — Swipe Card Game

| Attribute | Detail |
|---|---|
| Genre | Tinder-style swipe mechanic |
| Mechanic | Swipe right = safe, left = danger on job offers and messages |
| Build time | ~2 months (MVP) |
| Size | Under 5 MB PWA |
| Pros | Dead simple, works on any device, perfect for NGO workshops, shareable |
| Cons | Shallow engagement, limited replay value, less emotional impact |
| Verdict | **Recommended as initial MVP** for quick deployment and workshop use |

### Concept 2: "Safe Passage" — Interactive Narrative (SELECTED)

| Attribute | Detail |
|---|---|
| Genre | Choose-your-own-adventure / visual novel |
| Mechanic | Branching story with 4 characters, consequence-based learning |
| Build time | ~4-5 months |
| Size | 10-15 MB |
| Pros | Emotionally powerful, high retention, strong cultural relevance, viral potential |
| Cons | Content-heavy (needs localization), risk of re-traumatizing if not careful |
| Verdict | **Selected as flagship product** — strongest evidence for behavior change |

### Concept 3: "Village Guardian" — Community Simulation

| Attribute | Detail |
|---|---|
| Genre | Resource management / tower-defense hybrid |
| Mechanic | Protect community by allocating resources against trafficking threats |
| Build time | ~6 months |
| Size | 15-20 MB |
| Pros | Teaches systemic responses, strong replay value, collectivist culture alignment |
| Cons | More complex to build, harder to localize gameplay balance |
| Verdict | Future consideration for engaged users wanting deeper gameplay |

### Concept 4: "Spot the Signs" — Detective Game

| Attribute | Detail |
|---|---|
| Genre | Hidden object / puzzle investigation |
| Mechanic | Investigate suspicious situations as a community volunteer |
| Build time | ~7-9 months |
| Size | 20-25 MB |
| Pros | Empowers bystander intervention, teaches reporting mechanisms |
| Cons | Most complex to build, needs per-country legal accuracy |
| Verdict | Future consideration for training community responders |

### Concept 5: "TruthOrTrap" — Multiplayer Social Deduction

| Attribute | Detail |
|---|---|
| Genre | Among Us-style social deduction |
| Mechanic | One player is secretly the "recruiter" using real tactics |
| Build time | ~5 months |
| Size | 10 MB |
| Pros | Highly engaging, social/viral, teaches deception recognition through experience |
| Cons | Requires multiple players and connectivity, risks trivializing topic |
| Verdict | Future consideration for school workshops in urban settings |

## Recommended Phased Approach

1. **Phase 1** — Build "Red Flags" swipe game as a 2-month MVP (cheapest, fastest, perfect for NGO workshops)
2. **Phase 2** — Build "Safe Passage" interactive narrative as the flagship product (emotional depth, behavior change)
3. **Phase 3** — Expand to simulation/investigation games for engaged users

## Further Research Needed

- Mobile game usage patterns among rural SE Asian youth
- NGO partnership frameworks (IJM, World Vision, ECPAT, IOM, Mekong Club)
- Academic literature on inoculation theory applied to trafficking prevention
- Current reporting on scam compound evolution (rapidly changing landscape)
- Behavior change measurement frameworks for serious games
- Child protection and content compliance requirements per country
- Voice UI and audio-first design patterns for low-literacy users
- Mobile money integration for incentivized learning (GCash, GrabPay)
