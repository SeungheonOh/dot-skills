---
name: convert-image-color-profile
description: "Convert an existing SDR raster image to a specified ICC color space and deliver a correctly tagged derivative, preserving its source interpretation and separating conversion from profile assignment and soft proofing. Use for color-space delivery, not creative recoloring, display calibration or complete print production."
---

# Convert an image's color space without losing its meaning

Deliver the requested image derivative with an established source interpretation, an explicit destination profile and a checked saved-file result. A filename containing “sRGB,” a changed profile label or a pleasing preview does not establish that the pixel values were converted correctly.

Use [create-visual-asset](../create-visual-asset/SKILL.md) for creative image changes, [calibrate-desktop-display](../calibrate-desktop-display/SKILL.md) for measured display setup, and [prepare-print-production-package](../prepare-print-production-package/SKILL.md) for a complete printer-specific package. This workflow handles ordinary ICC-managed SDR raster derivatives. Camera-raw development, HDR tone mapping, video transfer functions, spot-color separations and custom profile creation need their own supported methods; do not treat them as simple RGB profile swaps.

## Establish the conversion contract

Identify the exact source revision and requested destination: a named RGB space for an image consumer, or a supplied output profile for a specified process. Record required format, pixel dimensions, precision, transparency and whether editable layers must survive. Preserve the original. For a batch, retain a source-to-output mapping and inspect each file's interpretation rather than assuming one camera, extension or folder means one color space.

Ask only for missing choices that change the result. “Make this suitable for print” does not identify a CMYK profile, paper or printing condition. Obtain the applicable provider specification rather than selecting a familiar profile by name. An ordinary screen derivative should not acquire a printer conversion merely because a print version might be useful later.

Use the available application's supported color-management and export path. Inspect its actual version and relevant documentation before relying on menu names or format support. Do not install a profile manager, change system-wide working spaces, alter a display profile or upload private artwork to a converter as an incidental step. Local preparation does not authorize transmission to a printer or publication.

## 1. Establish what the source numbers mean

Before accepting an import prompt, distinguish the file's embedded profile from the application's working-space default and current document interpretation. Opening a file can trigger an automatic conversion. Record whether that occurred and retain the original source identity; an already converted working document is not the untouched input.

Inspect the color model, precision and embedded profile through the supported file/application information. Use a profile's actual identity and relevant details, not just a basename that another profile could share. Preserve conflicting or unreadable metadata as a finding. Do not infer a source space from the image looking washed out, the file being a JPEG, or the destination requirement.

