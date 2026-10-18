# Dubbline: measuring quality

An engine change should be shown to make dubs better, not just different. Dubbline has a **quality bench** for that.

## How it works

The bench dubs a fixed set of reference clips and scores the results. The clips cover one, two and three speakers, a music bed, a fast talker and a non-English source. Each can carry hand-labelled speaker turns, which enable the speaker score. Runs are saved with the date or commit, and two runs can be compared side by side.

A full run of six short clips costs a couple of dollars with live providers, and the harness itself can run for free against offline stand-ins.

## Metrics

| Metric | Meaning | Better |
| --- | --- | --- |
| Speaker error | Share of word time given to the wrong speaker, under the best mapping to the hand-labelled truth | lower |
| Long takes | Share of takes longer than the time their line may use, after shortening | lower |
| Overruns | Lines that still run into the next line | lower |
| Words cut | Words lost to truncation. Always zero: the engine never truncates | 0 |
| Round-trip error | The dub is transcribed back and compared with the translation it should say (word error rate) | lower |
| Cost per minute | Measured provider usage per minute of video | lower |
| Wall time | Time for the whole dub | lower |

## Why it exists

The first-generation pipeline had known structural problems: speakers were assigned round-robin, lines that were too long were truncated, and the background audio was lost. The rewrite addressed those by design (real speaker detection, a fit loop that never truncates, and separated stems). The bench is how future changes are checked against that bar, and its first full run on the current engine becomes the baseline.

## In every dub

Each exported language also ships a **quality report** listing the status of every line, which were shortened, which were sped up, and which overrun, so the user can see exactly where to look.
