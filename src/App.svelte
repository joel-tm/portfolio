<script>
  import ContactSection from './lib/sections/ContactSection.svelte';
  import CertificationSection from './lib/sections/CertificationSection.svelte';
  import ExperienceSection from './lib/sections/ExperienceSection.svelte';
  import FeatureSection from './lib/sections/FeatureSection.svelte';
  import HeroSection from './lib/sections/HeroSection.svelte';
  import InsightsSection from './lib/sections/InsightsSection.svelte';
  import ProjectsSection from './lib/sections/ProjectsSection.svelte';
  import ServicesSection from './lib/sections/ServicesSection.svelte';
  import TechStackSection from './lib/sections/TechStackSection.svelte';
</script>

<svelte:head>
  <title>Joel | Portfolio</title>
  
  <link rel="icon" type="image/png" href="data:image/svg+xml,<svg xmlns=%22http://www.w3.org/2000/svg%22 viewBox=%220 0 100 100%22><text y=%22.9em%22 font-size=%2280%22>💻</text></svg>" />

  </svelte:head>

<main class="portfolio-shell">
  <HeroSection />
  <ServicesSection />
  <ExperienceSection />
  <ProjectsSection />
  <TechStackSection />
  <FeatureSection />
  <CertificationSection />
  <InsightsSection />
  <ContactSection />
</main>