<script>
  import { onDestroy } from 'svelte';

  import './ProjectsSection.css';

  // 1. Style AI Images
  const styleAiImages = Object.entries(
    import.meta.glob('../assets/style-ai/*.{png,jpg,jpeg}', { eager: true, import: 'default' })
  )
    .sort(([leftPath], [rightPath]) => leftPath.localeCompare(rightPath))
    .map(([, imagePath]) => imagePath);

  const styleAiPrimaryImage = styleAiImages[0];

  // 2. Fire Identification Images
  const fireIdentificationImages = Object.entries(
    import.meta.glob('../assets/fire-identification/*.{png,jpg,jpeg}', { eager: true, import: 'default' })
  )
    .sort(([leftPath], [rightPath]) => leftPath.localeCompare(rightPath))
    .map(([, imagePath]) => imagePath);

  // 3. Robotic Arm Images
  const roboticarmImages = Object.entries(
    import.meta.glob('../assets/robotic-arm/*.{png,jpg,jpeg}', { eager: true, import: 'default' })
  )
    .sort(([leftPath], [rightPath]) => leftPath.localeCompare(rightPath))
    .map(([, imagePath]) => imagePath);

  // 4. AI Research Agent Images
  const aiResearchAgentImages = Object.entries(
    import.meta.glob('../assets/ai-research-agent/*.{png,jpg,jpeg}', { eager: true, import: 'default' })
  )
    .sort(([leftPath], [rightPath]) => leftPath.localeCompare(rightPath))
    .map(([, imagePath]) => imagePath);

  // 5. Stock Market Predictor Images
  const stockMarketPredictorImages = Object.entries(
    import.meta.glob('../assets/stock-market-predictor/*.{png,jpg,jpeg}', { eager: true, import: 'default' })
  )
    .sort(([leftPath], [rightPath]) => leftPath.localeCompare(rightPath))
    .map(([, imagePath]) => imagePath);

  // 6. Disaster Response Rover Images
  const disasterResponseRoverImages = Object.entries(
    import.meta.glob('../assets/disaster-response-rover/*.{png,jpg,jpeg}', { eager: true, import: 'default' })
  )
    .sort(([leftPath], [rightPath]) => leftPath.localeCompare(rightPath))
    .map(([, imagePath]) => imagePath);


  const projects = [
    {
      title: 'Fire Identification using Thermal imaging',
      subtitle: 'THERMAL IMAGING TOOLKIT FOR COAL MINES',
      text: 'Developed a lightweight Python-based toolkit to interface with a Topdon TC001 thermal camera for fire identification and thermal monitoring in coal-mine environments. Implemented camera integration scripts to acquire live thermal frames, capture periodic snapshots, and store timestamped temperature imagery for inspection and analysis. Designed utilities to organize captured images into structured directories, enabling systematic monitoring and manual review of underground conditions.',
      image: fireIdentificationImages[0],
      images: fireIdentificationImages,
      github: 'https://github.com/joel-tm/Fire-Identification-in-Coal-Mines-Using-Thermal-Imaging',
    },
    {
      title: 'Robotic Arm 6-DOF',
      subtitle: '3D-PRINTED ROBOTICS WITH BLUETOOTH CONTROL',
      text: '3D-printed a robotic arm with 6 servo motors enabling full 3D movement, including base rotation, shoulder, elbow, wrist pitch, yaw, and gripper. Designed an Android app using MIT App Inventor with Bluetooth control and 6 independent sliders for joint movement, enabling real-time control over each joint. Implemented communication using an HC-05 Bluetooth module with an average response time of under 5 seconds for input.',
      image: roboticarmImages[2],
      images: roboticarmImages,
      github: 'https://github.com/joel-tm/Robotic-arm-with-6-DOF',
    },
        {
      title: 'Disaster Response Rover',
      subtitle: 'AUTONOMOUS NAVIGATION WITH ROS & LIDAR',
      text: 'Designed and engineered a 6-wheeled rover with rocker-bogie suspension for rough terrains. Developed a ROS-based obstacle detection system using LIDAR sensor data, achieving a 95% accuracy rate in identifying obstacles within a 15-meter radius during field tests.',
      image: disasterResponseRoverImages[1],
      images: disasterResponseRoverImages,
      github: 'https://github.com/joel-tm/Autonomous-Disaster-response-rover',
    },
    {
      title: 'AI Research Agent',
      subtitle: 'GRAPH-BASED AGENTIC SEARCH USING LANGGRAPH',
      text: 'An AI research agent built using Python, LangGraph, and the Gemini API. Designed a modular, terminal-based system that classifies user queries and dynamically routes them through a graph-based control flow. Encyclopedic queries are routed to Wikipedia, while time-sensitive requests are handled via DuckDuckGo Search. Focused on clean architecture, state management, and extensibility, ensuring responses are returned within 3–7 seconds.',
      image: aiResearchAgentImages[0],
      images: aiResearchAgentImages,
      github: 'https://github.com/joel-tm/AI-research-agent-using-LangGraph',
    },
    {
      title: 'Stock Market Predictor',
      subtitle: 'LSTM FORECASTING & BERT SENTIMENT ANALYSIS',
      text: 'Built a machine learning model using LSTM neural networks and implemented Sentiment Analysis of financial news using BERT (Transformers) to enhance stock price forecasting accuracy. Analyzed and merged 10 years of historical stock data for 5 companies with sentiment data using Python and Pandas. Created a Streamlit-based interface for visualization.',
      image: stockMarketPredictorImages[0],
      images: stockMarketPredictorImages,
      github: 'https://github.com/joel-tm/stock-market-predictor-using-machine-learning',
    },
    {
      title: 'Style AI',
      subtitle: 'FULL-STACK WARDROBE INTERFACE & LLM api',
      text: 'Built a full-stack AI-powered digital wardrobe system with modular features including wardrobe management, outfit recommendations, and image generation based on weather and destination. Developed intelligent clothing analysis and outfit recommendation pipelines using Gemini 2.0 Flash, extracting detailed garment attributes from images. Integrated Google Cloud APIs and AI services (Weather, Places, Imagen 3.0) to deliver context-aware outfit recommendations.',
      image: styleAiPrimaryImage,
      images: styleAiImages,
      github: 'https://github.com/joel-tm/style-ai-full',
    }
  ];

  let trackNode;
  let activeProject = null;
  let activeImageIndex = 0;
  let autoCycleTimer;

  function scrollRail(direction) {
    if (!trackNode) {
      return;
    }

    const distance = Math.max(320, Math.round(trackNode.clientWidth * 0.72));
    trackNode.scrollBy({ left: direction * distance, behavior: 'smooth' });
  }

  function openProject(project) {
    activeProject = project;
    activeImageIndex = 0;
    restartAutoCycle();
  }

  function closeProject() {
    activeProject = null;
    activeImageIndex = 0;
    stopAutoCycle();
  }

  function getProjectImages(project) {
    return project?.images?.length ? project.images : [project.image];
  }

  function previousProjectImage() {
    if (!activeProject) {
      return;
    }

    const images = getProjectImages(activeProject);
    if (images.length < 2) {
      return;
    }

    activeImageIndex = (activeImageIndex - 1 + images.length) % images.length;
    restartAutoCycle();
  }

  function nextProjectImage() {
    if (!activeProject) {
      return;
    }

    const images = getProjectImages(activeProject);
    if (images.length < 2) {
      return;
    }

    activeImageIndex = (activeImageIndex + 1) % images.length;
    restartAutoCycle();
  }

  function stopAutoCycle() {
    if (autoCycleTimer) {
      clearInterval(autoCycleTimer);
      autoCycleTimer = undefined;
    }
  }

  function restartAutoCycle() {
    stopAutoCycle();

    if (!activeProject || getProjectImages(activeProject).length < 2) {
      return;
    }

    autoCycleTimer = setInterval(() => {
      activeImageIndex = (activeImageIndex + 1) % getProjectImages(activeProject).length;
    }, 18000);
  }

  function projectBackground(imageUrl, overlayStrength = 0.45) {
    return `background-image: linear-gradient(180deg, rgba(0, 0, 0, 0.03), rgba(0, 0, 0, ${overlayStrength})), url("${imageUrl}");`;
  }

  function handleWindowKeydown(event) {
    if (event.key === 'Escape') {
      closeProject();
      return;
    }

    if (!activeProject) {
      return;
    }

    if (event.key === 'ArrowLeft') {
      previousProjectImage();
    }

    if (event.key === 'ArrowRight') {
      nextProjectImage();
    }
  }

  onDestroy(() => {
    stopAutoCycle();
  });
