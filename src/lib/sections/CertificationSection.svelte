<script>
  import './CertificationSection.css';

const visibleCount = 3;

const certificatesLeft = [
  {
    title: 'Microsoft Certified: Azure Administrator Associate',
    issuer: 'Microsoft',
    focus: 'Identity management, cloud governance, virtual networking, and storage solutions',
  },
  {
    title: 'Elasticsearch Essential Training',
    issuer: 'LinkedIn',
    focus: 'Distributed search engines, indexing strategies, cluster health, and data analysis',
  },
  {
    title: 'Learning Kubernetes',
    issuer: 'LinkedIn',
    focus: 'Container orchestration, pod configuration, service routing, and deployment basics',
  },
  {
    title: 'Programming Foundations: Databases',
    issuer: 'LinkedIn',
    focus: 'Relational data modeling, DBMS fundamentals, and SQL query structure',
  },
];

const certificatesRight = [
  {
    title: 'OpenShift Essential Training: Container Orchestration and Deployment',
    issuer: 'LinkedIn',
    focus: 'Enterprise Kubernetes management, cluster deployment, and cloud-native strategies',
  },  
    {
    title: 'Microsoft Certified: Azure AI Fundamentals',
    issuer: 'Microsoft',
    focus: 'AI workloads, computer vision, natural language processing, and ML workloads on Azure',
  },
  {
    title: 'Exploring Web Scraping with Python',
    issuer: 'Pluralsight',
    focus: 'Automated data extraction, DOM parsing, HTTP requests, and Python scripting',
  },
  {
    title: 'Certified English Proficiency',
    issuer: 'Duolingo English Test',
    focus: 'Professional English communication, comprehensive literacy, and conversational fluency',
  },
  {
    title: 'Machine Learning using R',
    issuer: 'TECHMAGHI',
    focus: 'Statistical modeling, predictive analytics, and data pipeline construction in R',
  },
  {
    title: 'Build, Train, and Deploy Your First Neural Network with TensorFlow 2',
    issuer: 'Pluralsight',
    focus: 'Deep learning architectures, neural network training, and model optimization',
  },
  {
    title: 'Arduino',
    issuer: 'Udemy',
    focus: 'Microcontroller programming, digital systems, hardware prototyping, and Arduino IDE',
  },
];

  let isExpanded = false;

  const hasMoreCertificates = certificatesLeft.length > visibleCount || certificatesRight.length > visibleCount;

  function toggleExpanded() {
    isExpanded = !isExpanded;
  }
</script>

<section class="certification-section" id="certifications">
  <div class="section-inner">
    <header class="certification-head">
      <p>Professional Development</p>
      <h2>Certifications</h2>
    </header>

    <div class="certification-split">
      <div class="certification-column" aria-label="Certificates column one">
        {#each (isExpanded ? certificatesLeft : certificatesLeft.slice(0, visibleCount)) as cert}
          <article class="certificate-card">
            <div class="cert-chip">{cert.year}</div>
            <div class="cert-copy">
              <h3>{cert.title}</h3>
              <p class="issuer">{cert.issuer}</p>
              <p>{cert.focus}</p>
            </div>
          </article>
        {/each}
      </div>

      <div class="certification-column" aria-label="Certificates column two">
        {#each (isExpanded ? certificatesRight : certificatesRight.slice(0, visibleCount)) as cert}
          <article class="certificate-card">
            <div class="cert-chip">{cert.year}</div>
            <div class="cert-copy">
              <h3>{cert.title}</h3>
              <p class="issuer">{cert.issuer}</p>
              <p>{cert.focus}</p>
            </div>
          </article>
        {/each}
      </div>
    </div>

    {#if hasMoreCertificates}
      <div class="certification-actions">
        <button class="certification-toggle" type="button" on:click={toggleExpanded}>
          {isExpanded ? 'View Less' : 'View More'}
        </button>
      </div>
    {/if}
  </div>
</section>
