---
name: configure-midi-keyboard-input
description: "Connect an existing MIDI music keyboard to a chosen installed software instrument, bind its note input to the intended port, channel and track, and verify physical playing, release behavior and usable audio output. Use for a bounded live MIDI input setup, not audio recording, DAW control mappings, hardware-synth output, clock synchronization or exported MIDI validation."
---

# Make a MIDI keyboard play the intended software instrument

Deliver a usable keyboard-to-instrument setup and a short record of how to return to it. Keep device detection, incoming MIDI events, instrument response, audible output and recorded playback distinct. A flashing MIDI indicator does not prove that notes reach the intended instrument; hearing a keyboard's own speakers does not prove the computer produced the sound.

This guide covers one ordinary MIDI 1.0 keyboard input and one software-instrument destination through an existing supported USB connection or MIDI interface. Keep multi-zone/MPE setups, network or Bluetooth MIDI, external synthesizer control, clock distribution, custom scripts and control-surface mapping outside this bounded workflow. A keyboard with additional capabilities can still supply a supported ordinary note-input route; do not change its whole operating mode without the user's agreement.

Use [MIDI export verification](../verify-generated-midi/SKILL.md) for a delivered score file, [analog-audio digitization](../digitize-analog-audio/SKILL.md) for recording an existing physical sound source, and [application shortcuts](../configure-application-shortcuts/SKILL.md) for command bindings. Those workflows do not establish this live event-to-instrument path.

## Establish the instrument task and available path

Recover the following from the request, visible settings and exact device documentation. Ask only about a missing choice that changes the result:

- The physical keyboard/model, selected USB or MIDI-interface connection, computer and OS, and the actual installed music application/version
- The intended software instrument and whether the user needs live playing only, recorded-note entry, a reusable project, or a setup proposal
- The keyboard's documented note port and current transmit channel, any relevant octave/transpose setting, and a sustain pedal only if it belongs to the task
- The intended headphones/speakers and already-working audio device; identify where the local person expects to hear sound
- The project, performances, existing controller assignments and other devices that must remain untouched
- Who can press and release the physical keys and report what is heard; remote keystrokes or an on-screen piano cannot replace this observation

Inspect existing connections before creating another route. A synthesizer's USB socket can have model-specific roles; a connector shape or a power light does not establish MIDI communication. Follow the keyboard and interface manuals for compatible cables, power and port direction. Do not connect an audio output to a MIDI socket or assume that MIDI carries the keyboard's internal sound.

Use current official guidance for the actual device and app. [Platform and event notes](references/platform-notes.md) give verified starting points and important limits. Class-compliant operation, driver requirements and automatic controller assignment are product-dependent. If a required driver, instrument or sound library is absent, identify that prerequisite instead of installing it, downloading content or replacing the user's chosen app implicitly.

If device access or physical assistance is missing, finish the supported setup candidate and mark physical-input and listening checks pending. A desktop app's MIDI setup is not verified by opening its documentation or playing a web instrument somewhere else.

## Preserve the session and bound the effects

Protect unsaved work before changing projects, closing an app or reconnecting a shared interface. Use a fresh authorized scratch project or a separately saved project copy when a live check could record, overwrite clips, trigger an arrangement or change an existing performance. Do not overwrite the user's template to make a convenient test bed. Record only affected before-state settings and the intended final configuration.

A request for this setup covers ordinary in-scope app routing changes. It does not imply driver/firmware installation, a new account, purchasing an instrument, granting unexpected device permissions, changing system security or uploading a project. Obtain the applicable authority for those separate actions. Hand off credentials through a supported secure route. Stop at managed restrictions rather than changing policy.

Use local note input and the existing audio output. Do not activate microphone capture, record room audio, join a call, stream, transmit MIDI to a new network endpoint, or create virtual buses for a keyboard-input check. Check whether a project location synchronizes to a service before saving private work there; use only the authorized destination. Do not retain unrelated performance data or device lists as diagnostic evidence.

Before playing, identify a safe way to stop the intended sound and a comfortable user-chosen listening level. Preserve an independent pointer/keyboard route to the app. A stop transport command may leave a live instrument sounding. A MIDI panic/reset command may affect every connected output; inspect its documented reach before treating it as a local stop. Keep unrelated hardware outputs and live performances outside the check.

## 1. Identify the musical-event input

Trace the actual route:

physical keys/pedal → keyboard's selected note output → host MIDI input port → app input filter → target track/instrument

Keep the separate audio route beside it:

software instrument → track/main output → selected audio device → intended headphones/speakers

For a DIN connection, establish which physical keyboard output reaches which interface input. The app may expose the interface port rather than the keyboard's model name. For USB, distinguish note ports from any separate DAW-control or auxiliary ports. Bind the observed label to the documented connection; do not enable every similar entry until one works.

