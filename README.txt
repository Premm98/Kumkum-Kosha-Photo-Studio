Studio Backdrop — PWA (installable web app for Android & iOS)
============================================================

WHAT THIS IS
------------
A Progressive Web App: the full Studio Backdrop tool, installable to the home
screen on both Android and iOS with no app store. Once installed it opens
full-screen like a native app and works offline (after the first load).

CONTENTS
--------
  index.html            The app (self-contained shell)
  manifest.webmanifest  App name, icons, colors, standalone display
  sw.js                 Service worker (offline app-shell cache)
  icons/                App icons (192, 512, maskable, apple-touch)

HOW TO PUBLISH (required — PWAs must be served over HTTPS)
----------------------------------------------------------
A PWA cannot be installed from a file on disk; it must be hosted on an HTTPS
URL. Any static host works — pick one:

  • Netlify Drop  — drag this whole folder onto https://app.netlify.com/drop
  • Vercel        — `vercel deploy` in this folder
  • GitHub Pages  — push this folder to a repo, enable Pages
  • Cloudflare Pages / Firebase Hosting / any static host

Serve the folder as-is (keep index.html, manifest, sw.js and icons/ together
at the same path). That's it — no build step.

HOW USERS INSTALL IT
--------------------
  Android (Chrome):  open the URL → menu (⋮) → "Install app" / "Add to Home screen".
                     Chrome also shows an automatic install prompt.
  iOS (Safari):      open the URL → Share button → "Add to Home Screen".
                     (On iOS, install must be done from Safari.)

After install it launches full-screen from the home-screen icon.

NOTES
-----
• Background removal downloads an AI model (~40 MB) on first use, then it's
  cached for offline reuse.
• Everything runs on-device — photos never leave the phone.
• Output images are 1080 × 1440 JPG (Myntra apparel portrait spec).

GOING FURTHER (optional, native store apps)
-------------------------------------------
This same folder can be wrapped into real App Store / Play Store binaries with
Capacitor or PWABuilder (https://www.pwabuilder.com) if you later want store
distribution. Not required for install-from-browser.
