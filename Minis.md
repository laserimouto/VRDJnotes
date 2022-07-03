# Minis
Enable MIDI input in Unity to use Launchpad Mini for Cineswitcher hotkeys + triggering avatar expressions via BlendShape animations
- https://github.com/keijiro/Minis

Relies on Unity's new [Input System](https://docs.unity3d.com/Packages/com.unity.inputsystem@1.0/manual/QuickStartGuide.html), and **is not compatible with Cineswitcher out of the box**, as this uses legacy Input handling.

## Set up MIDI controller as an input device
1. Add scoped repository + import package
2. Create `PlayerInput` component
3. Create Input Actions
4. Add script handlers for Actions
5. Add script to ensure MIDI devices are discovered on play/startup

Seems like you need to add an `onDeviceChange` callback somewhere, otherwise MIDI devices aren't discovered/active when running the scene:


```
// Source https://github.com/keijiro/Minis/blob/master/Assets/Script/DeviceCallback.cs

using UnityEngine;
using UnityEngine.InputSystem;
using UnityEngine.InputSystem.Layouts;

// DeviceCallback.cs - This script shows how to define a callback to get
// notified on MIDI device additions and removals.

sealed class DeviceCallback : MonoBehaviour
{
    void Start()
    {
        InputSystem.onDeviceChange += (device, change) =>
        {
            var midiDevice = device as Minis.MidiDevice;
            if (midiDevice == null) return;

            Debug.Log(string.Format("{0} ({1}) {2}",
                device.description.product, midiDevice.channel, change));
        };
    }
}
```

## Input System Tutorials
- https://gamedevbeginner.com/input-in-unity-made-easy-complete-guide-to-the-new-system/#input_system
- https://docs.unity3d.com/Packages/com.unity.inputsystem@1.0/manual/Debugging.html