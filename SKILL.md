---
name: beautify-artifact
description: Use when making any designed page, plan, study or report page. Builds single-file HTML in the label-sheet style from the bundled starter.
---

# Beautify artifact

Every designed page is a single HTML file in one house style: a dense **label sheet**. Start from `assets/starter.html`. Do not invent a different style, and do not soften this one.

## The look

One ink on one flat ground. Thin hand-drawn lines. Small spaced-out mono labels. A few large plain values. Barcodes, rulers and dimension lines as decoration. It should read as a printed spec label or a shipping tag, never as a web app.

- Values are a plain grotesk at regular weight, never heavy. Examples: "V6", "007", "0X2D".
- Small text is a typewriter mono, mostly in capitals.
- Status lines spread their letters edge to edge: `A C C E S S   G R A N T E D`.
- Lines are thin and a little wobbly. Large ink has grain and small holes.
- A single label sits inside crop marks or a thin box.
- Dashed rules end in ticks, like `|- - - - -|`. A dimension line carries its value in the middle.
- Tables are thin grids with no filled header.

## Colours

Exactly two colours per page: `--bg` (ground) and `--ink`. Nothing else gets a colour. No grey tints, no opacity tints, no shadows. The only gradients are the ones that draw rules, rulers and barcodes.

Default is Green. All 13 grounds appear as small buttons in the hero. The choice is saved in `localStorage` under `doc-way` and set as `data-way` on `<html>`. Each button shows a swatch of its ground and ink. The pressed button is filled with ink. There is no light or dark mode. The ground choice replaces it.

| Name | data-way | ground | ink |
|---|---|---|---|
| Green (default) | k-green | #0f5132 | #d7d7d2 |
| Bright | k-bright | #3ecf6e | #2a2d2b |
| Orange | k-orange | #df613a | #f6f1ea |
| Signal | k-signal | #d6d7cf | #f2481c |
| Lime | k-lime | #a7e046 | #111111 |
| Night | k-night | #0a0a0a | #e2ff1a |
| Black | k-black | #0a0a0a | #f6f5ee |
| Slate | k-slate | #6e736d | #0e140c |
| Bone | k-bone | #f0efe8 | #161616 |
| Sand | k-sand | #e5ddc5 | #2e271c |
| Charcoal | k-charcoal | #3e3f44 | #cfcdc8 |
| Lavender | k-lavender | #c4c0c9 | #141414 |
| Mint | k-mint | #e4eae1 | #1d211c |

The starter keys these rules on `[data-way="…"]`, not on `html`, so a swatch element can carry its own `data-way` and draw itself from the same table. Keep that.

## Type

- Mono: `"IBM Plex Mono", "Geist Mono", ui-monospace, monospace`, weight 400. Body is 12px, line height 1.55.
- Sans for values and headlines: `"Inter", "Helvetica Neue", Arial, sans-serif`, weight 500, letter spacing -0.04em.
- Both load from Google Fonts. The link is in the starter head.
- Small labels are 11 to 12px, capitals, letter spacing 0.04 to 0.1em.
- **Never go below 11px** for anything a reader needs to read.
- Spread lines (`.sp`) start at 0.5em letter spacing. The starter script widens them edge to edge when they fit and lets them wrap when they don't.

## Components

All of these are styled and shown working in `assets/starter.html`. Copy the markup from there.

