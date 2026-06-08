# userland-ascii

ASCII/grid UI design archive for **Userland**.

This repository preserves the mobile terminal visual system we have been prototyping: 8x14 cell grid, all-caps terminal typography, Cogmind-like decode transitions, modular item art, and full-screen swipe deck navigation.

## Current north star

Userland should feel like a mobile cyberpunk deck OS, not a generic responsive web app.

The main mobile structure is five full-screen boards:

```text
NOW -> RUNS -> SOUL -> MARKET -> NET
```

Swiping left/right moves between whole screens. The next screen decodes into the same ASCII grid in the direction of the swipe.

## Core rules

```text
1. THE GRID IS THE SURFACE
   Everything is drawn into the same 8x14 ASCII cell grid.

2. NO OVERLAY CHEATS
   Decode animation should not look like a mask, pattern, or separate layer.

3. DECODE DIRECTION MATCHES NAVIGATION
   Swipe left / next screen      = left-to-right decode.
   Swipe right / previous screen = right-to-left decode.

4. WORKING TOOLS DO NOT GLITCH
   Unknown/corrupted data can glitch. Working tools should look like clean electronics diagrams: ports, wires, routes, signal flow, result lock.

5. EACH SCREEN HAS ONE JOB
   NOW = status and best next action.
   RUNS = grid/action/tool animation.
   SOUL = identity/failure/recovery diagnostics.
   MARKET = items/loadout/economy.
   NET = chat/feed/faction/world signal.
```

## Files

```text
prototypes/directional-decode-swipe-deck.html
  Five-screen mobile deck prototype. Direction-aware swipe decode.

docs/MEMORY.md
  Conversation memory and decisions to preserve.

docs/ANIMATION_SYSTEM.md
  Animation grammar for decode, route trace, tool use, and result lock.

docs/MOBILE_SCREENS.md
  Screen model and mapping from the larger Userland app into five mobile boards.

docs/MAP_NEXT.md
  Next design target: bring back the searchable map using the same grid/decode language and wiki lore.
```

## Related repositories

```text
Beach-Bum/userland
  Main Phoenix/LiveView game repo.

Beach-Bum/userland-wiki
  Lore/wiki source for Indexes, locations, factions, territories, and map language.
```

## Current next task

Bring back the map as a full-screen mobile board/system using this same ASCII grid language.

The map should let players search around for:

```text
LOCATIONS
ITEMS
OTHER PLAYERS
FACTIONS
TERRITORIES
INDEX NODES
CONTRACTS
SIGNALS
```

It should be built from `userland-wiki` lore, not generic map filler.
