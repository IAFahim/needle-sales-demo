AFTER TRANSFORMATIONS
===========================================================

Vertex: Preamble.\<ChoicePoint>(AfterBargeIn)
-----------------------------------------
- Parent: Preamble
- Type: ChoicePoint
- Diagram Id: AfterBargeIn

### Behaviors
    [bargeInCount <= maxBargeIns] TransitionTo(PlayingSegment)

    else TransitionTo(CouldNotFinish)


Vertex: CallerTalking
-----------------------------------------
- Parent: Preamble
- Type: State
- Diagram Id: CallerTalking

### Behaviors
    CALLER_DONE TransitionTo(Preamble.<ChoicePoint>(AfterBargeIn))


Vertex: Complete
-----------------------------------------
- Parent: ROOT
- Type: State
- Diagram Id: Complete

### Behaviors
    enter / { preambleComplete = true; }


Vertex: CouldNotFinish
-----------------------------------------
- Parent: ROOT
- Type: State
- Diagram Id: CouldNotFinish

### Behaviors
    enter / { preambleComplete = false; }


Vertex: Preamble.\<ChoicePoint>(CountSegments)
-----------------------------------------
- Parent: Preamble
- Type: ChoicePoint
- Diagram Id: CountSegments

### Behaviors
    [admtRequired] / { segmentCount = 7; } TransitionTo(PlayingSegment)

    else / { segmentCount = 6; } TransitionTo(PlayingSegment)


Vertex: ROOT
-----------------------------------------
- Type: StateMachine
- Diagram Id: DisclosuresPlayingSm
- Initial State: ROOT.\<InitialState>

### Behaviors


Vertex: HungUp
-----------------------------------------
- Parent: ROOT
- Type: State
- Diagram Id: HungUp

### Behaviors


Vertex: Preamble.\<InitialState>
-----------------------------------------
- Parent: Preamble
- Type: InitialState
- Diagram Id: line_11_column_4

### Behaviors
    TransitionTo(Preamble.<ChoicePoint>(CountSegments))


Vertex: ROOT.\<InitialState>
-----------------------------------------
- Parent: ROOT
- Type: InitialState
- Diagram Id: line_3_column_0

### Behaviors
    TransitionTo(Preamble)


Vertex: Preamble.\<ChoicePoint>(NextSegment)
-----------------------------------------
- Parent: Preamble
- Type: ChoicePoint
- Diagram Id: NextSegment

### Behaviors
    [segmentIndex < segmentCount] TransitionTo(PlayingSegment)

    else TransitionTo(Complete)


Vertex: PlayingSegment
-----------------------------------------
- Parent: Preamble
- Type: State
- Diagram Id: PlayingSegment

### Behaviors
    enter / { playing = true; }

    exit / { playing = false; }

    SEGMENT_DONE / { segmentIndex += 1; } TransitionTo(Preamble.<ChoicePoint>(NextSegment))

    BARGE_IN / { bargeInCount += 1; } TransitionTo(CallerTalking)


Vertex: Preamble
-----------------------------------------
- Parent: ROOT
- Type: State
- Diagram Id: Preamble
- Initial State: Preamble.\<InitialState>

### Behaviors
    enter / { segmentIndex = 0; bargeInCount = 0; maxBargeIns = 2; }

    STOP TransitionTo(StopRequested)

    HANGUP TransitionTo(HungUp)


Vertex: StopRequested
-----------------------------------------
- Parent: ROOT
- Type: State
- Diagram Id: StopRequested

### Behaviors
    enter / { stopRequested = true; }
