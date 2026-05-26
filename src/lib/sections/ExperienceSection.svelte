<script>
  import './ExperienceSection.css';

  const experiences = [
    {
      period: '2024 - Present',
      role: 'Full-stack Engineer',
      company: 'Independent Consulting',
      summary: 'Designing and shipping product-ready systems across frontend architecture, APIs, and cloud deployment workflows.',
      highlights: ['Svelte + TypeScript delivery', 'Cloud infrastructure handling', 'Production release pipelines'],
      details: [
        'Led end-to-end delivery for product teams needing both rapid iteration and maintainable architecture.',
        'Owned cloud deployment flows, observability setup, and release hardening for stable production behavior.',
        'Delivered design-consistent frontend systems while keeping API and infrastructure decisions practical.',
      ],
      images: [
        'https://images.unsplash.com/photo-1451187580459-43490279c0fa?auto=format&fit=crop&w=1400&q=80',
        'https://images.unsplash.com/photo-1461749280684-dccba630e2f6?auto=format&fit=crop&w=1400&q=80',
        'https://images.unsplash.com/photo-1518770660439-4636190af475?auto=format&fit=crop&w=1400&q=80',
      ],
    },
    {
      period: '2022 - 2024',
      role: 'Frontend Engineer',
      company: 'Product Teams',
      summary: 'Built scalable UI systems and component libraries focused on consistency, performance, and long-term maintainability.',
      highlights: ['Design system implementation', 'State and routing strategy', 'Performance budget enforcement'],
      details: [
        'Built reusable component patterns and documentation workflows to speed up onboarding and reduce UI drift.',
        'Improved runtime performance with selective rendering strategy, route-level splitting, and bundle optimization.',
        'Worked closely with product and design to map roadmap priorities into stable implementation cycles.',
      ],
      images: [
        'https://images.unsplash.com/photo-1460925895917-afdab827c52f?auto=format&fit=crop&w=1400&q=80',
        'https://images.unsplash.com/photo-1498050108023-c5249f4df085?auto=format&fit=crop&w=1400&q=80',
        'https://images.unsplash.com/photo-1519389950473-47ba0277781c?auto=format&fit=crop&w=1400&q=80',
      ],
    },
  ];

  let activeExperience = null;
  let activeImageIndex = 0;

  function openExperience(item) {
    activeExperience = item;
    activeImageIndex = 0;
  }

  function closeExperience() {
    activeExperience = null;
    activeImageIndex = 0;
  }

  function nextImage() {
    if (!activeExperience) {
      return;
    }

    activeImageIndex = (activeImageIndex + 1) % activeExperience.images.length;
  }

  function previousImage() {
    if (!activeExperience) {
      return;
    }

    activeImageIndex = (activeImageIndex - 1 + activeExperience.images.length) % activeExperience.images.length;
  }

  function handleWindowKeydown(event) {
    if (!activeExperience) {
      return;
    }

    if (event.key === 'Escape') {
      closeExperience();
    }

    if (event.key === 'ArrowRight') {
      nextImage();
    }

    if (event.key === 'ArrowLeft') {
      previousImage();
    }
  }
</script>

<svelte:window on:keydown={handleWindowKeydown} />

<section class="experience-section" id="experience">
  <div class="section-inner">
    <header class="experience-head">
      <p>Journey</p>
      <h2>Experience</h2>
    </header>

    <div class="experience-grid">
      {#each experiences as item}
        <article class="experience-card">
          <button class="experience-open" type="button" on:click={() => openExperience(item)}>
            <p class="period">{item.period}</p>
            <h3>{item.role}</h3>
            <p class="company">{item.company}</p>
            <p class="summary">{item.summary}</p>
            <ul>
              {#each item.highlights as point}
                <li>{point}</li>
              {/each}
            </ul>
            <span class="experience-link">View experience details</span>
          </button>
        </article>
      {/each}
    </div>
  </div>
</section>

{#if activeExperience}
  <div class="experience-modal-overlay">
    <button class="experience-modal-backdrop" type="button" aria-label="Close experience details" on:click={closeExperience}></button>

    <div class="experience-modal" role="dialog" aria-modal="true" aria-label="Experience details" tabindex="-1">
      <button class="experience-modal-close" type="button" aria-label="Close experience details" on:click={closeExperience}>x</button>

      <div class="experience-modal-media" style={`background-image: linear-gradient(180deg, rgba(0, 0, 0, 0.05), rgba(0, 0, 0, 0.55)), url(${activeExperience.images[activeImageIndex]});`}>
        <button class="experience-image-nav experience-image-nav-left" type="button" on:click={previousImage} aria-label="Previous image"></button>
        <button class="experience-image-nav experience-image-nav-right" type="button" on:click={nextImage} aria-label="Next image"></button>
        <span class="experience-image-counter">{activeImageIndex + 1}/{activeExperience.images.length}</span>
      </div>

      <div class="experience-modal-content">
        <p class="period">{activeExperience.period}</p>
        <h3>{activeExperience.role}</h3>
        <p class="company">{activeExperience.company}</p>
        <p class="summary">{activeExperience.summary}</p>

        {#each activeExperience.details as line}
          <p class="detail-line">{line}</p>
        {/each}

        <ul>
          {#each activeExperience.highlights as point}
            <li>{point}</li>
          {/each}
        </ul>
      </div>
    </div>
  </div>
{/if}
