 <div class="nav-bar">
      <div class="nav-links">
        <a href="#top-picks" class="nav-item">Top Picks</a>
        <a href="#gadgets" class="nav-item">Gadgets</a>
        
        <!-- TODAY'S DEAL - CENTERED & HIGHLIGHTED -->
        <div class="deal-wrapper">
          <a href="#deals" class="deal-button">Today's Deal</a>
        </div>
        
        <a href="#home-essentials" class="nav-item">Home Essentials</a>
        <a href="#tech-accessories" class="nav-item">Tech Accessories</a>
      </div>
    </div>

    <style>
      /* NAVIGATION STYLES */
      .nav-bar {
        background: rgba(0,0,0,0.1);
        padding: 1rem 0;
        margin-top: 1rem;
      }

      .nav-links {
        display: flex;
        justify-content: center;
        align-items: center;
        gap: 1rem;
        max-width: 1200px;
        margin: 0 auto;
        padding: 0 1rem;
        flex-wrap: wrap;
        position: relative;
      }

      .nav-item {
        color: white;
        text-decoration: none;
        font-weight: 600;
        padding: 0.6rem 1.2rem;
        border-radius: 6px;
        transition: all 0.3s ease;
        border: 2px solid transparent;
        background: rgba(255,255,255,0.08);
        white-space: nowrap;
      }

      .nav-item:hover {
        background: rgba(255,255,255,0.15);
        border-color: rgba(255,255,255,0.3);
      }

      /* TODAY'S DEAL BUTTON */
      .deal-wrapper {
        margin: 0 2rem;
      }

      .deal-button {
        font-size: 1.1rem;
        font-weight: 700;
        padding: 0.7rem 2rem;
        background: linear-gradient(135deg, #e63946, #ff5a5f);
        border: 2px solid #ffccd5;
        box-shadow: 0 4px 12px rgba(230, 57, 70, 0.4);
        color: white;
        border-radius: 6px;
        transition: all 0.3s ease;
        text-transform: uppercase;
        letter-spacing: 1px;
      }

      .deal-button:hover {
        background: linear-gradient(135deg, #d62839, #e8484d);
        box-shadow: 0 6px 16px rgba(230, 57, 70, 0.6);
        transform: translateY(-2px);
      }

      /* MOBILE RESPONSIVE */
      @media (max-width: 768px) {
        .nav-links {
          flex-direction: column;
          gap: 0.8rem;
          padding: 1rem;
        }
        .deal-wrapper {
          margin: 0.5rem 0;
          order: 3;
        }
        .deal-button {
          width: 100%;
          text-align: center;
        }
      }
    </style>
