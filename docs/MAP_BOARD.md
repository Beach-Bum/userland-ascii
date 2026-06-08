# Map Board

The map should become its own full-screen swipe board.

Updated mobile board order:

```text
NOW -> MAP -> RUNS -> SOUL -> MARKET -> NET
```

The map is not a generic world map. It is a searchable Userland/Index signal map built from lore and game systems.

## Backend rule

The prototype may be static HTML, but production must stay on the main backend stack:

```text
Elixir + Phoenix LiveView + Channels
PostgreSQL
Oban
Hammer
GenServers for active intrusions
server-authoritative LiveView terminal UI
```

The map client should never become the source of truth. It should render server-authoritative cells, search results, active timers, player/faction signals, item sightings, and location states from LiveView assigns / streams / events.

## Why MAP is its own board

MAP is the spatial/search board that connects the rest of the game.

```text
NOW     tells you what matters now
MAP     shows where things are and what can be found
RUNS    executes the breach/action
SOUL    shows identity/failure/recovery
MARKET  handles items/economy
NET     handles social/world signal
```

## Lore model

Userland is a network of digital realities called Indexes, powered by Aura. The Natural World is the player's failing home Index. Paradise Systems maintains Index stability, JADENET created The Natural World and Userland OS, the GIL audits/reboots/unlinks Indexes, and the USER Project handles evacuation/soul transfer logic.

Map zones should come from that fiction.

## Map zones

```text
NATURAL WORLD CORE
  home Index, inefficient Aura, closed I/O, human evacuation pressure

JADENET OPEN ZONE
  open-source tools, repair nodes, beginner-friendly contracts, free-to-win philosophy

PARADISE SYSTEMS ADMIN RING
  governance, Aura allocation, Soul transfer infrastructure, stable but watched

GIL AUDIT FRONT
  audit pressure, trace danger, reboots, unlinking flags, Deep Pit routes

USER PROJECT SIGNAL CHAPEL
  registration, Memory Echoes, soul anchors, evacuation quests

BLACK MARKET / BAZAAR
  player listings, stolen methods, item sightings, fence, auction, trade

SAFEHOUSE MESH
  player bases, furniture, transmitters, bot stations, cached resources

VIOLENCE TOWN / BOUNTY GRID
  PvP, bounties, hostile runner signals, retaliation routes

DEEP PIT / LOCKUP
  failure space, bail/rescue, GIL containment, recovery routes

CRYSTAL PALACE / MICROSOFTS
  high-value chip/software/library economy, learning/training content
```

## Search targets

```text
LOCATIONS
ITEMS
PLAYERS
FACTIONS
TERRITORIES
INDEX NODES
CONTRACTS
CRIMES
BLACK MARKET LISTINGS
SAFEHOUSES
TRANSMITTERS
FRONTS
BOTS
MEMORY ECHOES
GIL AUDITS
```

## Glyph vocabulary

```text
@ player
R runner / other player signal
F faction
T territory
◇ location / node
I item sighting
$ market / SEN opportunity
C contract
! danger / crime / bounty
% corruption / GIL audit
+ route / gate
# boundary / wall
. known open signal
: weak/noisy signal
~ active transmitter / live signal
? unknown
```

## Interactions

```text
SWIPE BOARD
  Directional full-screen decode between boards.

PAN MAP
  Drag inside map mode to move viewport.

TAP CELL
  Decode focused info card for location/item/player/faction/territory.

SEARCH
  Filter/query map. Matching cells pulse and decode result list.

ROUTE
  Route-trace from player to selected target.

ACTION
  Context menu offers Run, Travel, Buy, Sell, Commit Crime, Inspect, Pin, Share, Contact, Bounty, Rescue, Donate, Study.
```

## Tap decode card

Tap any discovered entity and decode a small menu from that cell:

```text
OLD HOSPITAL INDEX
TYPE  LOCATION / LOW RISK RUN
ZONE  NATURAL WORLD CORE
RISK  HEAT +2 / GIL LOW
LOOT  MEMORY ECHO / SEN / PATCH
ACTIONS: RUN / ROUTE / PIN / SHARE
```

## Map to existing repo features

```text
City / Natural World
  Natural World Core, public locations, Index overview

Runs / Hack
  breachable map nodes, target grids, route into RUNS board

Crimes
  illegal opportunities, danger nodes, heat modifiers

Contracts / Quests / Jobs
  faction and job nodes

Items / Loadout / Depot
  item sightings, caches, salvage, source zones

Black Market / Auction / Trade / Fence
  Bazaar cells and player-market listings

Safehouses / Furniture / Transmitters
  base mesh and owned territory

Faction / Crew / Fronts
  faction territories, fronts, crew signals

Bounties / PvP / Violence Town
  hostile runner signals and bounty routes

Clinic / Lockup / Ripperdoc
  recovery, rescue, augment, failure spaces

Bots / Microsofts / Crystal Palace
  bot stations, learning/chip/software zones
```

## Production LiveView shape

Suggested module split:

```text
UserlandWeb.MapLive
  LiveView board/screen.

Userland.Map
  context for zones, nodes, search, visibility.

Userland.Map.Node
  location/item/player/faction/territory signal.

Userland.Map.Visibility
  discovered/hidden/unknown cell states.

Userland.Map.Search
  query -> matching nodes.

Userland.Map.Route
  route path for trace animation.
```

LiveView events:

```text
phx-click="map_select"
phx-click="map_route"
phx-change="map_search"
phx-click="map_action"
phx-window-keydown="map_key"
phx-hook="AsciiMap"
```

Channels can later stream live player/faction signals when needed. LiveView should be enough for the first board.

## First prototype content

Use these initial sample nodes:

```text
@ YOU                 Natural World Core
◇ OLD HOSPITAL        low-risk run / Memory Echo
◇ PEGGY SIGNAL        USER Project registration / soul anchor
F JADENET RELAY       open tools / repair contract
% GIL AUDIT FRONT     high trace / unlinking flag
$ BLACK MARKET NODE   items, fence, auction, trade
T SAFEHOUSE MESH      base, transmitter, bot station
! VIOLENCE TOWN       bounties, hostile runners
I KERNEL LENS CACHE   found item / salvage
C PARADISE CONTRACT   stability job / SEN reward
```
