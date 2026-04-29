<script>
  // App configuration
  const appName = "STRIDES";
  const tagline = "Record your daily accomplishments, one stride at a time.";
  const description = "STRIDES helps you track your daily wins, build momentum, and celebrate progress — no matter how small. Your personal accountability partner, right in your pocket.";
  
  // Feature data
  const features = [
    {
      icon: "📝",
      title: "Daily Logging",
      description: "Quickly record your accomplishments each day with our intuitive journal-like interface."
    },
    {
      icon: "📊",
      title: "Progress Tracking",
      description: "Visualize your streaks and achievements over time with beautiful charts and insights."
    },
    {
      icon: "🎯",
      title: "Goal Setting",
      description: "Set daily, weekly, or monthly goals and watch yourself crush them consistently."
    },
    {
      icon: "🔔",
      title: "Smart Reminders",
      description: "Never miss a day with customizable reminders that keep you accountable."
    },
    {
      icon: "📈",
      title: "Performance Analytics",
      description: "See patterns in your productivity and identify your most productive times."
    },
    {
      icon: "🏆",
      title: "Achievement Badges",
      description: "Earn rewards and badges as you hit milestones in your personal journey."
    }
  ];

  // How it works steps
  const steps = [
    {
      number: "01",
      title: "Log Your Day",
      description: "Spend 2 minutes noting what you accomplished today."
    },
    {
      number: "02",
      title: "Track Progress",
      description: "Watch your streak grow and see patterns emerge."
    },
    {
      number: "03",
      title: "Stay Motivated",
      description: "Celebrate your wins and stay consistent day after day."
    }
  ];

  let email = "";
  let showSuccess = false;

  function handleSubscribe() {
    if (email && email.includes("@")) {
      showSuccess = true;
      email = "";
      setTimeout(() => {
        showSuccess = false;
      }, 3000);
    }
  }

  // Simulated download click (replace with actual store links)
  function handleDownload() {
    alert("🚀 Thanks for your interest! The STRIDES app will be available soon on Google Play Store.");
  }
</script>

<svelte:head>
  <title>STRIDES – Track Your Daily Accomplishments</title>
  <meta name="description" content="STRIDES helps you record and celebrate your daily accomplishments. Build better habits, track progress, and achieve your goals with our simple accountability app." />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
</svelte:head>

