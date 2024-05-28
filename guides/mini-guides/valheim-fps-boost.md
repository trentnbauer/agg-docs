# Valheim FPS Boost

## Launch Options

You can add some lines to the launch options in Steam to enable dedicated Fullscreen and additional GPU resources. The game, by default, will run in DirectX Borderless mode.

_I would recommend first trying Vulkan and DirectX borderless variants and see what gives you the most FPS. After that, try the Fullscreen variant and see if that is better or worse. I found that Vulkan Borderless performed best for me (i5 12500, 3060 Ti)_

{% tabs %}
{% tab title="DirectX Renderer" %}
#### Borderless (native)

`-console -gfx-enable-gfx-jobs -gfx-enable-native-gfx-jobs`

#### Exclusive Fullscreen

`-window-mode exclusive -screen-fullscreen -console -gfx-enable-gfx-jobs -gfx-enable-native-gfx-jobs`
{% endtab %}

{% tab title="Vulkan Renderer" %}
#### Borderless (native)

`-console -gfx-enable-gfx-jobs -gfx-enable-native-gfx-jobs -force-vulkan`

#### Exclusive Fullscreen

`-window-mode exclusive -screen-fullscreen -console -gfx-enable-gfx-jobs -gfx-enable-native-gfx-jobs -force-vulkan`
{% endtab %}
{% endtabs %}

### Steam

_This does NOT apply to modpacks launched via Thunderstore_

1. Launch steam and navigate to your library
2. Locate Valheim, right click > properties
3. Select the general tab on the left, then input the launch options

### Xbox Store

1. ???
2. No idea, sorryyyy!

### Thunderstore

1. Launch Thunderstore, select Valheim and open your modpack
2. Select settings on the left
3. Select the Debugging tab
4. Locate Set launch parameters
5. Input the launch options and click update

## Boot file

You can tweak the boot.config file to enable more GPU resources and increase the CPU count to Valheim. Apparently, the boot file can be reset with updates so keep this in mind.

Options to add to your boot file;

{% code title="boot.config" %}
```
scripting-runtime-version=latest
hdr-display-enabled=0
gfx-enable-gfx-jobs=1
gfx-enable-native-gfx-jobs=1
wait-for-native-debugger=0
vr-enabled=0
```
{% endcode %}

#### gc-max-time-slice=???

Update the max-time-slice number to be either your CPU threads (eg if 12 threads, set to 12).

If you are streaming or using another tool while gaming that needs some CPU, like Chrome, I recommend setting it 2 or 4 below your thread count. Eg 12 thread CPU = 8 or 10.

### Steam

1. Launch steam and navigate to your library
2. Locate Valheim, right click > properties
3. Select the "Installed Files" tab on the left
4. Click on Browse and file explorer will open
5. Open the Valheim\_Data folder
6. Open the boot.config file in Notepad, or your text editor of preference
7. Add the content above
8. Update the `gc-max-time-slice=` line per [#gc-max-time-slice](valheim-fps-boost.md#gc-max-time-slice "mention")



Sources:

{% embed url="https://www.pcgamingwiki.com/wiki/Valheim" %}

{% embed url="https://steamcommunity.com/sharedfiles/filedetails/?l=german&id=2390029674" %}

{% embed url="https://www.reddit.com/r/valheim/comments/1ccum0s/better_valheim_fps_with_newer_bootconfig_25_fps/" %}