| Class | What it is |
|---|---|
| `.lb` | One label, a flex column. `.lb.box` has a thin wobbly border. `.lb.dsh` has a dashed one. |
| `.hd` | Label header row: a 14px line icon, the title in caps, tags pushed right inside `.r`. |
| `.tag` | Filled ink chip. |
| `.pill` | Outlined round chip. `.pill.no` is dashed, for "not decided" status. |
| `.big` | Large value. `.big.n` numbers at 64px, `.big.p` names at 27px in caps, `.big.s` at 23px. |
| `.cap` | Caption, 11px capitals. |
| `.txt` | Body text, 12px. |
| `.q` | A short question or claim, 15px. |
| `.dim` | Dimension line: end ticks, arrows, the value in the middle. Markup `<div class="dim"><i></i><b>VALUE</b><i></i></div>`. |
| `.bar` | Barcode from repeating gradients. Decorative, `aria-hidden`. |
| `.tick` | Ruler. Decorative. |
| `.rule` | Dashed rule with end ticks. Decorative. |
| `.tb` | Thin key/value grid. `.tb.kv` is one pair per row. `.tb.c2` is two pairs per row and drops to one on phones. Children alternate key, value. |
| `.sec` | Section rule: inverted label `<span class="n">02 / TITLE</span>`, a line `.ln`, a count `.ct`. |
| `table` | Thin grid. Header is ink text on the ground with a 2px bottom rule, never a filled band. Under 620px each row becomes a card and each cell shows its column name from `data-label`. |
| `.top` | Hero. Crop marks at four corners (`.cm.tl/.tr/.bl/.br`), not a full box. Holds `h1` in caps (clamp 46 to 124px), a one-sentence `.lead`, a `.bar`, a `.sp` status line, and the `.ways` ink buttons. |
| `.g2 .g3 .g4` | Grids. 2 columns under 980px, 1 column under 620px. `.stack` is a plain vertical stack. |

### Hand-made feel

A hidden `<svg>` at the top of `<body>` holds two filters. Keep it as `position:absolute; width:0; height:0`. Never `display:none`, which breaks the filters.

- `#k2wob`: feTurbulence plus feDisplacementMap at a small scale. It is applied only to the `::before` border of `.box`, `.dsh` and to the crop marks, so the line wobbles while text stays crisp. Never put it on an element that holds text.
- `#k2ink`: erode plus grain holes. Applied to `.big` and `h1` only.

## Content rules

These matter as much as the look.

- **Plain words.** The page is for the user to act on, not for specialists. Write "Music 1" and "very quiet under your voice", not cue, bed or "-16 dB". If a technical number must appear, put it in one table with a plain-words column beside it.
- **Every short code gets a tooltip.** IDs like N01, B03, R2 get `data-tip="what it means"`. A code that only means something to the author does not go on a plan page at all. Keep those on study or evidence pages.
- **Short sentences. No em dashes.** Easy units: seconds, minutes, words a minute.
- **Lead with the answer.** Section 01 says what the page decides or asks. Open questions go in `.lb.dsh` cards with a `.pill.no` status.
- **Markdown twin.** Every page has a `.md` file with the same content, for the repo and for agents. Generate it from the HTML with a script. Never edit it by hand.

## How to build a page

1. **Plan first.** List the sections, the one decision each section supports, and the numbers it shows. Get the user's yes on the plan before building anything big.
2. **Copy the starter.** Copy `assets/starter.html`. Replace the content inside `<main>` and the hero text. Keep the head, the CSS, the SVG filters and the script.
3. **Data in its own file.** Keep the page data in YAML or JSON and generate the HTML from it with a small script. A change to the data then rebuilds the page. The same script, or a second one, writes the Markdown twin.
4. **Tooltips.** Give every code a `data-tip`. The starter script already shows tips on hover, focus and tap.
5. **Screenshot before showing anyone.** Run through `CHECKLIST.md`: 1280 and 390 wide, in Green and in Bone. Look for overflowing text, labels under 11px, and tables that don't turn into cards on the phone. Fix, then shoot again.
6. **Publish one file.** One self-contained HTML file. Fonts from Google Fonts are the only outside load.
7. **Say what changed.** When showing the user a new version, name what changed since the last one in one line.

## Don'ts

- No third colour, grey, opacity tint, shadow or rounded card. Pills are the only rounded thing.
- No bold. Sans is 500, mono is 400.
- No filled table header.
- No emoji or icon fonts. Icons are small inline SVG line drawings in ink.
- No animation beyond the short fades in the starter. `prefers-reduced-motion` turns those off.
- No dark/light toggle. The ink buttons are the only theme control.
