***

## Phantom Process Killer

**NOTICE:**

**Termux may be unstable on Android 12+.** Android OS will kill any (phantom) processes greater than 32 (limit is for all apps combined) and also kill any processes using excessive CPU. You may get `[Process completed (signal 9) - press Enter]` message in the terminal without actually exiting the shell process yourself. Check the related issue [#2366](https://github.com/termux/termux-app/issues/2366), [issue tracker](https://issuetracker.google.com/u/1/issues/205156966), [gist with details](https://gist.github.com/agnostic-apollo/dc7e47991c512755ff26bd2d31e72ca8) and [this TLDR comment](https://github.com/termux/termux-app/issues/2366#issuecomment-1009269410) on how to disable trimming of phantom processes.

#### Deactivation Instructions (ADB):

- On an ADB console, paste the following commands on the following order:

```
adb shell "/system/bin/device_config set_sync_disabled_for_tests persistent"
```
```
adb shell "/system/bin/device_config put activity_manager max_phantom_processes 2147483647"
```
```
adb shell settings put global settings_enable_monitor_phantom_procs false
```
- If it doesn't work on your phone,Reboot your phone

#### Reboot Phone
```
adb reboot
```
#### You Can Deative with Termux
```
pkg up -y;pkg i -y android-tools
```
- After installing the package,you must open Developer Options in order to use wireless ADB with Termux

- Go to Settings, About Phone & Touch build-number for servial times.

- On Xiaomi Phones, Touch MIUI version servial times.

- After Opening Developer Options,Open wireless debugging & Split Screen.

- Then,Open Termux & Pair Device with paring code.(It doesn't work On Android 14,so use Computer Or Some Tools like ADB Tools)

- Write This ADB Command in termux

#### This is Example,use your host
```
adb connect 192.168.100.2:41538
```
## Example

![](https://raw.githubusercontent.com/atamshkai/Phantom-Process-Killer/main/Example.jpg)

#### Deactivation Instructions (ROOT):

- On Termux (or any Terminal Emulator), paste the following commands on the following order:

```
su -c /system/bin/device_config set_sync_disabled_for_tests persistent
```
```
su -c /system/bin/device_config put activity_manager max_phantom_processes 2147483647
```
```
su -c setprop persist.sys.fflag.override.settings_enable_monitor_phantom_procs false
```

- If it doesn't work on your phone,reboot your phone.

```
su -c reboot
```

#### Experimental Method (MAGISK)

- On a Rooted phone with Magisk installed, flash the following module:

  [Download](https://github.com/atamshkai/Phantom-Process-Killer/raw/main/PhantomProcessRetainer-main.zip) 

- After that, `PhantomProcessKiller' might be deactivated on every device boot.

#### Check if PhantomProcessKiller was Disabled (ROOT):
```
su -c /system/bin/dumpsys activity settings | grep max_phantom_processes
```
```
su -c /system/bin/device_config get activity_manager max_phantom_processes
```
- Both commands above should return `2147483647`

```
su -c getprop persist.sys.fflag.override.settings_enable_monitor_phantom_procs
```
- It should return "false"

***

### To Wait

After restarting , your phone may be hot for a while.

Wait it to normal state.

### Stop Auto Lauch Applications

  [Telegram Link](https://t.me/c/1731442555/346) 
