# 📰 iPad Passive News Ticker

A lightweight, full-screen news ticker designed for iPad that displays RSS feed headlines in a continuous horizontal scroll. Perfect for use as a passive digital bulletin board or information display.

![Version](https://img.shields.io/badge/Version-1.0.0-blue) ![Status](https://img.shields.io/badge/Status-Active-brightgreen) ![GitHub Pages](https://img.shields.io/badge/Hosted-GitHub%20Pages-blue) ![License](https://img.shields.io/badge/License-MIT-green)

## ✨ Features

- **Continuous Auto-Scrolling** - Headlines scroll horizontally without user interaction
- **Multiple RSS Feeds** - Aggregate news from various sources
- **Dark/Light Mode** - Toggle between themes with preference persistence
- **Adjustable Speed** - Control scroll speed (20s - 120s per cycle)
- **Auto-Refresh** - Automatically updates feeds every 10 minutes
- **iPad Optimized** - Responsive design for iPad display
- **Guided Access Ready** - Perfect for kiosk mode on iPad
- **Safari Compatible** - Fully functional on iOS Safari
- **Touch Controls** - Pause/play, refresh, and speed adjustment
- **CORS Proxy** - Fetches RSS feeds without CORS issues

## 🚀 Quick Start

### Option 1: GitHub Pages (Recommended)

1. **Fork this repository** to your GitHub account
2. Go to **Settings** → **Pages**
3. Set **Source** to `main` branch and `/` (root) folder
4. Click **Save**
5. Your ticker will be live at `https://yourusername.github.io/sw-ipad-news-ticker/`

### Option 2: Local Development

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/sw-ipad-news-ticker.git
   cd sw-ipad-news-ticker
   ```

2. Open `index.html` in your browser:
   ```bash
   # Using Python
   python -m http.server 8000
   
   # Or just open directly
   open index.html
   ```

3. Visit `http://localhost:8000` in your browser

## ⚙️ Configuration

### Customizing RSS Feeds

Edit the `CONFIG.feeds` array in `index.html` (around line 325):

```javascript
const CONFIG = {
    feeds: [
        'https://feeds.bbci.co.uk/news/rss.xml',
        'https://rss.nytimes.com/services/xml/rss/nyt/HomePage.xml',
        'https://feeds.npr.org/1001/rss.xml',
        'https://www.theguardian.com/world/rss',
        'https://www.wired.com/feed/rss'
    ],
    refreshInterval: 10 * 60 * 1000, // 10 minutes in milliseconds
    corsProxy: 'https://api.allorigins.win/raw?url='
};
```

### Adjusting Refresh Interval

Change the `refreshInterval` value (in milliseconds):
- 5 minutes: `5 * 60 * 1000`
- 15 minutes: `15 * 60 * 1000`
- 30 minutes: `30 * 60 * 1000`

### Changing Default Speed

Modify the CSS variable in the `:root` selector:

```css
:root {
    --scroll-speed: 60s; /* Default is 60 seconds */
}
```

## 📱 iPad Setup

### Full-Screen Mode

1. Open the page in Safari on your iPad
2. Tap the **Share** button
3. Select **Add to Home Screen**
4. Name it "News Ticker" and tap **Add**
5. Open from home screen for full-screen experience

### Guided Access (Kiosk Mode)

1. Go to **Settings** → **Accessibility** → **Guided Access**
2. Enable **Guided Access**
3. Set a passcode
4. Open the News Ticker app
5. Triple-click the **Side Button** (or Home button)
6. Configure accessibility options
7. Tap **Start** to lock into the app

### Prevent Sleep

To keep the display always on:
1. Go to **Settings** → **Display & Brightness**
2. Set **Auto-Lock** to **Never**

## 🎨 Customization

### Colors & Theme

Edit CSS variables in the `:root` selector:

```css
:root {
    --bg-color: #0a0a0a;           /* Background color */
    --text-color: #ffffff;          /* Text color */
    --accent-color: #00ffff;        /* Accent/highlight color */
    --separator-color: #333333;     /* Separator color */
}
```

### Font Size

Adjust `.ticker-item` font size:

```css
.ticker-item {
    font-size: 2em; /* Increase or decrease as needed */
}
```

### Animation Style

Change animation timing function for different effects:

```css
animation: scroll-horizontal var(--scroll-speed) linear infinite;
/* Try: ease, ease-in, ease-out, ease-in-out */
```

## 🔧 Troubleshooting

### Feeds Not Loading

**Issue**: Headlines show "Loading..." indefinitely

**Solutions**:
- Check console for CORS errors
- Verify RSS feed URLs are accessible
- Try alternative CORS proxy: `https://corsproxy.io/?`
- Some feeds may block proxy access - try different feeds

### Scroll Too Fast/Slow

**Issue**: Ticker speed is not comfortable

**Solutions**:
- Use the speed slider in the footer
- Adjust default speed in CSS (`:root { --scroll-speed: 60s; }`)
- For iPad landscape, try 45-60s; for portrait, try 30-45s

### White Screen on iPad

**Issue**: Page appears blank on iPad Safari

**Solutions**:
- Clear Safari cache (Settings → Safari → Clear History)
- Ensure JavaScript is enabled
- Check if Guided Access restrictions are blocking
- Try refreshing the page

### Theme Not Persisting

**Issue**: Theme resets on page reload

**Solutions**:
- Check if Safari is blocking localStorage
- Disable "Prevent Cross-Site Tracking" for this site
- Clear cookies and site data, then set theme again

## 🌐 Custom Domain Setup

1. Edit the `CNAME` file and replace `your-domain.com` with your domain:
   ```
   ticker.yourdomain.com
   ```

2. Add a DNS record at your domain provider:
   - **Type**: CNAME
   - **Name**: ticker (or subdomain of choice)
   - **Value**: yourusername.github.io

3. Wait for DNS propagation (up to 48 hours)

## 📋 Popular RSS Feed Sources

### News
- BBC News: `https://feeds.bbci.co.uk/news/rss.xml`
- New York Times: `https://rss.nytimes.com/services/xml/rss/nyt/HomePage.xml`
- NPR: `https://feeds.npr.org/1001/rss.xml`
- The Guardian: `https://www.theguardian.com/world/rss`
- Reuters: `https://www.reutersagency.com/feed/`

### Tech
- Wired: `https://www.wired.com/feed/rss`
- TechCrunch: `https://techcrunch.com/feed/`
- The Verge: `https://www.theverge.com/rss/index.xml`
- Hacker News: `https://news.ycombinator.com/rss`

### Sports
- ESPN: `https://www.espn.com/espn/rss/news`
- BBC Sport: `https://feeds.bbci.co.uk/sport/rss.xml`

## 🤝 Contributing

Contributions are welcome! Feel free to:
- Report bugs via GitHub Issues
- Submit feature requests
- Open pull requests with improvements

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

## 🙏 Acknowledgments

- CORS Proxy provided by [AllOrigins](https://allorigins.win/)
- Font: Apple System Font (-apple-system)
- Icons: Emoji (native browser rendering)

## 📞 Support

If you encounter issues or have questions:
1. Check the [Troubleshooting](#-troubleshooting) section
2. Search [existing issues](https://github.com/Stuow22/sw-ipad-news-ticker/issues)
3. Open a new issue with details

---

**Made with ❤️ for passive information display**

*Last updated: November 2025*