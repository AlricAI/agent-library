# Index

> <div class="hero">
  <div class="hero-inner">
    <div class="hero-text">
      <h1><span class="accent">Ratatoskr</span></h1>
      <p class="tagline

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
<div class="hero">
  <div class="hero-inner">
    <div class="hero-text">
      <h1><span class="accent">Ratatoskr</span></h1>
      <p class="tagline">
        Reliable event-driven messaging for .NET — transport-agnostic publishing, durable Outbox &amp; Inbox patterns, and native CloudEvents support.
      </p>
      <div class="hero-actions">
        <a href="getting-started.md" class="btn-hero primary">Get Started</a>
        <a href="architecture.md" class="btn-hero secondary">Architecture</a>
        <a href="api/" class="btn-hero secondary">API Reference</a>
      </div>
    </div>
    <div class="hero-mascot">
      <img src="images/mascot_lines_glow.png" alt="Ratatoskr — the cyber squirrel messenger">
    </div>
  </div>
</div>

<div class="install-banner">
  <div class="install-banner-inner">
    <span>Install via NuGet:</span>
    <code>dotnet add package Ratatoskr</code>
  </div>
</div>

<div class="features">
  <h2>Why Ratatoskr?</h2>
  <p class="section-subtitle">Everything you need for reliable, observable messaging in .NET applications.</p>
  <div class="feature-grid">
    <div class="feature-card">
      <span class="feature-icon">&#x1f4e1;</span>
      <h3>Channel-First Design</h3>
      <p>Declare channels with intent — event publish, command consume — and attach message types, handlers, and transports in one place.</p>
    </div>
    <div class="feature-card">
      <span class="feature-icon">&#x1f512;</span>
      <h3>Transactional Outbox</h3>
      <p>Messages are persisted in the same database transaction as your business data. Nothing is lost, even if the broker goes down.</p>
    </div>
    <div class="feature-card">
      <span class="feature-icon">&#x1f4e5;</span>
      <h3>Durable Inbox</h3>
      <p>Per-handler deduplication and retry with persistent state via EF Core. Poisoned messages are quarantined, not dropped.</p>
    </div>
    <div class="feature-card">
      <span class="feature-icon">&#x2601;</span>
      <h3>CloudEvents Native

*[truncated — see source for full prompt]*