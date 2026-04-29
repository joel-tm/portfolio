<script>
  import './InsightsSection.css';

  const articles = [
    {
      title: 'How I structure frontend systems for long-lived products',
      category: 'Engineering Notes',
      text: 'Patterns for component composition, state boundaries, and design consistency when a product has to keep shipping without turning into a rewrite candidate.',
    },
    {
      title: 'Observability decisions that save time later',
      category: 'Platform Notes',
      text: 'A practical approach to logs, metrics, release visibility, and issue triage for small teams that still need high confidence in production.',
    },
  ];
</script>

<section class="insights-row">
  <div class="articles-panel">
    {#each articles as article}
      <article class="insight-card">
        <div class="insight-thumb"></div>
        <div class="insight-copy">
          <p class="insight-meta">{article.category}</p>
          <h3>{article.title}</h3>
          <p>{article.text}</p>
          <a href="#contact">Read more</a>
        </div>
      </article>
    {/each}
  </div>

  <aside class="testimonial-panel">
    <blockquote>
      Structured delivery, sharp frontend implementation, and pragmatic engineering decisions. The work consistently balanced speed with maintainability.
    </blockquote>
    <p class="testimonial-author">Client feedback • product engineering engagement</p>
  </aside>
</section>