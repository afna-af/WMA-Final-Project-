# WMA-Final-Project-
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Virtual Art Gallery</title>
    <link
      rel="stylesheet"
      href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css"
    />
    <style>
      /* Reset and Base Styles */
      * {
        margin: 0;
        padding: 0;
        box-sizing: border-box;
      }

      html {
        scroll-behavior: smooth;
      }

      body {
        font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
        line-height: 1.6;
        color: #333;
        background: linear-gradient(135deg, #f5f7fa 0%, #c3cfe2 100%);
      }

      /* Hero Section */
      .hero {
        height: 100vh;
        background: linear-gradient(rgba(0, 0, 0, 0.7), rgba(0, 0, 0, 0.5)),
          url("https://images.unsplash.com/photo-1563089145-599997674d42?ixlib=rb-4.0.3&auto=format&fit=crop&w=1600&q=80");
        background-size: cover;
        background-position: center;
        background-attachment: fixed;
        display: flex;
        align-items: center;
        justify-content: center;
        text-align: center;
        color: white;
        padding: 0 20px;
      }

      .hero-content {
        max-width: 800px;
        animation: fadeIn 1.5s ease-out;
      }

      .hero-text h1 {
        font-size: 4rem;
        margin-bottom: 1rem;
        text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);
        background: linear-gradient(45deg, #ff6b6b, #4ecdc4);
        -webkit-background-clip: text;
        -webkit-text-fill-color: transparent;
        background-clip: text;
      }

      .subtitle {
        font-size: 1.5rem;
        margin-bottom: 2rem;
        opacity: 0.9;
      }

      .cta-button {
        display: inline-block;
        padding: 15px 40px;
        background: linear-gradient(45deg, #ff6b6b, #4ecdc4);
        color: white;
        text-decoration: none;
        border-radius: 50px;
        font-size: 1.1rem;
        font-weight: bold;
        transition: all 0.3s ease;
        border: none;
        cursor: pointer;
        box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
      }

      .cta-button:hover {
        transform: translateY(-3px);
        box-shadow: 0 6px 20px rgba(0, 0, 0, 0.3);
        background: linear-gradient(45deg, #ff5252, #26a69a);
      }

      /* Navigation */
      .navbar {
        position: fixed;
        top: 0;
        width: 100%;
        background: rgba(255, 255, 255, 0.95);
        backdrop-filter: blur(10px);
        z-index: 1000;
        box-shadow: 0 2px 20px rgba(0, 0, 0, 0.1);
      }

      .nav-container {
        max-width: 1200px;
        margin: 0 auto;
        padding: 1rem 2rem;
        display: flex;
        justify-content: space-between;
        align-items: center;
      }

      .logo {
        font-size: 1.8rem;
        font-weight: bold;
        color: #2c3e50;
        text-decoration: none;
      }

      .nav-menu {
        display: flex;
        list-style: none;
        gap: 2rem;
      }

      .nav-menu a {
        color: #2c3e50;
        text-decoration: none;
        font-weight: 500;
        padding: 0.5rem 1rem;
        border-radius: 5px;
        transition: all 0.3s ease;
      }

      .nav-menu a:hover {
        background: linear-gradient(45deg, #ff6b6b, #4ecdc4);
        color: white;
      }

      .hamburger {
        display: none;
        cursor: pointer;
      }

      .bar {
        display: block;
        width: 25px;
        height: 3px;
        margin: 5px auto;
        background-color: #2c3e50;
        transition: all 0.3s ease;
      }

      /* Gallery Section */
      .gallery {
        padding: 100px 20px;
        max-width: 1200px;
        margin: 0 auto;
      }

      .section-header {
        text-align: center;
        margin-bottom: 60px;
      }

      .section-header h2 {
        font-size: 3rem;
        color: #2c3e50;
        margin-bottom: 1rem;
        position: relative;
        display: inline-block;
      }

      .section-header h2::after {
        content: "";
        position: absolute;
        bottom: -10px;
        left: 50%;
        transform: translateX(-50%);
        width: 100px;
        height: 4px;
        background: linear-gradient(45deg, #ff6b6b, #4ecdc4);
        border-radius: 2px;
      }

      .section-header p {
        font-size: 1.2rem;
        color: #666;
        max-width: 600px;
        margin: 0 auto;
      }

      .grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
        gap: 30px;
        margin-top: 50px;
      }

      .art-card {
        background: white;
        border-radius: 15px;
        overflow: hidden;
        box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
        transition: all 0.3s ease;
        cursor: pointer;
      }

      .art-card:hover {
        transform: translateY(-10px);
        box-shadow: 0 20px 40px rgba(0, 0, 0, 0.2);
      }

      .art-image {
        height: 300px;
        overflow: hidden;
      }

      .art-image img {
        width: 100%;
        height: 100%;
        object-fit: cover;
        transition: transform 0.5s ease;
      }

      .art-card:hover .art-image img {
        transform: scale(1.1);
      }

      .art-info {
        padding: 25px;
      }

      .art-info h3 {
        font-size: 1.5rem;
        color: #2c3e50;
        margin-bottom: 10px;
      }

      .art-info p {
        color: #666;
        margin-bottom: 10px;
      }

      .artist {
        display: inline-block;
        padding: 5px 15px;
        background: linear-gradient(45deg, #ff6b6b, #4ecdc4);
        color: white;
        border-radius: 20px;
        font-size: 0.9rem;
      }

      /* Video Section */
      .video-section {
        padding: 100px 20px;
        background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
        color: white;
      }

      .video-container {
        max-width: 1200px;
        margin: 0 auto;
        display: grid;
        grid-template-columns: 2fr 1fr;
        gap: 40px;
        align-items: start;
      }

      .video-wrapper {
        position: relative;
        border-radius: 15px;
        overflow: hidden;
        box-shadow: 0 20px 40px rgba(0, 0, 0, 0.3);
      }

      .video-wrapper video {
        width: 100%;
        display: block;
        border-radius: 15px;
      }

      .video-controls {
        position: absolute;
        bottom: 20px;
        left: 50%;
        transform: translateX(-50%);
        display: flex;
        gap: 10px;
        background: rgba(0, 0, 0, 0.7);
        padding: 10px 20px;
        border-radius: 25px;
      }

      .control-btn {
        background: none;
        border: none;
        color: white;
        font-size: 1.2rem;
        cursor: pointer;
        padding: 5px 10px;
        transition: color 0.3s ease;
      }

      .control-btn:hover {
        color: #4ecdc4;
      }

      .video-description {
        padding: 20px;
      }

      .video-description h3 {
        font-size: 2rem;
        margin-bottom: 20px;
      }

      .video-description p {
        margin-bottom: 30px;
        line-height: 1.8;
      }

      .tour-info {
        display: flex;
        flex-direction: column;
        gap: 15px;
      }

      .info-item {
        display: flex;
        align-items: center;
        gap: 15px;
      }

      .info-item i {
        font-size: 1.5rem;
        color: #4ecdc4;
      }

      /* Contact Section */
      .contact {
        padding: 100px 20px;
        max-width: 1200px;
        margin: 0 auto;
      }

      .contact-container {
        display: grid;
        grid-template-columns: 1fr 1fr;
        gap: 50px;
        margin-top: 50px;
      }

      .contact-info {
        display: grid;
        grid-template-columns: 1fr 1fr;
        gap: 30px;
      }

      .info-card {
        background: white;
        padding: 30px;
        border-radius: 15px;
        text-align: center;
        box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
        transition: all 0.3s ease;
      }

      .info-card:hover {
        transform: translateY(-5px);
        box-shadow: 0 15px 35px rgba(0, 0, 0, 0.15);
      }

      .info-card i {
        font-size: 2.5rem;
        color: #4ecdc4;
        margin-bottom: 20px;
      }

      .info-card h3 {
        color: #2c3e50;
        margin-bottom: 10px;
      }

      .info-card p {
        color: #666;
        line-height: 1.6;
      }

      .contact-form {
        background: white;
        padding: 40px;
        border-radius: 15px;
        box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
      }

      .form-group {
        margin-bottom: 25px;
      }

      .form-group input,
      .form-group textarea {
        width: 100%;
        padding: 15px;
        border: 2px solid #eee;
        border-radius: 10px;
        font-size: 1rem;
        transition: all 0.3s ease;
      }

      .form-group input:focus,
      .form-group textarea:focus {
        outline: none;
        border-color: #4ecdc4;
        box-shadow: 0 0 0 3px rgba(78, 205, 196, 0.2);
      }

      .submit-btn {
        width: 100%;
        padding: 15px;
        background: linear-gradient(45deg, #ff6b6b, #4ecdc4);
        color: white;
        border: none;
        border-radius: 10px;
        font-size: 1.1rem;
        font-weight: bold;
        cursor: pointer;
        transition: all 0.3s ease;
        display: flex;
        justify-content: center;
        align-items: center;
        gap: 10px;
      }

      .submit-btn:hover {
        background: linear-gradient(45deg, #ff5252, #26a69a);
        transform: translateY(-2px);
        box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
      }

      /* Footer */
      footer {
        background: #2c3e50;
        color: white;
        padding: 60px 20px 20px;
      }

      .footer-content {
        max-width: 1200px;
        margin: 0 auto;
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
        gap: 40px;
        margin-bottom: 40px;
      }

      .footer-section h3,
      .footer-section h4 {
        margin-bottom: 20px;
        color: white;
      }

      .footer-section p {
        margin-bottom: 20px;
        opacity: 0.8;
      }

      .social-icons {
        display: flex;
        gap: 15px;
        margin-top: 20px;
      }

      .social-icons a {
        display: inline-flex;
        align-items: center;
        justify-content: center;
        width: 40px;
        height: 40px;
        background: rgba(255, 255, 255, 0.1);
        border-radius: 50%;
        color: white;
        text-decoration: none;
        transition: all 0.3s ease;
      }

      .social-icons a:hover {
        background: linear-gradient(45deg, #ff6b6b, #4ecdc4);
        transform: translateY(-3px);
      }

      .footer-section ul {
        list-style: none;
      }

      .footer-section ul li {
        margin-bottom: 10px;
      }

      .footer-section ul a {
        color: rgba(255, 255, 255, 0.8);
        text-decoration: none;
        transition: all 0.3s ease;
      }

      .footer-section ul a:hover {
        color: #4ecdc4;
        padding-left: 5px;
      }

      .newsletter-form {
        display: flex;
        gap: 10px;
        margin-top: 20px;
      }

      .newsletter-form input {
        flex: 1;
        padding: 10px;
        border: none;
        border-radius: 5px;
        background: rgba(255, 255, 255, 0.1);
        color: white;
      }

      .newsletter-form input::placeholder {
        color: rgba(255, 255, 255, 0.6);
      }

      .newsletter-form button {
        padding: 10px 20px;
        background: linear-gradient(45deg, #ff6b6b, #4ecdc4);
        color: white;
        border: none;
        border-radius: 5px;
        cursor: pointer;
        transition: all 0.3s ease;
      }

      .newsletter-form button:hover {
        background: linear-gradient(45deg, #ff5252, #26a69a);
      }

      .footer-bottom {
        text-align: center;
        padding-top: 20px;
        border-top: 1px solid rgba(255, 255, 255, 0.1);
        opacity: 0.7;
      }

      /* Back to Top Button */
      .back-to-top {
        position: fixed;
        bottom: 30px;
        right: 30px;
        width: 50px;
        height: 50px;
        background: linear-gradient(45deg, #ff6b6b, #4ecdc4);
        color: white;
        border: none;
        border-radius: 50%;
        font-size: 1.2rem;
        cursor: pointer;
        opacity: 0;
        visibility: hidden;
        transition: all 0.3s ease;
        z-index: 1000;
      }

      .back-to-top.show {
        opacity: 1;
        visibility: visible;
      }

      .back-to-top:hover {
        background: linear-gradient(45deg, #ff5252, #26a69a);
        transform: translateY(-3px);
      }

      /* Animations */
      @keyframes fadeIn {
        from {
          opacity: 0;
          transform: translateY(30px);
        }
        to {
          opacity: 1;
          transform: translateY(0);
        }
      }

      /* Responsive Design */
      @media (max-width: 768px) {
        .hero-text h1 {
          font-size: 2.5rem;
        }

        .subtitle {
          font-size: 1.2rem;
        }

        .nav-menu {
          position: fixed;
          left: -100%;
          top: 70px;
          flex-direction: column;
          background-color: white;
          width: 100%;
          text-align: center;
          transition: 0.3s;
          box-shadow: 0 10px 27px rgba(0, 0, 0, 0.05);
          padding: 2rem 0;
        }

        .nav-menu.active {
          left: 0;
        }

        .hamburger {
          display: block;
        }

        .hamburger.active .bar:nth-child(2) {
          opacity: 0;
        }

        .hamburger.active .bar:nth-child(1) {
          transform: translateY(8px) rotate(45deg);
        }

        .hamburger.active .bar:nth-child(3) {
          transform: translateY(-8px) rotate(-45deg);
        }

        .video-container,
        .contact-container {
          grid-template-columns: 1fr;
        }

        .contact-info {
          grid-template-columns: 1fr;
        }

        .grid {
          grid-template-columns: 1fr;
        }

        .section-header h2 {
          font-size: 2.2rem;
        }
      }

      @media (max-width: 480px) {
        .hero-text h1 {
          font-size: 2rem;
        }

        .cta-button {
          padding: 12px 30px;
          font-size: 1rem;
        }

        .art-info h3 {
          font-size: 1.3rem;
        }
      }
    </style>
  </head>
  <body>
    <!-- Hero Banner -->
    <header class="hero">
      <div class="hero-content">
        <div class="hero-text">
          <h1>Virtual Art Gallery</h1>
          <p class="subtitle">
            Explore creativity through images, videos, and interactive
            experiences
          </p>
          <a href="#gallery" class="cta-button">Explore Gallery</a>
        </div>
      </div>
    </header>

    <!-- Navigation -->
    <nav class="navbar">
      <div class="nav-container">
        <div class="logo">ArtGallery</div>
        <ul class="nav-menu">
          <li><a href="#home">Home</a></li>
          <li><a href="#gallery">Gallery</a></li>
          <li><a href="#video">Video Tour</a></li>
          <li><a href="#contact">Contact</a></li>
        </ul>
        <div class="hamburger">
          <span class="bar"></span>
          <span class="bar"></span>
          <span class="bar"></span>
        </div>
      </div>
    </nav>

    <!-- Gallery Section -->
    <section id="gallery" class="gallery">
      <div class="section-header">
        <h2>Featured Artworks</h2>
        <p>Discover our curated collection of modern and classical art</p>
      </div>
      <div class="grid">
        <div class="art-card">
          <div class="art-image">
            <img
              src="https://images.unsplash.com/photo-1541961017774-22349e4a1262?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80"
              alt="Abstract Painting"
            />
          </div>
          <div class="art-info">
            <h3>Abstract Dreams</h3>
            <p>Modern abstract expressionism</p>
            <span class="artist">By Maria Rodriguez</span>
          </div>
        </div>
        <div class="art-card">
          <div class="art-image">
            <img
              src="https://images.unsplash.com/photo-1506905925346-21bda4d32df4?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80"
              alt="Landscape Painting"
            />
          </div>
          <div class="art-info">
            <h3>Serene Landscape</h3>
            <p>Oil on canvas, 2024</p>
            <span class="artist">By James Wilson</span>
          </div>
        </div>
        <div class="art-card">
          <div class="art-image">
            <img
              src="https://images.unsplash.com/photo-1544005313-94ddf0286df2?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80"
              alt="Portrait"
            />
          </div>
          <div class="art-info">
            <h3>Timeless Portrait</h3>
            <p>Charcoal and pastel</p>
            <span class="artist">By Sarah Chen</span>
          </div>
        </div>
        <div class="art-card">
          <div class="art-image">
            <img
              src="https://images.unsplash.com/photo-1513475382585-d06e58bcb0e0?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80"
              alt="Sculpture"
            />
          </div>
          <div class="art-info">
            <h3>Modern Sculpture</h3>
            <p>Bronze and steel, 2023</p>
            <span class="artist">By David Park</span>
          </div>
        </div>
        <div class="art-card">
          <div class="art-image">
            <img
              src="https://images.unsplash.com/photo-1513364776144-60967b0f800f?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80"
              alt="Digital Art"
            />
          </div>
          <div class="art-info">
            <h3>Digital Universe</h3>
            <p>Digital art, animated</p>
            <span class="artist">By Alex Turner</span>
          </div>
        </div>
        <div class="art-card">
          <div class="art-image">
            <img
              src="https://images.unsplash.com/photo-1579783902614-a3fb3927b6a5?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80"
              alt="Watercolor"
            />
          </div>
          <div class="art-info">
            <h3>Watercolor Dreams</h3>
            <p>Mixed media on paper</p>
            <span class="artist">By Elena Martinez</span>
          </div>
        </div>
      </div>
    </section>

    <!-- Video Section -->
    <section id="video" class="video-section">
      <div class="section-header">
        <h2>Gallery Walkthrough</h2>
        <p>Experience our virtual tour in 4K resolution</p>
      </div>
      <div class="video-container">
        <div class="video-wrapper">
          <video
            id="galleryVideo"
            controls
            poster="https://images.unsplash.com/photo-1563089145-599997674d42?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80"
          >
            <source
              src="https://assets.mixkit.co/videos/preview/mixkit-art-gallery-exhibition-hall-42948-large.mp4"
              type="video/mp4"
            />
            Your browser does not support the video tag.
          </video>
          <div class="video-controls">
            <button id="playBtn" class="control-btn">
              <i class="fas fa-play"></i>
            </button>
            <button id="pauseBtn" class="control-btn">
              <i class="fas fa-pause"></i>
            </button>
            <button id="muteBtn" class="control-btn">
              <i class="fas fa-volume-up"></i>
            </button>
            <button id="fullscreenBtn" class="control-btn">
              <i class="fas fa-expand"></i>
            </button>
          </div>
        </div>
        <div class="video-description">
          <h3>Virtual Exhibition Tour</h3>
          <p>
            Join us on a guided tour through our latest exhibition "Modern
            Perspectives". This virtual walkthrough allows you to experience the
            gallery from the comfort of your home.
          </p>
          <div class="tour-info">
            <div class="info-item">
              <i class="fas fa-clock"></i>
              <span>Duration: 15 minutes</span>
            </div>
            <div class="info-item">
              <i class="fas fa-language"></i>
              <span>Available in 5 languages</span>
            </div>
            <div class="info-item">
              <i class="fas fa-vr-cardboard"></i>
              <span>VR compatible</span>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Contact -->
    <section id="contact" class="contact">
      <div class="section-header">
        <h2>Contact Us</h2>
        <p>Get in touch for inquiries, collaborations, or visits</p>
      </div>
      <div class="contact-container">
        <div class="contact-info">
          <div class="info-card">
            <i class="fas fa-map-marker-alt"></i>
            <h3>Visit Us</h3>
            <p>123 Art Street, Creative City<br />CC 10101, Artland</p>
          </div>
          <div class="info-card">
            <i class="fas fa-clock"></i>
            <h3>Opening Hours</h3>
            <p>
              Monday - Friday: 10am - 8pm<br />Saturday - Sunday: 9am - 10pm
            </p>
          </div>
          <div class="info-card">
            <i class="fas fa-envelope"></i>
            <h3>Email Us</h3>
            <p>info@virtualartgallery.com<br />support@virtualartgallery.com</p>
          </div>
          <div class="info-card">
            <i class="fas fa-phone"></i>
            <h3>Call Us</h3>
            <p>+1 (555) 123-4567<br />+1 (555) 987-6543</p>
          </div>
        </div>
        <form id="contactForm" class="contact-form">
          <div class="form-group">
            <input type="text" placeholder="Your Name" required />
          </div>
          <div class="form-group">
            <input type="email" placeholder="Your Email" required />
          </div>
          <div class="form-group">
            <input type="text" placeholder="Subject" />
          </div>
          <div class="form-group">
            <textarea placeholder="Your Message" rows="5" required></textarea>
          </div>
          <button type="submit" class="submit-btn">
            <span>Send Message</span>
            <i class="fas fa-paper-plane"></i>
          </button>
        </form>
      </div>
    </section>

    <!-- Footer -->
    <footer>
      <div class="footer-content">
        <div class="footer-section">
          <h3>Virtual Art Gallery</h3>
          <p>
            Bringing art to your screen since 2020. Experience the future of art
            exhibitions.
          </p>
          <div class="social-icons">
            <a href="#"><i class="fab fa-facebook"></i></a>
            <a href="#"><i class="fab fa-instagram"></i></a>
            <a href="#"><i class="fab fa-twitter"></i></a>
            <a href="#"><i class="fab fa-youtube"></i></a>
          </div>
        </div>
        <div class="footer-section">
          <h4>Quick Links</h4>
          <ul>
            <li><a href="#home">Home</a></li>
            <li><a href="#gallery">Gallery</a></li>
            <li><a href="#video">Virtual Tour</a></li>
            <li><a href="#contact">Contact</a></li>
          </ul>
        </div>
        <div class="footer-section">
          <h4>Exhibitions</h4>
          <ul>
            <li><a href="#">Current</a></li>
            <li><a href="#">Upcoming</a></li>
            <li><a href="#">Past</a></li>
            <li><a href="#">Permanent Collection</a></li>
          </ul>
        </div>
        <div class="footer-section">
          <h4>Newsletter</h4>
          <p>Subscribe for updates on new exhibitions</p>
          <form class="newsletter-form">
            <input type="email" placeholder="Your Email" required />
            <button type="submit"><i class="fas fa-envelope"></i></button>
          </form>
        </div>
      </div>
      <div class="footer-bottom">
        <p>&copy; 2026 Virtual Art Gallery. All rights reserved.</p>
      </div>
    </footer>

    <!-- Back to Top Button -->
    <button id="backToTop" class="back-to-top">
      <i class="fas fa-arrow-up"></i>
    </button>

    <script>
      // Mobile menu toggle
      const hamburger = document.querySelector(".hamburger");
      const navMenu = document.querySelector(".nav-menu");

      hamburger.addEventListener("click", () => {
        hamburger.classList.toggle("active");
        navMenu.classList.toggle("active");
      });

      // Close mobile menu when clicking on a link
      document.querySelectorAll(".nav-menu a").forEach((link) => {
        link.addEventListener("click", () => {
          hamburger.classList.remove("active");
          navMenu.classList.remove("active");
        });
      });

      // Video controls
      const video = document.getElementById("galleryVideo");
      const playBtn = document.getElementById("playBtn");
      const pauseBtn = document.getElementById("pauseBtn");
      const muteBtn = document.getElementById("muteBtn");
      const fullscreenBtn = document.getElementById("fullscreenBtn");

      playBtn.addEventListener("click", () => {
        video.play();
      });

      pauseBtn.addEventListener("click", () => {
        video.pause();
      });

      muteBtn.addEventListener("click", () => {
        video.muted = !video.muted;
        muteBtn.innerHTML = video.muted
          ? '<i class="fas fa-volume-mute"></i>'
          : '<i class="fas fa-volume-up"></i>';
      });

      fullscreenBtn.addEventListener("click", () => {
        if (video.requestFullscreen) {
          video.requestFullscreen();
        } else if (video.webkitRequestFullscreen) {
          video.webkitRequestFullscreen();
        } else if (video.msRequestFullscreen) {
          video.msRequestFullscreen();
        }
      });

      // Back to top button
      const backToTopBtn = document.getElementById("backToTop");

      window.addEventListener("scroll", () => {
        if (window.pageYOffset > 300) {
          backToTopBtn.classList.add("show");
        } else {
          backToTopBtn.classList.remove("show");
        }
      });

      backToTopBtn.addEventListener("click", () => {
        window.scrollTo({
          top: 0,
          behavior: "smooth",
        });
      });

      // Contact form submission
      const contactForm = document.getElementById("contactForm");

      contactForm.addEventListener("submit", (e) => {
        e.preventDefault();

        // Get form values
        const name = contactForm.querySelector('input[type="text"]').value;
        const email = contactForm.querySelector('input[type="email"]').value;
        const message = contactForm.querySelector("textarea").value;

        // Here you would typically send the data to a server
        // For now, we'll just show an alert
        alert(
          `Thank you ${name}! Your message has been sent successfully. We'll get back to you at ${email} soon.`
        );

        // Reset form
        contactForm.reset();
      });

      // Newsletter form
      const newsletterForm = document.querySelector(".newsletter-form");

      newsletterForm.addEventListener("submit", (e) => {
        e.preventDefault();
        const email = newsletterForm.querySelector('input[type="email"]').value;
        alert(
          `Thank you for subscribing with ${email}! You'll receive our newsletter soon.`
        );
        newsletterForm.reset();
      });

      // Smooth scrolling for anchor links
      document.querySelectorAll('a[href^="#"]').forEach((anchor) => {
        anchor.addEventListener("click", function (e) {
          e.preventDefault();

          const targetId = this.getAttribute("href");
          if (targetId === "#") return;

          const targetElement = document.querySelector(targetId);
          if (targetElement) {
            window.scrollTo({
              top: targetElement.offsetTop - 80,
              behavior: "smooth",
            });
          }
        });
      });

      // Add hover effect to gallery items
      document.querySelectorAll(".art-card").forEach((card) => {
        card.addEventListener("mouseenter", function () {
          this.style.transform = "translateY(-10px) scale(1.02)";
        });

        card.addEventListener("mouseleave", function () {
          this.style.transform = "translateY(0) scale(1)";
        });
      });
    </script>
  </body>
</html>


