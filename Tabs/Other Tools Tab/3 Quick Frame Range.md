[Return to Other Tools Page](/Tabs/Other%20Tools.md)

# Quick Frame Range

<div align="center">

![GH Animation Pro panel](/IMAGES/Quick_Frame_Range.png)

</div>

The **Quick Frame Range** section provides a set of tools for rapidly aligning the scene’s playback range to your current animation, loops, or markers. It also lets you save and restore a preferred frame range so you can safely experiment with different segments without losing your baseline timeline setup.

## Set Scene Range

**Set Scene Range** automatically adjusts the scene’s **Start** and **End** frames to tightly match the animation data on the selected objects or armature. Use it when you import or rough out animation and want the timeline to wrap exactly around the portion that actually contains keyframes, instead of manually hunting for the first and last key.

### Step by Step

- Select the object or armature that contains the main animation you want to work with.
- Open the **Quick Frame Range** section and click **Set Scene Range**.
- The scene’s frame range will snap to the first and last keyframes found on the selected animation, so playback and rendering focus only on the useful part of the timeline.

## Set Loop Range

**Set Loop Range** configures the scene frame range for looped animation work. It uses the keyframe span of the selected object or armature, but trims or adjusts the range so it is more convenient for previewing seamless cycles and quickly looping the timeline while you refine motion.

### Step by Step

- Select the looping asset (for example, a walk cycle armature or looping object animation).
- In **Quick Frame Range**, click **Set Loop Range**.
- The scene frame range is updated to a clean loop segment based on the animation keys, making it easier to preview continuous motion and tune transitions at the loop boundary.

## Set Range From Markers

**Set Range From Markers** reads the first and last timeline markers and uses them to define the scene’s **Start** and **End** frames. This is useful when you block out shots or sections using markers (for example, “Shot 01” and “Shot 02”) and want the scene range to follow those editorial boundaries instead of raw keyframe positions.

### Step by Step

- Place at least two markers in the timeline that mark the beginning and end of the segment you care about.
- Select any relevant object (the operator focuses on scene markers, not specific key data).
- Click **Set Range From Markers** in the **Quick Frame Range** section to set the scene range to the span between the outermost markers.

## Saved Frame Range Display

Beneath the main buttons, **Quick Frame Range** shows a **Saved Range** read from `SavedFrameRange.txt` if it exists next to the add-on file. This lets you always see the baseline frame span you saved earlier, even after changing the scene range multiple times while experimenting.

### How It Works

- When `SavedFrameRange.txt` is present and valid, the panel displays the stored start and end frames as `Saved Range: X - Y` with a preview icon.
- If the file is missing or corrupted, the panel displays a helpful message so you know why no saved range is shown.

## Save Current Frame Range

**Save Current Frame Range** writes the current scene **Start** and **End** frames into `SavedFrameRange.txt`, effectively bookmarking your preferred master range. Use it right after you decide on the final shot boundaries or master loop length so you can always come back to those values later.

### Step by Step

- Adjust the scene **Start** and **End** frames to the range you want to preserve.
- Click **Save Current Frame Range** in the **Quick Frame Range** section.
- The add-on stores the numbers in `SavedFrameRange.txt`, and the **Saved Range** display updates to reflect the newly saved values.

## Reset Frame Range From File

**Reset Frame Range From File** restores the scene’s **Start** and **End** frames back to the values previously saved with **Save Current Frame Range**, without requiring any manual editing of `SavedFrameRange.txt`. It is a quick way to revert the timeline after trying different frame ranges with the other Quick Frame tools.

### Step by Step

- Make sure you have used **Save Current Frame Range** at least once to store a baseline range.
- At any time, open **Quick Frame Range** and click **Reset Frame Range From File**.
- The scene frame range automatically returns to the saved **Start** and **End** values, with no need to touch the file yourself.

<div style="margin-top: 24px;">

> **Note:** Combining these tools lets you safely jump between automatically detected ranges (from keys, loops, or markers) and your saved master range, without losing track of the original shot or project settings.

</div>