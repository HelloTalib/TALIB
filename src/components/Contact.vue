<template>
  <section id="contact">
    <div class="section-wrap">
      <!-- Header -->
      <div class="contact-header fade-up">
        <div class="section-eyebrow">06 — Contact</div>
        <h2 class="section-heading">Let's <span class="gradient-text">talk.</span></h2>
        <p class="contact-sub">Have a project in mind or just want to say hi? I'd love to hear from you.</p>
      </div>

      <div class="contact-grid">
        <!-- Form -->
        <div class="form-wrap glass fade-up delay-1">
          <p class="form-hint">Fill out the form below and I'll get back to you within 24 hours.</p>
          <v-form
            ref="form"
            v-model="formIsValid"
            autocomplete="off"
            @submit.prevent="sendEmail"
            class="contact-form"
          >
            <v-text-field
              label="Name"
              variant="outlined"
              v-model="name"
              :rules="nonEmptyRule"
              required
              class="form-field"
            />
            <v-text-field
              label="Email"
              variant="outlined"
              v-model="email"
              :rules="emailRules"
              required
              class="form-field"
            />
            <v-text-field
              label="Subject"
              v-model="subject"
              :rules="nonEmptyRule"
              variant="outlined"
              required
              class="form-field"
            />
            <v-textarea
              variant="outlined"
              :rules="nonEmptyRule"
              v-model="message"
              label="Message"
              rows="5"
              required
              class="form-field"
            />

            <v-alert v-if="successAlert" type="success" class="form-alert" density="compact">Message sent successfully!</v-alert>
            <v-alert v-if="infoAlert"    type="info"    class="form-alert" density="compact">Sending…</v-alert>
            <v-alert v-if="errorAlert"   type="error"   class="form-alert" density="compact">Unable to send. Please email me directly.</v-alert>

            <div class="form-actions">
              <button
                type="submit"
                class="btn-send"
                :disabled="!formIsValid"
              >
                Send Message
                <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true"><line x1="22" y1="2" x2="11" y2="13"/><polygon points="22 2 15 22 11 13 2 9 22 2"/></svg>
              </button>
            </div>
          </v-form>
        </div>

        <!-- Info sidebar -->
        <div class="contact-info fade-up delay-2">
          <div class="info-block glass">
            <h3 class="info-heading">Get in touch</h3>

            <div v-for="(det, i) in contactDetails" :key="i" class="contact-row">
              <span class="contact-icon" aria-hidden="true">
                <svg v-if="det.title === 'Address'" width="15" height="15" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8"><path d="M12 13a4 4 0 100-8 4 4 0 000 8z"/><path d="M12 22s8-4.5 8-10a8 8 0 10-16 0c0 5.5 8 10 8 10z"/></svg>
                <svg v-else-if="det.title === 'Phone'" width="15" height="15" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8"><path d="M22 16.92v3a2 2 0 01-2.18 2 19.79 19.79 0 01-8.63-3.07A19.5 19.5 0 013.07 10.8 19.79 19.79 0 01.07 2.18 2 2 0 012.03 0h3a2 2 0 012 1.72c.127.96.361 1.903.7 2.81a2 2 0 01-.45 2.11L6.09 7.91a16 16 0 006 6l1.27-1.27a2 2 0 012.11-.45c.907.339 1.85.573 2.81.7A2 2 0 0122 14.92v2z"/></svg>
                <svg v-else width="15" height="15" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8"><path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"/><path d="M22 6l-10 7L2 6"/></svg>
              </span>
              <div>
                <div class="contact-label">{{ det.title }}</div>
                <div class="contact-value">{{ det.val }}</div>
              </div>
            </div>
          </div>

          <!-- Social links -->
          <div class="socials-block">
            <div class="socials-label">Follow</div>
            <div class="socials-row">
              <a
                v-for="(icon, i) in socialIcons"
                :key="i"
                :title="icon.name"
                target="_blank"
                rel="noopener noreferrer"
                :href="icon.link"
                class="social-link"
              >
                <!-- Telegram -->
                <svg v-if="icon.name === 'Telegram'" width="18" height="18" viewBox="0 0 24 24" fill="currentColor" aria-hidden="true"><path d="M12 0C5.373 0 0 5.373 0 12s5.373 12 12 12 12-5.373 12-12S18.627 0 12 0zm5.562 8.248l-2.016 9.504c-.149.67-.539.833-1.092.519l-3-2.21-1.447 1.394c-.16.16-.295.295-.605.295l.215-3.054 5.565-5.027c.242-.215-.053-.334-.375-.12l-6.88 4.332-2.963-.924c-.644-.2-.657-.644.135-.953l11.571-4.462c.537-.196 1.006.13.892.706z"/></svg>
                <!-- Twitter / X -->
                <svg v-else-if="icon.name === 'Twitter'" width="18" height="18" viewBox="0 0 24 24" fill="currentColor" aria-hidden="true"><path d="M18.244 2.25h3.308l-7.227 8.26 8.502 11.24H16.17l-5.214-6.817L4.99 21.75H1.68l7.73-8.835L1.254 2.25H8.08l4.713 6.231zm-1.161 17.52h1.833L7.084 4.126H5.117z"/></svg>
                <!-- LinkedIn -->
                <svg v-else-if="icon.name === 'Linkedin'" width="18" height="18" viewBox="0 0 24 24" fill="currentColor" aria-hidden="true"><path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433a2.062 2.062 0 01-2.063-2.065 2.064 2.064 0 112.063 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/></svg>
                <span v-else class="social-fallback">{{ icon.name }}</span>
              </a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      // Form model directives
      formIsValid: true,
      name: "",
      email: "",
      subject: "",
      message: "",

      // Alert visibility directives
      successAlert: false,
      infoAlert: false,
      errorAlert: false,

      nonEmptyRule: [v => !!v || "This field can't be empty"],

      emailRules: [
        v => !!v || "E-mail is required",
        v => /.+@.+/.test(v) || "E-mail must be valid"
      ],

      contactDetails: [
        {
          title: "Address",
          val: "Banani, Bogura, Bangladesh",
          icon: "mdi-map-marker"
        },
        { title: "Phone", val: "+8801795142054", icon: "mdi-phone" },
        { title: "Email", val: "talib@bdthemes.com", icon: "mdi-email" }
      ],

      socialIcons: [
        {
          name: "Telegram",
          link: "https://t.me/hellotalib",
          icon: "mdi-telegram"
        },
        {
          name: "Twitter",
          link: "https://twitter.com/hellotalib",
          icon: "mdi-twitter"
        },
        {
          name: "Linkedin",
          link: "https://linkedin.com/in/hellotalib",
          icon: "mdi-linkedin"
        },
      ]
    };
  },

  methods: {
    async sendEmail() {
      // Validate the form, if errors, exit right away
      const { valid } = await this.$refs.form.validate();
      if (!valid) return;

      const body = new URLSearchParams({
        name: this.name,
        email: this.email,
        subject: this.subject,
        message: this.message
      });

      this.infoAlert = true;
      this.formIsValid = false;

      try {
        const res = await fetch("https://talib.netlify.app/mail.php", {
          method: "POST",
          headers: { "Content-Type": "application/x-www-form-urlencoded" },
          body
        });
        const text = await res.text();
        this.infoAlert = false;
        if (text.trim() === "Success") {
          this.successAlert = true;
        } else {
          this.errorAlert = true;
        }
      } catch {
        this.infoAlert = false;
        this.errorAlert = true;
      } finally {
        setTimeout(() => {
          this.successAlert = false;
          this.errorAlert = false;
          this.$refs.form?.reset();
          this.formIsValid = true;
        }, 3000);
      }
    }
  }
};
</script>

