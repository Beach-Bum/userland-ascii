# Mobile Screen Model

Userland mobile should be five full-screen deck boards, not a menu dump.

```text
NOW -> RUNS -> SOUL -> MARKET -> NET
```

Each board fills the phone grid. Swiping moves between boards and decodes the next board into the same ASCII character grid.

## Shared screen skeleton

```text
TOP STRIP
  board name, Index/location, Aura, Nerve, Heat, SEN

PRIMARY AREA
  one main job for the screen

UTILITY RACK
  compact widgets/actions/status

EVENT STRIP
  Netwire, result, timer, alert

BOTTOM RAIL
  NOW RUNS SOUL MARKET NET
```

The bottom rail is a direct-jump fallback. The main interaction fantasy is swiping through installed deck boards.

## NOW

Purpose: return-home ritual and command center.

Use most of the screen for:

```text
current Index / signal
resources
best next action
active timer or danger
one primary widget
Netwire alert strip
```

Priority order for primary widget:

```text
active run
danger or attack
completed reward
recommended run
crew/faction opportunity
market opportunity
```

## RUNS

Purpose: Index intrusion loop.

Flow:

```text
Inspect -> Load Methods -> Breach -> Survive Trace -> Extract -> Aftermath
```

Mobile layout:

```text
TOP     target + Heat/Trace pressure
CENTER  map/grid/node/tool animation
BOTTOM  Method loadout + action rail
POST    Sell / Study / Run Again
```

This is the most animated board.

## SOUL

Purpose: identity, failure, and recovery.

Shows:

```text
Coherence
Integrity
Shatter risk
USER registration
Memory Echoes
Deep Pit / Flatline / recovery
```

This board should feel diagnostic and eerie, but still readable.

## MARKET

Purpose: items, loadout, economy.

Absorbs:

```text
Items
Loadout
Market
Bazaar / Black Market
Auction
Trade
Fence
Bank
Exchange
Depot
Crystal Palace
```

Every item card answers:

```text
what is it?
why does it matter?
what is it worth?
what can I do with it?
```

Rows stay compact. Detailed modular item ASCII appears in inspect modals.

## NET

Purpose: social/world signal.

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
run result shares
market notifications
world events
```

Chat bodies must be calm read surfaces. Event cards can be more visual.

## Route mapping from main repo

```text
NOW
  Home, current status, active timers, best action, alerts

RUNS
  Hack/Runs, Training, Crimes, Contracts/Quests, Violence Town/PvP, Bounties, Jobs

SOUL
  Profile, Ripperdoc, Clinic, Lockup, Microsofts/Academy, USER status, Memory Echoes

MARKET
  Items, Loadout/Equipment, Market, Black Market/Bazaar, Auction, Trade, Fence, Bank, Exchange, Depot, Crystal Palace, Casino

NET
  Chat, Mail, Forum, Feed, Crew, Faction, Leaderboard, Bots, Fronts, Transmitters, Safehouse alerts
```
