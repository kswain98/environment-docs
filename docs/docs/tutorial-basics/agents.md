---
sidebar_position: 2
---

# Agents

VirtualCity is filled with interactable objects and **Agents** are key part of the environment. There are 3 main types of agents that can be used within the environment:

- **Humanoids**
- **Robots**
- **Vehicles**

## Initialize a controllable agent

Place a agent inside your environment using the `add_agent` function:

```python
import virtualcity

environment.add_agent(
    num_agent=[1],
    agent_type="humanoid",
    coordinate=[0, 0, 0]
)
```
- `num_agent` → select the number of agents that will be placed in the environment `[int]`
- `agent_type` → select the type of agent `humanoid`, `robot`, `vehicle`
- `coordinate` → select the coordinate for where the agent should be placed `[int, int, int]`

`NOTE`: All the agents within VirtualCity support both high-level and low-level control. However, the amount of high-level actions will be limited depending on which type of agent is used. 



## System Agents

VirtualCity also supports **system agents** that make the environment more immersive and interactable.

To control how the system agents behave, you can use the `system_agent` function:

```python
import virtualcity

environment.system_agent(
    crowd=True,
    traffic=True,
    visualize=False
)
```
- `crowd` → choose to enable or disable the crowds walking around VirtualCity `Boolean`
- `traffic` → choose to enable or disable vehicle traffic in the city `Boolean`
- `visualize` → choose to visualize the crowd and traffic `Boolean`