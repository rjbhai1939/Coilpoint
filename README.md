<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>My Village Website</title>
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <link 
    rel="stylesheet" 
    href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css" 
    crossorigin=""
  />
  <style>
    body {
      font-family: Arial;
      background: #f0f0f0;
      margin: 0;
      padding: 0;
      text-align: center;
    }

    header {
      background-color: #4CAF50;
      padding: 20px;
      color: white;
      font-size: 24px;
    }

    .upload-box {
      margin: 20px auto;
      background: white;
      padding: 20px;
      width: 90%;
      max-width: 400px;
      border-radius: 10px;
    }

    .gallery {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 10px;
      padding: 10px;
    }

    .gallery img {
      width: 180px;
      height: auto;
      border-radius: 8px;
      box-shadow: 0 0 5px #888;
    }

    #map {
      height: 400px;
      width: 95%;
      margin: 20px auto;
      border: 2px solid #ccc;
      border-radius: 10px;
    }
  </style>
</head>
<body>

  <header>🌾 Welcome to My Village Website</header>

  <!-- Upload Form -->
  <div class="upload-box">
    <h2>Upload Photo</h2>
    <form action="upload.php" method="POST" enctype="multipart/form-data">
      <input type="file" name="photo" required><br><br>
      <button type="submit">Upload</button>
    </form>
  </div>

  <!-- Gallery Section -->
  <h2>📸 Photo Gallery</h2>
  <div class="gallery">
    <?php
      $images = glob("uploads/*.{jpg,jpeg,png,gif}", GLOB_BRACE);
      foreach ($images as $img) {
        echo "<img src='$img' />";
      }
    ?>
  </div>

  <!-- Map Section -->
  <h2>🗺 Village Location</h2>
  <div id="map"></div>

  <script 
    src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js" 
    crossorigin="">
  </script>
  <script>
    var map = L.map('map').setView([25.276987, 82.972989], 14); // Change coordinates

    L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
      attribution: '&copy; OpenStreetMap contributors'
    }).addTo(map);

    L.marker([25.276987, 82.972989]).addTo(map)
      .bindPopup('📍 मेरा गाँव')
      .openPopup();
  </script>

</body>
</html
