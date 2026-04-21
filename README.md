# JetsenAiSoftwareFoundry
The Foundry is a semi-automated software creation / lab orchestration tool that aims to connect nodes / robots into a collective in order to pool intelligence and capabilities across systems in real time.

## System Topology

```mermaid
flowchart LR
    subgraph Lab["Jetsen AI Software Foundry"]
        O["Overseer (gateway)"]
        KB["KanBan (task board)"]
        Q["Lab Queue (tasks & flights)"]

        %% TPM side (separate)
        subgraph TPM["TPM Agent"]
            V["Vision"]
            R["Roadmap"]
            T["Timeline"]
            RS["Research"]
            BP["BuildPlan"]
            KBT["KanBan view"]
        end

        %% Control flow
        TPM ---> KBT
        KBT --> KB
        KB --> O
        O --> Q

        subgraph Nodes["Execution Nodes"]
            MM["Mac mini<br/>(LLM / SD / Draw Things)"]
            LX["Linux JetPack 6.2<br/>(LLM / SD / Vision / OCR)"]
            PC["PC<br/>(LLM / SD / TRT / A1111 / ComfyUI / vLLM)"]
            IP["iPad Pro (M4)<br/>(LLM / LiDAR / Vision capture client)"]
            CL["Cloud<br/>(LLM / SD fallback)"]
        end

        %% Queue dispatch to nodes
        Q --> MM
        Q --> LX
        Q --> PC
        Q --> IP
        Q --> CL

        %% Results flow back to Overseer
        MM --> O
        LX --> O
        PC --> O
        IP --> O
        CL --> O

        %% Grading back to TPM
        O --> KBT
    end

    %% Capability bubbles
    classDef cap fill:#152b46,stroke:#3da9f5,color:#fff,font-size:11px;
    capLLM["LLM"]:::cap
    capSD["SD"]:::cap
    capDT["Draw Things"]:::cap

    MM --> capLLM
    MM --> capSD
    MM --> capDT
    LX --> capLLM
    LX --> capSD
    PC --> capLLM
    PC --> capSD
    IP --> capLLM
    CL --> capLLM
    CL --> capSD
```

<img width="1920" height="1080" alt="Jetsen_Desktop" src="https://github.com/user-attachments/assets/df80a8bd-6597-4236-952b-8ef8351fcd31" />
