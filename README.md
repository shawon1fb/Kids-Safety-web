# website/

Static marketing and legal site for **Kids Safety: Parent Guide**. Plain HTML
and one stylesheet — no build step, no dependencies, no JavaScript.

| File | Purpose |
|---|---|
| `index.html` | Landing page |
| `privacy.html` | Privacy policy — the URL App Store Connect and Play Console need |
| `support.html` | Support page — the other required store URL |
| `terms.html` | Terms of use (iOS also falls back to Apple's standard EULA) |
| `styles.css` | Shared styles, app palette |
| `assets/icon.png` | 1024×1024 app icon |
| `assets/icon-512.png` | 512×512, used by the pages and as favicon |

## Preview locally

```bash
cd website && python3 -m http.server 8000
# open http://localhost:8000
```

## Publish

**GitHub Pages** — push this folder as the repo root (or as `/docs`), then
Settings ▸ Pages ▸ deploy from branch. URLs become
`https://<user>.github.io/<repo>/privacy.html`.

**Firebase Hosting** — the account already hosts `firabsecrud.web.app`:

```bash
firebase init hosting     # public directory: website
firebase deploy --only hosting
```

## After it is live

1. Put the privacy and support URLs into App Store Connect and Play Console.
2. Update the in-app links in
   `Smart Kids iOS/Smart Kids/Core/Legal/LegalLinks.swift` — the privacy URL
   there still points at `https://firabsecrud.web.app/privacy-policy`, and
   terms still resolve to Apple's standard EULA.

## Before publishing, check

- Contact address is `shawon0187@gmail.com` on all three pages. Swap it if a
  dedicated support address is wanted.
- `privacy.html` §1 says "the developer identified on its store listings" —
  replace with the legal entity name if one should appear.
- The privacy policy describes what the app actually does today: AdMob ads in
  the free chapter, Firebase Analytics/Crashlytics/Performance/Messaging,
  RevenueCat purchase status, everything else on-device. Re-check it whenever
  an SDK is added or removed, and keep it in step with
  `Smart Kids/Resources/PrivacyInfo.xcprivacy` and the App Store privacy
  labels in `RELEASE.md` §3.
