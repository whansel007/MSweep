# Wingsweeper: Singapore's Butterfly Grid — Game Design Document

_Exported 11/09/2026, 09:48:40_

- **Genre:** Minesweeper-style grid puzzle with a biodiversity-survey theme
- **Platform:** Browser (responsive desktop and mobile web)
- **Theme:** Urban biodiversity and species loss in Singapore, experienced through a butterfly survey grid
- **Audience:** Casual puzzle players and nature/education audiences, ages 10 and up
- **Visual style:** Clean, bright tropical field-guide aesthetic: sunlit green edges against shaded forest interior, stylised butterfly cards based on real local species

## 01. Concept

Wingsweeper is a Minesweeper-style grid puzzle that reframes butterfly biodiversity and species loss in Singapore as a survey the player conducts. Each level is a patch of habitat rendered as a grid: a sunlit, open margin wraps a darker shaded interior. The player reveals cells to log butterflies, guided by numbered hints that count neighbours. Two real research findings drive the design. First, Singapore surveys found 85 butterfly species at open, sunny edges versus only 63 inside the shaded primary forest (Bukit Timah, 2019), so hints cluster at the edges and the smart play is to start there. Second, the species most likely to have vanished from Singapore are small, dull, cryptic ones - 6 of 9 recent losses were cryptic - so indistinct brown butterflies that look like empty cells can be wrongly declared extinct, while a patient player who logs them as cryptic keeps them alive. The game turns observation bias and detectability into the core puzzle.

## 02. Audience & Platform

Browser game, responsive for desktop and mobile web (mouse and touch). Target audience: casual puzzle players and nature/education audiences, ages 10 and up, including schools and Butterfly Watch volunteers. Session length 3-5 minutes per grid, with a codex that rewards repeat play. No install required; a progressive web app (PWA) shell is a sensible later upgrade for offline play. Content language: English, with local species names included.

## 03. Design Pillars

1) Reveal, do not destroy - the player logs and uncovers, never blasts; a safe first reveal is always guaranteed, as in classic Minesweeper.
2) Edges matter - life concentrates at sunny margins; starting there is both the strategic and the scientifically honest move.
3) See the unseen - detectability is conservation; the dull, overlooked species are where the game's tension lives.
4) Honest numbers - scores and codex reference real Singapore totals (334 extant species, 153 extirpated) drawn from the research, not invented figures.

## 04. Player Objectives

Primary: catalogue as many living butterflies as possible across each grid.
Secondary: correctly identify cryptic (dull, hard-to-see) species by flagging them, and avoid wrongly declaring them extinct.
Tertiary: complete a species codex by discovering real Singapore butterflies across sites.
Score = butterflies catalogued minus those wrongly lost, plus bonuses for rediscovering a cell previously thought absent. The end-of-run scoreboard compares the player's record to the real national totals.

## 05. Core Loop

1. Load a grid for a named Singapore site, shown with the real species count recorded there.
2. Probe sunny-edge cells first, where numbered hints cluster, to learn neighbour counts safely.
3. Read the hints to infer which neighbouring cells contain butterflies and reveal them.
4. When an ambiguous, dull cell appears, decide: flag it as cryptic (likely alive) or mark it extinct (declared lost).
5. Clear the grid; the scoreboard shows catalogued vs lost and compares to real totals.
6. Advance to the next site, which widens the shaded interior and raises the cryptic ratio, making edge-starting and careful reading matter more.

## 06. Mechanics & Controls

Inputs: tap/click to reveal; long-press / right-click / flag tool to mark cryptic; separate action to mark extinct.
Hint numbers count butterflies in the eight neighbouring cells (classic Minesweeper logic, logic-only reveals, no random first-click death).
Sunny-edge cells: higher average hint density (node-3). Shaded interior: sparse hints, fewer but rarer species.
Cryptic cells: visually near-empty; flagging as cryptic keeps the species in the record; marking extinct removes it permanently (node-7). A cell marked absent can later flip to a rediscovered cryptic species and award a bonus.
Controls are fully keyboard navigable; grid cursor plus action keys; on-screen legend maps every action.

