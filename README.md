# rl-distributed-computing

Distrbuted computing system for [Imitation Learning](https://github.com/LeeMarshall1113/jetspace-imitation-learning)

# Diagram Draft

```mermaid
graph TD
    subgraph Z[Experiment Cluster]
        PyTorch --> Code
    end
    subgraph K[Remote Resources]
        RESOURCES --> GPU
    end
    subgraph X[Remote Connection]
          CONTROL
    end
    subgraph Y[Security Layer]
          subgraph J[End User]
                SSH --> CONTROL
            end
      end
    RESOURCES --> CONTROL
    CONTROL --> Y[Security Layer]
    J[End User] --> Z[Experiment Cluster]
    X[Remote Connection] --> A[REMOTE COMPUTER CLI]
    A[REMOTE COMPUTER CLI] --> K[Remote Resources]
```
