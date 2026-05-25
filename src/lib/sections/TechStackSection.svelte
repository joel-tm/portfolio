<script>
  import './TechStackSection.css';

  const matrix = ['Python', 'JavaScript', 'TypeScript', 'React', 'Azure', 'GitHub', 'Docker', 'Kubernetes'];

  const groups = [
    {
      title: 'FRONTEND',
      icon: '🔮',
      items: ['React', 'Next.js', 'TypeScript', 'Tailwind CSS', 'Svelte'],
    },
    {
      title: 'BACKEND',
      icon: '🧠',
      items: ['Node.js', 'FastAPI', 'Python', 'NestJS'],
    },
    {
      title: 'MEMORY (DATABASE)',
      icon: '💾',
      items: ['PostgreSQL', 'MySQL', 'Redis', 'Azure SQL Server'],
    },
    {
      title: 'AI/ML',
      icon: '🤖',
      items: ['TensorFlow', 'PyTorch', 'GEMINI', 'Hugging Face', 'LangChain'],
    },
  ];
</script>

<section class="tech-stack-section" id="tech-stack">
  <div class="section-inner">
    <header class="tech-stack-head">
      <p class="kicker">TECHNOLOGY MATRIX</p>
      <h2>Tech Stack</h2>
      <p class="subhead">⚙️ Technology STACK</p>

      <div class="matrix-row" aria-label="Technology matrix">
        {#each matrix as tech}
          <span>{tech}</span>
        {/each}
      </div>
    </header>

    <div class="tech-grid">
      {#each groups as group}
        <article class="tech-panel">
          <h3>{group.icon} {group.title}</h3>
          <ul>
            {#each group.items as item}
              <li>{item}</li>
            {/each}
          </ul>
        </article>
      {/each}
    </div>
  </div>
</section>