Inspect the host/app's existing device availability and any port-in-use or unavailable state. If necessary and supported, have the local person perform one deliberate press and release while observing a native MIDI activity display. A general activity lamp can represent clock, controllers or other traffic, so it does not identify the event type, key or source by itself. Use an already-available bounded event view if the distinction matters; do not install a monitor or capture a whole performance by default.

Record the port, event channel and note number when visible. Use MIDI note numbers to resolve an apparent octave discrepancy before changing transpose: applications can label the same note number with different octave names. Preserve the user's actual transposition when it is intentional. If only a merged input is observable, report that source attribution remains limited rather than claiming a specific port has been proved.

An absent port calls for a model-matched connection check, not a global settings reset. Reconnecting a shared audio/MIDI interface can interrupt other work; resolve that effect before proceeding. After a reconnect, reidentify the actual port instead of relying on a remembered row position.

## 2. Bind one input to one software instrument

Use a known installed software instrument and a simple existing sound suited to the requested check. A MIDI-only track without an instrument cannot establish audible software playback. Preserve existing sound design; a diagnostic instrument belongs in the scratch project, not over a valued track's plug-in chain.

Select the intended input port and supported channel at the narrowest useful track scope. Leave unrelated global ports intact. If the keyboard's channel is unknown, first inspect it or temporarily observe that same port's channels in the scratch context. Resolve the source channel before deciding whether a fixed-channel or all-channel setting fits the actual task. Do not change every controller to channel 1 merely to match a default.

Inspect the target track's receive filter, selection/record-enable behavior, monitor state, mute, instrument availability and audio destination. Avoid changing all these at once. Keep record-enabling distinct from starting recording. Inspect multiple-track selection before changing a control that could apply to the whole selection, and preserve unrelated armed tracks rather than silently disarming the user's session.

For Ableton Live 12, the documented ordinary path uses the note port's Track input, a software-instrument track's MIDI From port/channel, and an appropriate monitor state. Auto monitors an armed track subject to clip-playback behavior; In passes live input while suppressing that track's clip output. Select the state for the actual live-playing or recording task, then revisit it for playback. Remote mappings, Sync clock routes and Track output to hardware serve other purposes and are not prerequisites for this one-way setup. See the [Live notes](references/platform-notes.md#ableton-live).

For another selected app, use its supported equivalents. Do not transplant Live's monitor labels into Logic or assume that selecting a track always record-enables it. Automatic controller integration may already assign buttons or knobs. Inspect that boundary and confine the trial to the intended musical keys/pedal; do not test transport buttons or turn controls experimentally.

Keep return paths absent from the new candidate unless explicitly required. Check for an existing USB-plus-DIN parallel feed, virtual bus, second monitored track or MIDI echo that could deliver the same action twice. A common all-inputs setting can merge several routes. Prefer selecting the single evidenced input for this track over deleting other devices or globally disabling working integrations.

## 3. Prove physical playing and release behavior

Choose a short, original, non-sensitive sequence agreed with the local person. A few distinct single notes, a repeated note with a clear release between presses, and a small chord usually distinguish the important paths. Use ordinary key pressure rather than asking for forceful playing. Test only features the user needs.

For each observation, keep its boundary visible:

| Observation | What it establishes | What still needs evidence |
| --- | --- | --- |
| Host/app lists the input | The port is available under that identity | Physical key events and destination routing |
| Deliberate presses reach a MIDI event view | Events reach that observed point | Instrument interpretation and audio output |
| Intended instrument/track responds | Events reach that instrument path | Sound at the user's chosen output |
| Local person hears the expected notes there | Audible live use under those conditions | Saved recording, later reconnection and measured latency |
| A saved scratch region replays correctly | The checked recorded path retained the sequence | Every future project or exported file |

Observe note starts and releases, not just initial sound. In ordinary MIDI 1.0, a zero-velocity Note On can represent release; do not count it as a second attack. Follow the event view's representation rather than demanding two differently named messages. A region editor may show a note's duration rather than raw release messages.

For a requested pedal, first check released-state behavior, then one held-note/pedal-down/key-release/pedal-up sequence through the same selected channel and instrument. Establish that the chosen instrument actually supports the intended sustain behavior. A natural release tail or reverb need not stop instantly; separate the sound's designed decay from a note that remains held. A message log alone does not establish audible silence, and audible decay alone does not prove which controller message arrived.

If the pedal behaves backwards or remains on, stop that branch and check the exact pedal/keyboard compatibility and model-supported polarity procedure. Do not randomly unplug a pedal, power-cycle equipment with work active, rewrite controller assignments or assume that any footswitch is a sustain pedal. Preserve the working note path while that specific requirement remains unresolved.

