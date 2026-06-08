# Map System Next

The next major design task is bringing back the map.

The map should use the same ASCII/grid/decode language as the five-screen deck and the item/tool animation system.

## Map goal

The player should be able to search around the world for:

```text
locations
items
other players
factions
territories
Index nodes
contracts
signals
safehouses
transmitters
fronts
```

This should not be a generic cyberpunk map. It should be built from `Beach-Bum/userland-wiki` lore.

## Lore source

Use `Beach-Bum/userland-wiki` as the source for:

```text
Mindscape
Indexes
Natural World
USER Project
GIL
JADENET
Paradise Systems
Duishou
factions
territories
locations
Signals
Memory Echoes
Deep Pit
```

The map should expose lore through search, territory, faction pressure, and discoverable routes.

## Screen placement

The map probably belongs inside RUNS and NOW first.

```text
NOW
  small current Index/local signal widget
  best next map opportunity

RUNS
  full interactive map/search/breach grid

NET
  faction/world signals can open map focus

MARKET
  item/source/territory filters can open map focus
```

Do not add a sixth primary board yet. Test the map as a RUNS primary mode first.

## Map visual grammar

Use the same cell vocabulary:

```text
# wall / blocked / hard boundary
. known floor / open signal
: noise / weak signal
~ active signal
+ door / route / gate
◇ node / point of interest
@ player
A agent
D daemon
F faction marker
T territory
I item signal
? unknown
! danger
% corruption
```

## Map interactions

```text
PAN
  drag grid or swipe within map mode.

SEARCH
  type/filter: location, item, player, faction, territory.

SCAN
  decode unknown cells or reveal nearby nodes.

ROUTE
  route-trace from player to target.

INSPECT
  open focused cell card.

BREACH
  convert a map target into a RUNS action.
```

## Animation rules

The map must follow the same grammar:

```text
DECODE-IN
  reveals new map cells, territories, search results.

ROUTE-TRACE
  draws path from player to target.

SIGNAL-FLOW
  shows active scanner, transmitter, or faction pressure.

RESULT-LOCK
  locks found location/item/player/faction result.
```

No animated background pattern. The map itself is the ASCII grid.

## Map search examples

```text
SEARCH: ITEM / KERNEL LENS
  highlights possible markets, caches, player listings, faction sources.

SEARCH: FACTION / GIL
  shows audit pressure, Deep Pit routes, locked territory.

SEARCH: PLAYER / MIRA
  shows last known signal, crew channel, route risk.

SEARCH: TERRITORY / JADENET
  shows open access zones, repair nodes, contracts.

SEARCH: LOCATION / OLD HOSPITAL
  reveals Index node, breach risk, reward tags.
```

## First prototype

Create a mobile RUNS/MAP board with:

```text
map grid
search row
filter chips
focused target card
route trace
result lock
```

Use fake data first, but name the fake data from wiki concepts. Then wire it to actual wiki-derived location/faction data.
