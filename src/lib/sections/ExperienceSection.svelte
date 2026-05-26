<script>
  import './ExperienceSection.css';

  const experiences = [
    {
      period: '2024 - Present',
      role: 'Full-stack Engineer',
      company: 'Independent Consulting',
      summary: 'Designing and shipping product-ready systems across frontend architecture, APIs, and cloud deployment workflows.',
      highlights: ['Svelte + TypeScript delivery', 'Cloud infrastructure handling', 'Production release pipelines'],
    },
    {
      period: '2022 - 2024',
      role: 'Frontend Engineer',
      company: 'Product Teams',
      summary: 'Built scalable UI systems and component libraries focused on consistency, performance, and long-term maintainability.',
      highlights: ['Design system implementation', 'State and routing strategy', 'Performance budget enforcement'],
    },
    {
      period: '2020 - 2022',
      role: 'Software Engineer',
      company: 'Engineering Projects',
      summary: 'Delivered internal tools, service integrations, and observability improvements to reduce operational friction.',
      highlights: ['Internal dashboards', 'API integrations', 'Logging and monitoring foundations'],
    },
  ];
</script>

<section class="experience-section" id="experience">
  <div class="section-inner">
    <header class="experience-head">
      <p>Journey</p>
      <h2>Experience</h2>
    </header>

    <div class="experience-grid">
      {#each experiences as item}
        <article class="experience-card">
          <p class="period">{item.period}</p>
          <h3>{item.role}</h3>
          <p class="company">{item.company}</p>
          <p class="summary">{item.summary}</p>
          <ul>
            {#each item.highlights as point}
              <li>{point}</li>
            {/each}
          </ul>
        </article>
      {/each}
    </div>
  </div>
</section>
