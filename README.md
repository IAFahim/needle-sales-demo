# Needle sales agent: StateSmith demo

The call flow of the Needle sales agent as StateSmith state machines. Each scenario has its own folder with the diagram, the generated code, a simulator you can click through, and a README. The scenarios don't link to each other yet.

## Scenarios

| Scenario | Diagram | Simulator | Code | What it does |
|---|---|---|---|---|
| [Disclosures playing](scenarios/DisclosuresPlaying/) | [puml](scenarios/DisclosuresPlaying/DisclosuresPlayingSm.puml) | [sim.html](scenarios/DisclosuresPlaying/DisclosuresPlayingSm.sim.html) | [cs](scenarios/DisclosuresPlaying/DisclosuresPlayingSm.cs) | plays the fixed opening; talking over a part replays it; the third interruption gives up |

## Open a simulator

GitHub shows a `.sim.html` file as text. Download it (the download button on the file's page) and open it in a browser. Click an event on the right to send it; the diagram shows the current state.

## Make the code again

After you change a diagram, in its folder:

```
ess r
```

`ess` runs StateSmith 0.22.2 and writes the `.cs`, `.md` and `.sim.html` next to the diagram.

## Layout

```
scenarios/
  <Scenario>/
    <Scenario>Sm.puml       the diagram, with its settings and variables
    <Scenario>Sm.sim.html   the simulator
    <Scenario>Sm.cs         the generated machine
    <Scenario>Sm.md         StateSmith's description of the machine
    README.md               what it does, its events and variables
```

The research behind these is in `needle-sales-learning`.
