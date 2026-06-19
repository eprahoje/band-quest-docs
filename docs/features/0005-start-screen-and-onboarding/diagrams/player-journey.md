# Player Journey Diagram

This is the feature-owned source of truth for the player journey flowchart.

```mermaid
flowchart TD
    Start([Start]) --> Launch[Open game]
    Launch --> FirstTime{First time player?}
    FirstTime -->|Yes| Onboarding[Show onboarding]
    FirstTime -->|No| MainMenu[Open main menu]
    Onboarding --> MainMenu

    MainMenu --> NewGame[Start new game]
    MainMenu --> Continue[Continue save]
    MainMenu --> Settings[Open settings]

    NewGame --> Era[Choose era]
    Era --> Band[Create band]
    Band --> Tutorial[Short guided tutorial]
    Tutorial --> FirstStep[Take the first action]

    FirstStep --> ProgressLoop[Core progression loop]
    Continue --> ProgressLoop
    Settings --> MainMenu

    ProgressLoop --> Economy[Manage money and reputation]
    Economy --> Milestone{New milestone unlocked?}
    Milestone -->|Yes| Unlock[Unlock next career step]
    Milestone -->|No| Adjust[Adjust strategy]
    Unlock --> ProgressLoop
    Adjust --> ProgressLoop
```

## Notes

- The first player choice is era selection.
- The journey should remain short on first launch.
- This diagram is referenced by [docs/journeys/player-journey.md](../../../journeys/player-journey.md).