# MacMobility

**An interactive explorer of open urban-mobility data — traffic, transit, collisions, and cycling — city by city.**

MacMobility turns a city's public mobility datasets into one cohesive, map-driven dashboard. It currently covers **Hamilton, Ontario**, visualizing ten open datasets across nine themed views, with the platform built so additional cities can be added as their open data is incorporated.

🔗 **Live site:** `[[https://<your-username>.github.io/macmobility/`]

---

## What it does

From a landing page you choose a city, then move between tabs that each tell a different part of the mobility story:

| Tab | What it shows |
|-----|----------------|
| **Map** | Traffic signals (City & MTO) and ITS devices on a dark basemap, with a glowing "vessel" road network — arteries and capillaries — and a cursor-following reach field with a heartbeat pulse. |
| **Collisions** | A cross-filtered analytics dashboard over ~83,000 collision records (2013–2023): severity, light, surface, control type, road class, pedestrian/cyclist involvement, and more. Click any chart to filter every other chart. |
| **Bike Share** | Live-snapshot dock stations colored by availability, an animated rebalancing flow along real roads, a pulsing low-stock indicator, and a chase-cam trip animation. |
| **Transit** | All HSR stops and routes, animated buses, a stop-density "terrain" heightfield that shifts as you pan, amenity filters, and street-routed walking distances between stops. |
| **Ridership** | HSR ridership and service trends (2014–2025), including the COVID collapse and recovery, on-time performance, cancelled hours, safety, and top routes. |
| **Truck Routes** | The designated heavy-truck network by road class, with restricted and part-time segments highlighted. |
| **Traffic Volume** | Average Daily Traffic counts (2000–2024): volume distribution, busiest corridors, survey cadence, and a growth explorer for locations measured in multiple years. |
| **Bike Parking** | 822 rack locations / ~7,800 spaces. Find the nearest rack by GPS, address search, or map click; ride a street-following chase-cam route with a top-down rider and live speed; and a cursor-following density heat field that beats faster and redder where parking clusters. |
| **Bikeways** | Hamilton's real cycling infrastructure network by facility type (lanes, tracks, trails, shoulders, signed and suggested routes), existing vs. planned, with km totals. Also overlayable beneath the Bike Parking rides. |

## Highlights

- **One self-contained file.** Everything — data, styling, and logic — lives in a single `index.html`. No backend, no build step, no database.
- **Consistent dark "traffic-management-centre" aesthetic** across every view.
- **Real routing.** Trip and walking routes follow the street network via a public routing service, with graceful fallback to straight-line estimates when the service is unavailable.
- **Honest framing.** Routes and travel times are clearly labelled as visualizations, not verified navigation or safe cycling routes; estimate-based figures are flagged throughout.

## Tech

- [Leaflet](https://leafletjs.com/) for mapping, with [CARTO](https://carto.com/) dark basemap tiles
- Custom SVG/Canvas for charts, heat fields, and animations (no charting library)
- [OSRM](https://project-osrm.org/) public API for routing; [OpenStreetMap Nominatim](https://nominatim.org/) for geocoding
- All geometry reprojected from NAD83 UTM Zone 17N to WGS84 and simplified for the browser

## Data & attribution

All datasets are published as **open data by the City of Hamilton** on its Open Data portal — [open.hamilton.ca](https://open.hamilton.ca) — and are used here under those open-access terms. MacMobility only visualizes this public data and adds no proprietary information. As other cities are added, each city's open-data source will be acknowledged in the same way.

> **Note on routing & estimates:** Trip routes and travel times are illustrative visualizations generated from public routing services and the road network. They are **not** verified navigation or safe cycling routes — always confirm a safe route yourself before riding.

## Running locally

Because the map tiles, routing, and geocoding are loaded over the network, open the file through a local web server rather than `file://` for full functionality:

```bash
# from the folder containing index.html
python3 -m http.server 8000
# then visit http://localhost:8000
```

The "find nearest rack → use my GPS location" feature requires HTTPS (or `localhost`), so it works on the deployed site and via `localhost`, but not from a plain `file://` open.

## Deployment

Hosted free on **GitHub Pages** — upload `index.html` to a public repository and enable Pages (Settings → Pages → deploy from `main` / root). HTTPS is provided automatically. See `HOW_TO_PUBLISH.md` for the full walkthrough.

## Author

**MacMobility** was created by **Amir Hossein Karbasi**, PhD Candidate in Transportation Engineering, McMaster University, under the supervision of **Dr. Hao Yang**, Associate Professor, McMaster University.

## License

The application code is released under the MIT License. The underlying datasets remain the property of the City of Hamilton and are subject to the [City of Hamilton Open Data terms](https://open.hamilton.ca).
