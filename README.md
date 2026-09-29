# Recall: record and take notes at the same time

Recall is a personal app that runs on your laptop and phone. It does four things:

- **Records audio** from lectures, sermons and meetings.
- **Writes a live transcript** as people speak.
- **Timestamps your notes.** Each note you type is linked to the moment you *started* typing it. Tap the time chip and the recording plays from that moment.
- **★ Mark** saves an "important moment" with one tap.
- **Syncs to your own Google Drive**, so the laptop and phone see the same recordings.

It costs nothing. There's no server and no subscription, and nobody else can see your data.

---

## 1. Put it online (free, about 10 minutes)

1. Create a free account at **github.com**.
2. Click **+ → New repository**. Name it `recall`, set it to **Public**, and click **Create repository**.
3. On the new repo page, click **"uploading an existing file"**. Drag in everything from this folder: `index.html`, `manifest.webmanifest`, `sw.js`, `README.md` and the `icons` folder. Then click **Commit changes**.
4. Go to **Settings → Pages**. Under *Build and deployment*, choose **Deploy from a branch**, then **main**, then **/(root)**, and click **Save**.
5. Wait 1–2 minutes. Your app is now live at:
   **`https://YOUR-USERNAME.github.io/recall/`**

The repo holds only the app's code. Your recordings and notes never go to GitHub.

## 2. Install it on your devices

| Device | How |
|---|---|
| **Mac, Chrome** | Open the link and click the install icon in the address bar. You can also use ⋮ → *Cast, save and share* → *Install page as app*. |
| **Mac, Safari** | Open the link, then **File → Add to Dock**. |
| **iPhone** | Open the link in **Safari**, then Share → **Add to Home Screen**. |
| **Android** | Open the link in Chrome, then ⋮ → **Add to Home screen / Install app**. |

The first time you record, allow microphone access.

## 3. Turn on Google Drive sync (free, once)

1. Go to **console.cloud.google.com** and create a project called `Recall`.
2. Go to **APIs & Services → Library**, search for **Google Drive API**, and click **Enable**.
3. Open **Google Auth Platform** (it may be labelled *OAuth consent screen*):
   - Get started, then choose **External** as the audience.
   - Enter the app name `Recall` and your Gmail address.
   - Under **Audience → Test users**, add your own Gmail.
4. Go to **Clients → Create client** and choose **Web application**. Under **Authorized JavaScript origins**, add
   `https://YOUR-USERNAME.github.io` with no `/recall` and no trailing slash.
5. Copy the **Client ID**. It ends in `.apps.googleusercontent.com`.
6. In Recall, open **⚙ Settings**, paste the Client ID and tap **Connect & sync now**. Do this on each device.
   Google may warn that it *hasn't verified this app*. That's expected for a personal app, so tap **Continue**.

Everything is saved in a **"Recall Notes"** folder in your Drive: one `.json` file with the notes and transcript, plus one `.m4a` audio file per recording. Recall can only see files it created itself.

The sign-in lasts about an hour. After that, tap the cloud button to sync again.

---

## Transcribe a recording afterwards

Open a recording, go to the **Transcript** tab and tap **Transcribe audio**. A speech model (Whisper) turns the whole recording into a timestamped transcript. It runs on your own device and is free.

- **Choose the language** right on the recording's Transcript tab. Tap the language name next to the button (for example *English (UK) ▾*) and pick *Русский*. Each recording keeps its own language, and the one you picked last becomes the default for new recordings. If you change it after making a full transcript, a **Redo** button appears.
- **Choose a model** in Settings. *Balanced* is the default. *Most accurate* gives better text (especially for Russian) but is a bigger download, so it's best used on your Mac.
- **The first run downloads the model.** After that it works offline.
- **It takes a while:** several minutes per hour of audio on a laptop, longer on a phone. Keep Recall open until it finishes. You can cancel, and it keeps whatever it has done so far.
- **Import** (the ⬆ button on the home screen) brings in audio files, several at once if you like.
  - **From Voice Memos on iPhone:** open the memo, then Share (or ⋯) → **Save to Files**. Then in Recall tap ⬆ and pick it. iPhone doesn't let web apps appear in the Share menu, so this two-step route is the shortest.
  - **On your Mac:** drag a memo straight out of the Voice Memos app and drop it anywhere on the Recall window.

## Folders (one per subject)

- On the home screen, tap **+ New folder** and name it after the subject, for example *Thermodynamics*.
- When a folder is selected, new recordings and imports go straight into it.
- To move a recording, tap the folder name under its title.
- With a folder selected you can also **Download all as text** (every recording in that subject in one file), **Rename** it or **Delete** it. Deleting a folder keeps the recordings and moves them to *No folder*.
- **For Claude:** when Drive sync is on, each recording is also saved as a readable text file at **Google Drive → Recall Notes → *Subject name* → *date title*.md**, with your notes and both transcripts. In a Claude chat for that subject, ask Claude to read the latest ones from *Recall Notes/Subject* in your Drive.

## Listening back

Playback keeps going when you leave a recording. A small player appears at the bottom with play/pause and ±10 s, and tapping its title takes you back to that recording. On iPhone and Mac it also shows up in the lock screen and Control Centre controls.

## Tips

- **Transcript language:** pick it on the recording's Transcript tab. Choose *Русский* for lectures in Russian and *English* for English ones. While recording, changing it switches the live transcript straight away.
- **Best transcript quality:** Chrome on your laptop, with the laptop reasonably close to the speaker. Live transcription needs internet, but the audio records fine offline.
- **On phones**, keep Recall open with the screen on. iPhones don't let any website use the microphone in the background, so if you switch apps, Recall pauses and resumes when you come back. It adds a note where the gap is, so your timestamps stay correct. For long recordings where you must switch apps, record in Voice Memos instead. On some Android phones, the live transcript and the recorder can't use the microphone at the same time. The audio still records; only the transcript stops.
- **Storage:** 1 hour is about 30 MB. Google Drive's free 15 GB holds hundreds of hours. To free up space on your phone, open a recording and choose **⋯ → Remove audio from this device**. It stays in Drive and can be downloaded again.
- **Exporting:** **⋯ → Download as text (.md)** or **Copy notes & transcript** gives you a clean, timestamped version. You can paste it into anything, or into Claude to summarise.
- **If the app crashes or the tab closes mid-recording,** the audio saved so far is recovered automatically the next time you open Recall.
- **To update the app later,** upload the new `index.html` and `sw.js` to the same GitHub repo, then fully close and reopen Recall.
