# BUFFER / LOOP · Random Glitch Music Player

[中文说明](README.md) · [Français](README.fr.md)

Turn a stalled stream into a happy accident. Load a local track, randomly loop the audio you just heard, then return to the song. A self-contained static player with no dependencies or build step.

## Play on your computer

1. Download and extract the project. Open `index.html` in Chrome, Edge or Safari.
2. Click **Choose audio**, select a local audio file and press **Play**.
3. Leave **Auto glitch** enabled, or click **Glitch now** to trigger a loop manually.
4. Click **Resume track** to end a glitch early and continue from the frozen position.

`random_glitch_player.html` is an identical portable copy. Either HTML file works on its own, offline. Keep both copies in sync when editing.

Default settings capture the last 0.5–3 seconds, repeat it 2–6 times, and trigger roughly every 6–14 seconds of normal playback. The song position freezes during a glitch. A glitch cannot trigger until enough audio is available at the start. Adjust the interval, loop length and maximum repeats to taste.

Includes pause, seeking, volume, a spectrum display and a glitch log. Keyboard shortcuts: **Space** to play/pause, **G** to glitch, **R** to resume. Shortcuts leave focused buttons and inputs to their normal keyboard behavior.

## Languages

The first visit uses your browser's preferred language: Chinese locales show Simplified Chinese, French locales show French, and other locales show English. Switch with **中文 / English / Français** at the top of the page. The introduction, controls, hints, status and logs all change without interrupting playback.

The choice is kept in the URL fragment, without cookies or browser storage. Share `index.html#lang=en` or `index.html#lang=zh` (French: `index.html#lang=fr`) to select a language explicitly. On GitHub Pages, append `#lang=en` or `#lang=zh` to your site's URL. All translations are bundled and work offline.

## Local audio and privacy

GitHub stores the player source code; GitHub Pages serves the player webpage. Neither needs your songs. Each visitor selects their own local file.

The player reads files with `File.arrayBuffer()` and decodes them with Web Audio's `decodeAudioData()` inside the browser. It has no upload endpoint, analytics, remote fonts, CDN, cookies, browser storage or service worker. Audio is held in memory, not saved by the player. Reloading the page requires selecting the file again. File names and logs appear only on the current page.

The bundled content security policy blocks network connections with `connect-src 'none'` and blocks form submissions. Opening a GitHub Pages link still requests the webpage from GitHub, and the hosting service may record webpage visits. That is separate from uploading audio. Opening the downloaded HTML needs no network. Recheck privacy if you add external scripts.

## Publish on GitHub Pages

This project is ready to publish; no repository has been created or pushed, and no live site has been deployed.

1. Create a GitHub repository, for example `random-glitch-player`.
2. Upload this folder's **contents** to the repository root, including both HTML files, all three READMEs, `LICENSE`, `.gitignore` and `.nojekyll`. Make sure `index.html` is at the root.
3. Go to **Settings → Pages → Build and deployment → Source → Deploy from a branch**.
4. Select your branch (usually `main`) and **/(root)**, then click **Save**.
5. When deployment finishes, open the link shown in Pages settings. It typically looks like `https://YOUR-USERNAME.github.io/random-glitch-player/`.

No npm, build command or custom workflow is required. See [GitHub's official publishing instructions](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site). GitHub Free supports Pages for public repositories; other availability depends on the account plan.

Keep personal music out of the repository. `.gitignore` excludes common audio formats and music directories, but it cannot stop manual uploads through the GitHub website or remove files Git already tracks.

## Compatibility and limits

- MP3, WAV, M4A, AAC, Ogg and FLAC support depends on the browser and encoding. Try an ordinary MP3 or PCM WAV if decoding fails.
- The full track is decoded into memory. Long recordings can use substantially more memory than their original file size.
- Use a full browser rather than a phone's file preview. Background tabs, locked screens and power saving may suspend audio or delay the interface and automatic triggers.
- Protected streaming services such as Spotify and Apple Music are not supported. No songs are included and the player does not export mixes.
- Short fades soften loop boundaries, but randomly cut slices may still produce audible changes.
- To use the player reliably offline, download the HTML instead of relying on the browser cache.

## License

The player code is provided under the [MIT License](LICENSE). You may use, modify and distribute it while retaining the copyright and license notice. The license does not cover imported songs, recordings or other third-party content, or grant rights to distribute them.

## Validation

Checked in headless Edge on Windows using a generated 12-second WAV: decoding, play/pause, manual and automatic glitches, automatic and manual recovery, seeking, overlapping file selections, recovery after an invalid file, end of track and replay. No page script exceptions occurred; the only page requests were local HTML loads.

Also checked language detection, switching languages while playing, preservation of file names and parameter values, translated logs, language selection after reload and the English layout at a 390-pixel viewport. This does not cover every browser, codec or mobile device, and is not a listening test.

To inspect local processing yourself, clear the browser developer tools' Network panel, import a song and play it. There should be no audio upload requests. Distinguish the initial webpage request on GitHub Pages from audio processing. The local HTML also works with the network disconnected.

French language detection, switching among all three languages during playback, translated glitch logs, the language choice after reload and the French mobile layout were also checked.
