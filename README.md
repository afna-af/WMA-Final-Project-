# WMA-Final-Project-


<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Virtual Art Gallery</title>
    <link rel="stylesheet" href="style.css" />
  </head>
  <body>
    <!-- Hero Banner -->
    <header class="hero">
      <div class="img">
        <img src="" alt="" />
        <div class="content">
          <h1>Virtual Art Gallery</h1>

          <p class="p">
            Explore creativity through images, videos, and interactive
            experiences
          </p>
        </div>
      </div>
    </header>

    <!-- Navigation -->
    <nav class="navbar">
      <ul>
        <li><a href="#gallery">Gallery</a></li>
        <li><a href="#video">Video Tour</a></li>
        <li><a href="#contact">Contact</a></li>
      </ul>
    </nav>

    <!-- Gallery Section -->
    <section id="gallery" class="gallery">
      <h2>Featured Artworks</h2>
      <div class="grid">
        <div class="art-card">
          <img
            src="abbs.jpeg"
            alt="Abstract Painting"
            width="250px"
            height="300px"
          />
          <p>Abstract Dreams</p>
        </div>
        <div class="art-card">
          <img
            src="landscape.jpg"
            alt="Landscape Painting"
            width="250px"
            height="300px"
          />
          <p>Serene Landscape</p>
        </div>
        <div class="art-card">
          <img
            src="-time_less-.jpg"
            alt="Portrait"
            width="250px"
            height="300px"
          />
          <p>Timeless Portrait</p>
        </div>
      </div>
    </section>

    <!-- Video Section -->
    <section id="video" class="video">
      <h2>Gallery Walkthrough</h2>
      <video autoplay loop muted>
        <source src="vdo.mp4" type="video/mp4" />
        Your browser does not support the video tag.
      </video>
    </section>

    <!-- Contact -->
    <section id="contact" class="contact">
      <h2>Contact Us</h2>
      <form id="contactForm">
        <input type="text" placeholder="Your Name" required />
        <input type="email" placeholder="Your Email" required />
        <textarea placeholder="Your Message"></textarea>
        <button type="submit">Send</button>
      </form>
    </section>

    <!-- Footer -->
    <footer>
      <p>&copy; 2026 Virtual Art Gallery</p>
    </footer>

    <script src="script.js"></script>
  </body>
</html>
/* style.css */
body {
  font-family: Arial, sans-serif;
  margin: 0;
  background: #f9f9f9;
  color: #333;
}

.hero {
  background: url("ig.jpg") center/cover no-repeat;
  text-align: center;
  padding: 80px 20px;
  color: white;
  font-size: 50px;
  align-items: center;
}
.p {
  color: white;
  font-size: 25px;
}

.navbar {
  background: #222;
  padding: 10px;
}

.navbar ul {
  list-style: none;
  display: flex;
  justify-content: center;
}
.navbar li {
  margin: 0 15px;
}
.navbar a {
  color: white;
  text-decoration: none;
}

.gallery {
  padding: 40px;
}
.grid {
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
}
.art-card {
  flex: 1 1 30%;
  background: white;
  padding: 10px;
  box-shadow: 0 2px 6px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s;
}
.art-card:hover {
  transform: scale(1.05);
}

.video,
.contact {
  padding: 40px;
  text-align: center;
}

form input,
form textarea {
  display: block;
  width: 80%;
  margin: 10px auto;
  padding: 10px;
}
button {
  background: #222;
  color: white;
  padding: 10px 20px;
  border: none;
  cursor: pointer;
}
button:hover {
  background: #444;
}

footer {
  background: #222;
  color: white;
  text-align: center;
  padding: 15px;
}
// script.js

// Contact form submission alert
document.getElementById("contactForm").addEventListener("submit", function (e) {
  e.preventDefault();
  alert("Thank you for contacting us! We'll reply soon.");
});

// Simple gallery filter (example)
const artworks = document.querySelectorAll(".art-card");
function filterGallery(keyword) {
  artworks.forEach((card) => {
    if (card.textContent.toLowerCase().includes(keyword.toLowerCase())) {
      card.style.display = "block";
    } else {
      card.style.display = "none";
    }
  });
}
// Example usage: filterGallery("Landscape");
