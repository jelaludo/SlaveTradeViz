# The Scale of Slavery Throughout History

An interactive data visualization showing slavery across 2,700 years, from the Roman Empire to modern forced labor. This project presents eight major slavery systems within a unified comparative framework using a custom-built, horizontally flowing Sankey timeline.

## Features

- **Cross-Historical Comparison**: Visualizes estimated numbers of enslaved people across different systems
- **Geographic & Temporal Precision**: Each system displays exact time spans aligned on a shared BCE/CE timeline
- **Interactive Elements**: Tooltips on flows, clickable destinations for detailed summaries
- **Educational Focus**: Designed for students, educators, researchers, and the general public

## Project Structure

```
.
├── index.html              # Main HTML entry point
├── src/
│   ├── css/
│   │   └── styles.css      # All styles
│   └── js/
│       └── app.js          # React component and D3 visualization
├── public/
│   └── data/
│       └── slavery_data.json  # Data for all slavery systems
├── package.json            # Dependencies and scripts
└── README.md               # This file
```

## Getting Started

### Prerequisites

- Node.js (v14 or higher)
- npm (comes with Node.js)

### Installation

1. Install dependencies:
```bash
npm install
```

### Development

Start the development server with auto-reload:

```bash
npm run dev
```

This will:
- Start a local server on port 3000
- Automatically open your browser
- Watch for file changes and reload the page automatically

The visualization will be available at `http://localhost:3000`

### Making Changes

- **Styles**: Edit `src/css/styles.css` - changes will auto-reload
- **Visualization Logic**: Edit `src/js/app.js` - changes will auto-reload
- **Data**: Edit `public/data/slavery_data.json` - changes will auto-reload
- **HTML Structure**: Edit `index.html` - changes will auto-reload

## The Eight Systems Visualized

1. **Roman Empire** (753 BCE - 476 CE) — 5-15M estimated
2. **Trans-Saharan Trade** (650-1900 CE) — 6-10M estimated
3. **Crimean/Black Sea** (1440s-1783) — 1-3M estimated
4. **Indian Ocean Trade** (1st-20th Century) — ~8M estimated
5. **Barbary Corsairs** (1500s-1830s) — 1-1.25M estimated
6. **Red Sea Trade** (Ancient-1962) — 0.5-1M estimated
7. **Transatlantic Trade** (1500-1867) — 10-12.8M estimated
8. **Modern Slavery** (2021) — ~50M people currently enslaved

## Technologies Used

- **React** (via CDN) - Component structure
- **D3.js** (via CDN) - Data visualization
- **Babel Standalone** (via CDN) - JSX transformation
- **live-server** - Development server with auto-reload

## Deployment

For production deployment, you can:

1. Simply upload all files to a web server (the project uses CDN links for dependencies)
2. Or use a static site hosting service like:
   - Netlify
   - Vercel
   - GitHub Pages
   - Any static file hosting

No build step is required - the project works as-is with CDN dependencies.

## License

MIT

