# Andrew McHaty Photography

A GitHub Pages-ready graduation portfolio, with 89 locally stored photographs from the existing Adobe Portfolio, six Square packages, and a review form prepared for Formspree.

## Publish on GitHub Pages

1. Create a public repository named `andrewmchaty.github.io` in the `andrewmchaty` account (or use a different repository name for a project site).
2. Upload the contents of this folder to the repository root, preserving the `assets` folder. Do not upload the ZIP itself or an enclosing folder.
3. In **Settings → Pages**, choose **Deploy from a branch**, select **main** and **/ (root)**, and save.
4. GitHub will show the published URL when deployment completes. For the suggested repository, it is `https://andrewmchaty.github.io/`.

No framework, package installation, build step, or private credentials are needed. Relative asset paths support both account sites and project sites.

GitHub instructions: https://docs.github.com/en/pages/getting-started-with-github-pages/creating-a-github-pages-site

## Enable review submissions

GitHub Pages cannot store incoming form submissions by itself. The form is intentionally disabled until a real receiving service is connected; it never pretends to save reviews in a visitor's browser.

1. Create a form in your Formspree account at https://formspree.io/ and verify its receiving email as required.
2. Copy its public form endpoint, such as `https://formspree.io/f/yourFormId`.
3. Set `reviewEndpoint` in `config.js` to that endpoint and commit the update. Never place account passwords or API secrets in the repository.
4. Submit one clearly marked test review and check that it arrives in Formspree. Delete the test in the Formspree dashboard. Check your plan's submission limits and spam settings.
5. The site sends the display name, school, rating, written review, and publication consent to Formspree. It does not collect email addresses.

## Approve and publish a review

Review submission and publication are separate. The owner reads submissions in Formspree, then adds only approved, consented reviews to `reviews.json`. Publication is manual; this version does not have an administrator dashboard or automatic approval integration.

The file starts as `[]` because no actual reviews were supplied. For each approved review, add an object with `name` (string), `school` (string), `rating` (integer 1–5), and `review` (string). Preserve the reviewer's words. Use valid JSON, with a comma between objects. Committing the updated file publishes the approved reviews after GitHub redeploys.

Do not add unapproved reviews or private details to this public repository. Visitors can see every file, including review data.

## Booking

Packages and booking links were copied from the public Square services page on November 12, 2026. Square remains responsible for availability and completing bookings; visitors finish booking in a new Square tab. An in-page Square widget would require the official embed code from your Square dashboard.

When prices or packages change, update the matching package in `index.html`. The site does not synchronize pricing automatically.

## Photographs and maintenance

`photos.json` lists the gallery images. `asset-sources.json` records their original public Adobe URLs. All 89 images were downloaded locally, so the new site does not need Adobe Portfolio to serve the images. Keep your original full-resolution photographs separately.

- `index.html`: page text and packages
- `styles.css`: appearance and responsive layout
- `app.js`: gallery, filters, lightbox, and form handling
- `config.js`: public review endpoint
- `reviews.json`: approved reviews only
- `assets/`: portfolio photos

## Local preview

Run `python3 -m http.server 8765` from this folder, then visit http://localhost:8765. Opening `index.html` directly as a file will not load the JSON gallery in some browsers.

## Current verification and remaining setup

Verified in browser: gallery loads, campus filter works, enlarged images and next-image navigation work, Escape closes the gallery. Photo files and JSON references checked locally. Review collection is not live or end-to-end tested because no Formspree endpoint has been supplied. GitHub deployment is pending an accessible repository or browser sign-in. The site has not been published.
