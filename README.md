# Upkeep Utah — Customer Document Viewer

Static HTML page that renders Upkeep Utah work orders (estimates, work orders, and invoices) shared from the Android contractor app.

## How It Works

1. The Android app serializes a work order to JSON and base64-encodes it
2. The encoded data is appended as a URL parameter: `https://<your-domain>/doc.html?data=<base64>`
3. The customer opens the link in any browser
4. `doc.html` decodes the data and renders a branded, professional document
5. The customer can sign directly in the browser and submit via email

## Files

| File | Purpose |
|------|---------|
| `doc.html` | Self-contained customer-facing document viewer with signature capture |
| `.gitignore` | Standard ignore rules |
| `README.md` | This file |

## Hosting via GitHub Pages

1. Go to **Settings → Pages** in this repository
2. Under **Source**, select **Deploy from a branch**
3. Set branch to `main` and folder to `/ (root)`
4. Click **Save**
5. Your page will be live at: `https://<username>.github.io/upkeep-utah-docs/doc.html`

## Connecting to the Android App

Update `ShareHelper.kt` in the Android project to use your GitHub Pages URL as the `baseUrl`:

```kotlin
val baseUrl = "https://<username>.github.io/upkeep-utah-docs/doc.html"
```

Replace `<username>` with your GitHub username.

## Custom Domain (Optional)

To use `upkeeputah.com/doc.html` instead of the GitHub Pages URL:

1. Add a `CNAME` file to this repo containing your domain (e.g., `docs.upkeeputah.com`)
2. Configure your domain's DNS with a CNAME record pointing to `<username>.github.io`
3. In **Settings → Pages → Custom domain**, enter your domain
4. Check **Enforce HTTPS**

## No Server Required

This is a fully static page. There is no backend, no database, and no server-side logic. All data is decoded client-side from the URL parameter. It can be hosted on GitHub Pages, Netlify, Vercel, or any static file host.

## License

Proprietary — Upkeep Utah Inc.
