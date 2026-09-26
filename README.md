# Orb Tanker - Privacy Policy

This repository hosts the public privacy policy page for the **Orb Tanker** Android game.

The policy is served via GitHub Pages at:

**https://KISSWARDMULTIMEDIA.github.io/orbtanker-privacy/**

The URL above is entered in:

1. **Google Play Console** - App content page (Privacy policy field). Play requires a publicly reachable policy URL for every app.
2. **Inside the app** - Settings > Privacy Policy screen, which carries the same wording.

## Publishing on GitHub Pages

The page is served from the repository root (`index.html`), so the root URL works.

- Create this repository (public) under the KISSWARDMULTIMEDIA account, with no README or licence file.
- Push `index.html` to the repository root (and this README).
- Enable Pages:
  - Settings > Pages > Build and deployment
  - Source: Deploy from a branch
  - Branch: main / folder: / (root) > Save
- Wait a minute or two, then confirm the policy loads at the URL above.

To push local changes:

```powershell
cd "C:\Users\DAVID\Desktop\orbtanker-privacy"
git add index.html
git commit -m "Update privacy policy"
git push
```

## Keeping it current

When the policy changes, update `index.html` and push. GitHub Pages updates automatically.

Note that `index.html` carries a "Last updated" date in its header - bump it whenever the wording changes.

## Design notes

- The page is fully self-contained: no cookies, no analytics, no third-party fonts, scripts or stylesheets. The only outbound link is to Google's Privacy Policy.
- Styling is inline so the page cannot break if a CDN is unreachable.
- The dark navy theme matches the game's own palette.

## Contact

David Kissward - kisswarddavid2@gmail.com
