[Return to Animation Tools Page](/Tabs/Animation%20Tools.md)

<div align="center" style="margin-top: 32px; margin-bottom: 64px;">

![FPS Tweaks](/IMAGES/IK_Lock_Points_Pose_Mode.png)

**IK Lock Points – Pose Mode View**

</div>

<div style="margin-top: 32px; margin-bottom: 64px;">

> **Note:** In the screenshot you see all buttons in this section only because an armature and an empty are selected at the same time. Normally, only the valid buttons for the current context are shown: different buttons appear when an empty is selected versus when an armature is active in Pose Mode, so keep this in mind.

</div>

# 1. Lock IK Position

**Lock IK Position** button let you pin the current position and rotation of a pose bone to a helper empty, driven through its own action and NLA strip. The helper is automatically named after the bone and the frame where the lock is created (for example, `BoneName_Lock_0123`), so you can quickly identify which lock belongs to which bone and frame even in heavy scenes with many IK Lock Points. The same naming is reused for the lock’s Action and its NLA track, keeping all technical layers clearly grouped and easy to navigate. This creates a clean, non-destructive IK “anchor” that you can move independently, while the bone follows via constraints. You can stack multiple locks on the same bone at different frames, freely animate between them, and later bake or clean them when the setup is no longer needed.

<div align="center">

![FPS Tweaks](/IMAGES/GHIK_Lock_Collection.png)

</div>

## Step by Step

- Select an **armature** and enter **Pose Mode**, then choose the pose bone you want to lock.
- Move to the frame where you want to create the lock.
- In the **Animation Tools** tab, open **IK Lock Points** and click **Lock IK Position**.
- The add-on creates a helper empty in the **GH_IK_Lock_Points** collection (with a name that encodes the bone and frame), adds Copy Location/Copy Rotation constraints to the bone, and builds an NLA strip and track that inherit the same naming for consistent organization.
- You can repeat this on other frames or bones to create additional IK Lock Points, then use the baking and cleanup tools to collapse them into regular keyframes when you are ready.

<div align="center">

![IK Lock Points NLA](/IMAGES/IK_Lock_Points_NLA.png)

**Target bone/bones follows IK Lock Point based on NLA tracks**

</div>

<div style="margin-top: 32px; margin-bottom: 64px;">

> **Note:** Until a lock has been baked, you can freely move its NLA strip, adjust Blend In/Out, change its length, and so on – everything updates dynamically. You can also add custom animation to the lock empties themselves to adapt the bones for specific situations, for example making hands appear to hold onto something or grip an object, thus creating interactive behavior.

> **Note:** Keep in mind that the IK Lock Point records the bone’s position on the frame where you create it, but the bone will not be fully locked to the helper empty exactly on that single frame. Because the generated NLA strip uses default **Blend In** and **Blend Out** values of 3 frames, the constraint influence smoothly ramps in and out across a short range, which you should consider when planning and refining your animation around the lock.

</div>

# 2. Bake Selected IK Locks (Bones)

**Bake Selected IK Locks** works from the **selected bones** on the active armature in Pose Mode. It bakes the IK Lock–driven motion for those bones **from all IK Lock Points that affect them** and then removes the corresponding IK Lock helper NLA strips and empties, without touching other parts of the rig that are not driven by those locks.

## Step by Step

- Select the **armature** that uses IK Lock Points and, in **Pose Mode**, select the bones whose IK Lock–driven motion you want to finalize.  
- Click **Bake Selected IK Locks** in the **IK Lock Points** section.  
- The add-on finds all IK Lock NLA strips whose empties constrain those selected bones, bakes the visual motion of these bones over each strip’s frame range into regular keyframes on the armature’s action, and then removes the related IK Lock NLA strips and helper empties, while leaving other IK Locks (that do not influence the selected bones) intact.

<div align="center">

![IK Lock Points NLA Bake](/IMAGES/IK_Lock_Points_NLA_Bake.png)

**IK Lock Point or Points can be baked into ketframes**

</div>

<div style="margin-top: 32px; margin-bottom: 64px;">

> **Note:** Unlike the generic bake tools in **Other Tools**, **Bake Selected IK Locks** works from the currently selected bones: it looks at all IK Lock Points that drive those bones, limits baking to the IK Lock NLA ranges, and then cleans up only the helpers related to those locks. Once baked, edits affect the direct keyframes; if you need IK Lock Points again, create new locks on top of the baked animation.

</div>

