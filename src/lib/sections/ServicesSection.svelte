<script>
  import './ServicesSection.css';

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
</script>

<section class="services-section" id="services">
  <div class="services-strip" />
  <div class="section-inner services-grid">
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
  </div>
</section>