<div class="landing">
  <!-- Hero Section -->
  <section class="hero">
    <div class="hero-content">
      <div class="logo">
        <span class="logo-icon">🚶</span>
        <span class="logo-text">{appName}</span>
      </div>
      <h1 class="hero-title">
        Every <span class="highlight">Stride</span> Forward<br />
        Deserves to Be Celebrated
      </h1>
      <p class="hero-description">{description}</p>
      
      <div class="cta-buttons">
        <button class="btn btn-primary" on:click={handleDownload}>
          📱 Download for Android
        </button>
        <button class="btn btn-secondary" on:click={handleDownload}>
          🎯 Learn More
        </button>
      </div>

      <!-- Stats / Social proof -->
      <div class="stats">
        <div class="stat-item">
          <span class="stat-number">10,000+</span>
          <span class="stat-label">Active Strides</span>
        </div>
        <div class="stat-item">
          <span class="stat-number">500K+</span>
          <span class="stat-label">Accomplishments Logged</span>
        </div>
        <div class="stat-item">
          <span class="stat-number">4.9</span>
          <span class="stat-label">⭐ App Rating</span>
        </div>
      </div>
    </div>
    <div class="hero-visual">
      <div class="phone-mockup">
        <div class="mockup-screen">
          <div class="mockup-header">
            <span>Today's Strides</span>
            <span>📅</span>
          </div>
          <div class="mockup-items">
            <div class="mockup-item">✅ Finished project report</div>
            <div class="mockup-item">🏃‍♂️ 30 min workout</div>
            <div class="mockup-item">📧 Replied to all emails</div>
            <div class="mockup-item">📚 Read 20 pages</div>
          </div>
          <div class="mockup-footer">
            <span>🔥 7 day streak</span>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- Features Section -->
  <section class="features">
    <div class="container">
      <div class="section-header">
        <span class="section-badge">Why STRIDES?</span>
        <h2>Everything you need to track<br />your daily wins</h2>
        <p>Simple, powerful features designed to help you stay consistent and celebrate progress.</p>
      </div>
      <div class="features-grid">
        {#each features as feature}
          <div class="feature-card">
            <div class="feature-icon">{feature.icon}</div>
            <h3>{feature.title}</h3>
            <p>{feature.description}</p>
          </div>
        {/each}
      </div>
    </div>
  </section>

  <!-- How It Works -->
  <section class="how-it-works">
    <div class="container">
      <div class="section-header">
        <span class="section-badge">Simple Process</span>
        <h2>How STRIDES works</h2>
        <p>Three simple steps to start tracking your accomplishments today.</p>
      </div>
      <div class="steps">
        {#each steps as step}
          <div class="step">
            <div class="step-number">{step.number}</div>
            <h3>{step.title}</h3>
            <p>{step.description}</p>
          </div>
        {/each}
      </div>
    </div>
  </section>

  <!-- Testimonial Section -->
  <section class="testimonials">
    <div class="container">
      <div class="section-header">
        <span class="section-badge">Success Stories</span>
        <h2>Loved by thousands of users</h2>
      </div>
      <div class="testimonial-grid">
        <div class="testimonial-card">
          <div class="quote">"</div>
          <p>STRIDES completely changed how I view my daily progress. Seeing my accomplishments written down keeps me motivated every single day.</p>
          <div class="testimonial-author">
            <strong>Sarah J.</strong>
            <span>⭐ 5/5</span>
          </div>
        </div>
        <div class="testimonial-card">
          <div class="quote">"</div>
          <p>Finally an app that celebrates small wins instead of just tracking tasks. The streak feature is incredibly addictive in the best way!</p>
          <div class="testimonial-author">
            <strong>Marcus T.</strong>
            <span>⭐ 5/5</span>
          </div>
        </div>
        <div class="testimonial-card">
          <div class="quote">"</div>
          <p>As someone with ADHD, this app has been a game-changer. Two minutes a day and I actually remember what I've accomplished.</p>
          <div class="testimonial-author">
            <strong>Alex R.</strong>
            <span>⭐ 5/5</span>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- Newsletter / Waitlist Section -->
  <section class="newsletter">
    <div class="container">
      <div class="newsletter-content">
        <h2>Be the first to know</h2>
        <p>Get updates on new features, tips for building better habits, and early access to premium features.</p>
        <div class="newsletter-form">
          <input 
            type="email" 
            placeholder="Enter your email" 
            bind:value={email}
            on:keypress={(e) => e.key === 'Enter' && handleSubscribe()}
          />
          <button class="btn btn-primary" on:click={handleSubscribe}>Subscribe</button>
        </div>
        {#if showSuccess}
          <div class="success-message">
            ✓ Thanks for subscribing! Check your inbox soon.
          </div>
        {/if}
      </div>
    </div>
  </section>

  <!-- Footer -->
  <footer class="footer">
    <div class="container">
      <div class="footer-content">
        <div class="footer-brand">
          <div class="logo">
            <span class="logo-icon">🚶</span>
            <span class="logo-text">{appName}</span>
          </div>
          <p>One stride at a time.</p>
        </div>
        <div class="footer-links">
          <div class="link-group">
            <h4>Product</h4>
            <a href="#" on:click|preventDefault={handleDownload}>Features</a>
            <a href="#" on:click|preventDefault={handleDownload}>Pricing</a>
            <a href="#" on:click|preventDefault={handleDownload}>Download</a>
          </div>
          <div class="link-group">
            <h4>Company</h4>
            <a href="#" on:click|preventDefault={handleDownload}>About</a>
            <a href="#" on:click|preventDefault={handleDownload}>Blog</a>
            <a href="#" on:click|preventDefault={handleDownload}>Contact</a>
          </div>
          <div class="link-group">
            <h4>Legal</h4>
            <a href="/privacy">Privacy Policy</a>
            <a href="#" on:click|preventDefault={handleDownload}>Terms of Service</a>
          </div>
        </div>
      </div>
      <div class="footer-bottom">
        <p>&copy; 2026 STRIDES. All rights reserved. Made with 🚶 for daily achievers.</p>
      </div>
    </div>
  </footer>
</div>

<style>
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }

  .landing {
    font-family: system-ui, -apple-system, 'Segoe UI', Roboto, 'Helvetica Neue', sans-serif;
    background: linear-gradient(135deg, #f5f7fa 0%, #c3cfe2 100%);
    color: #1a202c;
    overflow-x: hidden;
  }

  .container {
    max-width: 1200px;
    margin: 0 auto;
    padding: 0 2rem;
  }

  /* Hero Section */
  .hero {
    min-height: 100vh;
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 4rem 6rem;
    gap: 4rem;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    color: white;
    position: relative;
    overflow: hidden;
  }

  .hero::before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background: url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 200 200"><path fill="rgba(255,255,255,0.05)" d="M100 0L200 100L100 200L0 100L100 0z"/></svg>') repeat;
    opacity: 0.1;
    pointer-events: none;
  }

  .hero-content {
    flex: 1;
    z-index: 1;
  }

  .hero-visual {
    flex: 1;
    display: flex;
    justify-content: center;
    z-index: 1;
  }

  .logo {
    display: inline-flex;
    align-items: center;
    gap: 0.5rem;
    font-size: 1.5rem;
    font-weight: bold;
    margin-bottom: 2rem;
  }

  .logo-icon {
    font-size: 2rem;
  }

  .logo-text {
    background: white;
    background-clip: text;
    -webkit-background-clip: text;
    color: transparent;
    text-shadow: none;
  }

  .hero-title {
    font-size: 3.5rem;
    font-weight: 800;
    line-height: 1.2;
    margin-bottom: 1.5rem;
  }

  .highlight {
    color: #ffd700;
    position: relative;
    display: inline-block;
  }

  .hero-description {
    font-size: 1.2rem;
    line-height: 1.6;
    margin-bottom: 2rem;
    opacity: 0.95;
    max-width: 500px;
  }

  .cta-buttons {
    display: flex;
    gap: 1rem;
    margin-bottom: 3rem;
  }

  .btn {
    padding: 0.875rem 2rem;
    font-size: 1rem;
    font-weight: 600;
    border: none;
    border-radius: 50px;
    cursor: pointer;
    transition: transform 0.2s, box-shadow 0.2s;
    font-family: inherit;
  }

  .btn-primary {
    background: white;
    color: #667eea;
  }

  .btn-primary:hover {
    transform: translateY(-2px);
    box-shadow: 0 10px 20px rgba(0, 0, 0, 0.2);
  }

  .btn-secondary {
    background: rgba(255, 255, 255, 0.2);
    color: white;
    backdrop-filter: blur(10px);
  }

  .btn-secondary:hover {
    background: rgba(255, 255, 255, 0.3);
    transform: translateY(-2px);
  }

  .stats {
    display: flex;
    gap: 2rem;
  }

  .stat-item {
    text-align: center;
  }

  .stat-number {
    display: block;
    font-size: 1.75rem;
    font-weight: bold;
  }

  .stat-label {
    font-size: 0.875rem;
    opacity: 0.9;
  }

  /* Phone Mockup */
  .phone-mockup {
    width: 280px;
    height: 560px;
    background: #1a1a2e;
    border-radius: 40px;
    padding: 12px;
    box-shadow: 0 30px 50px rgba(0, 0, 0, 0.3);
    position: relative;
  }

  .phone-mockup::before {
    content: '';
    position: absolute;
    top: 12px;
    left: 50%;
    transform: translateX(-50%);
    width: 120px;
    height: 25px;
    background: #1a1a2e;
    border-radius: 20px;
    z-index: 1;
  }

  .mockup-screen {
    background: white;
    height: 100%;
    border-radius: 32px;
    overflow: hidden;
    display: flex;
    flex-direction: column;
  }

  .mockup-header {
    background: linear-gradient(135deg, #667eea, #764ba2);
    color: white;
    padding: 1rem;
    text-align: center;
    font-weight: bold;
    display: flex;
    justify-content: space-between;
  }

  .mockup-items {
    flex: 1;
    padding: 1rem;
    display: flex;
    flex-direction: column;
    gap: 0.75rem;
  }

  .mockup-item {
    background: #f3f4f6;
    padding: 0.75rem;
    border-radius: 12px;
    font-size: 0.875rem;
    color: #1f2937;
  }

  .mockup-footer {
    background: #f9fafb;
    padding: 1rem;
    text-align: center;
    font-weight: bold;
    color: #10b981;
    border-top: 1px solid #e5e7eb;
  }

  /* Features Section */
  .features {
    padding: 6rem 0;
    background: white;
  }

  .section-header {
    text-align: center;
    margin-bottom: 4rem;
  }

  .section-badge {
    display: inline-block;
    background: #e0e7ff;
    color: #4338ca;
    padding: 0.25rem 1rem;
    border-radius: 50px;
    font-size: 0.875rem;
    font-weight: 600;
    margin-bottom: 1rem;
  }

  .section-header h2 {
    font-size: 2.5rem;
    margin-bottom: 1rem;
    color: #1f2937;
  }

  .section-header p {
    font-size: 1.125rem;
    color: #6b7280;
    max-width: 600px;
    margin: 0 auto;
  }

  .features-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 2rem;
  }

  .feature-card {
    text-align: center;
    padding: 2rem;
    border-radius: 20px;
    transition: all 0.3s;
    background: #f9fafb;
  }

  .feature-card:hover {
    transform: translateY(-5px);
    box-shadow: 0 20px 25px -12px rgba(0, 0, 0, 0.1);
  }

  .feature-icon {
    font-size: 3rem;
    margin-bottom: 1rem;
  }

  .feature-card h3 {
    font-size: 1.25rem;
    margin-bottom: 0.5rem;
    color: #1f2937;
  }

  .feature-card p {
    color: #6b7280;
    line-height: 1.6;
  }

  /* How It Works */
  .how-it-works {
    padding: 6rem 0;
    background: #f3f4f6;
  }

  .steps {
    display: flex;
    justify-content: space-between;
    gap: 2rem;
    margin-top: 3rem;
  }

  .step {
    flex: 1;
    text-align: center;
  }

  .step-number {
    font-size: 3rem;
    font-weight: 800;
    color: #667eea;
    margin-bottom: 1rem;
  }

  .step h3 {
    font-size: 1.5rem;
    margin-bottom: 0.5rem;
  }

  .step p {
    color: #6b7280;
  }

  /* Testimonials */
  .testimonials {
    padding: 6rem 0;
    background: white;
  }

  .testimonial-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 2rem;
    margin-top: 3rem;
  }

  .testimonial-card {
    background: #f9fafb;
    padding: 2rem;
    border-radius: 20px;
    position: relative;
  }

  .quote {
    font-size: 4rem;
    color: #667eea;
    opacity: 0.3;
    position: absolute;
    top: 1rem;
    left: 1rem;
  }

  .testimonial-card p {
    margin-bottom: 1rem;
    line-height: 1.6;
    position: relative;
    z-index: 1;
  }

  .testimonial-author {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-top: 1rem;
    padding-top: 1rem;
    border-top: 1px solid #e5e7eb;
  }

  /* Newsletter */
  .newsletter {
    padding: 6rem 0;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    color: white;
  }

  .newsletter-content {
    text-align: center;
    max-width: 600px;
    margin: 0 auto;
  }

  .newsletter-content h2 {
    font-size: 2rem;
    margin-bottom: 1rem;
  }

  .newsletter-content p {
    margin-bottom: 2rem;
    opacity: 0.95;
  }

  .newsletter-form {
    display: flex;
    gap: 1rem;
    justify-content: center;
    flex-wrap: wrap;
  }

  .newsletter-form input {
    flex: 1;
    min-width: 250px;
    padding: 0.875rem 1.5rem;
    border: none;
    border-radius: 50px;
    font-size: 1rem;
    outline: none;
  }

  .success-message {
    margin-top: 1rem;
    padding: 0.75rem;
    background: rgba(255, 255, 255, 0.2);
    border-radius: 10px;
    backdrop-filter: blur(10px);
  }

  /* Footer */
  .footer {
    background: #1f2937;
    color: #9ca3af;
    padding: 3rem 0 2rem;
  }

  .footer-content {
    display: flex;
    justify-content: space-between;
    flex-wrap: wrap;
    gap: 2rem;
    margin-bottom: 2rem;
  }

  .footer-brand .logo {
    margin-bottom: 1rem;
  }

  .footer-links {
    display: flex;
    gap: 3rem;
    flex-wrap: wrap;
  }

  .link-group h4 {
    color: white;
    margin-bottom: 1rem;
    font-size: 1rem;
  }

  .link-group a {
    display: block;
    color: #9ca3af;
    text-decoration: none;
    margin-bottom: 0.5rem;
    font-size: 0.875rem;
    transition: color 0.2s;
  }

  .link-group a:hover {
    color: white;
  }

  .footer-bottom {
    text-align: center;
    padding-top: 2rem;
    border-top: 1px solid #374151;
    font-size: 0.875rem;
  }

  /* Responsive */
  @media (max-width: 968px) {
    .hero {
      flex-direction: column;
      padding: 3rem 2rem;
      text-align: center;
    }
    .hero-title {
      font-size: 2.5rem;
    }
    .hero-description {
      margin-left: auto;
      margin-right: auto;
    }
    .cta-buttons {
      justify-content: center;
    }
    .stats {
      justify-content: center;
    }
    .steps {
      flex-direction: column;
      align-items: center;
    }
    .step {
      max-width: 300px;
    }
    .footer-content {
      flex-direction: column;
      align-items: center;
      text-align: center;
    }
    .footer-links {
      justify-content: center;
    }
  }
</style>