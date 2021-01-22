---
title: "Debugging Unity Android Apps"
layout: post
date: 2018-07-23
---
This is pretty much a repost/summary of a [StackOverflow post](https://stackoverflow.com/questions/42392522/android-device-doesnt-show-up-as-target-of-unity3d-debugging), as it took me a long while to find this information; hopefully Google will do its magic and surface this for future generations.

I had a need to debug a Unity game on an Android device. The build running on the device was a *Development* build with debugging enabled etc etc. For reasons I had neither time nor inclination to investigate, Visual Studio was not discovering the device and it was not showing in the *Attach Unity Debugger* list, despite the device being on the same Wifi network, **and physically attached by USB cable**. I knew the IP address of the device, but not the port the debugger process was listening on, which apparently changes with each launch.

To summarise the [StackOverflow post](https://stackoverflow.com/questions/42392522/android-device-doesnt-show-up-as-target-of-unity3d-debugging), you want to get hold of the ADB logcat output for your game. I did (something like):

```
adb logcat -c
adb logcat > out.txt
(launch game on device)
(wait some period of time)
(CTRL + C)
```

...which will dump the logcat output to a file called out.txt . If you now search for `monoOptions` in the file you should see a line like:

```
Using monoOptions --debugger-agent=transport=dt_socket,embedding=1,defer=y,address=0.0.0.0:56785
```

If you add the device's IP address with the port from above to the Visual Studio *Attach Unity Debugger* window, it should now connect, obey breakpoints and the like!
