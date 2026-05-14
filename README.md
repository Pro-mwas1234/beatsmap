# 🎵 BeatMaps - Rhythmic GPS Navigation

A GPS navigation app that synchronizes turn-by-turn directions with the beat of your music, ensuring your favorite songs are never interrupted.

## Features

- 🗺️ **MapLibre GL + OpenFreeMap** vector maps (no API key required)
- 🎵 **Music Synchronization** - directions timed to your music's beat
- 📍 **Real-time GPS** tracking with geolocation
- 🛣️ **OSRM Routing** with up to 3 alternative routes
- 🔍 **Destination Search** via OpenStreetMap Nominatim
- ⛽ **Nearby Stops** - fuel, food, hotels, EV charging stations
- 🔊 **Voice Guidance** with adjustable pace
- 🌙 **Dark Mode** optimized for night driving
- 👆 **Large Touch Controls** for safe driving

## 🐳 Docker Deployment

### Quick Start with Docker Compose (Recommended)

```bash
# Build and run
docker-compose up -d

# Access the app
open http://localhost:8080
```

### Manual Docker Build

```bash
# Build the image
docker build -t beatmaps .

# Run the container
docker run -d -p 8080:80 --name beatmaps beatmaps

# Access the app
open http://localhost:8080
```

### Docker Commands

```bash
# Stop the container
docker-compose down

# View logs
docker-compose logs -f

# Rebuild after changes
docker-compose up -d --build

# Remove everything
docker-compose down -v
```

## 🚀 Running Without Docker

### Option 1: Direct Browser (Simplest)
1. Download `beatmaps.html`
2. Double-click to open in your browser
3. Allow location permissions when prompted

### Option 2: Local Web Server

**Python 3:**
```bash
python3 -m http.server 8000
```

**Node.js:**
```bash
npx http-server -p 8000
```

Then open: `http://localhost:8000/beatmaps.html`

## 📱 Usage Instructions

1. **Grant Permissions**
   - Allow location access for GPS tracking
   - Allow audio access for voice directions

2. **Load Your Music**
   - Tap "Load Music" button
   - Select an audio file from your device
   - The app will detect the beat/BPM

3. **Search Destination**
   - Type your destination in the search bar
   - Select from search results

4. **Choose Route**
   - Review alternative routes
   - Select your preferred option

5. **Start Navigation**
   - Tap "Start Navigation"
   - Voice directions will sync with your music's beat!

## 🛠️ Technical Stack

- **Maps**: MapLibre GL + OpenFreeMap
- **Routing**: OSRM (Open Source Routing Machine)
- **Geocoding**: Nominatim (OpenStreetMap)
- **POI Data**: Overpass API
- **Audio**: Web Audio API + Speech Synthesis
- **Server**: Nginx (Docker deployment)

## 🌐 Browser Requirements

- Modern browser with HTML5 support
- Geolocation API support
- Web Audio API support
- Speech Synthesis API support

**Recommended Browsers:**
- Chrome/Chromium (Desktop & Mobile)
- Safari (iOS/macOS)
- Firefox
- Edge

## 📡 Network Requirements

The app connects to these external services:
- `tiles.openfreemap.org` - Map tiles
- `router.project-osrm.org` - Route calculation
- `nominatim.openstreetmap.org` - Location search
- `overpass-api.de` - Nearby places

## 🔒 Security & Privacy

- No API keys required
- No data collection or tracking
- Music files stay on your device
- Location data is not transmitted to any server
- All routing/search uses public APIs

## 📄 License

Open source - feel free to modify and use!

## 🤝 Contributing

Contributions welcome! Areas for improvement:
- Advanced BPM detection algorithms
- Offline map caching
- Route optimization
- Additional voice languages
- Music streaming service integration

## 🐛 Troubleshooting

**Location not working?**
- Ensure location services are enabled
- Grant browser permission for location
- Try HTTPS or localhost (required for geolocation)

**Voice directions not working?**
- Check browser supports Speech Synthesis
- Ensure device volume is up
- Try different browser

**Music not loading?**
- Use common formats (MP3, WAV, OGG)
- Check file isn't corrupted
- Try smaller file size

**Maps not loading?**
- Check internet connection
- Verify no firewall blocking map tiles
- Try refreshing the page

## 📞 Support

For issues or questions, check the browser console for error messages.

---

Made with ❤️ for music lovers who navigate
