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

## Tips

- **Transcript language:** set it in Settings. Choose *Русский* for lectures in Russian and *English* for English ones.
- **Best transcript quality:** Chrome on your laptop, with the laptop reasonably close to the speaker. Live transcription needs internet, but the audio records fine offline.
- **On phones**, keep Recall open with the screen on. It asks the phone to stay awake, but if you switch apps, iPhones pause the microphone. On some Android phones, the live transcript and the recorder can't use the microphone at the same time. The audio still records; only the transcript stops.
- **Storage:** 1 hour is about 30 MB. Google Drive's free 15 GB holds hundreds of hours. To free up space on your phone, open a recording and choose **⋯ → Remove audio from this device**. It stays in Drive and can be downloaded again.
- **Exporting:** **⋯ → Download as text (.md)** or **Copy notes & transcript** gives you a clean, timestamped version. You can paste it into anything, or into Claude to summarise.
- **If the app crashes or the tab closes mid-recording,** the audio saved so far is recovered automatically the next time you open Recall.
- **To update the app later,** upload the new `index.html` to the same GitHub repo.
