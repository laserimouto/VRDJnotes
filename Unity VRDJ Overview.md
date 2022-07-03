# Unity For VRDJ
The basic workflow for using Unity to VRDJ consists of:
* __VirtualMotionCapture (VMC)__ to capture motion data from your VR controller and send it to Unity via OSC
* __EasyVirtualMotionCaptureForUnity (EVMC4U)__ to apply VMC motion data to a model inside of Unity
* __Unity__ to run the VRDJ scene
* __OBS__ to capture the Unity window and sync with DJ audio

This setup is taken from DJ Sharpnel's Techlist as seen in:
- https://www.youtube.com/watch?v=28wExxCaEOI
- https://www.youtube.com/watch?v=I8Ftu5Pp3FQ

### Pros & Cons
Advantages of Unity VRDJ (over VRChat):
* Can run locally / offline. Not reliant on a 3rd-party service 
* Access to all of Unity's functionality. VRChat heavily restricts scripting and only whitelists certain Unity components.
* More performant (\*potentially). You don't need to render a VR view if you don't want, and you aren't running the entire VRC client.

Disadvantages:
* You'll have to implement a lot/most quality of life things yourself
* It's a lot harder to share/publish Unity projects compared to a VRChat world
* No Multiplayer for free

## VirtualMotionCapture (VMC)
Captures motion data from your VR headset, controllers and trackers, then uses it to animate a VRM model. Can also send this motion data via OSC to other programs (which is our use case)
- https://vmc.info/
- https://github.com/sh-akira/VirtualMotionCapture

__Patreon version is required__ to enable OSC motion sending to other programs (Unity, VSeeFace, etc)

The actual model loaded inside VMC doesn't matter, as we only care about receiving tracker data.

### Setting Up VMC
1. Import VRM model
2. Assign controllers/trackers (Setting -> Open Tracker Assignment Settings)
3. Enable OSC motion sending (Setting -> Enable OSC motion sender)
4. Run Calibration

### Related Guides
* [Using Vive Controllers as Trackers in VMC](/Using Vive Controllers as Trackers in VMC.md) - Read this if you plan on strapping Vive wands to your wrist / elsewhere
* [Converting an avatar to VRM format by Emilianavt](https://gist.github.com/emilianavt/51d8399987d67544fdebfe2ebd9a5149) 


## EasyVirtualMotionCaptureForUnity (EVMC4U)
EVMC4U receives OSC motion data (from VMC) and uses it to animate a VRM model inside Unity:
- https://booth.pm/ja/items/1801535
- https://github.com/gpsnmeajp/EasyVirtualMotionCaptureForUnity

Lining up your model with your DJ controller inside a Unity scene can be fiddly, and I find that your avatar's postioning relative to the EVMC4U prefab can change in between runs. I suggest adding hotkeys to shift/rotate your avatar to help with alignment.

### Related Guides
* [EVMC4U](/EVMC4U.md)
* [Converting an avatar to VRM format by Emilianavt](https://gist.github.com/emilianavt/51d8399987d67544fdebfe2ebd9a5149) 
* How-to guide (English): https://github.com/gpsnmeajp/EasyVirtualMotionCaptureForUnity/wiki/How-to-use#how-to-use

The VRM format only supports SpringBones for animating hair, clothes, etc. If you are using a VRChat avatar that has DynamicBones (or PhysBones, but I haven't tested), you can always re-add them to your VRM model after conversion. I find DynamicBones/PhysBones animate much better than VRM SpringBones.

## OBS
Combine game capture from Unity with external audio input. Record/stream output:
- https://obsproject.com/


## Misc Utilities
### Cineswitcher
Allows controlling multiple [Cinemachine](https://docs.unity3d.com/Packages/com.unity.cinemachine@2.3/manual/index.html) cameras via hotkeys
- https://booth.pm/ja/items/1654878
- https://docs.google.com/document/d/1kvJMpgiWevLfodXn3vLYq1kaHW2XJAEdOo0iGaifdKg/edit# (Docs)

The actual script for controlling cameras is very simple, so it can be worth it to just write it yourself. I'd recommend skipping this if plan you plan to setup/script automatic cameras, use Unity's new Input system or extend it in any way.

### Minis
Script to enable MIDI input in Unity (e.g. for Camera hotkeys)
- https://github.com/keijiro/Minis

#### Related Pages
* [Minis](/Minis.md)

### EasyMotionRecorder
Record motion data as a Unity animation. I haven't tested this yet, but it *may* let you record a separate pass if you want to have a dedicated run for in-world VJ/lighting.
- https://github.com/neon-izm/EasyMotionRecorder