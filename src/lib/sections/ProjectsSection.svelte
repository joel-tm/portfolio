<script>
  import './ProjectsSection.css';

  const projects = [
    {
      title: 'Workflow Platform',
      subtitle: 'OPERATIONS AUTOMATION FOR DELIVERY TEAMS',
      text: 'A workflow platform that unifies approvals, SLA tracking, and escalation handling for distributed operations.',
      image: 'https://images.unsplash.com/photo-1451187580459-43490279c0fa?auto=format&fit=crop&w=1200&q=80',
    },
    {
      title: 'Revenue Insights',
      subtitle: 'ANALYTICS DASHBOARD FOR ENTERPRISE SALES',
      text: 'Data pipelines and visual analytics surfaces that help leadership spot revenue trends and bottlenecks quickly.',
      image: 'https://images.unsplash.com/photo-1460925895917-afdab827c52f?auto=format&fit=crop&w=1200&q=80',
    },
    {
      title: 'Community Housing',
      subtitle: 'TOOLS TO SUPPORT CITY-SCALE SERVICE DELIVERY',
      text: 'A central case coordination tool helping local teams prioritize requests, route cases, and improve response quality.',
      image: 'https://images.unsplash.com/photo-1449824913935-59a10b8d2000?auto=format&fit=crop&w=1200&q=80',
    },
    {
      title: 'Portfolio CMS',
      subtitle: 'LIGHTWEIGHT CONTENT OPERATIONS WORKBENCH',
      text: 'A modular publishing workspace with role-based editing and deployment-safe content workflows.',
      image: 'https://images.unsplash.com/photo-1552664730-d307ca884978?auto=format&fit=crop&w=1200&q=80',
    },
    {
      title: 'Signal Assistant',
      subtitle: 'INTELLIGENT ALERT ROUTING FOR SUPPORT SYSTEMS',
      text: 'A triage assistant that clusters incidents and routes critical alerts to the right teams in real time.',
      image: 'https://images.unsplash.com/photo-1545239351-1141bd82e8a6?auto=format&fit=crop&w=1200&q=80',
    },
  ];

  let trackNode;
  let activeProject = null;

  function scrollRail(direction) {
    if (!trackNode) {
      return;
    }

    const distance = Math.max(320, Math.round(trackNode.clientWidth * 0.72));
    trackNode.scrollBy({ left: direction * distance, behavior: 'smooth' });
  }

  function openProject(project) {
    activeProject = project;
  }

  function closeProject() {
    activeProject = null;
  }

  function handleWindowKeydown(event) {
    if (event.key === 'Escape') {
      closeProject();
    }
  }
</script>

<svelte:window on:keydown={handleWindowKeydown} />

<section class="projects-section" id="projects">
  <div class="section-inner">
    <div class="projects-head">
      <p>Selected work</p>
      <h2>Projects</h2>
    </div>

    <div class="projects-rail" aria-label="Projects showcase">
      <button class="projects-arrow projects-arrow-left" aria-label="Previous projects" on:click={() => scrollRail(-1)}></button>

      <div class="projects-track" bind:this={trackNode}>
        {#each projects as project}
          <button class="project-card" type="button" on:click={() => openProject(project)} aria-label={`Open ${project.title} details`}>
            <div class="project-media" style={`background-image: linear-gradient(180deg, rgba(0, 0, 0, 0.03), rgba(0, 0, 0, 0.45)), url(${project.image});`}></div>
            <div class="project-copy">
              <h3>{project.title}</h3>
              <p class="project-subtitle">{project.subtitle}</p>
              <p>{project.text}</p>
            </div>
          </button>
        {/each}
      </div>

      <button class="projects-arrow projects-arrow-right" aria-label="Next projects" on:click={() => scrollRail(1)}></button>
    </div>
  </div>
</section>

{#if activeProject}
  <div class="projects-modal-overlay">
    <button class="projects-modal-backdrop" type="button" aria-label="Close project details" on:click={closeProject}></button>
    <div class="projects-modal" role="dialog" aria-modal="true" aria-label="Project details" tabindex="-1">
      <button class="projects-modal-close" type="button" aria-label="Close project details" on:click={closeProject}>x</button>
      <div class="projects-modal-media" style={`background-image: linear-gradient(180deg, rgba(0, 0, 0, 0.08), rgba(0, 0, 0, 0.5)), url(${activeProject.image});`}></div>
      <div class="projects-modal-copy">
        <p class="projects-modal-label">Project</p>
        <h3>{activeProject.title}</h3>
        <p class="projects-modal-subtitle">{activeProject.subtitle}</p>
        <p>{activeProject.text}</p>
      </div>
    </div>
  </div>
{/if}
