# Personal branch of NVIDIA Quake II RTX
*Warning: OpenAL Soft is now REQUIRED to run the game in OpenAL audio mode, you can download newest version from here: https://github.com/kcat/openal-soft , to install drop the 64 bit .dll as OpenAL32.dll in q2rtxgame.exe folder (Windows releases provide precompiled binary of newest master brach of OpenAL Soft)*

**Changes made:**
 - Added flashlight (can be used via bind x toggle cl_flashlight).
 - Flare gun does not consume ammo (flares also bounce now).
 - Boosted reference path tracing mode params (more frames to accumulate, controlled via pt_accumulation_rendering_framenum).
 - MOTD.txt file support for coop sessions.
 - Re-enabled muzzle flashes (can be disabled via cl_muzzle_flash 0) (highly recommended to use with VSYNC enabled).
 - Support for both Ground Zero and Reckoning expansions via port from Yamagi Quake 2.
 - Custom launcher for easy switching between base game, expansions and mods.
 - Open AL effects extensions ported from Yamagi Quake 2, enabling low pass filter in water and doppler effect scaling with relative object speed. Also including brand new experimental (and very simplistic) sound occlusion, can be toggled via s_occlusion and scaled via s_occlusion_strength (higher values decrease the effect).Reverb is enabled by default, can be disabled via s_reverb 0. Also by default picks preset automatically out of 7 presets based on surrounding size, this function can be disabled via s_reverb_preset_autopick 0. Presets can be set manually via s_reverb_preset (0-113). (Combine with OpenAL soft for best results and HRTF support https://github.com/kcat/openal-soft ). If you're interested in HRTF, i recommend giving this a read: https://shodan.systemshock.org/index.php?topic=8371.0, especially the *Custom HRTF table* section (Personally i'm using ciair-48000.mhr HRTF table).
 - Voice input from default recording device passed into game and processed with same effects as other ingame sounds, controlled via s_voiceinput 0/1 and s_voiceinput_volume.
 - Footsteps sounds for all ground enemies (baseq2 and Ground Zero only at the moment), can be disabled via cl_monsterfootsteps 0.
 - Zaero mod support (courtesy of Yamagi Quake 2 yet again). 
 - Action Quake 2 support (courtesy of Quake 2 DOS: https://bitbucket.org/neozeed/q2dos/src/master/action/)
 - Light sources for laser beams (this can be disabled via cl_laserlights 0).
 - Option to disable obnoxious jumping "HUEH" via cl_jumpsound 0
 - Demo prerendering feature via cl_renderdemo and cl_renderdemo_fps. Playing a demo with cl_renderdemo 1 will essentially "render" a sequence of accumulated frames (according to pt_accumulation_rendering_framenum cvar) at the framerate of cl_renderdemo_fps to your game/screenshots folder (eg baseq2/screenshots) with demoname_framenumber syntax. This sequence of images can then be imported to video editor of your choice to be compiled to a movie. To capture sound you need to do a separate run without demo rendering enabled whilst maintaining same target framerate (so RTX off is recommended and framerate lock via r_maxfps should be used) and record the audio with external software of your choice.



**ORIGINAL DESCRIPTION BELOW**

# Quake II RTX

**Quake II RTX** is NVIDIA's attempt at implementing a fully functional 
version of Id Software's 1997 hit game **Quake II** with RTX path-traced 
global illumination.

**Quake II RTX** builds upon the [Q2VKPT](http://brechpunkt.de/q2vkpt) 
branch of the Quake II open source engine. Q2VKPT was created by former 
NVIDIA intern Christoph Schied, a Ph.D. student at the Karlsruhe Institute 
of Technology in Germany.

Q2VKPT, in turn, builds upon [Q2PRO](https://skuller.net/q2pro/), which is a 
modernized version of the Quake II engine. Consequently, many of the settings 
and console variables that work for Q2PRO also work for Quake II RTX. The 
[client](https://skuller.net/q2pro/nightly/client.html) and 
[server](https://skuller.net/q2pro/nightly/server.html) manuals are particularly useful.

## License

**Quake II RTX** is licensed under the terms of the **GPL v.2** (GNU General Public License).
You can find the entire license in the [license.txt](license.txt) file.

The **Quake II** game data files remain copyrighted and licensed under the
original id Software terms, so you cannot redistribute the pak files from the
original game.

## Features

**Quake II RTX** introduces the following features:
  - Caustics approximation
  - Cylindrical projection mode
  - Dynamic lighting for items such as blinking lights, signs, switches, elevators and moving objects
  - Dynamic real-time "time of day" lighting
  - Flare gun and other high-detail weapons
  - High-quality screenshot mode
  - Improved denoising technology
  - Multi-GPU (SLI) support
  - Multiplayer modes (deathmatch and cooperative)
  - Optional two-bounce indirect illumination
  - Particles, laser beams, and new explosion sprites
  - Physically based materials, including roughness, metallic, emissive, and normal maps
  - Player avatar (casting shadows, visible in reflections)
  - Reflections and refractions on water and glass, reflective chrome and screen surfaces
  - Procedural environments (sky, mountains, clouds that react to lighting; also space)
  - Sunlight with direct and indirect illumination
  - Volumetric lighting (god-rays)

You can download functional builds of the game from [NVIDIA](https://www.geforce.com/quakeiirtx/)
or [Steam](https://store.steampowered.com/).

## Additional Information

  * [Announcement Article](https://www.nvidia.com/en-us/geforce/news/quake-ii-rtx-ray-tracing-vulkan-vkray-geforce-rtx/)
  * [Ray-Tracing Deep Dive](https://www.nvidia.com/en-us/geforce/news/geforce-gtx-dxr-ray-tracing-available-now/)
  * [Launch Trailer Video](https://www.youtube.com/watch?v=unGtBbhaPeU)
  * [Path Tracer Overview Video](https://www.youtube.com/watch?v=BOltWXdV2XY)
  * [GDC 2019 Presentation](https://www.gdcvault.com/play/1026185/)

Also, some source files have comments that explain various parts of the renderer:

  * [asvgf.glsl](src/refresh/vkpt/shader/asvgf.glsl) explains the denoiser filters
  * [checkerboard_interleave.comp](src/refresh/vkpt/shader/checkerboard_interleave.comp) shows how checkerboarded rendering facilitates path tracing on multiple GPUs and helps with water and glass surfaces
  * [path_tracer.h](src/refresh/vkpt/shader/path_tracer.h) gives an overview of the path tracer
  * [tone_mapping_histogram.comp](src/refresh/vkpt/shader/tone_mapping_histogram.comp) explains the tone mapping solution 


## Support and Feedback

  * [GeForce.com Forums](https://forums.geforce.com/default/topic/1119082/geforce-rtx-20-series/quake-ii-rtx-installation-guide/)
  * [Steam Community Hub](https://steamcommunity.com/app/1089130)
  * [GitHub Issue Tracker](https://github.com/NVIDIA/Q2RTX/issues)

## System Requirements

In order to build **Quake II RTX** you will need the following software
installed on your computer (with at least the specified versions or more 
recent ones).

### Operating System

|             | Windows    | Linux     |
|-------------|------------|-----------|
| Min Version | Win 7 x64  | Ubuntu 16 |

Note: only the Windows 10 version has been extensively tested.

Note: distributions that are binary compatible with Ubuntu 16 should work as well.

### Software

|                                                     | Min Version |
|-----------------------------------------------------|-------------|
| NVIDIA driver <br> https://www.geforce.com/drivers  | 430         |
| git <br> https://git-scm.com/downloads              | 2.15        |
| CMake <br> https://cmake.org/download/              | 3.8         |
| Vulkan SDK <br> https://www.lunarg.com/vulkan-sdk/  | 1.1.92      |

## Submodules

* [zlib](https://github.com/madler/zlib)
* [curl](https://github.com/curl/curl)
* [SDL2](https://github.com/spurious/SDL-mirror)
* [stb](https://github.com/nothings/stb)

## Build Instructions

  1. Clone the repository and its submodules from git :

     ```git clone --recursive https://github.com/NVIDIA/Q2RTX.git ```

  2. Create a build folder named `build` under the repository root (`q2rtx/build`)     

     Note: this is required by the shader build rules.

  3. Copy (or create a symbolic link) to the game assets folder (`q2rtx/baseq2`) 

     Note: the asset packages from the binary build of Quake II RTX are required for the engine to run.
     Specifically, the `blue_noise.pkz` and `q2rtx_media.pkz` files or their extracted contents.

  4. Configure CMake with either the GUI or the command line and point the build at the `build` folder
     created in step 2.

     **Note**: only 64-bit builds are supported, so make sure to select a 64-bit generator during the initial configuration of CMake.

  5. Build with Visual Studio on Windows, make on Linux, or the CMake command
     line:

     ```cmake --build . ```

## Music Playback Support

Quake II RTX supports music playback from OGG files, if they can be located. To enable music playback, copy the CD tracks into a `music` folder either next to the executable, or inside the game directory, such as `baseq2/music`. The files should use one of these two naming schemes:
  - `music/02.ogg` for music copied directly from a game CD;
  - `music/Track02.ogg` for music from the version of Quake II downloaded from [GOG](https://www.gog.com/game/quake_ii_quad_damage).

In the game, music playback is enabled when console variable `ogg_enable` is set to 1. Music volume is controlled by console varaible `ogg_volume`. Playback controls, such as selecting the track or putting it on pause, are available through the `ogg` command.

Music playback support is using code adapted from the [Yamagi Quake 2](https://www.yamagi.org/quake2/) engine.

## MIDI Controller Support

The Quake II console can be remote operated through a UDP connection, which
allows users to control in-game effects from input peripherals such as MIDI controllers. This is 
useful for tuning various graphics parameters such as position of the sun, intensities of lights, 
material parameters, filter settings, etc.

You can find a compatible MIDI controller driver [here](https://github.com/NVIDIA/korgi)

To enable remote access to your Quake II RTX client, you will need to set the following 
console variables _before_ starting the game, i.e. in the config file or through the command line:
```
 rcon_password "<password>"
 backdoor "1"
```

Note: the password set here should match the password specified in the korgi configuration file.

Note 2: enabling the rcon backdoor allows other people to issue console commands to your game from 
other computers, so choose a good password.
