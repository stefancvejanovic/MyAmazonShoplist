<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <meta name="description" content="Curated Amazon affiliate products for tech lovers." />
  <title>MyAmazonPicks</title>
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@600;700&family=Open+Sans:wght@400;600&display=swap" rel="stylesheet">
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">

  <style>
  .separate-review-button {
      text-align: center;
    }

    .amazon-reviews-button {
      display: inline-flex;
      align-items: center;
      gap: 8px;
      padding: 12px 24px;
      background: var(--amazon-orange);
      color: white;
      border-radius: 4px;
      text-decoration: none;
      font-weight: 600;
      transition: all 0.2s ease;
      border: none;
      cursor: pointer;
    }

    .amazon-reviews-button:hover {
      background: #e68a00;
      transform: translateY(-2px);
      box-shadow: 0 4px 8px rgba(0,0,0,0.1);
    }

    /* Responsive Styles */
    @media (max-width: 768px) {
      .product-grid {
        grid-template-columns: 1fr;
      }
    }
    :root {
      --amazon-orange: #FF9900;
      --amazon-blue: #146EB4;
      --amazon-dark: #232F3E;
      --amazon-light: #FFFFFF;
      --amazon-gray: #F2F3F3;
      --amazon-text: #0F1111;
      --amazon-stars: #FFA41C;
      --amazon-link: #007185;
      --border-color: #EAEDED;
      --tagline-bg: rgba(255, 255, 255, 0.1);
      --sidebar-bg: #232F3E;
      --sidebar-text: #ffffff;
      --sidebar-accent: #FF9900;
      --sidebar-width: 250px;
      --animation-speed: 0.3s;
    }

    body {
      font-family: 'Open Sans', sans-serif;
      margin: 0;
      padding: 0;
      background: var(--amazon-light);
      color: var(--amazon-text);
      line-height: 1.5;
    }

    /* PREMIUM SIDEBAR STYLES */
    .sidebar {
      position: fixed;
      left: calc(-1 * var(--sidebar-width));
      top: 50%;
      transform: translateY(-50%);
      background: var(--sidebar-bg);
      padding: 1.5rem 0.8rem;
      border-radius: 0 12px 12px 0;
      box-shadow: 4px 4px 12px rgba(0,0,0,0.2);
      z-index: 1000;
      transition: all var(--animation-speed) ease;
      display: flex;
      flex-direction: column;
      gap: 1.5rem;
      width: var(--sidebar-width);
      will-change: transform;
      color: var(--sidebar-text);
    }

    .sidebar.open {
      left: 0;
      transform: translateY(-50%);
    }

    .sidebar-nav {
      display: flex;
      flex-direction: column;
      gap: 0.8rem;
    }

    .sidebar-nav .nav-item {
      padding: 0.7rem;
      font-size: 0.85rem;
      text-align: center;
      color: var(--sidebar-text);
      text-decoration: none;
      font-weight: 600;
      background: rgba(255,255,255,0.08);
      border-radius: 6px;
      transition: all 0.2s ease;
      transform: translateX(-10px);
      opacity: 0;
    }

    .sidebar.open .nav-item {
      transform: translateX(0);
      opacity: 1;
    }

    .sidebar-nav .nav-item:hover {
      background: rgba(255,255,255,0.15);
      transform: translateX(5px);
    }

    .sidebar .deal-button {
      padding: 0.7rem;
      font-size: 0.9rem;
      min-width: auto;
      margin-top: 0.5rem;
      background: linear-gradient(135deg, #e63946, #ff5a5f);
      color: white;
      border: 2px solid #ffccd5;
      border-radius: 6px;
      text-align: center;
      transition: all 0.2s ease;
    }

    .sidebar .deal-button:hover {
      transform: scale(1.05);
      box-shadow: 0 4px 8px rgba(0,0,0,0.2);
    }

    .sidebar-icons {
      display: flex;
      flex-direction: column;
      gap: 1rem;
      align-items: center;
      margin-top: auto;
      padding-top: 1rem;
      border-top: 1px solid rgba(255,255,255,0.1);
    }

    .sidebar-toggle {
      position: fixed;
      left: 20px;
      top: 50%;
      transform: translateY(-50%);
      background: var(--sidebar-bg);
      color: white;
      border: none;
      border-radius: 50%;
      width: 40px;
      height: 40px;
      display: flex;
      align-items: center;
      justify-content: center;
      cursor: pointer;
      z-index: 1001;
      box-shadow: 0 2px 5px rgba(0,0,0,0.2);
      transition: all var(--animation-speed) ease;
    }

    .sidebar-toggle:hover {
      background: var(--sidebar-accent);
      transform: translateY(-50%) scale(1.1);
    }

    .sidebar-toggle i {
      font-size: 1.2rem;
      transition: transform var(--animation-speed) ease;
    }

    .sidebar-backdrop {
      position: fixed;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
      background: rgba(0,0,0,0.5);
      z-index: 999;
      opacity: 0;
      pointer-events: none;
      transition: opacity var(--animation-speed) ease;
    }

    .sidebar-backdrop.active {
      opacity: 1;
      pointer-events: all;
    }

    /* Tooltips */
    [data-tooltip] {
      position: relative;
    }

    [data-tooltip]:hover::after {
      content: attr(data-tooltip);
      position: absolute;
      left: 100%;
      top: 50%;
      transform: translateY(-50%);
      background: #333;
      color: white;
      padding: 0.5rem;
      border-radius: 4px;
      white-space: nowrap;
      margin-left: 10px;
      font-size: 0.8rem;
    }

    /* Mobile Styles */
    @media (max-width: 900px) {
      .sidebar {
        width: 80%;
        left: -80%;
        top: 0;
        height: 100vh;
        transform: none;
        border-radius: 0;
        justify-content: center;
      }
      
      .sidebar-toggle {
        top: 20px;
        transform: none;
      }
    }

    /* Light Mode Support */
    @media (prefers-color-scheme: light) {
      :root {
        --sidebar-bg: #f8f9fa;
        --sidebar-text: #333333;
      }
      
      .sidebar {
        box-shadow: 2px 0 10px rgba(0,0,0,0.1);
      }
      
      .sidebar-nav .nav-item {
        background: rgba(0,0,0,0.05);
      }
      
      .sidebar-icons {
        border-top: 1px solid rgba(0,0,0,0.1);
      }
    }

    /* Animation delays for nav items */
    .sidebar-nav .nav-item:nth-child(1) { transition-delay: 0.1s; --i: 1; }
    .sidebar-nav .nav-item:nth-child(2) { transition-delay: 0.2s; --i: 2; }
    .sidebar-nav .nav-item:nth-child(3) { transition-delay: 0.3s; --i: 3; }
    .sidebar-nav .nav-item:nth-child(4) { transition-delay: 0.4s; --i: 4; }
    .sidebar-nav .nav-item:nth-child(5) { transition-delay: 0.5s; --i: 5; }
    /* END OF PREMIUM SIDEBAR STYLES */

    header {
      background: var(--amazon-dark);
      color: var(--amazon-light);
      padding: 1.5rem 1rem 0;
      position: relative;
      overflow: hidden;
    }

    header::before {
      content: "";
      position: absolute;
      top: 0;
      left: 0;
      right: 0;
      height: 4px;
      background: linear-gradient(90deg, var(--amazon-orange), #FFD700, var(--amazon-orange));
    }

    .header-content {
      max-width: 1200px;
      margin: 0 auto;
      display: flex;
      flex-direction: column;
      align-items: center;
      text-align: center;
    }

    .site-logo {
      display: flex;
      align-items: center;
      gap: 0.6rem;
      font-family: 'Poppins', sans-serif;
      font-size: 2.8rem;
      font-weight: 700;
      background: linear-gradient(to right, var(--amazon-orange), #FFD700);
      -webkit-background-clip: text;
      background-clip: text;
      color: transparent;
      text-shadow: 1px 1px 2px rgba(0,0,0,0.1);
      letter-spacing: -0.5px;
      line-height: 1.2;
      justify-content: center;
      margin: 0.5rem 0;
    }

    .site-logo i {
      font-size: 1.2em;
      color: var(--amazon-orange);
      text-shadow: none;
    }

    .tagline-container {
      background: var(--tagline-bg);
      border-radius: 12px;
      padding: 1.2rem 2rem;
      margin: 1rem auto 2rem;
      max-width: 80%;
      position: relative;
      border: 1px solid rgba(255, 255, 255, 0.2);
      box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
    }

    .tagline {
      font-family: 'Poppins', sans-serif;
      font-size: 1.3rem;
      font-weight: 400;
      color: #FFD700;
      margin: 0;
      text-shadow: 1px 1px 2px rgba(0,0,0,0.3);
      letter-spacing: 0.5px;
    }

    .tagline-container::before {
      content: "";
      position: absolute;
      top: -5px;
      left: 0;
      right: 0;
      height: 5px;
      background: linear-gradient(90deg, transparent, var(--amazon-orange), transparent);
    }

    /* FIXED NAVIGATION SECTION */
    .nav-bar {
      background: rgba(0,0,0,0.1);
      padding: 1.5rem 1rem;
      margin-top: 1rem;
      width: 100%;
    }

    .nav-container {
      max-width: 1200px;
      margin: 0 auto;
    }

    .nav-links {
      display: flex;
      justify-content: center;
      align-items: center;
      flex-wrap: wrap;
      gap: 1rem;
      padding: 0 1rem;
    }

    .nav-item {
      color: var(--amazon-light);
      text-decoration: none;
      font-weight: 600;
      padding: 0.7rem 1.2rem;
      border-radius: 6px;
      transition: all 0.3s ease;
      border: 2px solid transparent;
      background: rgba(255,255,255,0.08);
      white-space: nowrap;
      font-size: 0.95rem;
    }

    .nav-item:hover {
      background: rgba(255,255,255,0.15);
      border-color: rgba(255,255,255,0.3);
    }

    .deal-wrapper {
      margin: 0 1.5rem;
    }

    .deal-button {
      font-size: 1.1rem;
      font-weight: 700;
      padding: 0.8rem 2rem;
      background: linear-gradient(135deg, #e63946, #ff5a5f);
      border: 2px solid #ffccd5;
      box-shadow: 0 4px 12px rgba(230, 57, 70, 0.4);
      color: white;
      border-radius: 6px;
      transition: all 0.3s ease;
      text-transform: uppercase;
      letter-spacing: 1px;
      min-width: 160px;
      text-align: center;
      display: inline-block;
    }

    .deal-button:hover {
      background: linear-gradient(135deg, #d62839, #e8484d);
      box-shadow: 0 6px 16px rgba(230, 57, 70, 0.6);
      transform: translateY(-2px);
    }

    @media (max-width: 768px) {
      .nav-links {
        flex-direction: column;
        gap: 0.8rem;
      }
      
      .deal-wrapper {
        order: 0;
        margin: 0.5rem 0;
        width: 100%;
      }
      
      .deal-button {
        width: 100%;
        padding: 0.8rem 1rem;
      }
      
      .nav-item {
        width: 100%;
        text-align: center;
        padding: 0.7rem 1rem;
      }

      .site-logo {
        font-size: 2.2rem;
      }
    }
    /* END OF FIXED NAVIGATION SECTION */

    /* PRODUCT GRID STYLES */
    .product-grid {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 1.5rem;
      padding: 2rem;
      max-width: 1200px;
      margin: 0 auto;
    }

    .product {
      background: var(--amazon-light);
      border-radius: 8px;
      box-shadow: 0 2px 6px rgba(0,0,0,0.1);
      transition: transform 0.3s ease, box-shadow 0.3s ease;
      cursor: pointer;
      overflow: hidden;
      display: flex;
      flex-direction: column;
      height: 100%;
      border: 1px solid var(--border-color);
    }

    .product:hover {
      transform: translateY(-5px);
      box-shadow: 0 10px 20px rgba(0,0,0,0.1);
    }

    .product-title {
      padding: 1rem;
      border-bottom: 1px solid var(--border-color);
      background: var(--amazon-gray);
    }

    .product-title h2 {
      margin: 0;
      font-size: 1.2rem;
      color: var(--amazon-dark);
      font-weight: 600;
      text-align: center;
    }

    .product-image {
      padding: 1.5rem;
      display: flex;
      align-items: center;
      justify-content: center;
      border-bottom: 1px solid var(--border-color);
      background: white;
      height: 220px;
    }

    .product-image img {
      max-width: 100%;
      max-height: 100%;
      object-fit: contain;
    }

    .product-description {
      padding: 1rem;
      border-bottom: 1px solid var(--border-color);
      flex-grow: 1;
    }

    .product-description p {
      margin: 0;
      color: var(--amazon-text);
      font-size: 0.9rem;
      text-align: center;
    }

    .product-reviews {
      padding: 1rem;
      background: var(--amazon-gray);
    }

    .review-summary {
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 0.5rem;
      margin-bottom: 0.8rem;
    }

    .stars {
      color: var(--amazon-stars);
      font-size: 1rem;
    }

    .review-count {
      font-size: 0.85rem;
      color: var(--amazon-text);
    }

    

    /* SOCIAL ICONS */
    .social-icons {
      margin: 3rem auto 1rem;
      display: flex;
      justify-content: center;
      gap: 1.5rem;
    }

    .social-icons a {
      width: 50px;
      height: 50px;
      display: inline-flex;
      align-items: center;
      justify-content: center;
      border-radius: 12px;
      color: white;
      text-decoration: none;
      font-size: 24px;
      transition: all 0.3s ease;
      box-shadow: 0 4px 8px rgba(0,0,0,0.1);
      position: relative;
      overflow: hidden;
    }

    .social-icons a::before {
      content: "";
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: linear-gradient(45deg, transparent, rgba(255,255,255,0.2));
      transform: translateX(-100%);
      transition: transform 0.3s ease;
    }

    .social-icons a:hover {
      transform: translateY(-5px);
      box-shadow: 0 6px 12px rgba(0,0,0,0.15);
    }

    .social-icons a:hover::before {
      transform: translateX(100%);
    }

    .facebook { 
      background: linear-gradient(135deg, #3b5998, #4a6fbe);
    }
    .instagram { 
      background: linear-gradient(45deg, #f09433, #e6683c, #dc2743, #cc2366, #bc1888);
    }
    .tiktok { 
      background: linear-gradient(135deg, #25F4EE, #000000, #FE2C55);
    }
    .gmail { 
      background: linear-gradient(135deg, #D44638, #EA4335, #D44638);
    }

    /* FOOTER STYLES */
    .footer-links {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 1.5rem;
      margin-bottom: 1.5rem;
      padding: 0 1rem;
    }
    .footer-links a {
      color: #0066c0;
      text-decoration: none;
      font-size: 0.75rem;
      white-space: nowrap;
    }
    .footer-links a:hover {
      text-decoration: underline;
      color: #c45500;
    }

    .copyright {
      text-align: center;
      font-size: 0.7rem;
      color: #666;
      margin-top: 1rem;
    }
    .copyright p {
      margin: 0.2rem 0;
    }

    /* RESPONSIVE STYLES */
    @media (max-width: 900px) {
      .product-grid {
        grid-template-columns: repeat(2, 1fr);
      }
    }

    @media (max-width: 600px) {
      .product-grid {
        grid-template-columns: 1fr;
      }
      
      .site-logo {
        font-size: 2.2rem;
      }
      .tagline {
        font-size: 1.1rem;
      }
    }
  </style>
</head>

<body>
  <!-- SIDEBAR BACKDROP -->
  <div class="sidebar-backdrop" id="sidebarBackdrop"></div>

  <!-- SIDEBAR TOGGLE BUTTON -->
  <button class="sidebar-toggle" id="sidebarToggle" aria-expanded="false" aria-label="Toggle sidebar" aria-controls="sidebar">
    <i class="fas fa-bars"></i>
  </button>

  <!-- SIDEBAR -->
  <div class="sidebar" id="sidebar" data-theme="auto" data-position="left" data-width="250">
    <div class="sidebar-nav">
      <a href="#tech-accessories" class="nav-item">Tech Accessories</a>
      <a href="#gadgets" class="nav-item">Gadgets</a>
      <a href="#deals" class="deal-button">Today's Deal</a>
      <a href="#top-picks" class="nav-item">Top Picks</a>
      <a href="#home-essentials" class="nav-item">Home Essentials</a>
    </div>

    <div class="sidebar-icons">
      <a href="https://www.facebook.com/yourprofile" target="_blank" rel="noopener noreferrer nofollow" 
         class="facebook" aria-label="Facebook" data-tooltip="Facebook">
        <i class="fab fa-facebook-f"></i>
      </a>
      <a href="https://www.instagram.com/yourprofile" target="_blank" rel="noopener noreferrer nofollow" 
         class="instagram" aria-label="Instagram" data-tooltip="Instagram">
        <i class="fab fa-instagram"></i>
      </a>
      <a href="https://www.tiktok.com/@yourprofile" target="_blank" rel="noopener noreferrer nofollow" 
         class="tiktok" aria-label="TikTok" data-tooltip="TikTok">
        <i class="fab fa-tiktok"></i>
      </a>
      <a href="mailto:youremail@gmail.com" class="gmail" aria-label="Email" data-tooltip="Email Us">
        <i class="fas fa-envelope"></i>
      </a>
    </div>
  </div>

  <header>
    <div class="header-content">
      <div class="site-logo">
        <i class="fas fa-search"></i>
        <span>MyAmazonPicks</span>
      </div>
      <div class="tagline-container">
        <p class="tagline">Carefully handpicked Amazon finds just for you</p>
      </div>
      
      <!-- FIXED NAVIGATION -->
      <div class="nav-bar">
        <div class="nav-container">
          <div class="nav-links">
            <a href="#tech-accessories" class="nav-item">Tech Accessories</a>
            <a href="#gadgets" class="nav-item">Gadgets</a>
            <div class="deal-wrapper">
              <a href="#deals" class="deal-button">Today's Deal</a>
            </div>
            <a href="#top-picks" class="nav-item">Top Picks</a>
            <a href="#home-essentials" class="nav-item">Home Essentials</a>
          </div>
        </div>
      </div>
    </div>
  </header>

  <main>
   <div class="product-grid">
    <!-- Product 1 -->
    <div class="product-container">
      <div class="product" onclick="window.open('https://www.amazon.com/Shark-Navigator-Professional-Anti-Allergy-NV360/dp/B00JH98GR4?tag=20040605-20')">
        <div class="product-title">
          <h2>Shark Upright Vacuum</h2>
        </div>
        <div class="product-image">
          <img src="https://m.media-amazon.com/images/I/71ybuaqVLwL.__AC_SX300_SY300_QL70_FMwebp_.jpg" alt="Shark Vacuum">
        </div>
        <div class="product-description">
          <p>★ Customers generally find it easy to empty the dust cup of this vacuum.</p>
          <p>★ Product comes with tools like a stair beater bar attachment that users find great for cleaning stairs and furniture.</p>
		   <p>★ Works with a HEPA filter to trap dust and allergens inside the vacuum cleaner.</p>
        </div>
      </div>
      <div class="separate-review-button">
        <a href="https://www.amazon.com/Shark-Navigator-Professional-Anti-Allergy-NV360/product-reviews/B00JH98GR4?tag=20040605-20" 
           class="amazon-reviews-button" 
           target="_blank" 
           rel="nofollow noopener">
          <span>Read Reviews on Amazon</span>
          <i class="fas fa-external-link-alt"></i>
        </a>
      </div>
    </div>

      <!-- Product 2 -->
     <div class="product-container">
      <div class="product" onclick="window.open('https://www.amazon.com/Ninja-Capacity-Dehydrate-Technology-AF141/dp/B0CSZ7WBYW?pf_rd_r=AG4YQ8J219Q7Q54HCZ70&pf_rd_p=5ac04545-c2e2-4358-9acc-0e976288d228&th=1&linkCode=ll1&tag=20040605-20&linkId=65616576a41b266579278b0a0e752088&language=en_US&ref_=as_li_ss_tl')">
        <div class="product-title">
          <h2>Ninja Air Fryer Pro 4-in-1</h2>
        </div>
        <div class="product-image">
          <img src="https://m.media-amazon.com/images/I/71QwoGmcfUL._AC_SX679_.jpg" alt="Ninja Air Fryer Pro 4-in-1">
        </div>
        <div class="product-description">
          <p>★ FROZEN TO CRISPY: Cook frozen foods in just minutes for an extra-crispy finish.</p>
<p>★ SPACE SAVER: Ninja’s latest air fryer design allows you to save even more space on your countertop without compromising capacity.</p>
<p>★ EASY TO CLEAN: The basket and crisper plate are both nonstick for easy cleaning.</p>
<p>★ WHAT’S INCLUDED: Air Fryer, 5-QT nonstick basket and crisper plate, chef-inspired 20 recipe book and cooking charts.</p>
        </div>
      </div>
      <div class="separate-review-button">
        <a href="https://www.amazon.com/product-reviews/B0CSZ7WBYW?ie=UTF8&filterByStar=five_star&reviewerType=all_reviews&linkCode=ll2&tag=20040605-20&linkId=5cc376f4a4e35db3a90b2ea8e610e66e&language=en_US&ref_=as_li_ss_tl" 
           class="amazon-reviews-button" 
           target="_blank" 
           rel="nofollow noopener">
          <span>Read Reviews on Amazon</span>
          <i class="fas fa-external-link-alt"></i>
        </a>
      </div>
    </div>

      
     <!-- Product 3 -->
     <div class="product-container">
      <div class="product" onclick="window.open('https://www.amazon.com/Samsung-Smartphone-Unlocked-Manufacturer-Warranty/dp/B0FDH5XV8L?pf_rd_r=60BR3GK7HPKWWZKMSMSS&pf_rd_p=5ac04545-c2e2-4358-9acc-0e976288d228&th=1&linkCode=ll1&tag=20040605-20&linkId=d5051914705425249f0163c5755d9a2a&language=en_US&ref_=as_li_ss_tl')">
        <div class="product-title">
          <h2>Samsung Galaxy Z Flip7 + Gift Card</h2>
        </div>
        <div class="product-image">
          <img src="https://m.media-amazon.com/images/I/714IPPvZrSL._AC_SL1500_.jpg" alt="Samsung Galaxy Z Flip7 Cell Phone + Gift Card">
        </div>
        <div class="product-description">
   
<p>★ FlexWindow on Galaxy Z Flip7 unlocks a smarter, faster way to navigate your day. Talk to Gemini for hands-free help, or tap into personalized updates using Now Brief with Galaxy AI,</p>
<p>★ A SHORTCUT TO ALL YOUR FAVORITES: Now you can quickly customize your cover screen to do even more while your phone stays shut with the new MultiStar integration. Easily add apps, widgets and shortcuts right to your FlexWindow for on-the-go access.</p>
<p>★ GOOGLE GEMINI, MEET FLEXWINDOW: FlexWindow on Galaxy Z Flip7 unlocks a smarter, faster way to navigate your day. Talk to Gemini for hands-free help, or tap into personalized updates using Now Brief with Galaxy AI, all without opening your phone</p>
        </div>
      </div>
      <div class="separate-review-button">
        <a href="https://www.amazon.com/Samsung-Smartphone-Unlocked-Manufacturer-Warranty/dp/B0FDH5XV8L?pf_rd_r=60BR3GK7HPKWWZKMSMSS&pf_rd_p=5ac04545-c2e2-4358-9acc-0e976288d228&th=1&linkCode=ll1&tag=20040605-20&linkId=d5051914705425249f0163c5755d9a2a&language=en_US&ref_=as_li_ss_tl')" 
           class="amazon-reviews-button" 
           target="_blank" 
           rel="nofollow noopener">
          <span>Released on July 25, 2025</span>
          <i class="fas fa-external-link-alt"></i>
        </a>
      </div>
    </div>

  
  </main>

  <footer>
  <div class="social-icons">
    <a href="https://www.facebook.com/yourprofile" target="_blank" rel="noopener noreferrer nofollow" class="facebook" aria-label="Facebook">
      <i class="fab fa-facebook-f"></i>
    </a>
    <a href="https://www.instagram.com/yourprofile" target="_blank" rel="noopener noreferrer nofollow" class="instagram" aria-label="Instagram">
      <i class="fab fa-instagram"></i>
    </a>
    <a href="https://www.tiktok.com/@yourprofile" target="_blank" rel="noopener noreferrer nofollow" class="tiktok" aria-label="TikTok">
      <i class="fab fa-tiktok"></i>
    </a>
    <a href="mailto:youremail@gmail.com" class="gmail" aria-label="Email">
      <i class="fas fa-envelope"></i>
    </a>
  </div>
  
    <div class="footer-links">
      <a href="https://www.amazon.com/gp/help/customer/display.html/ref=footer_cou?ie=UTF8&nodeId=508088" target="_blank" rel="noopener noreferrer">Conditions of Use</a>
      <a href="https://www.amazon.com/gp/help/customer/display.html/ref=footer_privacy?ie=UTF8&nodeId=468496" target="_blank" rel="noopener noreferrer">Privacy Notice</a>
      <a href="https://www.amazon.com/gp/help/customer/display.html?nodeId=GX7NJQ4ZB8MHFRNJ" target="_blank" rel="noopener noreferrer">Consumer Health Data Privacy Disclosure</a>
      <a href="https://www.amazon.com/adprefs" target="_blank" rel="noopener noreferrer">Your Ads Privacy Choices</a>
    </div>

    <div class="copyright">
      <p>© 1996-2025, Amazon.com, Inc. or its affiliates</p>
      <p>© 2025 MyAmazonPicks. All rights reserved.</p>
    </div>
  </footer>

  <script>
    // SIDEBAR FUNCTIONALITY
    document.addEventListener('DOMContentLoaded', () => {
      const sidebar = document.getElementById('sidebar');
      const sidebarToggle = document.getElementById('sidebarToggle');
      const sidebarBackdrop = document.getElementById('sidebarBackdrop');
      let resizeTimeout;

      // Initialize sidebar state
      function initSidebar() {
        const savedState = localStorage.getItem('sidebarOpen');
        if (savedState === 'true') {
          openSidebar();
        }
      }

      // Toggle sidebar
      function toggleSidebar() {
        if (sidebar.classList.contains('open')) {
          closeSidebar();
        } else {
          openSidebar();
        }
      }

      function openSidebar() {
        sidebar.classList.add('open');
        sidebarBackdrop.classList.add('active');
        toggleIcon(true);
        localStorage.setItem('sidebarOpen', 'true');
        updateAria(true);
      }

      function closeSidebar() {
        sidebar.classList.remove('open');
        sidebarBackdrop.classList.remove('active');
        toggleIcon(false);
        localStorage.setItem('sidebarOpen', 'false');
        updateAria(false);
      }

      function toggleIcon(isOpen) {
        const icon = sidebarToggle.querySelector('i');
        icon.classList.toggle('fa-bars', !isOpen);
        icon.classList.toggle('fa-times', isOpen);
      }

      function updateAria(isExpanded) {
        sidebarToggle.setAttribute('aria-expanded', isExpanded);
      }

      // Smooth scrolling for nav links
      document.querySelectorAll('.sidebar-nav a').forEach(link => {
        link.addEventListener('click', (e) => {
          if (link.hash && document.querySelector(link.hash)) {
            e.preventDefault();
            document.querySelector(link.hash).scrollIntoView({
              behavior: 'smooth'
            });
            closeSidebar();
          }
        });
      });

      // Event listeners
      sidebarToggle.addEventListener('click', toggleSidebar);
      sidebarBackdrop.addEventListener('click', closeSidebar);

      // Keyboard navigation
      document.addEventListener('keydown', (e) => {
        if (e.key === 'Escape' && sidebar.classList.contains('open')) {
          closeSidebar();
        }
      });

      // Touch gestures
      let touchStartX = 0;
      sidebar.addEventListener('touchstart', (e) => {
        touchStartX = e.changedTouches[0].screenX;
      }, {passive: true});

      sidebar.addEventListener('touchend', (e) => {
        const touchEndX = e.changedTouches[0].screenX;
        if (touchStartX - touchEndX > 50) {
          closeSidebar();
        }
      }, {passive: true});

      // Responsive handling
      window.addEventListener('resize', () => {
        clearTimeout(resizeTimeout);
        resizeTimeout = setTimeout(() => {
          if (window.innerWidth > 900) {
            sidebar.style.display = '';
            sidebarToggle.style.display = '';
          } else if (sidebar.classList.contains('open')) {
            closeSidebar();
          }
        }, 100);
      });

      // Initialize
      initSidebar();

 document.querySelectorAll('.sidebar-nav .nav-item').forEach((item, index) => {
                item.style.transitionDelay = `${0.1 * (index + 1)}s`;
            });
        });
    </script>
</body>
</html>
