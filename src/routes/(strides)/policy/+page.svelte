<script context="module">
  // Optional: static page metadata for better SEO
  export const prerender = true;
</script>

<script>
  // App-specific variables (customize these)
  const appName = "Strides";
  const contactEmail = "gie.xx47@gmail.com";
  const lastUpdated = "April 29, 2026";
  const dataCollectionTypes = [
    "Account information (e.g., email, username)",
    "Device information (model, OS version, unique device identifiers)",
    "App usage data (features used, session duration)",
    "Crash logs and performance data"
  ];
  const dataUsagePurposes = [
    "To provide, maintain, and improve the app's functionality",
    "To personalize your experience and content",
    "To analyze app performance and fix bugs",
    "To send important updates, security alerts, and support messages"
  ];
  const thirdPartyServices = [
    {
      name: "Google Play Services",
      purpose: "App distribution, updates, and in-app purchases",
      privacyPolicy: "https://policies.google.com/privacy"
    },
    {
      name: "Firebase Analytics",
      purpose: "Anonymized usage statistics and crash reporting",
      privacyPolicy: "https://firebase.google.com/support/privacy"
    },
    {
      name: "AdMob",
      purpose: "Displaying personalized/non-personalized ads",
      privacyPolicy: "https://policies.google.com/privacy"
    }
  ];
  const userRights = [
    "Access and download your data",
    "Request correction or deletion of your personal data",
    "Opt-out of data collection (via in-app settings)",
    "Withdraw consent at any time"
  ];
</script>

<svelte:head>
  <title>Privacy Policy – {appName}</title>
  <meta name="description" content="Privacy Policy for {appName} Android app. Learn how we collect, use, and protect your personal information." />
</svelte:head>

