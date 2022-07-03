# Streaming Video (VJ) for VRChat
## Streaming To VRChat
An overview of (public) services you can use to stream videos/VJ into VRChat worlds

### VRCDN
* https://vrcdn.live/
* https://twitter.com/vrcdn
* https://www.patreon.com/vrcdn/

Features:
* Low-latency and server locations cover most users (Australia... ;;)
* Grab a Patreon sub to use it
* Has specific OBS->OBS relay for VJ setups (nice!)
* Guest accounts let other people stream with your account
* Twitch forwarding

### Twitch/Youtube
Just works, but there is a significant delay (30+ seconds from local -> world in Australia)

### TopazChat
* TopazChatPlayer/World prefab: https://booth.pm/ja/items/1752066
* JP README: https://github.com/TopazChat/TopazChat

* Low-latency, *if* you're in or near to Japan, can be rough elsewhere
* Limited to 320kbps audio / 2000kbps video
* No Twitch forwarding built-in

### Custom RTMP Server
* https://github.com/aler9/rtsp-simple-server


## Playing Video In-World
`Allow Untrusted URLs` needs to be enabled by the user for non-Youtube/Vimeo sources

### UdonSyncPlayer
* https://docs.vrchat.com/docs/video-players

Video player that comes with Udon/VRCSDK3. Basic, lets you copypaste a URL, no play/pause/seek/etc.

Use the __AVPro__ flavour of prefab as it support live streams (default does not).

### USharpVideo
* https://github.com/MerlinVR/USharpVideo

Video player built on top of [[USharp]]. Has fancier playback features compared to UdonSyncPlayer

### KineL Video Player
* https://booth.pm/en/items/2758684

Untested