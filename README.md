# AFI Junior Points Calculator

A single-page web app that scores junior athletics performances for **U14, U16 and U18** at any competition in India: district, state, zonal or national.
Pick the category, pick the event, type the National Record and the mark, and the points appear instantly. Nothing is pre-filled.

- The **National Record you enter = 1000 points**. No records are built into the page.
- Built on the World Athletics curve shape, rescaled to our junior NRs.
- 48 events: Boys/Girls U14 (4 each), Boys/Girls U16 (8 each), Men/Women U18 (12 each).
- **Meet sheet**: add athletes or paste rows from Excel (Name, State, Category, Event, Mark, optional National Record). Enter the NR once per event. The top score in each category is marked as Best Athlete, and the sheet can be copied as CSV. The sheet clears when the page is closed.

## Formula
| Event type | Points |
|---|---|
| Running / walks | `floor(a × (b − time)²)` (time in seconds) |
| Jumps | `floor(a × (cm + b)² + c)` |
| Throws | `floor(a × (m + b)² + c)` |
| Triathlon / Pentathlon / Heptathlon | same as throws, using the combined total |

The parent table is the senior event each junior event grows into. Examples: 80m Hurdles → 110mH (boys) or 100mH (girls); Kids Javelin → Javelin; Triathlon and Pentathlon → Decathlon (boys) or Heptathlon (girls).

## Records
The user types the National Record for each event. The curve re-anchors so that record scores 1000.

## Hosting
Turn on **Settings → Pages → Deploy from branch → main / root**. The app will be served at
`https://saket12345678.github.io/afi-junior-points-calculator/`.

## Notes
- U14 and U16 Best Athlete awards use these junior points.
- U18 values are for analysis only. The official U18 and U20 awards use World Athletics points on senior equipment.
- Only the derived junior constants are included. The World Athletics scoring library is **not** part of this repo.

## WA Senior Points Calculator
`wa-senior/index.html` scores senior performances with the World Athletics Scoring Tables 2025 and the World Rankings rules:
category, event and competition details start blank; result score from the WA tables, optional National Record comparison, wind modification (100m, 200m, 100mH, 110mH, LJ, TJ: 6 points per m/s, none from 0 to +2.0, −30 with no reading), and placing scores by competition category (OW to F) for finals and rounds before the final.
Live at `https://saket12345678.github.io/afi-junior-points-calculator/wa-senior/`.
