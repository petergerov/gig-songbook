# Changelog

What's new in each version of Gig Songbook.

## 1.4.1

- New: Gig Songbook inside Loopy Pro. Add the MIDI plugin Gig Songbook in Loopy Pro, or another AUv3 host, and your lyrics and chords appear right in its window — all songs, or a setlist with its sections, transposed the way you set them.
- Change songs without leaving Loopy: tap the arrows, or send MIDI from a footswitch or a Loopy button. Program Change n picks song n+1 of the list, CC 80 goes to the next song and CC 81 to the previous one, and CC 82 and CC 83 scroll the lyrics down and up. Loopy buttons can do the same through the plugin's parameters. Loopy remembers the setlist and song with your project. Switch it on in the plugin, and the lyrics scroll on their own while Loopy plays, paced by the song's length or Loopy's tempo, and an expression pedal can move through the song with the plugin's Scroll Position parameter.
- New: MIDI pedals and keyboards. In Settings → MIDI Control, tap Learn next to Next Song, Previous Song, Scroll Down or Scroll Up and press the pedal, key or button you want — in Performance and Rehearse it changes songs, scrolls the lyrics or turns score pages. Program Change picks a song from the setlist. Bluetooth MIDI pedals pair right on that screen, and the Loopy Pro plugin follows the same settings.
- Try everything first: every Pro feature — chord transposition, the Online Song Catalog, imports and exports, stem separation, the practice tools and the new plugin — is now free for 7 days from install. Settings shows the day the trial ends.

## 1.4.0

- New: everything works without internet — on every device. Recordings, score pages and stems added on another device used to stay in iCloud until you opened them, and iOS could take them away again to save space. Now each device downloads them on its own and keeps them, so a song you added on your iPhone plays on your iPad on stage with no network.
- Settings → Media on This Device lets each device choose. Keep Everything on This Device, the default, works without internet. Download When Needed saves space: files from your other devices load when you open them. Before switching to Keep Everything you see how much will be downloaded and how much space is free. Switching never deletes anything, and files you add on a device always stay on it.
- After updating, each device starts downloading the files it is missing. On a device that is short on space, choose Download When Needed first.
- New: make a setlist available offline. On a device set to Download When Needed, turn on Available Offline in a setlist, and just that set's recordings, pages and stems come down and stay — the rest of the library stays in iCloud. Turning it off frees the space again. Each device decides for itself.
- Every setlist shows whether it is ready to play without internet: a check when everything is on the device, how many files are still loading, and a clear warning when there isn't enough space — with how much to free up — or when a file is missing on every device.
- When you delete a song on one device, your other devices now remove their copies of its recording, pages and stems too. Files another song still uses stay.
- Fixed: after separating a song's stems again, another device could keep playing the old stems. Every new separation now gets files of its own.
- A song now keeps one set of saved stems. To separate it again — into a different number of stems, for example — tap Delete Stems first, then Separate Stems; Regenerate with Selected Mode is gone. In the player, Delete Stems removes all of the song's saved stems whichever layout you're on, and exporting new ones waits until they are deleted.

## 1.3.12

- Fixed: on Mac, the Songs list was missing two of its toolbar buttons — the globe that opens the Online Song Catalog, and the ••• menu for importing and exporting songs. Both are back next to +.
- Fixed: Storage Cleanup now updates by itself. While songs or media are still downloading from iCloud, it checks again on its own every few seconds and shows the list as soon as everything has arrived — no more tapping "Check Again".
- Online Song Catalog: songs now come in with their synced lyrics. Add the recording and the current line follows the music — no separate sync step.
- The catalog marks songs that are already in your library and asks before adding a second copy. After importing, you see how many songs were added.
- Manual Tap Sync no longer interrupts you. Tapping a line sets its time right away — no more "Timing Warning" when the time comes before or after a neighbouring line.

## 1.3.11

