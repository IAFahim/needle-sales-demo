# Needle sales agent: StateSmith demo

The call flow of the Needle sales agent as StateSmith state machines. Each scenario has its own folder with the diagram, the generated code, a simulator you can click through, and a README. The scenarios don't link to each other yet.

## Scenarios

| Scenario | Diagram | Simulator | Code | What it does |
|---|---|---|---|---|
| [Disclosures playing](scenarios/DisclosuresPlaying/) | [puml](scenarios/DisclosuresPlaying/DisclosuresPlayingSm.puml) | [sim.html](scenarios/DisclosuresPlaying/DisclosuresPlayingSm.sim.html) | [cs](scenarios/DisclosuresPlaying/DisclosuresPlayingSm.cs) | plays the fixed opening; talking over a part replays it; the third interruption gives up |

## Open a simulator

The simulators are on this repo's GitHub Pages site: Settings, Pages, Visit site. The site lists every scenario; click one, then click its events.

The site is built from the `gh-pages` branch, which holds only the `.sim.html` files and a list page. Anyone with its link can open it, even though the repo is private. After you change a scenario, copy its new `.sim.html` to the same path on `gh-pages` and push.

Or open one locally: download the `.sim.html` and open it in a browser.

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
