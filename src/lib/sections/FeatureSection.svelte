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
  <div class="section-inner feature-band-inner">
    <div class="feature-visual">
      <div class="screen-stack">
        <div class="screen-main">
          <span class="screen-label">Think</span>
          <strong>Build clean, scalable products.</strong>

          <div class="screen-main-ui" aria-hidden="true">
            <div class="screen-ui-row">
              <span>Pipeline</span>
              <span>99.4%</span>
            </div>
            <div class="screen-ui-bars">
              <i style="--bar: 78%"></i>
              <i style="--bar: 54%"></i>
              <i style="--bar: 86%"></i>
              <i style="--bar: 62%"></i>
              <i style="--bar: 92%"></i>
            </div>
            <div class="screen-ui-tags">
              <span>UI</span>
              <span>API</span>
              <span>Cloud</span>
            </div>
          </div>
        </div>

        <div class="screen-tablet" aria-hidden="true">
          <div class="tablet-ui">
            <p>Sprint</p>
            <div class="tablet-wave"></div>
            <small>Velocity +12%</small>
          </div>
        </div>

        <div class="screen-phone" aria-hidden="true">
          <div class="phone-ui">
            <span class="phone-dot"></span>
            <span class="phone-line short"></span>
            <span class="phone-line"></span>
            <span class="phone-line"></span>
          </div>
        </div>
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
  </div>
</section>