- New: importing a file now shows you what it would change, before it changes anything. Every song in the file is matched against your library and sorted into New, Changed and Identical — so re-importing your own backup no longer just says "already in your library" and stops there.
- A table at the top counts each group, and how many of each you have ticked to import. The groups start folded, so a file with hundreds of songs opens on that overview.
- Each changed song tells you what actually differs: lyrics, key, labels, notes — and the media, in plain numbers. "Stems: none → 4 files (48.3 MB)". "Audio: not downloaded → 4.2 MB". "Images: 1 file → 2 files", down to pages that only changed order. Each one also says whether the copy in the file or the one in your library was edited more recently.
- Compare any changed song side by side: your version and the file's, lyrics, chords and notes line by line with every change marked, and the pages in order, with added, removed and moved ones highlighted. Below it, the song exactly as the import would leave it.
- You decide song by song. New songs are ticked for you; anything that would overwrite a song you already have is yours to tick, one at a time, from the comparison, or a whole section at once. Nothing outside your ticks is written.
- Overwriting a song keeps media the file doesn't carry, so a backup made before you separated a song's stems can never take those stems away. And it never touches your playback settings: transposition, stem mix, tempo and scroll speed stay as you set them.
- Fixed: an import used to write every audio, image and stem file in the file over your own copies — even when it reported that it had imported nothing at all. Only the files belonging to the songs you tick are written now, and only where they genuinely differ.
- Importing a setlist uses the same screen, with the setlists listed at the top and a switch for replacing ones you already have by that name.
- The free stem & practice-tools trial is now 7 days from install.

## 1.3.10

- New: Storage Cleanup. Settings → Maintenance → Storage Cleanup shows you everything your library no longer uses — recordings, score pages and stems left behind by songs you deleted — with what each file is and how much space you get back. You see the list first, and nothing is removed until you confirm it. Earlier versions tidied up on their own at every launch; now it happens when you decide.
- It also spots the opposite: a song pointing at a page, a recording or stems that are no longer on any of your devices. Clearing that broken link is offered the same way — and the list waits until iCloud has finished syncing, so a file that is still on its way is never taken for a lost one.
- Fixed: deleting one song's stems could take another song's with them. A copied or imported song can share a stem folder with the song it came from, and "Delete Stems" emptied it for both, on every device. Stems another song still uses now stay where they are.
- Faster syncing: every song and setlist now syncs as its own small file. Editing one song sends a few kilobytes instead of your whole library, two devices can work on different songs without overwriting each other, and a single song that one device can't read no longer holds up the rest.
- Settings → Maintenance → Restore Image Attachments has been removed. Score pages that are no longer attached to a song stay safely in storage, and Storage Cleanup never offers them for removal.

## 1.3.9

- Important fix: score and lyric images could disappear from all of your devices after an iCloud sync. On a device that hadn't downloaded them yet, a cleanup routine mistook the not-yet-downloaded images for leftovers and removed them from iCloud — and a second routine then removed the now-empty page references on every other device too. Both routines are fixed: nothing that is only waiting to download is ever treated as leftover, and a local clean-up can no longer delete anything on your other devices.
- New: Settings → Maintenance → Restore Image Attachments. If pages have gone missing from your songs but the image files are still there — after restoring a backup, for example — this puts them back on the right songs automatically, in the right page order. It only ever adds pages, never removes any, tells you if something couldn't be matched, and the result syncs to your other devices.
- Fixed: exports could quietly leave out your media. Exporting from a device that had received its songs by sync produced a file with every song but none of the images, audio, or stems — with nothing to indicate it. Exports now fetch what's only in iCloud first (showing the download progress), and if something still can't be included, they say so and name the songs it belongs to, before you save the file.
- Fixed: a setlist could lose songs across devices. If a song couldn't be read on one device, that device removed it from your setlists and the removal spread to the others. A song is now only removed from a setlist when it was actually deleted.
- Safer syncing: if part of your library can't be read on a device, that device now pauses its iCloud uploads and shows a short notice, instead of saving an incomplete copy over the shared one.

## 1.3.8

