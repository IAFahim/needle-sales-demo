# Disclosures playing

The fixed opening of every call: company, sales purpose, that the caller is an AI, the recording notice, how to opt out, the anti-phishing line, and the automated-decision notice where the law asks for it.

A part counts only if it plays to the end. If the caller talks over a part, that same part plays again once they stop. After the third interruption the machine gives up in `CouldNotFinish`. `STOP` or `HANGUP` leave at any point in the opening.

| File | What it is |
|---|---|
| [`DisclosuresPlayingSm.puml`](DisclosuresPlayingSm.puml) | the diagram. Edit this one |
| [`DisclosuresPlayingSm.sim.html`](DisclosuresPlayingSm.sim.html) | the simulator. Download it, open it in a browser, click the events |
| [`DisclosuresPlayingSm.cs`](DisclosuresPlayingSm.cs) | the generated machine, C# |
| [`DisclosuresPlayingSm.md`](DisclosuresPlayingSm.md) | StateSmith's description of every state and transition |

## Events

| Event | Sent when |
|---|---|
| `SEGMENT_DONE` | the part finished playing with no interruption |
| `BARGE_IN` | the caller started talking over the part |
| `CALLER_DONE` | the caller stopped talking |
| `STOP` | the caller asked to stop or not be called |
| `HANGUP` | the line closed |

## Variables

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

## Try it in the simulator

1. Start: the machine is in `PlayingSegment`, part 0.
2. `SEGMENT_DONE` six times: it ends in `Complete`.
3. Start again, then `BARGE_IN`, `CALLER_DONE`: it is back in `PlayingSegment` on the same part.
4. Three `BARGE_IN` and `CALLER_DONE` pairs: it ends in `CouldNotFinish`.
