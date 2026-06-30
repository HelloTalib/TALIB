<template>
  <section id="about">
    <div class="section-wrap">
      <div class="about-grid">
        <!-- Left: visual column -->
        <aside class="about-left fade-up">
          <!-- Stats -->
          <div class="stats-grid" ref="statsGrid">
            <div
              v-for="(stat, i) in stats"
              :key="i"
              class="stat-card glass"
            >
              <div class="stat-num gradient-text">
                <template v-if="stat.target !== null">{{ stat.current }}{{ stat.suffix }}</template>
                <template v-else>{{ stat.symbol }}</template>
              </div>
              <div class="stat-label">{{ stat.label }}</div>
            </div>
          </div>

          <!-- Info card -->
          <div class="info-card glass">
            <div class="info-row">
              <span class="info-icon" aria-hidden="true">
                <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M12 13a4 4 0 100-8 4 4 0 000 8z"/><path d="M12 22s8-4.5 8-10a8 8 0 10-16 0c0 5.5 8 10 8 10z"/></svg>
              </span>
              <div>
                <div class="info-label">Location</div>
                <div class="info-value">Banani, Bogura, Bangladesh</div>
              </div>
            </div>
            <div class="info-row">
              <span class="info-icon" aria-hidden="true">
                <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"/><path d="M22 6l-10 7L2 6"/></svg>
              </span>
              <div>
                <div class="info-label">Email</div>
                <div class="info-value">talib@bdthemes.com</div>
              </div>
            </div>
            <div class="info-row">
              <span class="info-icon" aria-hidden="true">
                <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M22 16.92v3a2 2 0 01-2.18 2 19.79 19.79 0 01-8.63-3.07A19.5 19.5 0 013.07 10.8 19.79 19.79 0 01.07 2.18 2 2 0 012.03 0h3a2 2 0 012 1.72c.127.96.361 1.903.7 2.81a2 2 0 01-.45 2.11L6.09 7.91a16 16 0 006 6l1.27-1.27a2 2 0 012.11-.45c.907.339 1.85.573 2.81.7A2 2 0 0122 14.92v2z"/></svg>
              </span>
              <div>
                <div class="info-label">Phone</div>
                <div class="info-value">+8801795142054</div>
              </div>
            </div>
          </div>

          <!-- Signature -->
          <img :src="signature" alt="Abu Talib signature" class="signature-img" />
        </aside>

        <!-- Right: content column -->
        <div class="about-right">
          <!-- Who I am -->
          <div class="fade-up">
            <div class="section-eyebrow">01 — Introduction</div>
            <h2 class="section-heading">Who <span class="gradient-text">I am.</span></h2>
            <p class="about-bio">{{ aboutMe }}</p>
          </div>

          <!-- What I can do -->
          <div class="fade-up delay-2" style="margin-top: 64px;">
            <div class="section-eyebrow">02 — Services</div>
            <h2 class="section-heading">What I <span class="gradient-text">can do.</span></h2>

            <div class="accordion">
              <div
                v-for="(item, i) in aboutItems"
                :key="i"
                class="accordion-item"
                :class="{ 'is-open': openPanel === i }"
              >
                <button
                  class="accordion-trigger"
                  @click="openPanel = openPanel === i ? null : i"
                  :aria-expanded="openPanel === i"
                >
                  <span class="panel-num">0{{ i + 1 }}</span>
                  <span class="panel-title">{{ item.title }}</span>
                  <span class="panel-chevron" aria-hidden="true">
                    <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M6 9l6 6 6-6"/></svg>
                  </span>
                </button>
                <div class="accordion-body">
                  <p>{{ item.description }}</p>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import abstract1 from "@/assets/abstract-1.png";
import signature from "@/assets/signature.png";

export default {
  data() {
    return {
      abstract1,
      signature,
      openPanel: null,
      statsAnimated: false,
      stats: [
        { target: 5,   suffix: '+', label: 'Years experience', current: 0 },
        { target: 100, suffix: '+', label: 'Projects shipped', current: 0 },
        { target: 30,  suffix: '+', label: 'WordPress themes', current: 0 },
        { target: null, symbol: '\u221e', label: 'Cups of coffee' },
      ],
      aboutMe:
        "Hi there! I'm Abu Talib — known to most as just TALIB. I'm a Software Developer at BdThemes with 5+ years of experience building everything from pixel-perfect frontend interfaces to WordPress plugins used by thousands daily. For me, the sky's the limit.",
      aboutItems: [
        {
          title: "Front End Development",
          description:
            "I will create your website from scratch using HTML, CSS, SCSS, VueJs,VeutifyJs OR Meterial Design with Awesome jQuery features & cool animations:) I just needed PSD or anykind of website layout from you",
        },
        {
          title: "WordPress Theme Development",
          description:
            "I will convert your static website to Dynamic Website; That means you can change everyting in your website for example text, content, image, video, audio, etc. [without any coding knowledge]:-)",
        },
        {
          title: "Elementor Addons/Widget Develop From Scratch",
          description:
            "As a WordPress Developer or Elementor Expert you know that sometimes Elementor Or Elementor Pro default Widget is not enough to create your website. that's why you need a more customizable, Modern, and advanced Elementor Widget. @Hey! don't worry, I  will develop Elementor Addons or Wedget from scratch. I just want to make your life easier and put a smile on your face:)",
        },
        {
          title: "Online Store or e-Commerce Website",
          description:
            "I know, this is not something to boast of but yeah I have pretty decent knowledge of WooCommerce Website Development; In the world wide, I've dozens of active online store & e-commerce Website that I designed, customized and developed.",
        },
        {
          title: "REST APIs",
          description:
            "You are very well known what an API is, right? Well I know how to build one. yes, I can makes Node API and Restful Express API etc.",
        },
        {
          title: "CRUD Application",
          description:
            "I  will create your web application using firebase authentication that you can CREATE/READ/UPDATE/DELETE(post) without any kind of coding knowledge.",
        },
        {
          title: "Full Stack Web Development",
          description:
            'Count me, if you need to help any kind of Web Development. Be it frontend or backend. Just keep me away from Fornt-End Developer.I despise that, I have enough knowledge of backend too and alos "MERN, MEAN stack". that means build a website using MongoDB,"Expressjs, ReactJs or Vuejs & Nodejs.',
        },
      ],
    };
  },
  mounted() {
    const statsEl = this.$refs.statsGrid;
    if (!statsEl) return;
    const observer = new IntersectionObserver(([entry]) => {
      if (entry.isIntersecting && !this.statsAnimated) {
        this.statsAnimated = true;
        this.stats.forEach(stat => {
          if (stat.target !== null) this.animateStat(stat);
        });
        observer.disconnect();
      }
    }, { threshold: 0.55 });
    observer.observe(statsEl);
  },
  methods: {
    animateStat(stat) {
      const duration = 1800;
      const start = performance.now();
      const tick = (now) => {
        const p = Math.min((now - start) / duration, 1);
        const eased = 1 - Math.pow(1 - p, 4);
        stat.current = Math.round(eased * stat.target);
        if (p < 1) requestAnimationFrame(tick);
      };
      requestAnimationFrame(tick);
    },
    togglePanel(i) {
      this.openPanel = this.openPanel === i ? null : i;
    },
  },
};
</script>

