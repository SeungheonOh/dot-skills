---
name: configure-aggregate-audio-device
description: "Combine existing physical audio devices into one native macOS Aggregate Device for a chosen application, preserve separate channel identities and clock relationships, and verify the requested simultaneous input/output path. Use for reusable multi-device audio setup, not MIDI routing, mirrored playback, system-audio capture, recording production or driver installation."
---

# Make several audio devices usable as one application endpoint

Deliver a working aggregate configuration and a small channel map that lets the user return to the same setup. Keep physical devices, the aggregate's numbered channels, application tracks and the actual listening or recording destination connected. A device name appearing in an app does not establish that each required source reaches its own channel or that the intended output is audible.

This workflow covers a bounded set of already-connected, supported physical audio devices on one Mac and one installed Core Audio application. Use a common supported sample rate for this bounded route. It can combine several inputs, expose additional distinct outputs, or satisfy an application's requirement for one input/output device. Do not create an aggregate when an already-working single interface or separate app input/output selectors meet the task without it.

Keep wireless/network audio, virtual loopback drivers, new hardware clock wiring, streaming and software installation outside this workflow. An Aggregate Device does not by itself mix all inputs into one microphone or duplicate the same sound to every speaker. Apple's [multi-output guide](https://support.apple.com/guide/audio-midi-setup/play-audio-through-multiple-devices-at-once-ams7c093f372/mac) describes the separate playback-duplication feature; establish that this is not the requested outcome before proceeding.

[Meeting-device troubleshooting](../meeting-device-troubleshooting/SKILL.md) handles a failing call path. [MIDI keyboard setup](../configure-midi-keyboard-input/SKILL.md) binds musical events to an instrument. [Analog-audio digitization](../digitize-analog-audio/SKILL.md) captures an existing carrier. Those tasks may use an established audio device, but do not replace the channel-and-clock configuration here.

## Establish the required path

Use the request, visible configuration and exact device manuals to identify only what changes the setup:

- The Mac, macOS version, installed application and whether it accepts an Aggregate Device with the required channel count
- Each selected physical device, its connection, available input/output channels and supported sample rates
- Which sources must remain separate, which outputs are needed, and whether the user needs live use, a saved recording check or a reusable project
- The intended headphones/speakers and who can generate a harmless signal at each input and report what is heard
- Existing clock relationships, projects, device settings and other active audio sessions that must survive
- Authorized changes, capture sources, test duration and destination for any small local check recording

Do not require a serial-number inventory when two clearly identified devices suffice. If identical labels make selection ambiguous, resolve the physical-to-visible identity with available model information or a safe operator-assisted check. Do not unplug an active shared device merely to see which row disappears.

Check the real computer's access before promising operation. If physical assistance, app access or listening is unavailable, prepare the supported member/channel plan and mark the corresponding checks pending. Do not substitute an audio test in another environment.

Read the selected macOS version of Apple's [aggregate settings guide](https://support.apple.com/guide/audio-midi-setup/set-aggregate-device-settings-ams094c7edb4/mac), not just the first search snippet. Its controls and rate-conversion guidance can differ by version. Also read the device maker's compatibility and clock guidance when that affects a member. A marketing channel count is not evidence that the current driver exposes those channels together.

## Preserve the audio session and bound capture

Save or protect the user's current work before changing an audio engine, member sample rate or connection. Such changes can affect other applications using the same physical device, even when the new aggregate has its own name. Record the affected before state: app input/output selection, member format/rate, existing aggregate membership/order if relevant, clock selection, monitoring and current project identity. Avoid collecting unrelated device or project lists.

Prefer a newly named aggregate and an authorized scratch project rather than editing an aggregate already used by other projects. Do not replace a working template or rename a physical device to make its identity convenient. A name is a helpful label, not an immutable hardware identity.