</script>

<svelte:window on:keydown={handleWindowKeydown} />

<section class="projects-section" id="projects">
  <div class="section-inner">
    <div class="projects-head">
      <p>Selected</p>
      <h2>Projects</h2>
    </div>

    <div class="projects-rail" aria-label="Projects showcase">
      <button class="projects-arrow projects-arrow-left" aria-label="Previous projects" on:click={() => scrollRail(-1)}></button>

      <div class="projects-track" bind:this={trackNode}>
        {#each projects as project}
          <article class="project-card">
            <button class="project-open" type="button" on:click={() => openProject(project)} aria-label={`Open ${project.title} details`}>
              <div class="project-media" style={projectBackground(project.image)}></div>
              <div class="project-copy">
                <h3>{project.title}</h3>
                <p class="project-subtitle">{project.subtitle}</p>
                <p>{project.text}</p>
              </div>
            </button>
            <a class="project-github-link" href={project.github} target="_blank" rel="noreferrer">GitHub Repo</a>
          </article>
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

      <div class="projects-modal-media" style={projectBackground(getProjectImages(activeProject)[activeImageIndex], 0.5)}>
        {#if getProjectImages(activeProject).length > 1}
          <button class="projects-image-nav projects-image-nav-left" type="button" aria-label="Previous project image" on:click={previousProjectImage}></button>
          <button class="projects-image-nav projects-image-nav-right" type="button" aria-label="Next project image" on:click={nextProjectImage}></button>
          <span class="projects-image-counter">{activeImageIndex + 1}/{getProjectImages(activeProject).length}</span>
        {/if}
      </div>

      <div class="projects-modal-copy">
        <p class="projects-modal-label">Project</p>
        <h3>{activeProject.title}</h3>
        <p class="projects-modal-subtitle">{activeProject.subtitle}</p>
        <p>{activeProject.text}</p>
        <a class="project-github-link project-github-link-modal" href={activeProject.github} target="_blank" rel="noreferrer">GitHub Repo</a>
      </div>
    </div>
  </div>
{/if}

```