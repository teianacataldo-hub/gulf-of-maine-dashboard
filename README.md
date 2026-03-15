# Gulf of Maine Ocean Dashboard
**Teiana Cataldo — Northeastern University**

Interactive dashboard for exploring DOPPIO and GOMOFS ocean model output across the Gulf of Maine (2007–2025) at 2 km resolution.

[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/teianacataldo-hub/gulf-of-maine-dashboard/HEAD?urlpath=%2Fdoc%2Ftree%2Focean_dashboard.ipynb)

---

## Variables
- **Temperature** (°C) — DOPPIO
- **Salinity** (psu) — DOPPIO
- **Depth-averaged velocity Ubar / Vbar** (m/s) — DOPPIO
- **Surface currents U / V** (m/s) — GOMOFS

## How to use
1. Click the **Launch Binder** badge above
2. Wait for the environment to build (5–15 min first time)
3. Run **Cell 1** — downloads data from Google Drive (~20–40 min for the NetCDF)
4. Run **Cell 2** — launches the dashboard
5. Use the **Variable** and **Map metric** dropdowns to explore mean values and coefficient of variation across the study area
6. Click any point on the map to set **Location A** (blue), click again to set **Location B** (red)
7. Use the **Neighborhood** dropdown to average over a surrounding pixel window instead of a single pixel
8. Press **▶ Plot Time Series** to generate four plots comparing A and B:
   - Full record time series (2007–2025)
   - Year-over-year seasonal cycles
   - Monthly distribution box plots
   - GOMOFS data presence (for current variables only)
9. Press **✕ Reset Locations** to clear and pick new points

## Data
| File | Source | Size |
|------|--------|------|
| Combined DOPPIO + GOMOFS NetCDF | Google Drive | ~10 GB |
| HydroRIVERS shapefile | Google Drive | ~150 MB |
| Study area shapefile | Google Drive | small |

All data downloads automatically when Cell 1 is run. No manual setup needed.

## Notes
- Data coverage: DOPPIO 2007–2024, GOMOFS 2018–2025, overlap 2018–2024
- Grid resolution: 2 km (resampled to GOMOFS extent, DOPPIO native resolution)
- Resampling method: bilinear interpolation
- Map stats (mean, CV) are computed lazily via dask — first load per variable takes a few minutes
- Stats are cached for the session so switching back to a variable is instant