- New: 6-stem separation. Split a track into Drums, Bass, Other, Vocals, Guitar, and Piano — in addition to the existing 2-stem and 4-stem options — with the same realtime playback, mixer, and offline export you already know. Uses a separate on-device AI model (~123 MB, downloaded on first use).
- New mixer: every stem now shows its instrument icon and its waveform, with the part you have already played highlighted so you can see at a glance where you are in each part. Tap an instrument to mute or unmute it. For levels, tap its speaker for a comfortable full-width slider, or just hold the speaker and slide up and down — the waveform grows and shrinks as you do.
- On iPhone the mixer waveforms stay compact (about 30% shorter) and no longer jump taller when you press Play.
- The mixer now sits directly on the player bar, so you can start, stop, skip, and scrub while the stems stay in view.
- Original playback gets a waveform too: pick Original in the mixer and you see the track's own waveform with your position in it, and set its volume the same way as a stem — tap the speaker for a slider, or hold and slide.
- Pitch shifting now moves the whole mix, drums included, so everything stays perfectly in time when you transpose.
- New tempo and pitch controls: tap − or + to step exactly where you want, and see what it means — the song's BPM at the current tempo, and the key you land in when you transpose. Tap the value to reset it. Pitch can be changed while the song plays; tempo is set while playback is paused.
- Fixed: playback could occasionally come up as loud noise after stopping and starting again — most often when you had just changed the tempo. Sound now stays clean across stop/play.
- Fixed: saved 2/4/6-stem mixes could sound out of time after quitting and reopening the app. Exported stems now stay locked together from the first beat.
- Fixed: realtime stems could drift apart across stop/start, go-to-start, or pausing while the player was rebuffering. Starts stay locked, go-to-start no longer restarts separation, and a pause during rebuffer stays paused until you press Play.
- Fixed: a song separated into 6 stems could also be played as "4 stems", using the six-stem files — where the "other" track no longer contains guitar and piano. Each layout now plays only its own stems, and the picker offers only the layouts you have actually exported.
- Tapping a stem layout you haven't exported yet no longer starts a separation and playback by itself — it waits for Play.
- Fixed: an export that failed showed nothing at all. Failures are now reported, with the reason.
- Tidier mixer: Original / 2 / 4 / 6 stems stays at the top, tempo and pitch sit right above the tracks they affect, and a larger close button replaces the old Done.
- Fixed: with realtime separation, repeatedly stopping and starting (or adjusting pitch and tempo) could drift the playhead away from the music. The player now follows the audio exactly.
- Fixed: rewinding to the start during realtime separation could start a second separation over the top of the running one. Play now simply resumes; only Cancel resets it.
- Fixed: pausing during a rebuffer could let the song start playing again on its own while the transport still showed paused.

## 1.3.7

- Fixed: loading the built-in demo setlist could fail — the download pointed at an outdated address. It now downloads from a new, reliable location, so the one-tap demo works again on first launch and from Settings.

## 1.3.6

- Fixed: a song created on one device could show a dead Play button on your other devices — the audio file was still in iCloud and its download never started. The player now starts the download automatically, shows "Downloading audio…", and Play works the moment the file has arrived.
- Score images synced from another device now download automatically too: pages that used to show "Image not available" now show "Downloading image…" and appear as soon as each page arrives.
- Fixed: on a new device (or after reinstalling), a song's saved stems could show "Downloading stems…" forever, even after the files had actually arrived from iCloud. The player now tracks the download, automatically restarts stalled transfers, and switches to your stems the moment they're ready.

## 1.3.5

- Fixed: changing the tempo while a song was playing could knock the audio out of sync. The tempo slider is now paused-only — a short hint in the mixer explains it, and it unlocks the moment you pause.
- Realtime stems: when a song plays through to the end, you can now jump back and listen again right away — the separated audio stays ready, no need to run the separation again from the start.
- Seeking back during realtime stem playback now resumes instantly from the already-separated audio, without a short rebuffering pause.
- Smoother lyrics on stage: the performance screen now does far less work while music plays, so lyrics-follow and scrolling stay fluid and use less battery — most noticeable on long songs with many chords.

## 1.3.3

- Better realtime stems on recent devices: iPhone 14 Pro and newer, and iPad M1 and newer, now use the full-quality separation model for realtime playback too — so stems sound as good live as the exported versions. (These devices download a slightly larger model, ~75 MB.)
- Sharper offline stems on iPhone 12 and newer: these models now use the full-quality separation model (a ~75 MB download) with graphics-processor acceleration when you export stems, so separated tracks sound better. Realtime playback still needs iPhone 14 Pro or newer.
- Faster realtime preparation, now running on the graphics processor on supported devices, with an automatic fallback if needed.
- Clearer "Realtime preparation": when you start realtime playback the player shows a blinking "Realtime preparation" until the music begins, and Play waits instead of looking tappable — no more accidental double-tap.

## 1.3.2

- Practice tools for rehearsing: slow a song down (or speed it up) without changing its pitch, shift the pitch up or down in semitones, and set an A-B loop right on the seek bar to drill a tricky passage on repeat. Tempo and pitch are remembered per song, and per song within a setlist.
- Original volume: the mixer now has a volume slider for the original track too, not just the separated stems.
- Smoother mixer: the tempo, pitch, and volume sliders now glide without lag or stutter.
- Cleaner stem playback: once you've exported stems, the app just uses them — the confusing "Prefer realtime" switch is gone.
- The free stem & practice-tools trial is now 27 days from install.

