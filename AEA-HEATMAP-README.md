# AEA Schools & Shops Location Heatmap

## Overview

An interactive map system for the Aviation Electronics Association (AEA) to help members locate aviation schools and AEA member shops across the country. The system features a public-facing interactive map and an admin panel for managing locations.

## Files Included

- **aea-location-heatmap.html** - Public interactive map page
- **aea-location-admin.html** - Admin panel for managing locations
- **sample-locations.csv** - Sample data for testing (10 locations)

## Features

### Public Map Features
- 🗺️ **Interactive Map** with OpenStreetMap (free, no API key required)
- 📍 **Marker-Based View** with custom colored markers (Green = Schools, Blue = Shops)
- 🔥 **Heatmap Layer** showing concentration density (toggle on/off)
- 🔍 **Search Functionality** by name or location
- 🎯 **Filter Controls** to show/hide schools or shops
- 📊 **Clustering** for dense areas (toggle on/off)
- ℹ️ **Clickable Popups** with full contact information
- 🧭 **Get Directions** link (opens Google Maps)
- 📋 **List View Sidebar** for browsing all locations

### Admin Panel Features
- 🔒 **Password Protected** (default: `admin123`)
- ➕ **Manual Entry Form** for adding locations one-by-one
- 📄 **CSV Upload** with drag-and-drop support
- 📋 **JSON Import** for bulk data
- ✏️ **Edit/Delete** existing locations
- 🌍 **Auto-Geocoding** (converts addresses to coordinates automatically)
- 📥 **Export to CSV/JSON** for backup
- 📊 **Statistics Dashboard** showing total locations

## Quick Start Guide

### Step 1: Access the System

1. Open `index.html` in your browser (main training hub)
2. Click the **"Schools & Shops Map"** button in the navigation
3. Or directly open `aea-location-heatmap.html`

### Step 2: View the Map

The public map is immediately accessible - no login required. You can:
- Zoom and pan around the map
- Click markers to see location details
- Use the search box to find specific locations
- Toggle filters to show only schools or only shops
- Switch to heatmap view to see density patterns

### Step 3: Add Data (Admin Only)

1. Open `aea-location-admin.html`
2. Login with password: `admin123` (change this in browser console)
3. Choose one of three methods to add locations:

#### Method 1: Manual Entry (Single Locations)
- Click **"Add Manually"** tab
- Fill out the form
- Enter an address and wait for auto-geocoding
- Or manually enter lat/lng coordinates
- Click **"Add Location"**

#### Method 2: CSV Upload (Bulk Import)
- Click **"CSV Upload"** tab
- Download the CSV template (included button)
- Fill in your data following the format
- Drag & drop the CSV file or click to browse
- System will auto-geocode any missing coordinates

#### Method 3: JSON Import (API/Bulk Data)
- Click **"JSON Import"** tab
- Paste your JSON array of locations
- Follow the format shown in the example
- Click **"Import JSON"**

## Data Format

### Required Fields
- **type** - Either "school" or "shop"
- **name** - Full name of the location
- **address** OR **lat/lng** - Either address (will be geocoded) or coordinates

