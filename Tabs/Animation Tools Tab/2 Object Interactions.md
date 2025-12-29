[Return to Animation Tools Page](/Tabs/Animation%20Tools.md)

# 1. Attach Objects to Bone

**Attach Objects to Bone** button lets you quickly parent scene elements to a moving target using an animatable **Child Of** constraint driven by its own Action and NLA strip. You can attach meshes, empties, or even whole armatures to another Mesh/Empty, or to a specific pose bone inside a target armature, so any object (or rig) can ride along with another object or bone without baking or destroying existing keyframes. This is ideal for props, helpers, secondary rigs, and other scene elements that need to follow a character, controller, or driver object in a clean, non-destructive way.

## Step by Step

- First, select one or more **source** objects that you want to attach (for example, meshes, empties, or even another armature).
- Then **add the target object to the selection last**, so it becomes the active item:
  - Either pick a Mesh or Empty as the target (object-to-object attachment).
  - Or pick an Armature as the target object, switch it to **Pose Mode**, and activate the pose bone that should drive the attachment (object-to-bone attachment, where the armature object is the target and the bone is used as a subtarget).
- First, make sure the **objects you want to attach are selected first** (these can be armatures, meshes, or empties), and the **target object** (mesh, empty, whole armature or an armature with an active pose bone in Pose Mode) is selected **last** so it becomes the active object.
- In the **Animation Tools** tab, open **Object Interactions** and click **Attach Objects to Bone**.
- For each source object, the add-on:
  - creates a **Child Of** constraint targeting the active object (and its active pose bone as the constraint’s subtarget when applicable),
  - builds a dedicated Action that animates the constraint’s influence over time,
  - and adds an NLA strip on the source object to drive that influence with smooth Blend In/Out values for clean transitions.

<div align="center">

![Object Interactions - Attaching Object to Another Object (Order Correct)](/IMAGES/OI_Object_Attaching.png)

**Object Interactions - Attaching Object to Another Object (Order Correct)**

</div>

<div style="margin-top: 32px; margin-bottom: 64px;">

> **Note:** The last selected object is always treated as the **target**. If it is an armature, it must be in **Pose Mode** with a valid active pose bone, and that bone is used as the constraint’s subtarget while the armature object remains the actual parent; otherwise, the target is a Mesh or Empty. This workflow supports object-to-object, object-to-armature, and object-to-bone-style attachments and remains fully reversible: you can always bake the driven motion into regular keyframes or remove all attachments when they are no longer needed.

</div>

# 2. Remove All Attachments

**Remove All Attachments** button is a global cleanup tool for everything created by **Attach Objects to Bone**. It scans the entire scene for constraints, NLA strips, and Actions that belong to the attachment system (based on their naming), then removes them in one pass. This is useful when you want to revert the scene back to a state without any GH Attach–style relationships, either after baking or if you change your mind about the setup.

## Step by Step

- Make sure any important motion driven by attachments has been baked if you want to keep it, as this tool removes the technical layers behind those links.
- In the **Animation Tools** tab, open **Object Interactions** and click **Remove All Attachments**.
- The add-on:
  - switches to **Object Mode** to ensure safe constraint editing,
  - removes all constraints whose names indicate they were created by the attachment system (such as **GHAttachChildOf**) on every object in the scene,
  - cleans up NLA strips and tracks whose names are associated with attachment Actions,
  - and deletes any now-unused Actions created for these attachments.

<div style="margin-top: 32px; margin-bottom: 64px;">

> **Note:** This is a destructive cleanup for the attachment setup: the constraints, their NLA strips, and helper Actions are permanently removed. Use **Bake Attached Objects** first if you want to convert the attached motion into baked keyframes before wiping the technical layers.

</div>

# 3. Bake Attached Objects

Bake Attached Objects converts the motion of a child object that follows another object or bone via Attach Objects to Bone into regular keyframes and then removes its Child Of constraint and attachment NLA strip. This leaves the child with clean, standalone transform animation that no longer depends on the attachment target.

## Step by Step

- In **Object Mode**, select the **child object** that is attached to another object or bone via **Attach Objects to Bone** (the one that has the Child Of constraint) and make sure it is the **active object**.
- Go to **Animation Tools → Object Interactions** and click **Bake Attached Objects**.
- The add-on finds the attachment NLA strip on this child object, bakes its visual transform over that strip’s frame range into regular keyframes, then removes the matching Child Of constraint and the related NLA strip (deleting the track as well if it becomes empty).

<div style="margin-top: 32px;">

> **Note:** This tool works only on the **attached child object**, not on the parent/target. It operates per object: for the active child object it automatically finds its attachment NLA strip, bakes the driven motion into standard keyframes, and removes the attachment constraint and its driver strip.

</div>