## 07. Progression

Levels are sites. Early sites (Dairy Farm, Bukit Timah buffer) are open and edge-rich; later sites move into shaded reserves and then contrast urban-park colonists with forest-dependent specialists. Difficulty scales by grid size, interior proportion, and cryptic ratio. Discovering a species for the first time adds its card to a codex with its real status and source, giving long-term collection goals that mirror the actual Butterfly Watch common-species training list.

## 08. Narrative

Light framing: the player is a Butterfly Watch volunteer moving across Singapore's parks and reserves. Each grid is a patch of habitat to survey. Short site cards and occasional seasonal notes (monsoon peaks, urban-park colonisation) supply context without cutscenes. The run closes on the message that conservation is half about noticing the dull, overlooked ones - the exact idea the cryptic-species mechanic is built around.

## 09. World & Characters

No heavy fiction. The player is the volunteer. An optional senior recorder acts as a brief mentor via one-line site notes. The real characters are the butterflies: species are real Singapore taxa (for example Common Mormon, Plain Tiger, Grass Yellows, Tawny Coster) rendered as stylised cards whose facts cite NParks and the research sources. The world is contemporary Singapore's parks, gardens, and reserves.

## 10. UI & Accessibility

High-contrast, colour-blind-safe hint encoding (numbers plus shape/icon, never colour alone). Adjustable grid size and text size, reduced-motion option, optional audio cues for reveal/flag/extinction. A cryptic-difficulty toggle lets younger or casual players reduce ambiguous cells. Clear legend and undo for the last action. Full keyboard and screen-reader navigation with spoken cell state.

## 11. Art & Audio

Clean, bright tropical field-guide aesthetic: sunlit green edges against a cool shaded interior; stylised butterfly cards based on real local species. Ambient garden sound bed; soft confirmation chime on a correct cryptic flag; a low, sombre tone on a mistaken extinction to reinforce the stakes. All audio royalty-free or synthesised; no licensed music.

## 12. Technical Scope

Browser PWA. Vanilla JS plus Canvas (or a lightweight framework) for the grid; plain-data game model; progress saved to localStorage (no backend needed for single-player). Responsive layout for mouse and touch. Estimated small scope: roughly one to two developer-weeks for a vertical slice covering edge-density and cryptic mechanics, codex, scoreboard, and accessibility options.

## 13. Assets

Butterfly card illustrations of real Singapore species (public-domain or NParks-permitted artwork; otherwise stylised originals). Two habitat tile sets (sunny edge, shaded interior). UI icons for reveal/flag/extinct. Royalty-free ambient music and SFX. Codex text sourced from the research document citations (Jain et al. 2018; Khew and Tan 2019; NParks Butterfly Watch). No external API dependency required.

## 14. Acceptance Tests

1. Reveal on edge cells yields a higher average hint count than interior cells (node-3 holds).
2. Flagging a cryptic cell keeps the species in the record; marking it extinct removes it from the score (node-7 holds).
3. A cell previously marked absent can flip to a rediscovered cryptic species and grant a bonus.
4. Scoreboard displays catalogued vs lost and the real Singapore totals (334 extant, 153 extirpated).
5. Game is fully keyboard- and screen-reader-navigable, and colour-blind mode passes contrast checks.
6. No crash on grid resize or reload; progress persists across sessions.
7. All species facts shown link to a cited source.

## CW. Creative feature mappings: Butterfly biodiversity in Singapore

Sunny-edge density hint: Edge and trail cells carry denser butterfly-count hints; the shaded interior is sparse. Players are rewarded for starting reveals at sunny margins, mirroring the real 85-vs-63 species edge/forest split found in Singapore surveys.
Cryptic-species detectability: Cryptic butterflies look almost like empty cells. Flag as cryptic to keep them in the record; mark extinct to lose them permanently. Absent cells can later flip to rediscovered cryptic species for a bonus, reflecting that 6 of 9 recently lost Singapore species were cryptic.
