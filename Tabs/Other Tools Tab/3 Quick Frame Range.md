[Return to Other Tools Page](/Tabs/Other%20Tools.md)

# Quick Frame Range

<div align="center">

![GH Animation Pro panel](/IMAGES/Quick_Frame_Range.png)

</div>

The **Quick Frame Range** section provides a set of tools for rapidly aligning the scene’s playback range to your current animation, loops, or markers. It also lets you save and restore a preferred frame range so you can safely experiment with different segments without losing your baseline timeline setup.

## Quick Frame Range

**Quick Frame Range** button automatically adjusts the scene’s **Start** and **End** frames to tightly match the animation data on the selected objects or armature. Use it when you import or rough out animation and want the timeline to wrap exactly around the portion that actually contains keyframes, instead of manually hunting for the first and last key.

### Step by Step

- Select the object or armature that contains the main animation you want to work with.
- Open the **Quick Frame Range** section and click **Set Scene Range**.
- The scene’s frame range will snap to the first and last keyframes found on the selected animation, so playback and rendering focus only on the useful part of the timeline.

## Quick Frame Range (Loop)

**Quick Frame Range (Loop)** configures the scene frame range for looped animation work. It uses the keyframe span of the selected object or armature, but trims or adjusts the range so it is more convenient for previewing seamless cycles and quickly looping the timeline while you refine motion.

### Step by Step

- Select the looping asset (for example, a walk cycle armature or looping object animation).
- In **Quick Frame Range**, click **Quick Frame Range (Loop)**.
- The scene frame range is updated to a clean loop segment based on the animation keys, making it easier to preview continuous motion and tune transitions at the loop boundary.

## Loop Between Markers

**Loop Between Markers** uses the currently **selected** timeline markers to define the scene’s **Start** and **End** frames. To quickly set a time range, select any number of markers in the timeline, and the add-on will set the frame range from the earliest selected marker to the latest one, regardless of how many markers lie in between.

### Step by Step

- In the timeline, select at least **two** markers that cover the section you want to isolate.
- Click **Loop Between Markers** in the **Quick Frame Range** section.
- The scene frame range will snap to the outermost selected markers.

# Saved Frame Range Display

Beneath the main buttons, **Quick Frame Range** shows the **Saved Range** that is currently stored for the add-on. This helps you keep track of which frame span will be applied when you use **Reset Frame Range**, so you do not accidentally restore an unexpected segment.

### How It Works

- Whenever you use **Save Current Frame Range**, the panel updates to display the saved start and end frames as `Saved Range: X - Y`.
- This visual indicator lets you quickly compare the saved range with the scene’s current frame range and decide whether you really want to apply it back to the scene.

## Save Current Frame Range

**Save Current Frame Range** stores the scene’s **Start** and **End** frames exactly as they are at the moment you press the button. This defines the baseline range that will be used later by **Reset Frame Range**, so any future reset will jump back to this saved segment instead of whatever you were using before.

### Step by Step

- Adjust the scene **Start** and **End** frames to the range you want to treat as your baseline.
- Click **Save Current Frame Range** in the **Quick Frame Range** section.
- From now on, **Reset Frame Range** will restore the timeline to this saved range, until you save a new one.

## Reset Frame Range

**Reset Frame Range** restores the scene’s **Start** and **End** frames to whatever range was last saved with **Save Current Frame Range**. You never have to edit any files manually: the add-on simply reads the stored values and snaps the scene range back to them when you press the button.

### Step by Step

- First, set the scene **Start** and **End** frames to the range you want to use as your baseline and click **Save Current Frame Range**.
- Later, whenever you want to revert after experimenting with other frame ranges, open **Quick Frame Range** and click **Reset Frame Range**.
- The scene frame range will instantly return to the saved **Start** and **End** values; to change what “reset” returns to, just save a new range with **Save Current Frame Range**.

<div style="margin-top: 24px;">

> **Note:** Combining these tools lets you safely jump between automatically detected ranges (from keys, loops, or markers) and your saved master range, without losing track of the original shot or project settings.

</div>