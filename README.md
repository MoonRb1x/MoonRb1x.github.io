# MoonRb1x portfolio

Your portfolio site, written in [VCWL](https://vcwl.chteau.bzh): styled like an open Figma file (layers panel, selected frames, a cursor with your name gliding around), a boot intro, glitch effects, and four pages: Home, Work, Store, Contact.

## 1. Look at it on your computer

1. Unzip `moon-portfolio.zip` somewhere easy, like your Desktop.
2. Open the `moon-portfolio` folder, click the address bar at the top of File Explorer, type `powershell` and press Enter. A PowerShell window opens in that folder.
   (Mac: right-click the folder → "New Terminal at Folder".)
3. Run:
   ```
   vcwl dev
   ```
4. Open the address it prints (usually http://127.0.0.1:4400) in your browser. That's your site.
   Leave the window open: when you save a change to a file, the page reloads by itself.
   Press `Ctrl+C` in the window to stop it.

## 2. Change things (optional)

Open the files with Notepad (right-click → Open with → Notepad), change, save.

- `src/data.vcwl`: your links, your work (titles and descriptions) and your Creator Store items.
  - Put your X link between the quotes in `x_url()`, e.g. `"https://x.com/yourname"`. While it's empty, the X card is hidden.
  - New UI to show? Put the image in `public/images/work/` (e.g. `11.png`) and copy one `Work { ... }` line with a new `id`, and set `w` and `h` to the image's width and height in pixels (right-click the image → Properties → Details). It shows up on the Work page.
  - New Creator Store item? Put its icon in `public/images/store/` and copy the `Item { ... }` block.
- `public/images/avatar.png` (headshot, used for the logo and link previews) and `public/images/avatar-full.png` (full body, on the home and contact pages): replace them with new ones any time, same names. The full-body one needs a transparent background.

If you make a typo, `vcwl dev` prints an error with the file, the line, and a `help:` line telling you what to fix.

## 3. Build the site

In the same PowerShell window (stop `vcwl dev` with `Ctrl+C` first):

```
vcwl build
```

This creates a `dist` folder. That folder is the finished website.

## 4. Publish it on GitHub Pages (free)

1. Create an account on https://github.com (free) and sign in.
2. Top right, click **+** → **New repository**.
3. Repository name: `YOURNAME.github.io`, where YOURNAME is your GitHub username exactly (e.g. `moonrb1x.github.io`).
   Keep it **Public**. Click **Create repository**.
4. On the next page, click the link **uploading an existing file**.
5. Open the `dist` folder on your computer, select **everything inside it** (`Ctrl+A`) and drag it onto the GitHub page.
   Drag what's *inside* `dist`, not the `dist` folder itself.
6. Wait for the uploads to finish, then click **Commit changes** at the bottom.
7. Go to the repository's **Settings** tab → **Pages** (left menu).
   Under "Build and deployment": Source **Deploy from a branch**, Branch **main**, folder **/ (root)**, then **Save**.
8. Wait 1 or 2 minutes, then open `https://YOURNAME.github.io`. Your portfolio is live. 🎉
   (The Pages settings page shows the link too, with a **Visit site** button.)

## 5. Update it later

1. Change what you want (step 2), then run `vcwl build` again.
2. In your repository on GitHub: **Add file** → **Upload files**, drag everything inside `dist` again, **Commit changes**.
   Files with the same name get replaced. The site updates within a minute or two.

## Problems?

- **`vcwl` is not recognized**: close PowerShell and open a new one. Still broken? Run the installer again:
  `irm https://vcwl.chteau.bzh/install.ps1 | iex`
- **The site is a 404 on GitHub**: check the repository name is exactly `YOURNAME.github.io`, that `index.html` is at the top of the repository (not inside a `dist` folder), and wait a few more minutes.
- **The page stays black**: use a recent Chrome, Edge, Firefox or Safari.
