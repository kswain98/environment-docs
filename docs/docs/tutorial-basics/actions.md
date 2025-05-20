---
sidebar_position: 3
---

# Actions

One of the key parts of VirtualCity is the supported **Actions**. which allow the environment to be interactable.


## Execute a action within the environment

To execute a action using a agent, you will need to run the `set_action` function:

```python
import virtualcity

environment.set_action(
    "Agent_0 place object_1 on object_2"
  )
```
Behind the scenes, the action string is converted to the following parameters 
- `agent_index` → the agent chosen to complete the task 
- `task` → the task string converted to a array used by the engine
- `control` → the type of control level `high_level` or `low_level`
- `coordinate` → chosen coordinate for finer-grained control 
- `rotation` → chosen rotation for finer-grained control



## Action List

The following list contains all the supported actions available in VirtualCity:

- `idle` → idle at `location` or  `coordinate`
- `walk` → walk to `object` or `coordinate`
- `run` → run to `object` or `coordinate`
- `grab` → grab a `object`
- `place` → place a `object` on a `object`
- `sit` → sit on a `object`
- `stand` → idle at `location` or `coordinate`
- `open` → open a `object`
- `close` → close a `object`
- `switchon` → switch on a `object`
- `switchoff` → switch off a `object`
- `sleep` → sleep on a `object`
- `drive` → drive a `drivable object`
- `use` → use a `object`
- `drink` → drink a `drinkable object`
- `eat` → eat a `edible object`
- `push` → push a `movable object`
- `pull` → pull a `movable object`
- `talk` → talk to a `agent`
- `clean` → clean a `object`
- `cook` → cook a `object`

