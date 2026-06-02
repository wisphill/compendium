---
title: Animator
modified: Jun 01, 2026
---
#unity #avatar #animation
```table-of-contents
```
### I. Model preparation
1. Importing the fbx model.
2. Check the animation clips in that model (Check in the Unity). Tips: In the inspector if that has muscles, it could be a Humanoid animation type.
3. **Creating the prefab from the model**, the prefab is automatically referenced to the imported fbx model. Can re-import the fbx model if there are anything changed or updated
4. By clicking on the **create avatar in the fbx Unity object**, the prefab will be updated as animatable. 
5. **Avatar**: Usually it's **a mapping component** between the **armature of the root model** and the **standard bones of the Unity**
   **Humanoid**: the human bones with 4 legs, the standard of the Unity
   **Generic**: Any kind of bones, there are no rules for this, but still can create an avatar for the Generic Rig based on each use case. 

**Model > Inspector > Animation > Select animation > Change properties:
- Loop time & loop pose
### II. Animator Controller in the Unity
- Type: Asset (By creating new animator asset)
- Desc: It's **an asset, a controller**, presented for a **animation state machine**, handling the transition between multiple states.
- Parameters: Define the inputs as **conditions for each layers, transitions**
- Layers: Combine multiple animations of multiple components. For e.g firing while jumping.
- Sample state machine: `Entry <-> Idle <-> Walking <-> Running` based on the speed

#### Animator object/prefab in the Unity
- Automatically detected by Unity when it's referenced to the animated fbx model.
- Marked with `Animator` in the inspector. The prefab **needs to be controlled by the `Animator controller`** and applied to the model avatar.