<div align="center" style="margin-top: 32px; margin-bottom: 64px;">

![FPS Tweaks](/IMAGES/IK_Lock_Points_Objects_Mode.png)

**IK Lock Points – Object Mode View**

</div>

# 3. Remove All IK Locks

**Remove All IK Locks** button is a one-click cleanup for the entire IK Lock Points system on the current armature. It removes all IK Lock NLA tracks and strips, deletes the helper empties in the **GH_IK_Lock_Points** collection, and strips IK Lock–related constraints from all pose bones, restoring the rig to its original state before any IK Lock Points were added.

## Step by Step

- Select the **armature** whose IK Lock Points you want to remove, and make sure it is in **Pose Mode**.
- In the **Animation Tools** tab, open **IK Lock Points** and click **Remove All IK Locks**.
- The add-on deletes all IK Lock–related NLA tracks and strips on that armature, removes **GHIKLockLocation** and **GHIKLockRotation** constraints from its bones, and then deletes all helper empties in the **GH_IK_Lock_Points** collection (removing the collection itself if it becomes empty).

<div style="margin-top: 32px; margin-bottom: 64px;">

> **Note:** This is a destructive cleanup for the IK Lock Points setup: once removed, the empties, their NLA strips, and their driving actions are gone. Use **Bake All IK Locks** or **Bake Selected IK Lock** first if you want to preserve the IK-driven motion as regular keyframes before wiping the technical helpers.

</div>

# 4. Remove Selected IK Locks

**Remove Selected IK Locks** button lets you surgically delete only specific IK Lock Points instead of wiping the entire system. It works on the currently selected IK Lock empties in the **GH_IK_Lock_Points** collection: for each selected lock, the add-on removes all constraints on any armature bones that target this empty, cleans up the corresponding NLA strips and actions that drive the lock, and then deletes just those empties themselves, leaving other IK Lock Points intact.

## Step by Step

- Switch to **Object Mode** and select one or more IK Lock empties in the **GH_IK_Lock_Points** collection that you want to remove. These empties must be selected as objects; in **Pose Mode** this tool is not available.
- In the **Animation Tools** tab, open **IK Lock Points** and click **Remove Selected IK Locks**.
- The add-on searches all armatures for constraints that target the selected empties, removes those constraints, deletes the NLA strips and actions associated with the selected locks, and then removes only the chosen empties, keeping all other IK Lock Points and their animation intact.

<div style="margin-top: 32px; margin-bottom: 64px;">

> **Note:** Use **Remove Selected IK Locks** when you want to discard a specific lock (or a group of locks) without touching the rest of the IK Lock Points setup. Make sure the empties are selected in **Object Mode**; selecting bones in **Pose Mode** is not enough, and this button will not be shown there.

</div>

# 5. Bake Selected IK Lock (Empty)

**Bake Selected IK Lock** works from the **selected IK Lock empties themselves**. It bakes only the motion driven by the **specific locks you have selected**, for all bones and rigs that reference those empties as constraint targets, and then removes only those particular locks, their NLA strips, actions, and empties, leaving all other IK Lock Points and helpers untouched.

## Step by Step

- Switch to **Object Mode** and select one or more IK Lock empties in the **GH_IK_Lock_Points** collection whose motion you want to finalize; this tool is only available when empties are selected as objects, not in Pose Mode.  
- In the **Animation Tools** tab, open **IK Lock Points** and click **Bake Selected IK Lock**.  
- For each selected lock, the add-on finds every armature and pose bone that uses this empty as a constraint target, locates the NLA strip that plays the lock’s action, bakes only that strip’s visual IK-driven motion into the bones’ current action over the strip’s frame range, and then removes that lock’s constraints, NLA strip, action, and empty, while all other IK Lock Points and their animation remain active.

<div style="margin-top: 32px;">

> **Note:** Functionally, **Bake Selected IK Lock** uses the same visual-IK-to-keyframes approach as the bone-based **Bake Selected IK Locks**, but with a different scope:  
> – **Bake Selected IK Locks (Bones)** starts from the selected bones and bakes all IK Lock Points that drive them.  
> – **Bake Selected IK Lock (Empty)** starts from the explicitly selected empties and bakes only those particular locks, leaving all other IK Lock Points and their helpers intact.  
> In most workflows, the bone-based baker is more convenient for finalizing a whole pose setup; use the empty-based **Bake Selected IK Lock** when you need to surgically finalize or remove specific locks while keeping the rest for further editing.

</div>

