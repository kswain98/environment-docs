---
sidebar_position: 1
---

# Environments

Initialize **procedurally generated indoor and outdoor environments** to create your own unique virtual environment that can be explored and interacted with:

## Create your first Environment

To create a interactable environmemnt, you will need to run the `make` function:

```python
import virtualcity

environment.make(
    environment="apartment",
    num_env=[1],
    seed=[-1]
)
```

- `environment` → the type of environment that will be generated `city`, `apartment`, `convenience store`, `office`, `bank`, `subway station`
- `num_env` → number of environments for parallelism `[int]`
- `seed` → seed value used for replicating the procedeurally generated environment `[int]`

## Render the Environment

To render the environment that you just created, you will need to run the `render` function:

```python
import virtualcity

environment.render(
    camera_index=[-1],
    image_synthesis="raytracing",
    image_width=[2160],
    image_height=[1440],
    fps=60,
)
```

- `camera_index` → select the camera index used to render the environment `[-1]`
- `image_synthesis` → select the type of rendering is used `raytracing`, `segmentation_instance`, `segmentation_class`, `optical_flow`, `depth`
- `image_width` → select the width resolution in term of pixel size `[int]`
- `image_height` → select the height resolution in term of pixel size `[int]`
- `image_height` → select the frames per second target during rendering`[int]`

## Observe the Environment as a JSON Graph

Sometimes rendering the environment is not needed, especially when using the environment to train a agent that does not require visual inference. If you are only interested in observing the environment programatically as a JSON graph, you can run the `observation` function:

```python
import virtualcity

environment.observation(
    observation_type="full",
    radius=[-1]
)
```

- `observation_type` → select the type of observation `partial`, `full`, `visual`
- `radius` → select the radius of the observation that the graph contains `[int]`

The graph contains all the `objects`, `agents`, `cameras` within observation. Each object has a set of `properties` such as:
- `id` → the unique id given to the object as a way to identify within the environment 
- `sm_name` → the object name that is assigned to it by the 3D engine
- `sm_transform` → the coordinate, rotation, and scale of the of the object
- `relations` → the relation of the object with other objects within the environment
- `sockets` → the amount of "containers" within the object
- `states` → the state of the object

```json title="graph.json"
{
  Apartment_0: [
    {
      "id": 1,
      "sm_name": "SM_Football",
      "sm_transform": [
        "X=0.000 Y=0.000 Z=0.000",
        "P=0.000000 Y=0.000000 R=0.000000",
        "X=1.000 Y=1.000 Z=1.000"
      ],
      "relations": [
        "Supported by floor"        
      ],
      "sockets": [
        0
      ],
      "states": [
        "None"
      ]
    }
  ]
}
```