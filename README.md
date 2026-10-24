# mam_engine
A custom graphics engine developed as a final-year university project by a team of three developers. The engine was designed with a modular architecture and supports both OpenGL and Vulkan rendering backends.

# My Contributions
Audio System
Designed and implemented the engine’s full audio system on top of OpenAL. Built multi-format loaders for WAV (custom RIFF/fmt/data chunk parser), OGG (stb_vorbis), MP3 (dr_mp3), and FLAC (dr_flac), all decoded to PCM and uploaded to OpenAL buffers. Implemented a layered volume system (MASTER, MUSIC, SFX, AMBIENT, UI) where each source’s final gain is computed as masterGain × layerGain × sourceGain, allowing independent group control without touching individual sources. The demo scene features four spatially placed sources with a distance-based crossfade model (linear falloff between 6 m and 20 m) and per-frame 3D listener tracking synced to the camera’s position and orientation.

Terrain System
Built the engine’s procedural terrain pipeline end to end. The heightmap is generated with fractal Perlin noise (configurable frequency, octaves, persistence, redistribution) or loaded from an external image. The terrain is divided into a configurable chunk grid (up to 16×16 chunks of 1 km²) with per-chunk mesh subdivision. Surface appearance uses splat mapping — three textures (grass, ground, snow) blended by height plus a detail overlay. Vegetation is generated procedurally: an L-System constructs tree geometry from rewrite rules, and up to 5 000 instances are scattered across the terrain via GPU instancing within configurable height bands. Added a runtime sculpting tool with Raise, Lower, and Smooth brush modes controllable through ImGui, and a world-generation panel that regenerates terrain and vegetation in-place without restarting the application.

# Technologies
C++
OpenGL
Vulkan
GLSL
ImGui
CMake

# Features
Multi-backend rendering architecture (OpenGL / Vulkan)
Modular render pass system
Material and shader abstraction framework
Deferred rendering pipeline
Custom UI framework
Resource and state management systems

# Team
Developed by a team of three developers as a university capstone project.
