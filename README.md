# FY2027 Budget, Four Ways

An interactive look at the President's proposed Fiscal Year 2027 federal budget, rendered as a field of circles you can slice four ways: every named program, agency toplines, a by-department small-multiples grid, and a percent-change view.

**Live:** https://sdiggs.github.io/fy27-budget/

Each circle is a dollar figure. Area is scaled to the amount, and color follows the budget's own direction of travel: green where a line goes up, red where it comes down. Hover any circle for the figure, the percent change, and the budget's stated rationale.

## Inspiration

This is a direct homage to one of the cleaner "see the whole budget at once" treatments anyone has done: The New York Times' **"Four Ways to Slice Obama's 2013 Budget Proposal"** (updated February 12, 2012).

> https://archive.nytimes.com/www.nytimes.com/interactive/2012/02/13/us/politics/2013-budget-proposal-graphic.html

The visual grammar here borrows heavily from that piece: the circle-packed mass with increases floating up and cuts sinking down, the four-tab structure, the muted sage-and-terracotta diverging palette, the nested-circle size key, and the soft label tints that sit tonally inside each bubble rather than stamping white or black across them. The goal was to point that same lens at a different administration's budget so the two can be read in the same language.

## Source data

All figures are drawn from the primary government document:

> Office of Management and Budget, Executive Office of the President. *Budget of the U.S. Government, Fiscal Year 2027.* April 2026. ISBN 978-0-16-097477-9.
> https://www.whitehouse.gov/wp-content/uploads/2026/04/budget_fy2027.pdf

Agency toplines come from Summary Table S-3 (2027 base discretionary request and 2026 enacted or continuing-resolution levels). Program-level increases and cuts come from the dollar figures named in each department chapter.

## The four views

1. **All Programs.** Every increase or cut the budget chapters name, each circle sized by its dollar change. Increases rise to the top, cuts sink to the bottom.
2. **Agency Totals.** Each agency sized by its 2027 base discretionary request, colored by its percent change from 2026.
3. **By Department.** A small-multiples grid. Each panel is an agency, sized by its request, with its named programs packed inside.
4. **Changes.** Each agency placed vertically by its percent change from 2026, sized by the request.

A second toggle filters any view to increases only, cuts only, or all.

## How to read the encodings

Color uses seven buckets, from the deepest cut through no change to the deepest increase. The bubble fills and the matched, lighter label tints are taken directly from the original NYT color key, so the legend and the circles always agree. Labels are measured against each circle's true geometry and sized to fit, dropping to two lines or disappearing entirely when a word will not fit cleanly inside. The small bubbles speak through the tooltip instead.

## Honest limits

This is the summary volume of the President's Budget, so it has real boundaries worth stating plainly.

* It gives agency toplines cleanly, but only the program changes its authors chose to highlight. It is not the full account-level tree, which lives in the Appendix and Analytical Perspectives volumes.
* A handful of figures are funding levels, multi-year financing, or mandatory funds rather than annual discretionary changes. Examples include Critical Minerals, Foreign Military Financing loan authority, the Presidential Capital Stewardship mandatory fund, and the Infrastructure Investment and Jobs Act balance cancellations. Each of these is flagged in its tooltip.
* The "Budget cites" text in each tooltip paraphrases the document's own stated rationale. It reports the framing in the source, and is not an endorsement of it.
* The original NYT piece also offered a mandatory-versus-discretionary view and a forecast deficit circle. Both are omitted here because the summary volume does not give a clean program-level split or a single 2027 deficit figure, and inventing either would have meant putting numbers in the document's mouth.

Figures are in millions of dollars unless noted otherwise.

## Running it

The whole thing is a single static `index.html` file with no build step. It pulls D3 (v7) from a CDN and the Libre Franklin typeface from Google Fonts, and renders everything client-side. To serve it from this repository on GitHub Pages, rename the visualization file to `index.html` at the repository root, and the site will be live at the URL above.

If you want to run it locally, any static server works:

```
python3 -m http.server 8000
# then open http://localhost:8000
```

## Notes for contributors

The data lives in two arrays near the top of the script, `AG` (agencies) and `PR` (programs). Editing a value, a note, or adding a line item is all it takes to update the chart; there is no separate data file to keep in sync. The color buckets, the label-fitting routine, and the four view builders are each small and self-contained further down.

A reasonable next step would be to pull the account-level tables from the Analytical Perspectives supplemental data so the program layer becomes complete rather than chapter-highlight only, and to add a search box across program names.

## License and attribution

Built by Stephen C. Diggs. The underlying budget figures are a work of the U.S. Government and are in the public domain. The design owes its structure and palette to the NYT graphics team's 2013 original, linked above.
