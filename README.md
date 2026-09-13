# Raven Sim

An interactive educational game about animal behavior, developed in the PLAYlab at the University of Illinois Urbana-Champaign under the supervision of Dr. Katryna Starks.

Raven Sim treats animal behavior as an emergent property of individual agents following local rules, rather than as species-level facts to be read and recalled. The player inhabits the simulation as one agent among many, inferring population-level pattern from inside it. The project ships as an open-source 3D game with supplemental materials for teachers working in ecology and beyond.

This repository accompanies dissertation research on educational game design.

**Status:** In development. The current build is a technical prototype.

## Requirements

- Unity **6000.3.24f1** (Unity 6.3 LTS)
- Universal Render Pipeline
- WebGL Build Support module
- Git LFS

The Unity version is pinned for the duration of the study. Do not upgrade the editor without a deliberate decision — engine changes can alter render output and input behavior, which breaks comparability between builds that participants have played.

## Setup

```bash
git lfs install
git clone https://github.com/RobbieSieczkowski/raven-sim-dissertation.git
cd raven-sim-dissertation
```

Open the project folder in Unity Hub using the version above.

### Configure the merge driver

Scenes and prefabs are Unity YAML. Git's default text merge can silently corrupt them, so `.gitattributes` routes those files to Unity's SmartMerge tool. The attributes are committed, but the driver itself is local machine configuration and must be set up per clone:

```bash
git config --global merge.unityyamlmerge.name "Unity SmartMerge"
git config --global merge.unityyamlmerge.driver '"C:/Program Files/Unity/Hub/Editor/6000.3.24f1/Editor/Data/Tools/UnityYAMLMerge.exe" merge -p %O %B %A %A'
git config --global merge.unityyamlmerge.recursive binary
```

On macOS the driver path is `/Applications/Unity/Hub/Editor/6000.3.24f1/Unity.app/Contents/Tools/UnityYAMLMerge`.

## Building for web

1. File → Build Profiles → select **Web** → Switch Platform
2. Edit → Project Settings → Player → Web → Publishing Settings
   - Compression Format: **Brotli**
   - Decompression Fallback: **enabled** (required for hosts where `Content-Encoding` headers cannot be configured, including itch.io)
3. Build to `Builds/` — this directory is gitignored and is never committed

To publish, zip the *contents* of the build folder so that `index.html` sits at the archive root, then upload to itch.io as an HTML project with "This file will be played in the browser" enabled.

## Repository conventions

- Build output, `Library/`, and generated IDE files are excluded via `.gitignore`
- Binary assets (models, textures, audio, fonts) are tracked through Git LFS — see `.gitattributes`
- `.meta` files are always committed; never ignore them

## Assets and credits

<!-- Maintain a running list. Every third-party asset needs its source and license recorded here. -->

| Asset | Source | License |
| --- | --- | --- |
| | | |

## License

<!-- TODO: decide before making this repository public. -->

Code and assets are licensed separately. Third-party assets remain under their original licenses as listed above.

## Acknowledgements

Developed under the supervision of Dr. Katryna Starks in the PLAYlab, University of Illinois Urbana-Champaign.
