# Puzzlite

A geography guessing game where you drop a satellite image snippet onto the correct location on a map. Built with vanilla HTML, CSS, and JavaScript, powered by Leaflet and Esri satellite imagery.

<!-- Optional: add a screenshot or GIF here once you have one -->
<!-- ![Gameplay screenshot](screenshot.png) -->

## How to Play

1. Open `index.html` in a modern web browser.
2. Select a **region** and/or **country** from the menu.
3. Choose a **game mode**.
4. Click **Play**.
5. Drag the floating satellite piece to where you think it was taken.
6. Click **✔ Place Here** to confirm your guess.
7. Earn points based on how close your guess is to the actual location.

## Game Modes

- **Match**: 5 rounds. Score as many points as possible.
- **Infinite**: Keep playing rounds with no limit.
- **Time Trial**: Score as much as you can before time runs out.
- **Blitz**: 5 rounds, 30 seconds each.

Enable **Hard Mode** to disable panning and zooming for an extra challenge.

## Features

- 🗺️ Interactive map with Esri satellite imagery
- 🖼️ Real satellite image snippets cropped from the map
- 🎯 Distance-based scoring (up to 1000 points per round)
- 🏆 Global leaderboard via Google Apps Script
- 📱 Mobile-friendly touch controls
- 🌐 Filter cities by region or country

## File Structure

```
.
├── index.html   # Main game UI and logic
├── cities.json  # City data with coordinates and region tags
└── README.md    # This file
```

## City Data Format

`cities.json` contains an array of city objects. City names are intentionally stored in their **local/original form** (endonyms) rather than English exonyms — for example `Xixón` instead of `Gijón`, `Lisboa` instead of `Lisbon`, and `Beograd` instead of `Belgrade.

```json
{
  "country": "Spain",
  "city": "Xixón",
  "lat": 43.5357,
  "lng": -5.6615,
  "radius": 7000,
  "regions": ["Northern Mediterranean", "Mediterranean"]
}
```

| Field | Description |
|-------|-------------|
| `country` | Country name |
| `city` | City name in its local/original form |
| `lat` | Latitude |
| `lng` | Longitude |
| `radius` | Search radius in metres for generating satellite crops |
| `regions` | Region tags used for filtering |

## Requirements

- A modern web browser with JavaScript enabled
- An internet connection (for map tiles and optional leaderboard)

## Running Locally

No build step or dependencies are required. Simply serve the files with any static file server, for example:

```bash
python3 -m http.server 8000
```

Then open `http://localhost:8000` in your browser.

## Leaderboard Setup (Optional)

The game works fully offline without any leaderboard. If you want a global leaderboard, you can connect it to a Google Apps Script web app. To enable it:

1. Create a new Google Apps Script project.
2. Deploy it as a web app that accepts `GET` and `POST` requests.
3. Update the `LEADERBOARD_URL` constant in `index.html` with your deployed web app URL.

If no leaderboard URL is configured, the game still works locally but cannot save or load global scores.

## Technologies

- [Leaflet](https://leafletjs.com/) – interactive maps
- [Esri World Imagery](https://www.arcgis.com/home/item.html?id=10df2279f9684f4a9f6a7f08febac2a9) – satellite tiles
- Vanilla JavaScript, HTML, and CSS

## Contributing

Contributions are welcome! When adding cities:

- Use the **local/original form** of the city name.
- Include accurate latitude and longitude coordinates.
- Tag each city with the appropriate region(s).
- Keep the JSON valid and consistent with the existing format.
- Validate `cities.json` after editing, for example with:

  ```bash
  python3 -m json.tool cities.json > /dev/null && echo "Valid JSON"
  ```

## Licence

This project is provided as-is for personal and educational use.
