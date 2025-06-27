# Audio

On a fresh install of Arch, there doesn't appear to be any audio happening. I had to set something up in Debian before, so this wasn't a surprise. EndeavourOS uses Pipewire, so I'll look into that.

## Drivers

The default Linux kernel component appears to be ALSA (Advanced Linux Sound Architecture).

## Frameworks

Utility that captures playback for audio, video, etc, and uses drivers like ALSA to send signals out to output devices like speakers and headphones. Pipewire is one such framework.

## Pipewire install and config

Pipewire packages I've installed:
- pipewire
  - exposes streams, output devices, etc as nodes 
- wireplumber
  - session manager: decides which streams should be connected to which output devices
- pipewire-audio (uninstalled)
  - audio server
- pipewire-alsa (uninstalled)
- pipewire-pulse (uninstalled)
- alsa-utils
  - provides alsamixer, among other things

So far sound is still not working. I suspect it's because a default sink and source are not set. The output of `pactl info` shows both as "auto_null" and "auto_null.monitor" respectively.

Note: Some of the above services may not be essential to getting basic audio playback working. Consider pruning back once things work.

SOLVED!
It appears I needed the `sof-firmware` package. Now `/proc/asound/cards` is populated with something. I think that my Intel sound card just didn't have the necessary firmware or driver. 

In the output of `lspci -v | grep -A7 -i audio` that my Intel audio device uses a kernel driver prefixed with `sof-audio`, so that indicates to me that it needed something that the `sof-firmware` provided.
