# Illustration: a container is more than its password prompt

This is an original fictional, unexecuted illustration. All names, paths, sizes and observations below are invented to explain decisions. No image was created, password entered, file copied, application opened or setting changed.

## Bounded request

A fictional workshop organizer wants a reusable encrypted working container on one Mac for three ordinary reference files. The organizer wants to enter the password when opening it and leave it ejected after setup. The selected source folder must stay unchanged. Sharing, source deletion, password storage, whole-disk encryption and backup configuration are outside the request.

The proposed new backing file is `Local Containers/Workshop Reference.dmg`; the mounted volume would be `Workshop Reference`. The illustrative payload is:

- `agenda.txt`, 1 KiB
- `reference/room-layout.pdf`, 320 KiB
- `reference/supply-list.csv`, 8 KiB

The requested capacity is 128 MiB, subject to actual native format support, overhead and host free-space checks. These fictional payload sizes sum to 329 KiB; that arithmetic does not establish an image's actual allocation or usable space. A harmless marker would be additional declared content. The backing file would live outside the source tree and outside any synchronized or shared folder.

## Decisions before creation

The workflow would first establish the actual destination and the installed Mac's writable image options, then review the selected filesystem, encryption and manual-opening requirement. The user would give the required security-configuration approval and perform password creation privately. No password or password hint appears in the record.

The phrase “protect these files” would not make the originals disappear. The handoff would explicitly retain them and avoid claiming that every plaintext copy had been removed. If that broader outcome were essential, it would remain a separate unresolved requirement.

## Two boundaries that change acceptance

Suppose the paper scenario describes a created encrypted candidate, a correctly mapped mounted volume, a successfully rewritten marker and all three target files matching stable source baselines. That would support creation, writing and initial copy checks only.

1. The first ordinary eject is described as successful. Reopening the backing file immediately mounts it without the requested password interaction. The workflow would hold the manual-opening requirement. It would not conclude that the image lacks encryption or delete a saved credential. A user decision about the existing opening behavior is needed before claiming the requested gate works.
2. After that user-controlled issue is resolved, suppose another fictional check describes a password prompt, cancellation without a mount, user-controlled successful opening and the same marker/payload readback. An open PDF document then prevents final ejection. The report would retain the positive reopen evidence but say that the image is still mounted. It would ask to save/close that document normally before trying ordinary eject again. It would not label the finished state locked.

Neither branch permits deleting the originals, killing an application, forcing an unmount or uploading the image. If actual observation later established normal ejection, that could close the final-state gap; the invented narrative does not establish it.

## Illustrative handoff state

For the second branch before the busy document is closed, an honest paper handoff would read:

“The scenario describes one encrypted image with three reconciled payload files and one declared marker. Reopening and the marker's retained update are described as successful after user-controlled unlocking. Final ejection is unresolved because a document remains open. Original source files remain in their existing location. Second-Mac use, independent backup recovery, application cache contents and elimination of plaintext copies are unverified.”

This text demonstrates conclusion boundaries only. It is not a live setup report, a measured outcome or evidence that any password, encryption option, file, mount or application was inspected.
