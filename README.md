# This is GZDoom fork for browser platform. Emscripten support

cmake options
```
-DHAVE_VULKAN=OFF -DHAVE_GLES2=ON -DDYN_OPENAL=OFF -DBUILD_SHARED_LIBS=OFF -DHAVE_VM_JIT=OFF -DNO_GTK=ON -DDYN_GTK=OFF -DNO_OPENAL=OFF -DDYN_SNDFILE=OFF -DDYN_MPG123=OFF
```

If you need not just midi support build libsndfile.

Also it might require manual gzdoom.js library patching:

```js
        case 0x1025 /* AL_SAMPLE_OFFSET */:
          var offset = AL.sourceTell(src);
          if (offset > 0.0) {
            offset *= src.bufQueue[0].frequency;
          }
          return Math.round(offset); // !here: operation with numbers in js format sometimes leads to values like xxx.99999999998 
                                     // and we don't want write floats into int output
```


# Welcome to GZDoom!

[![Continuous Integration](https://github.com/ZDoom/gzdoom/actions/workflows/continuous_integration.yml/badge.svg)](https://github.com/ZDoom/gzdoom/actions/workflows/continuous_integration.yml)

## GZDoom is a modder-friendly OpenGL and Vulkan source port based on the DOOM engine

Copyright (c) 1998-2025 ZDoom + GZDoom teams, and contributors

Doom Source (c) 1997 id Software, Raven Software, and contributors

Please see license files for individual contributor licenses

Special thanks to Coraline of the EDGE team for allowing us to use her [README.md](https://github.com/3dfxdev/EDGE/blob/master/README.md) as a template for this one.

### Source code licensed under the GPL v3
##### https://www.gnu.org/licenses/quick-guide-gplv3.en.html
---

## How to build GZDoom

To build GZDoom, please see the [wiki](https://zdoom.org/wiki/) and see the "Programmer's Corner" on the bottom-right corner of the page to build for your platform.

# Resources
- https://zdoom.org/ - Home Page
- https://forum.zdoom.org/ - Forum
- https://zdoom.org/wiki/ - Wiki
- https://dsc.gg/zdoom - Discord Server
- https://docs.google.com/spreadsheets/d/1pvwXEgytkor9SClCiDn4j5AH7FedyXS-ocCbsuQIXDU/edit?usp=sharing - Translation sheet (Google Docs)
