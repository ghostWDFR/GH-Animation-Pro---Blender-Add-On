[Return to Other Tools Page](/Tabs/Other%20Tools.md)

# Baking Tab

<div align="center">

![GH Animation Pro panel](/IMAGES/Baking_Tab.png)

</div>

The **Baking** tab contains two tools that handle keyframe baking in different ways. **Bake Current Frame (Selected)** is designed for safely baking the *current visual pose* into the existing action without breaking NLA or active constraints, while **Bake Animation (Selected)** is a more classic full-range bake with streamlined settings for everyday production use.

# 1. Bake Current Frame (Selected)

<div align="center">

![GH Animation Pro panel](/IMAGES/Bake_Current_Frame.png)

</div>

**Bake Current Frame (Selected)** takes the visually evaluated transform of the selected objects or pose bones on the current frame and writes it as keys into the existing action. It keeps all NLA tracks, constraints, and rig connections intact, so the rest of the animation and setup continue to work as before, only the current pose is committed to keyframes at that frame.

## Step by Step

- Go to the frame whose **visual pose** you want to lock in.
- Select the objects or pose bones you want to bake on this frame.
- In the **Baking** tab, expand **Bake Current Frame (Selected)**.
- Enable which channels to bake: **Location**, **Rotation**, and/or **Scale**.
- Click **Bake Current Frame (Selected)** to key the evaluated transform into the current action without touching NLA, constraints, or parenting setup.

<div style="margin-top: 24px;">

> **Note:** This tool is ideal for quickly “freezing” the current constrained pose into keys while keeping all constraints active and the rig fully non-destructive for the rest of the timeline.

</div>

# 2. Bake Animation (Selected)

<div align="center">

![GH Animation Pro panel](/IMAGES/Bake_Animation.png)

</div>

**Bake Animation (Selected)** performs a full animation bake over a frame range, similar to Blender’s standard Bake Action, but wrapped in a focused panel with the most useful options grouped in one place. You can bake either **Object** or **Pose** data, choose which channels to key, and decide whether to clear constraints, parents, or overwrite the existing action after baking.

## Step by Step

- Set the desired **Start Frame** and **End Frame**, or enable **Use Current Frame** if the add-on provides that option for the end frame.
- Choose what to bake in **Bake Data**: **Pose** for armatures in Pose Mode or **Object** for regular transforms.
- Toggle **Location**, **Rotation**, and **Scale** to control which channels will receive keys.
- Decide whether to enable **Visual Keying**, **Clear Constraints**, **Clear Parents**, and **Overwrite Current Action** depending on whether you want a completely independent baked result or just a keyed copy that still follows the original rig.
- Optionally set a custom **Action Name** if you want the bake to go into a new action instead of modifying the current one.
- Click **Bake Animation (Selected)** to generate keys for the selected objects or bones across the chosen frame range using the evaluated result of all constraints and drivers.

<div style="margin-top: 24px;">

> **Note:** Unlike **Bake Current Frame (Selected)**, this tool is meant for full-range baking and can create self-contained animation data that no longer depends on the original constraints or parents if you enable the corresponding clearing options.

</div>