Use existing authority for ordinary requested routing changes. Ask specifically before an uncovered microphone permission, recording, disruptive app restart, driver installation, hardware-clock change, cloud save or external transmission. A setup request does not authorize capturing other people's speech, an active call or all computer audio. Keep the check local, brief and non-sensitive; inspect whether the save location synchronizes elsewhere. Credentials, new persistent access and security-sensitive settings require their own supported authorization route.

Establish a comfortable listening level and a supported stop/mute route before monitoring. Keep speaker feedback and duplicate direct/software monitoring out of the proposed path. Never raise gain or output volume simply because the wrong channel is silent. Do not change phantom power, electrical connections or device operating modes experimentally. Physical operations belong with a capable local person following the equipment's instructions.

## 1. Decide membership and channel identity before selecting tracks

Create a compact proposed map:

physical member and local channel → aggregate input/output number → application track or output bus → intended use

Treat input and output numbering as separate sequences. A member can contribute inputs, outputs, both or no channels in the direction being considered. Do not calculate an input number by counting that member's output channels. Preserve mono sources as independent mono assignments unless the user actually needs a stereo pair; two microphones are not automatically a stereo recording.

Include only members required by the task. If the app supports separate input and output devices, an input aggregate can be paired with an existing independent listening device. That may avoid adding an unnecessary output-only member. If the app requires one device, include the required output member and explicitly route to its channels. Do not assume output 1–2 is the desired headphone socket merely because it is the default.

