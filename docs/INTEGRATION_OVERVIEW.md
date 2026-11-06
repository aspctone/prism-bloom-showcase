# Integration overview

Prism Bloom is a Unity uGUI presentation for a reward your game has already selected. It uses one prefab and a separate Sprite slot. The included demo has a configured Canvas. The notes below describe use on your own Canvas once you have an authorized package copy.

1. In a project with **Unity UI** (`com.unity.ugui`), place the Prism Bloom prefab under a screen-space Canvas. A square 244 × 244 RectTransform is the documented starting size.
2. On **Prism Bloom Player**, choose a reward preset or assign your Sprite in **Reward Sprite**. Import transparent artwork as a Unity Sprite. Clear the field to use the baked Helion Core artwork.
3. Call the player methods from your UI or game code. If you connect uGUI buttons, use an EventSystem and a compatible UI input module. A `void` wrapper can call `TryClaim()` for a Button event.

| Method or event | Behavior |
| --- | --- |
| `PlayOpen()` | Starts OPEN from the closed pose. A repeat call restarts the reveal. |
| `Opened` | Fires when the player reaches its looping IDLE state. |
| `TryClaim()` | Accepts a claim in IDLE and returns `true`. Other states return `false`. |
| `Claimed` | Fires when the accepted claim animation reaches the final pose. Reset or restart can interrupt that animation. |
| `ResetToClosed()` | Returns the player to the closed pose and keeps the Sprite selection. |
| `SetRewardSprite(Sprite)` | Changes the reward without restarting the current playback. Passing `null` restores the baked fallback. |

Treat the events as presentation signals. Keep reward grants, inventory state, and input eligibility in your game logic.

Verification covers Windows x64, Unity 6000.3.28f1, uGUI 2.0.0, and Gamma color space, using Screen Space - Overlay and Screen Space - Camera. URP, HDRP, Android, mobile GPU, World Space, and other Unity versions and platforms remain unverified. The player is intended for a Unity Sprite, with Blender and After Effects used during authoring.
