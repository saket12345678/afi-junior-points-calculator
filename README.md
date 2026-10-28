# AFI Junior Points Calculator

A single-page web app that scores junior athletics performances for **U14, U16 and U18**.
Pick the category, pick the event, type the mark, and the points appear instantly.

- The Indian **National Record in each event = 1000 points**.
- Built on the World Athletics curve shape, rescaled to our junior NRs.
- 48 events: Boys/Girls U14 (4 each), Boys/Girls U16 (8 each), Men/Women U18 (12 each).
- Includes a **Best Athlete sheet**: add rows, and the top score per category is highlighted. It can preload the 2026 Junior Nationals medallists.

## Formula
| Event type | Points |
|---|---|
| Running / walks | `floor(a × (b − time)²)` (time in seconds) |
| Jumps | `floor(a × (cm + b)² + c)` |
| Throws | `floor(a × (m + b)² + c)` |
| Triathlon / Pentathlon / Heptathlon | same as throws, using the combined total |

The parent table is the senior event each junior event grows into. Examples: 80m Hurdles → 110mH (boys) or 100mH (girls); Kids Javelin → Javelin; Triathlon and Pentathlon → Decathlon (boys) or Heptathlon (girls).

## Updating a record
Edit the event's `nr` value inside `index.html`. The curve re-anchors itself so that the new record scores 1000. No other change is needed.

## Hosting
Turn on **Settings → Pages → Deploy from branch → main / root**. The app will be served at
`https://saket12345678.github.io/afi-junior-points-calculator/`.

## Notes
- U14 and U16 Best Athlete awards use these junior points.
- U18 values are for analysis only. The official U18 and U20 awards use World Athletics points on senior equipment.
- Only the derived junior constants are included. The World Athletics scoring library is **not** part of this repo.
