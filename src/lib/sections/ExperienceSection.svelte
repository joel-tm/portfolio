<script>
  import './ExperienceSection.css';


const experiences = [
  {
    period: 'Sep 2025 – Present',
    role: 'Full Stack Developer',
    company: 'Yokomet (Client: EQUAM Stiftung, Switzerland)',
    summary: 'Contributed to PrimaryPROMS, a healthcare web app focused on Patient-Reported Outcome Measures. Built robust backend APIs, automated CI/CD pipelines, and secure data integrations.',
    highlights: ['FastAPI & React', 'Azure Cloud Services', 'OAuth2 & Mutual TLS', 'CI/CD & ETL Pipelines'],
    details: [
      '• Contributed to the development of PrimaryPROMS, a healthcare web app focused on Patient-Reported Outcome Measures, built with FastAPI, React, and Azure.',
      '• Designed and implemented a GitHub Actions CI/CD pipeline to automate Docker image builds and deployments to Azure Container Apps.',
      '• Integrated external platform APIs using OAuth2 and Mutual TLS to enable secure data exchange with external clinics.',
      '• Built an automated data pipeline triggered by patient registration to fetch appointment data from external practices and forward it to third-party platforms.',
      '• Deployed and maintained a staging environment supporting a Power BI reporting solution on an Ubuntu Linux virtual machine.',
      '• Engineered backend APIs using Python and FastAPI by organizing application logic into schemas, models, routers, and service layers.',
      '• Implemented and deployed a daily scheduled cron job with container workflows to monitor upcoming appointments across an 8-day rolling window.',
      '• Configured system monitoring and automated alerting workflows to track data pipeline health.',
      '• Developed an automated ETL pipeline in Python that processed over 20,000 patient records using cron jobs within containerized microservices.',
      '• Configured and deployed Azure infrastructure services, including Storage Accounts, Key Vaults, Function Apps, and Container Apps, enabling secure and scalable frontend and backend deployments.'
    ],
    images: [
      'https://images.unsplash.com/photo-1461749280684-dccba630e2f6?auto=format&fit=crop&w=1400&q=80',
    ]
  },
  {
    period: 'Sep 2025 – Present',
    role: 'Full Stack Developer',
    company: 'Yokomet (Client: Mednota, Switzerland)',
    summary: 'Implemented backend features and built integration workflows using a microservice architecture and reliable REST APIs.',
    highlights: ['NestJS & PostgreSQL', 'React Frontend', 'Microservices', 'REST API Design'],
    details: [
      '• Implemented features in the backend using NestJS, supporting workflows through a microservice architecture.',
      '• Developed six REST APIs to integrate backend services with React-based frontend components, ensuring efficient and reliable data flow.'
    ],
    images: [
      'https://images.unsplash.com/photo-1460925895917-afdab827c52f?auto=format&fit=crop&w=1400&q=80',
    ]
  },
  {
    period: 'Jan 2025 – Apr 2025',
    role: 'Intern',
    company: 'STEAG Center for Smart City Technologies',
    summary: 'Developed a thermal imaging-based fire detection prototype for STEAG Energy Services using automated IoT edge systems.',
    highlights: ['Python & OpenCV', 'Raspberry Pi OS', 'Thermal Imaging', 'Real-time Data Logging'],
    details: [
      '• Developed a thermal imaging-based fire detection prototype for STEAG Energy Services.',
      '• Integrated a TOPDON TC001 thermal camera with a Linux-based Raspberry Pi OS for automated data collection.',
      '• Utilized thermal camera output to extract and analyze temperature data in real time using OpenCV and Python on Raspberry Pi.',
      '• Automated logging of image names and temperature data from the thermal camera into text files.',
      '• Generated annotated thermal image grids for visualization.'
    ],
    images: [
      'https://images.unsplash.com/photo-1519389950473-47ba0277781c?auto=format&fit=crop&w=1400&q=80'
      
    ]
  }
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
