#### @Thekentucian and I made this simple flight tracker web app to show our kiddos more about the immediate planes flying overhead. Requires no registration and uses free libraries only (Leaflet library to show OpenStreetMap, additional airplane details from ADSBdb), and will work for about 30 minutes per day via unauthenticated calls to OpenSky Network.

---

### Core Functionality
* **Displays a Map:** It uses the Leaflet library to show an interactive map from OpenStreetMap.
* **Fetches Live Flight Data:** Every 15 seconds, it contacts the **OpenSky Network API** to get real-time information about airplanes currently flying within the visible map area.
* **Tracks the Closest Planes:** The application identifies the **three airplanes** that are physically closest to a designated "Home Location" on the map.
* **Enriches Flight Details:** For those three planes, it makes a second API call to **ADSBdb** to get more specific details like the aircraft model and the flight route (origin and destination airports).
* **Visualizes Planes on the Map:** It displays the three closest planes as custom airplane icons. These icons are rotated to show the actual direction the plane is flying.
* **Shows Flight Path:** It draws a blue line (a "polyline") behind each tracked plane to show its recent flight path.

---

### User Interface and Features
* **Permanent Tooltips:** Each plane has an always-visible label that shows:
    * Aircraft model (e.g., Boeing 737)
    * Flag emoji of the origin country and the flight callsign
    * The flight route (e.g., `DEN > LAX`)
    * The distance from the user's location
* **Clickable Popups:** Clicking on a plane icon reveals a popup with more detailed information, including speed, altitude, and the time of the last data update.
* **User Location:** A "Detect My Location" button allows the user to center the map on their current geographical position.
* **Pause/Continue:** A button allows the user to pause and resume the automatic 15-second data refresh, which is useful for preventing API rate-limiting errors.
* **Notifications:** A banner at the top of the screen can display messages, such as a warning if the API rate limit has been reached.
