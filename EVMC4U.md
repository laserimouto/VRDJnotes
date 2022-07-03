# EVMC4U
Allows receiving OSC motion data from VMC and applies it to a VRM model in Unity 
- https://booth.pm/ja/items/1801535
- https://github.com/gpsnmeajp/EasyVirtualMotionCaptureForUnity

How-to guide (English); https://github.com/gpsnmeajp/EasyVirtualMotionCaptureForUnity/wiki/How-to-use#how-to-use

## Setting up EVMC4U in Unity
1. Import ExternalReceiverPack
2. Drag in (or import) VRM model to project
3. Open scene "ExternalReceiverScene"
4. Add VRM prefab to scene hierarchy as a child of the ExternalReceiver prefab
5. In the inspector, make sure the "Model" field of ExternalReceiver prefab is set to the VRM prefab in the scene
6. Play

## Changing avatar's origin in scene
(0,0,0) for the avatar seems to be the middle of your VR playspace, so your avatar will be offset in your scene depending on where your IRL DJ controller sits in your playspace.

You can adjust the position and rotation of the ExternalReceiver prefab to move the model to a better location in your scene.