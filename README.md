# Herb-map
A map where people can post locations to find herbs and spices to use for cooking in medicine
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Herb Locator Map</title>
  <link
    rel="stylesheet"
    href="https://unpkg.com/leaflet@1.9.3/dist/leaflet.css"
    integrity="sha256-sA+eCH/nH6kPftItj+oTFKnAJ0eDRXK11qkLGz9PKyU="
    crossorigin=""
  />
  <style>
    #map {
      height: 90vh;
      width: 100%;
    }
    body {
      margin: 0;
      font-family: Arial, sans-serif;
    }
    #info {
      padding: 10px;
      background: #f8f8f8;
    }
  </style>
</head>
<body>
  <div id="info">
    Click on the map to add a herb location.
  </div>
  <div id="map"></div>

  <script
    src="https://unpkg.com/leaflet@1.9.3/dist/leaflet.js"
    integrity="sha256-DvM/nl4b2Nh/kryN5lvIp/jqz+zjgs+lCkF6bCfYwYQ="
    crossorigin=""
  ></script>
  <script>
    // Initialize the map and set view to a default location
    const map = L.map('map').setView([40.7128, -74.006], 13); // New York City coords for example

    // Add OpenStreetMap tile layer
    L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
      attribution:
        'Map data © <a href="https://openstreetmap.org">OpenStreetMap</a> contributors',
    }).addTo(map);

    // Listen for clicks on the map to add herb markers
    map.on('click', function (e) {
      const marker = L.marker(e.latlng).addTo(map);
      marker.bindPopup('<b>Herb Location</b><br>Latitude: ' + e.latlng.lat.toFixed(5) + '<br>Longitude: ' + e.latlng.lng.toFixed(5)).openPopup();
    });
  </script>
</body>
</html>
