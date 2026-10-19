# killakg.com

A simple personal landing page, built with plain HTML and CSS. No dependencies, JavaScript, or build step required.

## Files

- `public/index.html`: the entire website, including styles.
- `README.md`: setup and editing instructions (not published as website content).

## Preview

Open `public/index.html` in a browser.

## Upload to GitHub

1. Extract this ZIP.
2. Open your website repository on GitHub. For a new repository, use a name such as `killakg-site`.
3. Choose **Add file → Upload files**. Drag the `public` folder and `README.md` into the upload area. Keep `public/index.html` inside `public`; do not upload the ZIP itself or an extra enclosing `killakg` folder.
4. Commit the files to your production branch, typically `main`.

If you already have a local clone, copy these files into that repository, then commit and push normally. Review existing files before replacing them.

## Connect Cloudflare Pages

1. In Cloudflare, open **Workers & Pages → Create application → Pages → Import an existing Git repository**.
2. Authorize GitHub and choose your repository.
3. Set:

   | Setting | Value |
   | --- | --- |
   | Production branch | `main` (or your chosen production branch) |
   | Framework preset | None |
   | Build command | `exit 0` |
   | Build output directory | `public` |
   | Root directory | Leave empty for the repository root |

4. Deploy, then check the generated `pages.dev` URL.
5. In the Pages project, open **Custom domains → Set up a custom domain**, enter `killakg.com`, and follow Cloudflare's instructions. The apex domain must be a Cloudflare zone in the same account, using Cloudflare nameservers.

Once connected, pushes to your production branch trigger deployments.

Official documentation:
- https://developers.cloudflare.com/pages/framework-guides/deploy-anything/
- https://developers.cloudflare.com/pages/configuration/custom-domains/

## Add your links later

Find the list under `On the way` in `public/index.html`. Replace an item with a real link, for example:

```html
<li><a href="YOUR_ACTUAL_APPLE_MUSIC_PLAYLIST_URL">My Apple Music playlist</a></li>
```

Replace the placeholder URL with your actual playlist URL before publishing. To style new links, add this inside the existing `<style>` element:

```css
a { color: inherit; text-underline-offset: 4px; }
a:hover { color: var(--accent); }
a:focus-visible { outline: 2px solid var(--accent); outline-offset: 4px; }
```

## Reverse proxy

This project serves only the landing page. Configure your reverse proxy separately. A common arrangement is to use `killakg.com` for this website and a separate hostname such as `app.killakg.com` for a proxied application. Pointing the apex domain to Pages affects any existing use of that same hostname, so choose distinct hostnames if you want both services.
