<script>
  import './CertificationSection.css';

  const certificatesLeft = [
    {
      title: 'Microsoft Azure Fundamentals (AZ-900)',
      issuer: 'Microsoft',
      focus: 'Cloud concepts, Azure services, governance, cost models',
      year: '2025',
    },
    {
      title: 'GitHub Actions & CI/CD',
      issuer: 'GitHub',
      focus: 'Workflow automation, release pipelines, repository security',
      year: '2025',
    },
    {
      title: 'Docker for Production Workloads',
      issuer: 'Docker',
      focus: 'Containerization, image strategy, runtime optimization',
      year: '2024',
    },
    {
      title: 'Kubernetes Application Developer',
      issuer: 'Cloud Native Training',
      focus: 'Pods, deployments, service networking, rollout strategies',
      year: '2024',
    },
  ];

  const certificatesRight = [
    {
      title: 'Advanced TypeScript Engineering',
      issuer: 'Frontend Masters',
      focus: 'Type safety, API contracts, scalable component patterns',
      year: '2025',
    },
    {
      title: 'React Performance & Architecture',
      issuer: 'Meta Learning',
      focus: 'State boundaries, rendering strategy, bundle control',
      year: '2024',
    },
    {
      title: 'PostgreSQL Performance Tuning',
      issuer: 'Database Academy',
      focus: 'Query plans, indexing strategy, reliability and scale',
      year: '2024',
    },
    {
      title: 'Applied AI with TensorFlow & PyTorch',
      issuer: 'ML Institute',
      focus: 'Model pipelines, practical deployment and evaluation',
      year: '2025',
    },
  ];
</script>

<section class="certification-section" id="certifications">
  <div class="section-inner">
    <header class="certification-head">
      <p>Professional Development</p>
      <h2>Certifications</h2>
    </header>

    <div class="certification-split">
      <div class="certification-column" aria-label="Certificates column one">
        {#each certificatesLeft as cert}
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
        {#each certificatesRight as cert}
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
  </div>
</section>