<div class="privacy-container">
  <div class="privacy-header">
    <h1>Privacy Policy</h1>
    <p class="effective-date">Last updated: {lastUpdated}</p>
    <p class="app-tagline">Your privacy is important to us. This policy explains how {appName} handles your information.</p>
  </div>

  <div class="privacy-content">
    <section>
      <h2>1. Information We Collect</h2>
      <p>When you use {appName}, we may collect the following types of information:</p>
      <ul>
        {#each dataCollectionTypes as item}
          <li>{item}</li>
        {/each}
      </ul>
      <p><strong>Note:</strong> We do NOT collect sensitive information such as precise location, contacts, SMS, or biometric data unless explicitly required for core functionality and with your consent.</p>
    </section>

    <section>
      <h2>2. How We Use Your Information</h2>
      <p>{appName} uses the collected data for the following purposes:</p>
      <ul>
        {#each dataUsagePurposes as purpose}
          <li>{purpose}</li>
        {/each}
      </ul>
    </section>

    <section>
      <h2>3. Third-Party Services</h2>
      <p>Our Android app integrates third-party services that may process data under their own policies:</p>
      <div class="third-party-list">
        {#each thirdPartyServices as service}
          <div class="third-party-card">
            <h3>{service.name}</h3>
            <p>{service.purpose}</p>
            <a href={service.privacyPolicy} target="_blank" rel="noopener noreferrer">View Privacy Policy →</a>
          </div>
        {/each}
      </div>
    </section>

    <section>
      <h2>4. Data Storage & Security</h2>
      <p>We store your data securely using industry-standard encryption. Data is retained only as long as necessary to provide app functionality or as required by law. We implement regular security audits and access controls.</p>
    </section>

    <section>
      <h2>5. Your Rights & Choices</h2>
      <p>Depending on your region (e.g., GDPR, CCPA), you have the following rights:</p>
      <ul>
        {#each userRights as right}
          <li>{right}</li>
        {/each}
      </ul>
      <p>To exercise your rights, please contact us using the email below.</p>
    </section>

    <section>
      <h2>6. Children's Privacy</h2>
      <p>{appName} does not knowingly collect personal information from children under 13 (or under 16 in certain regions). If you believe we have inadvertently collected such data, please contact us to delete it.</p>
    </section>

    <section>
      <h2>7. Changes to This Policy</h2>
      <p>We may update this Privacy Policy from time to time. We will notify you of any material changes via an in-app notice or by updating the "Last updated" date. Continued use of the app after changes constitutes acceptance of the revised policy.</p>
    </section>

    <section>
      <h2>8. Contact Us</h2>
      <p>If you have any questions, concerns, or requests regarding this Privacy Policy or your data, please contact us at:</p>
      <div class="contact-box">
        <strong>{appName} support email</strong><br />
        Email: <a href="mailto:{contactEmail}">{contactEmail}</a>
      </div>
    </section>

    <div class="consent-footer">
      <p>By using {appName}, you consent to the practices described in this Privacy Policy.</p>
    </div>
  </div>
</div>

<style>
  .privacy-container {
    max-width: 900px;
    margin: 0 auto;
    padding: 2rem 1.5rem;
    font-family: system-ui, -apple-system, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
    line-height: 1.6;
    color: #1f2937;
    background: #ffffff;
  }

  .privacy-header {
    text-align: center;
    margin-bottom: 2.5rem;
    border-bottom: 1px solid #e5e7eb;
    padding-bottom: 1.5rem;
  }

  h1 {
    font-size: 2.5rem;
    font-weight: 700;
    margin: 0 0 0.5rem 0;
    background: linear-gradient(135deg, #1e3c72, #2a5298);
    background-clip: text;
    -webkit-background-clip: text;
    color: transparent;
  }

  .effective-date {
    color: #6b7280;
    font-size: 0.9rem;
    margin-bottom: 0.75rem;
  }

  .app-tagline {
    font-size: 1.1rem;
    color: #374151;
  }

  .privacy-content section {
    margin-bottom: 2rem;
  }

  h2 {
    font-size: 1.5rem;
    font-weight: 600;
    margin-bottom: 1rem;
    color: #111827;
    border-left: 4px solid #3b82f6;
    padding-left: 0.75rem;
  }

  h3 {
    font-size: 1.2rem;
    font-weight: 600;
    margin: 0 0 0.4rem 0;
    color: #1f2937;
  }

  ul {
    padding-left: 1.5rem;
    margin: 0.75rem 0;
  }

  li {
    margin-bottom: 0.4rem;
  }

  .third-party-list {
    display: flex;
    flex-wrap: wrap;
    gap: 1rem;
    margin: 1rem 0;
  }

  .third-party-card {
    flex: 1;
    min-width: 200px;
    background: #f9fafb;
    border-radius: 12px;
    padding: 1rem;
    border: 1px solid #e5e7eb;
    transition: box-shadow 0.2s ease;
  }

  .third-party-card:hover {
    box-shadow: 0 4px 12px rgba(0, 0, 0, 0.05);
  }

  .third-party-card a {
    color: #2563eb;
    text-decoration: none;
    font-size: 0.9rem;
    font-weight: 500;
  }

  .third-party-card a:hover {
    text-decoration: underline;
  }

  .contact-box {
    background: #f0f4fe;
    padding: 1rem 1.5rem;
    border-radius: 12px;
    margin-top: 0.5rem;
    border-left: 4px solid #3b82f6;
  }

  .consent-footer {
    margin-top: 2.5rem;
    padding-top: 1.5rem;
    text-align: center;
    font-size: 0.85rem;
    color: #6b7280;
    border-top: 1px solid #e5e7eb;
  }

  a {
    color: #2563eb;
    text-decoration: none;
  }

  a:hover {
    text-decoration: underline;
  }

  @media (max-width: 640px) {
    .privacy-container {
      padding: 1rem;
    }
    h1 {
      font-size: 1.8rem;
    }
    .third-party-card {
      min-width: 100%;
    }
  }
</style>