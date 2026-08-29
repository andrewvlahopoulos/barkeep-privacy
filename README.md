# BarKeep — Privacy Policy

The published privacy policy for **BarKeep**, a home-bar inventory app for iPhone.

Live at **https://andrewvlahopoulos.github.io/barkeep-privacy/**

## Why this is its own repository

The policy has to be publicly readable — Apple's App Store Review Guideline 5.1.1 requires a
reachable privacy policy URL, and the app itself links it from the paywall and from
Settings → Privacy & Legal. BarKeep's own source repository is private, and GitHub Pages can't
publish from a private repository on a free account, so the policy lives here instead. Only the
policy is public; the app's source stays private.

**This repo is the source of truth for the policy.** BarKeep's repo points here rather than
keeping a second copy, so the two can't drift apart.

## Updating it

Edit `index.html` and push to `main`; GitHub Pages redeploys automatically. Bump the
"Last updated" date whenever the content changes — the policy itself promises that.

If a change alters which Settings screen a control lives on, or what data leaves the device,
check that the app's own copy agrees: `PaywallView.swift` and `PrivacyLegalView.swift` both link
this page, and App Store Connect holds the same URL in its app metadata.
