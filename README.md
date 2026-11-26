# Needle sales agent: StateSmith demo

The call flow of the Needle sales agent as StateSmith state machines. Each scenario is one self-contained diagram in `scenarios/`, with its own settings and variables. They don't link to each other yet.

| Scenario | File | What it does |
|---|---|---|
| Disclosures playing | `scenarios/DisclosuresPlayingSm.puml` | plays the fixed opening one part at a time; a part counts only if it plays to the end; talking over it replays that part; the third interruption gives up; STOP or HANGUP leave at any point |

## Make the code

With [ess](https://github.com/IAFahim/ess):

```
cd scenarios
ess r
```

That writes `DisclosuresPlayingSm.cs` (a struct in the namespace `Machines`), `DisclosuresPlayingSm.md` and `DisclosuresPlayingSm.sim.html`. Open the `.sim.html` in a browser and click the events.

Without ess, StateSmith 0.22.2 does the same: `ss.cli run --here` in `scenarios/`.

## Variables in the disclosures scenario

| Variable | Meaning |
|---|---|
| `admtRequired` | set before start: the opening has 7 parts instead of 6 |
| `segmentCount` | how many parts this opening has |
| `segmentIndex` | the part playing now; the host plays the fragment for it |
| `bargeInCount` | how many times the caller has talked over a part |
| `maxBargeIns` | how many interruptions are allowed (2) |
| `playing` | true while a part is playing |
| `preambleComplete` | true once every part played through |
| `stopRequested` | true if the caller said stop |

The research behind these is in `needle-sales-learning`.