Use Audio MIDI Setup's Audio Devices window, add a new Aggregate Device, give it a useful unique name, and select the intended members through their Use controls. Apple's [aggregate creation guide](https://support.apple.com/guide/audio-midi-setup/combine-audio-devices-a-single-aggregate-ams6e21c3f61/mac) documents this native route. Read back actual membership and channel totals before applying the device to the music app.

The order of members affects app-facing channel numbers. Set the intended order through the supported interface, then copy the displayed input and output ranges into the map. Apple's [channel-identification guidance](https://support.apple.com/en-us/102171) explains the correspondence between Audio MIDI Setup and application channel slots. Reordering or adding a member invalidates the previous map until read back and checked; a track label such as “Guest mic” does not repair a changed input assignment.

If a member is absent or shows fewer channels than expected, hold that requirement. Inspect its existing supported connection and availability instead of adding an unrelated microphone or resetting audio services. Do not call an aggregate complete merely because its total channel count happens to match the requested number.

## 2. Establish a compatible rate and clock relationship

Separate three facts: the selected nominal sample rate, the device used as the time reference, and how the other devices are kept aligned with it. Matching displayed rates alone does not establish shared hardware timing. A resampling/synchronization setting is also not proof of bit-transparent capture or measured latency.

For this workflow, choose one rate supported by every required member and suitable for the application's intended project. Check both input and output formats where the device exposes them separately. Preserve the project's existing required rate; if no common supported rate meets it, report the mismatch rather than silently changing existing media or excluding a needed member. A newer system may offer mixed-rate operation, but that needs a separately established version/device-specific path rather than an assumed extension of this common-rate setup.

Stop affected playback/recording before changing formats. Set the supported member rates and verify their readback; then verify the final clock/sync-source selection. A settings procedure that temporarily selects each member must not accidentally leave the last inspected device as the final reference.

Apply the branch supported by the visible controls and matched documentation:

- **Clock Source / Drift Correction:** The [macOS 26 settings guide](https://support.apple.com/en-in/guide/audio-midi-setup/ams094c7edb4/3.6/mac/26) requires a common rate and distinguishes independent clocks from existing hardware synchronization. For independent members, choose an appropriate reliable reference and enable the documented correction on the non-reference members. Preserve the reference's supported control state rather than trying to force an unavailable checkbox. Apple's [creation article](https://support.apple.com/en-us/102171) explicitly describes correction for members other than the clock source
- **Sync Source / Sync:** Follow the installed version's [settings guide](https://support.apple.com/guide/audio-midi-setup/set-aggregate-device-settings-ams094c7edb4/mac) for reference selection and available synchronization controls. Do not assume this is only a label change or copy older checkbox instructions blindly. Keep this guide's chosen common-rate boundary even where newer documentation describes conversion between rates
- **Existing hardware-synchronized members:** Identify the actual primary clock and evidenced synchronized group from device guidance and current settings. Preserve that established relationship and apply software correction only as the matched documentation requires for members outside it. If the topology or lock state is unknown, stop this branch; do not invent a clock master, disable correction everywhere or wire a new clock chain

Record the final rate, reference, each member's correction/sync state and the basis for any hardware-synchronization claim. “Both are USB” or “both say 48 kHz” is not that basis. Do not claim a clock is intrinsically best without device evidence; use an appropriate stable documented reference and verify the actual requested path.

## 3. Bind the aggregate to the application

Open the authorized scratch project or safe project copy. Select the aggregate in the application's supported audio settings, then read back input and output independently. Some apps couple those selections. Preserve the intended listening device if the app allows it; do not change the Mac's global default input/output just to make a local app use the aggregate.

Match each required track or bus to the final channel map. Check input mono/stereo selection, actual numbered input, arm/monitor state, mute and destination. Multiple tracks that all listen to input 1 do not establish independent capture, even if each meter moves. Conversely, a stereo track can contain two different sources whose separate editing requirement is unmet.

Check what the chosen app can actually consume. A meeting app that exposes only a stereo pair may not use all aggregate inputs or mix them as intended. Do not silently route private sources into a call, install a virtual mixer or promise that every Core Audio app supports the same behavior. Keep the configured aggregate useful while marking an incompatible consumer as the blocker.

Leave existing creative processing untouched in the user's project. For the scratch check, use a simple known path without effects that obscure source identity, automatic gating or duplicate monitoring. Preserve any necessary device processing explicitly rather than claiming the aggregate bypasses it. Do not tune every buffer to its minimum; responsiveness and dropout tolerance belong to the real task and supported setup.

## 4. Prove the required channels under simultaneous use

Use a brief agreed sequence that distinguishes each required input and output. For microphones, have the local person make a different ordinary spoken cue near each selected microphone in turn, followed by silence. Acoustic pickup can reach several microphones, so complete silence on all other channels is not a valid universal requirement. Combine the known cue, physical proximity, relative response and selected channel evidence; hold identity if the result is ambiguous. Do not tap capsules forcefully or disconnect powered inputs as a test.

For outputs, use an already-authorized harmless playback cue routed to one intended destination at a time, at a comfortable unchanged volume. Confirm the actual headphones/speakers, not only an output meter. Then check the simultaneous input/output state the task requires. A working direct hardware monitor can bypass the app; it does not prove that the app receives or saves the signal.

Keep the acceptance boundaries separate:

| Observation | Supported conclusion | Remaining limit |
| --- | --- | --- |
| Aggregate and members are listed | Configuration is present under those identities | Correct track mapping and sound |
| Distinct input cues reach the mapped tracks | Those live input paths responded | Saved recording and later stability |
| Intended playback is heard at the named output | That output path worked during the check | All other destinations and recorded content |
| A stopped, saved scratch take replays each source separately | The checked take retained those paths | A full production session or timing certification |
| A bounded simultaneous-use interval is reviewed | The observed setup worked for that interval | Untested duration, reconnects or changed projects |

If recording is part of acceptance and authorized, record only the bounded cues into fresh intended tracks, stop, save and replay that exact take with live input no longer contributing. Inspect each source assignment and the recorded track content; hearing the person repeat a cue while playback runs is not saved-file evidence. Reopen the saved project when retained setup is required, distinguishing application-global device choices from project-stored track assignments.

Check a representative continuous simultaneous-use interval when the task depends on ongoing use. State its actual duration, conditions and listening/review coverage. A short onset check cannot support a long-session stability claim. If repeated common markers are already suitable and authorized, compare their relative placement near the beginning and end; separate a stable offset from a changing separation, and retain measurement uncertainty. Different unrelated sources cannot establish precise inter-device alignment from their waveforms alone. Do not promise sample-accurate or phase-coherent recording from enabled drift correction.

Attribute listening reports to the local person when no direct audio-perception capability is available. File metadata, meters and a successful Play command are not listening. If the requested recording or simultaneous-use check cannot be performed, deliver the configured/prepared stage with that exact remaining limit.

## 5. Preserve the result and recover from the failed boundary

Read back the final aggregate membership/order, rate, reference and correction state, followed by app input/output and track assignments. Leave the requested working setup intact. Stop temporary recording, monitoring and test playback; restore only temporary settings whose current values still match the task's changes, preserving later user edits.

An app reopen or device reconnect is needed only when requested or necessary to resolve the fault. Stop affected audio and protect work first. After any such transition, reidentify members and channels before recording again. Apple's [device-switching guidance](https://support.apple.com/guide/audio-midi-setup/if-audio-switches-to-a-different-device-ams0c519de39/mac) notes that a disconnected endpoint can cause Core Audio to choose another device. A surviving aggregate name is therefore insufficient evidence that the intended capture/output path survived.

Choose recovery by the observed failure:

- **Missing member or changed channels:** preserve the map and inspect the supported connection/current device state. Reconcile numbering after recovery; do not accept a substitute source silently
- **All tracks capture the same source:** inspect each app input assignment and mono/stereo choice against the map before changing clocks or gain
- **Meters respond but no desired playback:** inspect the selected output device and exact output channels, mute and monitoring. Do not add microphones or raise input gain to fix an output route
- **Clicks, dropouts, changing relative timing or engine errors:** stop the check and preserve the take/error context. Reinspect member availability, common rate, reference and correction, then any supported implicated app setting one at a time. These symptoms do not uniquely diagnose clock drift; do not hide them with edits or declare the hardware defective
- **Unintended speaker feedback or extra captured source:** stop/mute the agreed local path immediately, verify capture has ended and hold further use until routing is understood. Do not share the affected take as a cleared example
- **App rejects the aggregate:** record the exact consumer/version and supported limitation. Restore the prior app selection when safe; do not reset global audio configuration, install drivers or change the user's chosen app implicitly

Do not automatically delete existing aggregates or scratch takes. If removing the newly created candidate is authorized, first establish that no active app still relies on it, restore the prior supported endpoint and verify ordinary audio remains usable. Device removal, recording deletion and project cleanup have separate effects; a rollback should not erase unrelated work.

Return a concise handoff:

- Aggregate name and physical members, with separate input/output channel maps
- Final rate, reference and correction/sync states, plus relevant version-specific limits
- App device choices, required track/bus assignments and what persists globally versus in the saved project
- Checks actually observed, saved take/project if requested, listening attribution and continuous-use coverage
- Safe return/stop route, unresolved requirement and smallest next check

Use an honest stage such as prepared only, configured with live channels checked, or saved simultaneous path checked. Stop when the requested stage is supported, or when a specific compatibility, physical-access, permission or synchronization prerequisite prevents the next meaningful check. A reusable setup is not a production recording, universal compatibility claim or latency certification.

## Fictional, unexecuted illustration

An invented user wants two existing mono USB microphones available as separate tracks in a local recording app, while retaining an already-working headphone output. The app supports separate input and output devices. The proposed aggregate would include only the two microphones at a common supported rate; the headphone device would remain the app's separate output.

In hypothetical configuration notes, microphone Cedar maps to aggregate input 1 and microphone Maple to input 2, but both scratch tracks still select input 1. Two moving track meters would not satisfy separate-source acceptance. The correction would be to bind the second track to the displayed input 2 and then repeat distinct physical cues. A later change in member order would require a fresh map and assignment check, even if both track names remained unchanged.

If the hypothetical live cues passed but no saved take had been replayed, the result would be “live input paths checked; retained recording unverified.” If one microphone disappeared during the planned continuous check, the interval would be incomplete and the remaining endpoint would be reidentified before retrying.

This is an original illustration of decisions only. No microphone, audio device, clock setting, application, recording, playback, listening check or reconnection was operated or executed for it.
