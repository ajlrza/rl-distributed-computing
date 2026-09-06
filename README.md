# rl-distributed-computing

Distrbuted computing system for [Imitation Learning](https://github.com/LeeMarshall1113/jetspace-imitation-learning)

# Diagram Draft

```mermaid
graph TD
    subgraph Experiment Cluster
        A1 --> A2
    end
    A[CLI] --> A1
    subgraph Remote Cluster
          A1 --> B
      end
    B -- Yes --> C[Great!]
    B -- No --> D[Debug Code]
    D --> B
```
