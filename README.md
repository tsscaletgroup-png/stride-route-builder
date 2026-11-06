# Stride — Running Route Builder

A browser-based running route planner hosted on GitHub Pages. It uses Leaflet and OpenStreetMap for the map, Valhalla pedestrian routing to follow mapped roads and paths, and Open-Meteo elevation data for an approximate ascent estimate.

## Features

- Click the map to place a start, intermediate stops, and a finish.
- Routes are matched to pedestrian-accessible streets, footways, and paths.
- Drag markers to move points; reorder or delete intermediate points.
- Calculate route distance and estimated elevation gain.
- Export the routed geometry as a GPX track.
- Share route links that encode the ordered waypoint coordinates.
- Save and restore a local draft in the current browser.

## Open the app

After GitHub Pages finishes its first deployment, open:

<https://tsscaletgroup-png.github.io/stride-route-builder/>

## How it works

The app is a static single-page site. It has no build step, backend, API key, or user account requirement. Map display uses Leaflet and OpenStreetMap tiles. Pedestrian routing is requested from the public Valhalla demo endpoint (`https://valhalla1.openstreetmap.de/route`). Elevation is sampled using the Open-Meteo Elevation API (`https://api.open-meteo.com/v1/elevation`).

The elevation model is coarse (about 90 m terrain resolution), so ascent is an estimate and may miss small trail undulations, stairs, bridges, or other short climbs. The public routing, elevation, and tile endpoints are intended for prototype use and are subject to availability and fair-use policies. For production traffic, use appropriately provisioned services or self-hosted routing and review each provider's current terms.

## Sharing and privacy

A share link contains the route name and ordered waypoint coordinates in its URL fragment. Anyone with the link can view the route. The app does not upload routes to a database. Unshared drafts are saved only in the browser's local storage on that device.

## Deployment

The workflow in `.github/workflows/deploy-pages.yml` deploys the repository root to GitHub Pages on every push to `main` and can also be run manually from the Actions tab. In repository Settings → Pages, set **Build and deployment → Source** to **GitHub Actions** if the workflow has not enabled Pages automatically.
