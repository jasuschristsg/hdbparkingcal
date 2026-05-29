# HDB Parking Calculator — Handover Notes

## Repo
`https://github.com/jasuschristsg/hdbparkingcal`
File: `hdb-parking-calculator.html` (single self-contained file, no dependencies)

## Live URL
`https://jasuschristsg.github.io/hdbparkingcal/hdb-parking-calculator.html`

---

## Rates (Outside Central Area)
- $0.60 per half-hour block
- Day cap: $12 per day window (7am–10:30pm)
- Night cap: $5 per night window (10:30pm–7am), NPS car parks only

## Free Parking
- Free day period (7am–10:30pm) on Sundays and Public Holidays
- PH in-lieu: if PH falls on Sunday, following Monday is also free
- PH dates hardcoded for 2024–2027, computed from `SG_PUBLIC_HOLIDAYS` Set in the script

## To Update Public Holidays
Find this block in the HTML file and add/edit dates in `YYYY-MM-DD` format:
```js
const SG_PUBLIC_HOLIDAYS = new Set([
  // 2027
  '2027-01-01', ...
]);
```
In-lieu Mondays are auto-computed — no need to hardcode them.

## Toggles
- **NPS toggle** — enables the $5 night cap
- **FPS toggle** — enables free parking on Sundays/PHs

## Key Functions

| Function | What it does |
|---|---|
| `splitPeriods(start, end)` | Splits session into day/night windows |
| `calcPeriod(period, nps, fps)` | Calculates charge for one window, applies cap |
| `isFreeDay(d)` | Returns true if Sunday, PH, or in-lieu Monday |
| `calculate()` | Main function triggered by the button |

---

## How to Edit in Claude Cowork
1. Open Claude Cowork
2. Click **Select Folder** and point it to the folder containing `hdb-parking-calculator.html`
3. Tell Claude: *"Edit the file `hdb-parking-calculator.html` in my selected folder"* and describe what you want changed
4. Claude can read, edit and save directly — no copy-pasting needed

## Source References
- [HDB Short-Term Parking Charges](https://www.hdb.gov.sg/parking/other-parking-matters/shortterm-parking/shortterm-parking-charges)
- [Free Parking Scheme](https://www.hdb.gov.sg/parking/other-parking-matters/shortterm-parking/free-parking-scheme-on-sundays-and-public-holidays)
- [MOM Public Holidays 2025](https://www.mom.gov.sg/newsroom/press-releases/2024/0805-public-holidays-for-2025)
- [MOM Public Holidays 2026](https://www.mom.gov.sg/newsroom/press-releases/2025/0616-public-holidays-for-2026)
