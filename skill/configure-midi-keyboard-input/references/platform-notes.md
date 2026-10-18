# Platform and event notes

These official pages were inspected on 2026-10-18 for the narrow behaviors below. Match the user's actual application, edition, version and hardware manual before operating anything. Documentation supports a proposed route; it does not establish that a device was connected, a sound heard or a project saved.

## Connection and unintended control scope

[Ableton's MIDI controllers FAQ](https://help.ableton.com/hc/en-us/articles/360011853159-MIDI-controllers-FAQ) describes USB connections and a controller's MIDI output feeding an interface input. It distinguishes class-compliant devices from those needing a manufacturer's driver. Its custom-mapping section serves a broader control task; it is not a reason to enable every option for note input alone. Installation remains a separate action.

[Apple's USB music keyboard guide](https://support.apple.com/guide/logicpro/connect-a-usb-music-keyboard-lgcpebe87ef1/mac) directs readers to their keyboard/interface instructions and notes that supported controller knobs and sliders can receive automatic assignments. Therefore establish the existing assignment scope before experimenting with controls. This workflow does not need new mappings, and physical note-input acceptance cannot be inferred from an automatically recognized device name.

## Ableton Live

[Live's MIDI Settings](https://help.ableton.com/hc/en-us/articles/209774205-Live-s-MIDI-Settings) distinguishes Track note/CC traffic, Sync timing and Remote mappings. It also warns that unnecessary input/output clock routes can create feedback. Inspect an existing automatically configured controller before making manual changes; do not use a blanket all-ports setting or install a control-surface script for this bounded note-input task.

[Live 12 Routing and I/O](https://www.ableton.com/en/live-manual/12/routing-and-i-o/) documents specific input-port/channel selection and merged inputs. Its monitoring section distinguishes Auto from In; In suppresses clip output, so a setup that works for live playing needs its playback condition checked separately. Instruments transform MIDI events into audio, which then needs its own output route. Those statements do not establish that the user's speakers actually emitted sound.

[Live 12 Recording New Clips](https://www.ableton.com/en/live-manual/12/recording-new-clips/) separates input selection, record arming and actual recording. It also documents multiple-track selection and the recording effects of loop/overdub modes. Use those controls only in the intended scratch destination; do not infer permission to alter another armed track or overwrite an existing region. This guide does not require recording when the task is only live playing.

## Event interpretation and stopping

[The MIDI Association's MIDI 1.0 message summary](https://midi.org/summary-of-midi-1-0-messages) distinguishes channel voice events, controller changes, note release and channel-mode messages. It is an overview rather than a complete implementation specification. Use the app and device's documented interpretation for the actual route; this workflow does not generate raw messages, send SysEx or implement a MIDI parser.

[Apple's note-event reference](https://support.apple.com/guide/logicpro/note-events-lgcp215904a3/mac) documents channel and note-number fields, a zero velocity's release meaning, and differing octave-name conventions for the same MIDI number. It also explains that a stored note can appear as position and length rather than separate raw on/off messages. A different displayed C octave is not sufficient evidence that transpose should change.

[Apple's MIDI monitoring/reset reference](https://support.apple.com/guide/logicpro/monitor-and-reset-midi-events-lgcpc412346d/mac) makes the reset reach consequential: its discrete-note-off panic sends releases for every note on every channel of every MIDI port, and controller resets have broad output scope. A generic instruction to press Panic is therefore inappropriate when unrelated destinations are active. Select a documented safe containment/reset path for the actual setup, and distinguish quieting an audio output from clearing held event state. Never use a maximum-volume command as a silence remedy.

## Evidence limits

These sources inform the written method only. No device, application, note generator, recording, driver, controller script, sound library or project was run while preparing this guide. The illustration is fictional and unexecuted. A real setup still needs the selected device's manual, current native controls and the requested physical-event and listening observations.
