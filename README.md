# Duotone Anatomy Icon Set

Hand-drawn duotone icons for body systems, vitals, labs and medical records — built for a chronic
illness pacing app, and free for anyone to use.

**This repository is the source of truth for these icons.** If a copy elsewhere disagrees with this
one, this one is right.

37 icons: body systems (immune, autoimmune, kidney, liver, lungs, thyroid, GI, skeletal,
reproductive, metabolism), vitals (heart rate, HRV, blood pressure, weight, steps, sleep,
thermometer), records (labs, medications, providers, events, records, confirmation, alert), and
interface marks (info, chart, chart-question, AI, home, bubble, spoon).

## How the two tones work

Every icon is a single colour plus a lighter interior, and both come from **one** value you set:

```svg
<path fill="currentColor" ... />                  <!-- the outline, full strength -->
<path fill="currentColor" opacity=".29" ... />    <!-- the interior, 29% -->
```

So `color: #B3C7E6` on the parent, or a single-colour tint on Android/iOS, gives you a two-tone
icon rather than a flat one. There is no second colour to keep in sync and nothing to theme twice.

## If you are converting these to Android VectorDrawables

**Check the aspect ratio.** These icons are not square — viewBoxes include `544 x 544`,
`754.55 x 544` and `563.56 x 544`, among others.

A `<vector>` maps its viewport onto `android:width` × `android:height` on each axis
*independently*, so declaring a non-square icon into a square box silently stretches it. We shipped
the AI robot 24% too wide for a week before anyone measured it. Either keep the declared size in
proportion, or pad the viewport to square and centre the artwork in a translated `<group>`.

`opacity` on a path becomes `android:fillAlpha`, which survives an `SRC_IN` tint — so the two tones
still work once converted.

## Naming

Lower case, hyphen separated, no spaces. Body-system and metric icons carry a `-duotone` suffix;
interface marks do not.

## Licence

Use them for whatever you like.
