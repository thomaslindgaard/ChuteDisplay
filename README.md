# Chute Status Display

A real-time HTML-based display system for monitoring chute status on sorting equipment. Designed for 16:9 displays with optimal space utilization and human-friendly navigation.

## Features

### Visual Display

- **Real-time Status**: Live monitoring of chute conditions with color-coded status indicators
- **Responsive Grid**: Automatically calculates optimal layout to fit all chutes on screen without scrolling
- **Full Viewport Usage**: Maximizes screen real estate with minimal padding and optimized spacing
- **Professional Layout**: Clean, modern interface suitable for industrial environments

### Chute Organization

- **Sequential Naming**: Chutes named CHU001, CHU002, etc. with zero-padded 3-digit numbers
- **Maximized Text Display**: Item counts and chute names sized to use maximum available space
- **Human-Friendly Navigation**: Grid layout optimized for quick visual scanning and chute location
- **Column Preferences**: Prioritizes layouts with columns divisible by 10, then by 5 for easy navigation

### Status Indicators

- **🟢 Green (Normal)**: Chute operating normally and accepting items
- **🟠 Orange (Full)**: Chute has reached capacity but is not blocked
- **🔴 Red (Blocked)**: Chute is blocked and cannot accept items

## Configuration

### URL Parameters

You can customize the display using URL parameters:

- **Number of Chutes**: `index.html?chutes=150`
- **Column Override**: `index.html?columns=20` (must be divisible by 10)
- **Combined Parameters**: `index.html?chutes=200&columns=20`
- **Examples**:
  - `index.html` - Uses default 112 chutes with automatic layout
  - `index.html?chutes=80` - Shows exactly 80 chutes
  - `index.html?chutes=200&columns=10` - 200 chutes in 10 columns (20 rows)
  - `index.html?columns=30` - Forces 30 columns regardless of chute count

### Layout Intelligence

The system includes several optimization features:

- **Automatic Chute Sizing**: Uses maximum available screen space for optimal readability
- **Font Maximization**: Item counts and chute names sized to fill available space
- **Column Preferences**: Prioritizes columns divisible by 10, then by 5, for easy navigation
- **Full Height Usage**: Chutes expand to use full vertical space while maintaining width > height
- **Minimal Padding**: Asymmetric padding (reduced horizontal) to maximize text space

## Layout Algorithm

### Grid Calculation

1. **Screen Analysis**: Measures viewport dimensions and available space
2. **Space Allocation**: Accounts for header, legend, and minimal padding
3. **Dimension Optimization**: Ensures chute width > height for better text display
4. **Full Height Usage**: Maximizes vertical space utilization
5. **Responsive Adjustment**: Adapts to window resizing in real-time

### Human Navigation

- **Logical Grouping**: Arranged in rows and columns for systematic scanning
- **Mental Math Friendly**: Easy to calculate chute positions (e.g., CHU087 = row 9, column 7)
- **Bottom Legend**: Horizontal status legend at bottom maximizes chute display area
- **Visual Consistency**: Uniform spacing and sizing across all chutes

## Technical Specifications

### Browser Compatibility

- Modern browsers with CSS Grid support
- JavaScript ES6+ features required
- Responsive design for various screen sizes

### Performance

- **Lightweight**: Pure HTML/CSS/JavaScript, no external dependencies
- **Real-time Updates**: 5-second refresh interval (configurable)
- **Efficient Rendering**: Optimized DOM manipulation for smooth updates

### Display Requirements

- **Optimal**: 16:9 aspect ratio displays (1920×1080, 2560×1440, etc.)
- **Minimum**: 1024×768 resolution
- **Recommended**: Full-screen display for maximum chute visibility

## File Structure

```
ChuteDisplay/
├── index.html          # Main application file
└── README.md          # This documentation
```

## Usage Instructions

### Basic Setup

1. Open `index.html` in a web browser
2. For full-screen operation, press F11 (recommended)
3. The display will automatically optimize for your screen size

### Customization

1. **Set Chute Count**: Add `?chutes=NUMBER` to URL
2. **Monitor Changes**: Status updates automatically every 5 seconds
3. **Interactive Elements**: Click on chutes for additional information

### Integration

For production use, replace the demo data generation with real data from your sorting system:

1. **Locate**: `generateChuteData()` function in the JavaScript
2. **Replace**: Random data generation with API calls to your sorting system
3. **Update**: Refresh interval as needed for your system's requirements

## Customization Options

### Status Colors

Modify the CSS color variables to match your branding:

```css
.chute-normal {
  background-color: #27ae60;
} /* Green */
.chute-full {
  background-color: #f39c12;
} /* Orange */
.chute-blocked {
  background-color: #e74c3c;
} /* Red */
```

### Update Frequency

Change the refresh interval in JavaScript:

```javascript
setInterval(updateChutes, 5000); // 5000ms = 5 seconds
```

### Minimum Chute Size

Adjust minimum dimensions for different screen sizes:

```javascript
if (chuteWidth >= 40 && targetHeight >= 25) // Minimum 40×25px
```

## Troubleshooting

### Common Issues

- **Chutes Too Small**: Reduce the number of chutes or increase screen resolution
- **Text Not Readable**: Check minimum font size calculations in CSS
- **Layout Not Optimal**: Verify screen aspect ratio and available space

### Performance Issues

- **Slow Updates**: Increase update interval or optimize data source
- **Memory Usage**: Ensure proper cleanup of DOM elements during updates

## Development

### Data Structure

Each chute object contains:

```javascript
{
  name: "CHU001",      // Chute identifier (3-digit format)
  count: 42,           // Number of items
  status: "normal"     // Status: normal, full, blocked
}
```

### Key Functions

- `calculateGridLayout()`: Optimizes chute sizing, positioning, and font scaling
- `generateChuteData()`: Creates/updates chute data (replace for production)
- `renderChutes()`: Updates DOM with current chute information
- `getConfigFromURL()`: Parses URL parameters for chute count and column overrides

## License

This project is designed for industrial sorting system monitoring. Customize as needed for your specific requirements.