For an untagged image, seek provenance such as its original export settings or a confirmed authoring-space statement. An application fallback is not recovered provenance. [GIMP's assignment documentation](https://docs.gimp.org/3.0/en/gimp-image-color-profile-assign.html) shows that an untagged image can receive a built-in sRGB interpretation on import; that default may be wrong for the source. If the source space remains unknown, hold an appearance-preserving conversion claim. A user-approved assumption may support a clearly conditional derivative, but it must not be reported as recovered original color.

Separate three actions:

- **Assign:** give existing sample values a profile interpretation. Use this to repair missing or demonstrably incorrect interpretation only when the correct source meaning is established.
- **Convert:** transform from the established source interpretation to the destination space using the selected color-management method.
- **Embed:** retain the profile describing the saved samples in the output file. Embedding a destination label without the matching transformation is not conversion.

[Adobe's profile workflow](https://helpx.adobe.com/photoshop/desktop/adjust-color/color-profiles/change-a-documents-color-profile.html) distinguishes assignment, which retains color numbers, from conversion and destination tagging. Do not assign the destination first and then convert: that substitutes the intended output interpretation for the real source. Removing a source tag is not a neutral repair either.

## 2. Choose one explicit transformation path

Confirm the source profile, destination profile, color-management engine and available conversion options immediately before applying the operation. Retain rendering intent, black-point compensation and any precision/dithering choice that materially affects reproducibility. [GIMP's conversion guide](https://docs.gimp.org/3.0/en/gimp-image-color-profile-convert.html) exposes current and destination profiles separately, along with rendering intent and black-point compensation; the last-used destination is not evidence of the requested one.

Use the requested production settings when supplied. Otherwise choose settings appropriate to the supported application, profiles and intended result, explaining important tradeoffs rather than asserting a universal best intent. If alternative settings are compared, derive each candidate from the same established source, not from another already-converted candidate. Do not promise preservation of every saturated source color in a smaller output gamut.

Identify which stage owns the conversion: the document operation or a documented export operation. Then inspect the remaining stages for additional conversions or profile stripping. A document already in the destination space must not later be interpreted as though it still contains the original source-space values. Record intentional intermediate conversions when unavoidable rather than hiding them behind an export preset.

Keep monitor, document and proof profiles distinct. A monitor profile belongs to the display path, not to a portable image's source or destination merely because that screen looks right. A simulated printer view is also not the converted derivative. [GIMP's color-management preferences](https://docs.gimp.org/3.0/en/gimp-prefs-color-management.html) distinguish managed display from soft proofing through a simulation profile. Inspect any proof view separately, with its actual settings, and leave physical matching unclaimed.

If layers or transparency are present, establish whether the selected application can preserve the required structure and composite appearance through this particular conversion/export. Do not flatten an editable deliverable or silently choose a matte background to fit a format. A separately approved flattened derivative can be appropriate; keep its master and chosen background distinct. Color conversion is not permission to retouch, sharpen, resize or change exposure.

## 3. Save and inspect the derivative, not just the working view

Save to a new destination with the requested format and profile embedding enabled where supported. If the consumer requires an untagged file, establish its documented assumed space and make the loss of explicit interpretation visible. Do not strip profiles just to reduce file size or avoid a warning.

Reopen the exact saved candidate without silently converting it again on import. Inspect the actual embedded profile or other documented color declaration, color model, sample precision, dimensions, orientation and transparency. A document status label can reflect an import fallback, so distinguish that label from evidence present in the file.

Compare the original under its established interpretation and the candidate under its own interpretation in the same color-managed viewing conditions. Inspect neutral tones, gradients, saturated regions and meaningful fine detail, plus transparent edges on appropriate backgrounds. For a conversion-only request, check that crop, wording and geometry remain unchanged. A preview or screenshot cannot establish numerical color accuracy on a remote or uncharacterized display.

Use the transformation record and saved-file inspection together. Pixel equality is not the general acceptance criterion because a valid conversion can change values; changed values alone do not establish the right transform. Lossy encoding and precision changes are separate effects and should not be mistaken for proof of conversion. Likewise, converting back to the source space is not a guarantee of reversibility or fidelity.

If the intended consumer is available and its use is authorized, open the delivered copy there and check its documented color-management behavior and any warnings. Keep consumer acceptance separate from file inspection. An unchecked browser, printer, recipient screen or online service remains unchecked even when the editor's preview looks plausible.

## Recover and hand off

When a candidate has the wrong interpretation, missing tag, unintended matte or unexplained appearance shift, isolate the import, conversion or export stage before retrying. Return to the untouched source or last established working state; do not repeatedly assign profiles to a damaged derivative until it looks familiar. If the source interpretation is unresolved, stop the dependent conversion rather than inventing certainty.

Deliver the actual derivative and a short record of source interpretation/provenance, destination profile, relevant conversion/export choices and observed checks. Identify any assumed input space, material gamut/appearance tradeoff or unavailable consumer check. Keep the original available and label held candidates so they cannot be mistaken for approved output. Stop after the requested preparation and authorized delivery, not after changing unrelated application defaults or ordering a proof.

## Fictional, unexecuted illustration

A fictional author supplies an untagged RGB TIFF and its export record establishing Adobe RGB (1998). They request an sRGB-tagged screen derivative without cropping. The editor initially displays an sRGB default for the imported TIFF.

The proposed path establishes the documented Adobe RGB interpretation without treating the fallback as source evidence, then converts a separate copy to the requested sRGB profile and saves it with matching tagging. Merely assigning sRGB would leave the original numbers under a different interpretation. A soft-proof toggle would change the preview, not establish the requested saved derivative.

Acceptance would require readback of the saved interpretation, preserved geometry and a managed comparison, with any consumer limitation stated. Without the export record or other source evidence, the conversion would remain conditional or held rather than “color corrected.” This authored example reports no executed image edit, conversion, export, rendering, application check, repository test or physical proof.
