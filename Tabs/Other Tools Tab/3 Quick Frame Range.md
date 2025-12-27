[Return to Other Tools Page](/Tabs/Other%20Tools.md)

# Quick Frame Range Tab

<div align="center">

![GH Animation Pro panel](/IMAGES/Quick_Frame_Range.png)

</div>

The **Quick Frame Range** section provides a set of tools for rapidly aligning the scene’s playback range to your current animation, loops, or markers. It also lets you save and restore a preferred frame range so you can safely experiment with different segments without losing your baseline timeline setup.

<div style="margin-top: 64px;"></div>

# 1. Quick Frame Range

**Quick Frame Range** button automatically adjusts the scene’s **Start** and **End** frames to tightly match the animation data on the active object or armature. It scans the keyframes in the object’s current Action, finds the very first and very last key, and snaps the scene frame range to that span so the timeline wraps exactly around the portion that actually contains animation, instead of wasting space on empty frames.

### Step by Step

- Select the object or armature whose animation you want to frame around. Make sure it has an active Action with keyframes.
- Open the **Quick Frame Range** section and click **Quick Frame Range**.
- The add-on looks through all F-Curves in the active Action, finds the minimum and maximum keyframe times, and sets the scene’s **Start** and **End** frames to those values, so playback and rendering focus only on the animated segment.

<div style="margin-top: 64px;"></div>

# 2. Quick Frame Range (Loop)

**Quick Frame Range (Loop)** is a loop-friendly variant of the same tool. It uses the keyframe span of the active object or armature’s current Action, but deliberately shortens the range by one frame at the end: the scene **Start** frame is set to the first key, and the **End** frame is set to the last key minus 1. This prevents the first and last poses from playing back twice in a row, which helps avoid visible stutters when the timeline loops.

### Step by Step

- Select the looping asset (for example, a walk cycle armature or any object with a cyclic Action) whose loop length you want to preview. The loop duration is taken directly from the earliest and latest keyframes in this object’s active Action.
- In the **Quick Frame Range** section, click **Quick Frame Range (Loop)**.
- The add-on gathers all keyframe times from the active Action, sets the scene’s **Start** frame to the earliest key and the **End** frame to one frame before the latest key, giving you a clean loop window that plays seamlessly without repeating the same frame at the boundary.

<div style="margin-top: 64px;"></div>

# 3 Loop Between Markers

**Loop Between Markers** uses the currently **selected** timeline markers to define the scene’s **Start** and **End** frames. To quickly set a time range, select any number of markers in the timeline, and the add-on will set the frame range from the earliest selected marker to the latest one, regardless of how many markers lie in between.

### Step by Step

- In the timeline, select at least **two** markers that cover the section you want to isolate.
- Click **Loop Between Markers** in the **Quick Frame Range** section.
- The scene frame range will snap to the outermost selected markers.

<div style="margin-top: 64px;"></div>

# 4 Saved Frame Range Display

Beneath the main buttons, **Quick Frame Range** shows the **Saved Range** that is currently stored for the add-on. This helps you keep track of which frame span will be applied when you use **Reset Frame Range**, so you do not accidentally restore an unexpected segment.

### How It Works

- Whenever you use **Save Current Frame Range**, the panel updates to display the saved start and end frames as `Saved Range: X - Y`.
- This visual indicator lets you quickly compare the saved range with the scene’s current frame range and decide whether you really want to apply it back to the scene.

<div style="margin-top: 64px;"></div>

# 5 Save Current Frame Range

**Save Current Frame Range** stores the scene’s **Start** and **End** frames exactly as they are at the moment you press the button. This defines the baseline range that will be used later by **Reset Frame Range**, so any future reset will jump back to this saved segment instead of whatever you were using before.

### Step by Step

- Adjust the scene **Start** and **End** frames to the range you want to treat as your baseline.
- Click **Save Current Frame Range** in the **Quick Frame Range** section.
- From now on, **Reset Frame Range** will restore the timeline to this saved range, until you save a new one.

<div style="margin-top: 64px;"></div>

# 6 Reset Frame Range

**Reset Frame Range** restores the scene’s **Start** and **End** frames to whatever range was last saved with **Save Current Frame Range**. You never have to edit any files manually: the add-on simply reads the stored values and snaps the scene range back to them when you press the button.

### Step by Step

- First, set the scene **Start** and **End** frames to the range you want to use as your baseline and click **Save Current Frame Range**.
- Later, whenever you want to revert after experimenting with other frame ranges, open **Quick Frame Range** and click **Reset Frame Range**.
- The scene frame range will instantly return to the saved **Start** and **End** values; to change what “reset” returns to, just save a new range with **Save Current Frame Range**.

<div style="margin-top: 32px;">

> **Note:** Combining these tools lets you safely jump between automatically detected ranges (from keys, loops, or markers) and your saved master range, without losing track of the original shot or project settings.

</div>