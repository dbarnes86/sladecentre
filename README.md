# The Slade Building — website guide

This is the website for The Slade Building. The whole site is one file called **index.html** — it contains all the words and the layout. This guide explains how to make changes to it without needing any technical knowledge.

---

## How to edit the website

The simplest way to make changes is directly on the GitHub website — no special software needed.

1. Go to [github.com/dbarnes86/sladecentre](https://github.com/dbarnes86/sladecentre)
2. Click on **index.html** in the list of files
3. Click the **pencil icon** (✏️) near the top right of the page
4. Make your changes (see below for what to change and where to find it)
5. When you're done, scroll to the bottom and click the green **Commit changes** button
6. The live website will update automatically within a minute or two

---

## What you'll need to change regularly

### The current exhibition

Open index.html for editing (steps above), then use **Ctrl+F** (or **Cmd+F** on a Mac) to search for the words:

> `NOW SHOWING`

That will take you straight to the right part of the file. Change these four things:

- **The dates** — e.g. `23 May – 20 June 2026`
- **The title** — the name of the exhibition
- **The artist** — the artist's name, or write `Group exhibition` if it's several artists
- **The description** — two or three sentences about the show

---

### Upcoming events

Search for:

> `UPCOMING EVENTS`

Each event in the list looks like this:

```
<article class="event-card">
  <div class="event-type">Exhibition</div>
  <h3 class="event-title">Name of the exhibition</h3>
  <p class="event-artist">Artist name</p>
  <p class="event-desc">A short description of the show.</p>
  <div class="event-dates"><strong>1 Jan – 28 Jan 2026</strong></div>
</article>
```

**To change an event:** just replace the words between the `>` and `<` symbols. Don't touch anything else on those lines.

**To remove an event:** delete everything from `<article class="event-card">` down to the matching `</article>` below it.

**To add a new event:** copy one of the existing event blocks, paste it in just below the last one, and fill in the new details.

---

### The café specials

Search for:

> `CAFÉ SECTION`

There's a small highlighted box for the week's specials. Just replace the text inside it with whatever's on offer that week.

---

### Opening hours

If the hours ever change, search for:

> `OPENING HOURS`

You'll need to update it in two places — once at the top of the page and once near the bottom. The search will find both.

---

### Phone number or email address

Search for:

> `CONTACT DETAILS`

Replace the phone number or email address if they ever change.

---

## Adding a photo to the current exhibition

**Step 1 — Upload the photo to GitHub:**

1. Go to [github.com/dbarnes86/sladecentre](https://github.com/dbarnes86/sladecentre)
2. Click on the **images** folder
3. Click **Add file**, then **Upload files**
4. Drag your photo into the box, then scroll down and click **Commit changes**

**Step 2 — Tell the website to use it:**

Open index.html for editing and search for:

> `Add exhibition image`

You'll see a placeholder block. Replace the whole placeholder block (it starts with `<div class="featured-image-placeholder">` and ends a few lines later with `</div>`) with this single line:

```
<img src="images/your-photo-name.jpg" alt="Brief description of the image" class="featured-image">
```

Replace `your-photo-name.jpg` with the actual filename of the photo you just uploaded (including the `.jpg` at the end).

**Tips for photos:**
- JPG or PNG files both work fine
- Landscape photos (wider than they are tall) work best
- Try to keep the file under 1MB so the page loads quickly — most phones take photos that are too large, so ask Dan if you need help resizing one

---

## Moving the domain to GitHub Pages

The site is set up to live at **www.thesladecentre.com** (see the `CNAME` file in this repo). To point the domain here instead of the old host, log in to wherever the domain's DNS is managed (e.g. the domain registrar or the old hosting provider's DNS panel) and set the following records:

| Type | Host/Name | Value | Notes |
|------|-----------|-------|-------|
| CNAME | `www` | `dbarnes86.github.io` | Points www.thesladecentre.com at GitHub Pages |
| A | `@` (root/apex) | `185.199.108.153` | GitHub Pages apex IP |
| A | `@` (root/apex) | `185.199.109.153` | GitHub Pages apex IP |
| A | `@` (root/apex) | `185.199.110.153` | GitHub Pages apex IP |
| A | `@` (root/apex) | `185.199.111.153` | GitHub Pages apex IP |

The four `A` records let `thesladecentre.com` (without the `www`) also work and redirect to `www.thesladecentre.com`.

**Before switching:** remove or replace any existing `A`, `CNAME`, or `ALIAS` records for `@` and `www` from the old host — having both old and new records in place at once can cause the site to load inconsistently.

**After updating DNS:**
1. DNS changes can take anywhere from a few minutes to 24–48 hours to fully take effect
2. In the GitHub repo, go to **Settings → Pages** and confirm the custom domain shows a green check and "DNS check successful"
3. Tick **Enforce HTTPS** once it becomes available (it's greyed out until GitHub finishes issuing the certificate)

---

## Something looks wrong — who do I ask?

Contact Dan: [dan@kijo.io](mailto:dan@kijo.io)
