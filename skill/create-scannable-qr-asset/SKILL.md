---
name: create-scannable-qr-asset
description: "Create reusable QR artwork for an approved URL or ordinary text, with exact payload checks, preserved quiet zones and verification of the final exported asset. Use for a handout, slide, sign or label; payment, login, credential-bearing and application-specific provisioning codes need their own workflow."
---

# Create and verify a scannable QR asset

Deliver a real encoded QR file and its readable destination or text. Visual resemblance to a QR code is not useful evidence: the saved result must decode to the approved payload after the export and placement steps that matter for the user's use.

## Establish the payload and use

Identify the exact URL or text, requested file format, screen or print use, available space and any required label. Determine whether the output is a standalone asset or a code placed into a supplied document. A request for one code does not authorize redesigning the whole document or publishing it.

Use the user-supplied destination, not a guessed homepage. Preserve query parameters, fragments and meaningful characters. If a link is visibly incomplete, conflicting or includes a temporary authorization token, stop that payload and resolve it. Do not silently replace it with a shortener, tracking redirect or different scheme.

This workflow covers ordinary URLs and text. Do not apply it unchanged to payment instructions, login links, Wi-Fi passwords, recovery secrets or device-enrollment payloads. Their data handling, protocol semantics and consequences require a purpose-specific authorized route. A QR image does not conceal the encoded information.

For several codes, make a small payload-to-label/file map before generation. Do not put private payloads in filenames, shell history, public logs or a third-party QR website. Use local generation and decoding where supported; sending data to a generator or decoder service needs the applicable authorization.

## 1. Freeze the exact value

Keep the approved payload separately from its human-readable label. Remove accidental surrounding whitespace only when that intention is clear; otherwise ask rather than alter significant text. Preserve the original string for later comparison.

For an ordinary URL:

1. Inspect its scheme, host, path, query and fragment without activating an application handler
2. Check that the display label accurately describes the destination
3. If a destination check is useful and safe, read the public page through authorized access; report redirects or access requirements separately from the encoded value
4. Do not visit a private, one-time or state-changing link merely to see whether it works, and do not alter access permissions to make a target public

A successful decode proves which value the symbol contains. It does not prove that a website is trustworthy, will stay available, or is accessible to every recipient. Avoid "permanent" or "works for everyone" claims.

## 2. Encode with an available deterministic tool

