# Web2APK

A browser-based HTML/ZIP-to-Android-APK builder powered by GitHub Actions.

## Setup

1. Open **Settings → Pages** and enable GitHub Pages from the `main` branch, root folder.
2. Open **Settings → Actions → General** and ensure workflows are allowed to run.
3. Create a fine-grained GitHub token restricted to this repository with:
   - Contents: Read and write
   - Actions: Read and write
4. Open the Pages website, upload a ZIP containing `index.html` (plus CSS, JS and assets) or a single HTML file, enter the token, configure the app, and press **Build APK**.
5. Follow **Actions → Build APK**. On success, download the APK from the repository's **Releases** page.

## Website

After Pages is enabled, the site should be available at:

https://fiesta1862.github.io/web2apk/

## Notes and limitations

- This builds a basic Android WebView wrapper. It does not convert HTML into native Android UI.
- A single HTML upload cannot include separate CSS, JavaScript or image files. Use a ZIP for a multi-file website.
- ZIP must contain `index.html` at its root or inside one top-level folder.
- Uploaded source is temporarily committed under `web2apk-inputs/` and the workflow attempts to delete it after building. Git history retains previous versions; do not upload passwords, API keys or other secrets.
- Keep the repository private if your website source should not be public.
- Output is a debug APK for testing. For stable public releases, configure a persistent Android signing key and build a signed release APK.
- Websites that depend on server-side code or APIs still need their backend hosted online.