<style scoped>
section { position: relative; }

/* ── Grid ── */
.about-grid {
  display: grid;
  grid-template-columns: 340px 1fr;
  gap: 80px;
  align-items: start;
}

/* ── Left Column ── */
.about-left { display: flex; flex-direction: column; gap: 20px; }

.stats-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 12px;
}
.stat-card {
  padding: 24px 18px;
  text-align: center;
}
.stat-num {
  font-family: var(--font-display);
  font-size: 40px;
  font-weight: 700;
  line-height: 1;
  margin-bottom: 6px;
}
.stat-label {
  font-size: 11px;
  font-weight: 500;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--color-muted);
}

/* Info card */
.info-card {
  padding: 8px 20px;
}
.info-row {
  display: flex;
  align-items: flex-start;
  gap: 14px;
  padding: 14px 0;
  border-bottom: 1px solid var(--color-border);
}
.info-row:last-child { border-bottom: none; }
.info-icon {
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
.info-label {
  font-size: 11px;
  font-weight: 500;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--color-muted);
  margin-bottom: 2px;
}
.info-value {
  font-size: 13px;
  color: var(--color-text);
}

.signature-img {
  width: 140px;
  opacity: 0.7;
  filter: invert(1) brightness(0.8);
}

/* ── Right Column ── */
.section-heading {
  font-size: clamp(32px, 4vw, 52px);
  font-weight: 700;
  line-height: 1.1;
  margin-bottom: 24px;
}

.about-bio {
  font-size: 16px;
  line-height: 1.75;
  color: rgba(226, 232, 240, 0.75);
  margin: 0;
  max-width: 560px;
}

/* ── Accordion ── */
.accordion { display: flex; flex-direction: column; gap: 8px; }

.accordion-item {
  border: 1px solid var(--color-border);
  border-radius: var(--radius-md);
  overflow: hidden;
  transition: border-color 0.25s ease;
}
.accordion-item.is-open,
.accordion-item:hover {
  border-color: var(--color-accent-border);
}

.accordion-trigger {
  width: 100%;
  display: flex;
  align-items: center;
  gap: 16px;
  padding: 16px 20px;
  background: none;
  border: none;
  cursor: pointer;
  text-align: left;
  color: var(--color-text);
  transition: background 0.2s ease;
}
.accordion-trigger:hover { background: rgba(255, 255, 255, 0.03); }

.panel-num {
  font-family: var(--font-mono);
  font-size: 11px;
  font-weight: 500;
  color: var(--color-accent);
  letter-spacing: 0.1em;
  flex-shrink: 0;
}
.panel-title {
  flex: 1;
  font-size: 15px;
  font-weight: 500;
}
.panel-chevron {
  color: var(--color-muted);
  flex-shrink: 0;
  transition: transform 0.25s ease, color 0.25s ease;
}
.accordion-item.is-open .panel-chevron {
  transform: rotate(180deg);
  color: var(--color-accent);
}

.accordion-body {
  max-height: 0;
  overflow: hidden;
  transition: max-height 0.35s ease;
}
.accordion-item.is-open .accordion-body { max-height: 240px; }
.accordion-body p {
  padding: 4px 20px 20px 20px;
  margin: 0;
  font-size: 14px;
  line-height: 1.7;
  color: var(--color-muted);
  padding-left: calc(20px + 16px + 20px);
}

/* ── Responsive ── */
@media (max-width: 1024px) {
  .about-grid { grid-template-columns: 280px 1fr; gap: 48px; }
}
@media (max-width: 768px) {
  .about-grid { grid-template-columns: 1fr; gap: 48px; }
  .about-left { display: grid; grid-template-columns: 1fr 1fr; gap: 16px; align-items: start; }
  .stats-grid { grid-column: 1 / -1; }
  .signature-img { display: none; }
}
@media (max-width: 640px) {
  .about-left { grid-template-columns: 1fr; }
}
</style>
