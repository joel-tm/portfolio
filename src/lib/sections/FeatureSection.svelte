<script>
  import './FeatureSection.css';

  const checklist = [
    'Production-ready web applications',
    'Interactive internal dashboards',
    'Modern frontend architecture',
    'API and delivery engineering',
  ];
</script>

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