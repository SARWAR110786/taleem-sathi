# Taleem Sathi — Website + App

People's School Thatta ka student project. Is folder mein poori website aur chat app hai.

```
index.html                 ← one-page website (team, features, download)
app/                       ← chat app (installable, connects to the n8n agent)
  index.html
  manifest.webmanifest
  sw.js
  icons/
assets/                    ← logo, favicon (put team photos in assets/team/)
downloads/                 ← put taleem-sathi.apk here (step 2)
```

The app talks to the live agent at:
`https://hahoiu.app.n8n.cloud/webhook/taleem-sathi`
(change `WEBHOOK` near the top of the script in `app/index.html` if it ever moves).

---

## Step 1 — Put the website online (free, ~5 minutes)

1. Make a free account at **netlify.com** (sign up with Google or email).
2. Open **app.netlify.com/drop**.
3. Drag this whole `site` folder onto the page.
4. Netlify gives a link like `https://random-name.netlify.app`.
   Rename it: **Site configuration → Change site name** → e.g. `taleem-sathi` → `https://taleem-sathi.netlify.app`
5. Open the link on your phone and test: **App kholein** → chat should answer.

## Step 2 — Make the Android APK (no Android Studio, no Play Store)

1. Open **pwabuilder.com**.
2. Paste your app address: `https://taleem-sathi.netlify.app/app/` → **Start**.
3. Click **Package For Stores → Android → Generate Package**.
   - Package ID: `pk.peopleschoolthatta.taleemsathi`
   - App name: `Taleem Sathi`
   - Keep the default signing option ("Create new").
4. Download the zip. Inside are:
   - the `.apk` file → rename it to **taleem-sathi.apk**
   - `signing.keystore` + `signing-key-info.txt` → **keep these safe forever** (needed for every future update).
   - `assetlinks.json` → put it in this folder at `.well-known/assetlinks.json` (removes the browser bar inside the app).
5. Put `taleem-sathi.apk` into the `downloads/` folder and drag the `site` folder onto Netlify again
   (**Deploys → drag and drop**).

The website's download button switches on automatically once the APK is there.

## Step 3 — Real team details

Open `index.html`, find the `<!-- TEAM -->` section and change names, roles and lines.
For photos: put square pictures in `assets/team/` and replace the initials, e.g.
`<div class="face"><img src="assets/team/ayesha.jpg" alt="Ayesha Memon"></div>`

## Updating later

- Change the agent (menus, replies): edit the n8n workflow — app updates instantly.
- Change the look of the app or website: edit the files, drag the folder onto Netlify again.
  The installed APK loads the app from the website, so students get the update without reinstalling.
