<script>
  import ContactSection from './lib/sections/ContactSection.svelte';
  import FeatureSection from './lib/sections/FeatureSection.svelte';
  import HeroSection from './lib/sections/HeroSection.svelte';
  import InsightsSection from './lib/sections/InsightsSection.svelte';
  import ProjectsSection from './lib/sections/ProjectsSection.svelte';
  import ServicesSection from './lib/sections/ServicesSection.svelte';
  import TechStackSection from './lib/sections/TechStackSection.svelte';
</script>

<svelte:head>
  <title>Jo | Software Developer</title>
</svelte:head>

<main class="portfolio-shell">
  <HeroSection />
  <ServicesSection />
  <ProjectsSection />
  <TechStackSection />
  <FeatureSection />
  <InsightsSection />
  <ContactSection />
</main>