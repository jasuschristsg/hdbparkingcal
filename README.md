# HDB Parking Calculator

A browser-based calculator for estimating HDB short-term parking charges (Outside Central Area). Enter your start and end time to get a full cost breakdown, with support for multi-day stays, capped periods, and free parking days.

**[Open the calculator](https://jasuschristsg.github.io/hdbparkingcal/hdb-parking-calculator.html)** — no install, no sign-up, works offline once loaded.

## Features
- Calculates charges in 30-minute blocks at $0.60/block
- Per-period caps: $12/day (7am–10:30pm), $5/night (10:30pm–7am)
- Night Parking Scheme (NPS) toggle
- Free Parking Scheme (FPS) toggle — automatically applies free parking on Sundays and Public Holidays (2024–2027)
- PH in-lieu support — if a Public Holiday falls on a Sunday, the following Monday is treated as free
- Collapsible day-by-day charge breakdown, with capped/free blocks visually marked
- No dependencies, no internet required — single self-contained HTML file

## Usage
1. Open the [live calculator](https://jasuschristsg.github.io/hdbparkingcal/hdb-parking-calculator.html) (or open `hdb-parking-calculator.html` directly in any browser).
2. Enter a **Start Date & Time** and **End Date & Time**.
3. Leave **NPS** and **FPS** toggled on unless your car park doesn't offer them (see [Toggles](#toggles) below).
4. Click **Calculate Charges** to see the total cost, duration, and a day-by-day breakdown.
5. Click any day in the breakdown to expand it and see the charge for each 30-minute block.

## How Charges Are Calculated
Each parking session is split into alternating **day** and **night** windows:

| Window | Time Range | Rate | Cap |
|---|---|---|---|
| Day | 7:00am – 10:30pm | $0.60 / 30 min | $12.00 (per day window) |
| Night | 10:30pm – 7:00am | $0.60 / 30 min | $5.00 (per night window, NPS car parks only) |

- A session spanning multiple days/nights is broken into separate windows, each capped independently.
- The final 30-minute block of a session is charged in full even if you park for less than 30 minutes into it.
- If **Free Parking Scheme (FPS)** is on and a day window falls entirely on a Sunday, Public Holiday, or PH-in-lieu Monday, that whole day window is free.

### Toggles
| Toggle | Effect when ON | Effect when OFF |
|---|---|---|
| **Night Parking Scheme (NPS)** | Night charges capped at $5.00 | Night charges accrue at $0.60/block with no cap |
| **Free Parking Scheme (FPS)** | Day windows on Sundays/PH/PH-in-lieu are free | All days charged normally, including Sundays/PH |

Turn a toggle off if your specific car park doesn't participate in that scheme — check signage at the car park or the [HDB source pages](#references) below.

## Example
Parking from **Saturday 8:00pm** to **Sunday 9:00am**:
- 8:00pm–10:30pm (Sat, day window): 5 blocks × $0.60 = $3.00
- 10:30pm–7:00am (night window, NPS capped): capped at $5.00
- 7:00am–9:00am (Sun, day window): free under FPS (Sunday)
- **Total: $8.00**

## Public Holiday Data
Public Holiday dates are hardcoded for 2024–2027 in the `SG_PUBLIC_HOLIDAYS` set inside the script. PH-in-lieu Mondays are computed automatically — you don't need to add them manually. See [HANDOVER.md](HANDOVER.md) for instructions on updating these dates for future years.

## Development
This is a single self-contained HTML file (`hdb-parking-calculator.html`) with inline CSS and vanilla JavaScript — no build step, no package manager, no dependencies.

To make changes:
1. Edit `hdb-parking-calculator.html` directly.
2. Open the file in a browser to test.
3. Commit and push — [GitHub Pages](https://jasuschristsg.github.io/hdbparkingcal/hdb-parking-calculator.html) serves the file directly from the repo.

For a map of the key functions and maintenance notes (e.g. updating Public Holiday dates), see [HANDOVER.md](HANDOVER.md).

## References
- [HDB Short-Term Parking Charges](https://www.hdb.gov.sg/parking/other-parking-matters/shortterm-parking/shortterm-parking-charges)
- [Free Parking Scheme](https://www.hdb.gov.sg/parking/other-parking-matters/shortterm-parking/free-parking-scheme-on-sundays-and-public-holidays)
- [MOM Public Holidays 2025](https://www.mom.gov.sg/newsroom/press-releases/2024/0805-public-holidays-for-2025)
- [MOM Public Holidays 2026](https://www.mom.gov.sg/newsroom/press-releases/2025/0616-public-holidays-for-2026)

## Disclaimer
This tool provides an estimate only. Always verify actual charges against official HDB signage and rates, as schemes and rates may change.

## License
[MIT](LICENSE)
