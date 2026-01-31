# Amateur Radio Digital Dashboard

A modern, configuration-driven web dashboard for amateur radio stations. Features a cyberpunk-inspired terminal aesthetic with real-time clock displays, dynamic node information, and comprehensive network resource links.

![Dashboard Preview](screenshot.png)

## Features

- **🎨 Cyberpunk Terminal Aesthetic** - Animated grid background, scanline effects, and glowing text
- **⚙️ JSON-Driven Configuration** - Update all content by editing a single config file
- **📡 Multi-Network Support** - AllStarLink, EchoLink, HOIP, DMR, D-STAR, and more
- **🕐 Real-Time Clocks** - Live UTC and local time displays
- **📱 Responsive Design** - Works on desktop, tablet, and mobile devices
- **🔗 Quick Links** - Organized navigation to all your node tools and resources
- **⚡ No Server Required** - Pure HTML/CSS/JavaScript static site

## Quick Start

1. **Download** the files to your web server directory:
   ```bash
   git clone https://github.com/yourusername/amateur-radio-dashboard.git
   cd amateur-radio-dashboard
   ```

2. **Edit** `config.json` with your station information (see Configuration section below)

3. **Deploy** to your web server or open `index.html` directly in a browser

That's it! No build process, no dependencies.

## File Structure

```
amateur-radio-dashboard/
├── index.html          # Main dashboard template
├── config.json         # Configuration file (EDIT THIS!)
└── README.md          # This file
```

## Configuration

All dashboard content is controlled by `config.json`. Simply edit this file to customize for your station.

### Configuration Sections

#### 1. Station Information
```json
"station": {
  "callsign": "N0CALL",
  "organization": "Your Organization Name",
  "primaryNodes": {
    "asl": "123456",
    "echolink": "654321",
    "hoipInbound": "99999"
  },
  "additionalNodes": ["123457", "123458"],
  "aprsSSID": "N0CALL-13",
  "location": "City, ST",
  "network": "AllStarLink 3 • DVSwitch"
}
```

#### 2. Status Panels (Radio IDs)
```json
"statusPanels": {
  "radioId": {
    "dmrId1": "1234567",
    "dmrId2": "1234568",
    "nxdnId": "--"
  }
}
```

#### 3. Connection Instructions
Supports HTML formatting with custom highlight classes for DTMF commands:
- `<span class="highlight-secondary">` - Green highlight for DTMF commands (e.g., `*3`)
- `<span class="highlight">` - Yellow highlight for parameters (e.g., node numbers)

```json
"connectionInstructions": {
  "allstarlink": {
    "label": "AllStarLink",
    "instruction": "Dial <span class=\"highlight-secondary\">*3</span><span class=\"highlight\">123456</span> from any ASL node"
  }
}
```

#### 4. Navigation Links
Organize your links into logical sections:

```json
"navigation": {
  "nodeTools": {
    "title": "Node Tools",
    "links": [
      {"label": "Supermon", "url": "https://123456.nodes.allstarlink.org/supermon/"},
      {"label": "DVSwitch", "url": "https://123456.nodes.allstarlink.org/dvswitch/"}
    ]
  }
}
```

Included sections:
- Node Tools
- ASL Nodes
- Affiliate Nodes
- AllStarLink Network
- DMR Networks
- D-STAR Network
- Other Resources
- AMPR / 44Net

#### 5. Footer
```json
"footer": {
  "callsign": "N0CALL",
  "organization": "Your Organization",
  "primaryNode": "123456",
  "echolinkNode": "654321",
  "website": "yourwebsite.com"
}
```

## Customization

### Color Scheme
Edit CSS variables in `index.html` (around line 11):

```css
:root {
    --primary: #00ff41;        /* Primary green glow */
    --secondary: #ff6b00;      /* Secondary orange */
    --bg-dark: #0a0e1a;        /* Dark background */
    --bg-panel: #151b2e;       /* Panel background */
    --border: #1e2942;         /* Border color */
    --text-primary: #e8f4f8;   /* Primary text */
    --text-dim: #7a8ea8;       /* Dimmed text */
}
```

