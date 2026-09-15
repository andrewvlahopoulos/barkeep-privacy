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

## The landing page, and why it is not at `/` yet

`home.html` is the marketing page. It is deliberately **not** `index.html`, because
`https://homebarkeep.com/` is currently the privacy policy — and that exact URL is load-bearing in
four places:

1. App Store Connect's **Privacy Policy URL** field.
2. `PaywallView.swift` — the in-app Privacy Policy link, required by Guideline 3.1.2.
3. `PrivacyLegalView.swift` — Settings → Privacy & Legal.
4. The **App Store description**, which lists it beneath the subscription terms (added 2026-09-13
   after review rejected 1.0 for a missing Terms of Use link).

BarKeep 1.0 build 387 is in App Store review as this is written. If the root started serving a
marketing page, a reviewer tapping "Privacy Policy" in the app would land on it — a Guideline 3.1.2
failure, and a second rejection days after the first.

### The swap, once 1.0 is approved

Do all of it, in order, or not at all:

1. `git mv index.html privacy/index.html` — the policy keeps working at a stable URL.
2. `git mv home.html index.html` — the landing page takes the root.
3. Update the **App Store Connect** Privacy Policy URL to `https://homebarkeep.com/privacy/`.
4. Update `privacyPolicyURL` in **`PaywallView.swift`** and **`PrivacyLegalView.swift`**, and ship
   that build. Until it ships, installed copies still point at `/`.
5. Update the **App Store description**'s Privacy Policy line.
6. Update `home.html`'s own footer link from `/` to `/privacy/`.

Step 4 is the one with a lag: an app already on someone's phone keeps the old URL until they update.
Keeping a redirect at `/` is not possible on GitHub Pages without a real page there, so the safe
sequence is to ship the app change *first*, let it propagate, and only then move the root.

### Assets

`assets/fonts/` holds Source Serif 4 Semibold, the app's own display face (SIL OFL, licence
included). Body text uses the system stack — it loads instantly and matches the privacy and support
pages, so the three pages read as one site.

`assets/shelf.json` is generated from BarKeep's `seed_cocktails.json`: a 15-ingredient shelf and the
15 recipes fully reachable from it, using the app's real ingredient-matching rule (category, or the
first `acceptableNames` entry where one exists, so sweet and dry vermouth stay distinct). Every drink
the demo lists is genuinely makeable from the selected bottles.
