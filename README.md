# CozAlyze — Continuous Opening (Scene 1 + animation result)

Stamps: SCENE 1 v19.71 continuous opening, TROPICAL v18.48 continuous opening,
SIDEREAL v19.41 continuous opening. Engine e27, ?v=27, AUDIO_VER 18.
Reveal routes ?v=1848 / ?v=1941.

## What this is

The full opening now runs into the animation-result page as one piece. The
living-page architecture is unchanged: the index is the only page that ever
loads. The card tap fades the choice bed and shows the chosen reveal file in a
fullscreen iframe, which adopts the index's already-running audio context, so
sound is alive from the reveal's first frame through to REVEAL MY CHART.

The only routing change is that the Tropical door now opens the v18.47
animation-result build (hero video, framed planet table, ascendant frame)
instead of the old v18.45 card layout. Sidereal is unchanged apart from its
engine tag and stamp.

Flow: opening -> location search -> Earth flight -> birth date -> birth time ->
Tropical/Sidereal doors -> whisper -> tap to reveal -> chart drawing ->
REVEAL MY CHART -> result page -> unlock -> pricing.

## Engine e27

The Earth-arrival cue (07_earth_arrival.wav) is retired. The wav is no longer
in the master, so it is out of FILES and DUCKS. Its call site in Scene 1 stays
where it is and is now a silent no-op — play() drops any cue with no buffer —
so the moment plays dry instead of throwing a 404 on every load. No other cue
changed, and no wav content changed, so AUDIO_VER stays 18.

## STILL NEEDED — 5 of your art files

These are referenced by the v18.48 result page and are NOT in this package.
Drop them into the repo root alongside everything else:

  asc-frame.jpg    (9-slice border, slice 60 — the ascendant frame)
  unlock.jpg       (the tappable unlock button art)
  icon-sun.jpg
  icon-moon.jpg
  icon-career.jpg

Without them the result page renders but those five slots come up broken.

The 12 gold glyph PNGs ARE included — sliced fresh from your glyph sheet,
recoloured #CCA466 on transparent, 256px square, named glyph-aries.png
through glyph-pisces.png to match TR_GLYPH_FILE.

calc-sky.mp4 is referenced but marked preload="none" with genesis bypassed
since v19.52. It is harmless to leave absent.

## Deploy

Drop the whole folder into the repo root, single commit, wait for the green
Actions run. Verify the corner stamps before testing anything:

  index          v19.71 continuous opening
  tropical       v18.48 continuous opening
  sidereal       v19.41 continuous opening
  engine         snd e27 running

Every recent test has trailed the delivered build by one version, so check the
stamp first.