## 1.3.0

- Locked sets keep their sound: a locked setlist now plays each song with the exact stem mix you set up — Original, 2 stems, or 4 stems, with your muted parts and levels — instead of reverting to the original track. Editing stays locked, so the mix can't change mid-gig; it just plays.
- Set sections: split a setlist into "Set 1", "Break", "Encore" and more — each section shows its own song count and length. Add a divider from Add Section or by swiping a song, then drag songs and dividers freely, even across sections.
- Gig timing: see the total length of every set in your setlists, and during a performance a subtle clock shows the current section, time elapsed and remaining, and whether you're running over or ahead of plan.
- Undo a delete: deleting a song now shows a 7-second Undo banner with a countdown — tap it to bring the song back exactly where it was, including in every setlist it was part of.
- Easier to delete a song: long-press a song for a Delete option, or tap Delete Song at the bottom of the editor — and deleting from the editor takes you straight back to your song list. (All still protected by the Undo banner above.)
- Cleaner lyrics from imported audio: when an audio file's lyrics are stored with karaoke-style timestamps, those are now used for synced lyrics instead of cluttering the plain lyrics text.
- Tapping a song inside a setlist now opens the song (not the gig), so you can't start a performance by accident — that view is read-only, and you launch a set from the Play Set button or the play button on any song row to start from there. Edit mode is now a clean reorder-and-organize mode.
- Song editor: the score-image section is now "Images (Score)", placed right under Lyrics, with Add from Files and Add from Photo Library.
- Send feedback in-app: Settings now starts with a Feedback section — file a feature request, bug report, or general feedback without leaving the app. You can optionally include your app version, iOS version, and device model to help us track things down.
- Smoother, freeze-free performance: the app no longer stalls while iCloud loads your library at startup or in the background, and starting a track plays without the brief hitch some songs had on first tap — heavy work now happens off the main thread, so the screen stays responsive.

## 1.2.9

- Smoother editing: reordering songs, toggling, and quick edits no longer freeze or show a spinner while iCloud is syncing in the background.
- Your changes now save instantly on your device and upload to iCloud a moment after you finish — no mid-edit hitches, and edits no longer briefly snap back.

## 1.2.8

- Fixed: reordering songs in a setlist could snap back after a couple of seconds while iCloud was syncing.
- Fixed: labels added in Settings could vanish or flicker while iCloud was syncing.
- Paste as New Song: copied lyrics anywhere? A one-tap paste button beside the Songs search bar creates a prefilled song — title, artist, key, BPM and lyrics detected automatically. Uses the system paste control, so there's no paste-permission pop-up.
- Sort your library: by Title, Recently Modified (new and imported songs at the top under "Today"), Artist, or Label — your choice is remembered.
- Cleaner, Contacts-style lists: no chevrons, and tapping anywhere on a row opens it.
- Start a set faster: every setlist now has a Play button right on its row, so you can launch the set without opening it.
- Songs inside a setlist now show the same details as your library, numbered in order; tap one to start the set from there.
- The song view now lists every setlist the song appears in.

## 1.2.7

This release makes iCloud sync between your devices significantly more reliable.

- Deleted songs and setlists now stay deleted — a deletion made on one device can no longer be brought back by another device's sync.
- Re-importing a song you previously deleted now sticks: it no longer silently disappears again on the next sync.
- Removed audio files, stems, and score images no longer reappear after syncing.
- Importing a backup now counts as your newest copy everywhere — imported songs win on all synced devices instead of being overwritten by older data.
- A single damaged song record can no longer prevent the rest of your library from loading.
- Songs now show when — and on which device — they were last edited; give this device a name in Settings → This Device (stored locally, never synced).
- Tapping a song now opens a read-only view — metadata, audio preview, score pages (swipeable when the song uses the image view), and stage-styled lyrics — with Edit and Rehearse one tap away, so you can no longer change a song by accident while browsing. In setlists, a new play button on each row starts the set from that song.
- Long-press a song in your library for quick actions: Rehearse, Edit, and Add to Setlist.
- Under-the-hood sync engine overhaul for safer startup merging across devices on different app versions.
