<script>
  import './ContactSection.css';

  const brands = ['Svelte', 'TypeScript', 'Node', 'Postgres', 'Docker', 'GitHub'];
</script>

<footer class="brand-row" id="contact">
  <div class="section-inner brand-row-inner">
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
  </div>
</footer>