### Fonts
The dashboard uses:
- **Orbitron** - Headers and callsign display
- **Share Tech Mono** - Body text and monospaced content

To change fonts, modify the Google Fonts import in the `<head>` section.

### Animations
The dashboard includes several animated effects:
- Grid background scroll
- Scanline overlay
- Text glow pulses
- Border sweeps

To disable animations, comment out the corresponding `@keyframes` sections in the CSS.

## Network Integration

### AllStarLink
The dashboard is designed to integrate with:
- Supermon (node monitoring)
- Allmon3 (multi-node display)
- AllScan (frequency scanner)
- SkywarnPlus-NG (weather alerts)

### DVSwitch
Full support for DVSwitch digital voice modes:
- DMR (via Brandmeister, TGIF)
- D-STAR
- NXDN
- P25

### Additional Networks
- EchoLink node linking
- HOIP (Hams Over IP) telephone interconnect
- APRS tracking integration
- AMPR/44Net IP addressing

## Deployment

### Static Web Hosting
Upload `index.html` and `config.json` to any web server:
- Apache
- Nginx
- lighttpd
- Python SimpleHTTPServer
- Any static hosting service (GitHub Pages, Netlify, etc.)

### Local Testing
```bash
# Python 3
python3 -m http.server 8000

# Python 2
python -m SimpleHTTPServer 8000

# Then open: http://localhost:8000
```

### Nginx Configuration Example
```nginx
server {
    listen 80;
    server_name yourdomain.com;
    root /var/www/html/dashboard;
    index index.html;
    
    location / {
        try_files $uri $uri/ =404;
    }
}
```

## Examples

### Example Configurations

**Hub Station:**
```json
{
  "station": {
    "callsign": "W0XYZ",
    "organization": "Repeater Network Hub",
    "primaryNodes": {
      "asl": "100001",
      "echolink": "200001",
      "hoipInbound": "30001"
    }
  }
}
```

**Emergency Communications:**
```json
{
  "station": {
    "callsign": "N0EMG",
    "organization": "County Emergency Services",
    "primaryNodes": {
      "asl": "555000",
      "echolink": "555001",
      "hoipInbound": "55500"
    },
    "network": "AllStarLink 3 • ARES/RACES"
  }
}
```

**Personal Station:**
```json
{
  "station": {
    "callsign": "K0ABC",
    "organization": "Personal Digital Node",
    "primaryNodes": {
      "asl": "999888",
      "echolink": "777666",
      "hoipInbound": "99988"
    }
  }
}
```

## Browser Compatibility

Tested and working on:
- ✅ Chrome/Chromium (latest)
- ✅ Firefox (latest)
- ✅ Safari (latest)
- ✅ Edge (latest)
- ✅ Mobile browsers (iOS Safari, Chrome Mobile)

## Performance

- **Load Time:** < 1 second
- **No External Dependencies:** All CSS/JS is inline
- **Minimal Bandwidth:** ~50KB total (HTML + JSON)
- **Low CPU:** Efficient animations using CSS transforms

## Troubleshooting

### Config not loading?
1. Check that `config.json` is in the same directory as `index.html`
2. Verify JSON syntax with a validator like [JSONLint](https://jsonlint.com/)
3. Check browser console (F12) for error messages

### Links not working?
1. Ensure URLs in `config.json` include `https://` or `http://`
2. Check for proper JSON escaping of special characters

### Clock not updating?
JavaScript must be enabled in your browser.

## Contributing

Contributions welcome! Areas for enhancement:
- Additional theme color schemes
- More animation options
- Node status API integration
- QSO logging features
- Weather widget integration

## License

This project is provided "as-is" for amateur radio use. Feel free to modify and distribute.

**73 DE [YOUR CALL]**

## Credits

Created for the amateur radio community by operators who wanted a modern, easy-to-maintain station dashboard.

Special thanks to:
- AllStarLink community
- DVSwitch developers
- Amateur radio digital mode pioneers

---

*For questions, issues, or feature requests, please open an issue on GitHub.*

**Last Updated:** January 2026
