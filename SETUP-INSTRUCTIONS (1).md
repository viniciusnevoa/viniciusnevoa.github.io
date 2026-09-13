# How to put this site online, and how to change it afterwards

You do not need to install anything. No terminal, no software, no code. Everything below happens in
a normal web browser on github.com.

Set aside about twenty minutes for Part One. After that, changing the site takes a minute.

---

## Part One — getting it online

### 1. Sign in

You already have an account, so this step is done. Your site will live at
**https://viniciusnevoa.github.io** — that address is fixed by your username.

### 2. Create the place your site will live

Once you are signed in, click the **+** in the top right and choose **New repository**.

- **Repository name:** type `viniciusnevoa.github.io`, exactly like that, all lowercase. This exact
  name is what tells GitHub to publish it as a website rather than as ordinary files, so it has to
  match your username precisely.
- Leave it set to **Public**.
- Do not tick any of the boxes about adding a README or a licence.
- Click **Create repository**.

If a repository by that name already exists on your account, use it rather than making a second one —
GitHub only publishes one site per account from that name.

### 3. Upload the files

On the page that appears, find the link that says **uploading an existing file**.

Now open the folder of files that came with these instructions. Select everything inside it — all the
files and all the folders, including the ones whose names begin with an underscore — and drag them
onto the GitHub page.

A few notes on this step:

- Drag the *contents* of the folder, not the folder itself.
- Do not zip anything. GitHub wants the loose files.
- The folders beginning with an underscore (`_layouts`, `_posts`) are not optional and must keep
  their names. GitHub treats those names as instructions.

When the upload finishes, scroll down and click the green **Commit changes** button.

### 4. Wait a minute, then look at it

Go to **https://viniciusnevoa.github.io**

The first build takes a couple of minutes, so if you get a "404" at first, wait ninety seconds and
refresh. If it is still not there after five minutes, see the troubleshooting notes at the bottom.

Your site is now live on the public internet.

---

## Part Two — making it yours

### Editing anything at all: the one procedure

This is the only mechanical skill the whole system requires, so it is worth doing once slowly.

1. On your repository page, click the name of the file you want to change.
2. Click the **pencil icon** at the top right of the file.
3. Type your changes.
4. Click **Commit changes**, then **Commit changes** again in the box that appears.
5. Wait about a minute and refresh your site. Your edit is live.

That is it. That is the entire workflow, forever.

### Start with `_config.yml`

Open that file first. The top section holds your name, your role, your department, your email
address, and links to your INSPIRE and arXiv profiles. Change those and they update everywhere on
the site at once.

Two rules for this file, and they matter:

- **Keep the quotation marks.** `name: "Ada Lovelace"` is correct; `name: Ada Lovelace` will usually
  work but breaks the moment your text contains a colon.
- **Keep the colon and the space after it.** The pattern is always `label: "your text"`.

To hide something — say you have no ORCID page — set it to empty quotation marks: `orcid: ""`. The
link will vanish from the sidebar rather than pointing nowhere.

### Then the pages

Five files, one per section of the site:

| File | Becomes |
|---|---|
| `index.md` | the front page |
| `research.md` | Research |
| `publications.md` | Publications |
| `teaching.md` | Teaching |
| `writing.md` | the list of posts — this one builds itself, leave it alone |

Each has some example content in it written in the register of a physics department page. Replace the
words; leave the few lines at the very top, between the two rows of dashes, exactly as they are. Those
lines tell the site what the page is.

The text is Markdown: blank line for a new paragraph, `##` at the start of a line for a section
heading, `**bold**`, `*italic*`, and `[visible text](https://address)` for a link.

### Mathematics

Single dollar signs for inline, double dollar signs on their own lines for a displayed equation. All
your LaTeX macros work inside them — `\frac`, `\int`, `amsmath` environments, the lot. What does not
apply is the document scaffolding: no preamble, no packages, no `\begin{document}`.

The front page opens with a displayed equation, which is the one deliberate piece of showmanship in
the design. Put something of yours there.

### Your CV

Upload the PDF into the `assets/files` folder — open that folder on GitHub, then **Add file →
Upload files**. Name it `cv.pdf`, or if you would rather not rename it, change the `cv_file` line in
`_config.yml` to match the name it already has. The sidebar link then works.

### Writing a post

Open the `_posts` folder. There is one example file in there that explains the naming rule, which is
strict: `2026-11-14-some-short-title.md`. Copy it, rename it, rewrite it. It appears on the Writing
page by itself.

---

## Optional: your own domain name

Worth the twelve dollars a year. It means that when you change institutions, or if GitHub someday
falls out of favour, your address survives.

1. Buy the domain from Cloudflare or Namecheap. `firstnamelastname.com` is the obvious choice; `.net`
   or a national domain is fine too.
2. On GitHub, go to your repository's **Settings**, then **Pages** in the left-hand menu, and enter
   the domain under **Custom domain**.
3. GitHub then shows you exactly which records to add at the company you bought the domain from.
   Follow those instructions literally — they are specific and they change occasionally, which is why
   they are better read from GitHub than from me.
4. Once it works, tick **Enforce HTTPS** on that same page.

Give the change up to a day to take effect across the internet.

---

## If something goes wrong

**The site shows a 404 after five minutes.** Check the repository name is exactly
`viniciusnevoa.github.io`, all lowercase, with no extra characters. Then go to **Settings → Pages**
and confirm the source is set to deploy from the `main` branch, folder `/ (root)`.

**The site appears but looks like unstyled text.** The stylesheet did not upload. Check that a folder
called `assets` exists in your repository, containing `css`, containing `style.css`.

**You get an email from GitHub saying the build failed.** Almost always `_config.yml`. A missing
quotation mark, or a missing space after a colon. Open it, look at what you changed last, restore the
pattern `label: "text"`.

**A page is blank or the layout is gone.** Check the very top of that file still has the three lines
between rows of dashes, and that `layout: default` is one of them.

**Equations show as raw dollar signs.** Usually a mismatched delimiter somewhere earlier on the same
page — one stray `$` will swallow everything after it. Also check for a missing closing brace.

**An inline formula came out in italics with letters missing.** Markdown read your underscores as
italic markers. Write that one formula with `\(` and `\)` instead of dollar signs.

**You want to undo something.** Click the file, then **History**, and you can see and restore every
previous version. Nothing you do here is unrecoverable, which is a good reason to experiment.

---

## Keeping it out of search results while you write

The first line of `_config.yml` is:

    draft: true

While that says `true`, every page tells search engines to ignore the site. It is still technically
public — anyone who knows the address can open it — but nothing links to it and Google will not list
it. That lets you edit with real rendered pages in front of you instead of guessing.

When you are ready to be found, change it to `false` and commit. Nothing else about the site changes.

If you would rather nothing be reachable at all while you work, make the repository **Private** when
you create it instead. GitHub then will not build the site on a free account, so there is nothing to
see until you switch it to Public in **Settings → General → Change visibility**. The tradeoff is that
you cannot preview anything until that moment.