Inspect available QR encoders and decoders before promising a verified asset. Use a standards-aware encoder, not generated artwork, a hand-drawn approximation or a screenshot of another code. Prefer ordinary QR Code Model 2 for this workflow unless the user specifies a supported alternative; do not silently substitute Micro QR or a proprietary variant. [DENSO WAVE describes these distinct QR types](https://www.qrcode.com/en/codes/).

Choose an error-correction level suited to the use. Level M is a reasonable starting point for a clean ordinary handout, not a universal requirement. Higher correction can increase symbol density; it is not a license to cover arbitrary areas with a logo. [DENSO WAVE's guidance](https://www.qrcode.com/en/about/error_correction.html) explains the size/correction tradeoff. Keep the data modules and finder patterns intact by default.

Use the encoder's documentation to set symbol family, encoding, correction and output options explicitly where they affect the result. For non-ASCII text, establish the byte encoding and any ECI handling; verify that the intended decoder recovers the exact text. Do not force an incompatible numeric/alphanumeric mode or truncate content to fit a chosen version.

For example, [Segno's official creation guide](https://segno.readthedocs.io/en/latest/make.html) distinguishes `make_qr` from automatic Micro QR selection and documents automatic error-correction boosting. If using it, record the actual generated version and correction level, not just the requested minimum. Other installed encoders are acceptable when their behavior is understood. Installing a package is a separate action requiring the applicable authority.

Record only what helps reproduce or diagnose this asset: encoder/version, payload identity, symbol type, module count, encoding, actual correction level and export settings. Do not invent these values from a filename or visual estimate.

## 3. Preserve geometry in the saved artwork

Keep a clear quiet zone of at least four modules on every side for the ordinary QR symbol used here. Place labels, borders, crop marks and artwork outside it. [DENSO WAVE's area guidance](https://www.qrcode.com/en/howto/code.html) gives this requirement and the size calculation.

For an `N`-module symbol and a quiet zone of `q` modules on each side, the complete square spans `N + 2q` modules. If the complete square is `W` millimeters wide, each module is `W / (N + 2q)` millimeters. State whether a requested physical size includes the quiet zone; do not accidentally fit only the data region into that space.

- For raster delivery, use a lossless format such as PNG and an integer number of pixels per module. Avoid smoothing or lossy compression of the matrix
- For scalable delivery, use real vector paths/geometry in SVG or PDF, retaining an explicit background and correct dimensions. An embedded low-resolution bitmap is not a scalable vector code
- Use dark modules on a plain light background by default. Transparency, inversion, gradients, rounded modules and overlaid logos need separate verification and should not be introduced merely for decoration
- When placing a code into a page or slide, preserve its aspect ratio, quiet zone and intended size. Verify the exported page, not only the original asset

Consult the chosen encoder's serializer options for units, background and scale; [Segno's serialization reference](https://segno.readthedocs.io/en/latest/serializers.html) distinguishes these controls. Measure the resulting file rather than assuming the requested option survived conversion.

Do not claim a universal minimum print size or scanning distance. Module size, printer output and reader capabilities all matter, as [DENSO WAVE's module-size guidance](https://www.qrcode.com/en/howto/cell.html) explains. Use the available area sensibly and disclose when the actual print/scanner combination has not been tried.

## 4. Decode the exact final deliverables

Reopen each saved asset. Render vector files and any final document at the intended output scale with an appropriate renderer; do not execute supplied active SVG content or fetch its external resources merely to make a preview. Inspect for missing background, cropped margins, distorted modules, labels entering the quiet zone and unexpected page scaling.

Use an independent decoder that reads the actual image pixels, rather than the encoder's original matrix or stored payload. Decode every distinct code from each delivered representation. For a multi-code page, reconcile decoded locations with the payload-to-label map so that a valid code under the wrong label cannot pass.

Compare the recovered payload with the approved value without forgiving punctuation, whitespace, query changes or Unicode normalization. When exact bytes matter, use a decoder that exposes raw payload bytes and compare those too. If the decoder returns only text, describe the check as a decoded-text match, not proof of byte equality.

For printed use, an actual-size print and representative device scan provide evidence unavailable from a desktop render. Perform them only when the devices and actions are available and authorized. Inspect the scanner's decoded value without activating the link or another action. If physical scanning is unavailable, deliver the digitally checked asset with that specific print check still pending; do not claim physical scan success.

## 5. Recover from failures without changing the destination

- **No decode:** check the final background, quiet zone, aspect ratio, resolution and actual module size. Re-export from the matrix at an appropriate scale; do not repeatedly resample a blurred image
- **Wrong decoded value:** fix the source-to-payload mapping or encoding and regenerate all affected outputs. Do not excuse a mismatch because the browser redirects to a similar page
- **Payload exceeds capacity or is too dense for the space:** explain the constraint. Offer more space or a user-approved shorter payload; do not create a new short-link account or split the data into several codes without agreement
- **Standalone asset works but document export fails:** repair placement/export within scope and decode the complete exported document again
- **Decoder or rendering capability is absent:** provide the candidate if useful, naming the missing verification. Do not label an encoder success or attractive preview as a verified scannable result

After any modification to payload, colors, scale, framing or placement, repeat affected final-output checks. Keep the last verified candidate separate from unfinished variants.

## Deliverable and completion

Return the requested asset and any requested placement file, plus readable payload/label information, dimensions including quiet zone, and a concise verification note. A simple request should receive a simple bundle, not an unsolicited dashboard or hosted service.

Completion requires the correct approved payload, intact geometry and margins, a matching decode from the exact final file where decoding is available, and explicit limits for unperformed device/print checks. Publication, printing orders, uploading to a new service or changing the destination's sharing settings require their own authorization. Preserve any supplied source document.

## Illustrative example, not executed

Request: "Make an SVG and PNG QR code for https://workshop.example/guide?lang=en#checklist. Put 'Workshop guide' beneath it, with a clear white background. It will occupy a 40 mm square on a handout, excluding the label. Don't publish anything."

A later execution would freeze that exact URL, choose a standard QR encoder, obtain its actual module count, and calculate module width from the 40 mm total including quiet zones. It would export both formats from the same matrix, keep the label outside the quiet zone, and decode the PNG and rendered SVG independently to the full URL including `?lang=en#checklist`.

The handoff would report actual file dimensions and decode results, with physical printing/scanning marked unperformed if unavailable. No symbol version, scan result or file-creation claim is implied by this example; it is an unexecuted specification.
