# Communist Crosswords — publishing guide

A lightweight, no-account, static archive of interactive puzzles, with printable PDFs. Puzzles 1–3 are included.

## Launch it

1. Create a public GitHub repository, e.g. `communist-crosswords`.
2. Upload **all the files and folders inside this package** to the repository root. Do not upload only `index.html`.
3. In the repository go to Settings → Pages → Build and deployment → Deploy from a branch. Select `main` and `/(root)`, then Save.
4. Visit `https://YOURUSERNAME.github.io/communist-crosswords/` once publishing finishes.

For local testing, open a terminal in this folder and run `python3 -m http.server 8000`, then visit `http://localhost:8000/`. Opening HTML files directly via `file://` may not load puzzle JSON because browsers restrict file-based requests.

## Add a fourth puzzle

Create `puzzles/004.json` in the same structure as 001–003 with a full solution grid (`rows`, `#` for black squares), `numbers`, and entries with clue, answer, direction, number, and `cells` (zero-based row-major cell indices). Add its printable PDF at `pdfs/004.pdf`, and add a card in `index.html`. The crossword player works with any square grid size; no changes to `crossword.js` are needed. **A future improvement** is to generate the archive cards from a separate manifest, but for three puzzles a simple static home page is easiest to maintain.

## Email subscriptions

The homepage deliberately shows a newsletter placeholder **rather than a fake working form**. Set up a Buttondown (or other newsletter) account and replace the `<section class="newsletter">...</section>` element in `index.html` with the provider's official embed form. Test subscription, confirmation, and unsubscribe before launching the form. Avoid collecting subscribers in `localStorage` or publishing email addresses in your repository.

## Progress and privacy

Each crossword uses a distinct browser `localStorage` key, so progress and completion do not overlap. Browser storage is tied to browser/device and can be deleted if users clear their browsing data. Solvers do not need accounts.

## Quality checks

- Open all three puzzles and check entries in both directions.
- Test Check, Reveal, Clear, phone keyboard navigation, and PDF downloads.
- PDFs are preserved from the originals.
- Clue/answer list discrepancies were resolved only when numbering on the printable grid was unambiguous.
