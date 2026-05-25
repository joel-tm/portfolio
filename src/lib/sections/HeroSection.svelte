<script>
  import './HeroSection.css';

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

  const particles = [
    { x: 12, y: 24, size: 4, depth: 0.6, opacity: 0.5 },
    { x: 24, y: 58, size: 6, depth: 1.1, opacity: 0.72 },
    { x: 31, y: 36, size: 3, depth: 0.8, opacity: 0.48 },
    { x: 42, y: 18, size: 5, depth: 1.3, opacity: 0.68 },
    { x: 49, y: 46, size: 7, depth: 1.8, opacity: 0.82 },
    { x: 58, y: 28, size: 4, depth: 0.9, opacity: 0.54 },
    { x: 67, y: 62, size: 5, depth: 1.2, opacity: 0.62 },
    { x: 74, y: 22, size: 3, depth: 0.7, opacity: 0.44 },
    { x: 83, y: 48, size: 6, depth: 1.5, opacity: 0.78 },
    { x: 90, y: 30, size: 4, depth: 0.85, opacity: 0.52 },
  ];

  let pointerX = 0;
  let pointerY = 0;

  function trackPointer(node) {
    function handlePointerMove(event) {
      const bounds = node.getBoundingClientRect();
      pointerX = (event.clientX - bounds.left) / bounds.width - 0.5;
      pointerY = (event.clientY - bounds.top) / bounds.height - 0.5;
    }

    function resetPointer() {
      pointerX = 0;
      pointerY = 0;
    }

    node.addEventListener('mousemove', handlePointerMove);
    node.addEventListener('mouseleave', resetPointer);

    return {
      destroy() {
        node.removeEventListener('mousemove', handlePointerMove);
        node.removeEventListener('mouseleave', resetPointer);
      },
    };
  }
</script>

<section class="hero-shell">
  <div class="hero-sky"></div>

  <div class="section-inner">
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
      <!--below is the top part --->
      <div class="brand-mark">
        <span class="brand-wings"></span>
        <strong>JO</strong>
        <small>software Engineer</small>
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

    <div class="hero-stage" use:trackPointer>
      <button class="stage-arrow stage-arrow-left" aria-label="Previous section"></button>
      <button class="stage-arrow stage-arrow-right" aria-label="Next section"></button>

      <div class="particle-field" aria-hidden="true">
        {#each particles as particle}
          <span
            class="particle"
            style={`left: calc(${particle.x}% + ${pointerX * particle.depth * 18}px); top: calc(${particle.y}% + ${pointerY * particle.depth * 18}px); width: ${particle.size}px; height: ${particle.size}px; opacity: ${particle.opacity};`}
          ></span>
        {/each}
      </div>

      <div class="hero-copy">
        <div class="hero-dots" aria-hidden="true">
          <span></span>
          <span></span>
          <span></span>
        </div>

        <p class="eyebrow">Software architecture</p>
        <h1>Software Engineer</h1>
        <p class="hero-subtitle">Full-stack systems, modern web interfaces, and cloud-infrastructure deployment.</p>
        <a class="launch-button" href="#services">Launch Portfolio</a>
      </div>
    </div>
  </div>
</section>