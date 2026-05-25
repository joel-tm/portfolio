<script>
  import './ContactSection.css';
</script>

<footer class="brand-row" id="contact-form">
  <div class="section-inner brand-row-inner">
    <div class="contact-block">
      <p class="eyebrow">Get In Touch</p>
      <h2>Available for product builds, redesigns, and engineering consulting.</h2>
      <div class="contact-links">
        <a href="mailto:jo@example.com">jo@example.com</a>
        <a href="https://github.com" target="_blank" rel="noreferrer">GitHub</a>
        <a href="https://linkedin.com" target="_blank" rel="noreferrer">LinkedIn</a>
      </div>

      <form class="contact-form" action="#" method="post">
        <label>
          Name
          <input type="text" name="name" autocomplete="name" required />
        </label>

        <label>
          Email
          <input type="email" name="email" autocomplete="email" required />
        </label>

        <label>
          Project brief
          <textarea name="message" rows="4" required></textarea>
        </label>

        <button type="submit">Send Message</button>
      </form>
    </div>
  </div>
</footer>