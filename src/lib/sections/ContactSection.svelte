<script>
  import './ContactSection.css';
</script>

<footer class="brand-row" id="contact-form">
  <div class="section-inner brand-row-inner">
    <div class="contact-block">
      <p class="eyebrow">Get In Touch</p>
      <h3>Available for product builds, redesigns, and engineering consulting.</h3>
      <div class="contact-links">
        <a href="mailto:joeltmathew4@gmail.com">joeltmathew4@gmail.com</a>
        <a href="https://github.com/joel-tm" target="_blank" rel="noreferrer">GitHub</a>
        <a href="https://www.linkedin.com/in/joel-t-mathew/" target="_blank" rel="noreferrer">LinkedIn</a>
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