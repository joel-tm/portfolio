<script>
  const navLeft = [
    { title: 'Innovative', subtitle: 'systems' },
    { title: 'Launch', subtitle: 'portfolio' },
    { title: 'Design', subtitle: 'tooling' },
  ];

  const navRight = [
    { title: 'Space', subtitle: 'projects' },
    { title: 'Get In', subtitle: 'touch' },
    { title: 'Quick', subtitle: 'quote' },
  ];

  const services = [
    {
      icon: '◈',
      title: 'Backend Systems',
      text: 'I build service layers, APIs, and deployment-aware architectures that stay maintainable as a codebase expands.',
      link: 'service architecture',
    },
    {
      icon: '✦',
      title: 'Web Development',
      text: 'Svelte, TypeScript, and product-facing frontend work with strong attention to responsiveness, state flow, and clarity.',
      link: 'frontend delivery',
    },
    {
      icon: '▣',
      title: 'Mobile-first UI',
      text: 'Interfaces designed to read well on every screen, with practical performance budgets and deliberate interaction detail.',
      link: 'mobile design',
    },
    {
      icon: '⟡',
      title: 'Interactive Tools',
      text: 'Internal dashboards, workflow surfaces, and operational tooling that help teams understand the state of their systems.',
      link: 'developer tooling',
    },
  ];

  const checklist = [
    'Production-ready web applications',
    'Interactive internal dashboards',
    'Modern frontend architecture',
    'API and delivery engineering',
  ];

  const articles = [
    {
      title: 'How I structure frontend systems for long-lived products',
      category: 'Engineering Notes',
      text: 'Patterns for component composition, state boundaries, and design consistency when a product has to keep shipping without turning into a rewrite candidate.',
    },
    {
      title: 'Observability decisions that save time later',
      category: 'Platform Notes',
      text: 'A practical approach to logs, metrics, release visibility, and issue triage for small teams that still need high confidence in production.',
    },
  ];

  const brands = ['Svelte', 'TypeScript', 'Node', 'Postgres', 'Docker', 'GitHub'];
</script>

<svelte:head>
  <title>Joel | Software Developer</title>
</svelte:head>

<main class="portfolio-frame">
  <section class="hero-shell">
    <div class="hero-sky"></div>

    <header class="top-command">
      <div class="command-grid command-grid-left">
        {#each navLeft as item}
          <a class="nav-tile" href="#services">
            <span class="nav-glyph"></span>
            <strong>{item.title}</strong>
            <small>{item.subtitle}</small>
          </a>
        {/each}
      </div>

      <div class="brand-mark">
        <span class="brand-wings"></span>
        <strong>JOEL</strong>
        <small>software developer</small>
      </div>

      <div class="command-grid command-grid-right">
        {#each navRight as item}
          <a class="nav-tile" href="#contact">
            <span class="nav-glyph"></span>
            <strong>{item.title}</strong>
            <small>{item.subtitle}</small>
          </a>
        {/each}
      </div>
    </header>

    <div class="hero-stage">
      <button class="stage-arrow stage-arrow-left" aria-label="Previous section"></button>
      <button class="stage-arrow stage-arrow-right" aria-label="Next section"></button>

      <div class="hero-copy">
        <div class="hero-dots" aria-hidden="true">
          <span></span>
          <span></span>
          <span></span>
        </div>

        <p class="eyebrow">Launching Creative Engineering</p>
        <h1>Software Developer</h1>
        <p class="hero-subtitle">Full-stack systems, modern web interfaces, and mobile-ready product delivery.</p>
        <a class="launch-button" href="#services">Launch Portfolio</a>
      </div>

      <div class="orbit-glow" aria-hidden="true"></div>
    </div>
  </section>

  <section class="services-strip" id="services">
    {#each services as service}
      <article class="service-card">
        <div class="service-icon">
          <span>{service.icon}</span>
        </div>
        <h2>{service.title}</h2>
        <p>{service.text}</p>
        <a href="#contact">{service.link}</a>
      </article>
    {/each}
  </section>

  <section class="feature-band">
    <div class="feature-visual">
      <div class="screen-stack">
        <div class="screen-main">
          <span class="screen-label">Think</span>
          <strong>Build clean, scalable products.</strong>
        </div>
        <div class="screen-tablet"></div>
        <div class="screen-phone"></div>
      </div>
    </div>

    <div class="feature-copy">
      <div class="feature-mini-grid">
        <div>
          <strong>We innovate</strong>
          <small>for the future</small>
        </div>
        <div>
          <strong>We prepare</strong>
          <small>for scale</small>
        </div>
        <div>
          <strong>We launch</strong>
          <small>with intent</small>
        </div>
      </div>

      <h2>Innovate your web stack.</h2>
      <p>
        I work across interface design, frontend implementation, backend integration, and delivery flow to ship software that looks sharp and behaves reliably.
      </p>

      <ul>
        {#each checklist as item}
          <li>{item}</li>
        {/each}
      </ul>

      <a class="secondary-button" href="#contact">Discuss your project</a>
    </div>
  </section>

  <section class="insights-row">
    <div class="articles-panel">
      {#each articles as article}
        <article class="insight-card">
          <div class="insight-thumb"></div>
          <div class="insight-copy">
            <p class="insight-meta">{article.category}</p>
            <h3>{article.title}</h3>
            <p>{article.text}</p>
            <a href="#contact">Read more</a>
          </div>
        </article>
      {/each}
    </div>

    <aside class="testimonial-panel">
      <blockquote>
        Structured delivery, sharp frontend implementation, and pragmatic engineering decisions. The work consistently balanced speed with maintainability.
      </blockquote>
      <p class="testimonial-author">Client feedback • product engineering engagement</p>
    </aside>
  </section>

  <footer class="brand-row" id="contact">
    <div class="contact-block">
      <p class="eyebrow">Get In Touch</p>
      <h2>Available for product builds, redesigns, and engineering consulting.</h2>
      <div class="contact-links">
        <a href="mailto:joel@example.com">joel@example.com</a>
        <a href="https://github.com" target="_blank" rel="noreferrer">GitHub</a>
        <a href="https://linkedin.com" target="_blank" rel="noreferrer">LinkedIn</a>
      </div>
    </div>

    <div class="brand-list" aria-label="Technology stack">
      {#each brands as brand}
        <span>{brand}</span>
      {/each}
    </div>
  </footer>
</main>