# Dubbline: product tour

Dubbline is a hosted, pay-as-you-go web app for AI video dubbing. This page walks through what a user does.

## 1. Start a dub

Drop in a video, then choose:

- the **original language** (or detect it automatically) and one or more **dub languages**;
- the **number of speakers** (or detect it);
- what happens to the **original audio**: keep the music and effects and replace only the voices (the default), or replace everything;
- optionally a **glossary** and a translation direction, or an uploaded **transcript** (SRT, VTT or CSV) to use instead of automatic transcription.

Before anything is spent the page shows the **estimated cost** and the balance, and asks the user to confirm they have the rights to the video and consent to cloning its voices. Files upload straight to object storage, in parallel parts when large. Videos can also be imported from a direct link.

## 2. Watch it work

The project page shows a Prepare, Adapt, Finish stepper with live progress. The user can leave and come back, or cancel. If cancelled before voices are generated the credits are returned.

## 3. The studio

Once a language is dubbed, the project opens in an editor laid out like a video editor:

- **Monitor:** plays the latest render with the current line as a subtitle and the speaker who is talking, with a switch between the dub and the original that keeps the playhead.
- **Timeline:** one lane per speaker with real waveforms of the dub voices, plus a lane for music and effects. It zooms from the whole video to a ten-second window. Line edges can be dragged or nudged by a tenth of a second.
- **Lines panel:** the original line, an editable translation, a speaker picker, per-line audio preview, and badges for edited lines, lines shortened to fit, lines that run into the next one, and lines with no usable voice sample.
- **Speakers panel:** rename speakers, set the gender used for translation, choose a cloned or stock voice, merge two detections of the same person, or add a speaker the detector missed.
- **Per-line controls:** a delivery cue (whispering, excited, calm, sad, angry, laughing, shouting), keep the original audio, split at the playhead, merge with the next line.
- **Regenerate:** select lines and regenerate their voice or retranslate them. Edits themselves are free; the toolbar shows any credit cost before a re-voice runs.

Keyboard shortcuts cover play/pause and moving between lines.

## 4. Languages

Each language is a tab with its own translation, takes and export. Adding another language reuses the prepared lines and voices, so it only runs the per-language stages. Speaker and timing edits apply to every language.

## 5. Export

Re-rendering after edits re-runs only fit, mix, render and quality. Nothing is re-voiced. Downloads per language:

- dubbed **MP4**, dubbed **WAV**, the **dub voices** alone, and the **stems** (music and effects, original voices);
- **SRT** and **VTT** subtitles;
- a **script CSV** (`id, start, end, speaker, source, translation`) that can be translated elsewhere and **imported back**, where it counts as the user's own edit and is never rewritten;
- a **quality report**.

## 6. Credits and billing

Pay as you go: credit packs, or a single video, with no subscription. Credits do not expire, failed dubs are refunded, and subtitles, editing and re-exporting are included. The user sees their balance and a ledger of every charge and refund.

## 7. Built for agents

People can hand a video to their AI agent. The same HTTP API the web app uses is available with **API keys**, a **command-line client** and an **MCP server** (local and hosted).

- Every entry point separates **quote** from **spend**: `dub` uploads and returns a price without spending anything, and `start` spends it.
- Dubbline never pays for anyone. An agent can create a checkout link, but only the person can open it and pay.
- The rights and voice-consent confirmation must come from the person.
- Keys cannot create or revoke keys, so a leaked key cannot mint more access.

## Languages

Source languages: 99 (via the speech-to-text provider). Target languages: 80+ (via the voice provider), grouped in the new-dub screen by quality tier, with Japanese, English and Chinese in the top tier.

## Deliberate v1 limits

Lip-sync, teams, undo and a personal voice library are not included yet.
