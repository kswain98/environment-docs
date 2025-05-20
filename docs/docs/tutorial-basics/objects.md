---
sidebar_position: 4
---

# Objects

VirtualCity is filled with **interactable objects**. Each object can be interacted using both low-level and high-level control.

Each object has a set of `properties` such as:
- `id` → the unique id given to the object as a way to identify within the environment 
- `sm_name` → the object name that is assigned to it by the 3D engine
- `sm_transform` → the coordinate, rotation, and scale of the of the object
- `relations` → the relation of the object with other objects within the environment
- `sockets` → the amount of "containers" within the object
- `states` → the state of the object

To view all the properties, available actions, and visual meshes of the interactable objects within VirtualCity, please visit this → **[link](http://visiongpu24.csail.mit.edu:5000/home)**.


## Object Relations
The following list contains all the relations a interactble object has in VirtualCity:

- On top
- Under
- Above
- Supported
- Inside
- Contains
- Hanging

`Note`: The relations left, right, in-front, and behind are supported but only determined depending on the agent's perspective


## Object States
The following list contains all the states a interactble object has in VirtualCity:

- Grabbed
- Occupied
- On
- Off
- Dirty
- Broken
- Full
- Empty
- Used
