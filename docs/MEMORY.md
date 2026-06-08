# Userland ASCII Memory

This file preserves the design decisions from the mobile ASCII/deck UI prototyping session so the system can be resumed later without losing context.

## Project

`userland-ascii` is the archive and working design lab for Userland's mobile ASCII terminal UI.

The main game repo is `Beach-Bum/userland`.
The lore/wiki repo is `Beach-Bum/userland-wiki`.

## Visual foundation

- Mobile-first phone/deck interface.
- 8x14 fixed cell grid.
- All caps.
- Pixel/crisp terminal feel.
- Every visible mark should live in the ASCII grid.
- Avoid blurry PNG mockups; prefer live browser HTML prototypes.
- Dense but readable. No spacious cards.
- Use solid color edges, line borders, panels, glyphs, and rows as a real vocabulary.

## Important correction

Do not fake the decode with a mask, overlay, generic background pattern, or top-to-bottom reveal.

The decode should operate on the same ASCII cells that become the final screen.

Correct screen transition model:

```text
old screen remains visible
new screen replaces it column-by-column
swipe direction controls decode direction
mixed cells inside each column resolve into final ASCII
no pure dark blank screen
no separate animated pattern behind the UI
```

## Swipe navigation

The five mobile boards are full screens:

```text
NOW -> RUNS -> SOUL -> MARKET -> NET
```

Navigation rule:

```text
swipe left / next screen      = left-to-right decode
swipe right / previous screen = right-to-left decode
```

Bottom rail can remain for direct navigation, but the fantasy is swiping through installed deck boards.

## Five mobile boards

### NOW
Command center and return-home ritual.

Shows:

```text
current Index / signal
Aura / Nerve / Heat / Coherence / SEN
best next action
active timer or danger
primary widget
Netwire alert strip
```

### RUNS
Highest-intensity interaction screen.

Flow:

```text
Inspect -> Load Methods -> Breach -> Survive Trace -> Extract -> Aftermath
```

This is where grid, targeting, route traces, tool use, and electronics-style animation belong.

### SOUL
Identity, diagnostics, failure, recovery.

Shows:

```text
Coherence
Integrity
Shatter risk
USER registration
Memory Echoes
Deep Pit / Flatline / recovery
```

### MARKET
Items, loadout, economy.

Absorbs:

```text
Items
Loadout
Market
Black Market / Bazaar
Auction
Trade
Fence
Bank
Exchange
Depot
Crystal Palace
```

Rows stay compact. Detailed modular item ASCII appears in inspect modals.

### NET
Social/world signal.

Absorbs:

```text
Chat
Mail
Forum
Feed
Crew
Faction
Leaderboard
Bounties
world events
run result shares
market notifications
```

Chat and reading surfaces must stay low-noise.

## Animation grammar

Only a few animation types should exist:

```text
DECODE-IN
  New objects, screens, panels, labels, item art.

ROUTE-TRACE
  Tool targeting, map connection, scan line, wire path.

SIGNAL-FLOW
  Working tools, electronics, active devices.

RESULT-LOCK
  Success/fail/status stabilization.
```

Unknown/corrupted data may glitch.
Working tools should not glitch.

## Working tools

A working tool should look like a clean electronics diagram, not static.

Correct:

```text
ports light
core pulses
bus routes
signal dots move along wires
result banner locks
```

Incorrect:

```text
random static over working tool
separate overlay animation
full-screen flashing
pure decorative noise behind text
```

## Modular items

Complex items are recipes, not one-off static drawings.

Item structure:

```text
CHASSIS + CORE + LENS + BUS + COIL + PORTS + WIRES + SKIN
```

Assembly should be clean and visible:

```text
part draws into the grid
part stabilizes
next part draws
connections resolve
final item locks
```

## Map next

Bring back the map as a first-class grid system.

The map should support searching/exploring:

```text
locations
items
players
factions
territories
Index nodes
contracts
signals
```

It must use the same ASCII grid, decode, route-trace, and lore language. It should be built from `userland-wiki`, not generic cyberpunk filler.
