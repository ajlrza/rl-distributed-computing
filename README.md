# rl-distributed-computing

Distrbuted computing system for [Imitation Learning](https://github.com/LeeMarshall1113/jetspace-imitation-learning)

# Diagram Draft

```mermaid
graph TD

    subgraph K[Remote Resources 1]
        style K fill:#e8f5e9,stroke:#2e7d32,stroke-width:2px,color:#000
        RESOURCES_ONE --> GPU_ONE
    end
    subgraph KNOCK_MECHANISM_1
        style KNOCK_MECHANISM_1 fill:#fff8e1,stroke:#f57f17,stroke-width:2px,color:#000
    end
    subgraph KNOCK_MECHANISM_2
        style KNOCK_MECHANISM_2 fill:#fff8e1,stroke:#f57f17,stroke-width:2px,color:#000
    end
    subgraph KNOCK_MECHANISM_3
        style KNOCK_MECHANISM_3 fill:#fff8e1,stroke:#f57f17,stroke-width:2px,color:#000
    end
    subgraph E[Remote Resources 2]
        style E fill:#e8f5e9,stroke:#2e7d32,stroke-width:2px,color:#000
        RESOURCES_TWO --> GPU_TWO
    end
    subgraph F[Remote Resources 3]
        style F fill:#e8f5e9,stroke:#2e7d32,stroke-width:2px,color:#000
        RESOURCES_THREE --> GPU_THREE
    end
    subgraph X[REMOTE CONNECTION]
        style X fill:#e3f2fd,stroke:#1565c0,stroke-width:2px,color:#000
    end
    subgraph Y[Security Layer]
        style Y fill:#f3e5f5,stroke:#6a1b9a,stroke-width:2px,color:#000
        subgraph J[End User]
            style J fill:#ce93d8,stroke:#4a148c,stroke-width:2px,color:#000
            SSH
        end
    end
    subgraph Z[Experiment Cluster]
        style Z fill:#eceff1,stroke:#455a64,stroke-width:2px,color:#000
        PyTorch --> Code
    end

    CONTROL --> X[REMOTE CONNECTION]
    CONTROL --> Y[Security Layer]
    X[Remote Connction] --> A[REMOTE COMPUTER CLI]
    X[Remote Connction] --> CONTROL
    Y[Security Layer] --> CONTROL
    
    A[REMOTE COMPUTER CLI] --> KNOCK_MECHANISM_1
    KNOCK_MECHANISM_1 --> System_Call_1
    System_Call_1 --> Resources_Check_1
    Resources_Check_1 -->|UP_1| CONTINUE_THE_1 --> K[Remote Resources 1] --> System_Call_1 --> KNOCK_MECHANISM_1 --> A[REMOTE COMPUTER CLI]
    Resources_Check_1 -->|DOWN_1| SKIP_THE_1
    
    A[REMOTE COMPUTER CLI] --> KNOCK_MECHANISM_2
    KNOCK_MECHANISM_2 --> System_Call_2
    System_Call_2 --> Resources_Check_2
    Resources_Check_2 -->|UP_2| CONTINUE_THE_2 --> E[Remote Resources 2] --> System_Call_2 --> KNOCK_MECHANISM_2 --> A[REMOTE COMPUTER CLI]
    Resources_Check_2 -->|DOWN_2| SKIP_THE_2
    
    A[REMOTE COMPUTER CLI] --> KNOCK_MECHANISM_3
    KNOCK_MECHANISM_3 --> System_Call_3
    System_Call_3 --> Resources_Check_3
    Resources_Check_3 -->|UP_3| CONTINUE_THE_3 --> F[Remote Resources 3] --> System_Call_3 --> KNOCK_MECHANISM_3 --> A[REMOTE COMPUTER CLI]
    Resources_Check_3 -->|DOWN_3| SKIP_THE_3  
    
    A[REMOTE COMPUTER CLI] --> X[Remote Connection]
    CONTROL --> Z[Experiment Cluster]
    Z[Experiment Cluster] --> CONTROL

    classDef controlNodes fill:#ffebee,stroke:#c62828,stroke-width:2px,color:#000;
    classDef sysCalls fill:#e0f7fa,stroke:#00838f,stroke-width:2px,color:#000;
    classDef resources fill:#c8e6c9,stroke:#2e7d32,stroke-width:1px,color:#000;
    classDef actions fill:#fff3e0,stroke:#ef6c00,stroke-width:1px,color:#000;
    classDef clusterNodes fill:#cfd8dc,stroke:#455a64,stroke-width:1px,color:#000;

    class CONTROL,A controlNodes;
    class System_Call_1,System_Call_2,System_Call_3,Resources_Check_1,Resources_Check_2,Resources_Check_3 sysCalls;
    class RESOURCES_ONE,GPU_ONE,RESOURCES_TWO,GPU_TWO,RESOURCES_THREE,GPU_THREE resources;
    class CONTINUE_THE_1,SKIP_THE_1,CONTINUE_THE_2,SKIP_THE_2,CONTINUE_THE_3,SKIP_THE_3 actions;
    class SSH actions;
    class PyTorch,Code clusterNodes;
```
