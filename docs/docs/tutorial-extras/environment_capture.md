---
sidebar_position: 4
---

# Environment Capture

Capture information about the environment of your Virtual Env environment in your project.

## Capture Screenshots

Render the environment and capture visual data:

```python
from interface.client import render

render_config = {
    "render_pipeline": 'raytracing',
    "camera_index": [0],
    "image_width": [1920],
    "image_height": [1080],
    "fps": [60]
}

render(render_config)
```

## Get Environment Data

Capture the environment structure as JSON:

```python
from interface.client import observation

# Get full environment observation
observation({"type": "full"})

# Read the data
with open('graph.json', 'r') as f:
    data = json.load(f)
```

## Render Configuration Options

| Option | Description | Values |
|--------|-------------|--------|
| `render_pipeline` | Rendering method | `raytracing`, `segmentation_instance`, `segmentation_class`, `optical_flow`, `depth` |
| `camera_index` | Camera to use | `[0]`, `[1]`, etc. |
| `image_width` | Width in pixels | `[1920]`, `[1080]`, etc. |
| `image_height` | Height in pixels | `[1080]`, `[720]`, etc. |
| `fps` | Frames per second | `[60]`, `[30]`, etc. |
| `fov` | Field of view | `[90]`, `[60]`, etc. |

## Observation Types

Choose what information to capture:

```python
# Complete environment graph
observation({"type": "full"})

# Limited observation radius
observation({"type": "partial"})

```

## Environment Data Structure

The captured data contains:

```json
{
  "id": 1,
  "sm_name": "BP_Table",
  "sm_transform": ["X=0.000 Y=0.000 Z=0.000"],
  "relations": ["BP_Table on floor"],
  "sockets": [0],
  "states": ["None"]
}
```

- `id` → unique object identifier
- `sm_name` → object name in 3D engine
- `sm_transform` → position, rotation, scale
- `relations` → relationships with other objects
- `sockets` → container capacity
- `states` → current object state

## Quick Start

```python
# 1. Set up environment
make({"environment": "apartment"})

# 2. Capture screenshot
render({"render_pipeline": 'raytracing', "camera_index": [0]})

# 3. Get environment data
observation({"type": "full"})
```

## Use Cases

- **Training Data**: Capture images for machine learning
- **Documentation**: Create visual environment docs
- **Analysis**: Study object relationships
- **Debugging**: Visualize environment state
- **Agents**: Provide visual input to AI agents
