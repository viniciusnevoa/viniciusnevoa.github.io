---
layout: default
title: "An example post, which also explains how to write one"
summary: "How the files in the writing folder work, and how to put mathematics in them."
---

This file lives in the folder called `_posts`. Every file in there shows up automatically on the
Writing page, newest first — you never edit that list by hand.

To write a new post, make a copy of this file in the same folder and give it a name of exactly this
shape:

`2026-11-14-a-short-slug-for-the-title.md`

The date at the front is what orders the posts and what appears under the title, so it has to be
four-digit year, two-digit month, two-digit day, separated by hyphens. Everything after the date
becomes part of the web address. Then change the `title` and `summary` lines at the top of the file,
keeping the quotation marks, and write below them.

## Formatting

The body is Markdown, which is a plain-text shorthand. Two asterisks make **bold**, one makes
*italic*, and a line starting with `##` is a section heading. A blank line starts a new paragraph.
Links look like `[the text you see](https://the-address.com)`.

## Mathematics

Single dollar signs give inline mathematics, so `$e^{i\pi} = -1$` renders as $e^{i\pi} = -1$. Double
dollar signs on their own lines give a displayed equation:

$$
\frac{\partial \rho}{\partial t} = -\frac{i}{\hbar}\left[H, \rho\right]
$$

Everything you already know from LaTeX works inside the dollar signs — `\frac`, `\int`, `\langle`,
`amsmath` environments like `align`, all of it. What does *not* carry over is the surrounding
document: no preamble, no `\begin{document}`, no `\section`, no packages.

One wrinkle worth knowing. Underscores mean *italic* in Markdown as well as *subscript* in LaTeX, so
an inline formula with several of them can occasionally come out garbled. If that happens, swap the
dollar signs for `\(` and `\)`, which do the same job and are immune to it: \( T_{\mu\nu} = R_{\mu\nu} \).

Delete this post once you have read it — remove the file from the `_posts` folder and it disappears
from the site.
