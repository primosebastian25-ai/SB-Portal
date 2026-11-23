# Gabay sa Pag-setup gamit ang PHONE lang

Libre ang lahat. Kailangan: phone na may Chrome (Android) o Safari (iPhone), at ang Google account ng opisina.

**Tip:** sa Firebase at GitHub, i-on ang **Desktop site** (Chrome: menu ⋮ > Desktop site; Safari: "aA" > Request Desktop Website) para lumabas lahat ng button.

---

## 1. I-extract ang zip
- **Android:** buksan ang **Files** app > Downloads > pindutin ang `sb-portal-phone.zip` > **Extract**.
- **iPhone:** buksan ang **Files** app > Downloads > pindutin ang zip. Kusa itong mag-e-extract.

Dapat may 9 file: `index.html`, `firebase-config.js`, `firestore.rules`, `manifest.json`, `sw.js`, 3 icon na `.png`, at ang gabay na ito.

## 2. Gumawa ng Firebase project
1. Pumunta sa **console.firebase.google.com** at mag-sign in gamit ang Google account ng opisina.
2. **Create a project** > pangalan: `sb-romblon-portal` > puwedeng i-off ang Analytics.
3. **Build > Authentication > Get started** > **Email/Password** > Enable > Save.
4. **Build > Firestore Database > Create database** > location **asia-southeast1 (Singapore)** > **production mode**.
5. Gear icon > **Project settings** > sa ibaba, pindutin ang **`</>`** (Web app) > pangalan `SB Portal` > Register.
6. May lalabas na `firebaseConfig = { apiKey: ..., ... }`. **Huwag munang isara** o i-screenshot ito. Kakailanganin mo ito sa Hakbang 4.

## 3. Gumawa ng GitHub account at i-upload ang app
1. Pumunta sa **github.com** > **Sign up** (libre). Pumili ng username, hal. `sbromblon`.
2. Pindutin ang **+** (itaas) > **New repository** > pangalan: `portal` > **Public** > **Create repository**.
3. Pindutin ang link na **"uploading an existing file"** (o **Add file > Upload files**).
4. Pindutin ang **choose your files** > piliin ang **lahat ng file** sa na-extract na folder > hintaying ma-upload > **Commit changes**.

> Public ang code, pero walang makakabasa ng **datos** dahil kailangan ng login at ng access mula sa admin (firestore.rules).

## 4. Ilagay ang Firebase config
1. Sa GitHub repository, pindutin ang file na **firebase-config.js** > icon na **lapis (Edit)**.
2. Palitan ang bawat `PALITAN` ng value mula sa Firebase (Hakbang 2.6). Panatilihin ang mga panipi `" "`.
3. **Commit changes**.

## 5. I-on ang GitHub Pages
1. Sa repository: **Settings > Pages**.
2. Sa **Branch**, piliin ang **main** at **/ (root)** > **Save**.
3. Maghintay ng 1–2 minuto at i-refresh. Lalabas ang link, hal. **`https://sbromblon.github.io/portal/`**. Ito na ang link ng portal.

## 6. Ikabit ang seguridad sa Firebase
1. **Authorized domain:** Firebase > **Authentication > Settings > Authorized domains > Add domain** > ilagay ang `sbromblon.github.io` (palitan ng username mo).
2. **Rules:** sa GitHub, buksan ang **firestore.rules** > pindutin ang **Copy raw file** (icon na dalawang parisukat) > sa Firebase **Firestore Database > Rules**, burahin ang laman, idikit, at **Publish**.

## 7. Gawing admin ang sarili mo
1. Firebase > **Authentication > Users > Add user** > email at password mo > kopyahin ang **User UID**.
2. **Firestore Database > Data > + Start collection**:
   - Collection ID: `users`
   - Document ID: idikit ang **User UID**
   - Mga field (lahat ay string): `role` = `admin`, `name` = pangalan mo, `email` = email mo
   - **Save**

## 8. Buksan at i-install
1. Buksan ang link mula sa Hakbang 5.3 at mag-login.
2. **I-install:** sa Android, pindutin ang **Install app** o menu ⋮ > **Add to Home screen**. Sa iPhone, pindutin ang Share > **Add to Home Screen**.
3. Para magdagdag ng konsehal: Firebase > Authentication > **Add user** > kopyahin ang UID > sa portal, **More > User Access > Grant access**.

---

## Kung may babaguhin sa app sa susunod
Sa GitHub, buksan ang file > lapis (Edit) > **Commit changes**. Mag-a-update ang portal sa loob ng 1–2 minuto.

## Mga file sa meeting
I-upload sa **Google Drive app** > i-share sa mga email ng konsehal > **Copy link** > sa portal, buksan ang meeting > **Edit meeting > Add document** > idikit.
