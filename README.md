# HP Software Silicon Standalone

A standalone software collection for organising musical sounds created using SuperCollider 3.14 (for Mac Silicon).

There are several software versions (exemple with Agents):

Agents Basic software.

WekAgents  with Wekinator added to control parameters.

AgentsTR  with HPtransformer added.

WekAgentsTR with Wekinator and HPtransformer added.

To use the Wek... versions, you need to install Wekinator:
https://github.com/fiebrink1/wekinator

You will find the necessary models for each piece of software in the repository:
[Wekinator-Models-for-HP-Software](https://github.com/provinescu/Wekinator-Models-for-HP-Software)

Quick started:

Very important: Unzip the archive and place the software in the ‘Applications’ folder before using it.
Ensure that MIDI is enabled by default ‘IAC Manager’.
Please be patient when starting it up for the first time – it takes a little while.

Launch the programme.
A window will open displaying a series of settings.
The first time you use it, simply click the ‘Working Folder’ button and then select ‘Cancel’.
A folder named after the programme will be created in your ‘home/documents/’ directory.
This is where the presets and data will be saved.
You can, of course, create further working folders later on.

Please note: some software programmes that use sounds loaded into memory are very sensitive to the number of sounds used.
If you wish to use your own sounds, you will need to create a new folder so that the software can initialise the start-up files correctly.
To use your sounds, edit the file named ‘sound’ or ‘list sound’ in the working folder, ensuring you follow the correct syntax.

 Check the guides!
[ HP-Software-Guides](https://github.com/provinescu/HP-Software-Guides)

Otherwise, explore and have fun.

Notes:

For versions using the Transformer, depending on the latency, you may receive ‘late’ messages. This is perfectly normal. The Transformer performs a great deal of computation.
If you set the latency to 0.2 (the default latency for the Supercollider server), you should not normally receive any ‘late’ messages.

With certain software, error messages may appear in the post window (e.g. ‘node not found’, ‘late’, ‘buffer’, etc.).
These have no effect on the software’s operation.

These standalone are based on the classes you will find here:
[ Software-Classes](https://github.com/provinescu/Software-Classes)

