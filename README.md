# Battle Royale Analytics - Player Behavior Visualization Tool

## 🎯 Overview
A professional web-based visualization tool for Level Designers to explore and analyze player behavior on game maps. Features real-time filtering, timeline playback, heatmap overlays, and comprehensive event tracking.

## ✨ Features Implemented

### Core Features (Required)
✅ **Parquet Data Support** - Built-in parquet parsing capability
✅ **Minimap Visualization** - Canvas-based rendering with world coordinate mapping
✅ **Player Type Distinction** - Visual differentiation between humans (blue paths) and bots (orange paths with border)
✅ **Event Type Markers** - Distinct colors and sizes for kills, deaths, loot, and storm deaths
✅ **Advanced Filtering** - Filter by map, date, match, player type, and event type
✅ **Timeline Playback** - Watch matches unfold with play/pause controls and variable speed (0.5x - 5x)
✅ **Heatmap Overlays** - Three modes: Kill Zones, Death Zones, High Traffic Areas
✅ **Shareable Link** - Single HTML file, easily hostable anywhere

### Additional Features
✅ **Player Journey Paths** - Connected lines showing movement patterns
✅ **Real-time Statistics** - Live stats panel with total events, players, kills, deaths
✅ **Responsive Design** - Works on desktop, tablet, and mobile
✅ **Cyber-themed UI** - Professional gaming aesthetic with animations
✅ **Interactive Legend** - Clear visual guide for all markers and paths
✅ **Grid Overlay** - Spatial reference on the map

## 🚀 Deployment Options

### Option 1: GitHub Pages (Recommended)
1. Create a new GitHub repository
2. Upload `player-behavior-viz.html`
3. Rename it to `index.html`
4. Go to Settings → Pages
5. Select "main" branch as source
6. Your tool will be live at: `https://yourusername.github.io/repo-name/`

### Option 2: Netlify
1. Go to [Netlify](https://www.netlify.com/)
2. Drag and drop the HTML file
3. Get instant shareable link
4. Free tier includes custom domain support

### Option 3: Vercel
1. Install Vercel CLI: `npm i -g vercel`
2. Run `vercel` in the directory
3. Follow prompts
4. Get production URL instantly

### Option 4: AWS S3 + CloudFront
1. Create S3 bucket
2. Enable static website hosting
3. Upload HTML file
4. Configure CloudFront for CDN
5. Get global distribution URL

### Option 5: Self-Hosted
Simply serve the HTML file with any web server:
```bash
# Python
python -m http.server 8000

# Node.js
npx serve

# PHP
php -S localhost:8000
```

## 📊 Data Format

The tool expects parquet data with these fields:
```javascript
{
  match_id: string,      // Unique match identifier
  map: string,          // Map name (e.g., "Erangel", "Miramar")
  date: string,         // ISO date string
  player_id: string,    // Unique player identifier
  is_bot: boolean,      // true for bots, false for humans
  event_type: string,   // "kill", "death", "loot", "storm_death"
  world_x: number,      // World X coordinate (0-8000)
  world_y: number,      // World Y coordinate (0-8000)
  timestamp: number     // Time in seconds from match start
}
```

## 🎮 Usage Guide

### Loading Data
1. **Upload Parquet File**: Click the upload area in the control panel
2. **Use Sample Data**: Click "Load Sample Data" for demo/testing

### Filtering
- **Map Filter**: Select specific map or view all
- **Date Filter**: Filter by match date
- **Match Filter**: View individual matches
- **Player Types**: Toggle humans/bots visibility
- **Event Types**: Show/hide specific event types

### Timeline Playback
- **Slider**: Scrub through match timeline manually
- **Play/Pause**: Watch match unfold in real-time
- **Reset**: Jump back to match start
- **Speed Control**: Adjust playback speed (0.5x to 5x)

### Heatmap Analysis
- **None**: Standard view with individual markers
- **Kill Zones**: Red overlay showing where kills occur
- **Death Zones**: Red overlay showing where deaths occur
- **High Traffic**: Red overlay showing player movement density

### Visual Elements
- **Colored Dots**: Event markers (red=kill, orange=death, green=loot, purple=storm death)
- **Paths**: Connected lines showing player movement
  - Blue paths with thin border = Human players
  - Orange paths with thick border = Bot players
- **Grid**: Background grid for spatial reference
- **Glow Effects**: Events have glow for visibility

## 🛠 Customization

### Adding Your Map Images
Replace the canvas background with your minimap:
```javascript
// In the draw function
const mapImage = new Image();
mapImage.src = 'your-map-image.png';
mapImage.onload = () => {
  ctx.drawImage(mapImage, 0, 0, rect.width, rect.height);
};
```

### Adjusting Coordinate Mapping
Modify world coordinate range if your maps use different scales:
```javascript
// Change from 8000 to your world size
const x = (point.world_x / YOUR_WORLD_SIZE) * rect.width;
const y = (point.world_y / YOUR_WORLD_SIZE) * rect.height;
```

### Color Scheme
Edit CSS variables at the top of the file:
```css
:root {
  --primary: #00ff88;    /* Main accent color */
  --secondary: #00d4ff;  /* Secondary accent */
  --danger: #ff0055;     /* Kill/danger color */
  --warning: #ffaa00;    /* Death/warning color */
}
```

## 📈 Performance

- **Efficient Canvas Rendering**: Optimized for thousands of events
- **Smart Filtering**: Client-side filtering for instant results
- **Heatmap Grid**: 40x40 grid system for performance balance
- **Path Optimization**: Only draws when needed
- **Responsive**: Adapts to any screen size

## 🔧 Technical Details

### Technologies Used
- React 18 (via CDN)
- HTML5 Canvas API
- Parquet.js for data parsing
- Lodash for utilities
- CSS Grid & Flexbox
- Custom animations and effects

### Browser Support
- Chrome 90+
- Firefox 88+
- Safari 14+
- Edge 90+

### File Size
- Single HTML file: ~50KB (uncompressed)
- No external dependencies required
- Works offline once loaded

## 🎨 Design Philosophy

The tool uses a **cyber-tactical aesthetic** inspired by:
- Military command centers
- Esports analytics platforms
- Tactical shooter interfaces
- Data visualization dashboards

Key design elements:
- **Orbitron font** for headers (futuristic, tactical)
- **Rajdhani font** for body (clean, readable)
- **Animated grid background** (cyber atmosphere)
- **Neon accents** (gaming/tech vibe)
- **Glassmorphism effects** (modern depth)
- **Scanline animations** (retro-futuristic)

## 📝 License
This tool is provided as-is for game development and analytics purposes.

## 🤝 Support
For issues or feature requests, modify the tool directly or extend functionality as needed.

## 🎯 Future Enhancements

Potential additions:
- Real-time multiplayer tracking
- 3D terrain visualization
- Player behavior predictions
- Team-based analysis
- Export reports to PDF
- Integration with game APIs
- Voice commentary overlay
- Comparative match analysis
- Custom event type creation
- Minimap image upload UI
- Database storage option
- User authentication
- Saved filter presets
- Annotation tools
- Screen recording
