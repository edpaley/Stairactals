
# Stairactals
Stairactals is a procedural staircase generator built with Blender Geometry Nodes. Starting from a simple flight of stairs, the system recursively replaces each step with a smaller staircase of its own, and each of those steps with another, producing a self-similar form that becomes more intricate with every level of depth.

<img width="842" height="792" alt="stairactal" src="https://github.com/user-attachments/assets/3ad7284f-aec5-48ff-bbb2-d936f455ceb2" />


## Usage

This file includes two versions of the generator, each on its own demo object:

| Object | Node group | Depth input |
|---|---|---|
| `Fractal_Stair` | `Fractal_Stair` | **Depth** (integer: whole levels) |
| `Fractal_Stair_Interpolated` | `FractalStairs` | **Depth_Interpolated** (float: smooth blending between levels) |

Select either object and open the **Modifier** tab (wrench icon) to adjust its parameters.

### Parameters

| Parameter | Default | Description |
|---|---|---|
| **Length** | 1.0 | Overall length of the staircase. |
| **Width** | 1.0 | Side-to-side width of the staircase. |
| **Steps** | 5 | Number of steps in each staircase. This applies at every level, so each step becomes a staircase with this many steps. |
| **Depth** | 2 | *(Standard version)* Number of recursion levels. Each level turns every step into a smaller staircase of its own. |
| **Depth_Interpolated** | 0.5 | *(Interpolated version)* Recursion depth as a decimal. Whole numbers match the standard version; values in between blend smoothly into the next level, with the new steps partially formed. For example, 0.5 is halfway between a plain staircase and one level of recursion. |

### Using it in your own project

1. In your project, go to **File → Append**.
2. Select `fractal-stairs.blend`, then open the `NodeTree` folder.
3. Choose `Fractal_Stair` (standard) or `FractalStairs` (interpolated) and click **Append**.
4. Select any object, add a **Geometry Nodes** modifier, and pick the node group from the dropdown.

### Animating depth (interpolated version)

Because **Depth_Interpolated** is a float, it can be keyframed so the staircase continuously unfolds into finer detail:

1. On your starting frame, set **Depth_Interpolated** to `0`, hover over the field, and press **I** to insert a keyframe.
2. Move to a later frame, set it to your target value (e.g. `2`), and press **I** again.
3. Play the animation: each new level of steps grows smoothly out of the one before it.

### Performance

Geometry grows exponentially with depth: every level multiplies the number of steps by the **Steps** value. High combinations (e.g. Steps 10 with Depth 4) can slow down or freeze Blender. Increase Depth one level at a time, and save before trying large values.

### Exporting

To use the result in other software (Unity, Unreal, 3D printing, etc.), select the object and **apply the Geometry Nodes modifier** (modifier dropdown → Apply), then export with **File → Export** (FBX, OBJ, or glTF). Applying makes the geometry permanent, so do it on a copy if you want to keep it editable.

## Requirements

- Blender 5.2 or later

[![CC BY 4.0][cc-by-shield]][cc-by]

[cc-by]: https://creativecommons.org
[cc-by-shield]: https://shields.io
