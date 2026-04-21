
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
<img width="917" height="528" alt="Gateway_alpha" src="https://github.com/user-attachments/assets/8cfa112b-e374-41bc-bb35-7a273626b3b3" />
<img width="1920" height="1080" alt="TPMPanel_1" src="https://github.com/user-attachments/assets/d72ab569-6c0f-4371-a6f6-78a5865c6693" />
<img width="1920" height="1080" alt="TPMPanel_2" src="https://github.com/user-attachments/assets/85d9eb49-f97f-422a-af45-1a81e2484a89" />
<img width="1920" height="1080" alt="TPM_Panel_ScreenShot" src="https://github.com/user-attachments/assets/2cce5a7b-38d3-4fad-84be-bb38e58960d2" />
<img width="1920" height="1080" alt="TestFlight_LaunchPad" src="https://github.com/user-attachments/assets/813fad71-88a6-4194-ae57-927a883c1609" />
<img width="1920" height="1080" alt="Overseer" src="https://github.com/user-attachments/assets/6521440d-d805-4702-843f-66e8039aec1b" />
<img width="1920" height="1080" alt="Model_Hanger" src="https://github.com/user-attachments/assets/2bbdbbdd-7a96-40b4-b963-54ff9ef3079b" />
<img width="1920" height="1080" alt="Kanban" src="https://github.com/user-attachments/assets/73cd9686-9a4f-4366-8bf7-85735576cfb0" />
<img width="1920" height="1080" alt="Settings" src="https://github.com/user-attachments/assets/91039d24-29ae-4790-a828-a3c6756f3ee5" />
<img width="1920" height="1080" alt="Files-Artifacts-Rag" src="https://github.com/user-attachments/assets/d958b740-4d52-4425-8944-120305655685" />
<img width="1920" height="1080" alt="Console" src="https://github.com/user-attachments/assets/42e851ba-7f43-4402-ae27-fc51b3363c88" />