<style scoped>
section { position: relative; }
a { text-decoration: none; }

/* ── Header ── */
.contact-header { margin-bottom: 64px; }
.section-heading {
  font-size: clamp(32px, 4vw, 52px);
  font-weight: 700;
  line-height: 1.1;
  margin-bottom: 16px;
}
.contact-sub {
  font-size: 16px;
  color: var(--color-muted);
  max-width: 480px;
  margin: 0;
}

/* ── Grid ── */
.contact-grid {
  display: grid;
  grid-template-columns: 1fr 380px;
  gap: 48px;
  align-items: start;
}

/* ── Form ── */
.form-wrap {
  padding: 40px;
}
.form-hint {
  font-size: 14px;
  color: var(--color-muted);
  margin: 0 0 28px 0;
}
.contact-form {
  display: flex;
  flex-direction: column;
  gap: 4px;
}
.form-alert { margin-bottom: 8px; }
.form-actions { display: flex; justify-content: flex-end; margin-top: 8px; }

/* ── Vuetify field overrides ── */
.form-field :deep(.v-field) {
  background: var(--color-surface-2) !important;
  border-radius: var(--radius-md) !important;
}
.form-field :deep(.v-field__outline__start),
.form-field :deep(.v-field__outline__notch),
.form-field :deep(.v-field__outline__end) {
  border-color: var(--color-border) !important;
  transition: border-color 0.2s ease;
}
.form-field :deep(.v-field--focused .v-field__outline__start),
.form-field :deep(.v-field--focused .v-field__outline__notch),
.form-field :deep(.v-field--focused .v-field__outline__end) {
  border-color: var(--color-accent) !important;
}
.form-field :deep(.v-label) {
  color: var(--color-muted) !important;
  font-family: var(--font-body);
  font-size: 14px;
}
.form-field :deep(input),
.form-field :deep(textarea) {
  color: var(--color-text) !important;
  font-family: var(--font-body) !important;
  font-size: 14px;
  caret-color: var(--color-accent);
}
.form-field :deep(.v-messages__message) {
  color: #F87171;
}

