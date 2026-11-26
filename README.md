# HP Silicon Standalone

**Standalone generative-music applications built with SuperCollider 3.14 for Apple Silicon Macs.**

HP Silicon Standalone is a collection of applications for organizing, transforming, generating, and performing user-defined musical sounds. The collection includes systems based on musical agents, density, matrices, automated processes, scores, and time structures.

Several editions are available, with optional [Wekinator](http://www.wekinator.org/) control, HPtransformer learning and generation, or both.

---

## Table of contents

- [Applications](#applications)
- [Edition names](#edition-names)
- [Requirements](#requirements)
- [Installation](#installation)
- [First launch and working folders](#first-launch-and-working-folders)
- [Adding your own sounds](#adding-your-own-sounds)
- [Wekinator editions](#wekinator-editions)
- [HPtransformer editions](#hptransformer-editions)
- [Performance and latency](#performance-and-latency)

---

## Applications

The collection currently includes the following application families.

| Application | Main purpose | Available editions |
|---|---|---|
| **Agents** | Organize and evolve autonomous musical agents | Base, Wek, TR, Wek+TR |
| **Density** | Explore musical density and event distribution | Base, Wek, TR, Wek+TR |
| **Matrix** | Organize sound and control data in matrix structures | Base, Wek, TR, Wek+TR |
| **Robot** | Automated and generative musical processes | Base, TR, Wek, Wek+TR |
| **Time** | Organize temporal structures and musical evolution | Base, Wek |
| **Scores** | Work with score-oriented musical organization | Base |
| **Provinescu** | All in One Launcher for All Software| Base, TR, Wek, Wek+TR |

---

## Edition names

| Name pattern | Wekinator | HPtransformer | Description |
|---|---:|---:|---|
| `Agents`, `Density`, etc. | No | No | Standard standalone application |
| `WekAgents`, `WekDensity`, etc. | Yes | No | Adds Wekinator parameter control |
| `AgentsTR`, `DensityTR`, etc. | No | Yes | Adds HPtransformer learning and generation |
| `WekAgentsTR`, `WekDensityTR`, etc. | Yes | Yes | Combines Wekinator and HPtransformer |

`TR` identifies an edition using HPtransformer. `Wek` identifies an edition designed to communicate with Wekinator.

---

## Requirements

### Base editions

- Apple Silicon Mac: M1, M2, M3, M4, or later
- A tested version of macOS
- Audio output or an audio interface supported by macOS

### Wek editions

- All base-edition requirements
- [Wekinator](http://www.wekinator.org/)
- OSC configuration matching the application guide

### MIDI workflows

- macOS **IAC Driver** enabled or any other MIDI driver must be enabled to launch the standalone application
- A MIDI controller is optional

### TR editions

- All base-edition requirements
- More CPU headroom than the corresponding base edition
- A practical starting server latency of `0.2` seconds

> The standalone applications are built with SuperCollider 3.14. A separate SuperCollider installation should not be required for ordinary standalone use unless a specific guide states otherwise.

---

## Installation

1. Download the required archive from **GitHub Releases**.
2. Extract the `.7z` archive with a compatible utility such as [Keka](https://www.keka.io/) or 7-Zip.
3. Move the `.app` bundle to:

   ```text
   /Applications
   ```

6. Launch the application from the Applications folder.

### If macOS blocks the first launch

If the application is unsigned or not notarized:

1. Try to open the application once.
2. Open **System Settings > Privacy & Security**.
3. Find the message concerning the blocked application.
4. Select **Open Anyway**.
5. Confirm the launch.

---

## First launch and working folders

Each application stores its user data in a working folder.

On first launch:

1. Click **Working Folder**.
2. Select an existing folder, or choose the application's default-folder option.
3. If the current build uses **Cancel** to select the default location, the application creates:

   ```text
   ~/Documents/ApplicationName/
   ```

4. Confirm that the folder contains the expected preset, sound, and configuration files.

Typical working-folder contents may include:

```text
ApplicationName/
├── presets/
├── data/
├── sound
├── list sound
├── sessions/
└── configuration files
```

Actual contents vary by application and edition.

---

## Adding your own sounds

Applications load user-defined sounds from a file named `sound` or `list sound` in the working folder.

Before editing:

1. Duplicate the original file.
2. Store the backup outside the active working folder.
3. Use a plain-text editor.
4. Preserve UTF-8 encoding.
5. Preserve every bracket, comma, symbol, and parenthesis.
6. Restart the application or use its reload command after saving.

---

## Wekinator editions

Wek editions communicate with Wekinator through OSC.

General workflow:

1. Launch the HP standalone application.
2. Launch Wekinator.
3. Open or create the matching Wekinator project.
4. Verify the OSC input port, output port, host, number of inputs, and number of outputs.
5. Confirm that incoming values change in Wekinator.
6. Train the Wekinator model.
7. Start Wekinator output.
8. Confirm that the standalone parameters respond.

---

## HPtransformer editions

TR editions use HPtransformer for online learning and generation.

HPtransformer may include:

- multi-head attention;
- mixture-of-experts routing;
- long-term memory;
- trajectory memory;
- prioritized replay;
- AutoTune;
- MetaLearn;
- targeted RCU inference snapshots.

---

## Performance and latency

Occasional `late` messages may appear during heavy transformer operations. Persistent `late` messages mean that the workload or scheduling should be adjusted.

Try the following in order:

1. Increase server latency to `0.2` seconds.
2. Keep `replayBatchSize` at `1`.
3. Disable verbose status output.

---

MIT License

Copyright (c) 2026 Provinescu

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
