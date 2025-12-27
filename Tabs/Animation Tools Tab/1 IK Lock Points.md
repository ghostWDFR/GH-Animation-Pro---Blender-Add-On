[Return to Animation Tools Page](/Tabs/Animation%20Tools.md)

# 1. Lock IK Position

**Lock IK Position** button let you pin the current position and rotation of a pose bone to a helper empty, driven through its own action and NLA strip. The helper is automatically named after the bone and the frame where the lock is created (for example, `BoneName_Lock_0123`), so you can quickly identify which lock belongs to which bone and frame even in heavy scenes with many IK Lock Points. The same naming is reused for the lock’s Action and its NLA track, keeping all technical layers clearly grouped and easy to navigate. This creates a clean, non-destructive IK “anchor” that you can move independently, while the bone follows via constraints. You can stack multiple locks on the same bone at different frames, freely animate between them, and later bake or clean them when the setup is no longer needed.

## Step by Step

- Select an **armature** and enter **Pose Mode**, then choose the pose bone you want to lock.
- Move to the frame where you want to create the lock.
- In the **Animation Tools** tab, open **IK Lock Points** and click **Lock IK Position**.
- The add-on creates a helper empty in the **GH_IK_Lock_Points** collection (with a name that encodes the bone and frame), adds Copy Location/Copy Rotation constraints to the bone, and builds an NLA strip and track that inherit the same naming for consistent organization.
- You can repeat this on other frames or bones to create additional IK Lock Points, then use the baking and cleanup tools to collapse them into regular keyframes when you are ready.

<div style="margin-top: 32px; margin-bottom: 64px;">

> **Note:** Keep in mind that the IK Lock Point records the bone’s position on the frame where you create it, but the bone will not be fully locked to the helper empty exactly on that single frame. Because the generated NLA strip uses default **Blend In** and **Blend Out** values of 3 frames, the constraint influence smoothly ramps in and out across a short range, which you should consider when planning and refining your animation around the lock.

</div>

# 2. Bake All IK Locks

**Bake All IK Locks** button is a dedicated baker for **IK Lock Points**, not a general-purpose bake for any animation. It looks for NLA strips that belong to IK Locks on the selected rig, bakes only the visible, constraint-driven motion of bones that actually depend on those locks (within the ranges of their IK Lock NLA strips), and then removes all IK Lock–related helper NLA strips and empties. This leaves you with a clean, lightweight rig that no longer depends on the temporary IK Lock Points setup, without touching unrelated animation or bones that are not driven by IK Locks.

## Step by Step

- Select the **armature** that uses IK Lock Points and, in **Pose Mode**, select the bones whose IK Lock–driven motion you want to finalize.
- Click **Bake All IK Locks** in the **IK Lock Points** section.
- The add-on finds NLA strips that belong to IK Locks and bakes only the IK Lock ranges for the selected bones that are actually constrained by IK Lock empties, writing that motion into regular keyframes on the armature’s action.
- After baking, the IK Lock NLA strips and their helper empties are automatically removed (along with their tracks if they become empty), leaving you with clean keyframes that no longer depend on the IK Lock Points system.

<div style="margin-top: 32px; margin-bottom: 64px;">

> **Note:** Unlike the generic bake tools in **Other Tools**, **Bake All IK Locks** understands the IK Lock Points structure: it limits baking to IK Lock NLA ranges, only affects bones driven by IK Locks, and performs full cleanup of all related helpers in one step. Once baked, edits affect the direct keyframes; if you need IK Lock Points again, create new locks on top of the baked animation.

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

# 5. Bake Selected IK Lock

**Bake Selected IK Lock** button is a precise baker for one or more chosen IK Lock Points. It works from the currently selected IK Lock empties in the **GH_IK_Lock_Points** collection: for each selected lock, the add-on finds all armatures and bones constrained to that empty, bakes their IK-driven motion only over that lock’s NLA strip range into regular keyframes on the armature’s current action, and then removes the corresponding constraints, NLA strips, actions, and empties for those locks while leaving all other IK Lock Points and helpers untouched.

## Step by Step

- Switch to **Object Mode** and select one or more IK Lock empties in the **GH_IK_Lock_Points** collection whose motion you want to finalize. These empties must be selected as objects; in **Pose Mode** this tool is not available and the button will not be shown.
- In the **Animation Tools** tab, open **IK Lock Points** and click **Bake Selected IK Lock**.
- For each selected lock, the add-on:
  - finds all armatures and pose bones that use this empty as a constraint target,
  - locates the NLA strip that plays the lock’s action and bakes the visual motion of those bones only over that strip’s frame range into their current action,
  - then removes the lock’s constraints, NLA strips, action, and the empty itself, leaving the baked motion as regular keyframes while other IK Lock Points and their animation remain active.

<div style="margin-top: 32px;">

> **Note:** Functionally, **Bake Selected IK Lock** uses the same idea as **Bake All IK Locks** (visual IK → keyframes over each lock’s NLA range), but with a different scope:  
> – **Bake All IK Locks** operates on the active armature, baking and cleaning *all* of its IK Lock Points and then removing all IK Lock empties and the collection.  
> – **Bake Selected IK Lock** operates only on the explicitly selected empties, baking and cleaning just those locks and leaving the rest of the IK Lock system intact.  
> In most workflows, **Bake All IK Locks** is sufficient and faster to use; reach for **Bake Selected IK Lock** when you need to finalize or remove specific locks while keeping others for further editing.

</div>

