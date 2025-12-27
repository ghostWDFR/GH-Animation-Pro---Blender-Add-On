[Return to Clean-Up Tools Page](/Tabs/Clean-Up%20Tools.md)

# Clean-Up NLA (Selected)

Clean-Up NLA (Selected) removes helper NLA tracks and constraints from the selected animated objects or pose bones, without touching the main animation you want to keep. Use it after baking IK Locks or attachment setups to strip away temporary drivers, constraints, and support layers, so your rig stays clean and easy to manage for further polishing or export. Constraints and modifiers that were not created by the add-on are left untouched, so your custom rig logic and manually added setups remain safe.

## Step by Step

- Select the bone or object that has one or more empties from the **GH_IK_Lock_Points** collection attached to it.
- Click **Clean-Up NLA (Selected)**.
- Done. Any NLA tracks, empties, and related constraints created by **GH Animation Pro** and linked to those locks will be removed, while unrelated constraints that are not part of the add-on remain untouched.

<div style="margin-top: 24px;">

> **Note:** This cleanup only targets helper NLA tracks, empties, and constraints created by **GH Animation Pro**. Any custom constraints or rig logic you added manually will remain untouched.

</div>