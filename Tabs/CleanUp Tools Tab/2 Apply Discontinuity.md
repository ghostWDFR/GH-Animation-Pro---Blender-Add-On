[Return to Clean-Up Tools Page](/Tabs/Clean-Up%20Tools.md)

# Apply Discontinuity (Euler)

<div align="center">

![GH Animation Pro panel](/IMAGES/Appy_Discontinuity.png)

</div>

Apply Discontinuity (Euler) scans the selected animated bones or objects for rotation issues and fixes visible flips or pops in their motion. Use it when you see sudden 360° twists after editing keys, baking constraints, or retargeting, and want your rotations to play back smoothly without manually tweaking every F-Curve.

# Step by Step

- Select the armature object and switch to **Pose Mode**.  
  Select either a single bone or multiple bones whose rotation you want to fix.  
  Or stay in **Object Mode** and select the animated object if you want to correct its object-level rotation.
- Open the **GH Animation Pro** panel and expand the **Clean-Up Tools** section.
- Click **Apply Discontinuity (Euler)**.
- Play back the animation to verify that visible rotation flips and pops on the selected bones or object have been smoothed out.


<div style="margin-top: 32px;">

> **Note:** In rare cases this tool may fail to resolve all discontinuities, but in typical workflows it should behave reliably and produce clean rotation results.

</div>