# HP Silicon Standalone

**Standalone generative-music applications built with SuperCollider 3.14 for Apple Silicon Macs.**

HP Silicon Standalone is a collection of applications for organizing, transforming, generating, and performing user-defined musical sounds. The collection includes systems based on musical agents, density, matrices, automated processes, scores, and time structures.

Several editions are available, with optional [Wekinator](http://www.wekinator.org/) control, HPtransformer learning and generation, or both.

---

## Table of contents

- [Applications](#applications)
- [Edition names](#edition-names)
- [Requirements](#requirements)
- [Downloads](#downloads)
- [Installation](#installation)
- [First launch and working folders](#first-launch-and-working-folders)
- [Adding your own sounds](#adding-your-own-sounds)
- [MIDI and IAC Driver](#midi-and-iac-driver)
- [Wekinator editions](#wekinator-editions)
- [HPtransformer editions](#hptransformer-editions)
- [Performance and latency](#performance-and-latency)
- [Documentation](#documentation)
- [Troubleshooting](#troubleshooting)

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
| **Provinescu** | Collection-specific standalone environment | Base, TR, Wek, Wek+TR |

Availability is based on the currently published archive names. If an edition is not listed, it should be considered unavailable until a release explicitly includes it.

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
- Enough free disk space for the application and its working folder

### Wek editions

- All base-edition requirements
- [Wekinator](http://www.wekinator.org/)
- OSC configuration matching the application guide

### MIDI workflows

- macOS **IAC Driver** enabled only when virtual MIDI routing is required
- A MIDI controller is optional

### TR editions

- All base-edition requirements
- More CPU headroom than the corresponding base edition
- A practical starting server latency of `0.2` seconds

> The standalone applications are built with SuperCollider 3.14. A separate SuperCollider installation should not be required for ordinary standalone use unless a specific guide states otherwise.

### Compatibility table

Maintain this table with tested systems only:

| Application version | Mac chips tested | macOS versions tested | Status |
|---|---|---|---|
| `v0.9.0-beta.1` | Add tested chips | Add tested versions | Planned |

Do not claim compatibility with a macOS version until the application has been launched, produced sound, saved a preset, reopened its working folder, and completed a normal quit on that version.

---

## Downloads

Download applications from the repository's **GitHub Releases** page rather than from the `main` branch.

Recommended asset naming:

```text
Agents-macOS-arm64-v0.9.0-beta.1.7z
AgentsTR-macOS-arm64-v0.9.0-beta.1.7z
WekAgents-macOS-arm64-v0.9.0-beta.1.7z
WekAgentsTR-macOS-arm64-v0.9.0-beta.1.7z
```

Each release should include:

- versioned application archives;
- release notes;
- `SHA256SUMS.txt`;
- relevant guides;
- known limitations;
- tested macOS versions.

---

## Installation

1. Download the required archive from **GitHub Releases**.
2. Download `SHA256SUMS.txt` from the same release.
3. Verify the archive checksum.
4. Extract the `.7z` archive with a compatible utility such as [Keka](https://www.keka.io/) or 7-Zip.
5. Move the `.app` bundle to:

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

Do not disable Gatekeeper globally. Do not run downloaded shell commands unless their purpose and source have been verified.

### Signed and notarized builds

When a build is signed and notarized, state this explicitly in the corresponding release notes. Do not imply that all releases are signed unless every downloadable application has been checked.

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

A future interface should provide a visible **Use Default Folder** button instead of using **Cancel** as an implicit command.

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

The exact syntax depends on the application. Use only a verified example from that application's guide. A malformed SuperCollider expression can prevent the sound list from loading.

See [Documentation/Sound-Files.md](Documentation/Sound-Files.md).

---

## MIDI and IAC Driver

The Apple component is named **IAC Driver**, not “IAC Manager.” It is required only for virtual MIDI routing between applications.

To enable it:

1. Open **Audio MIDI Setup**.
2. Select **Window > Show MIDI Studio**.
3. Double-click **IAC Driver**.
4. Enable **Device is online**.
5. Create or select an IAC bus.
6. Restart the standalone application if it was already open.

Physical MIDI controllers do not always require IAC Driver. Follow the individual application's MIDI guide.

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

Document the exact OSC ports and vector dimensions separately for every application. Do not assume that Agents, Density, Matrix, and Time use identical mappings.

See [Documentation/Wekinator.md](Documentation/Wekinator.md).

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

Recommended starting points:

```text
Learning interval:       0.10 s
Generation interval:     0.05–0.15 s
Snapshot publication:    every 5–10 s
Replay batch size:       1
Server latency:          0.2 s
```

These are starting values, not guarantees. Performance depends on the application, model size, Mac model, audio interface, sample rate, buffer size, and simultaneous software load.

See [Documentation/HPtransformer.md](Documentation/HPtransformer.md).

---

## Performance and latency

Occasional `late` messages may appear during heavy transformer operations. Persistent `late` messages mean that the workload or scheduling should be adjusted.

Try the following in order:

1. Increase server latency to `0.2` seconds.
2. Reduce the learning frequency.
3. Reduce the generation frequency.
4. Publish transformer snapshots less often.
5. Keep `replayBatchSize` at `1`.
6. Disable verbose status output.
7. Close unused applications.
8. Test the base edition before testing the TR edition.
9. Increase audio buffer size if acceptable for the musical use case.

Record the following when reporting a performance problem:

```text
Application and edition
Application version
Mac model and chip
macOS version
Audio interface
Sample rate
Hardware buffer size
Server latency
Learning interval
Generation interval
Snapshot interval
Complete error or late-message text
```

---

## Documentation

Repository documentation:

- [Installation](Documentation/Installation.md)
- [Applications and editions](Documentation/Applications.md)
- [Sound files](Documentation/Sound-Files.md)
- [MIDI and IAC Driver](Documentation/MIDI-IAC.md)
- [Wekinator setup](Documentation/Wekinator.md)
- [HPtransformer editions](Documentation/HPtransformer.md)
- [Troubleshooting](Documentation/Troubleshooting.md)
- [Support](SUPPORT.md)
- [Changelog](CHANGELOG.md)

Add one complete guide per application family when available.

---

## Troubleshooting

### The application does not open

- Confirm that the `.app` bundle is in `/Applications`.
- Check **System Settings > Privacy & Security**.
- Confirm that the archive was fully extracted.
- Compare the archive's SHA-256 checksum.
- Test the latest supported release.

### No sound

- Check macOS audio output.
- Check the selected audio interface.
- Confirm sample rate and device availability.
- Verify the application's output level.
- Load a known-good default sound file.

### The working folder is missing

- Click **Working Folder**.
- Select a valid writable folder.
- Check `~/Documents/ApplicationName/` if the default-folder behavior was used.
- Verify permissions in **System Settings > Privacy & Security > Files and Folders**.

### Wekinator does not respond

- Confirm that the correct Wek edition is running.
- Verify OSC host and ports.
- Verify input and output dimensions.
- Confirm that the Wekinator model is running.

### Frequent `late` messages

- Increase latency to `0.2` seconds.
- Reduce transformer learning and generation rates.
- Publish snapshots less frequently.
- Test the equivalent base edition.

### The sound file no longer loads

- Restore the backup.
- Compare the edited file with the original.
- Check commas, parentheses, brackets, symbols, and UTF-8 encoding.
- Reintroduce custom sounds one at a time.

See [Documentation/Troubleshooting.md](Documentation/Troubleshooting.md) for a structured diagnostic checklist.

---

## Acknowledgements

Built with [SuperCollider](https://supercollider.github.io/) for generative music, algorithmic composition, live performance, and musical interaction.

Optional editions integrate [Wekinator](http://www.wekinator.org/) and HPtransformer.
