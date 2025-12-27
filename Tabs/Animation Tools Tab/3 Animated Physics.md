[Return to Animation Tools Page](/Tabs/Animation%20Tools.md)


# 1. Add Physics Selected


**Add Physics Selected** button adds rigid body physics to all selected mesh objects and sets up a simple animated transition from kinematic to simulated at the current frame. Objects stay controlled by keyframes right before the current frame and then hand off to physics starting on the current frame, so the simulation starts from a clean, predictable pose.

## Step by Step

- In **Object Mode**, select one or more **mesh objects** you want to simulate with rigid body physics.
- In the **Animation Tools** tab, open **Animated Physics** and click **Add Physics Selected**.
- The add-on:
  - adds a **Rigid Body** to each selected mesh that does not already have one,
  - inserts a keyframe with **Kinematic = On** one frame before the current frame,
  - inserts a keyframe with **Kinematic = Off** on the current frame so physics starts from that frame onward.

<div style="margin-top: 32px; margin-bottom: 64px;">

> **Note:** Non-mesh objects and meshes that already have a rigid body are skipped with a warning, so existing physics setups are not overridden by accident. Use this when you want several meshes to begin simulating from the pose at the current frame. The initial velocity and inertia of each object are taken from how it was animated up to that frame, so you can create throws, impacts, or other complex interactions by keyframing motion first and then handing control over to physics.

</div>

# 2. Bake Physics Selected

**Bake Physics Selected** button converts rigid body simulation on selected mesh objects into regular keyframes over a defined frame range. It bakes the visual motion into each object’s action, then removes the rigid body components and their animation curves so the result is stable, non-simulated animation.

## Step by Step

- In **Object Mode**, select the **mesh objects** that already have rigid body physics and whose motion you want to bake.
- In the **Animation Tools** tab, open **Animated Physics** and set **Start Bake Frame** to the frame where you want baking to begin.
- Move the timeline to the frame where you want baking to end (the current frame will be used as the bake end).
- Click **Bake Physics Selected**.
- The add-on:
  - bakes the visual transform of all selected rigid-body meshes from **Start Bake Frame** up to the **current frame** into regular keyframes and removes their rigid body components.

<div style="margin-top: 32px; margin-bottom: 64px;">

> **Note:** Only selected mesh objects with rigid bodies are processed. After baking, the motion is fully keyframed and no longer depends on the rigid body simulation, which is useful for export or when you need deterministic playback. Also keep in mind that Blender’s rigid body cache (Scene → Rigid Body World → Cache) must cover the full frame range you want to bake; if your simulation extends beyond this range, parts of the motion may be baked incorrectly or not at all.

</div>

# 3. Calculate to Current Frame

**Calculate to Current Frame** button forces Blender to evaluate the scene frame by frame from the start frame up to the current frame so that physics and other dependency-based simulations are fully up to date. It does not create keyframes, but makes sure the state at the current frame reflects a continuous simulation from the start.

## Step by Step

- Set the **scene start frame** to where you want simulation calculation to begin (typically frame 1).
- Move the timeline to the frame you want to calculate up to (this becomes the end frame).
- In **Animation Tools → Animated Physics**, click **Calculate to Current Frame**.
- The add-on recalculates physics and related simulations for every frame between the start frame and the current frame so that the state on the current frame is fully up to date.

<div style="margin-top: 32px; margin-bottom: 64px;">

> **Note:** This tool is for refreshing simulation state only; it does not bake or modify keyframes. Use it before previewing or baking when physics appears out of sync after scrubbing or changing settings.

</div>

# 4. Remove Physics

**Remove Physics** button cleans rigid body setups and their animation curves from the active mesh object. It removes the rigid body itself and any keyframes that target rigid body properties, leaving other animation channels intact.

## Step by Step

- In **Object Mode**, select the **mesh object** whose rigid body physics you want to remove and ensure it is the **active object**.
- In **Animation Tools → Animated Physics**, click **Remove Physics**.
- The add-on removes the object’s rigid body setup and any animation that was driving its rigid body properties, leaving all other animation on the object unchanged.

<div style="margin-top: 32px;">

> **Note:** This tool only strips the rigid body and its related animation from the active object, leaving all regular keyframes untouched. Use it when you want an object to stop participating in physics interactions but keep its normal animation as-is.

</div>