If a single ordinary press appears doubled, compare incoming events and receiving tracks before blaming latency. Distinguish duplicate note events, two sounding instruments, the keyboard's own tone generator, and an intentionally layered patch. A thicker sound is not proof of duplicate MIDI. Do not use a generic Local Control Off command: identify the actual local-sound route and its model-specific effect before proposing any keyboard setting change.

Keep a user's report of lag separate from a measured latency value. A slow-attack sound and a delayed monitoring path can feel similar. A simple known patch or already-available supported comparison can narrow the cause within scope. Do not reduce every buffer to its minimum, change the sample rate of existing work, install a different driver or promise a universal acceptable latency. If responsiveness remains unacceptable, report the exact tested path and the next supported audio-configuration decision.

## 4. Verify the retained result when requested

For live-playing-only acceptance, actual physical playing and the required release/controller behavior can be sufficient. Do not force a recording or file export merely to fill a checklist.

When recorded-note entry is required, record only the bounded scratch sequence into an empty intended region/clip. Inspect the current recording mode, loop/overdub state and target before starting. Preserve the source performance: do not quantize, lengthen or delete events to hide a routing defect. Stop and inspect that exact take for plausible note identities, repetitions, chord membership, durations and required pedal/controller data. A matching total note count cannot establish that the right notes were retained.

Replay the take with live input no longer contributing, using the app's supported monitor/arm state. In particular, a live-input monitor mode can suppress clip playback. Do not diagnose a silent saved clip by re-pressing the hardware keys and hearing the live instrument. Compare the recorded sequence to the performed check; listening and event inspection support different claims.

If a reusable project or template was requested, save it under a new authorized identity, then reopen/read back its input route, instrument, audio destination and relevant monitor state. Keep application-global input preferences separate from settings stored in the project; a project file may not carry every prerequisite. Reopening must not discard unsaved work or replace a current session without permission.

A deliberate unplug/reconnect or app restart is required only if it belongs to acceptance or resolves the observed fault. Release keys/pedal and stop the affected sound first. Preserve other interface users, then reidentify the port and repeat the small physical check. A successful current session does not establish behavior after sleep, reboot, a changed USB connection or use on another machine.

## Recovery, handoff and stopping

Choose recovery from the failed boundary:

- **No physical events:** inspect the selected device route, model mode and port availability; do not reinstall or reset the app speculatively
- **Events but no instrument response:** inspect the exact port/channel filter, target and monitor/record-enable state; preserve the working input
- **Instrument response but no audible output:** inspect the existing audio path, mute and chosen endpoint; changing MIDI channels cannot fix a missing audio destination
- **Stuck sound:** stop further playing and reduce or mute the intended audible path through the agreed safe control. This contains sound but does not prove note state cleared. Inspect release/sustain state and use only a documented reset whose affected outputs are understood and authorized, then retest
- **Unexpected app command or external hardware response:** stop the trial, inspect the actual effect and routing, and hold further playing until the assignment/return-path boundary is understood. Do not assume Undo reverses external effects
- **Uncertain save or interrupted recording:** inspect existing regions/files and current transport state before retrying; do not create duplicate takes over an unknown first result

Restore only temporary changes that remain safe and useful, comparing current values to the recorded before state so later user edits survive. Leave the requested final setup intact, turn off temporary logging and stop recording/playback. Do not delete test projects, reset all MIDI preferences or erase controller presets as automatic cleanup.

Return a concise private handoff with:

- Keyboard connection and actual note-input port/channel → target instrument/track → audio output
- Final affected settings and what is global versus project-specific
- Physical sequence and release/pedal checks actually observed, with direct versus local-person evidence identified
- Saved project/take if requested, what was reopened/replayed, and the supported return/stop route
- Any unresolved requirement and its smallest next check

Use a status such as prepared only, events received but audio unverified, live playing checked, or recorded/reopened path checked. Do not call simulated notes a physical-device test, an event log a listening check, or a working input setup an export or timing certification. Stop when the requested stage is evidenced or a specific physical-access, capability, permission or device-support prerequisite blocks it.

## Fictional, unexecuted illustration

An invented user wants an existing USB keyboard to play a software piano in a scratch project. The hypothetical app's general MIDI light flashes, but the target track listens only to channel 1 while the keyboard's documented note port transmits on channel 3. The proposed correction would bind that track to the identified note port and channel 3 without enabling clock, remote-control or hardware-output routes.

A later hypothetical scratch take contains the intended notes, but playback is silent while the track remains in a mode that monitors only live input. Hearing sound after pressing the keyboard would not prove the take plays. The next supported check would select the app's appropriate playback state, leave the physical keys released, and replay the saved sequence. Until that observation occurred, only the recorded event content would be established.

This is an original decision illustration, not a completed setup. No keyboard, pedal, interface, application, MIDI event, sound, recording, project, setting or reconnection was operated, generated or tested for it.
