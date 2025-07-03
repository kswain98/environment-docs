---
sidebar_position: 3
---

# Smart Agent

Create and control **intelligent agents** that can navigate, interact with objects, and collaborate to complete tasks in your virtual environments.

## Overview

Agents are AI-powered characters that can:
- Navigate through environments using `walk to` actions
- Interact with objects using `grab`, `put`, `putin`, `open`, and `close` actions
- Collaborate with other agents to complete complex tasks
- Generate and execute action sequences based on goals

## Creating Agents

### Basic Setup

```python
from interface.client import observation, render, set_action, make
from llm import OpenAIBot

# Create an agent
agent = Agent(
    agent_id=0,
    agent_name="Alice",
    api_key="your-api-key",
    api_option="openai",
    model="gpt-4o",
    environment="EscapeRoom1"
)
```

### Agent Configuration

- `agent_id` → unique identifier for the agent
- `agent_name` → human-readable name for the agent
- `api_key` → API key for the LLM provider
- `api_option` → LLM provider: `"openai"`, `"anthropic"`, `"qwen"`, `"deepseek"`
- `model` → specific model to use
- `environment` → environment name

## Allowed Actions

| Action | Description | Format |
|--------|-------------|--------|
| `walk to` | Move to a specific object | `agent_0 walk to object_123` |
| `grab` | Pick up an object | `agent_0 grab object_123` |
| `put` | Place object on surface | `agent_0 put object_123` |
| `putin` | Place object inside container | `agent_0 putin object_123` |
| `open` | Open a container or door | `agent_0 open object_123` |
| `close` | Close a container or door | `agent_0 close object_123` |

## Multi-Agent Coordination

### Creating Multiple Agents

```python
# Configure multiple agents
agent_config = {
    'num_agents': 2,
    'agents': {
        0: {'name': 'Alice', 'role': 'Primary task executor'},
        1: {'name': 'Bob', 'role': 'Support assistant'}
    }
}

# Create agents
agents = {}
for agent_id, config in agent_config['agents'].items():
    agent = Agent(agent_id=agent_id, agent_name=config['name'], ...)
    agents[agent_id] = agent
```

### Collaboration Rules

1. **Task Division**: Agents focus on different areas and objects
2. **Communication**: Agents observe each other's actions and coordinate
3. **Efficiency**: Avoid redundant actions and repetitive behaviors
4. **Goal Sharing**: Work towards common objectives while maintaining individual roles

## Goal-Based Tasks

### Setting Goals

Agents work with goal states defined as tuples, you can either define them yourself in the prompt or let the agent define them itself using a built-in language model orchestrator.

```python
# Relation goals: (subject, relation, target): count
goals = {
    ('keycard', 'on', 'card_reader'): 1,
    ('milk', 'inside', 'refrigerator'): 2
}

# State goals: (object, 'state', state_type): count
goals = {
    ('door', 'state', 'open'): 1,
    ('refrigerator', 'state', 'closed'): 1
}
```

### Goal Types

- **Relation Goals**: Define spatial relationships between objects
  - `'on'`: Object placed on surface
  - `'inside'`: Object placed inside container

- **State Goals**: Define object states
  - `'open'`: Container or door is open
  - `'closed'`: Container or door is closed
  - `'switchon'`: Device is turned on
  - `'switchoff'`: Device is turned off

## Environment Observation

### Getting Environment Data

```python
# Get full environment observation
observation({"type": "full"})

# Read the observation graph
with open('graph.json', 'r') as f:
    data = json.load(f)
environment_objects = data["EscapeRoom1"]
```

### Object Properties

Each object has these properties:
- `id` → unique object identifier
- `sm_name` → object name in the 3D engine
- `sm_transform` → position, rotation, and scale
- `relations` → relationships with other objects
- `sockets` → container capacity
- `states` → current object state

## Complete Example: Escape Room

```python
# Set up environment
environment_name = "EscapeRoom1"
make({"environment": environment_name})

# Create multi-agent system
user_prompt = """I want 2 agents to escape from the room. Find the keycard and use it on the card reader to open the door. The keycard is in one of the containers in the room. The two agents should work together to find the keycard and open the door, while not focus on the same container."""

# Run multi-agent experiment
metrics = run_multi_agent_experiment(
    user_prompt=user_prompt,
    api_key="your-api-key",
    api_option="openai",
    model="gpt-4o",
    environment=environment_name
)
```

## Agent Behavior

### System Prompts

Define agent behavior through system prompts:

```python
ALICE_PROMPT = """You are Alice, the primary AI assistant. You control agent_0 using these actions: walk to, grab, put, putin, open, close.

Rules:
1. Don't repeat "walk to" if already near target
2. Can only hold one object at a time
3. Must grab before putting
4. Open containers before putting things inside
5. Use "put" for 'on' relations and "putin" for 'inside' relations
6. Object IDs must be integers
7. Avoid repeating the same action on the same object multiple times

Respond with only the next action, no explanation needed."""
```

## Performance Tracking

The system tracks agent performance:

```python
metrics = {
    'instruction_correct_rate': 0.85,    # Percentage of valid actions
    'instruction_error_rate': 0.15,      # Percentage of invalid actions  
    'instruction_effective_rate': 0.80,  # Percentage of successful actions
}
```

## Best Practices

1. **Clear Goals**: Define specific, achievable goals for agents
2. **Role Separation**: Give each agent distinct responsibilities
3. **Error Handling**: Implement fallback actions for failed attempts
4. **Monitoring**: Track agent performance and adjust strategies
5. **Coordination**: Ensure agents communicate and avoid conflicts
6. **Efficiency**: Minimize redundant actions and optimize task completion

## Debug Mode

Enable debug output to monitor agent behavior:

```python
agent = Agent(
    agent_id=0,
    agent_name="DebugAgent",
    api_key=api_key,
    debug=True  # Enable debug output
)
```