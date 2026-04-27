<script>
  let name = '';
  let email = '';
  let confirmationChecked = false;
  let successMessage = '';
  let errorMessage = '';

  const deletionEmail = "privacy@yourapp.com";

  function submitDeletionRequest() {
    // Reset messages
    successMessage = '';
    errorMessage = '';

    // Validation
    if (!name.trim()) {
      errorMessage = 'Please enter your full name.';
      return;
    }
    if (!email.trim()) {
      errorMessage = 'Please enter your email address.';
      return;
    }
    const emailPattern = /^[^\s@]+@([^\s@.,]+\.)+[^\s@.,]{2,}$/;
    if (!emailPattern.test(email)) {
      errorMessage = 'Please enter a valid email address.';
      return;
    }
    if (!confirmationChecked) {
      errorMessage = 'You must confirm that you understand the irreversible nature of deletion.';
      return;
    }

    // Simulate sending deletion request
    // In a real app, you'd send this to your backend API
    console.log('Deletion request submitted for:', { name, email });
    successMessage = `✅ Request received! A confirmation email has been sent to ${email}. Our team will verify your identity and process the deletion within 30 days.`;

    // Optionally reset form fields (keep email/name for UX, but clear checkbox)
    name = '';
    email = '';
    confirmationChecked = false;
    
    // Auto-clear success message after 8 seconds
    setTimeout(() => {
      successMessage = '';
    }, 8000);
  }
</script>

