# Spiricom Mark IV Audio Workbench

A dependency-free browser app recreating the documented thirteen-tone generator and providing local microphone recording. It is an audio reconstruction, not a complete RF Mark IV or a verified communication device.

## Use

Open `index.html` for tone generation, or serve the folder over localhost / HTTPS for microphone recording. Start with your device speaker volume low. Start tones, adjust individual levels, then optionally record the microphone. Stop recording to play back and download audio. Download the session log to preserve settings, changes, notes, and browser-reported input settings. Files stay in the current tab until downloaded. Keep the app in the foreground; mobile background recording is not guaranteed.

Microphone capture is not mixed digitally with the generated tones. It captures whatever reaches the chosen microphone/input. Echo cancellation, noise suppression, and automatic gain control are requested off, but browser/device processing may remain. Microphone audio is not routed back to the speaker.

## GitHub Pages

1. Create a repository named `spiricom-mark-iv` in the intended GitHub account. For a free personal account, use a public repository for Pages; check your plan if you require a private repository.
2. Upload `index.html`, `README.md`, and `.nojekyll` to its root and commit.
3. Under Settings → Pages, select Deploy from a branch, `main`, `/(root)`, then Save.
4. Use the URL displayed by GitHub after deployment. For the `missionaha` account and the suggested repository name, the expected URL is `https://missionaha.github.io/spiricom-mark-iv/`. This is a proposed destination, not confirmation of publication.

No build process, API key, server, or backend is needed. Do not upload private session recordings or logs into a public repository.

## Historical fidelity

Source: user's supplied *Spiricom Technical Manual*, Metascience Foundation (1982), Mark IV description, Fig. 11 and component list, PDF pages 32–34.

The listed tones are 131, 141, 151, 241, 272, 282, 292, 302, 415, 443, 515, 653, and 701 Hz. The app uses sine oscillators with equal initial amplitude and a fixed divisor of 13 to limit the sum. Relative levels are adjustable. The manual does not specify a complete amplitude/phase calibration; these defaults are implementation choices. The tone-only WAV is 10 seconds, mono 48 kHz / 16-bit PCM, with 20 ms fades at each end.

The historical system also used an AM RF signal generator around 29–31 MHz, separate transmitting and receiving antennas, an AM receiver, a speaker, and a microphone/recorder. Browser audio cannot supply the RF carrier or recreate the physical antenna gap. An external audio interface could feed a suitable instrument's modulation input after its input specifications are checked. A full RF build requires a separate hardware design and operating review.

The manual's claimed spirit communications are not established by recreating its tones. This app generates no words or voices and makes no attribution of recorded sounds.

## Technical scope

Web Audio API, MediaDevices getUserMedia, and MediaRecorder. Recording format is selected from supported WebM/Opus, MP4, or Ogg/Opus. No network requests, analytics, libraries, account, or remote storage. Tested in desktop Chromium with a synthetic microphone; actual iPhone and hardware-loop performance still require device testing.
