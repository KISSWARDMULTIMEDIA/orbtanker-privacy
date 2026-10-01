# Orb Tanker - Privacy Policy and app-ads.txt

This repository hosts the public web properties for the **Orb Tanker** Android game:

| File | Purpose |
| --- | --- |
| `index.html` | The privacy policy page. |
| `app-ads.txt` | Declares Google AdMob as the only authorised seller of this app's ad inventory. |

Both are served via GitHub Pages at:

- Policy: **https://KISSWARDMULTIMEDIA.github.io/orbtanker-privacy/**
- Authorised sellers: **https://KISSWARDMULTIMEDIA.github.io/orbtanker-privacy/app-ads.txt**

## Where these URLs are used

1. **Google Play Console** - App content page, **Privacy policy** field. Play requires a publicly reachable policy URL for every app.
2. **Google Play Console** - Store listing, **developer website** field. This is the URL AdMob reads to locate `app-ads.txt`; without it there is nothing for the crawler to fetch.
3. **Inside the app** - Settings > Privacy Policy screen, which carries the same wording.

## app-ads.txt

Content is exactly one line:

```text
google.com, pub-2032400037497626, DIRECT, f08c47fec0942fa0
```

- `pub-2032400037497626` is the AdMob publisher ID and matches the app ID `ca-app-pub-2032400037497626~2005109511` used in `AndroidManifest.xml`.
- AdMob is the only ad network in the app, so a single record is correct. If another network is ever added, append its own record rather than editing this one.
- Format follows the IAB Tech Lab Authorized Sellers for Apps spec: plain ASCII, no BOM, LF line endings, trailing newline.
- This file is not part of the app bundle. It must stay reachable over **both** HTTP and HTTPS, return 200, and must not be blocked by `robots.txt`.

### Verifying after a push

```powershell
$u = "https://KISSWARDMULTIMEDIA.github.io/orbtanker-privacy/app-ads.txt"
(Invoke-WebRequest $u -UseBasicParsing).Content
curl.exe -sI $u
```

Expect the single line above and `200 OK`.

### AdMob status

AdMob crawls the developer website from the store listing. After the file is live and the Play listing is set, allow **at least 24 hours** before expecting the status to update. If AdMob reports the file as hosted on an unsupported location, its app-ads.txt status page shows the exact URL it tried - use that to confirm the Play listing matches this repository's Pages URL character for character.

Advertising continues to serve normally if `app-ads.txt` is missing; it exists to stop other parties selling counterfeit copies of this app's inventory.

## Publishing on GitHub Pages

The page is served from the repository root (`index.html`), so the root URL works.

- This repository is public under the KISSWARDMULTIMEDIA account.
- Push `index.html`, `app-ads.txt` and this README to the repository root.
- Enable Pages:
  - Settings > Pages > Build and deployment
  - Source: Deploy from a branch
  - Branch: main / folder: / (root) > Save
- Wait a minute or two, then confirm the policy loads at the URL above.

To push local changes:

```powershell
cd "C:\Users\DAVID\Desktop\orbtanker-privacy"
git add index.html app-ads.txt README.md
git commit -m "Update privacy policy"
git push
```

## Keeping it current

When the policy changes, update `index.html` and push. GitHub Pages updates automatically.

Note that `index.html` carries a "Last updated" date in its header - bump it whenever the wording changes.

When the AdMob publisher ID changes, update `app-ads.txt` to match. A mismatch there will fail verification even though the file is served correctly.

## Design notes

- The page is fully self-contained: no cookies, no analytics, no third-party fonts, scripts or stylesheets. The only outbound link is to Google's Privacy Policy.
- Styling is inline so the page cannot break if a CDN is unreachable.
- The dark navy theme matches the game's own palette.

## Important: no AdMob consent message is configured

This app intentionally has **no** European regulations (consent) message configured in AdMob.
That is a deliberate choice, not an oversight.

- No consent form is ever displayed, in any region.
- Advertising in the EEA, the UK and Switzerland is therefore limited to non-personalised
  ads, for every player. This is the same outcome Google applies automatically when no
  certified consent management platform is present.
- Players outside those regions are unaffected; players confirmed to be 13 or older there may
  still receive personalised advertising.

**Do not add a European message without also implementing a privacy-options entry point.**
Google requires one whenever a consent message is configured, and section 3 of the policy
would stop being accurate.

## Contact

David Kissward - kisswarddavid2@gmail.com