<main>
  <div class="container">
    <header>
      <h1>Account & Data Deletion Request</h1>
      <p>You have the right to request the permanent deletion of your account and associated personal data. Below you'll find instructions to submit a request, along with a transparent breakdown of what information is removed and what may be retained for legitimate purposes.</p>
    </header>

    <div class="split-layout">
      <!-- LEFT COLUMN: Request Methods -->
      <div class="card request-card">
        <h2>✍️ How to request deletion</h2>
        <p>Choose the method that works best for you. All requests are reviewed manually to prevent unauthorized deletions.</p>

        <div class="method">
          <h3>Option 1: Online request form</h3>
          <form on:submit|preventDefault={submitDeletionRequest}>
            <div class="form-group">
              <label for="name">Full name <span class="required">*</span></label>
              <input type="text" id="name" bind:value={name} placeholder="John Doe" required />
            </div>
            <div class="form-group">
              <label for="email">Email address (associated with account) <span class="required">*</span></label>
              <input type="email" id="email" bind:value={email} placeholder="john@example.com" required />
            </div>
            <div class="form-group checkbox">
              <label>
                <input type="checkbox" bind:checked={confirmationChecked} />
                <span>I understand that account deletion is <strong>permanent and irreversible</strong>. All personal data and content will be removed from active systems, and I will lose access to my account.</span>
              </label>
            </div>
            <button type="submit" class="btn btn-danger">Request permanent deletion</button>
          </form>
          {#if successMessage}
            <div class="message success">{successMessage}</div>
          {/if}
          {#if errorMessage}
            <div class="message error">{errorMessage}</div>
          {/if}
        </div>

        <div class="method">
          <h3>Option 2: Email request</h3>
          <p>Send an email to <a href="mailto:{deletionEmail}?subject=Account%20Deletion%20Request&body=Please%20delete%20my%20account%20and%20associated%20data.%0A%0AName%3A%20%3CYour%20full%20name%3E%0AEmail%3A%20%3CAccount%20email%3E%0AUsername%3A%20%3CIf%20applicable%3E">{deletionEmail}</a> with the subject line <strong>"Account Deletion Request"</strong>. Include your full name, account email, and username (if any). For security, we may reply with an identity verification step.</p>
          <div class="info-note">
            📌 <strong>Processing timeline:</strong> We will respond within 7 days and typically complete the deletion within 30 days after verification.
          </div>
        </div>
      </div>

      <!-- RIGHT COLUMN: Deletion vs Retention summary -->
      <div class="card summary-card">
        <h2>📋 Data deletion & retention summary</h2>
        <div class="summary-blocks">
          <div class="deleted-block">
            <h3>🗑️ Data that is <strong>deleted</strong> (fully removed)</h3>
            <ul>
              <li>Account profile: name, email, avatar, bio, preferences</li>
              <li>All private messages & conversations</li>
              <li>Personal files, images, documents uploaded to your account</li>
              <li>Activity logs, session history, and device tokens</li>
              <li>Linked third-party connections (e.g., Google, Discord)</li>
              <li>Billing/payment method details (except legal retention — see below)</li>
            </ul>
          </div>
          <div class="retained-block">
            <h3>📌 Data that may be <strong>retained</strong> (limited purpose)</h3>
            <ul>
              <li><strong>Anonymized usage analytics:</strong> Aggregated metrics, no personal identifiers</li>
              <li><strong>Financial/transaction records:</strong> Retained for 7 years (tax & legal compliance)</li>
              <li><strong>Security & fraud logs:</strong> Hashed email/IP may be kept for 90 days to prevent abuse</li>
              <li><strong>Backups & disaster recovery:</strong> Residual copies are deleted within 60 days</li>
              <li><strong>Public content (if applicable):</strong> Posts/comments in public spaces become anonymized (attributed to "Deleted User")</li>
            </ul>
            <div class="legal-note">🔒 Retention is based on legitimate interests, legal obligations, and fraud prevention. All retained data is pseudonymized or securely isolated.</div>
          </div>
        </div>
      </div>
    </div>

    <!-- DETAILED SECTION: Extended policy -->
    <div class="detailed-policy">
      <h2>🔍 What exactly happens to your data?</h2>
      <div class="grid-detailed">
        <div>
          <h3>✔️ Data that is permanently deleted</h3>
          <ul>
            <li>Personally identifiable information (PII) from your account profile.</li>
            <li>Your unique account ID and associated metadata (creation date, last login).</li>
            <li>Saved searches, bookmarks, watchlists, or custom filters.</li>
            <li>Cloud-stored documents, images, and any content inside private folders.</li>
            <li>API keys, OAuth tokens, and integration settings.</li>
            <li>Email notification preferences and communication history.</li>
            <li>Support tickets (redacted after 30 days).</li>
          </ul>
        </div>
        <div>
          <h3>⏳ Data that is retained (with safeguards)</h3>
          <ul>
            <li><strong>Transaction records:</strong> Invoices, receipts, tax documents – retained for 7 years as required by financial regulations.</li>
            <li><strong>Deletion request logs:</strong> Email, request ID, and timestamp (stored for 1 year to prove compliance with data protection laws).</li>
            <li><strong>Anonymized contribution metrics:</strong> e.g., "user helped flag spam 5 times" – not linked to identity after deletion.</li>
            <li><strong>Fraud prevention:</strong> Hashed version of your email address kept in a "do not register" list for 90 days to prevent immediate account recreation.</li>
            <li><strong>Legal holds:</strong> If an account is under active legal investigation, relevant data may be retained until the case resolves.</li>
          </ul>
        </div>
      </div>
      <div class="retention-periods">
        <h4>📅 Retention timeline overview</h4>
        <div class="timeline">
          <span>Immediate (0-24h):</span> Profile, messages, personal files.<br/>
          <span>Within 30 days:</span> Backups purged, analytics aggregated.<br/>
          <span>Up to 90 days:</span> Security logs, hashed identifiers.<br/>
          <span>7 years:</span> Financial/accounting records (if any).<br/>
          <span>Indefinite (anonymized):</span> Non-personal statistical data.
        </div>
      </div>
    </div>

    <footer>
      <p>📧 Questions about your data? Contact our Data Protection Officer at <a href="mailto:dpo@yourapp.com">dpo@yourapp.com</a>. We are committed to GDPR, CCPA, and global privacy standards.</p>
      <p class="small">Last updated: April 2026 — This policy applies to account deletion requests. Deleting your account does not affect data that others may have shared about you (we will not delete messages sent to you by others without their own request).</p>
    </footer>
  </div>
</main>

<style>
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }

  main {
    font-family: system-ui, -apple-system, 'Segoe UI', Roboto, 'Helvetica Neue', sans-serif;
    background: linear-gradient(145deg, #f8fafc 0%, #eff3f8 100%);
    color: #0f172a;
    line-height: 1.5;
    padding: 2rem 1rem;
  }

  .container {
    max-width: 1280px;
    margin: 0 auto;
  }

  header {
    margin-bottom: 2rem;
    text-align: center;
  }

  h1 {
    font-size: 2.2rem;
    font-weight: 700;
    background: linear-gradient(135deg, #1e293b, #3b82f6);
    background-clip: text;
    -webkit-background-clip: text;
    color: transparent;
    margin-bottom: 0.75rem;
    letter-spacing: -0.01em;
  }

  header p {
    font-size: 1.1rem;
    color: #334155;
    max-width: 780px;
    margin: 0 auto;
  }

  /* Split layout */
  .split-layout {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 1.8rem;
    margin-bottom: 2.5rem;
  }

  .card {
    background: white;
    border-radius: 1.5rem;
    box-shadow: 0 10px 25px -5px rgba(0, 0, 0, 0.05), 0 8px 10px -6px rgba(0, 0, 0, 0.02);
    padding: 1.5rem;
    transition: transform 0.1s ease;
    border: 1px solid #e2e8f0;
  }

  .request-card h2, .summary-card h2 {
    font-size: 1.5rem;
    font-weight: 600;
    border-left: 5px solid #ef4444;
    padding-left: 0.9rem;
    margin-bottom: 1rem;
  }

  .method {
    margin-bottom: 2rem;
  }

  .method h3 {
    font-size: 1.2rem;
    font-weight: 600;
    margin: 1rem 0 0.75rem 0;
    color: #0f172a;
  }

  .form-group {
    margin-bottom: 1.2rem;
  }

  label {
    font-weight: 500;
    display: block;
    margin-bottom: 0.4rem;
    color: #1e293b;
  }

  .required {
    color: #ef4444;
  }

  input[type="text"],
  input[type="email"] {
    width: 100%;
    padding: 0.75rem 1rem;
    border: 1px solid #cbd5e1;
    border-radius: 0.75rem;
    font-size: 1rem;
    transition: all 0.2s;
    background-color: #fff;
  }

  input:focus {
    outline: none;
    border-color: #3b82f6;
    box-shadow: 0 0 0 3px rgba(59,130,246,0.2);
  }

  .checkbox {
    display: flex;
    align-items: flex-start;
    gap: 0.5rem;
  }
  .checkbox label {
    display: flex;
    gap: 0.75rem;
    font-weight: normal;
    cursor: pointer;
  }
  .checkbox input {
    margin-top: 0.2rem;
    flex-shrink: 0;
  }

  .btn {
    border: none;
    padding: 0.75rem 1.4rem;
    border-radius: 2rem;
    font-weight: 600;
    cursor: pointer;
    transition: 0.2s;
    font-size: 0.95rem;
  }

  .btn-danger {
    background-color: #ef4444;
    color: white;
    box-shadow: 0 1px 2px rgba(0,0,0,0.05);
  }
  .btn-danger:hover {
    background-color: #dc2626;
    transform: translateY(-1px);
    box-shadow: 0 8px 16px -6px rgba(239,68,68,0.3);
  }

  .message {
    margin-top: 1rem;
    padding: 0.75rem 1rem;
    border-radius: 0.75rem;
    font-size: 0.9rem;
  }
  .success {
    background-color: #dcfce7;
    color: #166534;
    border-left: 4px solid #22c55e;
  }
  .error {
    background-color: #fee2e2;
    color: #991b1b;
    border-left: 4px solid #ef4444;
  }

  .info-note {
    background: #f1f5f9;
    padding: 0.7rem 1rem;
    border-radius: 0.75rem;
    margin-top: 0.85rem;
    font-size: 0.9rem;
    border: 1px solid #e2e8f0;
  }

  .summary-blocks {
    display: flex;
    flex-direction: column;
    gap: 1.5rem;
  }
  .deleted-block, .retained-block {
    background: #fef9f5;
    padding: 1rem 1.2rem;
    border-radius: 1rem;
  }
  .deleted-block {
    background: #fff5f5;
    border-left: 4px solid #ef4444;
  }
  .retained-block {
    background: #f0f9ff;
    border-left: 4px solid #3b82f6;
  }
  .deleted-block h3, .retained-block h3 {
    font-size: 1.1rem;
    margin-bottom: 0.75rem;
  }
  ul {
    padding-left: 1.3rem;
    margin: 0.5rem 0;
  }
  li {
    margin: 0.4rem 0;
  }
  .legal-note {
    margin-top: 0.7rem;
    font-size: 0.8rem;
    background: #eef2ff;
    padding: 0.5rem;
    border-radius: 0.6rem;
    color: #1e3a8a;
  }

  .detailed-policy {
    background: white;
    border-radius: 1.5rem;
    padding: 1.8rem;
    margin-top: 0.8rem;
    border: 1px solid #e2e8f0;
    box-shadow: 0 1px 3px rgba(0,0,0,0.03);
  }
  .detailed-policy h2 {
    font-size: 1.5rem;
    margin-bottom: 1rem;
    font-weight: 600;
  }
  .grid-detailed {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 1.5rem;
    margin-bottom: 1.5rem;
  }
  .grid-detailed h3 {
    margin-bottom: 0.6rem;
    font-weight: 600;
    color: #0c4a6e;
  }
  .retention-periods {
    background: #f8fafc;
    border-radius: 1rem;
    padding: 1rem;
    margin-top: 0.5rem;
  }
  .retention-periods h4 {
    font-weight: 600;
    margin-bottom: 0.6rem;
  }
  .timeline {
    font-size: 0.9rem;
    line-height: 1.6;
  }
  .timeline span {
    font-weight: 600;
    background: #e2e8f0;
    padding: 0.1rem 0.3rem;
    border-radius: 0.3rem;
  }

  footer {
    margin-top: 2.5rem;
    font-size: 0.85rem;
    text-align: center;
    color: #475569;
    border-top: 1px solid #cbd5e1;
    padding-top: 1.8rem;
  }
  footer .small {
    font-size: 0.75rem;
    margin-top: 0.5rem;
    color: #64748b;
  }
  a {
    color: #2563eb;
    text-decoration: none;
  }
  a:hover {
    text-decoration: underline;
  }

  @media (max-width: 820px) {
    .split-layout {
      grid-template-columns: 1fr;
      gap: 1.5rem;
    }
    .grid-detailed {
      grid-template-columns: 1fr;
      gap: 1rem;
    }
    h1 {
      font-size: 1.8rem;
    }
    .card {
      padding: 1.2rem;
    }
  }
</style>