# Animation System

This document defines the shared animation grammar for Userland's mobile ASCII deck UI.

## Principle

The animation is not a decoration layer. The animation is the ASCII grid writing itself.

```text
GRID CELL -> TEMP DECODE GLYPH -> FINAL ASCII GLYPH
```

Every transition should resolve into the same 8x14 character grid the player uses after the animation finishes.

## Screen transition

The five mobile boards are paged screens:

```text
NOW <-> RUNS <-> SOUL <-> MARKET <-> NET
```

Swipe direction controls decode direction:

```text
swipe left / next board      = decode left to right
swipe right / previous board = decode right to left
```

Implementation model:

```text
1. Capture the old full screen buffer.
2. Render the target full screen into an offscreen/future buffer.
3. Keep the old buffer visible.
4. Replace columns in the target direction.
5. Within each active column, mix cells so it feels like a field resolving, not row-by-row drawing.
6. Final cells become the exact target screen glyph/class.
```

Do not reveal top-to-bottom. Do not use a black mask. Do not animate a separate background pattern.

## Decode-in

Used for:

```text
screen transitions
new panels
item art
modals
labels
new map regions
search results
```

Correct behavior:

```text
old glyphs remain until replaced
new glyphs resolve from mixed decode cells
blank final cells resolve to blank grid cells, not a decorative background
```

## Route-trace

Used for:

```text
tool targeting
map search paths
wire routes
scan lines
network links
```

A route trace should follow actual grid paths.

```text
source port -> route cells -> target cell -> result lock
```

## Signal-flow

Used when tools or devices are working.

Correct:

```text
ports light
core pulses
bus routes
signal dots travel along wires
status labels update
```

Incorrect:

```text
random glitch over working tools
screen-wide static
visual noise behind readable text
```

## Result-lock

Used after an action completes.

Examples:

```text
BREACH COMPLETE
NODE SCANNED
ITEM FOUND
TERRITORY CLAIMED
PLAYER SIGNAL LOST
FACTION ROUTE OPEN
```

Result-lock should be short and stable. It can flash once, then become a normal row/card/banner.

## Motion intensity

```text
RUNS       highest intensity
MAP        medium/high while searching, medium when browsing
NOW        medium
MARKET     medium/low except item inspect
SOUL       diagnostic, eerie, controlled
NET        low noise for chat/read surfaces
```

## Reduced motion

A reduced-motion mode should keep the same state changes but remove the repeated animation:

```text
screen jump + one edge pulse + result lock
```

## Implementation note

Keep animation functions reusable:

```text
decodeScreen(fromBuffer, toBuffer, direction)
decodeRegion(rect, targetBuffer, direction)
routeTrace(points, speed, color)
signalFlow(points, phase, color)
resultLock(rect, label, state)
```
