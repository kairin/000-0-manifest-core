# 000-0-manifest-core

Public setup guide for a new device. It shows how the core repositories fit together. The private repository inventory is kept elsewhere.

```mermaid
flowchart TB
    subgraph Rules["Rules and navigation"]
        W["000-0-workspace<br/>Shared policies, procedures and architecture"]
        M["000-0-manifest-core<br/>Public setup guide and bootstrap script"]
        S["000-0-ASD-STE100<br/>Writing standards and prose checker"]
    end

    subgraph Operations["Machine setup and automation"]
        A["000-0-ai<br/>AI configuration, skills, safeguards<br/>and update command"]
        D["000-0-dotfiles<br/>Machine and Bash setup<br/>Development-tool catalog, doctor and installer"]
        P["000-0-password<br/>Encrypted secrets and with-secret"]
    end

    subgraph Specialist["Terminal and database guidance"]
        G["000-0-ghostty<br/>Terminal configuration and integration"]
        TM["000-0-tmux-cheat-sheet<br/>Persistent terminal and agent sessions"]
        T["000-0-tables<br/>Database stack, research and reusable patterns"]
    end

    W -. "shared policies" .-> Operations
    W -. "shared policies" .-> Specialist
    M -. "points new devices to setup" .-> W
    S -. "writing standards" .-> W
    S -. "source for ste-writing skill" .-> A

    A -->|"calls development-tool checks and repairs"| D
    A -->|"builds Ghostty, installs Kitty and checks configuration"| G

    D -. "Bash integration and fonts" .-> G
    D -. "provides tmux" .-> TM
    TM -. "guidance for running agent sessions" .-> A

    P -. "secrets when required" .-> A
    P -. "credentials when required" .-> T
```

## Core repository connections

Solid arrows show operational connections. Dotted arrows show guidance, navigation, or support.


Workspace policies and STE writing rules apply to all nine core repositories. The new-device bootstrap script prepares a blank computer to run the update command.
