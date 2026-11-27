# HP Standalone Applications for Apple Silicon

> **Provinescu Software Production**
> Standalone generative-music applications for Macs with Apple silicon.
> 
> These Standalone use the VSTplugin class: https://github.com/Spacechild1/vstplugin.
> 
> Were created using Platypus: https://github.com/dathinaios/sc_osx_standalone.
> 
> Have been tested and verified on Mac OS Sequoia.

**SuperCollider 3.14 · Apple silicon · Generative Music · No Coding Required**

This repository brings together standalone applications designed to organize, transform, generate, and perform with sounds selected by the user.

## Overview

Developed as an extension of my practice as a **drummer, composer, and software developer**, this collection explores musical agents, density, matrices, automated processes, scores, and temporal structures.

The standalone applications make these systems accessible without requiring users to work directly in the SuperCollider development environment.

## Available applications

| Application | Main function | Standard | Wek | TR | Wek+TR |
|---|---|:---:|:---:|:---:|:---:|
| **Agents** | Organize and evolve autonomous musical agents | Yes | Yes | Yes | Yes |
| **Density** | Explore musical density and event distribution | Yes | Yes | Yes | Yes |
| **Matrix** | Organize sounds and control data in matrix structures | Yes | Yes | Yes | Yes |
| **Robot** | Create automated and generative musical processes | Yes | Yes | Yes | Yes |
| **Time** | Organize temporal structures and their musical evolution | Yes | Yes | No | No |
| **Scores** | Work with score-based musical organization | Yes | No | No | No |
| **Provinescu** | Launch the collection from a single application | Yes | Yes | Yes | Yes |

## Available editions

| Edition | Typical name | Wekinator | HPtransformer | Main function |
|---|---|:---:|:---:|---|
| **Standard** | `Agents` | No | No | Standard standalone application |
| **Wek** | `WekAgents` | Yes | No | Parameter control via Wekinator |
| **TR** | `AgentsTR` | No | Yes | Learning and generation with HPtransformer |
| **Wek+TR** | `WekAgentsTR` | Yes | Yes | Combines Wekinator and HPtransformer |

The `Wek` prefix identifies an edition that communicates with Wekinator. The `TR` suffix identifies an edition that integrates HPtransformer.

## Requirements

### Standard editions

- A Mac with Apple silicon
- A compatible version of macOS
- Built-in audio or a macOS-compatible audio interface
- The macOS IAC Driver or another MIDI source enabled before launch

A physical MIDI controller is optional, but the applications require an available MIDI source.

### Wek and Wek+TR editions

- All Standard-edition requirements
- [Wekinator](https://github.com/fiebrink1/wekinator)
- OSC settings matching the selected application
- The matching Wekinator project

Matching projects are available in [Wekinator Models for HP Software](https://github.com/provinescu/Wekinator-Models-for-HP-Software).

### TR and Wek+TR editions

- All Standard-edition requirements
- Additional CPU resources
- Recommended initial audio-server latency: `0.2` seconds

A separate SuperCollider installation is normally not required to use the standalone applications.

## Installation

1. Download the required `.7z` archive from the repository's **Releases** section.
2. Extract it with [Keka](https://www.keka.io/) or another utility compatible with the 7-Zip format.
3. Move the extracted application into:

```text
/Applications
```

4. Launch the application from the Applications folder.
5. Wait for the main window to appear. The first launch may take longer than later launches.

> **Important:** Do not run the application directly from the archive or the Downloads folder. Move it to `/Applications` first.

## Opening a blocked application in macOS

If macOS blocks an unsigned or unnotarized application:

1. Try to open the application once.
2. Open **System Settings**.
3. Select **Privacy & Security**.
4. Locate the message about the blocked application.
5. Click **Open Anyway**.
6. Confirm the launch.

Only use this procedure for an application downloaded from the official Provinescu repository.

## First launch

Each application stores its data in a dedicated working folder.

1. Launch the application.
2. Wait for the main window to appear.
3. Use the **Working Folder** command.
4. Select or create the working folder.
5. In editions where **Cancel** selects the default location, click **Cancel**.

The folder is generally created at:

```text
~/Documents/ApplicationName/
```

It contains presets, data, sound lists, and configuration files.

You can create additional working folders to keep projects or sound libraries separate.

## Custom sounds

Some programs load sounds into memory and may be sensitive to the number or size of the selected files.

To use your own sounds:

1. Create a new working folder.
2. Allow the application to initialize its files.
3. Locate the `sound` or `list sound` file.
4. Make a backup copy.
5. Edit the file in a text editor.
6. Preserve all existing brackets, commas, symbols, and paths exactly.
7. Save the file.
8. Restart the application or reload its sound configuration.

## Using Wekinator

Wek and Wek+TR editions communicate with Wekinator through OSC.

1. Launch the HP standalone application.
2. Launch Wekinator.
3. Open the matching Wekinator project.
4. Check the OSC address.
5. Check the input and output ports.
6. Check the numbers of inputs and outputs.
7. Confirm that incoming values change in Wekinator.
8. Train the model.
9. Start Wekinator's output.
10. Confirm that the standalone application's parameters respond correctly.

## Using HPtransformer

TR and Wek+TR editions use HPtransformer for real-time learning and generation.

Depending on the application and edition, HPtransformer may include:

- multiple attention heads;
- mixture-of-experts routing;
- multiple memory mechanisms;
- prioritized replay;
- AutoTune;
- MetaLearn;
- targeted inference snapshots.

These editions require more CPU resources than Standard and Wek editions.

## Performance and latency

`late` messages may appear during computationally intensive HPtransformer operations.

If they become frequent:

1. Set the audio-server latency to `0.2` seconds.
2. Keep `replayBatchSize` at `1` when this setting is available.
3. Disable verbose status messages.

Messages such as `node not found`, `late`, or `buffer` may occasionally be non-critical if audio and controls continue to work correctly.

## Documentation

See:

- [HP Software Guides](https://github.com/provinescu/HP-Software-Guides)
- [Wekinator Models for HP Software](https://github.com/provinescu/Wekinator-Models-for-HP-Software)
- [Source Classes](https://github.com/provinescu/Software-Classes)

## Project philosophy

This is an artistic and software project dedicated to experimental music, generative systems, and sound organization. The project is developed by a drummer, composer, and software developer.

Explore the parameters, listen to the results, save useful configurations, and adapt the systems to your own musical practice.

- [GitHub profile](https://github.com/provinescu)
- [Music on Bandcamp](https://provinescu.bandcamp.com/)

## License

These applications are distributed under the MIT License. See the repository's `LICENSE` file for the full license text.
