# soundandmovement.info

Website and research log of Tommaso Perego: Sound and Movement practice research.
A Jekyll site: GitHub Pages builds and hosts it for free. Edit it through an admin panel (Pages CMS), with no coding.

## How it fits together

| Where | What |
|---|---|
| `_posts/` | **Research log** posts, one Markdown file each (`YYYY-MM-DD-title.md`) |
| `_data/publications.yml` | Publications list shown on the home page |
| `index.html` | Home page: latest posts, research, works, publications, about, contact |
| `bees.html` | Song of the Bees project page (lists posts tagged *Song of the Bees*) |
| `blog/index.html` | Research log index, with tag sections |
| `_layouts/` | Page templates (`post.html` = how a post looks) |
| `style.css` | All styling |
| `img/` | Images. Files uploaded from the admin panel go to `img/uploads/` |
| `.pages.yml` | Admin panel configuration |
| `CNAME` | Custom domain www.soundandmovement.info |

## Writing a post (admin panel)

1. Go to **https://app.pagescms.org** and sign in with your GitHub account.
2. The first time: install the Pages CMS GitHub app and give it access to the `soundandmovement` repository.
3. Open the repository → **Research log** → **Add an entry**.
4. Fill in:
   - **Title** (and optional **Subtitle**)
   - **Date**
   - **Tags**: reuse the same tags to group posts, e.g. `Song of the Bees`, `spatial audio`
   - **In short**: 1–2 plain-language sentences for general readers. Shown highlighted at the top and on the post cards.
   - **Abstract** and **Keywords** (optional): the academic summary, folded away under the "In short" box
   - **Cover image** (optional), its description and caption/credit
   - **Post**: the text. Use headings, bold, links, quotes and images from the toolbar.
   - **References**: one entry per line, in your usual style (e.g. Harvard). They appear numbered at the end of the post.
   - **Published**: switch off to save it as a hidden draft.
5. **Save**. GitHub rebuilds the site and the post is live in about a minute.

Every post automatically gets the author and date, reading time, previous/next links, and a **"How to cite this post"** box (text citation + BibTeX). It is also added to the RSS feed (`/feed.xml`).

### Academic conventions

- **In-text citations**: write them author–date in the text, e.g. (Burgun 2015), and put the full entry in **References**.
- **Footnotes**: switch the editor to Markdown mode (toolbar switch). Type `[^1]` where the note goes and `[^1]: The note text.` at the end. Notes are numbered and linked automatically.
- **Figure captions**: put an italic line directly under an image: `*Figure 1. Caption (source).*`
- **Video**: in Markdown mode, paste the embed code from YouTube's Share → Embed. Audio: `<audio controls src="/img/uploads/file.mp3"></audio>`.
- **Co-authored posts**: add names under **Authors**.

The example post `_posts/2026-11-19-how-to-write-a-post.md` shows all of these. It is marked unpublished, so it never appears on the live site.

## Editing publications

In the admin panel, open **Publications**. Add an entry at the top (newest first), tick **Show "New" badge** for the latest one and untick it on the old one. To change the featured paper box on the home page, edit `index.html` (section "Current research").

## Still to fill in

Search the files for `TODO`: contact email, Google Scholar profile link, full names of the Song of the Bees collaborators, a link for the 2013 SAE paper, and the About bio in your own words.

## Publishing on GitHub Pages (one-time setup)

1. Create a **public** repository on github.com, e.g. `soundandmovement`, and upload this folder's contents (or push with git).
2. Repository **Settings → Pages → Source: Deploy from a branch → `main` / root → Save**.
3. Custom domain: at your domain registrar set
   - `www` → **CNAME** → `YOUR-USERNAME.github.io`
   - `@` → **A** records `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`

   then enter `www.soundandmovement.info` under **Settings → Pages → Custom domain** and tick **Enforce HTTPS**. This also fixes the certificate error on the address without "www".
4. Cancel the old site builder only once the new site is live.

## Preview on your computer (optional)

With Docker running:

```bash
docker run --rm -p 8765:4000 -v "$PWD":/src -w /src ruby:3.3-slim bash -c "gem install -N jekyll:3.10.0 kramdown-parser-gfm jekyll-feed webrick csv bigdecimal base64 logger >/dev/null && jekyll serve --host 0.0.0.0 --unpublished"
```

Then open http://localhost:8765.
