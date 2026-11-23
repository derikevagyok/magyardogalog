# Magyar dogalog

A 12.c közös naplója arról, melyik magyarórán írtunk dogát. Az oldal GitHub Pages-en fut, az adatok Firebase Firestore-ban vannak.

## Fájlok

- `index.html` – maga az oldal
- `firebase-config.js` – a Firebase projekt adatai
- `firestore.rules` – ki mit írhat az adatbázisba (ezt a Firebase konzolba kell bemásolni)

## Beüzemelés

1. [console.firebase.google.com](https://console.firebase.google.com) → új projekt.
2. **Build → Firestore Database → Create database** (régió pl. `eur3`, production mode).
3. **Firestore Database → Rules** fül: töröld ki, ami ott van, másold be a `firestore.rules` teljes tartalmát, majd **Publish**.
4. **Build → Authentication → Get started → Sign-in method → Anonymous → Enable.**
5. **Project settings (fogaskerék) → General → Your apps → Web (`</>`)**: a `firebaseConfig` értékeit másold be a `firebase-config.js` fájlba.
6. Commit + push. GitHub-on: **Settings → Pages → Build and deployment → Deploy from a branch → `main` / `(root)` → Save.**
   Pár perc múlva elérhető: `https://<felhasználónév>.github.io/magyardogalog/`

Ha később módosítod a `firestore.rules` fájlt, a 3. lépést meg kell ismételni, mert a GitHub nem tölti fel a Firebase-be.

## Biztonság

Olvasni bárki tudja, aki ismeri a linket. Írni csak névtelen bejelentkezéssel lehet (ez automatikus, fiók nem kell), és a szabályok csak érvényes óra-bejegyzéseket engednek: helyes dátum, státusz `igen`/`nem`/`elmaradt`, téma legfeljebb 120 karakter. Aki ismeri a linket, az tud írni és törölni is.
