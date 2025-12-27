[Return to Clean-Up Tools Page](/Tabs/Clean-Up%20Tools.md)


# F-Curve Cleanup

<div align="center">

![GH Animation Pro panel](/IMAGES/F_Curve_CleanUp.png)

</div>

**F-Curve Cleanup** simplifies your animation curves while keeping the motion visually intact. It uses a tolerance value (Threshold) to remove redundant keys and rebuild cleaner Bezier curves, making your graph easier to read, edit, and ready for production. You can either clean entire channels at once or focus on a specific segment of selected keys when you only need to tidy up part of the motion.

## Step by Step

- In the **Graph Editor**, select the F-Curves you want to clean and adjust the **Threshold** value in the **F-Curve Cleanup** section to control how aggressively the animation is simplified.

**Full Channel Cleanup (Channel)**

- To clean a **full channel**, either select the entire F-Curve or simply select any keyframe that belongs to that channel, then click **Clean-Up to F-Curves**. The whole curve will be rebuilt into a cleaner version using Bezier keys.

**Partial Cleanup (Selected Keys)**

- To clean **only a specific section**, select at least three keyframes on the desired F-Curve segment and click **Clean-Up Selected Keys**. The selected keys will be regenerated into a smoother, cleaner curve over that range.

<div style="margin-top: 32px;">

> **Note:** For best results, work with very small **Threshold** values. The default is `0.005`, and in most cases you should stay in that range or lower when cleaning animation curves.

</div>