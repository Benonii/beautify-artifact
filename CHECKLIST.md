# Pre-publish checklist

Run every item before showing a page to the user.

## Screenshots

- [ ] Desktop at 1280 wide, ground Green.
- [ ] Desktop at 1280 wide, ground Bone.
- [ ] Phone at 390 wide, ground Green.
- [ ] Phone at 390 wide, ground Bone.

## Look in each screenshot for

- [ ] No text overflows its box, and the page has no sideways scroll.
- [ ] No readable text under 11px.
- [ ] Every table turns into one card per row on the phone, each cell showing its column name.
- [ ] Grids drop to 2 columns under 980px and 1 column under 620px.
- [ ] The `.sp` status line runs edge to edge, or wraps cleanly if it is too long.
- [ ] Box borders wobble slightly but have no gaps.
- [ ] Large values and the title show light grain, and still read clearly.

## Colour

- [ ] Only `--bg` and `--ink` are used. No grey, opacity tint, shadow or extra colour.
- [ ] The default ground is Green.
- [ ] All 13 ink buttons are in the hero, the pressed one is filled with ink, and the choice survives a reload (`localStorage` key `doc-way`).

## Type

- [ ] Mono is IBM Plex Mono 400. Values and headlines are Inter 500 with -0.04em spacing.
- [ ] Values are regular weight, never bold.
- [ ] Table headers are ink text with a 2px bottom rule, not a filled band.

## Content

- [ ] Section 01 says what the page decides or asks.
- [ ] Plain words throughout. Any technical number sits in a table beside a plain-words column.
- [ ] Every short code has a `data-tip`. No author-only codes on a plan page.
- [ ] Short sentences. No em dashes. Easy units.
- [ ] Open questions are `.lb.dsh` cards with a `.pill.no` status.
- [ ] Every table cell has `data-label`.

## Files

- [ ] One self-contained HTML file. Only Google Fonts loads from outside.
- [ ] The page is generated from a data file (YAML or JSON) by a script.
- [ ] The Markdown twin was regenerated from the HTML, not edited by hand.
- [ ] The message to the user names what changed since the last version in one line.
