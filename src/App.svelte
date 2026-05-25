<script>
  import ContactSection from './lib/sections/ContactSection.svelte';
  import FeatureSection from './lib/sections/FeatureSection.svelte';
  import HeroSection from './lib/sections/HeroSection.svelte';
  import InsightsSection from './lib/sections/InsightsSection.svelte';
  import ProjectsSection from './lib/sections/ProjectsSection.svelte';
  import ServicesSection from './lib/sections/ServicesSection.svelte';
</script>

<svelte:head>
  <title>Joel | Software Developer</title>
</svelte:head>

<main class="portfolio-shell">
  <HeroSection />
  <ServicesSection />
  <ProjectsSection />
  <FeatureSection />
  <InsightsSection />
  <ContactSection />
</main>