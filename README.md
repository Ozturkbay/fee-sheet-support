# Fee Sheet — Privacy & Support site

Public support and privacy website for **Fee Sheet** (Resale Profit
Calculator) for iPhone. It provides the Privacy Policy URL and Support URL
required by App Store Connect, in English and Turkish.

- **Developer:** Fatih Öztürkbay
- **Support email:** `feesheet.support@icloud.com` (not chosen yet — see below)

It is a plain static site: HTML and one CSS file. No framework, no build
step, no JavaScript, no external fonts, scripts or stylesheets.

## URLs

Intended for GitHub Pages from the `main` branch, repository root:

| Page | URL |
| --- | --- |
| Home | https://ozturkbay.github.io/fee-sheet-support/ |
| Privacy Policy (EN) | https://ozturkbay.github.io/fee-sheet-support/privacy/ |
| Gizlilik Politikası (TR) | https://ozturkbay.github.io/fee-sheet-support/privacy/tr/ |
| Support (EN) | https://ozturkbay.github.io/fee-sheet-support/support/ |
| Destek (TR) | https://ozturkbay.github.io/fee-sheet-support/support/tr/ |

Use the **Privacy Policy (EN)** URL for App Store Connect's Privacy Policy
URL field and the **Support (EN)** URL for its Support URL field.

## Structure

```
index.html              Landing page (EN, with TR links)
privacy/index.html      Privacy Policy (EN)
privacy/tr/index.html   Gizlilik Politikası (TR)
support/index.html      Support (EN)
support/tr/index.html   Destek (TR)
assets/css/styles.css   The only stylesheet
assets/images/          App icon, favicon, apple-touch-icon
.nojekyll               Serve files as-is (no Jekyll processing)
```

All internal links are relative, so the site works under the
`/fee-sheet-support/` project path. The only absolute URLs are the
`<link rel="canonical">` and `hreflang` tags in each page's `<head>`. If the
site moves (for example, to a custom domain), update those tags too:

```sh
grep -rl "https://ozturkbay.github.io/fee-sheet-support/" --include='*.html' .
```

## Before publishing: set the support email

Every email address is the literal placeholder `feesheet.support@icloud.com`
(in `mailto:` links and visible text). Replace all of them once the address
is chosen, then confirm none remain:

```sh
grep -rl feesheet.support@icloud.com --include='*.html' . \
  | xargs sed -i '' 's/feesheet.support@icloud.com/you@example.com/g'
grep -rn feesheet.support@icloud.com .
```

## Local preview

From the repository root:

```sh
python3 -m http.server 8000
```

Then open http://localhost:8000/. (Opening the files directly with
`file://` won't resolve the directory-style links such as `privacy/`.)

## Updating the effective date

The privacy policies show their date near the top:

- `privacy/index.html` — `Effective date: 20 October 2026`
- `privacy/tr/index.html` — `Yürürlük tarihi: 20 Ekim 2026`

When the policy changes, edit both lines together and keep the English and
Turkish texts aligned section by section. Turkish month names: Ocak, Şubat,
Mart, Nisan, Mayıs, Haziran, Temmuz, Ağustos, Eylül, Ekim, Kasım, Aralık.

The policy describes what the app does today (since 20 October 2026): a
free download with Google AdMob ads (interstitial and rewarded, no banners;
Google Mobile Ads SDK plus UMP consent, then Apple's ATT prompt) and one
optional non-consumable in-app purchase, Fee Sheet Premium, that removes ads
and Free limits. The developer still has no account system, server or
analytics of its own; Buying Criteria, Seller Profiles, Saved Deals,
onboarding progress, appearance, the ad-frequency counter and rewarded-unlock
expiry stay in local device storage, and the Premium purchase record is kept
in the iOS Keychain. If the app adds another SDK, a permission, an account
system, analytics, a server or changes its ads or purchases, review both
privacy pages and the Support "Free version and Fee Sheet Premium" and "Ads
and Premium" sections before releasing that version.

## App icon

`fee-sheet-icon.png` (512×512), `favicon.png` (64×64) and
`apple-touch-icon.png` (180×180) were resized with macOS `sips` from
`assets/images/fee-sheet-app-icon-1024.png` in the Fee Sheet app repository
(`ProjectFlip`). The source file was not modified, and nothing is hotlinked.

## Design

Colors follow the Fee Sheet brand: a neutral light canvas (`#F5F5F7`), a
neutral black/charcoal dark appearance (`#0D1116`), and green (`#128C60`,
`#19BC79` in dark) used only as an accent for links, focus and highlights.
Copy follows the app's voice: concise, plain English, results described as
estimates, no profit guarantees.

## Privacy of this website

This website contains no first-party analytics or tracking code: its own
code sets no cookies, uses no analytics, tracking scripts or marketing
pixels, loads no third-party fonts, scripts or stylesheets, and contains no
JavaScript. When hosted on GitHub Pages, see the
[GitHub Privacy Statement](https://docs.github.com/en/site-policy/privacy-policies/github-general-privacy-statement)
for how GitHub handles data.
