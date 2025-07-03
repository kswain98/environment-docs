---
sidebar_position: 5
---

# Goal State

Define and track goals for agents to accomplish in your virtual environments.

## What are Goal States?

Goal states define what you want agents to achieve. They specify relationships between objects or states of objects that agents should create or maintain.

## Goal Types

### Relation Goals

Define spatial relationships between objects:

```python
goals = {
    ('keycard', 'on', 'card_reader'): 1,
    ('milk', 'inside', 'refrigerator'): 2,
    ('book', 'on', 'table'): 1
}
```

Format: `(subject, relation, target): count`

### State Goals

Define object states:

```python
goals = {
    ('door', 'state', 'open'): 1,
    ('refrigerator', 'state', 'closed'): 1,
    ('light', 'state', 'switchon'): 1
}
```

Format: `(object, 'state', state_type): count`

## Allowed Relations

| Relation | Description | Example |
|----------|-------------|---------|
| `'on'` | Object placed on surface | `('cup', 'on', 'table')` |
| `'inside'` | Object placed inside container | `('key', 'inside', 'drawer')` |

## Allowed States

| State | Description | Example |
|-------|-------------|---------|
| `'open'` | Container or door is open | `('door', 'state', 'open')` |
| `'closed'` | Container or door is closed | `('box', 'state', 'closed')` |
| `'switchon'` | Device is turned on | `('light', 'state', 'switchon')` |
| `'switchoff'` | Device is turned off | `('tv', 'state', 'switchoff')` |

