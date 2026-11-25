# Island of Champions — Digital Invitation

Interactive invitation for **GreatWhite Dealers Meet 2026 · Sri Lanka**.
The guest completes three mosaics; each one unlocks a clue, and the third
opens the full invitation.

Plain HTML, CSS and JavaScript. No build step, no dependencies, no backend.

## Repository structure

This structure matters. `index.html` must sit at the repository root, with
the `assets` folder **beside it**, not inside another folder:

```
.
├── index.html
├── vercel.json
├── README.md
└── assets/
    ├── r1.jpg              Mosaic 01 — "The Shore"
    ├── r2.jpg              Mosaic 02 — "The Mosaic"
    ├── r3.jpg              Mosaic 03 — "The Island"
    ├── destination-lg.jpg  Final full-screen reveal
    ├── logo.png            GreatWhite × Power Trip lock-up
    └── ioc.png             Island of Champions lock-up
```

All file names are lowercase. Keep them that way — Vercel runs on Linux,
where `R1.jpg` and `r1.jpg` are two different files. A capital letter that
works on your laptop will 404 once it is live.

## Deploying to Vercel

1. Push this repository to GitHub.
2. On vercel.com: **Add New → Project → Import** this repository.
3. Leave every build setting empty. `vercel.json` already declares
   no framework, no build command and the root as the output directory.
4. **Deploy.**

To confirm the images are deployed, open this directly after deploying:

```
https://<your-project>.vercel.app/assets/r1.jpg
```

If that shows the photograph, the invitation will render correctly.
If it 404s, the `assets` folder did not reach the repository root.

## Running it locally

Double-click `index.html`. That is all — it works straight from disk.

To test it on your phone over the same wifi, serve the folder instead:

```bash
python -m http.server 8000
# then open http://localhost:8000
```

## Before sending it to guests

Open `index.html` in a code editor and replace these placeholders:

| Find | Replace with |
| --- | --- |
| `DD – DD MMM 2026` | the event dates |
| `Resort name` | the venue |
| `City, Sri Lanka` | the venue city |
| `To be announced` | the dress code |
| `RSVP link to be connected here` | your RSVP / registration URL |

The day-by-day itinerary sits just below those, starting at **Day One**.

## Changing the three mosaics

Replace `assets/r1.jpg`, `r2.jpg` and `r3.jpg` with your own photographs,
keeping the same file names. Recommended size **900 × 1200 px (3:4 portrait)**.
Choose images with detail across the whole frame — a photo that is mostly
plain sky makes the pieces hard to tell apart.

To rename a round or rewrite its clue, edit the `ROUNDS` list near the top
of the script in `index.html`:

```js
{img:'assets/r1.jpg', title:'The Shore', gaps:4,
 n:'Clue 01 of 03', h:'The Shore',
 p:'"Where the Indian Ocean writes in gold."'}
```

`gaps` is how many pieces the guest must place in that round (4, 5 and 6 by
default). Adding a fourth round is one more entry in that list — the progress
rail rebuilds itself to match.