/* ── Send button ── */
.btn-send {
  display: inline-flex;
  align-items: center;
  gap: 10px;
  padding: 13px 28px;
  background: var(--color-accent);
  color: #0A0A0F;
  font-weight: 600;
  font-size: 14px;
  border: none;
  border-radius: var(--radius-md);
  cursor: pointer;
  transition: filter var(--transition-base), transform var(--transition-base);
  will-change: transform;
  font-family: var(--font-body);
}
.btn-send:hover:not(:disabled) { filter: brightness(1.06); transform: translateY(-1px); }
.btn-send:disabled { opacity: 0.5; cursor: not-allowed; }

/* ── Info sidebar ── */
.contact-info { display: flex; flex-direction: column; gap: 20px; }
.info-block { padding: 28px 24px; }
.info-heading {
  font-family: var(--font-mono);
  font-size: 11px;
  font-weight: 500;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--color-accent);
  margin-bottom: 20px;
}
.contact-row {
  display: flex;
  align-items: flex-start;
  gap: 14px;
  padding: 12px 0;
  border-bottom: 1px solid var(--color-border);
}
.contact-row:last-child { border-bottom: none; }
.contact-icon {
  width: 32px;
  height: 32px;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  background: var(--color-accent-dim);
  border: 1px solid var(--color-accent-border);
  border-radius: var(--radius-sm);
  color: var(--color-accent);
  flex-shrink: 0;
}
.contact-label {
  font-size: 11px;
  font-weight: 500;
  letter-spacing: 0.16em;
  text-transform: uppercase;
  color: var(--color-muted);
  margin-bottom: 2px;
}
.contact-value {
  font-size: 13px;
  color: var(--color-text);
}

/* ── Socials ── */
.socials-block { padding: 24px; }
.socials-label {
  font-family: var(--font-mono);
  font-size: 10px;
  letter-spacing: 0.22em;
  text-transform: uppercase;
  color: var(--color-muted);
  margin-bottom: 14px;
}
.socials-row { display: flex; gap: 10px; }
.social-link {
  width: 42px;
  height: 42px;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  border-radius: var(--radius-md);
  color: var(--color-muted);
  border: 1px solid var(--color-border);
  background: rgba(255, 255, 255, 0.02);
  transition: color var(--transition-base), border-color var(--transition-base), transform var(--transition-base);
}
.social-link:hover {
  color: var(--color-accent);
  border-color: var(--color-accent-border);
  transform: translateY(-2px);
}
.social-fallback { font-size: 10px; font-weight: 600; letter-spacing: 0.05em; }

/* ── Responsive ── */
@media (max-width: 1024px) {
  .contact-grid { grid-template-columns: 1fr 320px; gap: 32px; }
}
@media (max-width: 768px) {
  .contact-grid { grid-template-columns: 1fr; }
  .form-wrap { padding: 28px 24px; }
}
@media (max-width: 640px) {
  .form-wrap { padding: 20px 16px; }
  .contact-header { margin-bottom: 40px; }
}
</style>
