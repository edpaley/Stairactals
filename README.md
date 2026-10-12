
# Stairactals
Stairactals is a procedural staircase generator built with Blender Geometry Nodes. Starting from a simple flight of stairs, the system recursively replaces each step with a smaller staircase of its own, and each of those steps with another, producing a self-similar form that becomes more intricate with every level of depth.

<img width="842" height="792" alt="stairactal" src="https://github.com/user-attachments/assets/3ad7284f-aec5-48ff-bbb2-d936f455ceb2" />


## Usage

This file includes two versions of the generator, each on its own demo object:

| Object | Node group | Depth input |
|---|---|---|
| `Fractal_Stair` | `Fractal_Stair` | **Depth** (integer: whole levels) |

Select object and open the **Modifier** tab (wrench icon) to adjust its parameters.

### Parameters

| Parameter | Default | Description |
|---|---|---|
| **Length** | 1.0 | Overall length of the staircase. |
| **Width** | 1.0 | Side-to-side width of the staircase. |
| **Steps** | 5 | Number of steps in each staircase. This applies at every level, so each step becomes a staircase with this many steps. |
| **Depth** | 2 | Number of recursion levels. Each level turns every step into a smaller staircase of its own. |

### Using it in your own project

1. In your project, go to **File → Append**.
2. Select `fractal-stairs.blend`, then open the `NodeTree` folder.
3. Choose `Fractal_Stair` (standard) or `FractalStairs` (interpolated) and click **Append**.
4. Select any object, add a **Geometry Nodes** modifier, and pick the node group from the dropdown.

### Performance

Geometry grows exponentially with depth: every level multiplies the number of steps by the **Steps** value. High combinations (e.g. Steps 10 with Depth 4) can slow down or freeze Blender. Increase Depth one level at a time.

### Exporting

To use the result in other software (Unity, Unreal, 3D printing, etc.), select the object and **apply the Geometry Nodes modifier** (modifier dropdown → Apply), then export with **File → Export** (FBX, OBJ, or glTF). 

## Requirements

- Blender 5.2 or later

[![CC BY 4.0][cc-by-shield]][cc-by]

[cc-by]: https://creativecommons.org
[cc-by-shield]: https://shields.io
