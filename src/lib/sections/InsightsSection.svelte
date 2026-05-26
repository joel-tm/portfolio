<script>
  import './InsightsSection.css';

  const articles = [
    {
      title: 'How I structure frontend systems for long-lived products',
      category: 'Engineering Notes',
      text: 'Patterns for component composition, state boundaries, and design consistency when a product has to keep shipping without turning into a rewrite candidate.',
      thumbClass: 'thumb-engineering',
      thumbLabel: 'Frontend System',
      thumbValue: '99.2% stability',
    },
    {
      title: 'Observability decisions that save time later',
      category: 'Platform Notes',
      text: 'A practical approach to logs, metrics, release visibility, and issue triage for small teams that still need high confidence in production.',
      thumbClass: 'thumb-platform',
      thumbLabel: 'Observability',
      thumbValue: '12ms p95 logs',
    },
  ];

  const profileNote = 'First principles thinker, enjoys building things, likes all engineering, technology, science.';
</script>

<section class="insights-row">
  <div class="section-inner insights-row-inner">
    <div class="articles-panel">
      {#each articles as article}
        <article class="insight-card">
          <div class={`insight-thumb ${article.thumbClass}`}>
            <div class="thumb-header">
              <span>{article.thumbLabel}</span>
              <span class="thumb-led"></span>
            </div>
            <div class="thumb-bars" aria-hidden="true">
              <i style="--bar: 42%"></i>
              <i style="--bar: 68%"></i>
              <i style="--bar: 54%"></i>
              <i style="--bar: 86%"></i>
              <i style="--bar: 64%"></i>
            </div>
            <p class="thumb-metric">{article.thumbValue}</p>
          </div>
          <div class="insight-copy">
            <p class="insight-meta">{article.category}</p>
            <h3>{article.title}</h3>
            <p>{article.text}</p>
            {#if article.category === 'Engineering Notes'}

              <p class="insight-profile-note">{profileNote}</p>
            {/if}
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
  </div>
</section>