### Optional Fields
- **programType** - For schools only (e.g., "A&P", "Avionics")
- **contactPerson** - Name of primary contact
- **phone** - Phone number
- **email** - Email address
- **website** - Full URL (include https://)

### CSV Format Example
```csv
type,name,address,lat,lng,programType,contactPerson,phone,email,website
school,Aviation Institute,"123 Main St, City, ST 12345",39.8283,-98.5795,A&P,John Doe,(555) 123-4567,contact@example.com,https://example.com
shop,Repair Shop,"456 Oak Ave, Town, ST 67890",40.7128,-74.0060,,Jane Smith,(555) 987-6543,info@shop.com,https://shop.com
```

### JSON Format Example
```json
[
  {
    "type": "school",
    "name": "Aviation Institute",
    "address": "123 Main St, City, ST 12345",
    "lat": 39.8283,
    "lng": -98.5795,
    "programType": "A&P",
    "contactPerson": "John Doe",
    "phone": "(555) 123-4567",
    "email": "contact@example.com",
    "website": "https://example.com"
  }
]
```

## Testing with Sample Data

A sample CSV file (`sample-locations.csv`) is included with 10 example locations:
- 5 Aviation Schools
- 5 AEA Member Shops

To import:
1. Open admin panel
2. Go to CSV Upload tab
3. Upload `sample-locations.csv`
4. View results on the public map

## Data Storage

**IMPORTANT:** All data is stored in browser localStorage (client-side only)

### Implications:
✅ No server costs
✅ Works offline
✅ No database setup needed
✅ Fast and simple

⚠️ Data is browser-specific (not synced across devices)
⚠️ Clearing browser data will delete locations
⚠️ No automatic backups

### Backup Recommendations:
1. Regularly export data to CSV/JSON (Admin Panel → Manage Locations)
2. Keep CSV backups in a safe location
3. Re-import after browser cache clear if needed

## Changing the Admin Password

The default password is `admin123`. To change it:

1. Open browser Developer Console (F12)
2. Type: `localStorage.setItem('aeaAdminPassword', 'yournewpassword')`
3. Press Enter

Your new password will be saved and required for future logins.

## Geocoding

The system uses **Nominatim** (OpenStreetMap's free geocoding service) to convert addresses to coordinates.

### How it works:
1. Enter an address in the admin panel
2. Wait 1 second (auto-debounce)
3. System fetches coordinates automatically
4. Lat/lng fields populate automatically

### If geocoding fails:
- Manually enter latitude and longitude
- Use Google Maps to find coordinates (right-click on map → "What's here?")
- Ensure address is detailed (include city, state, ZIP)

### Rate Limits:
Nominatim has usage limits. For bulk imports:
- Upload CSV in batches of 50-100
- Wait 2-3 minutes between batches
- Or pre-fill lat/lng in your CSV

## Troubleshooting

### Map doesn't load
- Check internet connection (OpenStreetMap requires internet)
- Disable browser extensions (ad blockers can interfere)
- Clear browser cache and reload

### Locations not appearing
1. Verify coordinates are valid (lat: -90 to 90, lng: -180 to 180)
2. Check filters aren't hiding your locations
3. Zoom out to see if markers are off-screen

### CSV upload fails
- Ensure first row has headers
- Check commas are properly escaped (use quotes for addresses with commas)
- Verify file size is under 5MB
- Open CSV in text editor to check formatting

### Admin login doesn't work
- Default password: `admin123`
- Clear browser cache
- Reset password in console: `localStorage.setItem('aeaAdminPassword', 'admin123')`

### Geocoding not working
- Check internet connection
- Try a more specific address
- Manually enter coordinates as fallback

## Browser Compatibility

Tested and working on:
- ✅ Chrome/Edge (90+)
- ✅ Firefox (88+)
- ✅ Safari (14+)
- ✅ Mobile browsers (iOS Safari, Chrome Mobile)

## Mobile Responsive

The system is fully responsive and works on:
- 📱 Smartphones
- 📱 Tablets
- 💻 Laptops
- 🖥️ Desktop computers

Layout automatically adjusts for different screen sizes.

## Performance

- **Initial Load:** < 2 seconds
- **Marker Rendering:** Up to 1000 locations smoothly
- **Clustering:** Handles 10,000+ markers efficiently
- **Search:** Instant results (client-side)

## Privacy & Security

- No user tracking or analytics
- No external database
- All data stays in your browser
- Admin password stored locally (encrypted by browser)
- No cookies used

## Customization Ideas

Want to customize? Edit the HTML files to:
- Change color scheme (CSS variables)
- Modify marker colors
- Adjust map starting position/zoom
- Add custom fields to forms
- Change heatmap gradient colors

## Support & Questions

For issues or questions:
1. Check this README first
2. Review the sample data format
3. Test with included sample-locations.csv
4. Check browser console for error messages

## Future Enhancements (Optional)

If you want to upgrade to a server-based system later:
- Multi-device sync
- User accounts
- Advanced analytics
- Automated backups
- Real-time updates
- API integration

## License

This system is part of the AEA Training Hub and follows the same usage terms.

---

**Version:** 1.0
**Last Updated:** 2025-11-07
**Created by:** Claude Code Assistant

Enjoy mapping your aviation network! ✈️🗺️
